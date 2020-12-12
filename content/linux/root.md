+++
title = "Root"
date = 2020-12-12T13:28:40+08:00
isCJKLanguage = true
description = ""
tags = []
categories = []
weight = 10
+++




Linux命令----su（切换用户）以及passwd（修改用户密码）
一、su命令登录root

用户在使用telnet命令可以远程登录，但不可以登录root，这样就需要使用su命令来登录root用户。

telnet登录（不能登录root）---

1.启动终端 输入
telnet ip   //ip为Linux系统的ip

2.在login处输入root，在password处输入root密码

最后显示Login incorrect却不能登录上root
su登录（可以登录root）----

在终端输入“su - root”回车，出现password后输入密码（密码不显示）回车

[root@yuan ~]$ su - root
Password:
[root@yuan ~]#
则可以登录root

二、passwd命令修改用户密码

输入passwd(按提示输入旧密码和新密码，注：如果密码太短将会提示并重新输入）

[yuan@yuan ~]$ passwd
Changing password for user yuan.
Changing password for yuan
(current) UNIX password:
NEW UNIX password:
passwd另一个功能为：查看用户密码状态

passwd -S 用户名     //S必须为大写

[root@yuan ~]# passwd -S root
root PS 2018-08-08 0 99999 7 -1 (Password set, SHA512 crypt.)
可以看出Linux密码是经过SHA512算法加密过的。

同样可以使用--status命令查看密码状态

[root@yuan ~]# passwd --status root
root PS 2018-08-08 0 99999 7 -1 (Password set, SHA512 crypt.)
---------------------
作者：CircleYua
来源：CSDN
原文：https://blog.csdn.net/kingyuan666/article/details/81510316
版权声明：本文为博主原创文章，转载请附上博文链接！


## Ubuntu的su密码开启

通常在Linux中输入su命令，可以直接使用root权限来执行操作。

安装完成Ubuntu后，直接输入su命令，输入密码会提示认证错误。

主要是由于root用户没有赋值密码的原因。

我们可以通过sudo passwd root命令来给root用户赋值密码。

输入一边当前用户密码，然后两边root密码后回车即可。

注：su和sudo的区别是：

su的密码是root的密码，su直接将身份变成root用户。

sudo的密码是用户的密码，而sudo是以当前用户登录后，以root的身份运行命令，不需要知道root密码。


---------------------
作者：Jackie的储物袋
来源：CSDN
原文：https://blog.csdn.net/jackiexzy/article/details/79398520
版权声明：本文为博主原创文章，转载请附上博文链接！


## Linux系统su命令的详细用法

1.命令作用

su的作用是变更为其它使用者的身份，超级用户除外，需要键入该使用者的密码。

2.使用方式

su [-fmp] [-c command] [-s shell] [--help] [--version] [-] [USER [ARG]]

3.参数说明

-f ， –fast：不必读启动文件（如 csh.cshrc 等），仅用于csh或tcsh两种Shell。

-l ， –login：加了这个参数之后，就好像是重新登陆一样，大部分环境变量(例如HOME、SHELL和USER等)都是以该使用者(USER)为主，并

且工作目录也会改变。如果没有指定USER，缺省情况是root。

-m， -p ，–preserve-environment：执行su时不改变环境变数。

-c command：变更账号为USER的使用者，并执行指令（command）后再变回原来使用者。

–help 显示说明文件
–version 显示版本资讯

USER：欲变更的使用者账号，
ARG:  传入新的Shell参数。

4.例子

su -c ls root 变更帐号为 root 并在执行 ls 指令后退出变回原使用者。

su [用户名]

a>在root用户下, 输入 su 普通用户. 则切换至普通用户, 从root切换到变通用户不需要密码

b>在普通用户下, 输入 su [用户名]
提示 password:
输入用户的PASSWORD, 则切换至该用户

扩展阅读一:Linux下 su命令与su - 命令有什么区别？

su 是切换到其他用户，但是不切换环境变量（比如说那些export命令查看一下，就知道两个命令的区别了）

su - 是完整的切换到一个用户环境

所以建议大家切换用户的时候,尽量使用 su -  linuxso 这样 否则可能发现某些命令执行不了

扩展阅读二:su和sudo的区别



由于su 对切换到超级权限用户root后，权限的无限制性，所以su并不能担任多个管理员所管理的系统。如果用su 来切换到超级用户来管理系统，也不能明确哪些工作是由哪个管理员进行的操作。特别是对于服务器的管理有多人参与管理时，最好是针对每个管理员的技术特长和 管理范围，并且有针对性的下放给权限，并且约定其使用哪些工具来完成与其相关的工作，这时我们就有必要用到 sudo。

通过sudo，我们能把某些超级权限有针对性的下放，并且不需要普通用户知道root密码，所以sudo 相对于权限无限制性的su来说，还是比较安全的，所以sudo 也能被称为受限制的su ；另外sudo 是需要授权许可的，所以也被称为授权许可的su；

sudo 执行命令的流程是当前用户切换到root（或其它指定切换到的用户），然后以root（或其它指定的切换到的用户）身份执行命令，执行完成后，直接退回到当前用户；而这些的前提是要通过sudo的配置文件/etc/sudoers来进行授权；


su命令和su -命令区别就是：

su只是切换了root身份，但Shell环境仍然是普通用户的Shell；而su -连用户和Shell环境一起切换成root身份了。只有切换了Shell环境才不会出现PATH环境变量错误，报command not found的错误。

su切换成root用户以后，pwd一下，发现工作目录仍然是普通用户的工作目录；而用su -命令切换以后，工作目录变成root的工作目录了。

用echo $PATH命令看一下su和su - 后的环境变量已经变了。
