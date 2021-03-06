---
title: vue学习
date: 2019-05-29 09:20:46
tags: vue
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

## 按键值修饰符
在监听键盘事件时，Vue 允许为 v-on 在监听键盘事件时添加关键修饰符。例如@keyup.13="submit"

## 监视数据变化 - watch
watch是一个对象，键是需要观察的表达式，值是对应回调函数，当表达式的值发生变化后，会调用对应的回调函数完成响应的监视操作

## 实例生命周期
所有的 Vue 组件都是 Vue 实例，并且接受相同的选项对象即可 (一些根实例特有的选项除外)。
实例生命周期也叫做：组件生命周期

### 生命周期介绍
一个组件从开始到最后消亡所经历的各种状态，就是一个组件的生命周期
生命周期钩子函数的定义：从组件被创建，到组件挂载到页面上运行，再到页面关闭组件被卸载，这三个阶段总是伴随着组件各种各样的事件，这些事件，统称为组件的生命周期函数！
注意：
* Vue在执行过程中会自动调用生命周期钩子函数，我们只需要提供这些钩子函数即可
* 钩子函数的名称都是Vue中规定好的！

### 钩子函数 - beforeCreate()
在实例初始化之后，数据观测 (data observer) 和 event/watcher 事件配置之前被调用
注意：此时，无法获取 data中的数据、methods中的方法

