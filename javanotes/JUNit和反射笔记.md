#   Junit 单元测试 

1.白盒测试  ：需要写代码，关注代码走的流程
2.黑盒 ：给输入得到想要的输出即可。

        *步骤 ：
            1.定义一个测试类（测试用例）
                * 类名：       如CalculatorTest 
                * 包名        如com.ko.test
            2.定义测试方法 ：可以独立运行
               * 方法名：        如testadd()
                *返回值：void
                *参数列表（空参）
            3.给方法加上@Test  (使其让方法可以独立运行而不依赖于main)

            4.添加JUNit 依赖 (导包导类)

        *判定结果
            *用assert 断言操作来判定结果正确 （而不用sout输出肉眼判断）

~~~
        int result = clac.add(1, 3);
        Assert.assertEquals(3,result);
        
~~~


       * @Before
    public void init(){
        //该方法测试方法前执行    资源申请
    }
        * @After
    public void close (){
        //该方法测试方法后执行       释放资源
    }
            
        
# 反射 ：框架设计的灵魂
    *框架： 半成品软件 。简化开发。

    *反射：将类的各个组成部分封装为其他对象，这就是反射机制
        *好处:可以在程序运行中，操作对象。


    *获取class 对象的方式:
        1.在第一阶段：Class.forname("全类名")：   将字节码文件加载到内存，返回class对象  (包名+类名)
            *多数用于配置文件
        2.在第二阶段：类名.class：      通过类名属性class获取
            *多用于传参
        3.  三   ： 对象名.getClass().
            *多用于对象的获取字节码方式


    *Class 对象功能 
            *获取功能
                1.获取成员变量们

                    * Filed[] getFileds()       (获取public 的方法)
                    * Filed[] getFileds(string name)

                     *Filed[] getDeclaredFileds()       (获取所有的方法 甚至包括private(使用前忽略安全检查) )
                    *Filed[] getDeclaredFileds(string name)

                3.获取方法们

                   
                2.获取构造方法们
                    *Constructor<?>getConstructors()
                    *Constructor<T>getConstructor(String name)                                                    
    
                4.获取类名


        * 结论：
            同一个字节码文件（*.class ）在程序运行中只会被加载一次 ，三种获取对象方式都是指向同一个。



    *Filed :成员变量 

            *获取值      Filed a=personClass.getFiled("a")        a是Filed 对象不是真正的值     value=a.get(new Person)
            *修改值

    *Constructor  :构造方法

        *创建对象：
            *T newinstance (Object ~ )
            * 如果使用空参数构造方法创建对象，操作简化为：Class 对象的 new instance方法 


    *Method :成员方法
        *执行方法
            
            Object invocke(Object ~ )
        *获取方法的名称    

            getname

 * 案例
   * 需求 写一个”框架“，不改变代码前提下，可以创建任意类的对象，并执行其中方法
        * 实现：
          * 1.配置文件
          * 2.反射
        * 步骤：
          * 1.将需要创建的对象的全类名和方法 定义在配置文件中
          * 2.在程序中加载配置文件
          * 3.使用反射技术加载类文件进内存
          * 4.创建对象 执行方法 
    

    

    ``` 
        Properties pro= new Properties();


        ClassLoader classLoader = Reflectoranli.class.getClassLoader();     //获取类加载器

        InputStream resourceAsStream = classLoader.getResourceAsStream("pro.properties");

        pro.load(resourceAsStream);

        String classname = pro.getProperty("className");
        String method = pro.getProperty("methodName");

        Class aClass = Class.forName(classname);

        Object o = aClass.newInstance();
        Method m = aClass.getMethod(method);
        m.invoke(o);



        