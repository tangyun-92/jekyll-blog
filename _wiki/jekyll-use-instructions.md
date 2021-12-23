---
layout: wiki
title: jekyll 本地运行方式
cate1: Basis
cate2: Jekyll
description: "jekyll 本地运行方式"
keywords: Jekyll
---


确保已安装`Ruby 2.1.0` 或更高版本：

```bash
ruby --version
```

安装`Bundler`：

```bash
gem install bundler
```

安装依赖：

```bash
bundle install
```

运行 Jekyll：

```bash
bundle exec jekyll server
```

此时即可使用浏览器访问 `http://localhost:4000`，检查站点是否正确运行。



