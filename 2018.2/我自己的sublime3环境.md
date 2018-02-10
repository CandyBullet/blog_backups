[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:33:42)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:33:59)

# 我自己的sublime3环境 #

## 概述 ##
我本来一直用的别人自带的破解版sublime3，自带插件。

前几天看[《程序员修炼之道》](https://book.douban.com/subject/1152111/)，其中谈到了最好精通一种编辑器，我觉得说的很有道理，于是重新下了最新版的sublime3，一步步熟悉它。

下面是我熟悉的过程中的一些配置和理解，供自己开发时参考，相信对其他人也有用。

### 注册码 ###
> —– BEGIN LICENSE —– 
TwitterInc 
200 User License 
EA7E-890007 
1D77F72E 390CDD93 4DCBA022 FAF60790 
61AA12C0 A37081C5 D0316412 4584D136 
94D7F7D4 95BC8C1C 527DA828 560BB037 
D1EDDD8C AE7B379F 50C9D69D B35179EF 
2FE898C4 8E4277A8 555CE714 E1FB0E43 
D5D52613 C3D12E98 BC49967F 7652EED2 
9D2D2E61 67610860 6D338B72 5CF95C69 
E36B85CC 84991F19 7575D828 470A92AB 
—— END LICENSE ——

之前没有用ST3正式版也是因为被注册码吓到了，这次一看，原来网上一大堆注册码。。。。如果这个注册码失效了，重新去网上找一个即可。

### 基础用户设置 ###

工具栏 Preferences – Settings-User 加入下面的代码：
```
{
    //主题
    "theme": "Boxy Monokai.sublime-theme",
    //配色方案
    "color_scheme": "Packages/Boxy Theme/schemes/Boxy Monokai.tmTheme",
    //开启选中范围内搜索（而不是整个文档
    "auto_find_in_selection": true,
    //文件夹加粗
    "bold_folder_labels": true,
    //右侧代码预览时给所在区域加上边框
    "draw_minimap_border": true,
    //文件末尾自动保留一个空行
    "ensure_newline_at_eof_on_save": true,
    //默认显示行号右侧的代码段闭合展开三角号
    "fade_fold_buttons": false,
    //当前行高亮
    "highlight_line": true,
    //行间距
    "line_padding_bottom": 2,
    //行间距
    "line_padding_top": 2,
    //失去焦点时保存
    "save_on_focus_lost": true,
    //自动移除行尾多余空格
    "trim_trailing_white_space_on_save": true,
    //自动换行
    "word_wrap": "true",
    //忽略的包
    "ignored_packages":
    [
        "Vintage"
    ],

}

```

### 快捷键设置 ###
工具栏 Preferences – 快捷键设置。

```
[
    { "keys": ["alt+space"], "command": "auto_complete" },
    { "keys": ["alt+space"], "command": "replace_completion_with_auto_complete", "context":
      [
        { "key": "last_command", "operator": "equal", "operand": "insert_best_completion" },
        { "key": "auto_complete_visible", "operator": "equal", "operand": false },
        { "key": "setting.tab_completion", "operator": "equal", "operand": true }
      ]
    },
    { "keys": ["ctrl+alt+d"], "command": "goto_definition" },
    { "keys": ["shift+ctrl+alt+a"], "command": "alignment" },
    { "keys": ["ctrl+shift+c"], "command": "open_in_browser" },
    { "keys": ["ctrl+alt+shift+p"], "command": "autoprefixer" },
]
```
记录一下重要的快捷键

> ctrl+shift+p  所有命令
ctrl+g 跳转行
ctrl+/ 注释
ctrl+d 选择相同字符
ctrl+shift+up/down 整行移动
ctrl+alt+right 跳到下一个编辑点
ctrl+n 新建文件
ctrl+shift+t 重新打开最近关闭文件
ctrl+w 关闭文件
f11 切换全屏状态
ctrl+right 光标向右跳跃
alt+right 按单词移动
ctrl+alt+up 选择多行进行编辑
ctrl+shift+enter 在当前行前插入新行
ctrl+q 搜索项目中的文件
Alt+数字 切换打开第N个文件
ctr+shift+n 打开新的sublime text
ctr+shift+w 关闭sublime text
ctrl+tab(ctrl+shift+tab) 跳转到其他文本
alt+shift+数字 分屏

### 隐藏任务栏 ###
首先按下ctrl + shift + p，输入view，选择`View:Toggle Menu`即可。重复一遍就是换回来。

### 安装插件管理器 ###
首先进入[packagecontrol官网](https://packagecontrol.io/)，点击install now,复制sublime text 3标签下的代码。

然后ctrl+` 打开调试窗口，在输入框内粘贴上面复制的代码。

最后等待完成即可。

### 安装插件 ###
按下ctrl + shift + p，输入pci，选择`Package Control:Install Package`，等待一段时间会出现输入框，然后输入要安装的插件名，最后回车即可。

#### Boxy Theme ####
主题也是一种插件，用上面的方法安装Boxy Theme主题即可。

切换主题风格：首先按下ctrl + shift + p，输入box，选择`Boxy Theme:Activation`，然后切换即可预览各种风格，按回车确定。确定之后要重启ST3。

#### Emmet ####
神器，不解释

#### A File Icon ####
各种js,html,css等文件的图标，很好看。

#### Alignment ####
等号对齐（Ctrl+Alt+A）

#### BracketHighlighter ####
高亮的各种配对的语法符号。

#### AutoPrefixer ####
补上一些浏览器前缀。

需要先设置快捷键。
```
[
    { "keys": ["ctrl+alt+shift+p"], "command": "autoprefixer" }
]
```
然后在AutoPrefixer的设置里面填写即可使用。

```
{
    "browsers": ["last 2 versions","Firefox >= 20"]
}
```

#### Babel ####
ES6 JavaScript相关。

#### ChineseLocalizations ####
ST3界面汉化

#### ConvertToUTF8 ####
ST3可以读取中文文档

#### CSS3和JQuery ####
CSS3和JQuery的一些自动补全和高亮

#### DocBlockr ####
生成注释

```
/**
* 这里的注释内容【会】被压缩工具压缩
*/

/*！
* 这里的注释内容【不会】被压缩工具压缩
* 与上面一个注释块不同的是，第2个*换成了!
*/
```

#### HTML-CSS-JS Prettify ####
我觉得这个比其它的代码整理插件好用的多。不过这个插件需要nodejs环境。

注意，安装后需要在HTML-CSS-JS Prettify插件的Set Plugin Options里面修改nodejs路径，不然不能用。

#### HTML-CSS-JS Prettify ####
对js文件进行重新排版。

可以按下ctrl + shift + p调用命令面板，然后输入`Format: Javascript`启动插件排版，或者用快捷键：ctrl + alt + f。

#### MarkdownEditing和OmniMarkupPreviewer ####
markdown编辑和浏览器实时预览插件

需要在OmniMarkupPreviewer插件的用户设置里面添加下列代码，否则会出现404.

```
{
    "renderer_options-MarkdownRenderer": {
        "extensions": ["tables", "fenced_code", "codehilite"]
    }
}
```

#### SideBarEnhancements ####
侧边栏功能增强插件，添加了比如浏览器查看等选项。

设置快捷键让默认浏览器预览：

```
{ "keys": ["ctrl+shift+c"], "command": "open_in_browser" }
```

#### SublimeLinter ####
这是语法校验插件

说一下各个校验工具：

> JSLint
> 优点：配置是老道已经定好的，开箱即用。
> 缺点：有限的配置选项，很多规则不能禁用；扩展性差。
> JSHint
> 优点：有了很多参数可以配置；支持了基本的ES6。
> 缺点：不支持自定义规则。
> ESLint
> 优点：默认规则里面包含了JSLint和JSHint的规则；可以自定义规则。
> 缺点：需要进行一些自定义配置；慢 (它比其他两个都要慢)。

接下来配置JSHint。
首先在ST3里面安装如下插件：Sublimelinter，SublimeLinter-jshint和SublimeLinter-csslint.
然后在nodejs里面安装如下包：jshint和csslint.
最后如果你的nodejs安装路径不是默认安装路径的话，建议把nodejs的路径加到环境变量里面，比如说我就在path里面加入`;D:/Program Files/nodejs/node.exe`。

然后可以看情况配置ESLint。安装ESLint插件即可。然后在ESLint的配置文件中输入：

```
{
  "node_path": "D:\\Program Files\\nodejs",
  "node_modules_path": "C:\\Users\\zhou\\AppData\\Roaming\\npm\\node_modules",
  "config_file": "D:\\test\\.eslintrc.json"
}
```
其中json文件内容如下：

```
{
 "env": {
 "browser": true,
 "es6": true,
 "node": true
 },
 "parserOptions": {
 "sourceType": "module"
 },
 "rules": {
 "no-cond-assign": [2, "always"], //if, while等条件中不允许使用“=”
 "no-constant-condition": 2,
 "no-debugger": 2, // 程序中不能出现debugger
 "no-dupe-args": 2, // 函数的参数名称不能重复
 "no-dupe-keys": 2, // 对象的属性名称不能重复
 "no-duplicate-case": 2, // switch的case不能重复
 "no-func-assign": 2,
 "no-obj-calls": 2,
 "no-regex-spaces": 2,
 "no-sparse-arrays": 2,
 "no-unexpected-multiline": 2,
 "no-unreachable": 2,
 "use-isnan": 2,
 "valid-typeof": 2,
 "eqeqeq": [2, "always"],
 "no-caller": 2,
 "no-eval": 2,
 "no-redeclare": 2,
 "no-undef": 2,
 "no-unused-vars": 1,
 "no-use-before-define": 2,
 "comma-dangle": [1, "never"],
 "no-const-assign": 2,
 "no-dupe-class-members": 2
 }
}
```

#### TrailingSpaces ####
检测并一键去除代码中多余的空格。
