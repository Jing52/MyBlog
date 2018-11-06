---
title: MYSQL limit,offset 区别
date: 2018-10-04 00:30:24
tags: 
  - MYSQL
categories: 数据库
---
##### 首先看下表
![user表](https://upload-images.jianshu.io/upload_images/14481291-7330db7d31a2d3ea.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

<!-- more -->

执行下面SQL
``` 
SELECT
	*
FROM
	`user`
WHERE
	sex = 1 
```
结果
![结果0](https://upload-images.jianshu.io/upload_images/14481291-b602b5ec694254f3.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
再来看下下面的SQL
```
SELECT
	*
FROM
	`user`
WHERE
	sex = 1
LIMIT 2,
 2
```
结果
![结果1](https://upload-images.jianshu.io/upload_images/14481291-b8fa2b408cff271a.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
由此可以看出，limit后面是从第2条开始读，读取2条信息。
最后看下下面的SQL
```
SELECT
	*
FROM
	`user`
WHERE
	sex = 1
LIMIT 2
 OFFSET 1
```
结果
![结果2](https://upload-images.jianshu.io/upload_images/14481291-981149e14541943a.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
由此可知，limit后面跟的是2条数据，offset后面是从第1条开始读取




