---
title: Linux系统命令
date: 2018-12-15 21:16:47
tags:
categories: Linux
---

Unix/Linux 系统中的 Operation Not Permitted 问题

<!-- more -->

OS X EI Capitan 的 SIP

Apple 在 OS X 10.11 以后的版本中默认启动了一项系统保护程序，叫做 System Integrity Protection，也被唤作 rootless（寓意让 root 弱一点），该程序意在保护电脑不被恶意程序攻击，但是对于我们这群程序员，很多保护是多余的，甚至给我们带来了很多麻烦。

SIP 会锁定几个系统文件目录：

```shell
/System
/sbin
/usr （/usr/local 除外）
```

在 SIP 的保护下，部分软件、功能、脚本都会失效，我们可以通过如下步骤关闭 SIP：

重启电脑，按下 Command + R 直到听到开机声音，此时电脑会进入恢复模式（Recovery Mode）
当 OSX 工具出现在屏幕中时，下拉工具（Utilities）菜单，选择终端（Terminal）
键入 csrutil disable，回车
电脑重启后，SIP 就关闭了

恢复 SIP 的方式同上，只不过终端中键入 csrutil enable。通过 csrutil status 可以检测系统当前 SIP 的启动状态：

```shell
$ csrutil status
System Integrity Protection status: enabled.
```

**参考：** <https://www.barretlee.com/blog/2016/04/06/operation-not-permitted-problem-in-linux-or-unix-system/>
