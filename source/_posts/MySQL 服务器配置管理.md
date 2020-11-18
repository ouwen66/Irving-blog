---
title: MySQL服务器配置管理
tags:
  - MySQL
  - Linux
  - 技巧
categories: 实训日志
declare: true
cover: https://w.wallhaven.cc/full/g7/wallhaven-g7z2eq.jpg
abbrlink: 268fc8fd
date: 2020-06-17 09:51:35
---

## **前言**

实训第三天，上午

学习了Linux上MySQL数据库服务端的安装与配置

<!-- more -->

## 一、安装MySQL8.0

### 1. 使用命令下载MySQL8的软件库

`wget https://dev.mysql.com/get/mysql-apt-config_0.8.15-1_all.deb`

### 2.安装MySQL的数据源

`dpkg -i mysql-apt-config_0.8.15-1_all.deb`

### 3. 更新系统的apt软件仓库

`apt update`

### 4. 开始安装mysql

`apt install mysql-server`

### 5. 安装完成

输出mysql出现以下代码说明安装成功

```
root@iZ2ze4ojx7qtz1wv44gajnZ:~# mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```

## 二、连接MySQL8.0

### 1.本地连接MySQL(在服务器上连接MySQL)

```
root@iZ2ze4ojx7qtz1wv44gajnZ:~# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 8.0.20 MySQL Community Server - GPL

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
```

*注意：输入密码时，是没有任何提示的；出现mysql>时连接成功

### 2.远程连接MySQL(在个人电脑上连接MySQL)

#### 2.1 首先在个人电脑上安装MySQL的客户端

​	*我设备上是Navicat客户端，这里就以Navicat客户端为例，演示进行如何远程连接

![](https://gitee.com/ouwen666/my-image/raw/master/img/Navicat.jpg)

#### 2.2  mysql默认是不允许进行远程连接的，需修改成允许远程连接

​		现在服务端进入mysql，进行以下修改:

​		连接数据库

​		`mysql -uroot -p`

​		使用mysql数据库

​		`use mysql;`

​		修改user表中的root用户的host数据

​		` update user set host = '%' where user = 'root';`

#### 2.3 阿里云的服务器的安全规则中是不允许任何远程访问的，需在阿里云中作以下修改：

​		实例详情>>本实例安全组>>规则配置

​		!![](https://gitee.com/ouwen666/my-image/raw/master/img/aliyun1.jpg)

​		>>快速添加

​		![](https://gitee.com/ouwen666/my-image/raw/master/img/aliyun2.jpg)

​		>>MySQL(3306)

​		![](https://gitee.com/ouwen666/my-image/raw/master/img/aliyun3.jpg)

#### 2.4 重启MySQL服务

​		`service mysql restart`

​		*停止服务：service mysql stop  |  启动服务：service mysql start

#### 2.5 在个人电脑上进行连接

(在个人电脑上可以用图形化客户端连接，也可以用命令行来连接)

##### 		打开Navicat客户端，进行连接

​		![](https://gitee.com/ouwen666/my-image/raw/master/img/Navicat1.jpg)

##### 		常规配置

​	![](https://gitee.com/ouwen666/my-image/raw/master/img/Navicat2.jpg)

##### 		SSH配置

​		![](https://gitee.com/ouwen666/my-image/raw/master/img/Navicat3.jpg)

##### 		测试连接

​		![](https://gitee.com/ouwen666/my-image/raw/master/img/Navicat4.jpg)

##### 		连接成功

​		![](https://gitee.com/ouwen666/my-image/raw/master/img/Navicat5.jpg)

##### 		在命令行中进行连接

​		在cmd中输入以下命令回车，然后输入服务器上mysql的密码即可连接成功

​		`mysql -h 主机名 -uroot -p`

## 三、MySQL表数据的操作

### SQL语句总共有四种：

* DDL语句(数据定义语句)
* DCL语句(数据控制语句)
* DML语句(数据操作语句)
* TCL语句(事务控制语句)

#### 往表中插入数据

`insert into 表名(字段名,字段名) values(值,值);`

#### 查询表中的数据

`select * from 表名;`//查询所有

#### 修改表中的数据

`update 表名 set 字段名=值 where 字段名=值;`//where后面是修改条件

#### 删除表中的数据

`delete from 表名 where 字段=值;`//where后面是删除条件

