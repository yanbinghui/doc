# JAVA 网络IO 

## 模型

1. 阻塞I/O

 进程在调用recvfrom开始到它返回的整段时间内都是被阻塞的，所以叫阻塞I/O模型。
 需要从内核到用户空间的传输
 
2. 非阻塞I/O

 进程反复调用查看是否返回成功
 
3. I/O复用

 Linux提供select/poll，进程通过将一个或多个fd传递给select或poll系统调用，阻塞在select操作上，这样，select/poll可以帮我们侦测多个fd是否处于就绪状态。
 Linux还提供一个epoll系统调用，epoll使用基于事件驱动方式代替顺序扫描，因此性能更高。当有fd就绪时，立即回调函数rollback。
 
4. 信号驱动I/O

5. 异步 I/O

## java IO（BIO，NIO，AIO）

BIO、NIO、AIO适用场景分析: 

    BIO方式适用于连接数目比较小且固定的架构，这种方式对服务器资源要求比较高，并发局限于应用中，JDK1.4以前的唯一选择，但程序直观简单易理解。 

    NIO方式适用于连接数目多且连接比较短（轻操作）的架构，比如聊天服务器，并发局限于应用中，编程比较复杂，JDK1.4开始支持。 

    AIO方式使用于连接数目多且连接比较长（重操作）的架构，比如相册服务器，充分调用OS参与并发操作，编程比较复杂，JDK7开始支持。
    
NIO 需要selector，AIO使用AsynchronousServerSocketChannel.accept(this,new AcceptHandler());

1. Java IO
2. JAVA NIO 
 channel，buffer，异步IO，selector，DatagramChannel：UDP 
3. MappedByteBuffer(DirectByteBuffer)，RandomAccessFile

 从代码层面上看，从硬盘上将文件读入内存，都要经过文件系统进行数据拷贝，并且数据拷贝操作是由文件系统和硬件驱动实现的，理论上来说，拷贝数据的效率是一样的。
但是通过内存映射的方法访问硬盘上的文件，效率要比read和write系统调用高，这是为什么？

read()是系统调用，首先将文件从硬盘拷贝到内核空间的一个缓冲区，再将这些数据拷贝到用户空间，实际上进行了两次数据拷贝；
map()也是系统调用，但没有进行数据拷贝，当缺页中断发生时，直接将文件从硬盘拷贝到用户空间，只进行了一次数据拷贝。
所以，采用内存映射的读写效率要比传统的read/write性能高。

注：
普通read：磁盘->内核空间->用户空间缓冲区->应用程序
map：磁盘->用户空间->应用程序

4. 直接 I/O
注：磁盘->应用程序
把用户空间（页缓存）省略



## 参考

1. [Java I/O 模型的演进](https://waylau.com/java-io-model-evolution/)

2. [NIo、Bio、aio的原理及区别与应用场景](http://blog.csdn.net/u013851082/article/details/53942947)
3. [Java 网络IO编程总结](http://blog.csdn.net/anxpp/article/details/51512200)
4. [Java IO](http://blog.csdn.net/baobeisimple/article/details/1713797)
5. [Java 的新IO](http://blog.csdn.net/cowthan/article/details/53563206)
6. [NIO 系列](http://ifeve.com/overview/)
7. [RandomAccessFile vs FileChannel](http://blog.csdn.net/raintungli/article/details/7826904)
8. [深入浅出MappedByteBuffer](https://www.jianshu.com/p/f90866dcbffc)
9. [Linux 中直接 I/O 机制的介绍](https://www.ibm.com/developerworks/cn/linux/l-cn-directio/index.html)

