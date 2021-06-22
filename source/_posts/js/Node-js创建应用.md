---
title: Node.js创建应用
date: 2019-03-25 23:23:55
tags: [JS, Node]
categories: JS
---

## 创建Node.js应用

<!-- more -->

```node
// require载入http模块，实例化HTTP
var http = require('http');
http.createServer(function (request, response) {

    // 发送 HTTP 头部 
    // HTTP 状态值: 200 : OK
    // 内容类型: text/plain
    response.writeHead(200, {'Content-Type': 'text/plain'});

    // 发送响应数据 "Hello World"
    response.end('Hello world\n');
}).listen(8888);

// 终端打印如下信息
console.log('Server running at http://127.0.0.1:8888/');
```

保存为`server.js`文件

使用`node`命令执行

```terminal
node server.js
Server running at http://127.0.0.1:8888/
```

打开浏览器即可访问<http://127.0.0.1:8888/>，
