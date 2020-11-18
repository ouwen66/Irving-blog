---
title: 解决flutter doctor检测不到插件的问题
tags:
  - Android Studio
  - 技巧，Flutter
categories: Android
declare: true
cover: https://w.wallhaven.cc/full/73/wallhaven-73dvz3.png
abbrlink: a147dce
date: 2020-02-25 19:22:50
---


## 前言
今天学习混合模式移动应用开发，老师教我们如何在Windows上配置flutter的开发环境。

这里主要是针对Android Studio，将flutter搭建到Android Studio上。

<!--more-->
## 问题
在AS中安装了flutter和dart插件后命令行用flutter doctor检测发现以下问题：
```
C:\Users\Admin>flutter doctor
Doctor summary (to see all details, run flutter doctor -v):
[√] Flutter (Channel stable, v1.12.13+hotfix.8, on Microsoft Windows [Version 10.0.18363.657],
    locale zh-CN)
[√] Android toolchain - develop for Android devices (Android SDK version 29.0.2)
[!] Android Studio (version 3.5)
    X Flutter plugin not installed; this adds Flutter specific functionality.
    X Dart plugin not installed; this adds Dart specific functionality.
[!] Connected device
    ! No devices available

! Doctor found issues in 1 category.

```
显而易见的，这个提示的是我flutter和dart插件未安装，但是我AS里显示都安装好了

## 解决办法
这个问题是由自定义AS的安装路径及修改IDE的缓存目录造成的，导致flutter找不到插件下载位置，查阅百度后得到以下解决方案：
1.在IDE的安装目录下(注意是安装目录，不是sdk目录)的bin下面找到idea.properties配置文件，打开查看这两个路径目录：
```
idea.config.path=D:/Android/.AndroidStudio/config

idea.system.path=D:/Android/.AndroidStudio/system 
```
2.将上面查询到的路径里的文件拷贝到C:\Users\xxx\.AndroidStudio3.5下(xxx代表你的计算机名)，这样flutter doctor就能找到你在AS中所安装的插件了

## 总结
搭建flutter开发环境的过程中，坑很多，要耐心的解决每一个问题。