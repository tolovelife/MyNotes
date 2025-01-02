![image-20241230135828846](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241230135828846.png)





![image-20241230194255372](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241230194255372.png)



* 请求限定 常用 produces  和 consumes  规定其数据格式 
*   ![image-20241230195116793](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241230195116793.png)



————————————————————————————————————————————————————————————



* springMVC请求 
* ![image-20241230202644983](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241230202644983.png)

![image-20241230203028546](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241230203028546.png)



*  springMVC可将得到的数据封装为 pojo类 
* ![image-20241230204833742](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241230204833742.png)

对象嵌套 级联封装 

![image-20241231143419053](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231143419053.png)



————————————————————————————————————————————————————————————

* json 数据传输 与普通法不同  @RequestBody 标签 
* ![image-20241231145036340](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231145036340.png)



* ![image-20241231145107399](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231145107399.png)







* 当前端 给出 图片或视频 资源时候  必须要用 @RequestParm 
* 然后 MultipartFile  类型    进行操作 各种 方法 比如 
* headerFile.transferTo(new File("D:\\ img \ "));  （注意 这里得文件夹需要先判断 若无自己先创建 要不然会报错 （即他本身没有新创建文件夹功能 ））
* springMVC 默认文件上传大小 1MB 更改需要 在 application.properties  里面写 语句 spring.servlet.multipart.~~
* ![image-20241231150744688](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231150744688.png)





## 响应处理 ：返回json 

* ![image-20241231153506858](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231153506858.png)



* 响应下载 模板 （基本 固定） 
  * 1 读流
  * 2url编码 
  * 3.InputStreamResource 防溢出
  * 4 return  .ok().contentType().contentLength().header("内容处理 方式").body( 内容 )
* ![image-20241231154709077](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231154709077.png)



* thymeleaf  测试页面取值 
* ![image-20241231174728732](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231174728732.png)

![image-20241231175256756](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231175256756.png)

SpringBoot 支持thymeleaf    不支持jsp 

_—————————————————————————————————————————————————————————————



Restful 风格 （ 万物皆资源，请求路径名像文件夹一样写）

![image-20241231192930133](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231192930133.png)

* RequestMapping (value ="/employee/**{ id }**",method = RequestMethod.GET )

* 上面简略写 就是 GetMapping  (value ="/employee/{id}")
* @Pathvariable（"id")  是 获取路劲中参数





返回统一一个 类 包含 状态码  提示信息   数据  

写一个静态 成功方法  ，（固定的东西 写类中 省得重复）

![image-20241231200941143](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231200941143.png)





默认跨域 请求在浏览器中 不可以 ，非浏览器可以（即斜杠 前面要一摸一样 ）



![image-20241231201752590](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231201752590.png)

若想要跨域请求 需要后端加上那个注释就可以 





* pathvariable 其他用法     （最后一个支持正则约束 ）
* ![image-20241231202516824](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231202516824.png)





## HandlerInterceptor 拦截器 



springMVC 中 写配置类  实现

* ![image-20241231204130310](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231204130310.png)

![image-20241231204302914](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231204302914.png)

* WebMvcConfigurer 





handlerInterceptor 执行顺序     

preHandle    依次 

![image-20241231211113557](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20241231211113557.png)







————————————————————————————————————————————————————————————



# 异常处理 @ExceptionHandler



声明式注解异常



* ![image-20250101135648437](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101135648437.png)



多个异常 可以一个方法处理多种异常  也可以 一个方法 直接抛出 throwable 



(但是如果有精准异常 处理 ，那精准异常 方法处理优先)

```  java
@ExceptionHandler( Throwable.classs)
public R handleException (Throwable ex){ 
	return R.error( 500,"异常"+ ex.getMessage());
}
```





![image-20250101140740636](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101140740636.png)





* 全局异常 处理 

* ``` java
  @RestControlllerAdvice 
  public class GlobalControllerAdvice{ 
  	
      @ ExceptionHandler (Exception.class )
  	public R error(Exception ex ){
          return R.error( 500," 异常是 "+ ex.getmessage() )
  }
  
  }
  ```

* 

  

* 业务异常特定写一个类   （与系统异常区分 ）

  *  业务异常 通常 是大型的  ，为了后面维护方便更改 业务异常类的 封装一下 异常码 和 异常 信息 成枚举类  （不固定写死码 ）

    ![image-20250101150902624](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101150902624.png)

![image-20250101151201363](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101151201363.png)



![image-20250101151326532](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101151326532.png)



* 业务抛出异常 让全局异常管理器 来 接管  发送 消息 
* ![image-20250101151456165](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101151456165.png)



![image-20250101152054554](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101152054554.png)





# 数据校验  JSR303





![image-20250101154337464](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101154337464.png)

``` java
@NotBlank (message ="姓名不可为空")

@NotNUll( message = "~~~~")

@Email   @Max  @Min 
```





![image-20250101154516564](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101154516564.png) 



为了 拿到错误   紧跟 BindingResult  result 



``` java
public r add ( @RequestBody  @Valid Employee employee ,   BindingResult result )
```



![image-20250101154904518](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101154904518.png)







* 上述 在控制层里面写 显得 麻烦   直接 只添加 @Valid 注解 ，若验证失败 会报验证失败 异常     **所以在全局 异常类中加 上这个异常精确 处理方法 即可** 

``` java
 @ExceptionHandler(value =MethodArgumentValidException.class)
public R  ~ ( MethodArgumentValidException ex ){ 
	ex.getBindingResult();
 
}
```





* ![image-20250101160056656](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101160056656.png)



* 想要实现特定 验证 如 性别 必须 为男 或 女   
* @Patten( value =~~~)  regex 表达式
* 或者自己写 自定义注解 实现    annation 包下 实现  @interface  要实现validator  实现类  （这才是真正有用的部分 ）



国际化 i18s  internationalization    根据请求头 中的 语言环境 配置 不同 messages.properities     动态返回不同语言的版本  了解即可 	

![image-20250101163223484](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101163223484.png)





* bean 分层 因为要与 数据库 交互  前端 交互  后端交互  验证  各种 注解  ，且要脱敏 所以 要分 VO  各种 O层  pojo  po (persistent  object  持久层对象 )



比如数据库里有身份证 手机号 敏感信息 返回 前端 就不可以 全返回 

 

下面是不同层的bean  转换 对象  （当然强转不了，BeanUtils.copyProperties  

 ![image-20250101170538272](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101170538272.png)





# 接口文档



swagger  和 knife4 j (在swagger 增强版 )

导包 

在 applicationcontext.yaml  中 配置 改 扫描包 路径就可 

在每个参数 或者 方法 添加 前端可以理解的 注解 



@Schema (description =" ~~~" ) 类上面注解 

@ operation (summary = " ~~~~") 方法上 注解 



@Parameters ( )



![image-20250101172517335](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250101172517335.png)





## 日期转化json 格式 

默认的 日期格式传送并不像日常写的这样 

在 表示层上日期属性上面标注  @JsonFormat (pattern ="yyyy-MM-dd	HH:mm:ss",timezone= "GMT+8")

![image-20250102111147484](C:\Users\ZhuanZ\AppData\Roaming\Typora\typora-user-images\image-20250102111147484.png)