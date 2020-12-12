+++
title = "Android Device"
date = 2020-12-12T13:17:06+08:00
isCJKLanguage = true
description = ""
tags = ["android"]
categories = []
weight = 10
+++


# Android 设备连接 PC 调试

## linux

1. 在终端输入`lsusb`命令查看已连接的USB设备, 显示如下信息:
```shell
demo@demo-pc:~/android-sdk/platform-tools$ lsusb
Bus 002 Device 014: ID 18d1:4ee7 Google Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:58c1 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
其中`18d1`即为设备的ID.

2. 以root身份登陆，新建或编辑此文件: `/etc/udev/rules.d/51-android.rules`
```shell
vim /etc/udev/rules.d/51-android.rules
```

3. 将下面格式的内容添加到文件中:
`SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", MODE="0666", GROUP="plugdev"`
本例中`0bb4`为设备的ID, `MODE`赋值指定读/写权限, `GROUP`则定义哪个Unix组拥有设备节点

4. 以root身份执行以下命令
```shell
chmod a+r /etc/udev/rules.d/51-android.rules

```

5. 从SDK的`platform-tools/`目录执行`adb devices`验证设备是否连接.
+ 连接不成功的信息
```shell
demo@demo-pc:~/android-sdk/platform-tools$ ./adb devices
List of devices attached
19028B2305  no permissions (user in plugdev group; are your udev rules wrong?); see [http://developer.android.com/tools/device.html]
```
+ 连接成功的信息
```shell
w@w-pc:~/android-sdk/platform-tools$ ./adb devices
List of devices attached
19028B2305  device
```

6. Note: 如果以上未成功则执行以下命令后，重新打开终端验证
```shell
sudo service udev restart
sudo adb kill-server
sudo adb start-server
```


[参考文档](https://developer.android.google.cn/studio/run/device)
[参考文档1](http://developer.android.com/tools/device.html)
[Writing udev rules文档](http://www.reactivated.net/writing_udev_rules.html)
[GitHub51-android.rules](https://github.com/snowdream/51-android/blob/master/51-android.rules)
