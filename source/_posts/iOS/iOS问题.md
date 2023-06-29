---
title: iOS问题
date: 2022-10-17 14:32:50
tags: iOS
---

## 1. 改变View显示位置，2种方式 (layer的Z轴和view添加的层级)

<!-- more -->

+ 改变layer的Z轴, 大值在上，但下层的view显示在上面，不能响应事件

> view.layer.zPosition=100  

+ view添加的层级

> insertSubview
> bringSubviewToFront
> addSubview  
> insertSubview

## 2. ITSAppUsesNonExemptEncryption导出合规性

此值表示该应用程序不使用加密，或仅使用免除加密。如果您的应用使用加密且不可免除，则必须将此值设置为YES/true。

`info.plist`添加

> App Uses Non-Exempt Encryption = NO

## UIDocumentPickerViewController 选取文件

```ios
"com.microsoft.word.doc",
"com.microsoft.word.docx",
"com.microsoft.excel.xls",
"com.microsoft.excel.xlsx",
"com.microsoft.powerpoint.​ppt",
"com.microsoft.powerpoint.​pptx",
```

设置了 docx， xlsx，​pptx   发现还是 只能选择 .doc  .xls  .ppt，无法选择 docx， xlsx，​pptx，均为灰色不可选择：

后来谷歌发现对应的格式不对：下面才是 正确的对应 格式

```ios
"com.microsoft.word.doc",
"org.openxmlformats.wordprocessingml.document",
"com.microsoft.excel.xls",
"org.openxmlformats.spreadsheetml.sheet",
"com.microsoft.powerpoint.​ppt",
"org.openxmlformats.presentationml.presentation",
```

## 圆角与阴影

方法一：指定UIView的根 layer 为 CAShapeLayer 类型，通过设置 layer.path 实现圆角,这时的path是CGPath类型，CGPath 非常灵活，fillColor 当做背景填充色，strokeColor 从当边框颜色，使用 layer.path 作为 shadowPath 一举两得。  

方法二：利用2个UIView实现，父视图为阴影，添加一个ContentView子视图为圆角

+ 1. UIView 的 clipsToBounds 属性设置为 true，会把超出视图范围外的部分裁剪掉不显示，若要使 圆角和阴影共存，那么 clipsToBounds 必须设置为 false，庆幸的是UIView 的 clipsToBounds属性值默认为false

+ 2. 使用layer的mask来给UIView 切圆角会把超出mask范围外的部分裁剪掉，若要使圆角与阴影共存，此方法不可取。

+ 3. 让设计师切一张带阴影的背景图，这个方法简单粗暴。

### 圆角的绘制方法

+ 1. 使用 CAlayer 的 cornerRadius 属性设置圆角
+ 2. 设置 CAlayer 的 mask 属性
+ 3. 通过 layerClass 返回 CAShapeLayer,指定当前 UIView 的根 layer 类型，通过设置 CAShapeLayer 的 path 来实现圆角绘制

### 阴影的绘制方法

+ 1. 不指定 shadowPath绘制阴影，会造成离屏渲染
+ 2. 指定 shadowPath 绘制阴影，不会造成离屏渲染，在view使用自动布局的情况下，不好指定 shadowPath，可以通过重写 UIView 的 layoutSubviews 方法动态指定 shadowPath 的路径，实现过程相对麻烦

### Xcode 10之后删除的libstdc++库

`https://github.com/devdawei/libstdc-`
