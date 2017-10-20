在编写脚本中，经常会使用"``"（back quote）符号来来执行指令（命令替换），作用是将命令的输出替换到字符串或者变量中。

例如以下命令获取版本号存放到变量`redhat_version`中便于脚本中引用：

```bash
redhat_version=`cat /etc/redhat-release`
```

但是，需要注意的是，使用 "``" 符号执行指令会fork出脚本子进程来执行，也就是说，如果在脚本 test.sh 使用 back quote符号，此时会在系统中又出现一个 test.sh 名称的子进程。

虽然一般没有影响，但是在某些情况下，会在脚本中统计系统中有多少个"自己"的进程数量（主要是为了防止重复执行脚本，所以统计脚本进程数，超过指定数量禁止再启动新的脚本进程），就需要注意这个因素。