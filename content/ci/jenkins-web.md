+++
title = "Jenkins"
date = 2020-12-12T13:19:07+08:00
isCJKLanguage = true
description = ""
tags = ["ci"]
categories = []
weight = 10
+++


## Jenkins 构建web项目

### 插件安装
* Publish Over SSH
* Nodejs
* Gitlab

### 配置目标服务器
1. 系统管理
2. 系统配置
3. Publish over SSH
4. SSH Server
5. Name: 标识服务器的名字
6. Hostname: 服务器IP
7. Username: 登录服务器的用户
8. Remote Directory: /
9. 勾选 `Use password authentication, or use a different key`
10. Passphrase / Password: 登录服务器的用户对应密码

### 配置nodejs工具
1. 系统管理
2. 全局工具配置
3. Nodejs
4. 别名: node-v12.18.3
5. 安装目录: `/usr/local/nodejs`
6. 取消选中自动安装

### 新建任务
1. 输入任务名称
2. 选择 构建一个自由风格的软件
3. 点击 确定

#### 源码管理
4. 勾选 Git
5. Repository URL: gitlab 的仓库地址
6. Credentials: 点击添加
7. 输入gitlab的用户名密码
8. 点击 添加按钮

#### 构建触发器
1. 勾选 Build when a change is pushed to GitLab. GitLab webhook URL: ......
2. 点击高级按钮
3. Secret token: 点击 Generate 按钮

#### 构建环境
1. 勾选 `Provide Node & npm bin/ folder to PATH`
2. NodeJS Installation: 选择配置的Nodejs工具

#### 构建
1. 点击 增加构建步骤 按钮
2. 选择 执行Shell
3. 输入 构建命令
4. e.g.
   ```shell
   node --version
   npm --version
   ```
#### 构建后操作
1. 点击 增加构建后操作步骤 按钮
2. 选择 Send build artifacts over SSH
3. Name: 选择上面配置的目标服务器
4. Source files: 相对于该项目workspace对应的文件路径
5. Remove prefix: 上面 Source files 的目录路径
6. Remote directory: 上传到目标服务器的目录
7. Exec command: 在目标服务器上要执行的shell命令

### 配置Gitlab Webhook
1. Setting
2. Webhooks
3. URL: 上面构建触发器里[GitLab webhook URL]显示的URL
4. Secret Token: 上面构建触发器生成的Token
5. 点击 Add webhook

