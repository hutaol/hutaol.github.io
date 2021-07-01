---
title: Linux命令
date: 2018-12-15 21:16:47
tags: Linux
categories: Linux
---

> Linux命令

<!-- more -->

## 常用命令

> **ls** 列出目录

```shell
ls -a   // 全部的文件，连同隐藏档( 开头为 . 的文件) 一起列出来
ls -d   // 仅列出目录本身，而不是列出目录内的文件数据
ls -l   // 长数据串列出，包含文件的属性与权限等等数据
ls -al  // 将该目录下的所有文件列出来(含属性与隐藏档)
```

> **cd** 切换目录

```shell
cd .    // 当前目录
cd ..   // 回上一级目录
```

> **pwd** 显示目前的目录  

```shell
pwd
```

> **mkdir** 创建一个新的目录 `mkdir [-p] dirName`

```shell
mkdir       // 创建目录
mkdir -m    // 配置文件的权限
mkdir -p    // 可创建多层目录
```

> **rmdir** 删除一个空的目录 `rmdir [-p] dirName`

```shell
rmdir      // 删除空目录
rmdir -p   // 多层删除空目录
```

> **cp** 复制文件或目录 `cp [options] source dest`

```options
-a：在复制目录时使用，它保留链接、文件属性，并复制目录下的所有内容,相当于-pdr参数组合（常用）

-d：若来源档为连结档的属性(link file)，则复制连结档属性而非文件本身；

-f：为强制(force)的意思，若目标文件已经存在且无法开启，则移除后再尝试一次；

-i：若目标档(destination)已经存在时，在覆盖时会先询问动作的进行(常用)

-l：不复制文件，只是生成链接文件；

-p：连同文件的属性一起复制过去，而非使用默认属性(备份常用)；

-r：递归持续复制，用于目录的复制行为；(常用)

-s：复制成为符号连结档 (symbolic link)，亦即『捷径』文件；

-u：若 destination 比 source 旧才升级 destination ！
```

> **rm** 移除文件或目录 `rm [options] name`

```shell
rm -rf  // 强制移除目录及其子目录
-f ：就是 force 的意思，忽略不存在的文件，不会出现警告信息；
-i ：互动模式，在删除前会询问使用者是否动作
-r ：递归删除啊！
```

> **mv** 移动文件与目录，或修改文件与目录的名称 `mv [options] source dest`

```shell
-f ：force 强制的意思，如果目标文件已经存在，不会询问而直接覆盖；
-i ：若目标文件 (destination) 已经存在时，就会询问是否覆盖！
-u ：若目标文件已经存在，且 source 比较新，才会升级 (update)
```

## 系统管理命令

```shell
stat        显示指定文件的详细信息，比ls更详细
who         显示在线登陆用户
whoami      显示当前操作用户
hostname    显示主机名
uname       显示系统信息
top         动态显示当前耗费资源最懂进程
ps          显示瞬间进程状态 ps -aux   （mac ： ps -au）
du          查看目录大小  du -h/home带有单位显示目录信息
df          查看磁盘大小  df -h带有单位显示磁盘信息 
ifconfig    查看网络情况
ping        测试网络连通
netstat     显示网络状态信息
man         命令不会用了  如：man ls
clear       清屏
alias       对命令重命名 如: alias showmeit="ps -aux", 解除使用 unalias showmeit
kill        杀死进程，可以先用ps或top命令查看进程的id，然后再用kill命令杀死进程
```

## 文件内容查看

> `cat`  由第一行开始显示文件内容  
`tac`  从最后一行开始显示，可以看出 tac 是 cat 的倒著写！  
`nl`   显示的时候，顺道输出行号！  
`more` 一页一页的显示文件内容  
`less` 与 more 类似，但是比 more 更好的是，他可以往前翻页！  
`head` 只看头几行  
`tail` 只看尾巴几行

## 查看系统内核

> `cat /proc/version`

```shell
Linux version 2.6.32-642.el6.x86_64 (mockbuild@worker1.bsys.centos.org) (gcc version 4.4.7 20120313 (Red Hat 4.4.7-17) (GCC) ) #1 SMP Tue May 10 17:27:01 UTC 2016
```

