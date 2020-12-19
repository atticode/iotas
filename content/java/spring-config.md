+++
title = "Spring Config"
date = 2020-12-13T13:47:56+08:00
isCJKLanguage = true
description = ""
tags = ["java", "spring"]
categories = []
weight = 10
+++


## 配置

### 允许本地配置文件覆盖远端配置文件
在远端配置文件添加以下配置

```yaml
# 允许本地配置文件覆盖
cloud:
  config:
    allow-override: true
    override-none: true
    override-system-properties: false
```
