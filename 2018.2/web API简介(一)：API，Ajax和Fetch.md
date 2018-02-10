[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:37:45)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:37:58)

# web API简介(一)：API，Ajax和Fetch #

## 概述 ##

今天逛[MDN](https://developer.mozilla.org/en-US/)，无意中看到了[web API简介](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Client-side_web_APIs/Introduction)，觉得挺有意思的，就认真读了一下。

下面是我在读的时候对感兴趣的东西的总结，供自己开发时参考，相信对其他人也有用。

### 什么是API ###

 API (Application Programming Interface)就是一些规则，它使软件与其它东西更好的交互。

 原文如下：

 >An API (Application Programming Interface) is a set of features and rules that exist inside a software program enabling interaction between the software and other items, such as other software or hardware.

### 常见浏览器API ###

- 操作文档的API
- 从服务器获取数据的API
- 用于绘制和操作图形的API
- 音频和视频API
- 设备API
- 客户端存储API

**注意**：浏览器中封装了很多API，有几百个吧，具体可以看这里：[MDN API index page](https://developer.mozilla.org/en-US/docs/Web/API)。

### API的常见操作 ###

- API通常有几个可用的options，用来调整以获得程序所需的确切环境

- API通常仅在操作完成时调用函数

在使用API时，我们往往不能立即获得返回的数据，因此必须在确保一个操作完成之后再进行另一个操作。我们通过回调函数实现这种操作，或者更为现代的，用Promise实现。

- API通常有可识别的入口

这些入口一般是API对象的实例。比如DOM API的入口是document，Canvas API的入口是canvas。

```
var em = document.createElement('em'); 

var canvas = document.querySelector('canvas');
var ctx = canvas.getContext('2d');
```

- API通常使用事件来处理状态的变化

比如：XMLHttpRequest API的onload事件在成功返回时就触发包含请求的资源。

- API通常在适当的地方有额外的安全机制

为了用户的安全，很多API一般都会请求权限。

### XMLHttpRequest API ###

也就是我们俗称的Ajax。

一个简单的例子如下：

```
//正如前面所说，我们获得API的入口：创建一个XHR请求。
var request = new XMLHttpRequest();

//我们使用open()方法来指定用于从网络请求资源的get方法, 以及它的URL。
request.open('GET', url);

//我们设置我们期待的响应类型—这是由请求的responseType属性定义的—作为text。
//这并不是绝对必要的 — XHR默认返回文本。
request.responseType = 'text';

//正如前面所说，我们我们用一个事件onload来判断是否获得了返回的数据。
//如果返回则执行回调函数。
request.onload = function() {
  poemDisplay.textContent = request.response;
};

//以上都是XHR请求的设置 — 在我们告诉它之前，它不会真正运行。
//我们用send()来运行它们。
request.send();
```

### Fetch API ###

Fetch API基本上是XHR的一个现代替代品——它是最近在浏览器中引入的，它使异步HTTP请求在JavaScript中更容易实现，对于开发人员和在Fetch之上构建的其他API来说都是如此。

我们把上面的XHR代码改为Fetch代码：
```
fetch(url).then(function(response) {
  response.text().then(function(text) {
    poemDisplay.textContent = text;
  });
});
```

首先，我们调用了fetch()方法，将我们要获取的资源的URL传递给它。这相当于现代版的XHR中的request.open()，另外，我们不需要任何等效的send()方法。

然后，可以看到.then()方法连接到了fetch()末尾-这个方法是[Promises](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)的一部分，是一个用于执行异步操作的现代JavaScript特性。fetch()返回一个promise，它将解析从服务器发回的响应。我们使用then()来运行一些后续代码，这是我们在其内部定义的函数。这相当于XHR版本中的onload事件处理程序。

然后，在函数内部，我们获取响应并运行其text()方法。这基本上将响应作为原始文本返回，这相当于在XHR版本中的responseType = 'text'。

最后，我们执行回调函数。把text赋值给textContent。

*注意：大多数现代的JavaScript api都是基于Promises的。*

**注意**：Fetch确实比XHR更稳定强力，但是很多浏览器不支持。但是随着IE浏览器的使用量减少(微软在逐渐开发使用Edge浏览器取代IE)，Fetch的使用会越来越流行，但是在这之前，我们必须用一段时间的XHR。