> `uname -r`

```shell
2.6.32-642.el6.x86_64
```

> `uname -a`

```shell
Linux host.localdomain 2.6.32-642.el6.x86_64 #1 SMP Tue May 10 17:27:01 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

## 查看系统版本

> `cat /etc/issue`

```shell
CentOS release 6.8 (Final)
Kernel \r on an \m
```

> `cat /etc/redhat-release` // 只对Redhat Linux有效

```shell
CentOS release 6.8 (Final)
```

> `lsb_release -a` // 需安装lsb  yum install lsb –y

```shell
LSB Version:base-4.0-amd64:base-4.0-noarch:core-4.0-amd64:core-4.0-noarch:graphics-4.0-amd64:graphics-4.0-noarch:printing-4.0-amd64:printing-4.0-noarch
Distributor ID:CentOS
Description:CentOS release 6.8 (Final)
Release:6.8
Codename:Final
```

## 关机 shutdown

> `sync`  // 将数据由内存同步到硬盘中  
`shutdown -h new`  // 立马关机  
`shutdown –h 10`  // 10分钟后关机，显示在登录用户的屏幕中  
`shutdown –h +10`  // 10分钟后关机  
`shutdown –h 20:25`  // 在今天20:25关机  
`shutdown –r now`  // 系统立马重启  
`shutdown –r +10`  // 系统十分钟后重启  
`reboot`  // 就是重启，等同于 shutdown –r now  
`halt`  // 关闭系统，等同于shutdown –h now 和 poweroff

## 系统状态的命令

> **who**： 确定谁在系统中

* `who`：列出当前已登录入系统的用户
henry  tty1  2018-12-30 15:51
用户名  终端设备的设备文件名
设备文件一般放于目录/dev下

* `tty`：可以打印出当前终端的设备文件名
* `who am i`：可以列出当前终端上的登录用户
* `whoami`：仅列出当前终端上的登录用户

> **uptime**：已开机时间（年龄）

15:01:15 up 1:51, 1 user, load average: 0.00, 0.00, 0.00

系统自启动后到现在的运行时间
当前登录入用户数
近期1分钟，5分钟，15分钟内系统CPU的负载

> **top**：列出资源占用排名靠前的进程

VIRT进程逻辑地址空间大小(virtual)
RES驻留内存数(Resident)，也就是占用物理内存数
SHR与其他进程内存数(share)
%CPU占用CPU百分百，%MEM占用内存百分百
TIME+占用的CPU时间

> **ps**：查阅进程状态(process status)

用于控制列表的行数(进程范围)和列数(每进程列出的属性内容)  
`ps`：只列出在当前终端上启动的进程 PID TTY TIME COMMAND  
`ps e`：列出系统中所有的进程(进程范围)  
`ps f`：已*fill格式*列出每一个进程(控制列的数目)  
`ps l`：已*long格式*列出每一个进程(控制列的数目)

> UID：用户ID(注册名)
PID：进程ID  
PPID：父进程的PID  
C：CPU占用指数：最近一段时间(秒级别)进程占用CPU情况  
STIME：启动时间  
SZ：进程逻辑内存大小(size)  
TTY：终端的名字  
COMMAND：命令名  
WCHAN：进程在内核的何处睡眠(wait channel)  
TIME：累计执行时间(占用CPU的时间)  
PRI：优先级  
S：状态，S(sleep)，R(run)，Z(Zombie)  
> **free**：内存使用情况  
> **vmtat**：系统负载

Procs r等待运行的进程数 b处在非中断睡眠状态的进程数  
Memory free空闲的内存 buff/cache用做缓存的内存数  
Swap 磁盘/内存的交换页数量，单位：KB/秒  
IO 设备I/O块数，单位：块/秒  
System in每秒的硬件中断数(interrupt)，包括时钟中断 cs每秒环境切换次数(context switch)  
CPU 总使用率 us=user sy=system id=idle wa=wait for disk I/O
