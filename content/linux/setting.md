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
