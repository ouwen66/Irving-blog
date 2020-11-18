---
title: Redis数据库
tags:
  - Linux
  - 技巧
  - Redis
categories: 实训日志
declare: true
cover: https://w.wallhaven.cc/full/ey/wallhaven-eyl1xr.jpg
abbrlink: eb52a7b2
date: 2020-06-19 15:51:35
---

## **前言**

实训第五天，上午

Redis数据库的学习

<!-- more -->

## 一、Redis简介

![](https://gitee.com/ouwen666/my-image/raw/master/img/redis.jpg)

* REmote DIctionary Server(Redis) 是一个由Salvatore Sanfilippo写的key-value存储系统。
* Redis是一个开源的使用ANSI C语言编写、遵守BSD协议、支持网络、可基于内存亦可持久化的日志型、Key-Value数据库

## 二、Redis安装

### 安装Redis

在ubuntu上，使用 apt工具可以非常方便的安装和卸载 redis数据库

`apt install redis-server`

![](https://gitee.com/ouwen666/my-image/raw/master/img/redis1.jpg)

### 查看安装位置

用于检查是否安装成功

`whereis redis`

![](https://gitee.com/ouwen666/my-image/raw/master/img/redis2.jpg)

### 卸载Redis

`apt --purge autoremove redis-server`

![](https://gitee.com/ouwen666/my-image/raw/master/img/redis3.jpg)

## 三、连接Redis

### 本地连接

`redis-cli`

```
root@iZ2ze4ojx7qtz1wv44gajnZ:~# redis-cli
127.0.0.1:6379> 
```

### 远程连接

`redis-cli -h IP地址 -p 6379`

## 四、Redis基本配置

Redis 的配置文件位于 Redis 安装目录下，文件名为 redis.conf
可以通过 CONFIG 命令查看或设置配置项。

* 查看配置文件信息中的日志等级
  `CONFIG GET loglevel`
* 获得所有的配置参数
  `CONFIG GET *`
* 获得指定的配置参数
  `CONFIG GET 属性`
* 修改指定配置参数
  `config set 属性 值`
  `config set loglevel “notive”`

## 五、Redis基本操作

### 5.1 Redis的数据库

redis 一共有16个数据库，数据库没有名字，采用0~15这16个数字来标记
默认的数据库是0

可以通过`select`命令来切换数据库

```
127.0.0.1:6379> select 2
OK
127.0.0.1:6379[2]>    //切换到[2]数据库了
```

### 5.2 数据类型

* 字符串
* 列表类型[类似于Java中的List]
* 集合类型 [类似于Java中的Set]
* 哈希类型 [类似于java中的哈希表]

### 5.3 字符串操作

添加，如果名字存在，就覆盖
`set 变量名 值`

```
127.0.0.1:6379[2]> set username "zhangsan"
OK
```

获得
`get 变量名`

```
127.0.0.1:6379[2]> get username
"zhangsan"
```

删除
`del 变量名`

```
127.0.0.1:6379[2]> del username
(integer) 1
```

设置过期时间。默认是永久
`set 变量名 值 EX 时间`   //时间是以秒为单位的

```
127.0.0.1:6379[2]> set username zhangsan EX 10
OK
```

查看过期时间
`ttl 变量名`

```
127.0.0.1:6379[2]> ttl username
(integer) 8  //还有8秒过期
```

查看所有的键值对
`keys *`

```
127.0.0.1:6379[2]> keys *
1) "age"
2) "username"
```

## 六、列表操作

在列表的左边添加数据
`lpush 变量名 值`

```
127.0.0.1:6379> lpush username "zhangsan"
(integer) 1
```

在列表的右边添加数据
`rpush 列表名 值`

```
127.0.0.1:6379> rpush username "lisi"
(integer) 2
```

查看列表中的元素 起始位置  结束位置，结束-1表示查看所有
`lrange 列表名 起始位置 结束位置`

```
127.0.0.1:6379> lrange username 0 -1
1) "zhangsan"
2) "lisi"
```

移除并返回列表key的头元素（移除左边第一个数据）
`lpop 列表名`

```
127.0.0.1:6379> lpop username
"zhangsan"
```

移除并返回列表key的尾元素（移除右边第一个数据）
`rpop 列表名`

```
127.0.0.1:6379> rpop username
"lisi"
```

返回列表中的指定索引的元素
`lindex 列表名 索引值`

```
127.0.0.1:6379> lindex username 0
"zhangsan"
```

获取列表中的元素个数
`llen 列表名`

```
127.0.0.1:6379> llen username
(integer) 2   //表示列表中只有2
```

移除列表中的数据
`lrem 列表名 删除个数 值`

```
127.0.0.1:6379> lrem username 2 zhangsan
(integer) 2
```

## 七、集合操作

集合是不保证元素顺序的

添加元素 [可以同时添加多个]
`sadd 集合名 值`

```
127.0.0.1:6379> sadd username zhangsan lisi
(integer) 2
```

查看元素
`smembers 集合名`

```
127.0.0.1:6379> smembers username
1) "lisi"
2) "zhangsan"
```

删除元素,可以同时删除多个
`srem 集合名 值 值`

```
127.0.0.1:6379> srem username zhangsan lisi
(integer) 2
```

查看集合中的元素个数
`scard 集合名`

```
127.0.0.1:6379> scard username
(integer) 2
```

