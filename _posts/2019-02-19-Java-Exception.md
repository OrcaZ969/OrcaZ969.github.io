---
layout:     post
title:      "Java Exception"
subtitle:   
date:       2019-02-19 12:00:00
author:     "Mengxin"
lang:       zh
header-img: 
header-style:text
tags:
    - Java
    - note
---

![img](https://img-my.csdn.net/uploads/201211/27/1354020417_5176.jpg)

 除了RuntimeException及其子类以外，其他的Exception类及其子类都属于可查异常。**这种异常的特点是Java编译器会检查它，也就是说，当程序中可能出现这类异常，要么用try-catch语句捕获它，要么用throws子句声明抛出它，否则编译不会通过。**

运行时异常：RuntimeException及其子类

非运行时异常：除RuntimeException之外的

```java
try {
    // 可能会发生异常的程序代码
} catch (Type1 id1){
    // 捕获并处置try抛出的异常类型Type1
}
catch (Type2 id2){
    //捕获并处置try抛出的异常类型Type2
}
```

运行异常可由系统自动抛出，不一定需要throw语句

try 块：用于捕获异常。其后可接零个或多个catch块，如果没有catch块，则必须跟一个finally块。
catch 块：用于处理try捕获到的异常。
finally 块：无论是否捕获或处理异常，finally块里的语句都会被执行。当在try块或catch块中遇到return语句时，finally语句块将在方法返回之前被执行。在以下4种特殊情况下，finally块不会被执行：

1）在finally语句块中发生了异常。

2）在前面的代码中用了System.exit()退出程序。

3）程序所在的线程死亡

4）cpu关闭



![img](https://img-my.csdn.net/uploads/201211/27/1354022670_6403.jpg)

抛出异常的方法是不会处理异常的，调用方法的方法才应该处理异常