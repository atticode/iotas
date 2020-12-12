+++
title = "常见问题"
date = 2020-11-07T22:59:52+08:00
tags = ["frontend"]
+++

## npm install 问题
* 安装VC++和Python依赖

[[https://github.com/nodejs/node-gyp][参考文档]]


## Cordova build 问题
* Build时出现 Execution failed for task ':processReleaseResources'

解决: 在platforms/android/build.gradle文件的def promptForReleaseKeyPassword()上面添加如下代码
```gradle
configurations.all {
  resolutionStrategy {
    force 'com.android.support:support-v4:24.1.1'
  }
}
```
	
原因: compile "com.android.support:support-v4:+" 带 + 号指要用最新版本
```
// 添加 force 强制指定annotations
force 'com.android.support:support-v4:27.1.0'
```
