SpringBoot 特性





![image-20250102195703133](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250102195703133.png)



* 面试重点 
* ![image-20250102201831985](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250102201831985.png)





springMVC工作底层基本流程

![image-20250102211323317](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250102211323317.png)

![image-20250102211346151](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250102211346151.png)





.yaml (比properties 更加层次清楚 )

![image-20250103140857094](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250103140857094.png)



示例把bean 类放进容器里 面 ，在yaml中 放置属性 

![](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250103141733104.png)

上面日期格式不对 ，最后不能 识别 ，应写成 2019/02/02 12：00：00

属性是数组和 对象 的 形式可以  和 json 处理一样 。[ ]   { }



properties 和yaml 都是用来配置  如果冲突 properties 优先 



* 如果想用代码配置一些项  也可以自己来创建启动   

  ```
  new SpringApplication (Springboot~~~.class);
  
  设置一些自定义 
  ~.run()
  ```

  

* ![image-20250103144343248](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250103144343248.png)



## 日志框架



springboot 默认用 SLF4j（日志门面   ）  + Logback (日志实现 )			---> 接口和实现

![image-20250103152631957](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250103152631957.png)



* @Slf4j   注释 自动生成一个 LoggeFactory.getLogger(~~.class)   下面直接引用 log 
* ![image-20250103152843267](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250103152843267.png)

* 会用 log 打印不同级别 的日志 来 代替 sout
* 

![image-20250103154620347](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250103154620347.png)



* ##### 日志分组 

* 一个个不好管理 ，可放置一个组内 

* ``` 
  logging.group.biz =com.~~~~~
  logging.level.biz= debug 
  ```

* 

* ![image-20250103154928233](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250103154928233.png)





* 日志文件 -文件输出 
* logging.file.name                        logging.file.path  在properties 中 配置   路径（最后是文件夹 ）或 文件名字 就会输出到文件 



* 日志归档  （动态切割） 
* 可在spring properties 下面 改动 也可以  自己用原生框架的配置  改动  （spring 的灵活性）
* Logback     Logback.xml/logback-spring.xml
* Log4j2          Log4j2.xml
* jdk                 logging.properties
* ![image-20250103161405973](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250103161405973.png)



##### 环境隔离 

![image-20250103172328396](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250103172328396.png)



* 外部化配置   （方便修改 而不用改包 新打包 ）
* ![image-20250104154342330](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250104154342330.png)

越外围越远     优先级最高 即 java  -jar ~~.jar  --  ~~   命令行配置优先级最高。

激活优先    》	外部优先   》 内部 





## # 单元测试

![image-20250104155806983](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250104155806983.png)

* 断言注解 
* ![image-20250104160734377](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250104160734377.png)

用maven test 即可测试所有方法  根据断言判断是否真的符合了 业务得 最后结果的正确测试 



* actuator  可观测性 
* 导入场景即可 

![image-20250104162753882](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250104162753882.png)

有模块十分方便 查看相关 信息 url即可 

![image-20250104163520689](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250104163520689.png)

![image-20250104163617219](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250104163617219.png)







* springboot 生命周期监听    各个阶段



![image-20250104165034060](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250104165034060.png)



![image-20250110111841122](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250110111841122.png)



* 事件驱动开发 

原本代码是 同步阻塞式   硬编码形式     加减业务 要增删调用

![image-20250110112449062](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250110112449062.png)

* 事件开发 把传统 直接调取各个 服务  转而 发布一个事件    需要的服务在自己内部 注册事件即可 （还可以开启@Async @EnableAsync 异步 效率更高）
* 写事件类 
* ![image-20250110113611077](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250110113611077.png)
* ![image-20250110113503176](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250110113503176.png)

* 
* 
* 
* meta-inf 中 spring.factories   和  放容器 两种 方法   

![image-20250104165137569](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250104165137569.png)



* 自动配置原理 （）
* ![image-20250110114440897](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250110114440897.png)



![image-20250110114813235](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250110114813235.png)





* 自定义starter

自己写好的项目  让别的项目也能够使用

（1.去掉main方法 留下有用组件   2依赖于基础starter    ）

![image-20250110134621004](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250110134621004.png)



* ![image-20250110135502470](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250110135502470.png)

* spring只扫描主程序所在的包
* 解决方法：写个配置类放到容器中
* 了解springboot 底层配置原理就知道 怎么弄 

![image-20250110150415004](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250110150415004.png)





* 最后要掌握spring的源码

![image-20250110150213018](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250110150213018.png)