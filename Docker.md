![image-20250103182944516](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250103182944516.png)



* 映射端口   

![image-20250104140754259](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250104140754259.png)



* 交互命令修改   首页文件 
* ![image-20250104140903292](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250104140903292.png)



提交为一个镜像    保存为一个文件 （可以是 tar 压缩包 ） 加载使用这个压缩包 成镜像

![image-20250105205257135](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250105205257135.png)



* 推送仓库    docker  login  docker tag (重新打标签 )  docker push  ~~~ 新标签名字 
* ![image-20250105210115611](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250105210115611.png) 



* 目录挂载 （挂载后 以外部文件为主  外部为空 里面文件即使有也会清空） 
* ![image-20250105213728730](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250105213728730.png)



* 卷映射   （挂载后 之前数据 会同步过来 不清空 	）
* ![image-20250105220019265](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250105220019265.png)

![image-20250105220356555](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250105220356555.png)

 	

* 内部网络集群
* ![image-20250106090905988](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250106090905988.png)

自动在docker0 网络  可自己创建网络 （这样域名就是容器名 方便访问 ）