[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:24:54)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:25:25)

# 《CSS动画实用技巧》课程笔记 #

## 概述 ##
这是我学习[CSS动画实用技巧](https://www.imooc.com/learn/357)的课程笔记

### 常用动画属性——transition ###
![常用动画属性——transition](http://images.cnblogs.com/cnblogs_com/yangzhou33/1158868/o_2018_2_2_1.gif)

```
        .change img{
          display:block;
          width:300px;
          height:284px;
          opacity:0;
          -webkit-transform:translate(-100px,-100px);
          -webkit-transition:opacity 1s ease-in-out 0.5s,-webkit-transform 1s ease-in-out;
          transition: opacity 1s ease-in-out 0.5s,transform 1s ease-in-out;
        }
        .change:hover img{
          -webkit-transform:translate(0px,0px);
          opacity:1;
          -webkit-transition: opacity 1s ease-in-out,-webkit-transform 1s ease-in-out .1s;
          transition: opacity 1s ease-in-out,transform 1s ease-in-out .1s;
        }
```

主要是移动和透明渐变同时进行（有延迟）。

### 常用动画属性——animation ###
![常用动画属性——animation](http://images.cnblogs.com/cnblogs_com/yangzhou33/1158868/o_2018_2_2_2.gif)

```
@keyframes shake-hard {
  2% {
    transform: translate(1px, -2px) rotate(3.5deg); }
  4% {
    transform: translate(-7px, -6px) rotate(3.5deg); }
  6% {
    transform: translate(2px, -6px) rotate(-0.5deg); }
  8% {
    transform: translate(1px, 2px) rotate(2.5deg); }
  10% {
    transform: translate(1px, 7px) rotate(1.5deg); }
  12% {
    transform: translate(0px, 2px) rotate(-0.5deg); }
  14% {
    transform: translate(9px, 2px) rotate(1.5deg); }
  16% {
    transform: translate(-4px, 2px) rotate(3.5deg); }
  18% {
    transform: translate(-9px, 5px) rotate(1.5deg); }
  20% {
    transform: translate(-9px, -8px) rotate(1.5deg); }
  22% {
    transform: translate(-2px, 3px) rotate(-0.5deg); }
  24% {
    transform: translate(3px, 2px) rotate(-2.5deg); }
  26% {
    transform: translate(8px, -7px) rotate(2.5deg); }
  28% {
    transform: translate(-7px, 9px) rotate(-2.5deg); }
  30% {
    transform: translate(-9px, 3px) rotate(-0.5deg); }
  32% {
    transform: translate(-7px, 2px) rotate(3.5deg); }
  34% {
    transform: translate(-1px, -6px) rotate(0.5deg); }
  36% {
    transform: translate(5px, -1px) rotate(3.5deg); }
  38% {
    transform: translate(2px, 6px) rotate(3.5deg); }
  40% {
    transform: translate(-4px, -2px) rotate(-1.5deg); }
  42% {
    transform: translate(1px, -7px) rotate(-2.5deg); }
  44% {
    transform: translate(6px, 7px) rotate(-1.5deg); }
  46% {
    transform: translate(-3px, 6px) rotate(2.5deg); }
  48% {
    transform: translate(-6px, 6px) rotate(2.5deg); }
  50% {
    transform: translate(4px, -6px) rotate(1.5deg); }
  52% {
    transform: translate(-8px, 9px) rotate(-2.5deg); }
  54% {
    transform: translate(-7px, 5px) rotate(-0.5deg); }
  56% {
    transform: translate(-4px, 9px) rotate(2.5deg); }
  58% {
    transform: translate(-6px, -8px) rotate(-0.5deg); }
  60% {
    transform: translate(6px, -9px) rotate(2.5deg); }
  62% {
    transform: translate(2px, 9px) rotate(1.5deg); }
  64% {
    transform: translate(7px, -7px) rotate(1.5deg); }
  66% {
    transform: translate(1px, -3px) rotate(0.5deg); }
  68% {
    transform: translate(9px, -2px) rotate(-0.5deg); }
  70% {
    transform: translate(9px, -3px) rotate(-1.5deg); }
  72% {
    transform: translate(2px, -3px) rotate(-0.5deg); }
  74% {
    transform: translate(6px, -9px) rotate(1.5deg); }
  76% {
    transform: translate(-3px, 6px) rotate(3.5deg); }
  78% {
    transform: translate(1px, 8px) rotate(-0.5deg); }
  80% {
    transform: translate(10px, -2px) rotate(1.5deg); }
  82% {
    transform: translate(-5px, 5px) rotate(3.5deg); }
  84% {
    transform: translate(7px, -5px) rotate(-0.5deg); }
  86% {
    transform: translate(-3px, -7px) rotate(-0.5deg); }
  88% {
    transform: translate(-2px, -1px) rotate(-1.5deg); }
  90% {
    transform: translate(5px, 0px) rotate(-2.5deg); }
  92% {
    transform: translate(10px, -5px) rotate(-0.5deg); }
  94% {
    transform: translate(2px, 9px) rotate(0.5deg); }
  96% {
    transform: translate(4px, -8px) rotate(0.5deg); }
  98% {
    transform: translate(2px, 8px) rotate(-0.5deg); }
  0%, 100% {
    transform: translate(0, 0) rotate(0); } }
```

其实就是把抖动分隔成一帧帧，然后用keyframes连接起来。

### 常用动画属性——transform###
![常用动画属性——transform](http://images.cnblogs.com/cnblogs_com/yangzhou33/1158868/o_2018_2_2_3.gif)

```
.cardfan > img{
          position:absolute;
          border:10px solid #fff;
          box-sizing:border-box;
          box-shadow: 4px 4px 3px rgba(0, 0, 0, 0.2);
          -webkit-transform-origin: center 400px;
          transform-origin: center 400px;
          -webkit-transition: -webkit-transform .7s ease;
          transition: transform .7s ease;
        }
        .cardfan img:first-child{
          -webkit-transform:rotate(5deg);
          transform:rotate(5deg);
        }
        .cardfan img:last-child{
          -webkit-transform:rotate(-5deg);
          transform:rotate(-5deg);
        }
        .cardfan:hover img:first-child{
          -webkit-transform:rotate(25deg);
          transform:rotate(25deg);
        }
        .cardfan:hover img:last-child{
          -webkit-transform:rotate(-25deg);
          transform:rotate(-25deg);
        }
```
其实就是在鼠标接触之后第1,3张图旋转一下。

### 常用动画属性——animation-delay为负值 ###
![常用动画属性——animation-delay为负值](http://images.cnblogs.com/cnblogs_com/yangzhou33/1158868/o_2018_2_2_4.gif)

```
.spinner > div{
          display:inline-block;
          width:6px;
          height:100%;
          background:green;
          -webkit-animation: strechdelay 1.2s infinite ease-in-out ;
        }
        .spinner .line2{
          -webkit-animation-delay:-1.1s;
        }
        .spinner .line3{
          -webkit-animation-delay:-1.0s;
        }

        .spinner .line4{
          -webkit-animation-delay:-0.9s;
        }

        .spinner .line5{
          -webkit-animation-delay:-0.8s;
        }/**/
        @-webkit-keyframes strechdelay{
          0%,40%,100%{
            -webkit-transform:scaleY(.4);
          }
          20%{
            -webkit-transform:scaleY(1);
          }
        }
```
比如：`animation-delay`为-2s，效果是使动画马上开始，但跳过 2 秒进入动画。

### 常用动画属性——妙用border颜色 ###
![常用动画属性——妙用border颜色](http://images.cnblogs.com/cnblogs_com/yangzhou33/1158868/o_2018_2_2_5.gif)

```
.spinner{
          width:10em;
          height:10em;
          border-radius:100%;
          margin:100px auto;
          border:1.1em solid rgba(255,255,255,.2);
          border-left-color:#fff;
        }
```
主要是先让一个边框颜色不同，然后让它旋转。

## 常用动画属性——巧用border宽度  ##
![常用动画属性——妙用border宽度 ](http://images.cnblogs.com/cnblogs_com/yangzhou33/1158868/o_2018_2_2_6.gif)

```
.image-layer:before {
          content: '';
          position: absolute;
          top: 0;
          right: 0;
          border-style: solid;
          border-width: 0;
          border-color: rgba(0,0,0,0.2) #fff;
          border-radius: 0 0 0 4px;
          box-shadow: 0 1px 1px rgba(0,0,0,0.3), -1px 1px 1px rgba(0,0,0,0.2);
          -webkit-transition: all 0.4s ease-out;
          transition:all 0.4s ease-out;
        }

        .image-layer:hover:before{
          border-right-width:80px;
          border-bottom-width:80px;
        }

        .paper-flip.folded .image-layer:before{
          border-right-width:1000px;
          border-bottom-width:600px;
        }
```
利用宽度做成折角效果。翻页效果有点看不懂。

### 常用动画属性——实现运动动画 ###
![常用动画属性——实现运动动画](http://images.cnblogs.com/cnblogs_com/yangzhou33/1158868/o_2018_2_2_7.gif)

```
.stage{
          width:120px;
          height:auto;
          margin:0 auto;
          position:relative;
          -webkit-transform-origin:center top;
          -webkit-transform:rotate(-30deg);
          -webkit-animation:sway 2.2s infinite alternate ease-in-out;
        }
        .watch{
          width:100%;
          height:auto;
        }
        .seconds{
          position:absolute;
          width:8%;
          height:auto;
          bottom:11.5%;
          left:45.5%;
          -webkit-transform-origin:center 72.4%;
          -webkit-animation:second 60s infinite linear;
        }
        @-webkit-keyframes second{
          to{
            -webkit-transform:rotate(355deg);
          }
        }
        @-webkit-keyframes sway{
          to{
           -webkit-transform:rotate(30deg);
          }
        }
```
其实就是利用rotate来进行弧形运动，注意`animation-direction：alternate`和`center：top`。
