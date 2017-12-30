# ClassLoader工作机制

## 一、概念

ClassLoader是用来动态的加载class文件到虚拟机中，并转换成java.lang.class类的一个实例，每个这样的实例用来表示一个java类，我们可以根据Class的实例得到该类的信息，并通过实例的newInstance()方法创建出该类的一个对象，除此之外，ClassLoader还负责加载Java应用所需的资源，如图像文件和配置文件等。

ClassLoader类是一个抽象类。如果给定类的二进制名称，那么类加载器会试图查找或生成构成类定义的数据。一般策略是将名称转换为某个文件名，然后从文件系统读取该名称的“类文件”。ClassLoader类使用委托模型来搜索类和资源。每个 ClassLoader实例都有一个相关的父类加载器。需要查找类或资源时，ClassLoader实例会在试图亲自查找类或资源之前，将搜索类或资源的任务委托给其父类加载器。  

注意：程序在启动的时候，并不会一次性加载程序所要用的所有class文件，而是根据程序的需要，通过Java的类加载机制来动态加载某个class文件到内存中。

## 二、JVM平台提供三层classLoader

1. Bootstrap classLoader：采用native code实现，是JVM的一部分，主要加载JVM自身工作需要的类，如java.lang.*、java.uti.*等； 这些类位于$JAVA_HOME/jre/lib/rt.jar。Bootstrap ClassLoader不继承自ClassLoader，因为它不是一个普通的Java类，底层由C++编写，已嵌入到了JVM内核当中，当JVM启动后，Bootstrap ClassLoader也随着启动，负责加载完核心类库后，并构造Extension ClassLoader和App ClassLoader类加载器。

2. ExtClassLoader：扩展的class loader，加载位于$JAVA_HOME/jre/lib/ext目录下的扩展jar。

3. AppClassLoader:系统class loader，父类是ExtClassLoader，加载$CLASSPATH下的目录和jar；它负责加载应用程序主函数类。

## 三、JVM加载class文件到内存有两种方式

1. 隐式加载：不通过在代码里调用ClassLoader来加载需要的类，而是通过JVM来自动加载需要的类到内存，例如：当类中继承或者引用某个类时，JVM在解析当前这个类不在内存中时，就会自动将这些类加载到内存中。

2. 显示加载：在代码中通过ClassLoader类来加载一个类，例如调用this.getClass.getClassLoader().loadClass()或者Class.forName()。

## 四、ClassLoader加载类的过程

1. 找到.class文件并把这个文件加载到内存中

2. 字节码验证，Class类数据结构分析，内存分配和符号表的链接

3. 类中静态属性和初始化赋值以及静态代码块的执行

## 五、自定义类加载器

1、为何要自定义类加载器？

　JVM提供的类加载器，只能加载指定目录的jar和class，如果我们想加载其他位置的类或jar时，例如加载网络上的一个class文件，默认的ClassLoader就不能满足我们的需求了，所以需要定义自己的类加载器。

2、如何实现自定义的类加载器？

　我们实现一个ClassLoader，并指定这个ClassLoader的加载路径。
 
## 六、实现类的热部署

1、什么是类的热部署？

　　所谓热部署，就是在应用正在运行的时候升级软件，不需要重新启用应用。

　　对于Java应用程序来说，热部署就是运行时更新Java类文件。在基于Java的应用服务器实现热部署的过程中，类装入器扮演着重要的角色。大多数基于Java的应用服务器，包括EJB服务器和Servlet容器，都支持热部署。

　　类装入器不能重新装入一个已经装入的类，但只要使用一个新的类装入器实例，就可以将类再次装入一个正在运行的应用程序。

2、如何实现Java类的热部署

　　前面的分析，我们已经知道，JVM在加载类之前会检查请求的类是否已经被加载过来，也就是要调用findLoadedClass方法查看是否能够返回类实例。如果类已经加载过来，再调用loadClass会导致类冲突。

　　但是，JVM判断一个类是否是同一个类有两个条件：一是看这个类的完整类名是否一样(包括包名)，二是看加载这个类的ClassLoader加载器是否是同一个(既是是同一个ClassLoader类的两个实例，加载同一个类也会不一样)。

　　所以，要实现类的热部署可以创建不同的ClassLoader的实例对象，然后通过这个不同的实例对象来加载同名的类。
  
  
### 应用服务器的热部署

由于在应用程序执行过程中，已经new了出对象（包括静态对象，未来需要创建的对象）。应该会有一个监听程序，发现类的class文件有变化，然后触发一个新的类加载器，加载该类。在应用服务器中有一个类管理器，它有一个需要使用的类的列表，在该列表里面，用新类将旧类的引用替换。

