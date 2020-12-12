+++
title = "Operation"
date = 2020-12-12T14:03:05+08:00
tags = []
categories = []
isCJKLanguage = true
description = ""
weight = 10
+++


## 格式化JSON文件
M-x json-pretty-print-buffer

## 格式化源码
- 格式化整个文件
   1. M-x mark-whole-buffer (C-x h)    全选
   2. M-x indent-region (C-M-\)        格式化选中
- 格式化整个函数
   1. M-x mark-defun (C-M-h)           选中函数
   2. M-x indent-region (C-M-\)        格式化

## 更新插件
1. 进入列表
package-list-packages
2. 设置更新标识
package-menu-mark-upgrade [U]
3. 执行更新操作
package-menu-execute [x]

## 代码折叠(hs-minor-mode)
1. M-x hs-minor-mode 启动hs minor-mode
