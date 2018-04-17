---
layout: post
title: "Java的注解、反射、依赖注入、控制反转"
date: 2018-04-17 11:00
description: ""
category: Java
tags: []
---

![Java](/assets/images/2018/Java.svg)

<!-- TOC -->

- [反射](#%E5%8F%8D%E5%B0%84)
- [注解](#%E6%B3%A8%E8%A7%A3)
    - [内建注解](#%08%E5%86%85%E5%BB%BA%E6%B3%A8%E8%A7%A3)
        - [3个标准注解](#3%E4%B8%AA%E6%A0%87%E5%87%86%E6%B3%A8%E8%A7%A3)
        - [4个元注解](#4%E4%B8%AA%E5%85%83%E6%B3%A8%E8%A7%A3)
    - [自定义注解](#%E8%87%AA%E5%AE%9A%E4%B9%89%E6%B3%A8%E8%A7%A3)
        - [定义](#%E5%AE%9A%E4%B9%89)
        - [元素](#%E5%85%83%E7%B4%A0)
    - [自定义注解处理器](#%08%E8%87%AA%E5%AE%9A%E4%B9%89%E6%B3%A8%E8%A7%A3%E5%A4%84%E7%90%86%E5%99%A8)
        - [编译时注解](#%E7%BC%96%E8%AF%91%E6%97%B6%E6%B3%A8%E8%A7%A3)
        - [运行时注解](#%E8%BF%90%E8%A1%8C%E6%97%B6%E6%B3%A8%E8%A7%A3)
- [依赖注入](#%E4%BE%9D%E8%B5%96%E6%B3%A8%E5%85%A5)
- [控制反转](#%E6%8E%A7%E5%88%B6%E5%8F%8D%E8%BD%AC)
- [关系](#%E5%85%B3%E7%B3%BB)
- [参考](#%E5%8F%82%E8%80%83)

<!-- /TOC -->

# 反射

用于运行时修改程序的内容。

[Java Reflection API Spec](https://docs.oracle.com/javase/8/docs/api/java/lang/reflect/package-summary.html):

```Java
java.lang.reflect
```



应用：

- JUnit
- EventBus
- Gson
- Extensibility Features
- Class Browsers and Visual Development Environments
- Debuggers and Test Tools

缺点：

- 性能：使用反射的代码运行性能较低
- 安全限制：需要运行时权限
- 暴露内部数据：如一些private的成员也可以通过反射访问到

# 注解

Annotaion, 也叫metadata，从Java5开始引入。

## 内建注解

### 3个标准注解

```Java
@Overrde
@Deprecated
@SuppressWarnings
```

### 4个元注解

```Java
@Target
@Retention
@Documented
@Inherited
```

## 自定义注解

e.g.

```Java
package com.test.annotation;
import java.lang.annotation.*;

@Target(ElementType.METHOD)
@Retentation(RetentationPolicy.RUNTIME)
public @interface MyAnnotation {
    String desc() default "no desc";
}
```

### 定义

用 @interface 定义，并配合元注解来声明此注解的用途。

### 元素

元素支持的类型

- All primitives: int, float, boolean ...
- String
- Class
- Enums
- Annotations
- Arrays of any of the above

e.g. 以上MyAnnotation注解在使用时传入一个String类型的值:

```Java
public class Test {
    @MyAnnotation("This is a method")
    public void printSomething();
}
```

## 自定义注解处理器

### 编译时注解

基于apt工具，在编译期间处理。

应用：

- ARouter

### 运行时注解

基于Java反射API的扩展，在运行时动态的处理。

应用:

- Retrofit

# 依赖注入

DI -- Dependency Injection.

我的理解就是为了将『变化』隔离出去。

比如在构造对象的时候将该对象依赖的对象传进来，但这样一来，它依赖的对象又由谁来创建呢，以前写OOP代码时，知道隔离变化这样一条规则，所以会封装一层来管理依赖的对象现在可以注解来实现。

# 控制反转

IoC -- Inversion of Control.

在多模块的情况下，为了避免模块间出现严重的耦合，将原来由主模块控制子模块这样的方式改为由第三方模块来控制，对主模块来说，原来由自己控制，现在由第三方控制。

# 关系

控制反转是一种编程思想，依赖注入是一种反映这种思想的设计模式，而依赖注入更具体的实现可以由注解来完成，分为编译时由javac的APT工具来扫描并注入，和运行时由Java反射API动态的注入。

Java5时反射才开始支持操作注解。

# 参考

《Thinking in Java》 Annotations
