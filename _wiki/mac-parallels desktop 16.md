---
layout: wiki
title: Parallels Desktop 16 完美解决无法联网
cate1: Basis
cate2: OS
description: "Parallels Desktop 16 完美解决无法联网，无法连接USB"
keywords: Mac
---

首先进入路径：/资源库/Preferences/Parallels/

我们将要修改如下两个文件

![img](/images/wiki/Parallels Desktop 16.png)

在 dispatcher.desktop.xml 中找到 "<Usb>0</Usb>" ，替换为 "<Usb>1</Usb>"

在 network.desktop.xml 中找到 "<UseKextless>1</UseKextless>"  或者 "<UseKextless>-1</UseKextless>"，替换为 "<UseKextless>0</UseKextless>"



然后彻底退出Parallels Desktop，再新打开虚拟机，发现问题解决了。

