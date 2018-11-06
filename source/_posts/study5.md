---
title: 在Windows上安装Maven
date: 2018-09-15 00:21:33
tags: 
  - Maven
  - Java
categories: Java基础
---
一、检查JDK 安装
 

在安装Maven之前首先要确认JDK是否安装。Maven可以运行在JDK1.4及以上的版本。检查JDK版本的方式：

<!-- more -->
 

打开cmd窗口，运行以下命令可以查看Java安装。


![image](http://upload-images.jianshu.io/upload_images/14481291-15e5b1d22730f2a7?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 

二、下载Maven
Maven官网下载地址：http://maven.apache.org/download.html

 

三、本地安装
将下载的zip包解压到指定目录，我的是D:\apache-maven-3.5.2

接着设置环境变量：

1、右击“我的电脑”->“属性”，单机高级系统设置，选择“坏境变量”，在系统变量中新建一个变量M2_HOME，变量值为Maven的安装目录：D:\apache-maven-3.5.2

2、在系统变量中path变量后面添加%M2_HOME%\bin;注意：多个变量之间用英文分号隔开


![image](http://upload-images.jianshu.io/upload_images/14481291-1d3b0835caa3389c?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3、查看Maven安装情况


![image](http://upload-images.jianshu.io/upload_images/14481291-268e01bfa162c4ab?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     