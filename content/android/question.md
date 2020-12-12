+++
title = "Android 常见问题"
date = 2020-11-05T23:26:18+08:00
tags = ["android"]
+++


## 打开项目是运行 gradle build 时一直loading问题
修改gradle/wrapper/gradle-wrapper.properties文件
将 distributionUrl=https\://services.gradle.org/distributions/gradle-4.4-all.zip
改为 distributionUrl=https://services.gradle.org/distributions/gradle-4.4-all.zip
(去掉反斜线)

## 无法下载 junit 问题
在 app/build.gradle 文件中 "apply plugin: 'com.android.application'" 下面添加如下内容
allprojects {
    repositories {
        maven { url 'http://repo1.maven.org/maven2' }
    }
}

## Android Studio 添加依赖时jar包下载的位置
C:/User/admin/.gradle/caches/modules-2/file-2.1

## Cordova 在当前应用打开其他链接页面
在 config.xml 文件的</widget>上面添加 <allow-navigation href="*" /> 内容


