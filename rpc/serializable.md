# java 序列化

## Serializable
1. 序列化 ID 的问题
2. 静态变量序列化
3. Transient关键字
4. 子类序列化，父类没有序列化. 
 参考3，如果父类没有序列化，则分两种情况。父类有默认构造函数，这时候，父类信息不会写入序列化文件，反序列化时候，父类的相应field是默认构造函数创建的值。
 如果父类没有默认构造函数，那么反序列化失败，对于父类没有序列化的类，需要调用他的默认构造函数
 
5. 重复序列化存储问题

6. 反序列化不需要调用构造函数.


## 参考
1. [Java 序列化的高级认识](https://www.ibm.com/developerworks/cn/java/j-lo-serial/)
2. [Java 序列化Serializable详解](http://blog.csdn.net/sheepmu/article/details/27579895)
3. [Java序列化的机制和原理](http://developer.51cto.com/art/200908/147650.htm)

