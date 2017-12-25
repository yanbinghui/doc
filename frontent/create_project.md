# 开发前端应用的几种方式

## java + vm

简单介绍下这种方式，首先实现一个HttpServlet，在get和post方法中，使用VelocityEngine，将layout和include screen merge（VelocityEngine.mergeTemplate). 
这种方法的特点是比较简单，直接在vm里面包含js和html，js负责动态网页部分，比如button触发请求等。

## java + vm + requiredjs

在这种方式下，java负责填充vm的模型，并直接返回需要跳转的vm页面。这个时候vm页面启动。

如果启动的vm中包含一个data-main，如下所示：

```
<script src="js/require.js" data-main="js/main"></script>
```

那么会触发该main.js的执行，如果使用类似angularJS的框架，那么main.js能够与html直接交互，启动单页面应用。
