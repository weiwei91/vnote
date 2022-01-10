# rabbitmq配置

```

@Configuration
public class RabbitmqConfig {

    @Value("${component.id}")
    String componentId;

    @Bean
    public Queue uploadPicture () {
        return new Queue(Constants.QUEUE_KEY_UPLOAD_PICTURE);
    }
    @Bean
    public Queue uploadObject () {
        return new Queue(Constants.QUEUE_KEY_UPLOAD_OBJECT);
    }
    @Bean
    public DirectExchange exchangeOfSection (){
        return new DirectExchange(componentId);
    }

    @Bean
    public Binding bindingUploadPicture(){
        return BindingBuilder.bind(uploadPicture()).to(exchangeOfSection()).with(Constants.QUEUE_KEY_UPLOAD_PICTURE);
    }

    @Bean
    public RabbitTemplate createRabbitTemplate(ConnectionFactory connectionFactory) {
        RabbitTemplate rabbitTemplate = new RabbitTemplate();

        rabbitTemplate.setConnectionFactory(connectionFactory);
        //设置开启Mandatory,才能触发回调函数,无论消息推送结果怎么样都强制调用回调函数
        rabbitTemplate.setMandatory(true);

        rabbitTemplate.setConfirmCallback(new RabbitTemplate.ConfirmCallback() {
            @Override
            public void confirm(CorrelationData correlationData, boolean ack, String cause) {
                logger.info("ConfirmCallback:     " + "correlationData：" + correlationData);
                logger.info("ConfirmCallback:     " + "ack：" + ack);
                logger.info("ConfirmCallback:     " + "cause：" + cause);
                //如果消息发送不成功,需要重新发送[组件内部处理，需要拿到发送的消息]
                if (!ack){
                    //将相关信息存数据库，定期重新发送
                }else{
                    //发送成功，如果是重新发送记录，那么删除记录
                }
            }
        });
        //如果正确达到消息队列就不执行
        rabbitTemplate.setReturnCallback(new RabbitTemplate.ReturnCallback() {
            @Override
            public void returnedMessage(Message message, int replyCode, String replyText, String exchange, String routingKey) {
                logger.info("ReturnCallback:     " + "message：" + message);
                logger.info("ReturnCallback:     " + "replyCode：" + replyCode);
                logger.info("ReturnCallback:     " + "replyText：" + replyText);
                logger.info("ReturnCallback:     " + "exchange：" + exchange);
                logger.info("ReturnCallback:     " + "routingKey：" + routingKey);
            }
        });

        return rabbitTemplate;
    }

        /**
         * 消费者设置手动确认模式
         */
    @Bean
    public RabbitListenerContainerFactory<?> rabbitListenerContainerFactory(ConnectionFactory connectionFactory){
        SimpleRabbitListenerContainerFactory factory = new SimpleRabbitListenerContainerFactory();
        factory.setConnectionFactory(connectionFactory);
        factory.setMessageConverter(new Jackson2JsonMessageConverter());
        factory.setAcknowledgeMode(AcknowledgeMode.MANUAL);
        return factory;
    }


    /**
     * dac只支持fanout类型交换机
     * **/
    @Bean
    public Queue eventDevice () {
        return new Queue(Constants.QUEUE_KEY_EVENT_DEVICE);
    }
    @Bean
    public FanoutExchange exchangeOfDac (){
        return new FanoutExchange("EventDevice");
    }
    @Bean
    public Binding bindingEventDevice(){
        return BindingBuilder.bind(eventDevice()).to(exchangeOfDac());
    }

}


```
