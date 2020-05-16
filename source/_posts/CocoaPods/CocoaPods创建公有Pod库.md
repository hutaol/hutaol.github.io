---
title: CocoaPods创建公有Pod库
date: 2019-03-08 11:50:31
tags: 
categories: CocoaPods
---

## 1.注册CocoaPods账号信息

> pod trunk register 邮箱地址 用户名 --verbose

在邮箱中收到确认邮箱，在浏览器中点击链接确认即注册成功

查看注册信息及自己开源pod库

> pod trunk me

## 2.Github创建仓库（略）

## 3.创建共享库文件并上传到公有仓库

> pod lib create 库名

配置*.podspec文件

## 4.推送到远程仓库

## 5.打tag, 发布一个release版本

> git tag -m 'first release' '1.0.1'
> git push --tags #推送tag到远端仓库

## 6.trunk push pod

> pod trunk push TestPod.podspec --allow-warnings

## 7.search pod

> pod search TestPod 检验是否可用

* 问题

> [!] Unable to find a pod with name, author, summary, or description matching `TestPod`

* 解决办法

> rm ~/Library/Caches/CocoaPods/search_index.json