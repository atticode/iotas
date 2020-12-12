+++
title = "Directory"
date = 2020-12-12T13:24:51+08:00
isCJKLanguage = true
description = ""
tags = ["linux", "website"]
categories = []
weight = 10
+++


## Linux 程序安装目录
* `/usr` 系统级的目录
* `/usr/local` 用户级的程序目录，用户自己编译的软件默认会安装到这个目录下
* `/opt` 用户级的程序目录，安装到/opt目录下的程序，它所有的数据、库文件等等都是放在同个目录下面,想要卸载直接`rm -rf`
掉即可
* `/home/[username]/app` 用户自定义安装目录
* `/usr/src` 系统级的源码目录
* `/usr/local/src` 用户级的源码目录

/usr/local这里主要存放那些手动安装的软件，即不是通过apt-get安装的软件。它和/usr目录具有相类似的目录结构。让软件包管理器来管理/usr目录，而把自定义的脚本(scripts)放到/usr/local目录下面

## Linux 查看程序位置
``` shell
# 查看软件的目录位置 e.g.: whereis vim
$ whereis [softwareName]
# 查看软件运行文件所在目录 e.g.: which vim
$ which [softwareName]
```