+++
title = "Mysql User"
date = 2020-12-12T13:07:50+08:00
isCJKLanguage = true
description = ""
tags = ["database", "mysql"]
categories = []
weight = 10
+++


## 创建用户


### 5.7
```sql
use mysql;

select host, user from user;

-- 因为mysql版本是5.7，因此新建用户为如下命令：
-- CREATE USER IF NOT EXISTS 'user'@'localhost' IDENTIFIED BY 'password';
CREATE USER IF NOT EXISTS 'dev' identified by 'dev';

-- 将docker_mysql数据库的权限授权给创建的docker用户，密码为123456：
-- grant all privileges on 库名.表名 to '用户名'@'IP地址' identified by '密码' with grant option;
-- 这里用户名和密码一样
grant all on *.* to dev@'%' identified by 'dev' with grant option;

-- 这一条命令一定要有：
flush privileges;
```
