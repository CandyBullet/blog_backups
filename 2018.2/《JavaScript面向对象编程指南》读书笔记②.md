[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:32:24)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:32:38)

# 《JavaScript面向对象编程指南》读书笔记② #

## 概述 ##
[《JavaScript面向对象编程指南》读书笔记①][1]

这里只记录一下我看[JavaScript面向对象编程指南][2]记录下的一些东西。那些简单的知识我没有记录，我只记录几个容易遗漏的或者精彩的知识点，以后再看也可当做拾遗之用！

## 内容 ##

1.枚举属性用for-in循环显示。

2.当我们对对象的prorotype属性进行完全重写时，有可能会对对象constructor属性产生一定的负面影响。

3.uber——子对象访问父对象的方式Triangle.uber = TwoDShape.prototype

4.<script>标签的type="text/javascript"可以保证js的代码执行顺序。

5.setTimeout函数会返回一个超时id，利用这个超时id可以用clearTimeout()函数取消超时。

6.setTimeout函数和setInterval函数的第一个参数可以是一个可以被eval()执行的字符串。

7.DOM中空白符也被认为是文本节点;注释是一个comment节点。

8.window.document是由HTMLDocument()构造器创建的。

9.利用document对象的documentElement属性可以访问根节点，即<html>标签。

10.css属性中的短线（“-”）在js中是不可用的。因此我们直接跳过并将下一个单词的首字母大写。比如padding-top写成paddingTop。

11.由匿名函数所定义的监听器是不能被removeEventListener移除的。

12.所谓模式，其实就是针对某类问题的具有可重用性的解决方案。

13.构造器返回的是新建对象的this指针

  [1]: http://www.imooc.com/article/22795
  [2]: https://book.douban.com/subject/21372235/
