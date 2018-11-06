---
title: 学习笔记——设计模式：MVC模式
date: 2018-08-04 01:14:43
tags: 
 	- 设计模式
	- Java
categories: Java基础
---
MVC模式全称 Model-View-Controller（模型-视图-控制器） 模式。这种模式用于应用程序的分层开发。

MVC模式的这三个部分的职责非常明确，而且相互分离，因此每个部分都可以独立地改变而不影响其他部分，从而大大提高应用的灵活性和重用性。

<!-- more -->

#### Model（模型）：
指模型表示业务规则。在MVC的三个部件中，模型拥有最多的处理任务。被模型返回的数据是中立的，模型与数据格式无关，这样一个模型能为多个视图提供数据，由于应用于模型的代码只需写一次就可以被多个视图重用，所以减少了代码的重复性。

#### View（视角）：
指用户看到并与之交互的界面。比如由html元素组成的网页界面，或者软件的客户端界面。MVC的好处之一在于它能为应用程序处理很多不同的视图。在视图中其实没有真正的处理发生，它只是作为一种输出数据并允许用户操纵的方式。

#### Controller（控制器）：
指控制器接受用户的输入并调用模型和视图去完成用户的需求，控制器本身不输出任何东西和做任何处理。它只是接收请求并决定调用哪个模型构件去处理请求，然后再确定用哪个视图来显示返回的数据。

 

例子：

步骤一：创建模型StaffModel.java
```
  package com.cxy.model;
  
  /**
   * @author cxy
   * @Description
   * @Date 2018/9/28 下午2:47
   */
  public class StaffModel {
      private String name;
      private String sex;
      private int age;
  
      public String getName() {
          return name;
      }
  
      public void setName(String name) {
          this.name = name;
      }
  
      public String getSex() {
          return sex;
      }
  
      public void setSex(String sex) {
          this.sex = sex;
      }
  
      public int getAge() {
          return age;
      }
  
      public void setAge(int age) {
          this.age = age;
      }
  }
```
 

步骤二：创建视图StaffView.java
```
  package com.cxy.view;
  
  import java.util.logging.Logger;
  
  /**
   * @author cxy
   * @Description
   * @Date 2018/9/28 下午2:52
   */
  public class StaffView {
      public void printStaffInfo(String name,String sex,int age){
          System.out.println("Name:"+name);
          System.out.println("sex:"+sex);
          System.out.println("age:"+age);
      }
  }
```
 

步骤三：创建控制器StaffController.java
```
  package com.cxy.controller;
  
  import com.cxy.model.StaffModel;
  import com.cxy.view.StaffView;
  import jdk.nashorn.internal.objects.annotations.Constructor;
  
  /**
   * @author cxy
   * @Description
   * @Date 2018/9/28 下午2:58
   */
  public class StaffController {
      private StaffModel staffModel;
      private StaffView staffView;
  
      public StaffController(StaffModel staffModel,StaffView staffView){
          this.staffModel = staffModel;
          this.staffView = staffView;
      }
  
      public String getStaffName() {
          return staffModel.getName();
      }
  
      public void setStaffName(String name) {
          staffModel.setName(name);
      }
  
      public String getStaffSex() {
          return staffModel.getSex();
      }
      
      public void setStaffSex(String sex) {
          staffModel.setSex(sex);
      }
  
      public void setStaffAge(int age) {
          staffModel.setAge(age);
      }
  
      public int getStaffAge() {
          return staffModel.getAge();
      }
  
      public void printInfo(){
          staffView.printStaffInfo(staffModel.getName(),staffModel.getSex(), 47        staffModel.getAge());
      }
  }
```
 

步骤四：创建测试类来演示MVC模式的用法StaffTest.java
```
  package com.cxy.test;
  
  import com.cxy.controller.StaffController;
  import com.cxy.model.StaffModel;
  import com.cxy.view.StaffView;
  
  /**
   * @author cxy
   * @Description
   * @Date 2018/9/28 下午3:03
   */
  public class StaffTest {
      public static void main(String[] argc){
          //获取角色数据
          StaffModel staffModel = createRole();
          //创建视图，展示角色信息到控制台
          StaffView staffView = new StaffView();
  
          StaffController staffController = new StaffController(staffModel,staffView);
  
          staffController.printInfo();
          
          //修改角色
          staffController.setStaffName("lyj");
          staffController.setStaffSex("女");
          staffController.setStaffAge(18);
          staffController.printInfo();
      }
  
      public static StaffModel createRole(){
          StaffModel staffModel = new StaffModel();
  
          staffModel.setName("cxy");
          staffModel.setSex("男");
          staffModel.setAge(25);
          return staffModel;
      }
  }
```
 

执行结果：

![image](http://upload-images.jianshu.io/upload_images/14481291-8f9c79e9fe494edd?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)