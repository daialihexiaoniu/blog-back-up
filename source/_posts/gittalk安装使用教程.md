---
title: gittalk安装使用教程
date: 2019-09-19 08:57:23
tags: hexo
categories: JS
---

引用了新的主题之后，加入了评论功能，评论使用的是gittalk，下面介绍下gittalk的使用教程。

<!-- more -->

1. gittalk 需要你有自己的 github 账号，这一步请大家自己上网百度如何有自己的 github 账号。

2. 拥有 github 账号之后， 点击头像，点击 settings
![settings](./01.png)

3. 点击 Developer settings
![Developer settings](./02.png)

4. 点击 OAuth Apps，点击 New OAuth Apps
![OAuth Apps](./03.png)

5. 接下来我们会看到这个页面
![New OAuth Apps](./04.png)
* ```Application name```： 填写你的应用的名称
* ```Homepage URL```：填写你博客仓库的地址
* ```Application description```：填写应用的表述
* ```Authorization callback URL```：填写博客的地址
这边要注意两个 url 内容不要填错了，填错的话可能就会出问题哦。

6. 有时你会遇到 gittalk error: validation failed. 这个错误。
遇到这个错误时，需要找到你这边主题创建 gittalk 的地方，找到 id，增加 decodeURI。
```
var gitalk = new Gitalk({
    clientID: '<%= theme.gitalk.clientID %>',
    clientSecret: '<%= theme.gitalk.clientSecret %>',
    id: decodeURI(window.location.pathname),
    repo: '<%= theme.gitalk.repo %>',
    owner: '<%= theme.gitalk.owner %>',
    admin: '<%= theme.gitalk.admin %>'
})
gitalk.render('gitalk')
```

7. 有时你会遇到 Error:Not found 这个错误.
这个错误的产生主要是第5步内容填写的不对，url内容需要按照上面的正确填写哦。  

✿✿ヽ(°▽°)ノ✿