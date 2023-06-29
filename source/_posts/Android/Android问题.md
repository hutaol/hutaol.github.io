---
title: Android问题
date: 2022-10-17 14:32:40
tags: Android
---

## 1. Android9，http适配，解决不能使用http协议

<!-- more -->

Android9开始原生不支持http协议需要适配  

`res`目录下创建xml目录，xml目录里面新建xml文件，名字叫 `network_security_config.xml`
  
文件内容如下

```xml
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
    <base-config cleartextTrafficPermitted="true" />
</network-security-config>
```

修改清单文件`application`头标签加入属性

```xml
android:networkSecurityConfig="@xml/network_security_config"
```
