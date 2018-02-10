[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:35:26)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:35:37)

# EXCEL在改动某几个单元格时隐藏空列 #

## 概述 ##

今天我哥来找我帮他搞下excel表格，本着程序猿对程序无所不能的精神，我爽快的答应了。结果查了半天才搞定。现在记录在此，供自己以后参考，相信对其他人也有用。

PS：这几天正在弄博客，马上就要弄完啦，弄完就把这些手记搬到博客上面啦！

### 说明 ###

EXCEL的条件格式不能改变单元格的高宽，不能删掉单元格，不能隐藏单元格。

要实现这些功能需要用VBA编写宏，其中用到了EXCEL的Change事件。

EXCEL的Change事件是当改变单元格时自动运行的，不需要绑定按钮。

### 用法 ###

右键点击工作表的标签，然后点击“查看代码”，然后分别选择“Worksheet”和“Change”，如下图。最后贴入代码即可。

![图片描述][1]
![图片描述][2]

### 代码 ###

以下代码将更改的单元格的颜色设为蓝色。

```
Private Sub Worksheet_Change(ByVal Target as Range) 
    Target.Font.ColorIndex = 5 
End Sub
```

以下代码将在改动EXCEL的C1单元格和G1单元格时，隐藏D4到AH4列之间的空列

```
Private Sub Worksheet_Change(ByVal Target As Range)
    Dim abc As String
    Dim rng As Range
    abc = Target.Address
    If abc = "$C$1" Or abc = "$G$1" Then
        For Each rng In [D4:AH4]
            If rng.Value = "" Then
                rng.EntireColumn.Hidden = True
            Else
                rng.EntireColumn.Hidden = False
            End If
        Next
    End If
End Sub
```

注意：`Private Sub Worksheet_Change(ByVal Target As Range)`这一行不能改动；其中Target 就表示你改动的单元格。


  [1]: //img.mukewang.com/5a733e930001454203480395.jpg
  [2]: //img.mukewang.com/5a733caa00016c2608480153.jpg
