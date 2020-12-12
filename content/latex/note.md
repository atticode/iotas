+++
title = "LaTex Note"
date = 2020-11-07T11:10:10+08:00
tags = ["LaTeX"]
+++


## 编译器
XeLaTeX

## 支持中文的方法
以下方法需使用 XeLaTeX 编译
- 方法一: 导入以下宏包
```latex
\usepackage{fontspec, xunicode, xltxtra}
\setmainfont{KaiTi}
```

- 方法二: 导入 xeCJK 宏包
```latex
\usepackage{xeCJK}
```

- 方法三: 使用 CTeX 宏包
```latex
\documentclass[UTF8]{ctexart}
```

## beamer 支持中文的方法
```latex
\usepackage{fontspec, xunicode, xltxtra}
\setmainfont{KaiTi}
\setsansfont{KaiTi}
```

## 中文自动换行问题
```latex
% 在使用以下宏包支持中文时的解决方法
\usepackage{fontspec, xunicode, xltxtra}
\setmainfont{KaiTi}
\begin{document}
% 添加如下命令
\XeTeXlinebreaklocale "zh"
\XeTeXlinebreakskip = 0pt plus 1pt
% \usepackage{setspace}
% \onehalfspacing
% \XeTeXinterchartokenstate=1
```

## 设置导出的PDF页面大小
```latex
\usepackage{geometry}
\geometry{top=2cm, right=2cm, bottom=2cm, left=2cm}
```

## 编辑器
- TeXstudio
- Emacs + AUCTeX插件

## LaTex 发行版
- MikTeX
- TeX Live

## MikTeX 安装 beamer
1. 下载 beamer, pgf, xcolor
   + [[https://ctan.org/tex-archive/macros/latex/contrib/beamer/][beamer 下载]]
   + [[https://ctan.org/tex-archive/graphics/pgf/][pgf 下载]]
   + [[https://ctan.org/tex-archive/macros/latex/contrib/xcolor/][xcolor 下载]]
2. 将解压的文件夹分别命名为beamer, pgf, xcolor 并拷贝到 C:\MiKTeX 2.9\tex\latex\ 目录下
3. 打开命令行窗口, 运行 texhash

## LaTeX 段落与间距
* 水平间距
```latex
% 插入当前字体大小的空白
\quad
% 是`\quad`的两倍
\qquad
```

* 垂直间距
