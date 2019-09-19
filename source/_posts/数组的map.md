---
title: 数组的 map、filter、sort 和 reduce 的用法
date: 2018-08-01 11:54:05
tags: js知识
categories: JS
---

> 本文文章来讲述一下关于map、filter、sort 和 reduce 的用法，如果有错误的地方欢迎下伙伴来指正、

<!-- more -->

# 基本概念

1. map 遍历数组返回一个新的数组，返回的是加工之后的值。
2. filter 遍历过滤出一个新的子数组， 返回条件为true的值。
3. sort 数组排序。
4. reduce 方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。
    reduce() 可以作为一个高阶函数，用于函数的 compose。
    reduce() 对于空数组是不会执行对调函数的。

# 通过一些题目来更加熟悉这些东西吧~
## 题目
这个题目是网上获取的，可以再浏览器控制台打印结果。这边给出两个数组
* 第一个数组
```
const inventors = [
    { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
    { first: 'wawa', last: 'fs', year: 1830, passed: 1905 },
    { first: 'grvd', last: 'xcvxcv', year:1900, passed: 1977 },
    { first: 'Hanna', last: 'Hammarström', year: 1829, passed: 1909 }
];
```
* 第二个数组
```
['Albert, Einstein', 'wawa, fs', 'grvd, xcvxcv', 'Hanna, Hammarström']
```

**题目如下：**
* 筛选出生于1800-1900的发明家；
* 以数组形式，列出其名与姓；
* 根据其出生日期，并从大到小排序；
* 计算所有的发明家加起来一共活了几岁；

## 解决方法
* 第一个问题：筛选出生于1800-1900的人。
  这边因为是筛选，可以用 filter 方法。
  **注意**：filter 不会对空数组进行检测
  **注意**：filter 不会改变原始数组
  ```
  funtction born(inventor) {
      return inventor.year >= 1800 && inventor.year < 1900;
  }
  var person = inventors.filter(born); // filter 参数是一个函数，做筛选用。
  console.log(person);
  // 简化的写法
  var person = inventors.filter(inventor => (inventor.year >= 1800 && inventor.year < 1900));
  ```

* 第二个问题：以数组形式，列出其名与姓。
  以数组形式返回，可以对原数组进行处理，这边用 map 方法。
  **注意**：map 不会对空数组进行检测
  **注意**：map 不会改变原始数组
  ```
   const fullnames = inventors.map(inventor => `${inventor.first} ${inventor.last}`);
   console.log(fullnames);
  ```
* 第三个问题：根据其出生日期，并从大到小排序。
  按照出生日期进行排序，采用 sort 方法。
  ```
   const birthdate = inventors.sort((inventora, inventorb) => (inventorb.year - inventora.year));
   console.log(birthdate)
  ```
* 第四个问题：计算所有的发明家加起来一共活了几岁。
  计算总过获得岁数，采用 reduce 方法
  ```
  const totalyears = inventors.reduce(
      (total, inventor) => { return total + (inventor.passed - inventor.year); }, 0
      );
  console.log(totalyears);
  ```

