---
title: Mac工具
date: 2019-07-02 16:10:10
tags:
categories: Mac
---

# Mac 必备工具

## Homebrew 包管理工具

安装/卸载/更新各种软件包，如：nodejs, elasticsearch, kibana, mysql, mongodb 等等，快速搭建各种本地环境，程序员必备工具

### 安装 brew

```u
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### 基本用法

以 nodejs 为例，安装目录在 /usr/local/Cellar

```brew
// 安装 nodejs
brew install nodejs

// 更新
brew upgrade nodejs

// 卸载
brew remove nodejs

// 列出当前安装的软件
brew list

// 查询与 nodejs 相关的可用软件
brew search nodejs

// 查询 nodejs 的安装信息
brew info nodejs
```

**注：** 如果需要指定版本，可以在`brew search`查看有没有需要的版本，在`@`后面指定版本号，例如`brew install thrift@0.9`

## npm nodejs的包管理器

用于node插件管理（包括安装、卸载、管理依赖等）, NPM是随同NodeJS一起安装的包管理工具

安装npm 或者直接安装nodejs

```brew
brew install npm
```

nodejs官网链接下载安装 https://nodejs.org/

