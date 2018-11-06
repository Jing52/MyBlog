---
title: IDEA搭建和部署Maven项目
date: 2018-09-28 13:18:30
tags: 
  - Maven
  - Java
categories: Java基础
---
#### 创建Maven项目

<!-- more -->

1. File->New->Project
![第1步](https://upload-images.jianshu.io/upload_images/14481291-b2ce9755f06fe2d3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2. 点击Maven项目，并选择archetype-webapp，然后next
![第2步](https://upload-images.jianshu.io/upload_images/14481291-63f3cd1a32be845e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3.  输入 groupId 和 ArtifactId ，一个是组，一个是项目名称 ，version默认就行，然后next
![第3步](https://upload-images.jianshu.io/upload_images/14481291-f6cfeea4dcfdd197.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
4. 选择maven的根目录、settings.xml文件和本地仓库的位置，根据个人路径配置。添加一个archetypeCatalog=internal的属性。这个参数的意义是让这个maven项目的骨架不要到远程下载而是本地获取。如果你没加这个参数，那么项目创建可能在卡在downloading maven plugins...点击Next
![第4步](https://upload-images.jianshu.io/upload_images/14481291-446ff8ba88bbf4e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
5. 项目名，finish
![第5步](https://upload-images.jianshu.io/upload_images/14481291-f7f40ec8d4858cdd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
6. 查看项目的结构
![项目目录结构](https://upload-images.jianshu.io/upload_images/14481291-97a1b5c207e676b2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
PS:新创建的Maven项目是没有resources文件夹的，可以通过以下方式添加
* File->Project Structure
![one](https://upload-images.jianshu.io/upload_images/14481291-b37c9272b19b162f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 打开Project Structure，选择Modules
![two](https://upload-images.jianshu.io/upload_images/14481291-dcf227b7f1f93b5f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 选择New Folder
![three](https://upload-images.jianshu.io/upload_images/14481291-3e0dad9cccc2e625.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 输入folder name
![four](https://upload-images.jianshu.io/upload_images/14481291-1f3a15873d4fd5af.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 选择Resources文件资源类型,然后apply
![five](https://upload-images.jianshu.io/upload_images/14481291-fc673dd94f2c121a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
7. Terminal终端输入mvn clean install，编译打包成功，显示BUILD SUCCESS字样
![打包](https://upload-images.jianshu.io/upload_images/14481291-1f22318ff1f6b82b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
8. 打包后根目录下出现target目录
![target](https://upload-images.jianshu.io/upload_images/14481291-668a39b024664581.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
9. 部署到Tomcat
![给项目添加Tomcat 服务器](https://upload-images.jianshu.io/upload_images/14481291-ed361eb5e169b42c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
10. 选择local
![选择Tomcat](https://upload-images.jianshu.io/upload_images/14481291-006e2f85e730efed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
11. 修改Name，可以不修改，选择Tomcat、jdk，以及端口。将打包好的war包部署到Tomcat，点击apply
![Server](https://upload-images.jianshu.io/upload_images/14481291-4a087f08e541b67b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![Deployment](https://upload-images.jianshu.io/upload_images/14481291-bbdea2ac31dd6db5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
12. Run运行，浏览器跳出页面，输出Hello World，项目发布成功
![Hello World](https://upload-images.jianshu.io/upload_images/14481291-0e9396c8e15c7209.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




