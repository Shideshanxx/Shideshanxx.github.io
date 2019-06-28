---
layout:     post
title:      "sticky footer布局"
subtitle:   "sticky footer布局"
date:       2018-10-10
author:     "Deshan Shi"
tags: 		[css,布局]
categories : [前端]
header-img: "/img/post/flex.jpg"
description: "sticky footer布局常见的实现方式"
---


## 基础介绍

什么是sticky footer布局？

当页面内容超出屏幕，页脚模块会像正常页面一样，被推到内容下方，需要拖动滚动条才能看到

而当页面内容小于屏幕高度，页脚模块会固定在屏幕底部，就像是底边距为零的固定定位。 

## 具体实现

### html结构

	<div class="container">
    	<div class="content-wrapper clearfix">
    		<div class="content">内容区域，可随机长度</div>
    	</div>
		<div class ="close">始终在底部</div>
	</div>

### css样式

	.clearfix
		display: inline-block
		&:after
			display: block
			content: '.'
			height: 0
			line-height: 0
			clear: both
			visibility: hidden
	
	.content-wrapper
		min-height: 100%   //至关重要，class="content"内容不足一屏时，class ="close"内容依然在底部
		.content
			padding-bottom: 64px //为底部内容留位置
		.close
			position: relative
			margin: -64px auto 0 auto   //把底部内容向上移动
			clear: both
			