### 钩子函数 - created()
注意：这是一个常用的生命周期，可以调用methods中的方法、改变data中的数据 [参考资料1](https://segmentfault.com/a/1190000008879966) [参考资料2](https://segmentfault.com/a/1190000008010666)

### 钩子函数 - beforeMounted()
在挂载开始之前被调用

### 钩子函数 - mounted()
此时，vue实例已经挂载到页面中，可以获取到el中的DOM元素，进行DOM操作

### 钩子函数 - beforeUpdated()
数据更新时调用，发生在虚拟 DOM 重新渲染和打补丁之前。你可以在这个钩子中进一步地更改状态，这不会触发附加的重渲染过程。
注意：此处获取的数据是更新后的数据，但是获取页面中的DOM元素是更新之前的

### 钩子函数 - updated()
组件 DOM 已经更新，所以你现在可以执行依赖于 DOM 的操作。

### 钩子函数 - beforeDestroy()
实例销毁之前调用。在这一步，实例仍然完全可用。
使用场景：实例销毁之前，执行清理任务，比如：清除定时器等

### 钩子函数 - destroyed()
Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。

## axios
* Promise based HTTP client for the browser and node.js
    * 以Promise为基础的HTTP客户端，适用于：浏览器和node.js
    * 封装ajax，用来发送请求，异步获取数据
* 安装：npm i -S axios
* 拦截器：拦截器会拦截发送的每一个请求，请求发送之前执行request中的函数，请求发送完成之后执行response中的函数

## 自定义组件
* 作用：进行DOM操作
* 使用场景：对纯 DOM 元素进行底层操作，比如：文本框获得焦点
* 两种指令：1 全局指令 2 局部指令

## 组件
> 组件系统是 Vue 的另一个重要概念，因为它是一种抽象，允许我们使用小型、独立和通常可复用的组件构建大型应用。仔细想想，几乎任意类型的应用界面都可以抽象为一个组件树

创建组件的两种方式：1 全局组件 2 局部组件

### 全局组件
* 说明：全局组件在所有的vue实例中都可以使用
* 注意：先注册组件，再初始化根实例
* extend：使用基础 Vue 构造器，创建一个“子类”。参数是一个包含组件选项的对象。

### 局部组件
局部组件，是在某一个具体的vue实例中定义的，只能在这个vue实例中使用

### is特性
> 在某些特定的标签中只能存在指定表恰 如ul > li 如果要浏览器正常解析则需要使用is

## 组件通讯
### 父组件到子组件
通过子组件props属性来传递数据 props是一个数组, 传递过来的props属性的用法与data属性的用法相同
注意：属性的值必须在组件中通过props属性显示指定，否则，不会生效

### 子组件到父组件
父组件给子组件传递一个函数，由子组件调用这个函数。借助vue中的自定义事件（v-on:cunstomFn="fn"）
步骤：
1. 在父组件中定义方法 parentFn
2. 在子组件 组件引入标签 中绑定自定义事件 v-on:自定义事件名="父组件中的方法" ==> @pfn="parentFn"
3. 子组件中通过$emit()触发自定义事件事件 this.$emit(pfn,参数列表。。。)

### 非父子组件通讯
> 在简单的场景下，可以使用一个空的 Vue 实例作为事件总线
$on()：绑定自定义事件

### 内容分发
通过<slot></slot> 标签指定内容展示区域

### 获取组件（或元素） - refs
vm.$refs 一个对象，持有已注册过 ref 的所有子组件（或HTML元素）.在 HTML元素 中，添加ref属性，然后在JS中通过vm.$refs.属性来获取
注意：如果获取的是一个子组件，那么通过ref就能获取到子组件中的data和methods

## SPA -单页应用程序
### SPA： Single Page Application
> 单页Web应用（single page application，SPA），就是只有一个Web页面的应用，是加载单个HTML页面，并在用户与应用程序交互时动态更新该页面的Web应用程序。

* 单页面应用程序：只有第一次会加载页面, 以后的每次请求, 仅仅是获取必要的数据.然后, 由页面中js解析获取的数据, 展示在页面中
* 传统多页面应用程序：对于传统的多页面应用程序来说, 每次请求服务器返回的都是一个完整的页面
优势:
* 减少了请求体积，加快页面响应速度，降低了对服务器的压力
* 更好的用户体验，让用户在web app感受native app的流畅
实现思路和技术点
1. ajax
2. 锚点的使用（window.location.hash #）
3. hashchange 事件 window.addEventListener("hashchange",function () {})
4. 监听锚点值变化的事件，根据不同的锚点值，请求相应的数据
5. 原本用作页面内部进行跳转，定位并展示相应的内容

### 路由
路由即：浏览器中的哈希值（# hash）与展示视图内容（template）之间的对应规则
vue中的路由是：hash 和 component的对应关系,在 Web app 中，通过一个页面来展示和管理整个应用的功能。SPA往往是功能复杂的应用，为了有效管理所有视图内容，前端路由 应运而生！简单来说，路由就是一套映射规则（一对一的对应规则），由开发人员制定规则。当URL中的哈希值（# hash）发生改变后，路由会根据制定好的规则，展示对应的视图内容
基本使用 安装：npm i -S vue-router
重定向 { path: '/', redirect: '/home' }
路由其他配置 
* 路由导航高亮 当前匹配的导航链接，会自动添加router-link-exact-active router-link-active类
* 匹配路由模式 配置：mode
路由参数
* 说明：我们经常需要把某种模式匹配到的所有路由，全都映射到同一个组件，此时，可以通过路由参数来处理
* 语法：/user/:id
* 使用：当匹配到一个路由时，参数值会被设置到 this.$route.params
* 其他：可以通过 $route.query 获取到 URL 中的查询参数 等
嵌套路由 - 子路由
* 路由是可以嵌套的，即：路由中又包含子路由
* 规则：父组件中包含 router-view，在路由规则中使用 children 配置

## 前端模块化
为什么需要模块化?
1. 最开始的js就是为了实现客户端验证以及一些简单的效果
2. 后来，js得到重视，应用越来越广泛，前端开发的复杂度越来越高
3. 旧版本的js中没有提供与模块（module）相关的内容
### 模块的概念
* 在js中，一个模块就是实现特定功能的文件（js文件）
* 遵循模块的机制，想要什么功能就加载什么模块
* 模块化开发需要遵循规范

### 模块化解决的问题
1. 命名冲突
2. 文件依赖（加载文件）
3. 模块的复用
4. 统一规范和开发方式

### JS实现模块化的规范
AMD 的使用
> Asynchronous Module Definition：异步模块定义，浏览器端模块开发的规范 代表：require.js 特点：模块被异步加载，模块加载不影响后面语句的运行

1. 定义模块
```
    // 语法:define(name, dependencies?, factory);
    // name表示：当前模块的名称，是一个字符串 可有可无
    // dependencies表示：当前模块的依赖项，是一个数组无论依赖一项还是多项 无则不写
    // factory表示：当前模块要完成的一些功能，是一个函数
    
    // 定义对象模块
    define({})
    // 定义方法模块
    define(function() {
      return {}
    })
    // 定义带有依赖项的模块
    define(['js/a'], function() {})
```

2. 加载模块
```
    // - 注意：require的第一个参数必须是数组

    // 参数必须是数组 表示模块路径 以当前文件为基准,通过回调函数中的参数获取加载模块中的变量 参数与模块按照顺序一一对应
    require(['a', 'js/b'], function(a, b) {
      // 使用模块a 和 模块b 中的代码
    })
```

3. 路径查找配置
    * requirejs 默认使用 baseUrl+paths 的路径解析方式
    * 可以使用以下方式避开此设置：1 以.js结尾 2 以 / 开始 3 包含协议：https:// 或 http://
```
    // 配置示例
    // 注意配置应当在使用之前
    require.config({
      baseUrl: './js' // 配置基础路径为：当前目录下的js目录
    })
    require(['a'])    // 查找 基础路径下的 ./js/a.js

    // 简化加载模块路径
    require.config({
      baseUrl: './js',
      // 配置一次即可，直接通过路径名称（template || jquery）加载模块
      paths: {
        template: 'assets/artTemplate/template-native',
        jquery: 'assets/jquery/jquery.min'
      }
    })
    // 加载jquery template模块
    require(['jquery', 'template'])
```

4. 非模块化和依赖项支持
    * 添加模块的依赖模块，保证加载顺序（deps）
    * 将非模块化模块，转化为模块化（exports）
```
    // 示例
    require.config({
      baseUrl: './js',
      paths: {
        // 配置路径
        noModule: 'assets/demo/noModule'
      },
      // 配置不符合规范的模块项
      shim: {
        // 模块名称
        noModule: {
          deps: [],         // 依赖项
          exports: 'sayHi'  // 导出模块中存在的函数或变量
        }
      }
    });

    // 注意点  如果定义模块的时候，指定了模块名称，需要使用该名称来引用模块
    // 定义 这个模块名称与paths中的名称相同
    define('moduleA', function() {})
    // 导入
    require.config({
      paths: {
        // 此处的模块名：moduleA
        moduleA: 'assets/demo/moduleA'
      }
    })
```

5. 路径加载规则
路径配置的优先级：1 通过 config 配置规则查找 2 通过 data-main 指定的路径查找 3 以引入 requirejs 的页面所在路径为准查找
```
    <!-- 
      设置data-main属性
      1 data-main属性指定的文件也会同时被加载
      2 用于指定查找其他模块的基础路径
    -->
    <script src="js/require.js" data-main="js/main"></script>
```