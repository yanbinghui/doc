# ThreadPoolExecutor

## 参考

1. 相关类

 Executors：包含一些快捷创建 ExecutorService 的方法，主要调用 ThreadPoolExecutor 和 ScheduledExecutor

 ScheduledThreadPoolExecutor：可以提交定时任务的ThreadPoolExecutor

 ThreadPoolExecutor：可以创建Fixed，cached，single ThreadExecutor

2. 阿里巴巴java规约建议直接使用ThreadPoolExecutor，用户可以对其中的参数有感知。

```
 其中参数为：

        int corePoolSize,
        int maximumPoolSize,
        long keepAliveTime,
        TimeUnit unit,
        BlockingQueue<Runnable> workQueue,
        ThreadFactory threadFactory,
        RejectedExecutionHandler handler
```
