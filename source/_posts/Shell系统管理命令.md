---
title: Shelll系统管理命令
tags:
  - Linux
  - 技巧
categories: 实训日志
declare: true
abbrlink: 5065baa0
cover: https://w.wallhaven.cc/full/2e/wallhaven-2eroxm.jpg
date: 2020-06-18 15:00:00
---

## **前言**

实训第四天，下午

Shell系统管理常用命令的学习

<!-- more -->

## 一、用户管理

### 	1.用户管理命令

| 命令            | 说明                         | 示例                                   |
| --------------- | ---------------------------- | -------------------------------------- |
| adduser         | 创建用户并创建同名用户组     | adduser zhangsan    [--gid 1000]       |
| deluser         | 删除用户                     | deluser zhangsan                       |
| addgroup        | 创建用户组                   | addgroup test                          |
| delgroup        | 删除用户组                   | delgroup test                          |
| passwd          | 修改当前用户密码             | passwd 根据提示输入当前密码和新密码    |
| chmod ugoa+-rwx | 修改文件权限                 | chmod u+x aa.txt    chmod 765 aa.txt   |
| chown           | 修改文件所有者               | chown root aa.txt                      |
| chgrp           | 修改文件相关的用户组         | chfrp root aa.txt                      |
| su              | 切换用户                     | su root                                |
| sudo            | 以超级管理员身份执行特定操作 | sudo ls -l /root  需要修改/etc/sudoers |



## 二、进程管理

### 	2.1 进程概述

程序和进程关系
  - 程序安装或存储磁盘上的一组文件，静态，通常指未运行
  - 进程是运行程序的容器。启动一个程序，操作系统创建一个（或多个）进程（进程有编号 PID），加载程序的指令和数据到进程的内存区域，操作系统为该进程分配CPU时间片（多个进程交替获得CPU来运行）
  - 一个程序可以拥有多个进程，程序运行，至少启动一个进程
  - 一个进程只属于一个程序

- 进程与线程关系
  - 一个进程至少存在一个主线程
  - 线程是进程中独立的执行单元

> 每间教室是一个进程，有独立的空间，有一个共同的主题，但是存在多个执行单元，教师和二十个学生，21个线程

### 	2.2 进程管理命令

| 命令   | 说明                         | 示例                                  |
| ------ | ---------------------------- | ------------------------------------- |
| top    | 实时显示系统状态             | top       退出 ctrl+C                 |
| ps     | 进程快照，执行指令的瞬时状态 | ps  ,   ps -uroot  , ps-aux , ps  -ef |
| kill   | 杀死进程                     | kill -9 pid                           |
| vmstat | 系统状态统计                 |                                       |
| mpstat | 处理器状态统计               |                                       |
| \|     | 管道符号，连接两个命令       |                                       |
| grep   | 全局搜索匹配                 | ls -l \| grep nginx                   |
| which  | 定位一个命令或程序           | which nginx                           |
| find   | 查找文件或目录               | find . -name "nginx"                  |



## 三、服务管理

### 3.1 服务管理命令

服务的配置：`/etc` 存放基本配置，`/etc/init.d` 存放守护进程（开机自动启动的服务）
服务管理 `service`

* #### 查看状态

  `service mysql status`

* #### 启动

  `service mysql start`

* #### 停止

  `service mysql stop`

* #### 重启

  `service mysql restart`

* #### 重新加载配置文件

  `service mysql reload`

  

## 四、网络管理

### 4.1 网络管理命令

网络命令主要是和网络操作相关的一些命令

* #### 测试网络是否畅通

  `ping www.baidu.com`

* #### 查看网络配置

  `ifconfig`

* #### 查看网络状态信息

  `netstat -antu`