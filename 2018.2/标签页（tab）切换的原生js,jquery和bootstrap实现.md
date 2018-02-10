[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:25:49)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:26:24)

# 标签页（tab）切换的原生js,jquery和bootstrap实现 #

## 概述 ##
这是我在学习课程[Tab选项卡切换效果][1]时做的总结和练手。

原课程中只有原生`js`实现，`jquery`和`bootstrap`实现是我自己补上的。

## 本节内容 ##
 - 标签页（tab）切换的原生`js`实现
 - 标签页（tab）切换的`jquery`实现
 - 标签页（tab）切换的`bootstrap`实现

### js实现 ###
![标签页（tab）切换的原生`js`实现][2]

说明：

 1. 代码是我自己写的，与课程中的不一样。
 2. 主要利用`display:none`来把部分内容隐藏而显示其它内容。
 3. 遇到了事件的循环绑定，我是利用添加id使其成为钩子来解决的。

代码：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>tab切换</title>
    <style type="text/css">
        *{
            font-family: Times;
        }

        #main {
            font-size: 13px;
            height: 100px;
            width: 300px;
            border: 1px solid #c0c0c0;
        }

        #top_column {
            height: 30px;
            width: 300px;           
        }

        #top_column div {
            height: 30px;
            width: 75px;    
            background-color: #fffff0;  
            text-align: center; 
            line-height: 30px;  
            border: 1px solid #c0c0c0;
            margin: -1px -1px 0px -1px; 
        }

        #top_column div:hover { 
            background-color: #fff; 
            font-weight:bold;
            color: orange;      
        }   

        .top_column_hover { 
            background-color: #fff; 
            font-weight:bold;
            color: orange;      
        }           

        #bottom_column {
            height: 70px;
            width: 300px;       
        }
        
        #bottom_column a {
            height: 35px;
            width: 140px;
            display: block;
            text-align: left;   
            text-decoration: none;
            outline: none;
            color: black;
            line-height: 35px;  
            padding-left: 10px; 
            float: left;    
        }

        #bottom_column a:hover {
            color: orange;      
        }

        #main div {
            float: left;
        }



    </style>
</head>
<body>
    <div id="main">
        <div id="top_column">
            <div class="column_notice">公告</div>
            <div class="column_rule">规则</div>
            <div class="column_forum">论坛</div>
            <div class="column_security">安全</div>
        </div>
        <div id="bottom_column">
            <div class="content_notice" style="display:block">
                <a href="#" class="notice1">颠覆式创新</a>
                <a href="#" class="notice2">旗舰来了</a>
                <a href="#" class="notice3">全国首测</a>
                <a href="#" class="notice4">千年一遇</a>
            </div>
            <div class="content_rule" style="display:none">
                <a href="#" class="rule1">司机高速</a>
                <a href="#" class="rule2">北欧村名</a>
                <a href="#" class="rule3">高校老师</a>
                <a href="#" class="rule4">公安工作组</a>
            </div>
            <div class="content_forum" style="display:none">
                <a href="#" class="forum1">百度贴吧</a>
                <a href="#" class="forum2">哈尔滨</a>
                <a href="#" class="forum3">麦当劳</a>
                <a href="#" class="forum4">光头哥</a>
            </div>
            <div class="content_security" style="display:none">
                <a href="#" class="security1">经纪人</a>
                <a href="#" class="security2">以上处于</a>
                <a href="#" class="security3">国足领队</a>
                <a href="#" class="security4">国务院</a>
            </div>
        </div>
    </div>

    <script type="text/javascript">

        window.onload=tab;

        function tab(){
            var top_column=document.getElementById("top_column").getElementsByTagName("div");
            var bottom_column=document.getElementById("bottom_column").getElementsByTagName("div");

            for(var i=0;i<top_column.length;i++){
                top_column[i].id=i;
                top_column[i].onmouseover=function(){
                    tab_content(this.id);
                }
            }

            function tab_content(i){

                for(var j=0;j<top_column.length;j++){
                        top_column[j].className="top_column_not_hover";
                        bottom_column[j].style.display="none";
                }

                top_column[i].className="top_column_hover";
                bottom_column[i].style.display="block";
            }
        }
    </script>
