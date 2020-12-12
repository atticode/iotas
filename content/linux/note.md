---
title: "Linux Note"
date: 2020-11-07T11:15:09+08:00
draft: true
---


## Linux 字体安装
### Fedora 字体安装
+ 安装 Inconsolata 字体
```bash
# 1. 在 /usr/share/fonts/ 目录下新建文件夹
mkdir /usr/share/fonts/Inconsolata
# 2. 将字体文件复制到新建的目录下
cp Inconsolata-Regular.ttf /usr/share/fonts/Inconsolata
```

## Linux 查看软件位置
```bash
# 查看软件的目录位置 e.g.: whereis vim
whereis [softwareName]
# 查看软件运行文件所在目录 e.g.: which vim
which [softwareName]
```
