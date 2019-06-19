---
title: git
date: 2019-05-23 09:19:13
tags:
categories:
---

## Git

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
