+++
title = "Encoding"
date = 2020-12-12T14:02:24+08:00
tags = []
categories = []
isCJKLanguage = true
description = ""
weight = 10
+++



Emacs 打开文件时首先根据一个包含许多编码系统的列表依次进行判断,
直到遇到能够识别的编码系统就停止

## 查看当前buffer的编码
``` lisp
M-x describe-coding-system
```

## 列出所有支持的编码
``` lisp
  C-x <RET> r <TAB>
```

## 打开文件出现乱码，修改文件的编码
``` lisp
  M-x revert-buffer-with-coding-system RET
  然后输入编码名字: utf-8 或 chinese-gbk
```

## 保存时指定文件编码/改变当前文件编码
``` lisp
  M-x set-buffer-file-coding-system RET
  然后输入编码名字: utf-8 或 chinese-gbk

  命令为: C-x RET f utf-8
```

## 以指定的编码重新读入文件
``` lisp
  M-x revert-buffer-with-coding-system RET
  然后输入编码名字: utf-8 或 chinese-gbk

  # 命令为: C-x RET r utf-8
```

## 不改变当前文件, 以指定编码另存为
``` lisp
  M-x universal-coding-system-argument RET utf-8
  # 命令为: C-x RET c utf-8 RET C-x C-w RET
```

## 文件格式转换
``` lisp
  dos->unix: M-x set-buffer-file-coding-system unix
  unix->dos: M-x set-buffer-file-coding-system dos
  # 命令为: C-x RET f unix/dos
```

## 问题: 从其他窗口复制内容粘贴到Emacs中，出现乱码
``` emacs-lisp
;; 将下面一行注释掉
;;(set-selection-coding-system 'utf-8)
```

## 在配置文件中设置编码

``` lisp
;; 设置默认的buffer编码
(setq default-buffer-file-coding-system 'utf-8)
;; 优先选择的编码
(prefer-coding-system 'utf-8)
(set-language-environment "UTF-8")
(set-terminal-coding-system 'utf-8)
(set-keyboard-coding-system 'utf-8)
(set-clipboard-coding-system 'utf-8)
(setq locale-coding-system 'utf-8)
;; 设置buffer的编码
(set-buffer-file-coding-system 'utf-8)
(set-selection-coding-system 'utf-8)
(modify-coding-system-alist 'process "*" 'utf-8)

;; 指定后缀名的字符编码
(add-to-list 'file-coding-system-alist '("\\.txt" . utf-8-unix) )
```
