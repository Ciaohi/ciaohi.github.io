---
title: Linux 常用命令详解
date: 2019-10-18 08:13:21
tags: Linux Commands
---

# ps 命令详解

## ps 概述

Linux中的ps命令是Process Status的缩写。ps命令用来列出系统中当前运行的那些进程。ps命令列出的是当前那些进程的快照，就是执行ps命令的那个时刻的那些进程，如果想要动态的显示进程信息，就可以使
用top命令。

### linux上进程有5种状态及对应的状态码

1.R运行(正在运行或在运行队列中等待)  runnable (on run queue)
2.S中断(休眠中, 受阻, 在等待某个条件的形成或接受到信号) sleeping
3.D不可中断(收到信号不唤醒和不可运行, 进程必须等待直到有中断发生) uninterruptible sleep (usually IO)
4.Z僵死(进程已终止, 但进程描述符存在, 直到父进程调用wait4()系统调用后释放)a defunct (”zombie”) process
5.T停止(进程收到SIGSTOP, SIGSTP, SIGTIN, SIGTOU信号后停止运行运行) traced or stopped


## ps使用

``` bash
用法: ps [参数]
```

### 参数说明

- a 显示一个终端的所有进程，除了会话引线
- u uid or username 选择有效的用户id或者是用户名
- x 显示没有控制终端的进程，同时显示各个命令的具体路径。dx不可合用。（utility）


## 示例:ps -aux

最常用的方法是ps -aux,然后再利用一个管道符号导向到grep去查找特定的进程,然后再对特定的进程进行操作。


# grep 命令详解

## grep 概述

grep (global search regular expression(RE) and print out the line,全面搜索正则表达式并把行打印出来)是一种强大的文本搜索工具，它能使用正则表达式搜索文本，并把匹配的行打印出来。


