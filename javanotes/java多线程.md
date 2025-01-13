![image-20250111200814935](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250111200814935.png)



* **三种创建方式 	Thread class 	Runnable interface	Callable interface** 



# Thread 类

* 继承 Thread 类
* 重写run方法
* 实例对象 启动实例start方法
  * （调用实例run方法 是传统的 	调用start才是多线程 ）
  * ![image-20250111201844665](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250111201844665.png)



* 代码实现
* 先写个下载工具类 
* 线程类中用run方法中实例工具类 调用下载方法（网络路径由类构造器传入）
* 在主线程中实例多个线程类      线程类调用start（）方法执行run方法 
* ![image-20250111203146622](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250111203146622.png)







* # Runnable 接口 

* （与thread 类似 最后实现 调用  丢给一个new Thread类 调用run 方法）

* ![image-20250111204011716](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250111204011716.png)