+++
title = "Connect 中间件的理解"
date = 2020-11-05T23:47:32+08:00
tags = ["nodejs"]
+++


## 中间件的简单理解
> 简单来说，中间件由函数组成，它除了处理req和res对象之外，还接收一个next函数来做流控制。     ——引自《了不起的Node.js》

## Connect 使用

```js

// 引入模块
var http = require('http');
var connect = require('connect');

// 创建 Connect 对象
var app = connect();

// 添加所有请求的中间件
app.use(function middleware1(req, res, next) {
  // TODO
  
  next();
});

// 添加 '/url1' 路径请求的中间件
app.use('/url1', function middleware2(req, res, next) {
  // TODO

  next();
});

// 创建 HTTP 服务器
http.createServer(app).listen(3000);

```

## Connect 源码简单拆解

``` js
/******   省略实现细节 *********
 * 1. 通过 use() 方法，将路由和匹配的中间件函数放入 stack 数组
 * 2. 开始接到请求，调用 next() 方法
 * 3. 在 next() 方法里面调用 middlewareFunc() 中间件方法, 并使stack数组的索引值加1
 * 4. 在中间件方法继续调用 next() 方法
 * 5. 直到 stack 数组中符合条件的中间件执行完毕
 */

// 导出模块
module.exports = function createServer() {
  function app(req, res, next) {
    app.handle(req, res, next);
  }
  // 保存路由和中间件函数
  app.stack = [];
  return app;
};

// use 方法
app.use = function use(route, fn) {
  // 将中间件函数和url 追加到 app.stack
  this.stack.push({route: route, middlewareFunc: fn});

  return this;
};

// handle 方法
app.handle = function handle(req, res, out) {
  var index = 0;

  // 定义 next() 方法
  function next(err) {
    // 获取stack的项, 并使索引值加 1
    var layer = this.stack[index++];

    call(layer.middlewareFunc, layer.route, err, req, res, next);

  };
  // 执行 next()
  next();
}

function call(middlewareFunc, route, err, req, res, next) {
  try {
    middlewareFunc(err, req, res, next);
  } catch {
    next();
  }
};

```
