

——————————————————————————————————————————————————

* 与平常不同，获得的Map里面保存的Emp 实际不是Emp类 而是HashMap 
* 原因是mapper.xml中 resulttype 里面写的是map 类型 

![image-20241229150638404](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229150638404.png)

* 所以做如下更改   即使返回的是map 也这样写 result type这样就可以获取到原本类 
* ![image-20241229150957094](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229150957094.png)



——————————————————————————————————————————————————

* 





——————————————————————————————————————————————————

* 一对一 关联查询    <association > 标签   （原本的bean 类中也要 要加一个customer 对应类 属性）	

* ![image-20241229153819492](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229153819492.png)

  

* 一对多 的情况   <collection  property     ofType    ~
* ![image-20241229154928313](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229154928313.png)



——————————————————————————————————————————————————

mybatis 分步查询 （就可以不使用连表查询 ）



即 写两个select  xml 然后 此列中 用<collection  连接 启动 第二次查询 起来  ，若连接中有多个传参 可以 { cid=id, ~~~} 

![image-20241229160916103](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229160916103.png)

——————————————————————————————————————————————————



* 延迟 加载 

* 

* ```properties
  # 开启 懒加载
  mybatis.configuration.lazy-loading-enabled=true
  mybatis.configuration.aggressive-lazy-loading=false
  ```



* 分布查询时候 有时候只用到 前面 的部分 后面 部分暂时不用查询  开启此功能 效率更高   





——————————————————————————————————————————————————

* 



* <trim> 标签更强大  prefix   属性   和  prefixOverrides 前缀覆盖" all || or"  属性   sufferfixOverrides 

![image-20241229192623303](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229192623303.png)

* suffix 中 像字符串 但仍然是占位符  获取 穿过来的id （也可以 末尾写 硬where）

![image-20241229192957201](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229192957201.png) 

* 上面if 是判断走不走 哪个   下面 是 只走一个

![image-20241229193440746](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229193440746.png)



* foreach 标签 

  * 当传入参数 是列表数  不能list(0) list(1)  因为不确定用户会传哪些参数  用foreach 来遍历参数列表
  * <foreach>    item  separetor open   
  * ![image-20241229194428458](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229194428458.png)

  	* 批量插入
  	*  要允许 一次发送多个sql 执行，并用;隔开 
  	* spring.datasource.url=jdbc:mysql://localhost:3306/mybatis?allowMultiQueries=true
  	* 

![image-20241229200229392](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229200229392.png)

![image-20241229200345389](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229200345389.png)



—————————————————————————————————————————————


——————————————————————————————————————————————————

* sql 复用片段     xml 转移字符      

![image-20241229202019088](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229202019088.png)





* 事务的缓存机制 
  * ![image-20241229202758096](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229202758096.png)

​	



——————————————————————————————————————————————————

* mybatis 插件  

  * 分页插件 
  * 1.创建分页对象  （记得在 xml加bean ）
  * ![image-20241230105756984](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241230105756984.png)

  * ![image-20241230110725491](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241230110725491.png)

  * 分页对象可设置属性 下面 是设置properties ，先写 properties 类 中设置属性 
  * 

​	![image-20241230111915673](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241230111915673.png)

* ​	
* 将现在的分页数据 封装成类  发送到前端 	![image-20241230112146558](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241230112146558.png)