---
title: H5唤起App
date: 2024-01-16 22:05:18
tags:
---

* URL Scheme（通用）
* Universal Link （iOS）
* App Link、Chrome Intents（android）

参考：https://blog.csdn.net/qq_41960279/article/details/124817190

<!-- more -->

## URL Scheme（通用）

URL Scheme 组成， 一般由协议名、路径、参数组成

[scheme:][//authority][path][?query][#fragment]

常用APP的 URL Scheme

| App        | 微信       | 支付宝 | 淘宝 | QQ | 知乎 | 微博 |
| --         | --        | --    | --   | -- | --  | -- |
| URL Scheme | weixin:// | alipay:// | taobao:// | mqq:// | zhihu:// | sinaweibo:// |

常用的 URL Scheme 格式

```c
     行为(应用的某个功能)    
            |
scheme://[path][?query]
   |               |
应用标识       功能需要的参数
```

打开方式

直接通过window.location.href跳转

```js
window.location.href = 'weixin://'
```

通过iframe跳转

```js
const iframe = document.createElement('iframe')
iframe.style.display = 'none'
iframe.src = 'weixin://'
document.body.appendChild(iframe)
```

直接使用a标签进行跳转

```js
<a href="weixin://">打开app</a>
```

通过js bridge来打开

```js
window.miduBridge.call('openAppByRouter', {url: 'weixin://'})
```

缺点：无法准确判断是否唤起成功
ios上确认弹窗提示用户是否打开

## Universal Link （iOS） iOS 9以上

直接通过https协议的链接来打开 APP

让 APP 支持 Universal Link

1. 拥有一个支持 https 的域名
2. 在 开发者中心 ，Identifiers 下 AppIDs 找到自己的 App ID，编辑打开 Associated Domains 服务。
3. 打开工程配置中的 Associated Domains ，在其中的 Domains 中填入你想支持的域名，必须以 applinks: 为前缀
4. 配置 apple-app-site-association 文件，文件名必须为 apple-app-site-association ，不带任何后缀
5. 上传该文件到你的 HTTPS 服务器的 根目录 或者 .well-known 目录下

apple-app-site-association

```c
{
    "applinks": {
        "apps": [],
        "details": [
            {
                "appID": "BQNXB4G3KQ.com.henry.app",
                "paths": [ "*" ]
            }
        ]
    }
}
```

## App Link、Chrome Intents（Android）

国内的支持相对较差

H5插件：https://github.com/suanmei/callapp-lib