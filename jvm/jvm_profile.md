# JVM 调优建议

## 4. 小结

#### 4.1 性能相关
-XX:-UseBiasedLocking -XX:-UseCounterDecay -XX:AutoBoxCacheMax=20000 -XX:+PerfDisableSharedMem -XX:+AlwaysPreTouch -Djava.security.egd=file:/dev/./urandom

#### 4.2 内存大小相关(JDK7)
-Xms4096m -Xmx4096m -Xmn2048m -XX:MaxDirectMemorySize=4096m-XX: PermSize=256m -XX:MaxPermSize=512m -XX:ReservedCodeCacheSize=240M

#### 4.3 CMS GC 相关
-XX:+UseConcMarkSweepGC -XX:CMSInitiatingOccupancyFraction=75 -XX:+UseCMSInitiatingOccupancyOnly -XX:MaxTenuringThreshold=6 -XX:+ExplicitGCInvokesConcurrent -XX:+ParallelRefProcEnabled

#### 4.4 GC 日志 相关
-Xloggc:/dev/shm/app-gc.log -XX:+PrintGCApplicationStoppedTime -XX:+PrintGCDateStamps -XX:+PrintGCDetails

#### 4.5 异常 日志 相关
-XX:-OmitStackTraceInFastThrow -XX:ErrorFile=${LOGDIR}/hs_err_%p.log -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=${LOGDIR}/

#### 4.6 JMX相关

## 参考链接

1. [JVM 调优建议](https://www.weixin765.com/doc/oaezziqf.html)

2. [一步步优化JVM](https://yq.aliyun.com/articles/140597?spm=a2c4e.11153959.blogcont140555.18.437c3187n3OxnC)

3. [OpenJDK](https://github.com/bloodstars/OpenJDK)

4. [强引用，弱引用，软引用](http://blog.csdn.net/mazhimazh/article/details/19752475)

5. [四种引用](https://www.cnblogs.com/yw-ah/p/5830458.html)
