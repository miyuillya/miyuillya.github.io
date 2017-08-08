---
title: chocolatey and cmder
date: 2017-08-05 18:44:49
tags: windows
---
本文记录chocolatey 和cmder的安装过程和注意事项<!--more-->

### 1.Chocolatey软件包管理系统

#### 下载安装

安装Chocolatey可以到[官网](https://chocolatey.org/install)找安装教程,很简单.就是**用管理员模式打开命令行提示符,复制官网里面一段命令到命令行提示符里**即可自动安装.(安装命令会变动,以[官网](https://chocolatey.org/install)的为准)

我的安装过程:

`复制CHOCOLATEY官网安装命令:`
![复制chocolatey官网命令](http://i.imgur.com/W9Qw6CY.jpg)
`粘帖到命令行提示符中,自动安装:`
![粘帖到命令行提示符中,自动安装](http://i.imgur.com/DC6NNNX.jpg)

#### 相关命令

**`clist 软件名`**----  查询数据库中的程序

**`cinst 软件名`**----  安装程序

### 2.Cmder

#### 下载解压

cmder是一个把conemu,msysgit和clink打包在一起,让你无需配置就能使用一个干净的Linux终端!甚至还附带漂亮的monoka配色主题.

安装cmder可以到[官网](http://cmder.net/)下载mini版与full版(区别是:**mini版没有内建的msysgit工具,而full版有**.full版还可以使用大量的linux命令;比如:grep curl等)

`下载解压完后的cmder:`

![下载解压完后的cmder](http://i.imgur.com/Y6L1Jes.png)

#### 配置cmder

##### 启动

因为是即压即用的存在,所以解压完后点击`Cmder.exe`即可运行,但是这般打开它,不怎么方便.所以我们可以这样做:

1.把cmder添加到系统环境变量:可以把`Cmder.exe`存放的目录添加到系统环境变量,添加完之后,`win+r` 输入`cmder`即可.

`添加到环境变量:`  
![把cmder添加到系统环境变量](http://i.imgur.com/RGQVUgw.jpg)
![通过win+r运行cmder](http://i.imgur.com/ZV0Zjw7.png)

2.添加cmder到右键菜单:打开一个管理员权限终端输入以下语句即可:

    Cmder.exe /REGISTER ALL
<!--  -->
`添加到右键菜单:`
![打开一个管理员权限终端](http://i.imgur.com/310L8Px.jpg)
![输入命令](http://i.imgur.com/caQyDXC.png)
![右键菜单有cmder](http://i.imgur.com/5XAlzrT.jpg)

不用打开文件夹就能打开Cmder,并进入该目录;爽
