+++
title = "Git Command"
date = 2020-11-07T11:06:43+08:00
tags = ["git"]
+++


## Git 本地新建分支并关联远程分支
``` shell
$ git checkout -b dev origin/dev
```

## 修改远程版本库
* 直接修改
```bash
git remote origin set-url [url]
```

* 先删除，再添加
```bash
  git remote rm origin
  git remote add origin [url]
```

