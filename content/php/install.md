+++
title = "PHP 开发环境"
date = 2020-11-05T23:25:18+08:00
tags = ["php"]
+++


## Windows

### 下载


### 安装


### 配置

#### 配置 Apache Httpd
打开 apache/conf/httpd.conf 文件, Apache 添加 PHP 模块

* PHP8
``` ini
LoadModule php_module C:/Develop/php/php8apache2_4.dll
PHPIniDir "C:/Develop/php"
<IfModule mime_module>
AddType application/x-httpd-php .php
</IfModule>
```

* PHP7
``` ini
LoadModule php7_module C:/Develop/php/php7apache2_4.dll
PHPIniDir "C:/Develop/php"
<IfModule mime_module>
AddType application/x-httpd-php .php
</IfModule>
```

* PHP 5
``` ini
 # 1. 添加PHP模块
 LoadModule php5_module "C:/Develop/php/php5apache2_4.dll"
 # 2. php.ini 文件所在目录
 PHPIniDir "C:/Develop/php"
 # 3. 需要php解析的文件类型
 AddType application/x-httpd-php .php

```

#### 配置 PHP

* 取消掉 `extension_dir`的注释, 并将目录改为PHP安装目录(734行)
```
extension_dir = "C:/Develop/php/ext"
```

* 修改PHP文件上传临时目录(816行)
```
upload_tmp_dir = C:/phpextend/upload
```

* 取消掉dll库的注释
```
extension=php_curl.dll
extension=php_mbstring.dll
extension=php_mysql.dll
extension=php_mysqli.dll
extension=php_pdo_mysql.dll
```

* 修改时区(PHP7-936行, PHP8-971行)
```
date.timezone = Asia/Shanghai
```


### 常见问题
1. Apache在windows下安装时出现服务无法启动的问题?

将`httpd.conf`文件的181行`LoadModule ssl_module modules/mod_ssl.so`注释掉

2. 切换PHP版本后Apache关联的还是旧版本？
通过命令重启`httpd -k restart`无效，需要在任务管理器重启Apache服务或以管理员打开终端然后运行`httpd -k restart`重启Apache


