---
layout: post
title: 移动App GUI层架构设计
categories: app
---

<!-- TOC -->

- [架构分类](#%E6%9E%B6%E6%9E%84%E5%88%86%E7%B1%BB)
    - [MVP](#mvp)
- [参考资料](#%E5%8F%82%E8%80%83%E8%B5%84%E6%96%99)

<!-- /TOC -->

# 架构分类

![App Architecture](/assets/images/2018/AppArchitecture.png)

[点击查看大图](https://jiangguo27.github.io/assets/images/2018/AppArchitecture.png)


## MVP

![MVP](https://upload.wikimedia.org/wikipedia/commons/d/dc/Model_View_Presenter_GUI_Design_Pattern.png)

学习MVP可以看这个[例子](https://github.com/googlesamples/android-architecture/tree/todo-mvp/)，提供了一个基本的MVP架构，我画了一下GUI层的类图，方便理解：

![MVP](/assets/images/2018/mvp.svg)

<!--
![Test PUML](http://www.plantuml.com/plantuml/png/JOqxhW8n303xTmguG0pRWAZsAYPhPOrY9_87hWz85A-QAKQQrGCjKlhVaRNst2Yj7_Q8wJS0mrTf77lUqydgq22DKeV0Wr5Rox5S_kclBJn0q8CCq9t2WGKREIodynNaESly3bVIxSCt)
-->

# 参考资料

[选择恐惧症的福音！教你认清MVC，MVP和MVVM](http://zjutkz.net/2016/04/13/%E9%80%89%E6%8B%A9%E6%81%90%E6%83%A7%E7%97%87%E7%9A%84%E7%A6%8F%E9%9F%B3%EF%BC%81%E6%95%99%E4%BD%A0%E8%AE%A4%E6%B8%85MVC%EF%BC%8CMVP%E5%92%8CMVVM/)

[被误解的 MVC 和被神化的 MVVM](https://mp.weixin.qq.com/s?__biz=MjM5NTIyNTUyMQ==&mid=407454565&idx=1&sn=f2c207e30f700219d5811371b34b8cf9&scene=21#wechat_redirect)

[猿题库 iOS 客户端架构设计](https://mp.weixin.qq.com/s?__biz=MjM5NTIyNTUyMQ==&mid=444322139&idx=1&sn=c7bef4d439f46ee539aa76d612023d43&scene=0#wechat_redirect)

[Android Architecture Blueprints](https://github.com/googlesamples/android-architecture)

[Android Architecture Components](https://developer.android.com/topic/libraries/architecture/index.html)

[精通 Android Data Binding](https://github.com/LyndonChin/MasteringAndroidDataBinding)