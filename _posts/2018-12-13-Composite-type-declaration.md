---
layout:     post
title:      "C++复合类型声明"
subtitle:   "引用 指针 const限定符"
date:       2018-12-13 12:00:00
author:     "Mengxin"
lang:	    zh
tags:
    - C++
    - note
---

## 引用

引用必须被初始化，且引用只能绑定在对象上。

```c++
int &ref;//错误：引用必须被初始化
int &ref1=0;//错误：引用必须绑定在对象上而不是字面值或表达式上
```

引用本身不是对象，因此不存在引用的引用，也不存在引用的指针。

## 指针

如果一句话中定义了多个指针，每个变量名前面都要有*

```C++
int *p1,p2;//p1是指针，p2是int
int *p3,*p4;//p3 p4都是指针
```

空指针的生成/判断：

```C++

```

不能用int给指针赋值，哪怕int变量的值为0

```C++
int i=0;
int *p=i;//error
```

void* 指针是一种可以存放任意对象地址的指针，**但我们并不能直接操作所指的对象**

## 引用和指针的区别

- 引用是一个对象的别名，而指针本身就是一个对象

- 引用必须初始化，一旦定义便无法绑定到其他对象上；指针无需在定义时赋值，也可以重新复制让其指向其他对象


## const 限定符

- const对象必须初始化
- **const对象仅在文件内有效**
  - 即：在多个文件中出现同名的const变量，视作独立的变量而不是重复定义
  - 若想共用一个const变量：在定义和声明之前都加上extern

### const的引用

常量引用允许绑定到非常量对象，字面值，表达式上

```c++
const int &r1=0;//OK
int i=1;
const int r2=i;//OK
```

- 引用非常量：可以用常量引用，在此情况下，被引用的量不能通过该引用进行改变，却可以通过其他方式进行改变
- 引用常量：必须使用常量引用

引用是不存在顶层const的，因为它本身就不是一个对象！	

### 指针和const

```C++
const int *p1;//指针指向常量
int const *p2;//指针指向常量
int * const p3=p1;//常量指针
const int * const p=p1;//指向常量的常量指针
```

**常量指针必须初始化**

指向常量的指针和常量的关系：

- 指向非常量：可以用指向常量的指针，在此情况下，被引用的量不能通过该指针进行改变，却可以通过其他方式进行改变

- 指向常量：必须使用指向常量的指针

底层const的拷贝关系：

- 要么两者拥有相同的底层const资格
- 要么被赋值的为底层const，赋值的为非底层const

```C++
int i=0;
const int * p1;
int *p2=&i;
p1=p2//OK
p2=p1//error
```
