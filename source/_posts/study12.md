---
title: 上传文件至GitHub
date: 2018-09-22 00:16:34
tags: Git
categories: 工具
---
# Git安装

可查看我之前写过的[博文](https://nullcxy.github.io/2018/06/21/study11/ "Git安装")


<!-- more -->


# 设置[SSH key](https://segmentfault.com/q/1010000000118744)

###### 查看ssh key

可以先查看一下是否已经生成过ssh key
![.ssh key](https://upload-images.jianshu.io/upload_images/14481291-5ccc83fa5d8420cb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
我这边显示已经生成过了，如果没有显示这三个文件，说明没有生成

###### 生成ssh key

```
$ ssh-keygen -t rsa -C "youremail@xxx.com"
```

生成过程中点击Enter键三次，此时在默认路径会生成.ssh文件夹，里面有如图三个文件
![.ssh](https://upload-images.jianshu.io/upload_images/14481291-1531b2c93bab8639.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###### 查看id_rsa.pub

![id_rsa.pub](https://upload-images.jianshu.io/upload_images/14481291-64b5c63f54274828.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 为GitHub账号配置ssh key

###### Settings

点击头像，下拉框中有个Settings设置选项
![Settings](https://upload-images.jianshu.io/upload_images/14481291-ac31896ef036cf75.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###### Personal settings

在Personal settings选择  SSH and GPG keys
![SSH and GPG keys](https://upload-images.jianshu.io/upload_images/14481291-1a47c215ee1f76ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###### New SSH key

点击New SSH key
![New SSH key](https://upload-images.jianshu.io/upload_images/14481291-ca4402db5b53f8e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###### SSH keys/Add new 
![Add new](https://upload-images.jianshu.io/upload_images/14481291-8f9f9800bc31e199.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###### Add后

![key](https://upload-images.jianshu.io/upload_images/14481291-6db142c4058ae462.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 创建本地仓库

###### 创建
```
mkdir test

cd f:test
```
![test](https://upload-images.jianshu.io/upload_images/14481291-b2286c20f5cc462e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###### 初始化本地仓库
```
git init
```
![init](https://upload-images.jianshu.io/upload_images/14481291-36577c6f8c82f98d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
初始化后会出现.git文件夹，如图
![.git](https://upload-images.jianshu.io/upload_images/14481291-acd8743e1d50a1cf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
如果没有，是被隐藏了，工具->文件夹选项->查看，选择“显示隐藏的文件、文件夹和驱动器”

###### 添加
将所有文件添加到仓库
```
git add .
```

##### 提交
提交，双引号内是提交注释
```
git commit -m 'first'
```
![commit](https://upload-images.jianshu.io/upload_images/14481291-e601b8e0cf7daeae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
显示已经提交一个文件

# 连接GitHub

###### 创建一个新的仓库

1. 登录GitHub账号，没有可以申请一个。点击右上角“+”，选择创建一个仓库
![ new repository](https://upload-images.jianshu.io/upload_images/14481291-381b4ac711626171.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 定义Repository name，点击创建
![repository](https://upload-images.jianshu.io/upload_images/14481291-59cdd735c2ba1880.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. 创建完之后的仓库
![first repository](https://upload-images.jianshu.io/upload_images/14481291-bc9da1605978ec7f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###### 连接GitHub
```
git remote add origin https://github.com/nullcxy/First-Repository.git
```
![git地址](https://upload-images.jianshu.io/upload_images/14481291-ae1b7c36111e93a9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###### 将文件推送到远程仓库
```
$ git push -u origin master
```
刚开始的时候远程仓库是空的，所以需要加上“-u”这个参数，下次再push就不需要了，如下即可
```
$ git push origin master
```
![push](https://upload-images.jianshu.io/upload_images/14481291-5496d60448fd506b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
推送到远程仓库成功
<br>
看一下远程仓库
<br>
![success](https://upload-images.jianshu.io/upload_images/14481291-eb891eb3a8745a2e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