</body>
</html>
```

### jquery实现 ###
![标签页（tab）切换的`jquery`实现][3]

说明：

 1. 效果其实和原生js实现是一样的。

 2. 因为我想写一下jquery代码练练手，所以只是把原生js实现中的js代码改成了jquery的形式。

代码：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>tab切换</title>
    <style type="text/css">
        *{
            font-family: Times;
        }

        #main {
            font-size: 13px;
            height: 100px;
            width: 300px;
            border: 1px solid #c0c0c0;
        }

        #top_column {
            height: 30px;
            width: 300px;           
        }

        #top_column div {
            height: 30px;
            width: 75px;    
            background-color: #fffff0;  
            text-align: center; 
            line-height: 30px;  
            border: 1px solid #c0c0c0;
            margin: -1px -1px 0px -1px; 
        }

        #top_column div:hover { 
            background-color: #fff; 
            font-weight:bold;
            color: orange;      
        }   

        .top_column_hover { 
            background-color: #fff; 
            font-weight:bold;
            color: orange;      
        }           

        #bottom_column {
            height: 70px;
            width: 300px;       
        }
        
        #bottom_column a {
            height: 35px;
            width: 140px;
            display: block;
            text-align: left;   
            text-decoration: none;
            outline: none;
            color: black;
            line-height: 35px;  
            padding-left: 10px; 
            float: left;    
        }

        #bottom_column a:hover {
            color: orange;      
        }

        #main div {
            float: left;
        }



    </style>
</head>
<body>
    <div id="main">
        <div id="top_column">
            <div class="column_notice">公告</div>
            <div class="column_rule">规则</div>
            <div class="column_forum">论坛</div>
            <div class="column_security">安全</div>
        </div>
        <div id="bottom_column">
            <div class="content_notice" style="display:block">
                <a href="#" class="notice1">颠覆式创新</a>
                <a href="#" class="notice2">旗舰来了</a>
                <a href="#" class="notice3">全国首测</a>
                <a href="#" class="notice4">千年一遇</a>
            </div>
            <div class="content_rule" style="display:none">
                <a href="#" class="rule1">司机高速</a>
                <a href="#" class="rule2">北欧村名</a>
                <a href="#" class="rule3">高校老师</a>
                <a href="#" class="rule4">公安工作组</a>
            </div>
            <div class="content_forum" style="display:none">
                <a href="#" class="forum1">百度贴吧</a>
                <a href="#" class="forum2">哈尔滨</a>
                <a href="#" class="forum3">麦当劳</a>
                <a href="#" class="forum4">光头哥</a>
            </div>
            <div class="content_security" style="display:none">
                <a href="#" class="security1">经纪人</a>
                <a href="#" class="security2">以上处于</a>
                <a href="#" class="security3">国足领队</a>
                <a href="#" class="security4">国务院</a>
            </div>
        </div>
    </div>

    <script src="http://how2j.cn/study/js/jquery/2.0.0/jquery.min.js"></script>
    <script type="text/javascript">

    $(window).load(function(){
        var $top_column=$("#top_column div");
        var $bottom_column=$("#bottom_column div");

        $.each($top_column,function(i,item){
            $(item).hover(tab_content);
        })

        function tab_content(){
            $.each($top_column,function(i,item){
                $(item).attr("class", "top_column_not_hover");
            })

            $.each($bottom_column,function(i,item){
                $(item).hide();
            })

            var index=$top_column.index($(this));
            $bottom_column.eq(index).show();
            $top_column.eq(index).attr("class", "top_column_hover");
        }
    })
    </script>
</body>
</html>
```
### bootstrap实现 ###
![标签页（tab）切换的`bootstrap`实现][4]

