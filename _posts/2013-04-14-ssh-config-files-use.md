---
layout: post
title: "配置ssh的config文件"
description: "wxsolo's bolg"
category: Technology
tags: [ssh,git,config]
---
{% include JB/setup %}

使用ssh进行登录时,默认会使用名为id_rsa的文件作为私钥.

但有多个不同的私钥在同一客户端使用时,可以使用config文件来配置不同的站点指定相应的私钥.
## Example

		Hust example.com    
			HustName example.com
			User username
			IdentityFile ~/.ssh/the_private_kye_name

Hust 			为在客户端定义的主机别名,可以自定义.

HustName 		为要访问的站点域名或ip.

User 			登录站点用户名
	
IdentityFile 	ssh访问站点时指定私钥的路径

使用Hust指定别名,如:

		Hust test
			HustName www.stuzone.com
			User username
			IdentityFile ~/.ssh/the_private_kye_name

ssh登录时就可以这样写了(当需要用不同用户名登录同一站点时特别有用): 

		ssh test

