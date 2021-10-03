# Spring Boot 启动原理分析

## 重要注解

### @Configuration

```
<bean id="mockService" class="..MockServiceImpl">
    <propery name ="dependencyService" ref="dependencyService" />
</bean>
<bean id="dependencyService" class="DependencyServiceImpl"></bean>

等价

@Configuration
public class MockConfiguration{
    @Bean
    public MockService mockService(){
        return new MockServiceImpl(dependencyService());
    }
    
    @Bean
    public DependencyService dependencyService(){
        return new DependencyServiceImpl();
    }
}
```

### @ComponentScan
自动扫描并加载副歌条件的组件，最后将这些bean定义加载到ioc容器中，默认spring框架
从申明@ComponentScan 所在的package 进行扫描，因此是spingbooot启动类最好放在
root下，因为默认不指定basepaclages

### @EnableAutoConfiguration
借助@import 的支持，收集和注册特定场景相关的bean定义,作为复合注解，定义的关键信息如下

```
@SuppressWarnings("deprecation")
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Inherited
@AutoConfigurationPackage
@Import(EnableAutoConfigurationImportSelector.class)
public @interface EnableAutoConfiguration {
    ...
}

AutoConfigurationPackage注解：

static class Registrar implements ImportBeanDefinitionRegistrar, DeterminableImports {

        @Override
        public void registerBeanDefinitions(AnnotationMetadata metadata,
                BeanDefinitionRegistry registry) {
            register(registry, new PackageImport(metadata).getPackageName());
        }

它其实就是注册了一个bean定义，返回当前主程序的同级以及子集的包组件，这也是为什么我们要把
启动类放在最高级中

```

###  SpringFactoriesLoader详解





## 参考资料

https://www.cnblogs.com/shamo89/p/8184960.html