+++
title = "Setting"
date = 2020-12-12T14:03:28+08:00
tags = []
categories = []
isCJKLanguage = true
description = ""
weight = 10
+++



## 显示行号
### 通过命令设置
1. 设置当前 Buffer 显示行号
```
M-x linum-mode
```

2. 设置所有 Buffer 显示行号
```
M-x global-linum-mode
```

### 配置文件里设置
``` emacs-lisp
;; 显示行号
(global-linum-mode t)
;; 或者
(global-linum-mode 1)
```

## 设置 tab
### 在 .emacs 配置文件中设置
``` emacs-lisp
;; tab改为空格
(setq-default indent-tabs-mode nil)
;; tab不改为空格
(setq-default indent-tabs-mode t)
;; 设置tab宽度
(setq default-tab-width 4)
;; c c++ 缩进4个空格
(setq c-basic-offset 4)
(setq c-default-style "linux")
```

### 将所有超过两个的连续空格使用TAB替换掉
```
M-x tabify
```

### 将所有TAB使用适当个数的空格替换掉
```
M-x untabify
```

## 设置启动时的窗口大小
``` emacs-lisp
;; 设置窗口位置为屏幕左上角(0, 0)
(set-frame-position (selected-frame) 0 0)
;; 设置宽度
(set-frame-width (selected-frame) 110)
;; 设置高度
(set-frame-height (selected-frame) 33)
```

## 关闭启动页面
``` emacs-lisp
(setq inhibit-splash-screen t)
```

## 更改 tango-dark 主题注释的颜色
```
// 1. 打开主题文件, Widows系统下的文件位置为:
emacs-25.3_1-x86_64\share\emacs\25.3\etc\themes\tango-dark-theme.el
// 2. 找到变量 cham-2(原值为: #73d216)
// 3. 改为: #a7adba
```

## 更改 emacs-color-theme-solarized 默认字体的颜色
```
// 1. 打开主题文件, Widows系统下的文件位置为:
.emacs.d/emacs-color-theme-solarized/solarized-definitions.el
// 2. 找到变量 base00(原值为: "#657b83")
(base00  "#657b83" "#52676f" "#626262" "brightyellow"  "yellow")
// 3. 将 "#657b83" 改为: "#3D3E3F" 或 "#586e75"
```

## 插入 TAB 字符的问题
emacs 中 TAB 键的作用相当于格式化缩进和排版, 要是想插入TAB字符, 应输入 `C-q TAB`
```
只按 TAB 并不能插入TAB字符, 插入 TAB 字符的命令为
C-q TAB
```

## emacs设置背景色
``` emacs-lisp
;; 设置背景色
(set-background-color "black")
;; 设置前景色
(set-foreground-color "white")
;; 设置区域前景色
(set-face-background 'region "blue")
;; 设置区域背景色
(set-face-background 'region "blue")
```

## emacs 设置中英文字体
``` emacs-lisp
(defun set-font (english chinese english-size chinese-size)
  (set-face-attribute 'default nil :font
                      (format   "%s:pixelsize=%d"  english english-size))
  (dolist (charset '(kana han symbol cjk-misc bopomofo))
    (set-fontset-font (frame-parameter nil 'font) charset
                      (font-spec :family chinese :size chinese-size))))

(set-font   "Source Code Pro" "Hiragino Sans GB" 16 20)
```

## 在配置文件中添加设置
### 高亮匹配字符
``` emacs-lisp
;; highlight marked region
(transient-mark-mode t)
```

## 语法高亮
``` emacs-lisp
(global-font-lock-mode t)
```

## 配置
``` emacs-lisp
;; show column number on status bar
(setq column-number-mode t)

;; close toolbar
(tool-bar-mode)

;; enable mouse wheel support
(mouse-wheel-mode)
(put 'upcase-region 'disabled nil)

;; 设置环境变量 "HOME" 和 "PATH
(setenv "HOME" "C:/emacs_home")
(setenv "PATH" "C:/emacs_home")

;; 设置emacs默认打开文件的路径
(setq default-directory "E:/emacs_workspace/")
(setq command-line-default-directory "E:/emacs_workspace/")
;;(add-to-list 'load-path "D:/emacs/")

;;set tab width
(setq-default tab-width 4)

;; 中文与外文字体设置
(defun set-font (english chinese english-size chinese-size)
  (set-face-attribute 'default nil :font
                      (format   "%s:pixelsize=%d"  english english-size))
  (dolist (charset '(kana han symbol cjk-misc bopomofo))
    (set-fontset-font (frame-parameter nil 'font) charset
                      (font-spec :family chinese :size chinese-size))))

(set-font   "Source Code Pro" "Consolas" 14 16)

;; 关闭启动页面
(setq inhibit-startup-message t)

;; title设置成 "文件名@Emacs"
(setq frame-title-format "%b@Emacs"

;; 高亮配匹配的字符
(show-paren-mode t)
(setq show-paren-style 'parentheses)
```

## 安装Packages
``` emacs-lisp
;; define function
(defun install-package (package)
  (if (not (package-installed-p package))
      (package-install package)))

;; install package
(install-package 'dart-mode)

```
