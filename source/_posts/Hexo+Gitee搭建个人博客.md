---
title: Hexo+Gitee搭建个人博客
tags:
  - Hexo
  - 教程
categories: Hexo
declare: true
cover: https://w.wallhaven.cc/full/kw/wallhaven-kwmood.jpg
top: 2
abbrlink: 8fe2b6a8
---
## 前言
寒假封城，只能呆在家里鼓捣电脑，有一天看到了b站大佬[CodeSheep](https://space.bilibili.com/384068749)的[手把手教你从0开始搭建自己的个人博客 |无坑版视频教程| hexo](https://www.bilibili.com/video/av44544186?t=1173),看了之后着手搭建了属于自己的博客。
视频里博客是搭建在Github上的，但其终究是国外的网站，访问速度得不到保障。推荐使用Gitee，Gitee类似于国内的Github，访问速度没问题。
<!-- more -->

## 环境要求
* Windows系统电脑(Mac用户可以参考上面的视频)
* [Git](https://git-scm.com/)
* [Node.js](https://nodejs.org/en/)

## 安装Git
因为我们要用到[Git](https://git-scm.com/)中的[Git Bash](https://git-scm.com/download/win)，类似于Windows的cmd命令行，不过要好用许多(我开始是用cmd按视频的步骤来的，运行命令容易报错)。
* [下载地址](https://git-scm.com/download/win)
* 安装步骤：双击下载好的exe文件，一路点击next就好了
* 安装完成之后打开Git Bash，输入`git version`查看版本：(我这里安装的版本是2.23.0)
``` 
    $ git version 
    git version 2.23.0.windows.1 
```
* 能看到版本号就说明你安装成功了，之后的命令都是在这里运行的

## 安装Node.js
[Hexo](https://hexo.io/)是基于[Node.js](https://nodejs.org/en/)制作的静态博客，我们要用到Node.js里面的[npm](https://www.npmjs.cn/)(node package manager)包管理器来安装插件，如果你想玩Hexo博客，那么这个Node.js是必装的。

* [下载地址](https://nodejs.org/en/download/)(选择自己电脑版本相对应的包来下载)
* 安装步骤：双击下载好的msi文件，也是一路下一步就好了
* 安装完成后打开Git Bash，输入`node -v`和`npm -v`查看node和npm的版本：
```
    $ node -v
    v12.14.1

    $ npm -v
    6.13.4

```
* 到这里前置步骤就已经算完成了，接下来我们就来安装Hexo博客

## 安装Hexo
安装[Hexo](https://hexo.io/)，我们需要借助[npm](https://www.npmjs.cn/)这个工具来安装，但是我们国内下载镜像源的速度很慢，所以我们可以先利用npm工具来安装一个[cnpm](https://npm.taobao.org/)工具(国内的淘宝npm镜像源)，这样一来速度会快很多。
* 安装cnpm：(安装完之后照样可以用`cnpm -v`来查看版本号验证是否成功)
```
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
```
* 用cnpm安装Hexo
```
$ cnpm install -g hexo-cli
```
* 接着用`Hexo -v`来验证是否安装成功
```
$ hexo -v
hexo-cli: 3.1.0
os: Windows_NT 10.0.17134 win32 x64
node: 12.14.1
```
如果出现以上信息，那么恭喜安装成功了
* 到这里Hexo博客已经算是安装完成了，步骤还是非常简单的，重点是耐心~

## 初始化Hexo
在你的电脑上建一个文件夹，命名没有要求，我这里创建的是blog，文件夹路径也无所谓，最好装在出了系统盘的固态硬盘中，路径要自己找得到。
* 在创建的文件夹目录下右键选择`Git Bash Here`，也就是在此处打开Git Bash终端
* 输入Hexo初始化命令
```
$ hexo init
```
这个命令执行需要一定的时间，请耐心等待
* 初始化完成之后可以查看指定文件夹目录下有：
   * node_modules: 依赖包
   * public：存放生成的页面
   * scaffolds：生成文章的一些模板
   * source：用来存放你的文章
   * themes：主题
   * _config.yml: 博客的配置文件
* 打开Hexo服务
```
$ hexo s
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
```
这样你就可以再浏览器输入:localhost:4000来访问你的博客啦，使用Ctrl+C可以关闭服务。
大概是这样：

![](https://gitee.com/ouwen666/my-image/raw/master/img/blog.jpg)

* 用Hexo写一篇博客
```
$ hexo n "我的第一篇博客"
INFO  Created: E:\bolg\source\_posts\我的第一篇博客.md
```
到E:\bolg\source\_posts目录下打开我的第一篇博客.md进行编辑(推荐用vscode进行编辑，vscode有预览md文件的插件)：
```
---
title: 我的第一篇博客
date: 2020-02-03 21:16:52
tags:
---

## 第一章

内容

---


## 第二章

内容

---

## 参考资料


https://ouwen.gitee.io
```
注意：这里的md文件是基于[markdown](https://baike.baidu.com/item/markdown/3245829?fr=aladdin)语法进行编辑的，不了解的朋友可以百度学习一下，很简单的，几分钟就能看明白，相信你不是问题。

* 编辑完保存文件，重启Hexo服务
```
$ hexo clean          # 清除所有记录 
$ hexo generate       # 生成静态网页 简写：hexo g
$ hexo server         # 启动服务 简写：hexo s
```
打开浏览器输入localhost:4000：

![](https://gitee.com/ouwen666/my-image/raw/master/img/blog2.jpg)

## 将博客部署到Gitee上
上面访问的localhost:4000是本地服务器端口，我们的博客不可能是放在本地服务器的，我们需要把博客部署到远端去。我这里推荐的一个免费的部署的方式就是部署到[Gitee](https://gitee.com/)上，部署好之后就可以通过访问[Gitee](https://gitee.com/)上的那个地址来访问我们的博客。
* 进到[Gitee](https://gitee.com/)官网，注册账号并登陆
* 点击个人主页右上角新建个人仓库

![](https://gitee.com/ouwen666/my-image/raw/master/img/blog3.jpg)

* 创建完成后进入仓库

![](https://gitee.com/ouwen666/my-image/raw/master/img/blog4.jpg)

* 打开Hexo的配置文件`_config.yml`
```
deploy:
  type: git
  repo: https://gitee.com/ouwen666/test.git #仓库的url
  branch: master 
```
* 这里先安装一个Hexo插件
```
cnpm install hexo-deployer-git --save  #通过cpnm安装git插件
git config --global user.email '******@qq.com'  #设置gitee邮箱（gitee的注册邮箱）
git config --global user.name '****'            #设置用户名（gitee的y注册昵称）
hexo d  #上传到gitee的远端仓库
# 在上传时，需要再次输入gitee的用户名username和密码password
```
* 上传成功仓库会多出一些文件

![](https://gitee.com/ouwen666/my-image/raw/master/img/blog5.jpg)

* 接着打开Gitee Page服务

![](https://gitee.com/ouwen666/my-image/raw/master/img/blog6.jpg)

然后点击启动或更新即可。**注意每次更改网页重新上传到仓库都要到这里来更新服务。**

![](https://gitee.com/ouwen666/my-image/raw/master/img/blog7.jpg)

* 访问Gitee Page服务的网站地址

![](https://gitee.com/ouwen666/my-image/raw/master/img/blog8.jpg)

从图中地址栏中的网址可以看出我们已经成功将本地的博客部署到了远端仓库，这样你的小伙伴也能在自己的电脑访问你的Gitee Page服务网站看到你的博客啦。

## 总结
Hexo博客搭建总的来说还是比较简单的，搭配Gitee码云使用起来还是比较方便的，访问速度也还行。总结下面几点：
1. Hexo博客个性化定制的话，大家可以多参考Hexo官方中文文档
2. 更新完代码可以访问localhost:4000预览效果再上传，上传后千万记得更新Gitee Page服务，否则刷新页面会出现没更新的情况
3. Hexo还支持很多主题，有兴趣的小伙伴可以自行搜索更改，参照官方文档进行操作也是不难的哦
4. 小伙伴们注意将自己写的代码保存好哦！我是将代码备份到Github上保存的，将博客部署到Gitee码云进行访问