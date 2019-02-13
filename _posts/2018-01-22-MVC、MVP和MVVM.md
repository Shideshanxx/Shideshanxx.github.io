---
layout:     post
title:      "MVC、MVP及MVVM"
subtitle:   "关于这三种模式的简单认识"
date:       2018-1-22
author:     "Deshan Shi"
tags:       [blog,Markdown]
categories : [blog]
header-img: "/img/post/markdown.jpg"
description: "MVC、MVP及MVVM三者之间的关系"
---

## 目录
{: .no_toc}

* 目录
{:toc}

## 介绍

写这篇随笔完全是为了加深自己的印象，毕竟写比看能获得得更多，另外本人对这三种模式的认识还是浅薄的，有待在以后的工作学习中有更深入的理解，因此不免会有误解，这里推荐大家阅读[廖雪峰关于MVVM的介绍](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/001475449022563a6591e6373324d1abd93e0e3fa04397f000)，以及阮一峰的[MVC，MVP 和 MVVM的图示](http://www.ruanyifeng.com/blog/2015/02/mvcmvp_mvvm.html)及[谈谈MVC模式](http://www.ruanyifeng.com/blog/2007/11/mvc.html)，相信您会有更深刻的理解。

## 概要

MVC、MVP及MVVM都是一种架构模式，为了解决图形界面应用程序复杂性管理问题而产生的应用架构模式。

### 发展历程

 ![](https://i.loli.net/2019/02/13/5c638037e0916.png)

## MVC模式

1.即Model、View、Controller即模型、视图、控制器。

+ View：它是提供给用户的操作界面，是程序的外壳；
+ Model：是程序需要操作的数据和信息；
+ Controller：接收View层传递过来的指令，选取Model层对应的数据，进行相应操作。

2.举一个现实中的类似的例子，MVC如同一家商铺的运作模式，View层相当于是这家商铺的店面，Model层相当于这家商铺的仓库，Controller层相当于是这家商铺的执行部门。

3.MVC有如下两种模式，不管哪种模式，MVC的通信都是单向的，由图也可以看出，View层会从Model层拿数据，因此MVC中的View层和Model层还是存在耦合的。

![](https://i.loli.net/2019/02/13/5c63816982abf.png)
![](https://i.loli.net/2019/02/13/5c63817b64ca8.png)

## MVP模式

1.MVP是从MVC进化而来，即Model、View、Presenter；View和Model同MVC中的M和V，MVP只是将MVC中的Controller变成了Presenter；

2.由上面对MVC的介绍中我们可以得知，MVC中的View层和Model层是存在耦合的，但其实我们不提倡View层与Model层有直接的交互；MVP就是这样一种思想的体现，View层与Model的交互只能通过Presenter；

3.MVP与MVC还有一点不同是，它的通信是双向的，如下图所示，有两个方向：V—>P—>M，M—>P—>V

![](https://i.loli.net/2019/02/13/5c6381e885168.png)

## MVVM模式

1.MVVM是由MVP进化而来，MVVM模式基本上与MVP相同，只是把MVP中的P变成了VM，即ViewModel

2.MVVM中的数据可以实现双向绑定，即View层数据变化则ViewModel中的数据也随之变化，反之ViewModel中的数据变化，则View层数据也随之变化

![](https://i.loli.net/2019/02/13/5c6382478c47c.png)

3.这里以前端框架VUE举例说明MVVM，当然还有许多有名的框架都用的是MVVM模式；MVVM的好处就是数据驱动，数据变，则页面变，这样就能用简单的代码，实现比较复杂的逻辑操作；因此MVVM框架比较适合逻辑复杂的前端项目，比如一些管理系统等。


