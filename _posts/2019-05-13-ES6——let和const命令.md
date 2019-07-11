---
layout:     post
title:      "ES6——let和const命令"
subtitle:   "let和const命令"
date:       2019-05-13
author:     "Deshan Shi"
tags:       [Javascript，ES6]
categories : [前端]
header-img: "/img/post/post-bg-js-version.jpg"
description: "let和const命令"
---

## 目录
{: .no_toc}

* 目录
{:toc}

## let

### 块级作用域

let所声明的变量，**只在let命令所在的代码块内有效**，在代码块之外调用这个变量，let声明的变量报错；

for循环的计数器，就很合适使用let命令。

eg1：

	var a = [];
	for (var i = 0; i < 10; i++) {
	  a[i] = function () {
	    console.log(i);
	  };
	}
	a[6](); // 10

上面代码中，变量i是var命令声明的，在全局范围内都有效，所以全局只有一个变量i。每一次循环，变量i的值都会发生改变，而循环内被赋给数组a的函数内部的console.log(i)，里面的i指向的就是全局的i。也就是说，所有数组a的成员里面的i，指向的都是同一个i，导致运行时输出的是最后一轮的i的值，也就是 10.

eg2：

	var a = [];
	for (let i = 0; i < 10; i++) {
	  a[i] = function () {
	    console.log(i);
	  };
	}
	a[6](); // 6

上面代码中，变量i是let声明的，当前的i只在本轮循环有效，所以每一次循环的i其实都是一个新的变量，所以最后输出的是6。你可能会问，如果每一轮循环的变量i都是重新声明的，那它怎么知道上一轮循环的值，从而计算出本轮循环的值？这是因为 JavaScript 引擎内部会记住上一轮循环的值，初始化本轮的变量i时，就在上一轮循环的基础上进行计算。

### for循环中的let

for循环还有一个特别之处，就是设置循环变量的那部分是一个父作用域，而循环体内部是一个单独的子作用域。

eg：

	for (let i = 0; i < 3; i++) {
	  let i = 'abc';
	  console.log(i);
	}
	// abc
	// abc
	// abc

上面代码正确运行，输出了 3 次abc。这表明**函数内部的变量i与循环变量i不在同一个作用域**，有各自单独的作用域。

### 不存在变量提升

var命令会发生“变量提升”现象，即变量可以在声明之前使用，值为undefined；let命令改变了语法行为，**没有变量提升**，它所声明的变量一定要在声明后使用，否则报错。

### 暂时性死区

> 只要块级作用域内存在let命令，它所声明的变量就“绑定”（binding）这个区域，不再受外部的影响。

eg：
	
	var tmp = 123;
	
	if (true) {
	  tmp = 'abc'; // ReferenceError
	  let tmp;
	}

ES6 明确规定，如果区块中存在let和const命令，这个区块对这些命令声明的变量，从一开始就形成了封闭作用域。凡是在声明之前就使用这些变量，就会报错。