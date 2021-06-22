---
title: Git
date: 2019-05-23 09:19:13
tags: Git
categories: Git
---

> Git（分布式版本控制系统）

`Git`（读音为/gɪt/）是一个开源的分布式版本控制系统，可以有效、高速地处理从很小到非常大的项目版本管理。

<!-- more -->

### 丢弃本地修改

```git
git checkout . #本地所有修改的。没有的提交的，都返回到原来的状态
git stash #把所有没有提交的修改暂存到stash里面。可用git stash pop回复。
git reset --hard HASH #返回到某个节点，不保留修改。
git reset --soft HASH #返回到某个节点。保留修改

git clean -df #返回到某个节点
git clean 参数
    -n 显示 将要 删除的 文件 和  目录
    -f 删除 文件
    -df 删除 文件 和 目录

```

丢弃本地修改的所有文件（新增、删除、修改）

`git checkout . && git clean -xdf`

### 删除本地分支

```git
# 查看分支
git branch -a

# 删除本地分支
git branch -D <BranchName>

```

### 删除远程分支

```git
git push origin --delete <BranchName> 
```

### Tags

```git
git ls-remote --tags origin  # 查询远程tags

git tag  # 列出所有tag
git tag -l v1.* #列出符合条件的tag（筛选作用）

git tag v1  # 创建tag
git tag -a -m 'first version' v1  # 创建含标注tag
git tag -a f1bb97a(commit id) # 为之前提交打tag

git push origin --tags  # 推送所有本地tag到远程
git push origin v1  # 推送指定本地tag到远程

git tag -d v1  # 删除本地指定tag
git push origin :refs/tags/v1 # 删除远程指定tag

git fetch origin v1 # 拉取远程指定tag
git show v1 # 显示指定tag详细信息

git tag -l | xargs git tag -d  # 删除所有本地分支
git fetch origin --prune  # 从远程拉取所有信息

```

### Git忽略文件

创建`.gitignore`文件

忽略文件的原则是：

1. 忽略操作系统自动生成的文件，比如缩略图等；
2. 忽略编译生成的中间文件、可执行文件等，也就是如果一个文件是通过另一个文件自动生成的，那自动生成的文件；
3. 就没必要放进版本库，比如Java编译产生的.class文件；
4. 忽略你自己的带有敏感信息的配置文件，比如存放口令的配置文件。

例如：

```git
*.xcuserstate
project.xcworkspace
xcuserdata
UserInterfaceState.xcuserstate
project.xcworkspace/
xcuserdata/
UserInterface.xcuserstate
```

如果存在文件，需要先清理缓存文件 git rm --cached xx
或者找到文件后删除它，然后commit， push。

### Git合并分支&取消合并

```git
// 合并分支dev
git merge dev
// 取消合并
git merge --abort
```
