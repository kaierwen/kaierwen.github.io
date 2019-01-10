---
layout: post
title:  "Jekyll 笔记"
date:   2019-01-03 11:40:00 +0800
categories: jekyll update
published: true
permalink: /:categories/:year/:month/:day/:title
---

# permalink属性
参考[https://www.bilibili.com/video/av25864819/?p=9](https://www.bilibili.com/video/av25864819/?p=9)

说明：permalink是永久链接
- 写死：例permalink: /about/不会因为frontmatter中的如date，categories的属性改变而改变文章的url地址，比如本博客的[about](/about/)页面头部中的permalink: /about/属性
- 动态配置：设置"permalink/:categories/:year/:month/:day/:title"，:表示引用变量，categories,year,monty,day,title等都是jekyll中自带的变量

- - - - - - - - - - - - - - - - - - - - -
### 参考文章：

1. [视频教程](https://www.bilibili.com/video/av25864819)
2. 作者：ds19991999
- [为Jekyll博客添加小功能](https://blog.csdn.net/ds19991999/article/details/81293467)
- [https://ds19991999.coding.me/](https://ds19991999.coding.me/)
