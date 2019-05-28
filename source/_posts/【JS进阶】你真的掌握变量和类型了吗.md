---
title: 【JS进阶】你真的掌握变量和类型了吗
date: 2019-05-28 09:29:12
tags: JS
categories: JS
---

> 【JS进阶】你真的掌握变量和类型了吗, [参考地址](https://juejin.im/post/5cec1bcff265da1b8f1aa08f)

<!-- more -->

这篇文章记录了变量和类型的一些内容，我觉得内容还挺好的，在这边分享给大家。

## [JavaScript数据类型](https://juejin.im/post/5cec1bcff265da1b8f1aa08f#heading-1)
### 原始类型
Null：只包含一个值：null
Undefined：只包含一个值：undefined
Boolean：包含两个值：true 和 false
Number：整数或浮点数，还有一些特殊值（-Infinity、+Infinity、NaN）
String：一串表示文本值的字符序列
Symbol：一种实例是唯一且不可改变的数据类型

(在es10中加入了第七种原始类型 BigInt，现已被最新 Chrome 支持)
### 对象类型

Object：除了常用的 Object，Array、Function 等都属于特殊的对象

## [为什么区分原始类型和对象类型](https://juejin.im/post/5cec1bcff265da1b8f1aa08f#heading-2)
### 不可变性
### 引用类型
### 复制
### 比较
### 值传递和引用传递

## [分不清的 Null 和 Undefined](https://juejin.im/post/5cec1bcff265da1b8f1aa08f#heading-8)

## [不太熟的 Symbol 类型](https://juejin.im/post/5cec1bcff265da1b8f1aa08f#heading-9)
### Symbol 的特性
### Symbol 的应用场景

## [不老实的 Number 类型](https://juejin.im/post/5cec1bcff265da1b8f1aa08f#heading-12)
### 精度丢失
### 对结果的分析—更多的问题
### js 对二进制小数的存储方式
### IEEE 754
### js中的toString(2)
### JavaScript能表示的最大数字
### 最大安全数字

## [还有哪些引用类型](https://juejin.im/post/5cec1bcff265da1b8f1aa08f#heading-20)
### 包装类型
### 装箱和拆箱

## [类型转换](https://juejin.im/post/5cec1bcff265da1b8f1aa08f#heading-23)
### 类型转换规则
### if 语句和逻辑语句
### 各种运数学算符
### ==
### 一道有意思的面试题

## [判断 JavaScript 数据类型的方式](https://juejin.im/post/5cec1bcff265da1b8f1aa08f#heading-29)
### typeof
### instanceof
### toString
### jquery
