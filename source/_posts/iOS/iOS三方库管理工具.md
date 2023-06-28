---
title: iOS三方库管理工具
date: 2022-12-22 16:22:22
tags: iOS
---

## CocoaPods, Carthage, Swift Package Manager

<!-- more -->

OC开发的话推荐使用`cocoapods`
用swift开发的话推荐使用`carthage`

### CocoaPods

CocoaPods是OSX和iOS下的一个第三方开源类库管理工具

安装

Ruby镜像，更换源

```sh
sudo gem update --system
gem sources --remove https://rubygems.org/
gem sources --add https://gems.ruby-china.com/

gem sources -l
```

```sh
sudo gem install -n /usr/local/bin cocoapods

pod setup
```

使用

创建文件`Podfile`

```sh
pod init
```

编辑文件 `vim Podfile`，在相应的位置添加以下内容保存

```sh
pod 'AFNetworking'
```

加载

```sh
pod install
```

需使用`project.xcworkspace`打开项目

参考：<https://www.jianshu.com/p/ab6411a05bc2>
参考：<https://www.jianshu.com/p/d40ac1f18f92>

### Carthage

Carthage使用Swift语言编写，只支持动态框架，iOS8以上，是一个去中心化的Cocoa依赖管理工具。

安装

```sh
brew install carthage
```

使用

创建文件`Cartfile`

```sh
touch Cartfile
```

编辑文件 `vim Cartfile`，添加以下内容保存

```sh
github "Alamofire/Alamofire"
```

更新

```sh
# 平台ios，框架xcframeworks
carthage update --platform iOS --use-xcframeworks
```

添加

项目 -> General -> Frameworks 导入XCFramework即可，选择Embed & sign

参考：<https://www.codetd.com/article/13755148>
