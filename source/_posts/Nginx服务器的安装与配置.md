---
title: Nginx服务器安装与配置
tags:
  - Nginx
  - Linux
  - 技巧
categories: 实训日志
declare: true
cover: https://w.wallhaven.cc/full/v9/wallhaven-v9xxp8.png
abbrlink: d94918b2
date: 2020-06-17 09:51:35
---

## **前言**

实训第三天，下午

学习了Nginx服务器的安装与配置

<!-- more -->

## Nginx服务器

### 1. Nginx简介

* Nginx (engine x) 是由伊戈尔·赛索耶夫开发的，第一个公开版本0.1.0发布于2004年10月4日；
* Nginx是一款轻量级的Web 服务器/反向代理服务器；
* Nginx是一款电子邮件（IMAP/POP3）代理服务器；
* 中国大陆使用nginx网站用户有：百度、京东、新浪、网易、腾讯、淘宝等。


### 2. Nginx安装与卸载

#### 	安装

​	`apt install nginx`

#### 	卸载

​	`apt remove nginx`

### 3. Nginx的相关安装目录

Nginx安装好之后，相关文件会存放到一下的文件夹中：

* /usr/sbin/nginx：主程序
* /etc/nginx：存放配置文件
* /usr/share/nginx：存放静态文件
* /var/log/nginx：存放日志文件

### 4. Nginx配置管理

#### 	阿里云实例中添加访问规则

​      ![](https://gitee.com/ouwen666/my-image/raw/master/img/aliyun4.jpg)

#### 	编写Nginx配置文件

​		进入Nginx服务器的配置文件夹/etc/nginx，有一个conf.d，切到/etc/nginx/conf.d文件夹下

发现没有任何文件

​		![](https://gitee.com/ouwen666/my-image/raw/master/img/Nginx1.jpg)

​		使用Vim编辑器创建一个配置文件，文件名为nginx.conf，并编写配置信息

​		![](https://gitee.com/ouwen666/my-image/raw/master/img/Nginx2.jpg)

#### 	 编写Nginx首页

​		我们配置的Nginx的访问目录是/opt/www,首页是index.html，所以在/opt/www目录下创建index.html页面，并用vim打开编写以下内容：

​		![](https://gitee.com/ouwen666/my-image/raw/master/img/Nginx3.jpg)

### 5. 启动Nginx 

​	`service nginx start`

​	![](https://gitee.com/ouwen666/my-image/raw/master/img/Nginx4.jpg)

​	启动成功！！

​	*其他的一些操作命令：

​		停止服务器：`service nginx stop`

​		重新启动：`service nginx reload`

​		查看状态：`service nginx status`

​		查看端口：`netstat -apn`

​		杀死进程：`kill -9`