说明：

 1. 代码中不需要额外写`js`，只需引用`jquery`和`bootstrap`文件即可。
 2. 虽然不需要写`js`，但是缺点是需要点击，并且鼠标离开后回复原状，解决这些问题的话需要写`js`。
 3. 虽然`bootstrap`看起来很华丽，而且很简便。但是在一些小改动上面很麻烦，而且会踩很多坑。所以如果需要细致并且频繁修改网站的话，不建议用`bootstrap`搭建网站。
 4. 踩坑记录：`box-sizing` 属性的`content-box`和`border-box`（其实这也是盒模型的基本）。

代码：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>tab切换</title>
    <style type="text/css">
        *{
            font-family: Times;
        }

        #main {
            font-size: 13px;
            height: 100px;
            width: 300px;
            border: 1px solid #c0c0c0;
            margin:10px 10px;
            box-sizing: content-box; 
        }

        #myTab {
            height: 30px;
            width: 300px;           
        }

        #myTab div {
            height: 30px;
            width: 75px;    
            background-color: #fffff0;  
            text-align: center; 
            line-height: 30px;  
            border: 1px solid #c0c0c0;
            margin: -1px -1px 0px -1px;
            box-sizing: content-box; 
        }

        #myTab div:hover {  
            background-color: #fff; 
            font-weight:bold;
            color: orange;  
            cursor: pointer;    
        }               

        #myTabContent {
            height: 70px;
            width: 300px;       
        }
        
        #myTabContent a {
            height: 35px;
            width: 140px;
            display: block;
            text-align: left;   
            text-decoration: none;
            outline: none;
            color: black;
            line-height: 35px;  
            padding-left: 10px; 
            float: left;    
        }

        #myTabContent a:hover {
            color: orange;      
        }

        #main div {
            float: left;
        }


    </style>
</head>
<body>
    <div id="main">
        <div id="myTab" class="nav nav-tabs">
            <div href="#notice" data-toggle="tab">公告</div>
            <div href="#rule" data-toggle="tab">规则</div>
            <div href="#forum" data-toggle="tab">论坛</div>
            <div href="#security" data-toggle="tab">安全</div>
        </div>
        <div id="myTabContent" class="tab-content">
            <div class="tab-pane fade in active" id="notice">
                <a href="#" class="notice1">颠覆式创新</a>
                <a href="#" class="notice2">旗舰来了</a>
                <a href="#" class="notice3">全国首测</a>
                <a href="#" class="notice4">千年一遇</a>
            </div>
            <div class="tab-pane fade" id="rule">
                <a href="#" class="rule1">司机高速</a>
                <a href="#" class="rule2">北欧村名</a>
                <a href="#" class="rule3">高校老师</a>
                <a href="#" class="rule4">公安工作组</a>
            </div>
            <div class="tab-pane fade" id="forum">
                <a href="#" class="forum1">百度贴吧</a>
                <a href="#" class="forum2">哈尔滨</a>
                <a href="#" class="forum3">麦当劳</a>
                <a href="#" class="forum4">光头哥</a>
            </div>
            <div class="tab-pane fade" id="security">
                <a href="#" class="security1">经纪人</a>
                <a href="#" class="security2">以上处于</a>
                <a href="#" class="security3">国足领队</a>
                <a href="#" class="security4">国务院</a>
            </div>
        </div>
    </div>

    <script src="http://how2j.cn/study/js/jquery/2.0.0/jquery.min.js"></script>
    <link href="http://how2j.cn/study/css/bootstrap/3.3.6/bootstrap.min.css" rel="stylesheet">
    <script src="http://how2j.cn/study/js/bootstrap/3.3.6/bootstrap.min.js"></script>

    <script type="text/javascript">

    </script>
</body>
</html>
```

  [1]: http://www.imooc.com/learn/176
  [2]: //img.mukewang.com/5a5da468000134e400500012.gif
  [3]: //img.mukewang.com/5a5da603000134e400500012.gif
  [4]: //img.mukewang.com/5a5da74a0001647800370012.gif
