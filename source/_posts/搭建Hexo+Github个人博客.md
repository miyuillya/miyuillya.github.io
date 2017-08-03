---
title: 搭建hexo博客(windows)
date: 2017-08-02 17:21:03
tags:
---
主要是为了熟悉如何使用hexo+github+域名来创建自己的博客.本文所有命令都是使用**cmder**<!-- more -->
### 简介:
[Hexo](https://hexo.io/zh-cn/)是一个开源的静态博客生成器,是由**台湾大学生tommy351**使用node.js开发的.
[Github](https://github.com)是一个面向开源以及私有软件项目的托管平台
### 准备工作:
- Git
- github
- node
- hexo

**1.安装Git:**
到[Git for windows官网](https://git-for-windows.github.io/)下载Git SCM To Windows
**2.配置github**
注册一个[github](https:github.com)帐号,github的相关配置请参考[Git教程](http://www.runoob.com/git/git-tutorial.html)[git配置](https://cnbin.github.io/blog/2015/05/22/git-pei-zhi/)
**3.安装node.js:**
直接到[node.js官网](http://nodejs.cn/download/)下载安装,还要把node.js的安装路径添加到系统环境变量的PATH里,我使用的是**node_v6.11.2**版本
**4.安装hexo:**
*Node.js*和*Git*都安装好后,可执行以下命令安装hexo:
```
npm install hexo-cli -g
```
会出现一点错误,但是不影响使用
```
npm install hexo --save
```
### 初始化hexo:
新建一个文件夹,这个就是我们本地的hexo目录,然后通过通过命令行进入该文件夹 比如新建myhexo
```
cd myhexo
```
> 也可以点击进入该文件夹,右键打开cmder here,效果相同

```
hexo init
```
安装相关组件:
```
npm install
```
### 生成页面:
**在init的目录下执行**
```
hexo generate//或者 hexo g
```
> 在其他地方执行,虽然不会报错,但是也不能生成

### 本地启动:
```
hexo sever//或者hexo s
```
启动本地服务,并在浏览器打开*http://localhost:4000*便可预览刚刚生成的页面

-------------------------
### 发布到github pages上

> 以下操作默认你已经配置好github和git,也就是添加好ssh key到github上,设置好git的全局用户名和邮箱等

在github上创建一个仓库,名为:`yourname.github.io` 并且开启该仓库的`github pages`,可以在仓库的setting里面找到,按下`choose a theme`
![githubpages](http://i.imgur.com/Izo6dSR.png)

打开本地hexo博客目录里的`_config.yml`文件,并拉到最下面`deploy`那里,并编辑:
```
deploy:
  type: git 
  repo: https://github.com/yourname/yourname.github.io.git
  branch: master
```
因为是使用git的方式部署,所以要执行:
```
npm install hexo-deployer-git -save 
```
> 如果不执行这条命令,有时会报错`ERROR Deployer not found: git`

之后执行以下命令,部署发布:
```
hexo g -d
```
打开*https://yourname.github.io*便可以看见自己刚刚发布的博客.

--------------
### github pages 绑定域名
1.在阿里云,腾云等地方注册一个域名.并且在Dnspod解析,添加A记录如下
![添加A记录](http://i.imgur.com/W0XqCwr.jpg)
> 其中的192.30.252.153是github官网的IP

在本地的hexo博客目录下的`source`文件夹里面创建一个CNAME文件,并写入你的域名如 example.com  不需要www http:// 这样的前缀 
![创建CNAME文件](http://i.imgur.com/MAesxdm.png)
![写入域名](http://i.imgur.com/GdvwuLo.png)
再执行
```
hexo g -d
```
部署发布博客,经过一段时间后,便可通过刚刚注册的域名访问你的博客
> 如果不能通过注册的域名访问博客可以到`setting-github pages`下填写刚刚注册的域名,再重新测试.

![github-pages页面填域名](http://i.imgur.com/Fiu9WHc.png)

---------
### hexo常用命令:
> hexo new post "新建文章" ##简写形式:hexo n "新建文章"
> hexo clean ##清除旧的public文件夹
> hexo generate ##生成静态页面,简写形式:hexo g
> hexo deploy  ##发布到github上,简写形式:hexo d
> hexo sever   ##本地测试博客,简写形式hexo s
> 

---------
### 站点配置文件`_config.yml`的说明
```
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site                //修改以适应搜索引擎的收录
title: hexo           ##网站的标题
subtitle:             ##网站的副标题
description:          ##网站的描述
author:               ##网站的作者
language: zh-Hans     ##网站的语言 
timezone:             ##网站的时区

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yoursite.com   ##网站访问的域名
root: /                    ##所在Web文件夹在哪个目录
permalink: :year/:month/:day/:title/ ##网站的时间格式
permalink_defaults:

# Directory
source_dir: source         ##获取博客资料的文件夹
public_dir: public         ##生成静态网站的文件夹
tag_dir: tags 
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:
  
# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date
  
# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10            ##每一页多少条博客
pagination_dir: page

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next             ##使用的主题

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:                 ##发布的设置
  type: git 
  repo: https://github.com/yourname/yourname.github.io.git
  branch: master
```
参考教程:
[Mac下利用Hexo+GitHub轻松搭建自己的博客](http://blog.csdn.net/jasonjwl/article/details/52887575)



