---
title: Xcode工具
date: 2018-12-16 22:12:51
tags:
categories: Xcode
---

1.查找未使用的Objective-C导入。

### [fui](https://github.com/dblock/fui)

```shell
gem install fui  // 安装

fui help  // 帮助

fui find  // 在当前目录中查找未使用的类
```

2.一键查找Xcode中所有中文

![图片](https://upload-images.jianshu.io/upload_images/1282916-2d99682ee717dc66.png)

按如图所示，点击，然后输入：

`@"["]*[\u4E00-\u9FA5]+["\n]*?"`

进行搜索

3.自定义代码块

创建代码块

> 代码编辑区右击 -> Create Code Snippet

删除代码块

> 选中要删除的代码块，按键delete，确定Delete

参数规则

```oc
<#param#>
```

**`Xcode`自定义代码块位置**

>~/Library/Developer/Xcode/UserData/CodeSnippets

定义过的代码块，可拷贝到该目录下使用，或者在这个文件夹下建一个Git仓库，到哪都可以用。

<https://github.com/hutaol/XcodeCodeSnippet>