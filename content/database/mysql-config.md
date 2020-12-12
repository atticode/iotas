+++
title = "Mysql Config"
date = 2020-12-12T13:08:36+08:00
isCJKLanguage = true
description = ""
tags = ["database", "mysql"]
categories = []
weight = 10
+++


## MySQL 配置文件


```conf

[mysqld]

# 模式设置
    # STRICT_TRANS_TABLES：在该模式下，如果一个值不能插入到一个事物表中，则中断当前的操作，对非事物表不做限制
    # NO_ZERO_IN_DATE：在严格模式下，不允许日期和月份为零
    # NO_ZERO_DATE：设置该值，mysql数据库不允许插入零日期，插入零日期会抛出错误而不是警告。
    # ERROR_FOR_DIVISION_BY_ZERO： 在INSERT或UPDATE过程中，如果数据被零除，则产生错误而非警告。如 果未给出该模式，那么数据被零除时MySQL返回NULL
    # NO_AUTO_CREATE_USER：禁止GRANT创建密码为空的用户
    # NO_ENGINE_SUBSTITUTION： 如果需要的存储引擎被禁用或未编译，那么抛出错误。不设置此值时，用默认的存储引擎替代，并抛出一个异常
sql_mode = STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION 

# 关闭符号连接
symbolic-links = 0

# MySQL选项以避免外部锁定。该选项默认开启
skip-external-locking

# 不区分大小写
lower_case_table_names = 0

# 在排序发生时由每个线程分配，如果排序后的数据无法放入排序缓冲,一个用来替代的基于磁盘的合并分类会被使用
sort_buffer_size = 2M

# 在日志组中每个日志文件的大小. 
innodb_log_file_size = 1024M

# 字符编码格式
character_set_server = utf8

# 关键词缓冲的大小, 一般用来缓冲 MyISAM 表的索引块.
key_buffer_size = 16M

# 每个连接独立的大小，大小动态增加，服务所能处理的请求包的最大大小以及服务所能处理的最大的请求大小(当与大的 BLOB 字段一起工作时相当必要)
max_allowed_packet = 100M

# 线程使用的堆大小. 此容量的内存在每次连接时被预留，MySQL 本身常不会需要超过 64K 的内存  
thread_stack = 512K

# 我们在 cache 中保留多少线程用于重用
thread_cache_size = 16

# 超过10天的binlog删除
expire_logs_days = 10

# binlog每个日志文件大小
max_binlog_size = 100M

# 表示的是binlog 能够使用的最大cache内存大小
max_binlog_cache_size = 1M

# 只有小于此设定值的结果才会被缓冲，此设置用来保护查询缓冲,防止一个极大的结果集将其他所有的查询结果都覆盖. 
query_cache_limit = 1M

# 查询缓冲常被用来缓冲 SELECT 的结果并且在下一次同样查询的时候不再执行直接返回结果，打开查询缓冲可以极大的提高服务器速度, 如果你有大量的相同的查询并且很少修改表. 
query_cache_size = 128M

# 选项是用于创建启动MySQL时MyISAM的自动恢复
    # DEFAULT: 不用备份，强制，或快速检查进行恢复。
    # BACKUP: 如果数据文件在恢复时被更改，将MYD 文件的备份保存为 tbl_name‐datetime.BAK。
    # FORCE: 即使会从.MYD 文件丢失多于一行仍运行恢复。
    # QUICK: 如果没有任何delete块就不检查行。
myisam-recover-options = BACKUP



# 使用给定目录作为根目录(安装目录), 设置mysql的安装目录
basedir=C:\MySQL
# 设置mysql数据库的数据的存放目录
#datadir=D:\MySQL\data
# 数据路径，从给定目录读取数据库文件。
datadir = /var/lib/mysql

# 错误日志路径
log-error = /var/lib/mysql/mysql.err

# 开启查询缓存，这也是web缓存之一，对重复查询只需要在缓存中读取就可以
explicit_defaults_for_timestamp = true
[mysqld]
# 设置3306端口
port=3306

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
