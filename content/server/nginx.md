+++
title = "Nginx 配置"
date = 2020-12-13T13:47:56+08:00
isCJKLanguage = true
description = ""
tags = ["server", "nginx"]
categories = []
weight = 10
+++


## 设置禁用缓存

### 禁用缓存
* 对所有文件都禁用缓存

```
location / {
    # 如果expires 和 add_header 同时开启的情况下，则add_header优于expires生效
    # Cache-Control比Expires可以控制的多一些， 而且Cache-Control会重写Expires的规则
    # 设置禁止浏览器缓存，每次都从服务器请求
    add_header Cache-Control 'max-age=0, no-cache, no-store, must-revalidate';
    add_header Pragma 'no-cache';
    add_header Expires 'Wed, 11 Jan 1984 05:00:00 GMT';

    # 设置缓存上面定义的后缀文件缓存到浏览器的生存时间
    expires -1s;
}
```

* 对指定后缀文件禁用缓存

```
location ~ .*\.(gif|jpg|jpeg|png|bmp|swf|js|css)$ {
  #禁止缓存，每次都从服务器请求
  add_header Cache-Control 'max-age=0, no-cache, no-store, must-revalidate';
  add_header Pragma 'no-cache';
  add_header Expires 'Wed, 11 Jan 1984 05:00:00 GMT';
}
```

### 启用缓存
```
location ~ .*\.(gif|jpg|jpeg|png|bmp|swf|js|css)$ {
  #设置缓存上面定义的后缀文件缓存到浏览器的生存时间
  expires   3d;
}
```

## 允许跨域
```
server {
    add_header Access-Control-Allow-Origin *;
    add_header Access-Control-Allow-Methods 'GET,POST';
    add_header Access-Control-Allow-Headers 'DNT,X-Mx-ReqToken,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Authorization';
    add_header Access-Control-Allow-Credentials true;
}
```

## SPA 部署

在配置文件添加以下内容

```
location / {
  try_files $uri $uri/ /index.html;
}
```
