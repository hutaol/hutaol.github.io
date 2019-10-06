---
title: iOS持久化方式
date: 2018-12-16 22:34:06
tags:
categories: iOS
---

### iOS持久化方式

>1.NSUserDefaults
>2.NSKeyedArchiver
>3.沙盒Document
>4.sqlite3
>5.KeyChain

持久化分为两类：沙盒内和沙盒外。

#### 一、沙盒目录结构和各个目录的路径获取方法

>**AppName.app**:  应用程序包目录

>**Documents**：存储用户数据，您应该将所有的应用程序数据文件写入到这个目录下。该路径可通过配置实现iTunes共享文件。会被iTunes同步。

>**Library**：有两个子目录Preferences和Caches，除Caches以外，都会被iTunes备份。
>>**Preferences**：包含应用程序的偏好设置文件。您不应该直接创建偏好设置文件，而是应该使用NSUserDefaults类来取得和设置应用程序的偏好。结果在目录下面以plist的方式存储
>>**Caches**：用于存放应用程序专用的支持文件，保存应用程序再次启动过程中需要的信息。可创建子文件夹。可以用来放置您希望被备份但不希望被用户看到的数据。

>**SystemData**：系统数据

>**tmp**：用来存放应用再次启动时不需要的临时文件，该目录下的东西随时可能被系统清理掉，不会被iTunes同步。

##### 沙盒主目录
```
NSString *homeDir = NSHomeDirectory();
```

##### Documents目录
```
NSString *documentsDir = [NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES) firstObject];
```

##### Library目录
```
// 获取Library的目录路径
NSString *libraryDir = [NSSearchPathForDirectoriesInDomains(NSLibraryDirectory, NSUserDomainMask, YES) firstObject];

// 获取Caches目录路径
NSString *cachesDir = [NSSearchPathForDirectoriesInDomains(NSCachesDirectory, NSUserDomainMask, YES) firstObject];
```

##### tmp目录
```
NSString *tmpDir =  NSTemporaryDirectory();
```

##### AppBundle目录路径
```
// 获取AppBundle目录路径
NSLog(@"%@",[[NSBundle mainBundle] bundlePath]);
 
NSString *imagePath = [[NSBundle mainBundle] pathForResource:@"apple" ofType:@"png"];
 
UIImage *appleImage = [[UIImage alloc] initWithContentsOfFile:imagePath];
```

#### 二、沙盒内的持久化方式
**NSKeyedArchiver** 归档








