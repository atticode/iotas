+++
title = "JDK 安装"
date = 2020-11-04T23:25:18+08:00
tags = ["java"]
+++

## Windows

### 下载JDK
根据系统, 选择下载32位或64位的 '.exe'格式文件
[JDK 下载地址](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

### 安装JDK
双击下载的执行文件, 安装到指定目录, 比如 'C:/java/jdk'

安装 JDK 的过程中, 最后会提示安装单独的 JRE, JRE 的安装可选可不选, JDK 已经自带 JRE

### 配置系统环境变量

```
// 1. 新建 JAVA_HOME 变量(值为安装的目录)
JAVA_HOME  C:/java/jdk

// 2. 新建 CLASSPATH 变量
CLASSPATH  .;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar

// 3. 在 PATH 变量的值前面添加下面内容
PATH  %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
```


## Linux
### 下载JDK
根据系统选择下载32位或64位的 '.tar.gz' 格式的文件

### 安装JDK
在命令行下转到下载的文件所在目录, 运行如下命令:

```bash
# 解压文件到指定目录
sudo tar -zxvf jdk-8u151-linux-x64.tar.gz -C /usr/local/
```

### 配置环境变量
1. 打开配置文件
```bash
sudo vi /etc/profile
```

2. 添加如下内容
```bash
# 设置 java 环境
export JAVA_HOME=/usr/local/jdk1.8.0_151
export CLASSPATH=.:$JAVA_HOME/lib:$JAVA_HOME/lib/tools.jar
export PATH=&JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
```

3. 重启电脑或运行 'sudo source /etc/profile' 使之生效

## 测试 JDK 是否已配置好
在命令行下输入以下几个命令:
```bash
# 查看当前安装的 JDK 版本信息
java -version

# 显示javac的命令帮助
javac
```
