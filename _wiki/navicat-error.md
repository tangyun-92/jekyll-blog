---
layout: wiki
title: navicat连接数据库报错2059-AUTHENTICATION PLUGIN...错误解决方法
cate1: Basis
cate2: navicat
description: "Parallels Desktop 16 完美解决无法联网，无法连接USB"
keywords: navicat
---



出现这个错误的原因是因为MySQL8.0以上数据库使用的加密方式是：caching_sha2_password；

我们可以使用如下命令查看一下加密信息：show variables like 'default_authentication_plugin';

![img](/images/wiki/navicat-error.png)

在Navicat不支持MySQL8.0以上的这种用户登录账户加密方式，所以下面我们要修改root账户的加密方式为【mysql_native_password】。

使用如下指令：

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '密码';
```

修改成功之后，就可以使用navicat连接了。

