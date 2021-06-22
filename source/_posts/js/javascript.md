---
title: JavaScript
date: 2018-11-07 13:15:56
tags: JS
categories: JavaScript
---

> JavaScript（解释型编程语言）

JavaScript（简称“JS”） 是一种具有函数优先的轻量级，解释型或即时编译型的编程语言。虽然它是作为开发Web页面的脚本语言而出名，但是它也被用到了很多非浏览器环境中，JavaScript 基于原型编程、多范式的动态脚本语言，并且支持面向对象、命令式和声明式（如函数式编程）风格。上线时间：1995年

<!-- more -->

## 一、前言

### JavaScript

不例外，我们从`Hello, world`开始

```HTML
<html>
<head>
  <script>
    alert('Hello, world');
  </script>
</head>
<body>
  ...
</body>
</html>
```

由`<script>...</script>`包含的代码就是JavaScript代码，它将直接被浏览器执行。

### 如何运行JavaScirpt

先创建一个`helloworid.html`文件，把代码复制到文件中，保存，用浏览器打开，就能看到一个`Hello，world`弹窗效果啦。
**恭喜你，编程的第一步就从此开始，走向人生巅峰，谱写你的辉煌传奇！**

## 二、基础

### 基础语法

每一个语句以`;`结束，语句块`{...}`,但JavaScript并不强制要求在每个语句的结尾加`;`，浏览器中负责执行JavaScript代码的引擎会自动在每个语句的结尾补上`;`
**让JavaScript引擎自动加分号在某些情况下会改变程序的语义，导致运行结果与期望不一致**

### 注释

以`//`开头直到行末的字符被视为行注释，注释是给开发人员看的，JavaScript引擎会自动忽略：

```JavaScript
// 这是一行注释
alert('hello'); // 这也是注释
```

块注释`/*...*/`把多行字符包裹起来，把一大“块”视为一个注释

```JavaScript
/* 从这里开始是块注释
仍然是注释
仍然是注释
注释结束 */
```

### 数据类型

> **值类型**(基础类型)：字符串(`String`)、数字(`Number`)、布尔(`Boolean`)、对空(`Null`)、未定义(`Undefined`)、`Symbol`。
**引用数据类型**：对象(`Object`)、数组(`Array`)、函数(`Function`)。

*注：`Symbol` 是 `ES6` 引入了一种新的原始数据类型，表示独一无二的值。*

**`typeof`运算符** 可以返回一个值得数据类型

> typeof 运算符
instanceof 运算符
Object.prototype.toString 方法

```JavaScript
typeof 123 // "number"
typeof '123' // "string"
typeof false // "boolean"
function f() {}
typeof f // "function"
typeof undefined // "undefined"

// instanceof
var o = {};
var a = [];
o instanceof Array // false
a instanceof Array // true
```

#### 字符串(String)

可以使用`双引号`或`单引号`，字符串中可以使用引号，只要不匹配包围字符串的引号即可

```JavaScript
"I'm OK";
```

字符串内部既包含`'`又包含`"`,可以用转义字符`\`来标识

```JavaScript
'I\'m \"OK\"!';
```

##### 转义字符`\`

| 代码 | 输出 |
| ------ | ------ |
| `\n` | 换行 |
| `\r` | 回车 |
| `\t` | 制表符 |
| `\b` | 退格符 |
| `\f` | 换页符 |
| `\\` | 反斜杠`\` |
| `\'` | 单引号 |
| `\"` | 双引号 |

ASCII字符可以以`\x##`形式的十六进制表示，例如：

```JavaScript
'\x41'; // 完全等同于 'A'
```

`\u####`表示一个Unicode字符

```JavaScript
'\u4e2d\u6587'; // 完全等同于 '中文'
```

##### 多行字符串

每行结尾用`\n`，ES6标准新增，反引号表示

```JavaScript
`这是一个
多行
字符串`;
```

##### 模板字符串

多个字符串连接起来，可以用`+`号连接

ES6新增了一种模板字符串，用反斜杠表示，字符串里的变量`${name}`表示，自动替换字符串中的变量：

```JavaScript
var name = '小明';
var age = 20;
var message = `你好, ${name}, 你今年${age}岁了!`;
```

##### 操作字符串

获取字符串某个指定位置的字符，索引号从0开始

```JavaScript
var s = 'Hello, world!';

s[0]; // 'H'
s[6]; // ' '
s[7]; // 'w'
s[12]; // '!'
s[13]; // undefined 超出范围的索引不会报错，但一律返回undefined
```

