+++
title = "Postgresql Shell"
date = 2020-12-12T13:10:39+08:00
isCJKLanguage = true
description = ""
tags = []
categories = []
weight = 10
+++


# PostgreSQL命令

## User
``` shell
postgres
```

## 启动
``` shell
/usr/lib/postgresql/10/bin/pg_ctl -D /var/lib/postgresql/10/main -l logfile start
```

## 停止
``` shell
/usr/lib/postgresql/10/bin/pg_ctl -D /var/lib/postgresql/10/main stop

Ver Cluster Port Status Owner    Data directory              Log file
10  main    5432 down   postgres /var/lib/postgresql/10/main /var/log/postgresql/postgresql-10-main.log
```

## 连接数据库
``` shell
psql -h 127.0.0.1 -d test -U w -p 5432
```

## 操作
### 添加角色
``` sql
CREATE USER w WITH PASSWORD 'root123';
```
### 添加角色权限
``` sql
ALTER ROLE w WITH CREATEDB;
```

### User
postgres  w
