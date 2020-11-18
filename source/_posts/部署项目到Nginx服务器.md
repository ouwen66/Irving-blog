---
title: 部署项目到Nginx服务器
tags:
  - Nginx
  - Linux
  - 技巧
categories: 实训日志
cover: https://w.wallhaven.cc/full/ey/wallhaven-eyd5j8.png
declare: true
abbrlink: 5351ac83
date: 2020-06-18 09:00:00
---

## **前言**

实训第四天，上午

Nginx服务器的项目部署

<!-- more -->

## 一、将客户端上传到服务器

### 	1. 安装putty文件上传工具

​			下载地址：[官网下载](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

​			下载好安装包，双击打开进行安装，一直next即可

### 	2. 使用putty工具上传和下载文件

​			上传文件

​			`pscp 本地文件路径 root@公网IP:路径`

​			输入密码后上传成功

```
C:\Users\Admin>pscp E:\test\aa.txt root@112.126.76.74:/opt/www
root@112.126.76.74's password:
```

​			上传文件夹

​			`pscp -r 本地文件夹路径 root@公网IP:路径`

​			![](https://gitee.com/ouwen666/my-image/raw/master/img/putty.jpg)

​			下载文件

​			`pscp root@公网IP:文件路径 本地路径`

​			下载文件夹

​			`pscp -r root@公网IP:文件夹路径 本地路径`

### 	3. 检查服务器上是否有上传文件

​			检查要访问的默认文件夹是不是在nginx的配置文件中的默认根目录(/opt/www)				![](https://gitee.com/ouwen666/my-image/raw/master/img/putty1.jpg)

​			如果不在，有两种解决办法

​			1.修改配置nginx的配置文件中root目录（加一个目录root /opt/www/web）

​				![](https://gitee.com/ouwen666/my-image/raw/master/img/putty2.jpg)

​			2.将上传的资源移动到nginx.com配置文件中的root目录中

### 	4. 重新加载nginx配置资源

​			`service nginx reload`

### 	5. 打开浏览器访问

可以看到现在还查询不到疫情数据，因为服务端还没配置好

下一步就是配置服务端，使之能成功查询到疫情数据

​			![](https://gitee.com/ouwen666/my-image/raw/master/img/putty3.jpg)

## 二、将服务端上传到服务器

### 1. 上传服务端文件

```
C:\Users\Admin>pscp -r E:\学习文档\test\server root@112.126.76.74:/opt/www
root@112.126.76.74's password:
```

### 2. 修改客户端访问数据地址为服务器的IP地址

/opt/www/web/index.html

![](https://gitee.com/ouwen666/my-image/raw/master/img/putty4.jpg)

### 3. 安装NodeJS

`apt install nodejs`

输入node检查是否安装成功：

![](https://gitee.com/ouwen666/my-image/raw/master/img/putty5.jpg)

### 4. 启动服务端

进到服务端的上传文件夹，用nodejs启动服务端

/opt/www/server/index.js

`node index`

![](https://gitee.com/ouwen666/my-image/raw/master/img/putty6.jpg)

### 5. 在阿里云实例安全组配置新规则

手动添加8090端口的访问规则

![](https://gitee.com/ouwen666/my-image/raw/master/img/putty7.jpg)

### 6. 浏览器中访问

可以看到成功查询到了疫情数据

![](https://gitee.com/ouwen666/my-image/raw/master/img/putty8.jpg)