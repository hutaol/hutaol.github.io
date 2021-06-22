---
title: 字符串属性和方法
date: 2019-01-10 00:38:15
tags: JS
categories: JavaScript
---

> 字符串属性和方法

<!-- more -->

## 属性

### `constructor` 返回创建字符串属性的函数

  ```JavaScript
  var s = 'Hello, world!';
  s.constructor;   // function String() { [native code] }
  ```

### `prototype` 允许您向对象添加属性和方法

  ```JavaScript
  var s = new String('Jion');
  s.prototype.name = 'world'; // 添加属性name
  s.name;   // world
  s.prototype.myFunc = function() {}  // 添加方法
  s.myFunc();
  ```

### `length` 返回字符串的长度(字符数)

  ```JavaScript
  var s = 'Hello, world!';
  s.length;  // 13
  ```

## 方法

### `charAt()` 返回指定索引位置的字符

  > string.charCodeAt(index)

  ```JavaScript
  var s = 'Hello, world';
  s.charAt(1);  // e 索引从0开始
  s.charAt(s.length-1);  // d 最后一个字符串
  ```

### `charCodeAt()` 返回指定索引位置字符的`Unicode`值
  
  > string.charCodeAt(index)

  ```JavaScript
  var s = 'Hello, world';
  s.charCodeAt(0);  // 72
  ```

### `fromCharCode()` 将`Unicode`转换为字符串

  > String.fromCharCode(n1, n2, ..., nX)

  ```JavaScript
  var n = String.fromCharCode(72, 69, 76, 76, 79);  // HELLO
  ```

### `indexOf()` 返回字符串中检索指定字符第一次出现的位置

  > string.indexOf(searchvalue, start)

  ```JavaScript
  var s = 'Hello world, welcome to the JavaScript!';
  var n = s.indexOf('l');  // 2
  ```

### `lastIndexOf()` 从后向前搜索字符串，并从起始位置（0）开始计算返回字符串最后出现的位置

  > string.lastIndexOf(searchvalue, start)

  ```JavaScript
  var s = 'Hello world';
  var n = s.lastIndexOf('l');  // 8 索引从后(0)到前
  ```

### `slice()` 返回两个指定索引区间的字符

  > string.slice(start, end)

  提示： 如果是负数，则该参数规定的是从字符串的尾部开始算起的位置。也就是说，-1 指字符串的最后一个字符，-2 指倒数第二个字符，以此类推。

  ```javascript
  var s = 'Hello world';
  s.slice(0, 5);  // Hello 从索引0开始到5（不包括5）
  s.slice(6);  // world 从索引6开始到结束
  s.slice(-1);  // d 最后一个字符
  ```

### `substring()` 返回两个指定的索引区间的字符

  > string.substring(from, to)

  ```javascript
  var s = 'Hello world';
  s.substring(0, 5);  // Hello 从索引0开始到5（不包括5）
  s.substring(6);  // world 从索引6开始到结束
  ```

### `substr()` 返回从索引开始指定长度的字符

  > string.substr(start, length)

  ```javascript
  var s = 'Hello world';
  s.substr(1, 2);  // el 从索引1开始2个长度
  s.substr(6);  // lo world  从索引6开始到结束
  ```

**思考**：`slice()`、`substring()`、`substr()`区别

`substring()`以两个参数中较小一个作为起始位置，较大的参数作为结束位置
当参数为负数时，
`slice()`将它字符串的长度与对应的负数相加，结果作为参数
`substring()`将负参数都直接转换为0
`substr()`将第一个参数与字符串长度相加后的结果作为第一个参数

```javascript
var s = 'hello world';

// substring
s.substring(2, 8);  // llo wo
s.substring(8, 2);  // llo wo

// 负数
s.slice(-3);      //  
s.substring(-3);  // hello world
s.substr(-3);     // rld

s.slice(3, -4);   // lo w (3, 7)
s.substring(3, -4); // hel (0, 3)
s.substr(3, -4);    // 空字符串 索引为3长度为0
```

**注意:** IE对substr接收负值的处理有错，它会返回原始字符串。

### `match()` 找到一个或多个正则表达式的匹配

  如果没有找到任何匹配的文本，`match()`将返回`null`。否则，它将返回一个`array`，其中存放了与它找到的匹配文本有关的信息
  > string.match(regexp)

  ```javascript
  var str = "The rain in SPAIN stays mainly in the plain";
  var n = str.match(/ain/g);  // ain, ain, ain

  // 不区分大小写
  var m = str.match(/ain/gi);  // ain, AIN, ain, ain
  ```

### `search()` 检索与正则表达式相匹配的值

  如果没有找到任何匹配的子串，则返回 -1。
  > string.search(searchvalue)

  ```javascript
  var str = "Mr. Blue has a blue house";
  var n = str.search("blue");  // 15
  var m = str.search(/blue/i);  // 4
  ```

### `toUpperCase()` 把一个字符串全部变为大写

  > string.toUpperCase()

  ```javascript
  var s = 'Hello world';
  s.toUpperCase();  // HELLO WORLD
  ```

### `toLowerCase()` 把一个字符串全部变成小写

  > string.toLowerCase()

  ```javascript
  var s = 'Hello world';
  s.toLowerCase();  // hello world
  ```

### `concat()` 连接两个或多个字符串，返回连接后的字符串

  > string.concat(string1, string2, ..., stringX)

  ```JavaScript
  var s1 = 'Hello ';
  var s2 = 'world!';
  var n = s1.concat(s2);   // Hello world!
  // 连接多个 , 隔开
  var s3 = ' How are you!';
  var m = s1.concat(s2, s3)  // Hello world! How are you!
  ```

### `replace()` 替换与正则表达式匹配的子串

  注意：`replace()`方法不改变原始字符串。只执行一次替换
  > string.replace(searchvalue, newvalue)

  ```JavaScript
  var s = 'hello world, good world'
  var n = s.replace('world', 'javascript');  // hello javascript, good world

  // 执行一个全局替换 正则表达式
  var str = "Mr Blue has a blue house and a blue car";
  var m = str.replace(/blue/g,"red"); // Mr Blue has a red house and a red car
  
  // 执行一个全局替换 忽略大小写
  var o = str.replace(/blue/gi, "red"); // Mr red has a red house and a red car
  ```

### `split()` 把字符串分割为字符串数组

  注意：`split()`方法不改变原始字符串。
  如果把空字符串`("")`用作`separator`，那么`stringObject`中的每个字符之间都会被分割.

  > string.split(separator, limit)

  ```javascript
  var s = 'hello world';
  s.split("");  // ['h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd']
  s.split(" ");  // ['hello', 'world']
  ```

### `trim()` 去除字符串两边的空白

  > string.trim()

  ```javascript
  var s = ' hello world    ';
  s.trim();  // hello world
  ```

### `valueOf()` 返回某个字符串对象的原始值

  > string.valueOf()

  ```javascript
  var s = 'hello world';
  s.valueOf();  // hello world
  ```
