---
title: Android-ADB
date: 2014-06-13 13:46:30
tags: Android
categories: Android
---

## ADB

```shell
# 查看所有安装的包
adb shell pm list packages
# 查看安装的第三方app的包名
adb shell pm list packages -3
# 查看启动的app的包名
adb shell dumpsys activity top | find "ACTIVITY"
adb shell dumpsys activity activities | findstr "Run"

# 获取正在运行应用的activity
adb shell dumpsys package 包名
# 启动app 包名/activity
adb shell {device} am start -n {包名/activity}'
```
