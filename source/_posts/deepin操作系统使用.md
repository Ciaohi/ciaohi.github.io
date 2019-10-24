---
title: deepin操作系统使用
date: 2019-10-23 19:34:36
tags: [deepin,linux]
---

## 安装软件命令

- sudo apt install snapd
- sudo snap install --classic notepadqq

## 数据盘路径

- media ciao dd

## 获得root权限

- sudo -i

## deepin安装notepad

- apt-get install software-properties-common

Notepad++鼎鼎大名就不多说了吧，但是如果需要在Linux环境下使用需要Wine来实现。推荐一个Notepad++的替代品 — Notepadqq，基本上就是Notepad++的复制品，无论是界面还是功能来说，都和Notepad++十分相似。

$ sudo add-apt-repository ppa:notepadqq-team/notepadqq

$ sudo apt-get update

$ sudo apt-get install notepadqq

add-apt-repository指令出现出错，即：找不到命令

apt-get install software-properties-common
————————————————
版权声明：本文为CSDN博主「汉明图」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/Scott_kang/article/details/92779149
