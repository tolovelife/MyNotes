
1.导入依赖包


      <dependency>
            <groupId>org.aspectj</groupId>
            <artifactId>aspectjweaver</artifactId>
            <version>1.9.4</version>
            <scope>runtime</scope>    
        </dependency>


        <dependency>
            <groupId>org.aspectj</groupId>
            <artifactId>aspectjrt</artifactId>
            <version>1.9.4</version>
        </dependency>
  <!--      1. 缺少 AspectJ 运行时库 (aspectjrt)
        @Aspect 注解是来自 AspectJ 的 aspectjrt 库，而 aspectjweaver 主要用于 AspectJ 编织的支持。如果你仅仅引入了 aspectjweaver，但缺少了 aspectjrt，则会导致无法识别 @Aspect 注解。

        解决方法：
        你需要同时引入 aspectjrt 和 aspectjweaver 两个依赖。-->用于第一次弄@Aspect 注解找不到




    三种方式 :1.注解方式  2.自定义类实现AOP(切面自定义)  3.用Spring 的接口实现

    重要点: 在xml 中配置bean 以及 <aop:config>        使用注解需要配置<aop:aspectj-autoproxy >

    例如:    这是自定义切面类配置
                <aop:config>
    <!--        自定义切面   是定义类-->
        <aop:aspect ref="div">
            <!--切点 -->
            <aop:pointcut id="point" expression="execution(* com.kuang.service.UserServiceImpl.*(..))"/>
    <!--            通知-->
            <aop:before method="before" pointcut-ref="point"></aop:before>
            <aop:after method="after" pointcut-ref="point"></aop:after>


        </aop:aspect>
    </aop:config>