---
title: 解决GitHub下载速度缓慢
date: 2019-07-02 16:36:12
tags:
categories: Other
---

# 一、修改本机的Hosts

1. Hosts文件的路径:

```path
// Windows

C:\Windows\System32\drivers\etc

// Mac
sudo vim /etc/hosts
```

2. 追加域名的IP地址
 
可以利用`https://www.ipaddress.com/`获得以下两个GitHub域名的IP地址

`github.com`  

`github.global.ssl.fastly.net`

```n
192.30.253.112 github.com
151.101.185.194 github.global.ssl.fastly.net
```


