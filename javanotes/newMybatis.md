* 驼峰命名规则映射( 比 别名方便)

* 在application.properties 中

* ```
  mybatis.configuration.map-underscore-to-camel-case=true
  ```

![image-20241229131310434](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229131310434.png)

![image-20241229131127699](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229131127699.png)



${} 和 #{} 的区别  一个是预编译 一个是拼接 

![image-20241229132639103](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229132639103.png)

————————————————————————————

* 单参数

![image-20241229134311300](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229134311300.png)

对象属性值，直接获取  例如下面的传参Emp e，在Empmapper.xml 中 直接用属性名 不要带e



* 多参数 新版mybatis 支持 直接#{}  老版本 需要 @Param("对应") 参数

![image-20241229134711785](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229134711785.png)

——————————————————————————————————————————————————

* 与平常不同，获得的Map里面保存的Emp 实际不是Emp类 而是HashMap 
* 原因是mapper.xml中 resulttype 里面写的是map 类型 

![image-20241229150638404](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229150638404.png)

* 所以做如下更改   即使返回的是map 也这样写 result type这样就可以获取到原本类 
* ![image-20241229150957094](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229150957094.png)



——————————————————————————————————————————————————

* resulttype 自定义结果封装类型  <id > 主键 < result  coloum =?  property =? >	 resultmap =？ 

![image-20241229151843797](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229151843797.png)





——————————————————————————————————————————————————

* 一对一 关联查询    <association > 标签   （原本的bean 类中也要 要加一个customer 对应类 属性）	
* ![image-20241229153819492](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229153819492.png)

* 对应查询的sql 语句 （复习 ！！！！）

![image-20241229154045842](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229154045842.png)

* 一对多 的情况   <collection  property     ofType    ~
* ![image-20241229154928313](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229154928313.png)



——————————————————————————————————————————————————

mybatis 分步查询 （就可以不使用连表查询 ）



即 写两个select  xml 然后 此列中 用<collection  连接 启动 第二次查询 起来  ，若连接中有多个传参 可以 { cid=id, ~~~} 

![image-20241229160916103](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229160916103.png)

——————————————————————————————————————————————————

spring 中 启动网页  返回 json 信息  （还没讲解到）

![image-20241229163457921](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229163457921.png)

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

* 动态sql 
* ![image-20241229191636443](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229191636443.png)

* 用where 容易 sql 错误 因为传参总想不到一些奇怪的 sql注入  



![image-20241229192106391](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229192106391.png)



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



——————————————————————————————————————————————

* 开启事务 

* 

* ```
  @EnableTransactionManagement
  @SpringBootApplication
  public class AlltestApplication {
  
      public static void main(String[] args) {
         SpringApplication.run(AlltestApplication.class, args);
      }
  
  }
  ```

* 上面 是开启事务 功能  后面在具体接口前面加上加上  @ Transactional 

* 

* ```
  @Transactional
  boolean update(Emp emp);
  ```

* 注： 分布式项目情况下 ，分布式事务 很多不支持 SQL批量操作 的回滚



——————————————————————————————————————————————————

* sql 复用片段     xml 转移字符      

![image-20241229202019088](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229202019088.png)



![image-20241229202305432](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229202305432.png)



* 事务的缓存机制 
  * ![image-20241229202758096](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241229202758096.png)

​	



_——————————————————————————————————————————————————

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