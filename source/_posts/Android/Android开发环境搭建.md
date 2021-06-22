---
title: Android开发环境搭建
date: 2019-10-24 13:46:30
tags: Android
categories: Android
---

> Android（美国谷歌公司开发的移动操作系统）

`Android`（安卓）是一种基于`Linux`内核（不包含`GNU`组件）的自由及开放源代码的`操作系统`。主要使用于`移动设备`，如`智能手机`和`平板电脑`，由美国`Google`公司和`开放手机联盟`领导及开发。上线时间:`2008年9月23日`

<!-- more -->

## Android开发环境搭建（Windows）

* 四步骤完成Android开发环境的搭建

> 1、下载安装JDK  
2、配置Windows上JDK的变量环境  
3、下载安装Android Studio  
4、下载安装Android SDK

### 一、JDK安装

JDK的全称是Java SE Development Kit，也就是Java 开发工具箱。SE表示标准版。JDK是Java的核心，包含了Java的运行环境（Java Runtime Environment），一堆Java工具和给开发者开发应用程序时调用的Java类库。

JDK下载地址：<https://www.oracle.com/technetwork/java/javase/downloads/index.html>

### 二、JDK环境变量

> 详细步骤配置参考：<https://www.runoob.com/java/java-environment-setup.html>

为了配置JDK的系统环境变量，我们需要设置三个系统变量，分别是JAVA_HOME，Path和CLASSPATH。下面是这三个变量的设置范例：

`JAVA_HOME`
先设置这个系统变量名称，变量值为JDK在你电脑上的安装路径：`C:\Program Files\Java\jdk1.8.0_20`。创建好后则可以利用%JAVA_HOME%作为JDK安装目录的统一引用路径。

`Path`
PATH属性已存在，可直接编辑，在原来变量后追加：`;%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin`。

`CLASSPATH`
设置系统变量名为：CLASSPATH  变量值为：`.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar` 。
注意变量值字符串前面有一个"."表示当前目录，设置CLASSPATH 的目的，在于告诉Java执行环境，在哪些目录下可以找到您所要执行的Java程序所需要的类或者包。

### 三、安装Android Studio

Android Studio 下载地址：<https://developer.android.google.cn/studio>

### 四、安装Android SDK

Android Studio中下载Android SDK，翻墙除外

参考方法：<https://blog.csdn.net/qq_23599965/article/details/80910202>

方式一、设置HTTP Proxy，反正我没成功过

设置 Host name 为：mirrors.neusoft.edu.cn  
设置 Port number 为：80

方式二、 更改hosts文件
  
得取消设置HTTP Proxy，为了方便Hosts文件下载地址：<https://github.com/googlehosts/hosts> 可直接替换掉hosts文件

hosts系统文件地址：C:\WINDOWS\System32\drivers\etc\hosts

后面就轻松多了。。。。。。

注明：Android相关下载工具地址：<https://www.androiddevtools.cn/>
