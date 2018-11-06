---
title: String，StringBuilder，StringBuffer的区别
date: 2018-10-31 01:15:34
tags: Java
categories: Java基础
---
## 可变性

首先我们看下String的源码

```
		/** The value is used for character storage. */ 
		private final char value[];  
```

<!-- more -->

由此可以看出，String类中使用final关键字字符数组来保存字符串，所以是不可变的。  

注：在Java中，final关键字可以用来修饰类、方法和变量（包括成员变量和局部变量）

　　1、当用final修饰一个类时，表明这个类不能被继承。也就是说，如果一个类你永远不会让他被继承，就可以用final进行修饰。

　　2、final修饰的方法不能被重写。

　　3、当final修饰一个基本数据类型时，表示该基本数据类型的值一旦在初始化后便不能发生变化；如果final修饰一个引用类型时，则在对其初始化之后便不能再让其指向其他对象了，但该引用所指向的对象的内容是可以发生变化的。

再来看下StringBuilder，StringBuffer的源码

```
   public final class StringBuilder 
             extends AbstractStringBuilder 
             implements java.io.Serializable, CharSequence 
   { 
       ... 
   }
```

```
  public final class StringBuffer 
            extends AbstractStringBuilder 
            implements java.io.Serializable, CharSequence 
  { 
        ... 
   }
```

由源码可以看出，StringBuilder、StringBuffer都继承自AbstractStringBuilder类，我们接下来再看下AbstractStringBuilder类的源码

```
  /**
     * The value is used for character storage. 
     */
    char[] value;
```


由源码可以看出，StringBuilder、StringBuffer在AbstractStringBuilder中也是使用字符数组保存字符串的，但是这两种都是可变的。

## 线程安全性

String中的对象是不可变的，也可以理解为常量，线程安全的。

接下来我们继续看下StringBuffer源码，我在这随机截取了源码中的一些方法

```
   /**
      * @throws StringIndexOutOfBoundsException {@inheritDoc}
      * @since      1.2
      */
     @Override
     public synchronized String substring(int start, int end) {
         return super.substring(start, end);
     }

    /**     
       * @throws StringIndexOutOfBoundsException {@inheritDoc}      
       */     
      @Override     
      public synchronized StringBuffer insert(int offset, Object obj) {                             
          toStringCache = null; 
          super.insert(offset, String.valueOf(obj));         
          return this;     
       }      

    /**      
      * @since      1.4      
      */     
      @Override     
      public int indexOf(String str) {         
          // Note, synchronization achieved via invocations of other                          
          StringBuffer methods   
          return super.indexOf(str);     
      }
```


由源代码可以看出StringBuffer对方法加了同步锁或者对调用的方法加了同步锁，所以是线程安全的。

再来看下StringBuilder源码中的一些方法

```
     @Override
     public StringBuilder append(Object obj) {
         return append(String.valueOf(obj));    
      }
      
     /**
      * @throws StringIndexOutOfBoundsException {@inheritDoc}
      */
     @Override      
      public StringBuilder insert(int index, char[] str, int offset, int len)  { 
          super.insert(index, str, offset, len); 
          return this; 
      } 

     /** 
       * @throws StringIndexOutOfBoundsException {@inheritDoc} 
       */
       @Override 
       public StringBuilder replace(int start, int end, String str) { 
           super.replace(start, end, str); 
           return this; 
       }
```

由源码可以看出，StringBuilder并没有对方法进行加同步锁，所以是非线程安全的。

## 性能

每次对 String 类型进行改变的时候，都会生成一个新的 String 对象，然后将指针指向新的 String 对象。

StringBuffer 每次都会对 StringBuffer 对象本身进行操作，而不是生成新的对象并改变对象引用。

相同情况下使用 StirngBuilder 相比使用 StringBuffer 仅能获得 10%~15% 左右的性能提升，但却要冒多线程不安全的风险。

1、操作少量的数据 ： String

2、单线程操作字符串缓冲区下操作大量数据 ： StringBuilder

3、多线程操作字符串缓冲区下操作大量数据 ： StringBuffer
