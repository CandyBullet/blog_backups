[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:37:15)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:37:28)

# Markdown内嵌Html语言 #

## 概述 ##

&emsp;&emsp;Markdown是**内嵌Html语言**的，这使得我们可以在Markdown文档里面实现很多**有趣的东西**。现在记录在此，供自己以后参考，相信对其他人也有用。

### 介绍 ###

&emsp;&emsp;Markdown的语法只有一个目标：作为在**网上书写**的一种格式。  

&emsp;&emsp;Html是一种**方便出版**的格式，Markdown是一种**方便书写**的格式，因此Markdown语法只规定了那些适用于纯文本的情形。  

&emsp;&emsp;对于那些Markdown语法没有规定的情形，可以直接在Markdown里面使用Html语法。只有2点限制：(1)Html的块级元素必须用空行和Markdown的内容分隔开。(2)Html标签前后没有空格。  

&emsp;&emsp;注意: 想要了解更多内容[请点击这里。](https://daringfireball.net/projects/markdown/syntax#html)

### 缩进 ###

&emsp;&emsp;可以使用Html中的转义字符。比如缩进：&amp;emsp;&amp;emsp;

```
&emsp;&emsp;Roses are blue
```

&emsp;&emsp;会被渲染为：  

&emsp;&emsp;Roses are blue


### 换行 ###

&emsp;&emsp;标准的Markdown语法规定了2个空格表示换行。  

&emsp;&emsp;但是你也可以使用&lt;/br&gt;标签换行。

```
Roses are blue</br>Violets are red
```

&emsp;&emsp;会被渲染为：  

Roses are blue</br>Violets are red

### 删除线 ###

&emsp;&emsp;可以使用删除线标签&lt;s&gt;&lt;/s&gt;。

```
Roses are <s>Blue</s>
```

&emsp;&emsp;会被渲染为：  

Roses are <s>Blue</s>

### 分割线 ###

&emsp;&emsp;可以使用分割线标签&lt;hr&gt;。

```
分割线上面
<hr>
分割线下面
```

&emsp;&emsp;会被渲染为：  

分割线上面
<hr>
分割线下面


### 上下标 ###

&emsp;&emsp;可以使用上标标签&lt;sup&gt;&lt;/sup&gt;和下标标签&lt;sub&gt;&lt;/sub&gt;。

```
n<sup>2</sup> + 2n + 1 = 0

H<sub>2</sub>O
```

&emsp;&emsp;会被渲染为：  

n<sup>2</sup> + 2n + 1 = 0

H<sub>2</sub>O

### 高亮 ###

&emsp;&emsp;可以使用高亮标签&lt;mark&gt;&lt;/mark&gt;。

```
这是<mark>高亮文本</mark>
```

&emsp;&emsp;会被渲染为：  

这是<mark>高亮文本</mark>

### 表格 ###

&emsp;&emsp;可以使用表格标签。  

&emsp;&emsp;表格与Html代码的转换器：[点这里](http://pressbin.com/tools/excel_to_html_table/index.html)

```
<table class="table table-bordered table-striped table-condensed">
   <tr>
      <td>John</td>
      <td>Smith</td>
      <td>123 Main St.</td>
      <td>Springfield</td>
   </tr>
   <tr>
      <td>Mary</td>
      <td>Jones</td>
      <td>456 Pine St.</td>
      <td>Dover</td>
   </tr>
   <tr>
      <td>Jim</td>
      <td>Baker</td>
      <td>789 Park Ave.</td>
      <td>Lincoln</td>
   </tr>
</table>
```
&emsp;&emsp;会被渲染为：  

<table class="table table-bordered table-striped table-condensed">
   <tr>
      <td>John</td>
      <td>Smith</td>
      <td>123 Main St.</td>
      <td>Springfield</td>
   </tr>
   <tr>
      <td>Mary</td>
      <td>Jones</td>
      <td>456 Pine St.</td>
      <td>Dover</td>
   </tr>
   <tr>
      <td>Jim</td>
      <td>Baker</td>
      <td>789 Park Ave.</td>
      <td>Lincoln</td>
   </tr>
</table>

### iframe标签 ###

&emsp;&emsp;是的，你没有看错，在Markdown里面也可以直接使用**iframe标签**  

&emsp;&emsp;下面是一个简单的演示图

```
<p><iframe style="width: 100%; height: 120px;" src="https://demo.xiaohuochai.site/css/transition/t18.html" frameborder="0" width="320" height="240"></iframe></p>
```
&emsp;&emsp;会被渲染为：  

<p><iframe style="width: 100%; height: 120px;" src="https://demo.xiaohuochai.site/css/transition/t18.html" frameborder="0" width="320" height="240"></iframe></p>

&emsp;&emsp;下面是一个演示器

```
<p><iframe style="width: 100%; height: 300px;" src="https://demo.xiaohuochai.site/css/transition/t4.html" frameborder="0" width="320" height="240"></iframe></p>
```
&emsp;&emsp;会被渲染为：  

<p><iframe style="width: 100%; height: 300px;" src="https://demo.xiaohuochai.site/css/transition/t4.html" frameborder="0" width="320" height="240"></iframe></p>
