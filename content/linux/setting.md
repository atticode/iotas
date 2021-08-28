+++
title = "Linux Setting"
date = 2020-12-20T13:28:40+08:00
isCJKLanguage = true
description = ""
tags = ["linux"]
categories = []
weight = 10
+++

## Ubuntu 修改文件最大监控数量

1. 查看文件最大监控数量
```bash
cat /proc/sys/fs/inotify/max_user_watches
```

2. 修改配置文件`/etc/sysctl.conf`
  * 打开配置文件
  ```bash
  sudo vim /etc/sysctl.conf
  ```

  * 在文件底部添加如下内容
  ```
  fs.inotify.max_user_watches=524288
  ```

3. 运行以下命令使配置生效
```bash
sudo sysctl -p
```

### 修改文件最大监控数量可解决以下问题
* Visual Studio Code： Visual Studio Code is unable to watch for file changes in this large workspace
* Vue-cli: Error: ENOSPC: System limit for number of file watchers reached

## CentOS 修改最大进程数限制(nproc)
通过命令 `ps -eLf | wc -l` 查看进程数, 通过命令 `sysctl kernel.pid_max` 查看最大进程数, 如果进程数接近最大进程数则说明进程数达到上限

### 计算最大进程数的值
最大进程数可设的值
* `default_nproc = total_memory / 128K` : 通过此公式计算得出值
* `default_nproc = total_memory / 128K / 2` : 通过此公式计算得出值
* `unlimited` : 设为此值表示不设限制

计算方式
1. 查看总内存 `cat /proc/meminfo |grep MemTotal`
2. 计算进程数 `echo "49421024 / 128"| bc `

### 修改相关配置文件
1. 修改配置文件 `/etc/sysctl.conf`
  * 在文件底部添加如下内容
  ```
  kernel.pid_max=32768
  ```

  * 运行以下命令使配置生效
  ```bash
  sudo sysctl -p
  ```

2. 修改普通用户的 nproc 配置文件 `/etc/security/limits.d/20-nproc.conf`
将下面内容
```shell
*          soft    nproc     32768
*          hard    nproc     32768
```
改为此内容
```shell
*          soft    nproc     unlimited
*          hard    nproc     unlimited
```

3. 修改root用户的 nproc 配置文件 `/etc/security/limits.conf`
将下面内容
```shell
*                soft    nproc           32768
*                hard    nproc           32768
```
改为此内容
```shell
*          soft    nproc     unlimited
*          hard    nproc     unlimited
```

### 可解决的问题
1. -bash: fork: 无法分配内存