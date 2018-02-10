[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:31:49)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:32:03)

# 利用nodejs安装并运行express的三个坑 #

## 概述 ##
这是我安装并运行`express`的三个坑，应该是比较常见的，在此记录一下。
## 内容 ##

### express不是内部或外部命令 ###

```
输入命令：express -V
报错：'express' 不是内部或外部命令，也不是可运行的程序或批处理文件。
```
解决方法：

最新`express4.0`版本中将命令工具分家出来了,所以我们还需要安装一个命令工具,命令是:`npm install -g express-generator`。如果在`AppData\Roaming\npm`目录下生成了`express`、`express.cmd`两个文件，那么就成功解决了。

### npm install报错 ###

```
输入命令：npm install
报错：Unexpected end of input at 1:23510
```
解决方法：
输入指令：`npm cache clean --force`。然后再输入`npm install`就正常了。

### npm start报错 ###
```
输入命令：npm start
报错：missing script:start
```
解决方法：
在`init`文件夹的`package.json`里面添加`"scripts": {"start": "node ./bin/www"},`如果里面本来就有，那就表示你之前`npm install`的位置错了，要先进入`init`文件夹再执行`npm install`。
