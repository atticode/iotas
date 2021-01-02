+++
title = "代理设置"
date = 2020-12-26T19:10:32+08:00
tags = ["develop", "proxy"]
+++


## Windows设置命令行代理

### 查看已占用的端口
```bash
netstat -ano
```

### 根据`PID`查看对应的进程或程序
```bash
tasklist|findstr "672"
```

### 设置代理
```bash
set http_proxy=http://127.0.0.1:49973/
set https_proxy=http://127.0.0.1:49973/
```