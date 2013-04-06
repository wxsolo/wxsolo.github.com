---
layout: post
title: "Input chinese in sublime at ubuntu with ibus"
description: "wxsolo's bolg"
tagline: ""
category: Technology
tags: [sublime, ubuntu, chinese, ibus, plugin]
---
{% include JB/setup %}

今天在ubuntu下使用sublime折腾自己的blog,突然发现ibus怎么也打不出中文来.
好吧!查了下,发现了一个sublime的插件[InputHelper](https://github.com/xgenvn/InputHelper)
## Install
		cd ~/.config/sublime-text-2/Packages
		git clone https://github.com/xgenvn/InputHelper.git
## Usage

- 确定ibus正常开启
- 按住`ctrl+shift+z`启动Inpt Helper,切换ibus到中文输入，输入后回车即可