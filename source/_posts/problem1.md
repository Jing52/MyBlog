---
title: 为什么Java中1000==1000为false而100==100为true
date: 2018-07-02 13:18:30
tags: 
  - Java
categories: Java基础
---
我们首先看下面一段代码

```
Integer a = 1000,b=1000;
System.out.println(a==b);
Integer c = 100,d = 100;
System.out.println(c==d);
```

<!-- more -->

运行结果如下

![image](http://upload-images.jianshu.io/upload_images/14481291-108844abf4e09bee.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

按照我们的理解，如果两个引用指向同一个对象，用==表示它们是相等的。如果两个引用指向不同的对象，==代表不相等的，即使它们的内容相同。

因此，后面一条语句应该也是false。

#### 分析：

我们看下Integer.java类，我们会发现有一个内部私有类，IntegerCache.java，它缓存了从-128~127之间的所有的整数对象。

所以我们在声明类似——

```
Integer c = 100;
```

的时候，它实际上在内部做的是——

```
Integer i = Integer.valueOf(100);
```

我们看下valueOf()方法，可以看到


```
/**
	* Returns an {@code Integer} instance representing the specified 
	* {@code int} value.  If a new {@code Integer} instance is not 
	* required, this method should generally be used in preference to
	* the constructor {@link #Integer(int)}, as this method is likely 
	* to yield significantly better space and time performance by
	* caching frequently requested values.
	*
  * This method will always cache values in the range -128 to 127, 
  * inclusive, and may cache other values outside of this range. 
  * 
  * @param i an {@code int} value. 
  * @return an {@code Integer} instance representing {@code i}. 
  * @since 1.5 
 	*/
  public static Integer valueOf(int i) { 
      if (i >= IntegerCache.low && i <= IntegerCache.high) 
          return IntegerCache.cache[i + (-IntegerCache.low)]; 
      return new Integer(i); 
  }
```


如果值的范围在-128~127之间，它就从高速缓存返回实例。

所以——

```
Integer c = 100,d = 100;
```

指向同一个对象，所以输出才会是true。
