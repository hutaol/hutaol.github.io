---
title: Laravel基础学习
date: 2020-03-09 17:59:11
tags: [PHP, Laravel]
categories: PHP
---

> Laravel（PHP开发框架）

`Laravel`是一套简洁、优雅的PHP Web开发框架(`PHP Web Framework`)。它可以让你从面条一样杂乱的代码中解脱出来；它可以帮你构建一个完美的网络APP，而且每行代码都可以简洁、富于表达力

<!-- more -->

```php
// 1.创建模型
php artisan make:model Categories
// 创建模型并生成迁移
php artisan make:model Categories -m

// 2.生成迁移
php artisan make:migration create_categories_table

// 3.运行数据库迁移
php artisan migrate

// admin
// 4.创建一个对应模型的路由器
php artisan admin:make CategoryController --model=App\\Category

// 5.将以下路由添加到 app/Admin/routes.php:
$router->resource('categories', CategoryController::class);

```

## 1、Eloquent ORM

> 提供一个漂亮、简洁的 ActiveRecord 实现来和数据库交互

### 创建Eloquent 模型

所有的 `Eloquent` 模型都继承至 `Illuminate\Database\Eloquent\Model` 类，创建的模型类默认在app目录下，可指定到app目录下的Models目录下，

```php
// app/Flight
php artisan make:model Flight

// app/Models/Flight
php artisan make:model Models/Flight
```

如果要在生成模型的时候生成 数据库迁移 ，可以使用 `--migration` 或 `-m` 选项：

```php
php artisan make:model Flight --migration

php artisan make:model Flight -m
```

### 数据表

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Flight extends Model
{
    // 数据库连接 模型指定一个不同的连接
    protected $connection = 'connection-name';

    // 与模型关联的表名，默认：flights
    protected $table = 'my_flights';

    // 主键，默认：id
    protected $primaryKey = 'flight_id';

    // 指示模型主键是否递增，默认：一个自增的整数值
    public $incrementing = false;

    // 自动递增ID的“类型”
    protected $keyType = 'string';

    // 指示是否自动维护时间戳， created_at 和 updated_at
    public $timestamps = false;

    // 自定义时间戳的格式
    protected $dateFormat = 'U';

    // 自定义存储时间戳的字段名
    const CREATED_AT = 'creation_date';
    const UPDATED_AT = 'last_update';

    // 可以被批量赋值的属性
    protected $fillable = ['name', 'url'];
    // 不可批量赋值的属性
    protected $guarded = ['price'];

    // 默认属性值
    protected $attributes = [
        'delayed' => false,
    ];
}
```

### 模型检索(Eloquent 模型 查询构造器 )

```php
<?php

// 所有数据
$flights = App\Flight::all();

foreach ($flights as $flight) {
    echo $flight->name;
}

// 附加约束
$flights = App\Flight::where('active', 1)
               ->orderBy('name', 'desc')
               ->take(10)
               ->get();

// 重新加载模型
// fresh 和 refresh 方法重新加载模型
// fresh现有的模型实例不受影响
$flight = App\Flight::where('number', 'FR 900')->first();
$freshFlight = $flight->fresh();

// refresh新数据重新赋值现有模型
$flight = App\Flight::where('number', 'FR 900')->first();
$flight->number = 'FR 456';
$flight->refresh();
$flight->number; // "FR 900"

```

一些问题

[laravel 图片上传与前端显示问题](https://www.cnblogs.com/linqingvoe/p/11253859.html)

执行命令：

```php
php artisan storage:link
```
