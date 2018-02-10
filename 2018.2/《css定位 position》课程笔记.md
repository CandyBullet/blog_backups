[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 10:20:10)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:22:08)

# 《css定位 position》课程笔记 #

这是我学习课程[css定位 position][1]时做的笔记!

## 本节内容 ##

 - html的三种布局方式
 - position可选参数
 - z-index
 - 盒子模型和定位的区别
 - 侧边栏导航跟随实例

### 三种布局 ###

 三种布局：标准流，浮动，定位

 两大元素：块级元素（div,h1-6,table,ol,ul,li,p）,内联元素（a,span,img,input）

### position参数 ###

static（标准流中正常排列）

relative（相对定位）

absolute（绝对定位）

fixed（脱离正常的文档流，登录弹窗，内联广告，不受制于父元素）

inherit（继承父元素的position属性）

### z-index ###
z-index大的元素会覆盖z-index小的元素

z-index为auto的元素不参与层级比较

z-index为负值，会被普通流中的层级覆盖

只作用于position为除static之外的定位属性

父元素层级的优势

### 盒子和定位 ###
盒子模型通过内外边距来实现移动，定位则通过位置来实现移动。

慕课网的登录界面的定位实例（有遮罩）
![慕课网的登录界面的定位实例][2]

### 导航实例 ###
一级栏目用div，二级栏目用ul和li，三级栏目用div

三级栏目用absolute定位在右边展开

二三级栏目一开始用`display：none`,然后用`hover:display:block`

![侧边栏导航跟随实例][3]


  [1]: http://www.imooc.com/learn/931
  [2]: //img.mukewang.com/5a5c058f00016cf710960613.jpg
  [3]: //img.mukewang.com/5a5c07f10001ba4506410606.jpg
