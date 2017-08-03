---
title: 不同PC之间同步管理博客
date: 2017-08-03 16:08:21
tags:
---
主要为了解决自己在mac和windows之间同步管理博客的问题
<!--more-->
> 利用git进行版本控制,实现不同PC之间的同步

### 先在远程仓库中新建一个branch,比如hexo
![新建一个hexo分支](http://i.imgur.com/cn3uRsP.png)
### 接着把hexo分支设置为默认分支
![把hexo分支设置为默认分支](http://i.imgur.com/Rg8SXK3.png)
### 把博客的源文件上传到hexo分支
>提示:如果你的主题(theme)文件是通过`git clone` 下载下来的话,要把主题文件夹里面的`.git`文件夹删除,不然主题无法`push`到远程仓库
   
**`git init`** ***//初始化本地仓库***

**`git add -A`** ***//添加本地所有文件到本地缓存区***-------也可以使用`git add .`

**`git commit -m "bolgSourceFile"`** ***//添加commit说明***

**`git branch hexo`** ***//添加本地仓库分支hexo***-------如果报错:`fatal: A branch named 'hexo' already exists.`则说明该分支已经存在

**`git checkout hexo`** ***//切换到hexo分支***-------如果报错:`Already on 'hexo'Your branch is up-to-date with 'origin/hexo'.`则说明你已经在hexo分支

**`git remote add origin git@github.com:yourname/yourname.github.io.git`** ***//添加远程仓库***-------如果报错:`fatal: remote origin already exists.`则说明远程仓库已经添加过了,有两个选择:1.执行`git remote rm origin`清除远程仓库之后再重新添加;2.啥也不管继续进行下面的操作

**`git push origin hexo -f`** ***//把本地仓库的源文件分支hexo强制推送到远程仓库hexo分支***-------`f`是代表强制

***上传完成:***
![博客源文件上传完成](http://i.imgur.com/8U8OOEm.png)
上传完成之后,我们就拥有了两个远程的分支:master和hexo,其中master使我们部署成博客的分支;hexo是我们可以clone到其他PC的博客源文件的分支.
### 当我们想在其他电脑上更新博客的时候,我们可以把远程仓库hexo分支的博客源文件clone到本地上
>git clone -b hexo git@github.com:yourname/yourname.github.io.git

进入刚刚clone下来的`yourname.github.io`文件夹里面执行`npm install`
### 编辑完本地的blog之后,部署发布博客

依次执行:`git add .`,`git commmit -m "修改的内容"`,`git push origin hexo`,同步到本地仓库分支hexo到远程仓库分支hexo

部署发布博客:`hexo g -d`

### 遇到的问题:

- `gitignore`文件的作用是声明不被git记录的文件,博客根目录下的`.gitignore`是hexo初始化创建的,可以删除或者直接编辑,对hexo不会有影响.`.gitignore`文件默认声明不被git记录的文件如下:
```
node_modules/
public/
.deploy*/
```
1.`.deploy*`是hexo默认的.git配置文件夹,不需要同步
2.`public`内文件是根据source文件夹内容自动生成的,不需要同步,不然每次改动内容太多

参考教程:[搭建hexo博客并简单的实现多终端同步 ](https://righere.github.io/2016/10/10/install-hexo/)
        [利用git解决hexo博客多PC间同步问题 ](http://chitanda.me/2015/06/18/hexo-sync-in-multiple-pc/)












