+++
title = "Mysql Install"
date = 2020-12-12T13:05:00+08:00
isCJKLanguage = true
description = ""
tags = ["database", "mysql"]
categories = []
weight = 10
+++


## Windows

### 下载
1. MySQL官网[下载](https://dev.mysql.com/downloads/mysql/) `Windows (x86, 64-bit), ZIP Archive`安装文件(当时版本为8.0.22)
2. Microsoft官网[下载](https://support.microsoft.com/zh-cn/help/2977003/the-latest-supported-visual-c-downloads)`Visual C++`软件包

### 安装
1. 将安装文件解压到安装目录
2. 在 MySQL 解压后的根目录添加`my.cnf`文件, 添加如下内容, 并根据安装目录, 修改配置文件中目录的相关路径
```cnf
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录
basedir=C:\MySQL
# 设置mysql数据库的数据的存放目录
datadir=D:\MySQL\data
# 允许最大连接数
max_connections=200
# 允许连接失败的次数
max_connect_errors=10
# 服务端使用的字符集默认为utf8mb4
character-set-server=utf8mb4
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用"mysql_native_password"插件认证
#mysql_native_password
default_authentication_plugin=mysql_native_password
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8mb4
[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8mb4
```
3. `datadir`目录不需要手动创建, 初始化时会自动创建
4. 将MySQL的安装目录里的`bin`目录添加到`PATH`环境变量
5. 以管理员身份运行CMD
6. 运行`mysqld --initialize --console`命令初始化, 此时会输出如下部分内容显示生成root的初始密码, * 为对应的root密码
```cmd
A temporary password is generated for root@localhost: **********
```
7. 运行`mysqld --install`安装MySQL服务, 显示Service successfully installed为安装成功
8. 运行`net start mysql`启动MySQL服务, 成功后会提示'MySQL 服务已经启动成功'

### 配置
1. 登录MySQL修改root密码
```cmd
mysql -u root -p

```
2. 输入上面生成的初始密码
3. 修改密码
```sql
ALTER USER 'root'@'localhost' IDENTIFIED BY '新密码';
```

### 卸载
1. 运行`NET STOP mysql` 或 `sc stop mysql` 停止MySQL服务
2. 运行 `mysqld -remove` 或 `SC DELETE mysql`删除MySQL服务
3. 运行`mysqladmin -u root shutdown` 停止MySQL

### 只启动MySQL不安装
1. 第一次时先运行`mysqld --console`
2. 运行`mysqld`启动
3. 运行`mysqladmin -u root shutdown`停止MySQL

### 备注
MySQL支持启动多个, 运行不同安装目录下的mysqld可以启动多个MySQL


## 参考
* [Windows install ZIP Archive](https://dev.mysql.com/doc/refman/8.0/en/windows-install-archive.html)
* [MySQL option file](https://dev.mysql.com/doc/refman/8.0/en/option-files.html)
