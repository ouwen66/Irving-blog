---
title: Vim编辑器
tags:
  - Linux
  - 技巧
categories: 实训日志
declare: true
abbrlink: 73bed3ab
cover: https://w.wallhaven.cc/full/13/wallhaven-13vym3.jpg
date: 2020-06-16 14:51:35
---

## **前言**

实训第二天，下午

学习的是使用Vim编辑器来开发shell程序

使用VIM编辑器来开发Java程序

<!-- more -->

## 一、用Vim编辑器编写第一个Java文件

打开Vim编辑器，默认的模式是命令模式

* 输入i，切换到输入模式
* 输入ESC,切换到命令模式
* 输入：，切换到底线命令模式
  * 输入w，保存文件
  * 输入q，退出编辑器
  
  用Vim编辑器新建一个java文件

```
root@iZ2ze4ojx7qtz1wv44gajnZ:~# vim hello.java
```

进入Vim编辑器后输入i切换到输入模式，编写java程序

```
public class hello{
        public static void main(String[] args){
                System.out.println("hello world!");
        }
}
```

编写完成后输入ESC切换到命令模式，然后输入:wq切换到底线命令模式保存并退出

```
:wq
```



## 二、运行第一个Java程序

Java源文件是不能直接执行的！！

需要先将Java源文件编译成class文件才能运行！！

需要jdk才能进行编译！！

使用apt工具来安装jdk！！

1. 首先先更新一下apt工具

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# apt update
   ```

2. 用apt命令安装openjdk

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# apt install openjdk-11-jdk-headless
   ```

   等待安装完成后，查看版本号检查是否安装完成

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# java -version
   openjdk version "11.0.7" 2020-04-14
   OpenJDK Runtime Environment (build 11.0.7+10-post-Ubuntu-2ubuntu218.04)
   OpenJDK 64-Bit Server VM (build 11.0.7+10-post-Ubuntu-2ubuntu218.04, mixed mode, sharing)
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# javac -version
   javac 11.0.7
   ```

3. 使用javac命令将Java源文件编译成class文件

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# javac hello.java
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# ls -l
   total 8
   -rw-r--r-- 1 root root 416 Jun 16 16:05 hello.class
   -rw-r--r-- 1 root root 104 Jun 16 15:03 hello.java
   ```

4. 执行Java程序

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# java hello
   hello world!
   ```

   *这里的java后的class文件是不用带后缀名的

   

## 三、使用Vim编辑器编写shell程序

shell程序不像java需要编译才能执行！！

但是需要申请执行shell脚本的权限！！

1. 使用Vim编辑器创建shell脚本

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# vim aa.sh
   ```

2. 编写shell脚本，保存并退出

   ```
   #定义数组
   myArray=(A B "C" 100)
   #输入数组的内容
   echo "元素1：${myArray[0]}"
   echo "元素2：${myArray[1]}"
   printf "%s %s \n" "元素3："${myArray[2]}
   printf "%s %s \n" "元素4："${myArray[3]}
   ```

3. 申请执行shell脚本的权限

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# chmod +x ./aa.sh
   ```

4. 执行shell脚本文件

   ```
   root@iZ2ze4ojx7qtz1wv44gajnZ:~# ./aa.sh
   元素1：A
   元素2：B
   元素3：C  
   元素4：100  
   ```

   

