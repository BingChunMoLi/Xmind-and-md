# 架构
<!--![Spring架构图](https://docs.spring.io/spring-framework/docs/5.0.0.RC2/spring-framework-reference/images/spring-overview.png)-->
![Spring架构图](https://cdn.jsdelivr.net/gh/LeagueJinx/img/20210417183545.png)
1. Spring IOC:
    1. spring-beans
    2. spring-core
    3. spring-context
    4. spring-expression
2. spring AOP:
    1. spring-aop
    2. spring-aspects
3. spring TEST:
    1. spring-test
4. spring 数据访问:
    1. spring-jdbc
    2. spring-orm
    3. Spring-ox(xml)m
    4. spring-jms
5. spring 事务:
    1. spring-tx
6. spring web:
    1. spring-web
    2. spring-websocket
    3. spring-webmvc
    4. spring-webmvc-portlet

# spring 容器细节:
- IOC(控制反转)和DI(依赖注入)

1. 自动装配(autowire)
    1.  byName
    2.  byType
    3.  constructor
        1. 按照构造器进行赋值:
            1. 先按照有参构造器的类型进行装配(成功就赋值):没有就直接为组件装配null
            2. 如果按照类型找到多个，参数名作为id继续匹配，结果同上
            3. 不会报错
2. SpEL
    1. 字面量计算
    2. 引用其他bean的属性值
    3. 引用其他bean
    4. 调用非静态方法（"#{对象名.方法名()}"）
    5. 调用静态方法（"#{T(java.util.UUID).randomUUID().toString()"}）,
3. XML配置文件:
    1. <context:component-scan />
        1. use-default-filters="false" 默认为true，false时禁止默认的排除规则
        2. <context:exclude-filter/>
            1. type属性：
                1. annotation 根据注解
                2. assignable 具体类
                3. aspectj aspectj表达式
                4. custom 自定义TypeFilter实现方法
                5. regex 正则表达式
4. 注解
    1. @scope控制单例多例
    2. @Autowire 优先按类型，如果有多个再按id名称
    3. @Qualifier 配合autowire指定一个id名称注入
    4. @Inject 也是自动装配,再EJB环境下使用
