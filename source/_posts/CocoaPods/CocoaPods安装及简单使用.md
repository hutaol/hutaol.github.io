---
title: CocoaPods安装及简单使用
date: 2019-07-02 16:50:27
tags:
categories: CocoaPods
---

# CocoaPods ios 三方管理工具

## Ruby镜像 更换源

```gem
sudo gem update --system

gem sources --remove https://rubygems.org/

gem sources --add https://gems.ruby-china.com/

```

### 验证是否成功

```gem
gem sources -l

# success
*** CURRENT SOURCES ***

https://gems.ruby-china.com/

```

## 安装CocoaPods

`sudo gem install -n /usr/local/bin cocoapods`

## 安装本地库

`pod setup`

## CocoaPods的使用

使用终端cd进入Xcode工程根目录

创建Podfile文件：

```pod
pod init
```

编辑Podfile文件

```pod
vim Podfile
```

写入以下内容并保存 小提示：（终端vim文件 按 i 可编辑 ，esc 退出编辑，：wq  可保存退出）

添加相关库：

```pod
pod 'AFNetworking'
```

`:wq` 保持后退出

开始下载：

```pod
pod install
```

参考： https://www.jianshu.com/p/ab6411a05bc2