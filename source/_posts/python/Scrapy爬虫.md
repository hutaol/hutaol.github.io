---
title: Scrapy爬虫
date: 2024-06-21 15:03:42
tags:
---

Scrapy是python主流爬虫框架，可以很方便的通过url抓取web信息，同时与传统的requests库相比，提供了更多的工具和更高的并发。

<!-- more -->

## 安装Scrapy

```shell
pip3 install scrapy
```

## 创建工程

```shell
scrapy startproject VideoCrawler
```

## 创建一个基于 url 的爬虫服务

```shell
scrapy genspider txvideo https://v.qq.com/
```
