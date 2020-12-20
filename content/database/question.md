+++
title = "Database 常见问题"
date = 2020-11-05T23:37:18+08:00
tags = ["database"]
+++


在mysql8中导出的数据，想导入mysql5.7中的时候总是报错utf8mb4_0900_ai_ci，然后发现utf8mb4_0900_ai_ci在mysql8以下是不被支持的，导出的数据库需要修改utf8mb4_0900_ai_ci为utf8mb4_unicode_ci或者utf8mb4_general_ci。
配置utf8mb4_unicode_ci或者utf8mb4_general_ci时，需要数据库支持utf8mb4

utf8mb4_0900_ai_ci，中间的0900，它对应的是Unicode 9.0的规范，最后两部分_ai_ci，ai表示accent insensitivity，也就是“不区分音调”，而ci表示case insensitivity，也就是“不区分大小写”

