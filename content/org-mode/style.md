+++
title = "Org mode 样式"
date = 2020-11-04T23:29:18+08:00
tags = ["OrgMode"]
+++


## 导出HTML样式
```
#+HTML_HEAD: <style>body{padding: 15px 20px 25px;}table,tr,th,td{border:1px solid #C6CBD1;} tbody>tr:nth-child(even){background-color:#F6F8FA;}</style>
#+HTML_HEAD: <style>table{margin: 20px;}#postamble{margin-top:15px;}#postamble .creator, #postamble .validation{display: none;}</style>
#+HTML_HEAD: <style>tbody{border-top: 2px solid #5185d9;}</style>
```