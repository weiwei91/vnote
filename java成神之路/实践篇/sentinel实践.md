# sentinel实践
## 引入依赖
 <!--服务容错-->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-sentinel</artifactId>
        </dependency>
## 整合控台台
```
    sentinel:
      transport:
        # 指定sentinel 控制台的地址
        dashboard: 10.19.134.69:8080
```

## 控制台面板
![](_v_images/1618470101_10608.png)

## 流控规则
![](_v_images/1618470228_2342.png)

## 限流规则配置
sentinal 使用

