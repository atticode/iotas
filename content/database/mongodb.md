+++
title = "Mongodb"
date = 2020-11-29T12:10:32+08:00
tags = ["database", "mongodb"]
+++

## Install

创建目录
```
D:/


```

启动mongod
```bash
mongod --config D:/mongodb/mongod.conf
```

## Config
创建配置文件`mongod.conf`, 添加如下内容

```conf
# mongod.conf

# for documentation of all options, see:
#   http://docs.mongodb.org/manual/reference/configuration-options/

# Where and how to store data.
storage:
  dbPath: D:/mongodb/data
  journal:
    enabled: true
#  engine:
#  mmapv1:
#  wiredTiger:

# where to write logging data.
systemLog:
  destination: file
  logAppend: true
  path:  D:/mongodb/log/mongod.log

# network interfaces
net:
  port: 27017
  bindIp: 127.0.0.1  # 指定IP可访问
#  bindIp: 0.0.0.0   # 所有IP都可访问
#  bindIpAll: true   # 所有IP都可访问


#processManagement:

#security:

#operationProfiling:

#replication:

#sharding:

## Enterprise-Only Options:

#auditLog:

#snmp:

```