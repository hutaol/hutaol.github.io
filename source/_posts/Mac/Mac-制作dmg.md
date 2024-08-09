---
title: Mac-制作dmg
date: 2024-07-10 10:00:00
tags: Mac
categories: Mac
---

https://zhuanlan.zhihu.com/p/56864296

```shell
cd /Volumes/timeGO

# 创建应用程序快捷方式
ln -s /Applications Applications

# 隐藏图标文件和背景图：
chflags hidden AppIcon.icns
chflags hidden dmg.png 
```
