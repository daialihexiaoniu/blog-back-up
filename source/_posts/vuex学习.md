---
title: vuex学习
date: 2019-09-30 09:13:15
tags: vue
categories: JS
---

Vuex 学习
<!-- more -->

## 什么是 Vuex？

Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。

“单向数据流” 示意图如下：
![单向数据流示意图](./flow.png)
* state：驱动应用的数据源
* view：以声明方式将 state 映射到视图
* actions：响应在 view 上的用户输入导致的状态变化

Vuex 的基本思想是通过定义和隔离状态管理中的各种概念并通过强制规则维持视图和状态间的独立性，使我们的代码变得更结构化且易维护。

Vuex 示意图如下：
![vuex](./vuex.png)

## 什么情况下我应该使用 Vuex？
如果应用足够简单，不需要开发大型单页应用，则不需要使用Vuex。
如果打算构建一个中大型单页应用，则需要考虑如何更好地在组件外部管理状态，这时，Vuex将是一个很好的选择。

## 核心 Store
每一个 Vuex 应用的核心就是 Store（仓库）。“Store”基本上就是一个容器，它包含着你的应用中大部分的状态 (state)。

Vuex 和单纯的全局对象有以下两点不同：
1. Vuex 的状态存储是响应式的。当 Vue 组件从 store 中读取状态的时候，若 store 中的状态发生变化，那么相应的组件也会相应地得到高效更新。
2. 你不能直接改变 store 中的状态。改变 store 中的状态的唯一途径就是显式地提交 (commit) mutation。这样使得我们可以方便地跟踪每一个状态的变化，从而让我们能够实现一些工具帮助我们更好地了解我们的应用。

## 最简单的 Store
```
// 如果在模块化构建系统中，请确保在开头调用了 Vue.use(Vuex)
const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  }
})
store.commit('increment')
console.log(store.state.count) // -> 1
```

# State
## 单一状态树
Vuex 使用**单一状态树**，用一个对象包含全部应用层级状态。每个应用仅仅包含一个 store 实例。单一状态树让我们能够直接地定位任一特定的状态片段，在调试的过程中也能轻易地取得整个当前应用状态的快照。