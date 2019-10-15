---
title: 换电脑后如何更新blog
author: ycx
avatar: https://wx1.sinaimg.cn/large/006bYVyvgy1ftand2qurdj303c03cdfv.jpg
#authorLink: hojun.cn
authorAbout: 一个好学的人
authorDesc: 一个好学的人
categories: 技术
date: 2019-10-15 13:00:00
comments: true
tags: 
 - 技术
keywords: Sakura
description: 换电脑后如何更新blog
photos: https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1570792027193&di=4c023dc216d41d558ab7617a3dd8455b&imgtype=0&src=http%3A%2F%2Fi1.hdslb.com%2Fbfs%2Farchive%2F52c8218bfad13dd5111221035080f1761dd3625a.jpg
---
更新博客的具体操作及产生问题的解决方案

## Start

### 1.安装git 

[下载地址](https://git-for-windows.github.io/)
安装步骤：双击下载好的exe文件，一直next就好。
安装好后，打开gitbash，查看版本：

``` bash
$ git version
```
![](https://yechengxin.github.io/images/donate/gitversion.png)

### 2.安装NodeJs

[下载地址](https://nodejs.org/en/)(说明：LTS为长期支持版，Current为当前最新版)
安装步骤：下载好msi文件后，双击打开安装，一路next，在Custom Setup这一步选 Add to PATH ,这样就需要自己去配置电脑上环境变量了。
安装好后，打开gitbash，查看版本：

``` bash
$ node -v
```
![](https://yechengxin.github.io/images/donate/node-v.png)

### 3.安装hexo
创建一个文件夹(用于存放blog的所有文件)，然后在该文件夹下gitbash。
安装hexo命令：

``` bash
$ npm install -g hexo-cli
```
查看版本：
``` bash
$ hexo -v
```
![](https://yechengxin.github.io/images/donate/hexo-v.png)

### 4.github添加ssh key
检查本地是否有 SSH key
``` bash
$ cd ~/.ssh
$ ls
```
第一个命令是进入 .ssh 文件夹，第二个是显示 .ssh 文件下的文件夹及文件。
如果 SSH key 存在，就会显示 id_rsa、id_rsa.pub、know_hosts 三个文件 。
![](https://yechengxin.github.io/images/donate/sshkey-ls.webp)

没有就新建一个
设置user.name和user.email配置信息:
``` bash
$ git config --global user.name "你的GitHub用户名"
$ git config --global user.email "你的GitHub注册邮箱"
```
生成ssh密钥文件：
``` bash
$ ssh-keygen -t rsa -C "你的GitHub注册邮箱"
```
然后三个回车
现在找到.ssh的文件夹(通常在C:\Users\Administrator\.ssh)中的id_rsa.pub密钥，将内容全部复制
点击github头像-->settings
![](https://yechengxin.github.io/images/donate/settings.png)
ssh and gpg keys --> new ssh key,title随便取，key就粘贴刚才复制的
输入命令测试：
``` bash
$ ssh -T git@github.com
```
![](https://yechengxin.github.io/images/donate/ssh-t.png)
成功！

### 5.克隆仓库代码
在blog文件夹中gitbash，输入克隆命令:
``` bash
$ git clone -b hexo xxx
```
(克隆一个hexo分支到文件夹中，xxx为仓库地址)

### 6.提交代码
在blog文件夹中gitbash，输入命令:
``` bash
$ git add --all   提交未跟踪、修改和删除文件到暂存区
$ git commit -m '注释'   将暂存区里的改动给提交到本地的版本库
$ git push -u origin 分支名   将本地的分支推送到origin主机，同时指定origin为默认主机   
```

More info: [git命令](https://git-scm.com/docs)

