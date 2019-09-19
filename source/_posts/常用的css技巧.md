---
title: 常用的css技巧
date: 2019-08-21 16:43:02
tags: CSS
categories: CSS
---
日常中可能会遇到各种各样的css问题， 常见的一些比如垂直居中，图片居中，清除浮动，按钮样式，滚动条自定义等，这边整理一些可能会比较常用的技巧，希望大家能够喜欢。
<!-- more -->

1. 清除浮动
   文档元素浮动情况下，会出现各种问题，这时候需要清除浮动： 

```
.clearfix:after {
     content: "."; 
     display: block;
     clear: both;
     visibility: hidden;
     line-height: 0;
     height: 0; 
}
.clearfix { display: inline-block; }
html[xmlns] .clearfix { display: block; }
* html .clearfix { height: 1%; }
```

2. 文本省略显示...
   文本超过一定宽度时，需要显示省略号。
   单行省略（需要设置外层宽度）： 

```
.text-overflow {
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden；
}
```
  多行省略（css多行省略在chrome生效需要设置高度、宽度）：
    
    ```
    .text-overflow-more {
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 3;
        -webkit-box-orient: vertical;
    }
    ```


3. 透明效果，兼容不同浏览器

```
.transparent {
    filter: alpha(opacity=50); /* internet explorer */
    -khtml-opacity: 0.5;      /* khtml, old safari */
    -moz-opacity: 0.5;       /* mozilla, netscape */
    opacity: 0.5;           /* fx, safari, opera */
}
```

4. 制作三角形

```
.triangle { 
    border-color: transparent transparent green transparent; 
    border-style: solid; 
    border-width: 0px 300px 300px 300px; 
    height: 0px; 
    width: 0px; 
}
```

5. 禁止换行, 文字只在一行内显示不换行

```
.nowrap {white-space:nowrap;}
```

6. 文字渐变效果

```
.text-gradient{
    background-image: linear-gradient(135deg, deeppink, deepskyblue);
    -webkit-background-clip: text;
    color: transparent;
}
```

7. 背景渐变

```
.gradient{
    background: #e6e6e6;   //当浏览器不支持背景渐变时该语句将会被执行
    background: -o-linear-gradient(top, #fdfdfd,  #e6e6e6); 
    background: -moz-linear-gradient(top, #fdfdfd, #e6e6e6); 
    background: -webkit-linear-gradient(top, #fdfdfd, #e6e6e6);   //最新发布语法
    background: -webkit-gradient(linear, 0% 0%, 0% 100%, from(#fdfdfd), #e6e6e6);   //老式语法
}
```

8. 自定义滚动条

css元素(针对chrome浏览器，其他浏览器可能不生效)
>整体部分 ::-webkit-scrollbar
>两端按钮 ::-webkit-scrollbar-button
>外层轨道 ::-webkit-scrollbar-track
>内层轨道 ::-webkit-scrollbar-track-piece
>滚动滑块 ::-webkit-scrollbar-thumb
>边角 ::-webkit-scrollbar-corner
>边角拖动块的样式 ::-webkit-resizer

    ```

    .scroll-horizontal::-webkit-scrollbar{
        height: 10px;
    }
    .scroll-horizontal::-webkit-scrollbar-button{
        display: block;
        width: 5px;
        border: 5px solid transparent;
    }
    .scroll-horizontal::-webkit-scrollbar-button:start:decrement{
        border-right-color: red;
    }
    .scroll-horizontal::-webkit-scrollbar-button:end:increment{
        border-left-color: red;
    }
    .scroll-horizontal::-webkit-scrollbar-button:end:decrement{
        display: none;
    }
    .scroll-horizontal::-webkit-scrollbar-button:start:increment{
        display: none;
    }
    .scroll-horizontal::-webkit-scrollbar-thumb{
        background-color: green;
        border-radius: 30px;
    }
    .scroll-horizontal::-webkit-scrollbar-track-piece{
        /* background-color: #0898b2; */
        border-radius: 30px;
    }
    .scroll-horizontal::-webkit-scrollbar-track{
        border: 1px solid #721f1f;
        border-radius: 30px;
        margin: 0 5px;
    }
    ```

