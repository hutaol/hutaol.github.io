---
title: CocoaPods使用
date: 2023-06-29 01:02:55
tags: iOS
---

> CocoaPods（Xcode依赖库管理） `https://cocoapods.org/`

<!-- more -->

## 安装

1. 安装Homebrew

```sh
git clone https://github.com/Homebrew/brew homebrew

eval "$(homebrew/bin/brew shellenv)"
brew update --force --quiet
chmod -R go-w "$(brew --prefix)/share/zsh"
```

验证是否成功

```sh
brew -v
```

2. 使用Homebrew安装CocosPods

```sh
brew install cocoapods 
```

验证是否成功

```sh
pod --version
```

## 使用

install时查看进度

```shell
pod install --verbose --no-repo-update
```

复制
![参考](https://upload-images.jianshu.io/upload_images/2699846-98c29969b73d0e73.png)

新开终端窗口cd到复制的路径
输入命令：du -sh

## 创建公有Pod库

### 1.注册CocoaPods账号信息

> pod trunk register 邮箱地址 用户名 --verbose

在邮箱中收到确认邮箱，在浏览器中点击链接确认即注册成功

查看注册信息及自己开源pod库

> pod trunk me

### 2.Github创建仓库（略）

### 3.创建共享库文件并上传到公有仓库

创建库
> pod lib create 库名

只创建`podspec`文件
> pod spec create 库名

配置*.podspec文件

### 4.推送到远程仓库

### 5.打tag, 发布一个release版本

> git tag -m 'first release' '1.0.1'
> git push --tags #推送tag到远端仓库

### 6.trunk push pod

> pod trunk push TestPod.podspec --allow-warnings

### 7.search pod

> pod search TestPod #检验是否可用

* 问题

> [!] Unable to find a pod with name, author, summary, or description matching `TestPod`

* 解决办法

> rm ~/Library/Caches/CocoaPods/search_index.json

[podspec相关设置, 及其私有库常见错误记录](https://www.jianshu.com/p/5ab1e6d9ddc3)
[CocoaPods - Podspec文件配置讲解](https://www.jianshu.com/p/743bfd8f1d72)
