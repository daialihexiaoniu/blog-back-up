---
title: vue学习
date: 2019-05-29 09:20:46
tags: JS
categories: JS
---

> 记录 Vue 的学习, Vue -渐进式JavaScript框架

<!-- more -->

## MVC 与 MVVM 的区别
MVC 是指 Model View Controller（模型-视图-控制器），是一种 Web 架构的模式。
MVVM 是指 Model-View-ViewModel，是一种基于前端开发的架构模式。
在MVC里，View是可以直接访问Model的！从而，View里会包含Model信息，不可避免的还要包括一些业务逻辑。 MVC模型关注的是Model的不变，所以，在MVC模型里，Model不依赖于View，但是 View是依赖于Model的。不仅如此，因为有一些业务逻辑在View里实现了，导致要更改View也是比较困难的，至少那些业务逻辑是无法重用的。
MVVM在概念上是真正将页面与数据逻辑分离的模式，它把数据绑定工作放到一个JS里去实现，而这个JS文件的主要功能是完成数据的绑定，即把model绑定到UI的元素上。

## Vue 实例
<b>注意点：</b>
1. 需要先在data中声明数据，再使用数据
2. 可以通过 vm.$data 访问到data中的所有属性，或者 vm.msg

## 双向数据绑定
将DOM与Vue实例的data数据绑定到一起，彼此之间相互影响。通过 getter 和 setter 来实现双向绑定

## 动态添加数据的注意点
只有 data 中的数据才是响应式的，动态添加进来的数据默认为非响应式
可以通过以下方式实现动态添加数据的响应式
1. Vue.set(object, key, value) - 适用于添加单个属性
2. Object.assign() - 适用于添加多个属性

## 异步 DOM 更新
* 说明：Vue 异步执行 DOM 更新，监视所有数据改变，一次性更新DOM
* 优势：可以去除重复数据，对于避免不必要的计算和避免重复 DOM 操作上，非常重要
* 如果需要那到更新后 DOM 中的数据，则需要通过 Vue.nextTick(callback)：在DOM更新后，执行某个操作（属于DOM操作） 实例调用 vm.$nextTick(function () {})

## Vue 指令
Vue 指令一般是带有 v- 前缀的特殊属性，当表达式的值改变是，将其产生的连带影响，响应式地作用于 DOM
* v-text: 更新 DOM 对象的 textContent
* v-html: 更新 DOM 对象的 innerHTML
* v-bind: 当表达式的值改变时，将其产生的连带影响，响应式地作用于 DOM
* v-on: 绑定事件， 绑定的事件定义在 methods 中
* 事件修饰符
    * .stop 阻止冒泡，调用 event.stopPropagation()
    * .prevent 阻止默认行为，调用 event.preventDefault()
    * .capture 添加事件侦听器时使用事件捕获模式
    * .self 只当事件在该元素本身（比如不是子元素）触发时，才会触发事件
    * .once 事件只触发一次
* v-model: 在表单元素上创建双向数据绑定，监听用户的输入事件以更新数据
* v-for: 基于源数据多次渲染元素或模板块
* key属性: 使用 v-for 的时候提供 key 属性，以获得性能提升。使用 key，Vue 会基于 key 的变化重新排列元素顺序，并且会移除 key 不存在的元素。

## 样式处理 -class 和 style
使用方式：v-bind:class="expression" or :class="expression"， 表达式的类型：字符串、数组、对象（重点）

* v-if 和 v-show
    * v-if: 根据表达式的值的真假条件，销毁或重建元素
    * v-show: 根据表达式之真假值，切换元素的 display CSS 属性

* 提升性能: v-pre
vue会跳过这个元素和它的子元素的编译过程。可以用来显示原始 Mustache 标签。跳过大量没有指令的节点会加快编译

* 提升性能：v-once
vue只渲染元素和组件一次。随后的重新渲染，元素/组件及其所有的子节点将被视为静态内容并跳过。这可以用于优化更新性能。

## 过滤器 filter
文本数据格式化
* 全局过滤器
通过全局方式创建的过滤器，在任何一个vue实例中都可以使用。使用全局过滤器的时候，需要先创建全局过滤器，再创建Vue实例。显示的内容由过滤器的返回值决定
* 局部过滤器
局部过滤器是在某一个vue实例的内容创建的，只在当前实例中起作用