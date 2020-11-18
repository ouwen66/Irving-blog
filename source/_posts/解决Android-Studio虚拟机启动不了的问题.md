---
title: 解决Android Studio虚拟机启动不了的问题
tags:
  - Android Studio
  - 技巧
categories: Android
declare: true
cover: https://w.wallhaven.cc/full/6o/wallhaven-6oj73l.jpg
abbrlink: bc509111
date: 2020-02-16 13:22:50
---


## 前言
过几天就要线上教学了，应学院老师要求检查自身设备及软件情况。

其中检查Android Studio的运行情况时，出了点问题。

<!-- more -->
## 问题
运行虚拟机时卡在开机页面，下方显示下载信息：`waiting for target device to come online`

## 解决办法
这个问题是由虚拟机引起的，查阅相关资料，获得以下解决方案：
1. 先关掉正在运行的模拟器
2. 点击上方工具栏中的Tools>AVD Manager,进到模拟器管理页面，点击自己的模拟器选项，选择Clod Boot Now，模拟器打开并提示一行信息，直接dismiss掉就好了
3. 重新运行你的app就ok了

## 总结
记录这次遇到的问题，日后再遇到能有效的解决，也希望能帮到有需要的人，共同学习与进步。