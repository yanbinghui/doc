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

## angularJS入门


#### 从velocity到js的入口

```
<script data-main="main"
    src="1.4.30/vendor/requirejs/require.js">
</script>
<script>
    require(['bootstrap'], function (bootstrap) {
    });
</script>
```

在main中显示说明了依赖，以及依赖中export的模块和模块的依赖。

从bootstrap启动，在initConfig中声明监听事件。引用state，controller，service，directives，filters的相关模块，已经模块的注册子服务。
声明的ui.router触发跳转页面链接。跳转页面链接触发states对应的jsController，然后得到scope，再映射为html展示。

其中的服务分两类，一类是可以使用依赖注入。如state，controller，service，directives，filters。一类是直接使用路径引入，如jsHelper和model。

Html也分为三类，一类是states中跟controller映射的html；一种是jsHelper映射的html；还有一种是直接showDialog对应的页面。在jsHelper中调用，还可以设置callback函数。

#### 前端跳转的方式

1. 可以通过ui-sref, href跳转
2. 通过在controller中依赖其他的helper函数触发跳转。

