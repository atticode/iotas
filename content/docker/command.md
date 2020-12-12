+++
title = "Command"
date = 2020-12-12T14:14:26+08:00
tags = []
categories = []
isCJKLanguage = true
description = ""
weight = 10
+++



## 镜像仓库

### docker login

登录到一个docker镜像仓库, 如果未指定镜像仓库的地址，则默认官方仓库——docker hub
``` shell
$ docker login [OPTIONS] [SERVER]
$ docker login -u username -p password

1. OPTIONS:
   -p, --password string: 密码
   -u, --username string: 用户名
   --help: 打印用法

2. SERVER: 镜像仓库的地址
```
### docker logout

登出一个docker镜像仓库，如果未指定镜像仓库的地址，则默认官方仓库——docker hub
``` shell
$ docker logout [OPTIONS] [SERVER]
$ docker logout

1. OPTIONS:
   --help: 打印用法
2. SERVER: 镜像仓库的地址
```
### docker search

从镜像仓库查找镜像
``` shell
$ docker search [OPTIONS] TERM
$ docker search httpd

1. OPTIONS:
   -f, --filter value: 根据限制条件搜索 (default [])
    e.g.: docker search --filter=stars=10
   --limit int: 显示搜索结果的数量 (default 25)
   --no-index: 显示完整的镜像描述
   --no-trunc: 显示完整的镜像描述
   --help: 打印用法
2. TERM: 镜像名称
```

### docker pull

从镜像仓库中拉取或更新指定镜像
``` shell
$ docker pull [OPTIONS] NAME[:TAG|@DIGEST]
$ docker pull tomcat

1. OPTIONS:
   -a, --all-tags: 拉取所有 tagged 镜像
   --disable-content-trust: 忽略镜像的校验，默认开启
   --help: 打印用法
2. NAME: 镜像名称
3. TAG: 镜像的tag
4. DIGEST: 镜像的ID
```

### docker push

将本地的镜像上传到镜像仓库，要先登录到镜像仓库
``` shell
$ docker push [OPTIONS] NAME[:TAG]
$ docker push myhttpd:1.0

1. OPTIONS:
   --disable-content-trust: 忽略镜像校验(默认开启)
   --help: 打印用法
2. NAME: 镜像名称
3. TAG: 镜像的tag
```

## 本地镜像

### docker images

列出本地镜像

``` shell
$ docker images [OPTIONS] [REPOSITORY[:TAG]]
$ docker images

1. OPTIONS:
   -a, --all: 列出本地所有镜像，(包括中间映射层，默认情况下过滤掉中间映射层)
   --digests: 显示sha256信息
   -f, --filter value: 根据限制条件过滤输出(default [])
   --format string: 指定返回值的模板文件
   --no-reunc: 显示完整的镜像信息
   -q, --quiet: 只显示镜像ID
   --help: 打印用法
2. REPOSITORY: 镜像名称
3. TAG: 镜像的tag
```

### docker tag

标记本地镜像到一个仓库

``` shell
$ docker tag [OPTIONS] IMAGE[:TAG] IMAGE[:TAG]
$ docker tag httpd:latest myhttpd:mytag

1. OPTIONS:
   --help: 打印用法
2. IMAGE: 镜像名称
3. IMAGE: 自定义镜像名称
```
### docker history

查看镜像的历史记录

``` shell
$ docker history [OPTIONS] IMAGE
$ docker history httpd

1. OPTIONS:
   -H, --human:以可读的格式打印镜像的大小和日期, 默认为 true
   --no-trunc: 显示完整的镜像信息
   -q, --quiet: 仅列出提交记录ID
   --help: 打印用法
2. IMAGE: 镜像名称
```

### docker rmi

删除一个或多个镜像

``` shell
> Usage: docker rmi [OPTIONS] IMAGE [IMAGE...]
> e.g: docker rmi httpd

1. OPTIONS:
   -f, --force: 强制删除镜像
   --no-prune: 不移除该镜像的过程镜像，默认移除
   --help: 打印用法
2. IMAGE: 镜像名称
```

### docker save

将一个或多个镜像保存成 tar 文件
``` shell
$ docker save [OPTIONS] IMAGE [IMAGE...]
$ docker save -o httpd.tar httpd

1. OPTIONS:
   -o, --output string: 保存到的文件
   --help: 打印用法
2. IMAGE: 镜像名称
```

### docker load


### docker export


### docker import


### docker build

