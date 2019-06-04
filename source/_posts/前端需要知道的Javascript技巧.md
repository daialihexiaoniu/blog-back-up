---
title: 前端需要知道的Javascript技巧
date: 2019-05-31 14:19:52
tags: JS
categories: JS
---

> 前端需要知道的 JavaScript 技巧，会常常补充进来

<!-- more -->

## 判断对象的数据类型
使用 Object.prototype.toString 配合闭包，通过传入不同的判断类型来返回不同的判断函数，一行代码，简洁优雅灵活（注意传入 type 参数时首字母大写）
不推荐将这个函数用来检测可能会产生包装类型的基本数据类型上,因为 call 会将第一个参数进行装箱操作
```
const isType = type => target => `[object ${type}]` === Object.prototype.tpString.call(target)
const isArray = isType('Array)

console.log(isArray([]))

```

## 数组去重
```
const a = [...new Set([1, 2, 3, 3])]
>> [1, 2, 3]
```

## 合并对象
```
const a = {m: 1, n: 2}
const b = {n: 3, x: 5}

cons res = {
    ...a,
    ...b
}

/*
res = {
  m: 1,
  n: 3,
  x: 5
}
*/  
```

## 简单的判断逻辑书写方式
短路求值（Short-Circuit Evaluation）， 三目运算符是一个很方便快捷的书写一些简单的逻辑语句的方式
```
x > 100 ? 'Above 100' : 'Below 100';
x > 100 ? (x > 200 ? 'Above 200' : 'Between 100-200') : 'Below 100';
```
但是有些时候当逻辑复杂之后，三目运算符书写起来可读性也会很难。这个时候，我们就可以使用逻辑与（&&）和逻辑或（||）运算符来改写我们的表达式。

逻辑与和逻辑或操作符总是先计算其做操作数，只有在仅靠左操作数的值无法确定该逻辑表达式的结果时，才会求解其右操作数。这被称为“短路求值（Short-Circuit Evaluation）”

### 工作原理
* 与（&&）运算符将会返回第一个false/‘falsy’的值。当所有的操作数都是true时，将返回最后一个表达式的结果。
```
let one = 1, two = 2, three = 3;
console.log(one && two && three); // Result: 3

console.log(0 && null); // Result: 0
```
* 或（||）运算符将返回第一个true/‘truthy’的值。当所有的操作数都是false时，将返回最后一个表达式的结果。
```
let one = 1, two = 2, three = 3;
console.log(one || two || three); // Result: 1

console.log(0 || null); // Result: null
```