**注意**：字符串是不可变的，如果对字符串的某个索引赋值，不会有任何错误，但是，也没有任何效果。

##### {% post_link js-string-method 字符串属性和方法 %}

#### 数字(Number)

只要一种数据类型，不区分整数和浮点数

`Infinity` - 无穷大

`NaN` - 非数字值

`Number`基本运算

```JavaScript
1 + 2;    // 3
3 - 2;    // 1
1 * 2;    // 2
3 / 2;    // 1.5

// % 求余
10 % 3;    // 1
10.5 % 3; // 1.5

// Special
2 / 0;    // Infinity
0 / 0;    // NaN
```

#### 布尔(Boolean)

布尔只有2个值：`true`、`false`

基本运算：

- `&&`运算是`与`运算，只有所有都为`true`，`&&`运算结果才是`true`

  ```JavaScript
  true && true;             // true
  true && false;            // false
  false && true && false;   // false
  ```

- `||`运算是`或`运算，只要其中有一个为`true`，`||`运算结果就是true`

  ```JavaScript
  false || false;           // false
  true || false;            // true
  false || true || false;   // true
  ```

- `!`运算是`非`运算，它是一个单目运算符，把`true`变成`false`，`false`变成`true`

  ```JavaScript
  ! true;       // 结果为false
  ! false;      // 结果为true
  ! (2 > 5);    // 结果为true
  ```

- 比较运算符 `>` `<` `>=` `<=` `==`

  *布尔值经常用在条件判断中*

  相等运算符 `===` `!==` `==` `!=`

  **`==`：会自动转换数据类型再比较，在一些情况下会得到诡异的结果
  `===`：不会自动转换数据类型，如果数据类型不一致返回`false`**

  例如：
  `NaN`这个特殊的Number与所有其他值都不相等，包括它自己

  ```JavaScript
  NaN === NaN; // false
  ```

  唯一能判断`NaN`的方法是通过`isNaN()`函数：

  ```JavaScript
  isNaN(NaN); // true
  ```

#### 对空(Null)、未定义(Undefined)

`null` 表示一个“空”的值，它和`0`以及空字符串`''`不同，`0`是一个数值，`''`表示长度为0的字符串，而`null`表示“空”。
`undefined` 表示变量不含有值(值未定义)。

大多数情况下，我们都应该用`null`。`undefined`仅仅在判断函数参数是否传递的情况下有用

#### 数值(Array)

数组是一组按顺序排列的集合，集合的每个值称为元素。JavaScript的数组可以包括任意数据类型。例如：

```JavaScript
var arr = [1, 2, 3.14, 'Hello', null, true];
arr[0]; // 返回索引为0的元素，即1
arr[5]; // 返回索引为5的元素，即true
arr[6]; // 索引超出了范围，返回undefined
```

数组用`[]`表示，元素之间用`,`分隔

另一种创建数组的方法是通过`Array()`函数实现：

```JavaScript
new Array(1, 2, 3); // 创建了数组[1, 2, 3]
```

#### 对象(Object)

JavaScript的对象是一组由键-值组成的无序集合，例如：

```JavaScript
var person = {
    name: 'Bob',
    age: 20,
    tags: ['js', 'web', 'mobile'],
    city: 'Beijing',
    hasCar: true,
    zipcode: null
};
```

JavaScript对象的键都是字符串类型，值可以是任意数据类型。

要获取一个对象的属性，我们用对象变量.属性名的方式：

```JavaScript
person.name; // 'Bob'
person.zipcode; // null
```

#### 变量

变量名是`大小写英文`、`数字`、`$`和`_`的组合，且不能用数字开头。
变量名也不能是JavaScript的关键字，如`if`、`while`等
申明一个变量用`var`语句.

拥有动态类型，即相同的变量可用作不同的类型，例如：

```JavaScript
var x;          // x 为undefined  
var x = 1;      // 现在 x 为数字
var x = "ht"    // 现在 x 为字符串
```

*这种变量本身类型不固定的语言称之为`动态语言`，与之对应的是静态语言。`静态语言`在定义变量时必须指定变量类型，如果赋值的时候类型不匹配，就会报错。例如Java是静态语言*

##### strict模式

在`strict`模式下运行的JavaScript代码，强制通过`var`申明变量，未使用`var`申明变量就使用的，将导致运行错误。

启用strict模式的方法是在JavaScript代码的第一行写上：

```JavaScript
'use strict';
```

这是一个字符串，不支持strict模式的浏览器会把它当做一个字符串语句执行，支持strict模式的浏览器将开启strict模式运行JavaScript。
