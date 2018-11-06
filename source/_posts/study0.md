---
title: 学习笔记——Java技术体系
date: 2018-07-14 00:08:30
tags: 
  - Java
categories: Java基础
---
从广义上讲，Clojure，JRuby，Groovy等运行于java虚拟机上的语言及其相关的程序都属于java技术体系的一员。如果仅从传统意义上来看，Sun官方所定义的java技术体系包括以下几个组成部分：

<!-- more -->


　　·java程序设计语言

　　·各种硬件平台上的java虚拟机

　　·Class文件格式

　　·Java API类库

　　·来自商业机构和开源社区的第三方Java类库

我们可以把Java程序设计语言、Java虚拟机、Java API类库这三个部分统称为JDK（Java Development Kit），JDK是用于支持Java程序开发的最小环境。另外，可以把Java SE API子集和Java虚拟机这两部分统称为JRE（Java Runtime Environment），JRE是支持Java程序运行的标准环境，下图展示了Java技术体系所包含的内容，以及JDK和JRE所涵盖的范围。

![image](http://upload-images.jianshu.io/upload_images/14481291-5c3ea3b78a827b52.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

以上是根据各个组成部分的功能来进行划分的，如果按照技术所服务的领域来划分，或者说按照Java技术关注的重点业务领域来划分，Java技术体系可以分为4个平台，分别为：

　　1、Java Card：支持一些Java小程序（Applets)运行在小内存设备（如智能卡）上的平台

　　2、Java ME（Micro Edition）：支持Java程序运行在移动终端（手机，PDA）上的平台，对Java API有所精简，并加入了针对移动终端的支持，这个版本以前称为J2ME

　　3、Java SE（Standard Edition）：支持面向桌面级应用（如Windows下的应用程序）的Java平台，提供了完整的Java核心API，这个版本以前称为J2SE

　　4、Java EE（Enterprise Edition）：支持使用多层架构的企业应用（如ERP、CRM应用）的Java平台，除了提供Java SE API外，还对其做了大量的扩充并提供了相关的部署支持，在各个版本以前称为J2EE
