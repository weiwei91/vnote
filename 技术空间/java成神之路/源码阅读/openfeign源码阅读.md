# 前言
首先弄清楚，feign、openfeign、spring-cloud-openfeign的区别联系。
* netflix 公司维护的版本是feign。后面nerflix不在维护转由社区维护，openfeign。  
* Spring Cloud OpenFeign (类似组件)是声明式的服务调用工具，它整合了 Ribbon（负载均衡） 和 Hystrix（熔断、降级），拥有负载均衡和服务容错功能。默认是采用 
java.net.HttpURLConnection，每次请求都会建立、关闭连接，为了性能考虑，可以引入httpclient、okhttp作为底层的通信框架。

```
<!-- https://mvnrepository.com/artifact/com.netflix.feign/feign-core -->
<dependency>
    <groupId>com.netflix.feign</groupId>
    <artifactId>feign-core</artifactId>
    <version>8.18.0</version>
</dependency>

<!-- https://mvnrepository.com/artifact/io.github.openfeign/feign-core -->
<!-- https://github.com/OpenFeign/feign -->
<dependency>
    <groupId>io.github.openfeign</groupId>
    <artifactId>feign-core</artifactId>
    <version>10.5.1</version>
</dependency>

<!-- https://mvnrepository.com/artifact/org.springframework.cloud/spring-cloud-starter-openfeign -->
<!-- https://spring.io/projects/spring-cloud-openfeign -->
<!-- https://github.com/spring-cloud/spring-cloud-openfeign -->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-openfeign</artifactId>
    <version>2.1.2.RELEASE</version>
</dependency>
```

# 版本对应关系
直接看源码中pom文件，例如spring-cloud-openfeign-core 2.2.1 RELEASE 对应的openfeign版本>10.4.0,这样就跟github上的版本对应上了

[OpenFeign 源码地址](https://github.com/OpenFeign/feign)
