---
title: 学习笔记——浏览器对象模型（Window）
date: 2018-06-25 02:02:30
tags: 
  - HTML
categories: 前端
---
## Window 对象

所有浏览器都支持 window 对象。它表示浏览器窗口。

<!-- more -->

所有 JavaScript 全局对象、函数以及变量均自动成为 window 对象的成员。

全局变量是 window 对象的属性。

全局函数是 window 对象的方法。

甚至 HTML DOM 的 document 也是 window 对象的属性之一：

```
window.document.getElementById("header");
```

等同于

```
document.getElementById("header");
```

## Window 尺寸

有三种方法能够确定浏览器窗口的尺寸（浏览器的视口，不包括工具栏和滚动条）。

对于Internet Explorer、Chrome、Firefox、Opera 以及 Safari：

*   window.innerHeight - 浏览器窗口的内部高度
*   window.innerWidth - 浏览器窗口的内部宽度

对于 Internet Explorer 8、7、6、5：

*   document.documentElement.clientHeight
*   document.documentElement.clientWidth

或者

*   document.body.clientHeight
*   document.body.clientWidth

实用的 JavaScript 方案（涵盖所有浏览器）：

### 实例：

```
 <!DOCTYPE html>
  <html>
  <body>
  
  <p id="demo"></p>
  
  <script>
  var w=window.innerWidth
  || document.documentElement.clientWidth 10 || document.body.clientWidth; 11 
  var h=window.innerHeight 13 || document.documentElement.clientHeight 14 || document.body.clientHeight; 15 
  x=document.getElementById("demo"); 17 x.innerHTML="浏览器的内部窗口宽度：" + w + "，高度：" + h + "。"
  </script>
  
  </body>
  </html>
```


### 结果：

```
浏览器的内部窗口宽度：705，高度：400。
```

## 其他 Window 方法

一些其他方法：

*   window.open() - 打开新窗口
*   window.close() - 关闭当前窗口
*   window.moveTo() - 移动当前窗口
*   window.resizeTo() - 调整当前窗口的尺寸

### jQuery.isWindow()方法：判断传入的参数是否为 window对象


```
  <!DOCTYPE html>
  <html>
  <head>
  <meta charset="utf-8">
  <title>菜鸟教程(runoob.com)</title>    
  <script src="../jquery/1.10.2/jquery.min.js"></script>
  </head>
  <body>
  
  window 是一个窗口吗? <b></b>
  <script>
  $(function () { 13     $("b").append( "" + $.isWindow(window) ); 14 }) 15 </script>
   
  </body>
  </html>
```


### 结果：

```
window 是一个窗口吗? true
```

### 语法：

```
$.isWindow( object )
```

*object：任意类型，需要进行判断的任意值。*
