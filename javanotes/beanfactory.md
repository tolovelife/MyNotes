# BeanFactory

容器 也是把 我们的类 信息各种 保存住  底层 。所以使用时候 要用 它的 格式来保存住各种信息

![image-20250108184328198](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250108184328198.png)



***加锁步骤 重要**  （加锁后再从那两个地方找一次 真找不到 再从工厂找一次  找到放到 那两个地方  ）（3级缓存）

![image-20250108191109087](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250108191109087.png)



* **3级缓存是为了 解决循环依赖的问题**   （a 对象 有 b属性  b对象 有 a 属性  创建就不成了 ）（）

![image-20250108192224480](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250108192224480.png)



* **找组件（核心 ）**

![image-20250108192944747](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250108192944747.png)



* **内部大概流程** 

![image-20250108193054424](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250108193054424.png)