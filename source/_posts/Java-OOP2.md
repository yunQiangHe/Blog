---
title: Java-OOP2
date: 2019-05-25 21:59:39
categories: java
tags:
description: 疯狂Java讲义第五章
---

### 1.类和对象
* 定义类
```
[修饰符] class 类名
{
    构造器
    成员变量
    成员方法
}
修饰符： public final abstract
```
* 定义构造器
```
[修饰符] 构造器名（形参列表）
{
    //逻辑代码
}
修饰符： public protected private  三选一 
```
* 定义成员变量类型
```
[修饰符] 类型 成员变量名 = [= 默认值];
修饰符： （public  protected private) 三选一 可以与 static final组合修饰成员变量 
```
* 定义成员方法
```
[修饰符] 方法返回值类型 方法名（形参列表）
{
    //逻辑代码
}
修饰符： （public  protected private) 三选一 final和abstract最多只能出现其中之一 可以与 static 组合修饰成员方法

```
* static特殊关键字 static修饰的成员表面它属于这个类本身，而不属于该类的单个实例。因此把static修饰的成员变量成员方法也叫类变量 类方法。不使用static的称为实例变量实例方法。英文直译静态 因此有时候把static修饰的成员变量和方法称为静态变量静态方法。