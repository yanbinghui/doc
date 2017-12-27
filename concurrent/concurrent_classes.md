## BlockingQueue

 - ArrayBlockingQueue
 环状队列
 - DelayQueue
 通过delay函数可以设置延迟时间
 - LinkedBlockingQueue
 LinkedBlockingQueue 类实现了 BlockingQueue 接口。
 LinkedBlockingQueue 内部以一个链式结构(链接节点)对其元素进行存储。如果需要的话，这一链式结构可以选择一个上限。如果没有定义上限，将使用 Integer.MAX_VALUE 作为上限。
 - PriorityBlockingQueue
 PriorityBlockingQueue 类实现了 BlockingQueue 接口。
PriorityBlockingQueue 是一个无界的并发队列。它使用了和类 java.util.PriorityQueue 一样的排序规则。你无法向这个队列中插入 null 值。
所有插入到 PriorityBlockingQueue 的元素必须实现 java.lang.Comparable 接口。因此该队列中元素的排序就取决于你自己的 Comparable 实现。
 - SynchronousQueue
 SynchronousQueue 是一个特殊的队列，它的内部同时只能够容纳单个元素。newCachedThreadPool用到了它
 
## BlockingDeque

BlockingDeque 接口继承自 BlockingQueue 接口。这就意味着你可以像使用一个 BlockingQueue 那样使用 BlockingDeque。如果你这么干的话，各种插入方法将会把新元素添加到双端队列的尾端，而移除方法将会把双端队列的首端的元素移除。正如 BlockingQueue 接口的插入和移除方法一样。

 - LinkedBlockingDeque
 LinkedBlockingDeque 类实现了 BlockingDeque 接口。
deque(双端队列) 是 "Double Ended Queue" 的缩写。因此，双端队列是一个你可以从任意一端插入或者抽取元素的队列。(译者注：唐僧啊，受不了。)
LinkedBlockingDeque 是一个双端队列，在它为空的时候，一个试图从中抽取数据的线程将会阻塞，无论该线程是试图从哪一端抽取数据。
 
## ConcurrentMap

 - ConcurrentHashMap
 - ConcurrentNavigableMap（interface）
     1. headMap(), tailMap(), subMap()
     
     2. ConcurrentSkipListMap（实现）
 
## CountDownLatch

java.util.concurrent.CountDownLatch 是一个并发构造，它允许一个或多个线程等待一系列指定操作的完成。
CountDownLatch 以一个给定的数量初始化。countDown() 每被调用一次，这一数量就减一。通过调用 await() 方法之一，线程可以阻塞等待这一数量到达零。

## CyclicBarrier

java.util.concurrent.CyclicBarrier 类是一种同步机制，它能够对处理一些算法的线程实现同步。换句话讲，它就是一个所有线程必须等待的一个栅栏，直到所有线程都到达这里，然后所有线程才可以继续做其他事情。

## Exchanger

java.util.concurrent.Exchanger 类表示一种两个线程可以进行互相交换对象的会和点。


## Semaphore

java.util.concurrent.Semaphore 类是一个计数信号量。这就意味着它具备两个主要方法：
acquire()
release()
计数信号量由一个指定数量的 "许可" 初始化。每调用一次 acquire()，一个许可会被调用线程取走。每调用一次 release()，一个许可会被返还给信号量。因此，在没有任何 release() 调用时，最多有 N 个线程能够通过 acquire() 方法，N 是该信号量初始化时的许可的指定数量。

## ExecutorService

 - ThreadPoolExecutor
  - Executors.newSingleThreadExecutor(), Executors.newFixedThreadPool(10), 
  
 - ScheduledThreadPoolExecutor
  - Executors.newScheduledThreadPool(10)
  
 ## ForkJoinPool 
 
 ## Lock
 
  - ReentrantLock
  
 ## synchronized
 
 ## ReadWriteLock
 
  - ReentrantReadWriteLock
 
## Atomic

 - AtomicBoolean
 - AtomicInteger
 - AtomicLong
 - AtomicReference
 
 
### 参考链接

[Java 并发工具包 java.util.concurrent 用户指南](http://blog.csdn.net/defonds/article/details/44021605/)
