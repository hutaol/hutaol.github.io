---
title: PHP管理工具Composer
date: 2019-06-19 11:42:44
tags: [PHP, Composer]
categories: PHP
---

> PHP管理工具Composer

<!-- more -->

## 全局安装

```php
curl -sS https://getcomposer.org/installer | php

mv composer.phar /usr/local/bin/composer
```

## Composer 国内镜像

全局配置

```php
composer config -g repo.packagist composer https://packagist.phpcomposer.com

```

解除镜像并恢复到packagist官方源

```php
composer config -g --unset repos.packagist
```

*参考*：<http://www.yanchat.com/75.html>