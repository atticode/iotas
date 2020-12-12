+++
title = "Example"
date = 2020-12-12T14:14:02+08:00
tags = []
categories = []
isCJKLanguage = true
description = ""
weight = 10
+++

* docker

## httpd
### With Dockerfile

``` dockerfile
FROM httpd:2.4
COPY /home/w/docker/httpd/www/ /usr/local/apache2/htdocs/
```

``` shell
$ docker build -t httpd .
$ docker run -dit --name httpd -p 80:80 httpd
```

### Without Dockerfile
``` shell
$ docker run -dit --name httpd -p 80:80 -v /home/w/docker/httpd/www/:/usr/local/apache2/htdocs/ httpd:2.4
```

### Configuration
``` dockerfile
FROM httpd:2.4
COPY /home/w/docker/httpd/httpd.conf /usr/local/apache2/conf/httpd.conf
COPY /home/w/docker/httpd/www/ /usr/local/apache2/htdocs/
```

## php-apache
``` dockerfile
sudo docker run --name php-apache -p 99:80 -v /home/w/docker/php/www:/var/www/html/ -dit --rm php:7.3-apache
```

## php
``` shell
docker run --name php -v /home/w/docker/nginx/www:/www  -dit --rm php:7.3-fpm
```

## nginx
复制Nginx的配置文件
``` shell
$ docker run --name nginx-tmp -d nginx:1.15
$ docker cp nginx-tmp:/etc/nginx/nginx.conf /home/w/docker/nginx/nginx.conf
$ docker rm -f nginx-tmp
```

### 编辑配置文件

* nginx 处理PHP的配置

``` 
server {
    listen       80;
    server_name  localhost;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm index.php;
    }

    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

    # proxy the PHP scripts to Apache listening on 127.0.0.1:80
    #
    #location ~ \.php$ {
    #    proxy_pass   http://127.0.0.1;
    #}

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    # 修改root值
    location ~ \.php$ {
        root           /var/www/html;    # 提示未找到文件时，需要配置此项
    #   fastcgi_pass   172.17.0.4:9000;  # 如果用容器名称不行时，则使用IP
        fastcgi_pass   php:9000;         # 容器名称:端口
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include        fastcgi_params;
    }

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    #    deny  all;
    #}
}


```

* 负载均衡配置

``` config
#events {
#    accept_mutex on;   #设置网路连接序列化，防止惊群现象发生，默认为on
#    multi_accept on;  #设置一个进程是否同时接受多个网络连接，默认为off
#    #use epoll;      #事件驱动模型，select|poll|kqueue|epoll|resig|/dev/poll|eventport
#    worker_connections  1024;    #最大连接数，默认为512
#}

upstream balance {
#    hash $request_uri;
#    server ci:80;
    server nginx-php:80;   # 容器名称(容器别名):端口
}

upstream balance-ci {
    server ci:80;
}

server {
    listen       80;
    server_name  localhost;

    #charset koi8-r;
    #access_log  /var/log/nginx/host.access.log  main;

    location / {
        #root   /usr/share/nginx/html;
        index  index.html index.htm index.php;
        proxy_pass http://balance;
    }
    location /index.php/ {
        #root   /usr/share/nginx/html;
        index  index.html index.htm index.php;
        proxy_pass http://balance-ci;
    }


    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    #    deny  all;
    #}
}

```


### 启动Nginx容器
``` shell
docker run --name nginx -p 88:80 -dit --rm \
    -v /home/w/docker/nginx/www:/usr/share/nginx/html:ro \
    -v /home/w/docker/nginx/conf.d:/etc/nginx/conf.d:ro \
    --link php:php \
    nginx:1.15
```


## portal(负载均衡)
### 运行容器的命令
``` shell
sudo docker run --name portal -p 80:80 -dit --rm \
 -v /home/w/docker/portal/www:/usr/share/nginx/html:ro \
 -v /home/w/docker/portal/conf.d:/etc/nginx/conf.d:ro \
 --link=php-apache-ci:ci \
 --link=nginx:nginx-php \
 nginx:1.15

```

### 备注
nginx docker的负载均衡连接其他容器的端口是容器内部的的端口

## node
``` shell
sudo docker run --name node-demo -p 3000:3000 -v /home/w/docker/node/demo:/home/node/app/ -dit --rm node:12
```


## docker run 参数
* `--link <name or id>:alias`: 添加链接到另一个容器；容器名称或id:定义别名——其他容器可通过别名访问此容器
* `-p 8080:80` : 指定端口映射，格式为：主机(宿主)端口:容器端口
* `--rm`: 容器退出时就自动清理容器内部的文件系统
* `--name name`: 容器运行的名称
* `-d`: 后台运行容器，并返回容器ID
* `-i`: 以交互模式运行容器，通常与 -t 同时使用
* `-t`: 为容器重新分配一个伪输入终端，通常与 -i 同时使用
* `-dit`: `-d -i -t`的简写
* `--volume , -v`: 绑定一个卷
* `-m`: 设置容器使用内存最大值

## docker 使用network代替--link选项
1. 创建network
``` shell
docker network create env-net
```
2. 运行mysql docker镜像
```
docker run -p 3306:3306 --name env-mysql -d \
    --network env-net --network-alias mysql \
    -e MYSQL_ROOT_PASSWORD=123 \
    mysql
```

3. 运行 wordpress 镜像
```
docker run -p 80:80 --name env-web -d \
    --network env-net --network-alias wordpress \
    -e WORDPRESS_DB_PASSWORD=123 \
    wordpress
```

4. 验证
``` shell
docker exec -it env-web /bin/bash

root@202fdad27426:/var/www/html# ping -w 2 mysql
```

### docker run 参数
* `--network net-name`: 将此容器加入到net-name网络中
* `--network-alias mysql`：指定容器在net-name网络中的别名是mysql

