# spring推荐注入方式

# 前言
了解spring注入方式，已经方式间有何不同，为什么推荐构造器注入方式？
- 构造器
- Setter
- 属性（@Autowired）

## 属性（@Autowired）优缺点
优点
1. 代码简单明了，注入简单（只需要@Autowired 或者 @Resource）
缺点
1. 破坏单一职责原则
2. 非强制依赖，容易产生NPE
3. 会出现循环依赖的隐患
4. 对单元测试不友好，需要初始化整个Sping环境
## 构造器注入优缺点
优点：
1. 强制依赖，尽早暴露NPE
2. 单元测试友好，不需要初始化整个Spring环境
缺陷：
1. 代码冗余，阅读不方便（lombook解决）


## @Autowired  和 @Resource 区别
- 相同点：
1.都可以用于依赖注入
- 不同点
- 1.@Resource 默认注入byName，属于jdk提供（javax.annotation.Resource）
- 2.@Autowired注入byType，属于spring提供（org.springframework.beans.factory.annotation.Autowired）

```
理解byName 和byType的区别：
    <bean id="userServiceImpl"
            class="cn.com.bochy.service.impl.UserServiceImpl"
            autowire="byName">
       </bean>  
   <bean id="userDao"                                         
             class="cn.com.bochy.dao.impl.UserDaoImpl">
</bean>
第一种是ByName  第二种是ByType（class的类型）

```


## @Service @Compoent @Controller@Repository
理解起来也很简单，四个注解都是用于向spring容器中注入bean，但是都侧重点不同
- @Repository 主要用于dao层
- @Service 主要用于逻辑层
- @Controller主要用于mvc的展现层
- @Compoent主要用于自定义的bean
方便以后项目的维护和开发


## @RequiredArgsConstructor 和 @RequiredArgsConstructor(onConstructor = @__(@Autowired)) 区别

onConstructor 是其中的指定属性，现在已经被废弃