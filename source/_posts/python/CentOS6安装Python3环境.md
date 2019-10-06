---
title: CentOS6安装Python3.6环境
date: 2019-08-09 11:07:50
tags:
categories: python
---

# CentOS6.5安装python3.6.9

CentOS6安装python3.7，会出现问题：pip is configured with locations that require TLS/SSL

系统版本centos6.5，其中openssl的版本为OpenSSL 1.0.1e-fips 11 Feb 2013,而python3.7需要的openssl的版本为1.0.2或者1.1.x,需要对openssl进行升级，并重新编译python3.7.0。yum 安装的openssl 版本都比较低。

解决办法可参考地址：https://www.cnblogs.com/khstudy/p/11102633.html
嫌麻烦，安装python3.6.9

## 1、安装Python前的库环境

```shell
yum install gcc patch libffi-devel python-devel  zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel -y
yum install openssl-devel bzip2-devel expat-devel gdbm-devel readline-devel sqlite-devel readline-devel.x86_64 -y
```

## 2、下载Python源码包

```shell
wget https://www.python.org/ftp/python/3.6.9/Python-3.6.9.tgz

// wget: command not found 安装wget
yum -y install wget
```

## 3、 安装Python

```shell
tar zxvf Python-3.6.9.tgz
cd Python-3.6.9
./configure --prefix=/usr/local/python3
make && make install
```

## 4、设置软连接

```shell
ln -s /usr/local/python3/bin/python3.6 /usr/local/bin/python3
ln -s /usr/local/python3/bin/pip3 /usr/local/bin/pip3
```

## 5、查看python3版本以及pip3版本

```shell
python3
exit() // 退出python
pip3 -V
```

## 6、更新pip3版本

```shell
pip3 install --upgrade pip
```

**注意**：Centos系统中自带Python2，不过没有安装pip `centos -bash: pip: command not found
`

```shell
// 安装EPEL
yum -y install epel-release
// 启用EPEL
yum install -y yum-utils && yum-config-manager --enable epel
// 安装pip
yum install -y python-pip
// 更新
pip install --upgrade pip
```




# 卸载python3

```shell
rpm -qa|grep python3|xargs rpm -ev --allmatches --nodeps       // 卸载pyhton3
whereis python3 |xargs rm -frv           // 删除所有残余文件
whereis   python       // 查看现有安装的python
```

# 安装Django

```shell
pip3 install django

// 给Django设置软连接
ln -s /usr/local/python3/bin/django-admin /usr/local/bin/django-admin
```

// 出现错误：SQLite 3.8.3 or later is required
解决方法1：给django降级

```shell
卸载django:   pip3 uninstall django
安装低版本：   pip3 install django==2.1.8
```

解决方法2：升级SQLite

```shell
// 查看版本
sqlite3 --version
```

还是嫌麻烦选择降级，降级后又出现错误：`django.db.utils.NotSupportedError: URIs not supported`

。。。。。。还是老老实实升级吧

参考地址：https://blog.csdn.net/qq_39969226/article/details/92218635


# 安装git

```shell
yum install git -y
```

# 安装MySQL

## 1、查看是否安装了MySQL

```shell
rpm -qa | grep mysql
```

## 2、删除原来的数据库

```shell
rpm -e   mysql; // 一般删除，如果提示依赖的其他文件，则不能删除
rpm -e  --nodeps mysql; // 强力删除，如果有其他依赖文件，则可以对其进行强力删除
```

## 3、mysql安装

```shell
// 将mysql,mysql-server,mysql-devel都安装好
yum install -y mysql-server mysql mysql-devel
```

## 4、数据库安装成功之后，查看mysql-server的命令

```shell
rpm  -qi mysql-server
```

## 5、启动mysql服务

```shell
service mysqld start
```

## MySql相关命令

```shell
// 查看mysql数据库服务是否设置成开机自己启动
chkconfig --list  | grep mysqld

// 设置mysql数据库服务开机自动启动
chkconfig  mysqld on

// 给root账号设置密码为 root
mysqladmin -u root  password 'root';

// 登录数据库
mysql -u root -p

```

## CentOS6 部署Django+Nginx+uwsgi


参考：https://www.cnblogs.com/Black-rainbow/articles/9455927.html
     https://www.cnblogs.com/khstudy/p/11102633.html