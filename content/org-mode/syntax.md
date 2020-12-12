+++
title = "Org mode Syntax"
date = 2020-11-04T23:28:18+08:00
tags = ["OrgMode"]
+++

## 标题

标题的标记为: 一至多个 `*`

```org-mode
* 一级标题
** 二级标题
*** 三级标题
**** 四级标题
***** 五级标题
****** 六级标题
```

## 段落
起始直接书写内容即为段落, 段落之间以空行分隔

## 列表
列表包括: 有序列表, 无序列表, 描述列表; 同一级的列表缩进必须相同, 不同级的列表以不同缩进区分

### 有序列表
有序列表的标记为: `1.` 或 `1)`
```org-mode
  1. 有序列表一

  1) 有序列表二
```

### 无序列表
无序列表的标记为: `-`, `+`, `*`(使用 `*` 做列表项的标记时, 这一行必须缩进, 最好不使用 `*`)

```org-mode
  - 无序列表一

  + 无序列表二

  * 无序列表三
```

### 描述列表
描述列表的标记为: `::`

```org-mode
  列表项 :: 列表描述
```

## 超链接
类似于HTML, 可以添加文件内部的链接和文件外部的链接

```org-mode
  [[link][description]]

  [[link]]

  [[#my-custom-id]]
```

常用链接格式
```org-mode
| http://orgmode.org/org.html  | on the web          |
| file:/home/notes/note.org    | file, absolute path |
| /home/notes/note.org         | same as above       |
| ./notes/note.org             | same as above       |
| mailto:myemail@example.com   | mail link           |
```

## 表格

```org-mode
| Name  | Phone | Age |
|-------+-------+-----|
| name1 | 123   | 1   |
| name2 | 789   | 2   |
```

## 文本样式

### 加粗
```org-mode
  *加粗文本*
```

### 斜体
```org-mode
  /斜体/
```

### 删除线
```org-mode
  +删除线+
```

### 下划线
```org-mode
  _下划线_
```

### 等宽字
```org-mode
  =org=
```

### 下标
```org-mode
  H_2 O
  (下标和普通字符之间以一个空格分隔)
```

### 上标
```org-mode
  πr^2
```

## 源代码块
当源代码块中以 `*`, `,*`, `#+`, `,#+` 开始, 
在这些符号之前插入 `,` , 防止导出时解释为org的语法;
(代码内容最好在开始处添加两个或四个空格缩进)

```org-mode
  ,#+NAME: <name>
  ,#+BEGIN_SRC <language> <switches> <header arguments>
    <code body>
  ,#+END_SRC
```

## 待办事项
在标题的标记后面加上 `TODO`, 即变成待办事项; 
待办事项默认只有两种状态: `TODO` 和 `DONE`;
```org-mode
  ** TODO 待办事项一
```

通过设置TODO关键字标示事项处于工作流程中的不同状态, 
设置里的竖线 `|` 划分未完结状态和以完结状态

```emacs-lisp
(setq org-todo-keywords
  '((sequence "TODO" "FEEDBACK" "VERIFY" "|" "DONE" "DELEGATED")))
```

## 标签
每个标题可以包含多个标签; 标签放在标题的末尾位置;
标签的前后必须被冒号包括, 比如 `:notes:`

```org-mode
  * 标题一    :标签一:标签二:
  ** 标题二   :tag1:tag2:
```


