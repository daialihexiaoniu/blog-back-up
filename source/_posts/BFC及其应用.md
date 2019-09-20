---
title: BFC及其应用
date: 2019-09-20 09:43:21
tags: CSS
categories: CSS
---

本章内容将介绍下 BFC 的相关内容，带领大家去了解什么事 BFC。

<!-- more -->

1. 首先介绍下什么是 BFC？
BFC（Block Formatting Context）块级格式上下文，是页面盒模型布局的一种 CSS 的渲染模式。BFC 可以相当于一个独立的容器，里面的元素与外面的元素互不影响。

2. 如何形成 BFC？
1) 根元素，即 HTML 元素
2) float 的值不为 none 的元素
3) overflow 的值不为 visible 的元素
4) display 的值为 inline-block、table-cell、table-caption 的元素
5) position 的值为 absolute 或 fixed 的元素

3. BFC 的特性及应用
1) 在同一个 BFC 下的两个元素之间的外边距会发生折叠
```
<style>
    div{
        width: 100px;
        height: 100px;
        background: rgb(226, 158, 158);
        margin: 100px;
    }
</style>
<body>
    <div></div>
    <div></div>
</body>
```
![01](./01.png)
效果如图，当两个 div 元素在同一个容器中时，边距会发生重叠，如果要两个边距不发生重叠，我们可以将两个元素放在不同的BFC中。
2) 在 BFC 中，每一个盒子的左外边缘(margin-left)会触碰到容器的左边缘(border-left)(对于从右到左的格式来说，则触碰到右边缘)
3) 形成了 BFC 的区域不会与 float box 重叠，即BFC可以阻止元素被浮动元素覆盖。
4) 计算 BFC 高度时，浮动元素也参与计算

