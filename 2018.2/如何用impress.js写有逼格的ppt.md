[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:26:44)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:27:23)

# 如何用impress.js写有逼格的ppt #

## 概述 ##
这是我学习课程[impress让你的内容“舞”起来][1]而做的总结和练手。

[你可以点这里在线预览我做的ppt][2]

**注意**：等加载完了之后，点击空格键翻页！

### 简化模板 ###

下面是一个简化的模板
```
<!doctype html>
<html lang="zh">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
    <title>a mod of impress.js</title>
</head>
<body>
    <div id="impress">  
        <div class="fallback-message">
            Your browser doesn't support impress.js.  Try Chrome or Safari.
        </div>
        <div id="first" class="step" data-x="0" data-y="0" data-z="0" data-rotate="0" data-rotate-x="0" data-rotate-y="0" data-scale="0">
            <p>This is my first slide.  </p>
        </div>
    </div>
</body>
</html>
```

这是我简化后的模板，去除掉了一些css加载，js加载和注释的相关语句。

当然这个模板不能正常运行，但是可以很清楚的看出使用`impress.js`的相关语法

首先是`head`头部：

```
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
    <title>a mod of impress.js</title>
</head>
```
按惯例添加元信息和标题，和一般的html文件一样。

然后是`body`部分：

```
    <div id="impress">
```

先建立一个`id="impress"`的`div`，表示初始化它里面`impress`的相关语句；

```
    <div class="fallback-message">
            Your browser doesn't support impress.js.  Try Chrome or Safari.
    </div>
```

然后是`class="fallback-message"`也就是回调函数的`div`，表示如果浏览器不支持就返回这些信息：`Your browser doesn't support impress.js.  Try Chrome or Safari.`；

```
    <div id="first" class="step" data-x="0" data-y="0" data-z="0" data-rotate="0" data-rotate-x="0" data-rotate-y="0" data-scale="0">
            <p>This is my first slide.  </p>
    </div>
```

最后是`id="first" class="step"`的`div`，表示这是一张幻灯片。

解释一下幻灯片语句里面的相关参数：

 - `id="first"`这张幻灯片的`id`，可以自定义，方便`css`文件中调。
 - `class="step"`表示这是一张幻灯片，必须写`step`。
 - `data-x`表示这张幻灯片的x轴偏移量，`y`，`z`也是同理。
 - `data-rotate`表示这张幻灯片的三围旋转量，`x`，`y`，`z`也是同理。
 - `data-scale`表示这张幻灯片的放大缩小量。

### 思考 ###

其实`impress.js`使用起来非常简单，只要照个能用的模板，修改一下变量就会了。

我个人觉得，虽然`impress.js`在幻灯片的切换运动效果上非常有逼格和高大上，但是对于单张幻灯片的细枝末节却需要一点一点的写代码，非常麻烦，还不如用powerpoint。所以`impress.js`只适用于注重幻灯片的切换效果的场合，比如商业总结性报告，在线简历等。

  [1]: http://www.imooc.com/learn/119
  [2]: https://sishenhei7.github.io/impress_js_ppt/
