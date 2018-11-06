---
title: freemarker判断对象是否为空
date: 2018-10-01 12:24:30
tags: 
  - freemarker
categories: 前端
---
一、freemarker中显示某对象使用${object}

例：

` <input class="easyui-textbox" id="" value="${TOPIC_NAME}">`

<!-- more -->
 

二、如果对象出现null值，freemarker就会报错，可以通过判断来对象是否为空

```
1 <#if object??>
2 
3    ......
4 
5     <#else>
6 
7    ......
8 
9 </#if>
```
 

也可以通过设置默认值${object!""}，如果object为null，页面就会显示”“

`<input class="easyui-textbox" id="" value=${TOPIC_NAME!"如果TOPIC_NAME为null，显示"}>`
 

三、如果对象导航为null，可以通过${(map.name)!"如果map为null或者name为null，显示"}

``` 
 <#--加上括号，感叹号解决对象导航为空的问题-->
 <input class="easyui-textbox" id="" value=${(map.name)!"map为null或者name为null"}>
```
 

四、总结

！可以解决null

！可以解决未定义的问题

！和（）可以解决对象导航的问题