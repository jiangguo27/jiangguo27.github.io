---
layout: post
title: 移动 App GUI 层架构设计
categories: app
---

<!-- TOC -->

- [GUI层架构分类](#gui%E5%B1%82%E6%9E%B6%E6%9E%84%E5%88%86%E7%B1%BB)
    - [MVC](#mvc)
    - [MVP](#mvp)
- [模块化](#%E6%A8%A1%E5%9D%97%E5%8C%96)
- [参考资料](#%E5%8F%82%E8%80%83%E8%B5%84%E6%96%99)

<!-- /TOC -->

# GUI层架构分类

![App Architecture](/assets/images/2018/AppArchitecture.svg)
[点击查看大图](https://jiangguo27.github.io/assets/images/2018/AppArchitecture.svg)

## MVC

刚开始写Android App时，习惯将很多的东西放到Activity里边，有GUI操作逻辑，有业务逻辑，
这样Activity即充当了Controller，又当了View，耦合比较重；
在写iOS App时，iOS内建的MVC架构，也面临同样的境地，一开始都习惯把很多的东西放到ViewController中去。

## MVP

![MVP](https://upload.wikimedia.org/wikipedia/commons/d/dc/Model_View_Presenter_GUI_Design_Pattern.png)

学习MVP可以看这个[例子](https://github.com/googlesamples/android-architecture/tree/todo-mvp/)，提供了一个基本的MVP架构，我画了一下GUI层的类图，方便理解：

![MVP](/assets/images/2018/mvp.svg)

<!--
![Test PUML](http://www.plantuml.com/plantuml/png/JOqxhW8n303xTmguG0pRWAZsAYPhPOrY9_87hWz85A-QAKQQrGCjKlhVaRNst2Yj7_Q8wJS0mrTf77lUqydgq22DKeV0Wr5Rox5S_kclBJn0q8CCq9t2WGKREIodynNaESly3bVIxSCt)
-->

# 模块化

这里讨论的不是Android的插件化，也不是iOS的动态化，只是将工程拆分成不同模块来降低维护难度。

Android中实现模块化可以利用Android Library或者Java Library来实现, 将业务能用的东西抽象到一个Jar包中供上层模块使用；
Android Library则可以加上一些资源文件，简单配置就可以成为一个独立的app来跑。

iOS则可以利用Cocoa Touch Framework或者Cocoa Touch Static Library来实现模块物理上的拆分。

# 参考资料

[选择恐惧症的福音！教你认清MVC，MVP和MVVM](http://zjutkz.net/2016/04/13/%E9%80%89%E6%8B%A9%E6%81%90%E6%83%A7%E7%97%87%E7%9A%84%E7%A6%8F%E9%9F%B3%EF%BC%81%E6%95%99%E4%BD%A0%E8%AE%A4%E6%B8%85MVC%EF%BC%8CMVP%E5%92%8CMVVM/)

[被误解的 MVC 和被神化的 MVVM](https://mp.weixin.qq.com/s?__biz=MjM5NTIyNTUyMQ==&mid=407454565&idx=1&sn=f2c207e30f700219d5811371b34b8cf9&scene=21#wechat_redirect)

[猿题库 iOS 客户端架构设计](https://mp.weixin.qq.com/s?__biz=MjM5NTIyNTUyMQ==&mid=444322139&idx=1&sn=c7bef4d439f46ee539aa76d612023d43&scene=0#wechat_redirect)

[Android Architecture Blueprints](https://github.com/googlesamples/android-architecture)

[Android Architecture Components](https://developer.android.com/topic/libraries/architecture/index.html)

[精通 Android Data Binding](https://github.com/LyndonChin/MasteringAndroidDataBinding)
