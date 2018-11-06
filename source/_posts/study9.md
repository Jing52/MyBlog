---
title: 学习笔记——Spring MVC接收前端入参数据的方式
date: 2018-08-31 22:13:59
tags: Spring MVC
categories: 开源框架
---
Spring MVC开发中，接收前端参数并解析参数是非常重要的，我总结了如下接收参数的方式：

<!-- more -->

#### 方式一：
普通方式接收

```
  @RequestMapping("/index")
  public String getUserName(String username) {
      System.out.println("username is:"+username);
      return "index";
  }
```
参数写在Controller的方法的形参中，适用于get, post方式提交。参数名必须和前台的一致。

 

#### 方式二：
接收HttpServletRequest
```
  @RequestMapping("/index")
  @ResponseBody
  public String getUserName(HttpServletRequest request) {
       String username = request.getParameter("username");
       return username;
  }
```
可以通过getParameter()获取POST/GET传递的参数值；它用于客户端重定向时，即点击了链接或提交按扭时传值用，即用于在用表单或url重定向传值时接收数据。getParameter只是应用服务器在分析你送上来的request页面的文本时，取得你设在表单或url重定向时的值。

 

#### 方式三：
通过@RequestParam注解
```
  @RequestMapping(value="/index")
  public String getUserName(@RequestParam(value="name",required=false)String username, Model model){
       System.out.println(username);
       model.addAttribute("hello", "这是用action传过来的值："+ username);
       return "index";
  }
``` 

#### 方式四：
通过bean来接收json

```
  @RequestMapping("/index")
  public @ResponseBody User getUserName(@RequestBody User u) {
      System.out.pringln("name: " + u.getName());
  
      User user = new User();
      user.setName(request.getParameter("name"));
  
      return user;
  }
```
 

# 未完待续......