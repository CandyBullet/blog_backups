[^_^]: # ( -*- coding: utf-8 -*-)
[^_^]: # ( @Author: yang zhou)
[^_^]: # ( @Date:   2018-02-10 12:23:50)
[^_^]: # ( @Last modified by:   yang zhou)
[^_^]: # ( @Last Modified time: 2018-02-10 12:24:26)

# 完美解决打开github速度慢的问题 #

摘抄自知乎。

修改hosts（HOSTS文件路径：C:\Windows\System32\drivers\etc\hosts）

1.打开[Dns检测|Dns查询 - 站长工具][1]

2.在检测输入栏中输入[http://github.com][2]官网

3.把检测列表里的TTL值最小的IP输入到hosts里，并对应写上github官网域名。

例如：

192.30.255.112 github.com

192.30.255.113 www.github.com

192.30.255.120 nodeload.github.com


  [1]: http://tool.chinaz.com/dns/
  [2]: http://github.com
