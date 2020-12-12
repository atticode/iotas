+++
title = "Emacs Note"
date = 2020-11-08T22:59:52+08:00
tags = ["emacs"]
+++

## 格式化JSON文件
```bash
M-x json-pretty-print-buffer
```

## 格式化源码
1. 格式化整个文件
```bash
 M-x mark-whole-buffer (C-x h)    全选
 M-x indent-region (C-M-\)        格式化选中
 ```

2. 格式化整个函数
```bash
 M-x mark-defun (C-M-h)           选中函数
 M-x indent-region (C-M-\)        格式化
```

## 更新插件
1. 进入列表
```bash
package-list-packages
```

2. 设置更新标识
```bash
package-menu-mark-upgrade [U]
```

3. 执行更新操作
```bash
package-menu-execute [x]
```

## 代码折叠(hs-minor-mode)
1. M-x hs-minor-mode 启动hs minor-mode

## 将所有超过两个的连续空格使用TAB替换掉

```bash
M-x tabify
```

## 将所有TAB使用适当个数的空格替换掉
```bash
M-x untabify
```

## 更改 tango-dark 主题注释的颜色
```
// 1. 打开主题文件, Widows系统下的文件位置为:
emacs-25.3_1-x86_64\share\emacs\25.3\etc\themes\tango-dark-theme.el
// 2. 找到变量 cham-2(原值为: #73d216)
// 3. 改为: #a7adba
```

## 插入 TAB 字符的问题
emacs 中 TAB 键的作用相当于格式化缩进和排版, 要是想插入TAB字符, 应输入 `C-q TAB`
```
只按 TAB 并不能插入TAB字符, 插入 TAB 字符的命令为
C-q TAB
```




