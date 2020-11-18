---
title: Linux基本命令
tags:
  - Linux
  - 技巧
categories: 实训日志
declare: true
cover: https://w.wallhaven.cc/full/dg/wallhaven-dg9yjm.jpg
abbrlink: 8d1d62a8
date: 2020-06-16 11:51:35
---

## 前言

实训第二天，上午

学习的是Linux基本命令与shell脚本

<!-- more -->

## 一、Linux基本命令

* pwd：查看当前路径

  `root@用户ID:~#  pwd`
  
* ls：查看路径下的所有文件和目录

  `root@用户ID:~#  ls [选项] 目录名称`
  
  | 特殊符号 | 作用                                                         |
| -------- | ------------------------------------------------------------ |
  | -a       | 显示全部的文件，包括隐藏文件（开头为 . 的文件）也一起罗列出来，这是最常用的选项之一。 |
  | -h       | 以人们易读的方式显示文件或目录大小，如 1KB、234MB、2GB 等。  |
  | -i       | 显示 inode 节点信息。                                        |
  | -l       | 使用长格式列出文件和目录信息。                               |
  
* cd：切换目录

  `root@用户ID:~#  cd  目录路径`
  
  | 特殊符号 | 作用                       |
| -------- | -------------------------- |
  | ~        | 代表当前登录用户的主目录   |
  | ~用户名  | 表示切换至指定用户的主目录 |
  | -        | 代表上次所在目录           |
  | .        | 代表当前目录               |
  | ..       | 代表上级目录               |
  
* clear：清除屏幕

  `root@用户ID:~#  clear`
  
* mkdir：创建目录

  `root@用户ID:~#  mkdir [-mp] 目录名`
  
  | 特殊符号 | 作用                                                   |
| -------- | ------------------------------------------------------ |
  | -m       | 选项用于手动配置所创建目录的权限，而不再使用默认权限。 |
  | -p       | 选项递归创建所有目录                                   |
  
* rmdir：删除空目录

  `root@用户ID:~#  rmdir [-p] 目录名`
  
  | 特殊符号 | 作用                 |
| -------- | -------------------- |
  | -p       | 选项递归删除所有目录 |
  
* touch：创建文件

  `root@用户ID:~#  touch [选项] 文件名`
  
* rm：删除文件或目录

  `root@用户ID:~# rm[选项] 文件或目录`
  
* cp：复制文件或者目录

  `root@用户ID:~#  cp [选项] 源文件 目标文件`
  
* mv：移动或者重命名文件或者目录

  `root@用户ID:~# mv [选项] 源文件 目标文件`
  
  

## 二、Shell编程

Shell 编程跟 JavaScript、Java编程一样，只要有一个能编写代码的文本编辑器和一个能解释执行的脚本解释器就可以了。

Linux 的 Shell 种类众多，常见的有：

* Bourne Shell（/usr/bin/sh或/bin/sh）

* Bourne Again Shell（/bin/bash）

* C Shell（/usr/bin/csh）

* K Shell（/usr/bin/ksh）
* Shell for Root（/sbin/sh）

### 基本工作

**Linux有两个输出命令**

`root@用户ID:~#  echo 数据`

`root@用户ID:~#  printf "格式" 数据`

例如：

```
root@iZ2ze4ojx7qtz1wv44gajnZ:~# echo zhangsan
zhangsan
root@iZ2ze4ojx7qtz1wv44gajnZ:~# printf "%s \n" zhangsan
zhangsan 
```

**首先查看当前系统的shell环境**

```
root@iZ2ze4ojx7qtz1wv44gajnZ:~# echo $SHELL
/bin/bash
```

### Shell变量

1. Shell变量声明

```
name="zhangsan"
```

***注意***：变量名和等号之间不能有空格，这可能和你熟悉的所有编程语言都不一样。同时，变量名的命名须遵循如下规则：

* 命名只能使用英文字母，数字和下划线，首个字符不能以数字开头。

* 中间不能有空格，可以使用下划线（_）。

* 不能使用标点符号。

* 不能使用bash里的关键字（可用help命令查看保留关键字）。

2. Shell变量的使用

*使用shell变量只需要在变量前加一个 $ 即可*

```
root@iZ2ze4ojx7qtz1wv44gajnZ:~# name="zhangsan"
root@iZ2ze4ojx7qtz1wv44gajnZ:~# echo $name
zhangsan
```

3. Shell变量的删除

使用unset关键字来删除Shell变量

```
root@iZ2ze4ojx7qtz1wv44gajnZ:~# unset name
```

### Shell数组

1. 创建一个Shell数组

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# myArray=(A B "C" 100)
   ```
   
2. 输出数组中的数据

   ```
root@iZ2ze4ojx7qtz1wv44gajnZ:~# echo "第一个元素: ${myArray[0]}"
   第一个元素: A
   ```

3. 修改数组中的元素

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# myArray[1]=BB
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# echo ${myArray[1]}
   BB
   ```

4. 一次性输出所有的元素

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# echo ${myArray[@]}
   A BB C 100
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# echo ${myArray[*]}
   A BB C 100
   ```

5. 获得数组的长度

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# echo ${#myArray[@]}
   4
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# echo ${#myArray[*]}
   4
   ```

   

### Shell运算符

Shell 和其他编程语言一样，支持多种运算符，包括：

- 算数运算符
- 关系运算符
- 布尔运算符
- 字符串运算符
- 文件测试运算符

原生bash不支持简单的数学运算，但是可以通过其他命令来实现，例如 awk 和 expr，expr 最常用。

expr 是一款表达式计算工具，使用它能完成表达式的求值操作。

#### 算术运算符

下表列出了常用的算术运算符，假定变量 a 为 10，变量 b 为 20：

| 运算符 | 说明                                          | 举例                          |
| :----- | :-------------------------------------------- | :---------------------------- |
| +      | 加法                                          | `expr $a + $b` 结果为 30。    |
| -      | 减法                                          | `expr $a - $b` 结果为 -10。   |
| *      | 乘法                                          | `expr $a \* $b` 结果为  200。 |
| /      | 除法                                          | `expr $b / $a` 结果为 2。     |
| %      | 取余                                          | `expr $b % $a` 结果为 0。     |
| =      | 赋值                                          | a=$b 将把变量 b 的值赋给 a。  |
| ==     | 相等。用于比较两个数字，相同则返回 true。     | [ $a == $b ] 返回 false。     |
| !=     | 不相等。用于比较两个数字，不相同则返回 true。 | [ $a != $b ] 返回 true。      |

注意：条件表达式要放在方括号之间，并且要有空格，例如: [$a==$b] 是错误的，必须写成 [ $a == $b ]

(注意使用的是反引号 ` 而不是单引号 ')