## java面向对象有哪些特征

![image-20250109144716012](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109144716012.png)

（封装  继承 增加了代码的复用性   多态增加了代码的可移植性 健壮性  灵活性）



# ArrayList和 LinkList有什么不同

![image-20250109145405199](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109145405199.png)



# 高并发的集合有哪些

![image-20250109145907918](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109145907918.png)

![image-20250109145847009](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109145847009.png)

# JDK1.8新特性



* （内容很多   下面仅列最重要几点）
* lambda 表达式 
* stream 接口 
* 多重注解



# java 接口 和抽象 类区别

![image-20250109150735477](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109150735477.png)



* 除了语法上的不同  语义也不同 
* 抽象类 是用来描述一种概念性东西                   接口 用来描绘共有特征 
* ![image-20250109151004238](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109151004238.png)



# Hashcode 和 equals如何使用 

（在hashmap中 两个配合使用 ）

![image-20250109151524097](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109151524097.png)



# java代理的实现方式

静态 

* 动态代理 
* java自带 proxy  和 cglib
* **spring Aop 中两个代理都有**



proxy通过反射实现 

* ![image-20250109151921856](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109151921856.png)

cglib 通过 asm 实现 	

![image-20250109152044198](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109152044198.png)





# java中==和equals

![image-20250109152312408](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109152312408.png)

# java中的异常处理机制

![image-20250109154328206](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109154328206.png)

# 重写和重载 不同

![image-20250109154701267](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109154701267.png)



# String / StringBuffer/ StringBuilder 不同 

![image-20250109155805895](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250109155805895.png)



StringBuilder 比 String Bugffer 更加 效率高   但线程不安全  （synchornized	看源码 ）

