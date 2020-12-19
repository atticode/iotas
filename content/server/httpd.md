+++
title = "Apache Httpd 配置"
date = 2020-12-13T13:47:56+08:00
isCJKLanguage = true
description = ""
tags = ["server", "httpd"]
categories = []
weight = 10
+++


## 设置禁用缓存

### 修改 `httpd.conf` 方式

```
# 开启
LoadModule expires_module modules/mod_expires.so

# 添加以下内容
<IfModule mod_headers.c>
  <filesmatch ".(html|css|js|json|ico|gif|jpg|png|)$">
    header set Cache-Control "no-store, no-cache"
    Header set Pragma "no-cache"
  </filesmatch>
</IfModule>
```

### 修改 `.htaccess` 方式

```
<IfModule mod_headers.c>
<filesMatch "\.(html|js|json|css|php)$">
  FileETag None
  Header unset ETag
  Header set Cache-Control "max-age=0, no-cache, no-store, must-revalidate"
  Header set Pragma "no-cache"
  Header set Expires "Wed, 11 Jan 1984 05:00:00 GMT"
</filesMatch>
</IfModule>

```

### Cache-Control的参数可选值
* `Public` 指示响应可被任何缓存区缓存。
* `Private` 指示对于单个用户的整个或部分响应消息，不能被共享缓存处理。这允许服务器仅仅描述当用户的部分响应消息，此响应消息对于其他用户的请求无效。
* `no-cache` 指示请求或响应消息不能缓存
* `no-store` 用于防止重要的信息被无意的发布。在请求消息中发送将使得请求和响应消息都不使用缓存。
* `max-age` 指示客户机可以接收生存期不大于指定时间（以秒为单位）的响应。
* `min-fresh` 指示客户机可以接收响应时间小于当前时间加上指定时间的响应。
* `max-stale` 指示客户机可以接收超出超时期间的响应消息。如果指定- - - max-stale消息的值，那么客户机可以接收超出超时期指定值之内的响应消息。

### max-age= 参考值

* `max-age=3600` 缓存一个小时
* `max-age=604800` 缓存一个星期
* `max-age=29030400` 缓存一年


## SPA 部署
新增 `.htaccess` 文件, 并添加以下内容

```
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule . /index.html [L]
</IfModule>

```
