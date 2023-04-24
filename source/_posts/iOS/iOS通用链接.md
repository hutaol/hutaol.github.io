---
title: iOS通用链接
date: 2023-04-21 11:02:42
tags:
---

## iOS Associated Domains


1. 服务器配置 `apple-app-site-association`, 此文件需放在网站域名根目录或.well-known下，域名必须支持 HTTPS

> iOS会先请求https://domain.com/.well-known/apple-app-site-association，如果此文件请求不到，再去请求https://domain.com/apple-app-site-association，所以如果想要避免服务器接收过多GET请求，可以直接把apple-app-site-association放在./well-known目录下


```f
{
    "applinks": {
        "apps": [],
        "details": [
            {
                "appID": "TeamID.BundleID",
                "paths": ["/app/*"]
            },
            {
                "appID": "TeamID.BundleID",
                "paths": ["*", "/qq_conn/QQ申请下来的APPID/*"] 
            }
        ]
    }
}
```

> "appID": 开发者团队ID与bundle id的组合, 
> "paths": 配置可以跳转的路径。可以域名下的所有路径，也可以具体到某个页面。

**注意**

> appID

查找app，查看描述文件embedded.mobileprovision，application-identifier即为appID

`Xcode`->`Product`->`Show Build Folder in Finder`->`Products`->`Debug-iphoneos` 

app显示包内容，找到描述文件`embedded.mobileprovision`里的application-identifier: 26ZXN84639.com.tsl3060.www

> 确保`apple-app-site-association`可以访问下载文件

地址`https://domain.com/.well-known/apple-app-site-association`或者`https://domain.com/apple-app-site-association`


2. Xcode配置Associated Domains（域名）

> 在项目Target下，添加`Capabilities` -> `Associated Domains` -> 设置domain为：`applinks:xxx.xxx.com`

3. 在AppDelegate中实现

```oc
- (BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler {
    // 在此方法中添加响应处理
    return YES;
}
```

4. 验证通用链接

在iOS设备中的备忘录中输入App能识别的链接，然后直接点击此链接，就会直接跳转到你的app

参考：`https://blog.csdn.net/forzhouwei/article/details/120648371`

## UniApp 通用链接配置

参考 `https://ask.dcloud.net.cn/article/36393#unilink`

使用HBuilderX云端打包时在manifest.json中配置域名

> 在"plus" -> "distribute" -> "apple" -> "capabilities" -> "entitlements"节点（uni-app项目在"app-plus" -> "distribute" -> "ios" -> "capabilities" -> "entitlements"）下添加"com.apple.developer.associated-domains"字段，字段值为字符串数组，每个字符串为要关联的域名

```f
    "capabilities": {  
        "entitlements": {  
            "com.apple.developer.associated-domains": [  
                "applinks:demo.dcloud.net.cn"  
            ]  
        }  
    }
```

苹果指南 <https://developer.apple.com/library/archive/documentation/General/Conceptual/AppSearch/UniversalLinks.html>
微信接入指南 <https://developers.weixin.qq.com/doc/oplatform/Mobile_App/Access_Guide/iOS.html>
QQ接入指南 <https://wiki.connect.qq.com/>



