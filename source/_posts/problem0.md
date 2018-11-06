---
title: Method breakpoints may dramatically slow down debugging情况解决
date: 2018-10-10 00:48:30
tags: 
  - Java
categories: Java基础
---
首先给大家看张图

![image](http://upload-images.jianshu.io/upload_images/14481291-e771d3e140a7f072.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


<!-- more -->

这是我最近degubber启动项目时遇到的问题。

### 原因：

根据语义，断点打在了方法上面。

### 引起的问题：

导致项目启动变慢，IDEA调试会越来越慢。

### 解决方法：

Ctrl+shift+F8打开Breakpoints面板，如图

![image](http://upload-images.jianshu.io/upload_images/14481291-94c98d7cd1c962a6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

由此，我们可以清晰看到有一个断点在方法上，我们只要将方法前面的勾去掉就行了
