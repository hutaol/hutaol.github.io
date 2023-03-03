---
title: Mac工具
date: 2023-03-03 10:00:00
tags: Mac
categories: Mac
---

> **Homebrew** 包管理工具

安装/卸载/更新各种软件包，如：nodejs, elasticsearch, kibana, mysql, mongodb 等等，快速搭建各种本地环境，程序员必备工具

<!-- more -->

## 安装brew

```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## 基本用法

以 nodejs 为例，安装目录在 /usr/local/Cellar

```shell
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

## Homebrew更换国内镜像源

参考：https://blog.csdn.net/xiewanchen0708/article/details/128232697

查看 brew.git 当前源

`cd "$(brew --repo)" && git remote -v`

查看 homebrew-core.git 当前源

`cd "$(brew --repo homebrew/core)" && git remote -v`


切换 Homebrew 镜像源为中科大镜像源

替换brew.git:

`cd "$(brew --repo)" && git remote set-url origin https://mirrors.ustc.edu.cn/brew.git`

替换homebrew-core.git:

`cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" && git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git`

替换homebrew-cask.git:

`cd "$(brew --repo)/Library/Taps/homebrew/homebrew-cask" && git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-cask.git`

zsh 替换homebrew-bottles镜像，Mac OS在10.15系统开始，默认的shell都换成了zsh

`echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.aliyun.com/homebrew/homebrew-bottles' >> ~/.zshrc`

修改使其立即生效

`source ~/.zshrc`

bash 替换homebrew-bottles镜像

`echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.aliyun.com/homebrew/homebrew-bottles' >> ~/.bash_profile`

修改使其立即生效

`source ~/.bash_profile`

刷新源

`brew update`

## brew 关闭自动更新

参考：https://www.jianshu.com/p/3e413524c79a

```shell
export HOMEBREW_NO_AUTO_UPDATE=true
```