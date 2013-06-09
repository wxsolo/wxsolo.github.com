---
layout: post
title: "Frame之间的通信"
description: ""
category: "Technology"
tags: [javascript,frame,dom]
---
{% include JB/setup %}

##前言

ps: 如果可以不用frame,建议别用,影响seo优化的同时也复杂了DOM操作

不过有时Frame别无选择.

[ys](http://blog.ysmood.org/ "ysmood")做的一键评教确实好用,可惜系统换了.
我也想偷懒,打算用chrome插件助力一把.
这里面主要还是js对dom的操作.而学校的系统,自然少不了frame.
所有回归正题了.`访问frame的dom`的需求就来了.

##主要概念

在跨frame脚本中有四个要点:
*	window或者self指向当前frame中的页面;
*	parent则指向包含当前页的frame中的页面;
*	top指向最顶层的frame所包含页面.如果继承关系中只有一个frameset,则parent和top的指向都一样;
*	frames则是当前页中所有frame的集合数组;
*	opener是用open方法打开当前窗口的那个窗口;

在contentFrame中的脚本与navigationFrame中的页面通信,而这些页面都包含在一个frameset中,而且是继承
关系中唯一的一个,我们就可以在contentFrame中访问到下面这些frame:
*	parent.frames[0];
*	top.frames[0];
*	parent.frames['navigationFrame'];
*	top.frames['navigationFrame'];
frames集合是一个数组,所以可以使用序号或者名字访问.推荐使用名字,当frame顺序发生变化时,造成的影响不大.

##示例
		// 获取frame引用,调用其他页面的函数.
		var navframe = top.frames['frame name'];
		navframe.callMyFunction();

		// 获取其他frame中的文档对象,进而进行DOM操作.
		var navdoc = navframe.document;
		var menu = navdoc.getElementById('myid');

*鉴于安全性问题,这种frame间的通信不能跨域进行*

##其他参考方法

使用contentWindow属性,contentWindow属性是指指定的frame或者iframe所在的window对象,在IE中iframe或者frame的contentWindow属性可以省略,但在Firefox中如果要对iframe对象进行编辑则,必须指定contentWindow属性,contentWindow属性支持所有主流浏览器.

ie6和ie7还可以使用document.frames["iframe Name"]或者document.frames["iframe ID"]来获取相当于contentWindow属性,而firefox和chrome并不支持这些document.frames["iframe Name"]或者document.frames["iframe ID"],但是window.frames["iframe Name"]或window.frames[index]（index是索引值）也支持所有主流浏览器；