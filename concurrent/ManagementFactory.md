## ManagementFactory

anagementFactory是一个为我们提供各种获取JVM信息的工厂类，使用ManagementFactory可以获取大量的运行时JVM信息，比如JVM堆的使用情况，以及GC情况，线程信息等，通过这些数据项我们可以了解正在运行的JVM的情况，以便我们可以做出相应的调整。本文将基于ManagementFactory，介绍如何通过ManagementFactory获取一些运行时的JVM信息，下面首先展示了ManagementFactory的类图，可以看出它提供了大量的工厂方法，使得我们可以通过调用这些方法来获取运行时的相关Bean，通过这些Bean就可以获取到我们想要的数据：

![方法列表](https://upload-images.jianshu.io/upload_images/7853175-0b1a6426d60a7132.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)


#### 参考


[Java ManagementFactory解析](https://www.jianshu.com/p/5d854245051d)
