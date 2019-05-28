---
title: vue学习
date: 2019-05-28 09:20:46
tags: JS
categories: JS
---

> 记录 Vue 的学习

<!-- more -->

## MVC 与 MVVM 的区别
MVC 是指 Model View Controller（模型-视图-控制器），是一种 Web 架构的模式。
MVVM 是指 Model-View-ViewModel，是一种基于前端开发的架构模式。
在MVC里，View是可以直接访问Model的！从而，View里会包含Model信息，不可避免的还要包括一些业务逻辑。 MVC模型关注的是Model的不变，所以，在MVC模型里，Model不依赖于View，但是 View是依赖于Model的。不仅如此，因为有一些业务逻辑在View里实现了，导致要更改View也是比较困难的，至少那些业务逻辑是无法重用的。
MVVM在概念上是真正将页面与数据逻辑分离的模式，它把数据绑定工作放到一个JS里去实现，而这个JS文件的主要功能是完成数据的绑定，即把model绑定到UI的元素上。