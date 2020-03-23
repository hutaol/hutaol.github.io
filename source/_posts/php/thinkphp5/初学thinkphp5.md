---
title: 初学thinkphp5
date: 2020-03-23 17:28:39
tags:
categories: php
---

## php环境的搭建

使用`phpstudy`集成环境

开发手册：https://www.kancloud.cn/manual/thinkphp5/118003

入口为`public/index.php`

如何需要隐藏`public/index.php`，则需要配置入口，有很多方法，才疏学浅，目测了一种方法

* 使用`.htaccess`来实现URL重定向

在根目录下创建文件`.htaccess`，`public`目录下删除`.htaccess`文件，`.htaccess`内容如下：

```htaccess
<IfModule mod_rewrite.c>
  Options +FollowSymlinks -Multiviews
  RewriteEngine On

  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteRule ^(.*)$ public/index.php?/$1[QSA]
</IfModule>
```

## 多模块

命令行：https://www.kancloud.cn/manual/thinkphp5/118021

默认的框架的根目录下面自带了一个`build.php`，用于自动生成的规则定义文件

读取application下面的build.php作为自动生成的定义文件
> php think build

读取根目录下的build.php文件
> php think build --config build.php

* 快速生成模块

> php think build --module admin

* 快速生成控制器类

生成index模块的Blog控制器类库文件
> php think make:controller index/Blog

> php think make:controller index\Blog --plain

* 快速生成模型类

生成index模块的Blog模型类库文件
> php think make:model index/Blog
