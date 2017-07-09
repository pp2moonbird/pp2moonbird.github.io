---
layout: post
title: "Shadowsocks的安装与优化"
date : 2017-07-09 08:47:21 +8000
categories: tool
---

今天来介绍一下自建Shadowsocks服务器和优化的方法。Shadowsocks是一款优秀的开源翻墙工具，自建shadowsocks服务器比起托管的vpn服务，感觉更安全，更有折腾的成就感。此外，通过BBR-TCP算法优化之后能够流畅的看720p的youtube视频（见优化部分）。

# 安装

## 购买Linux虚拟机

因为是自建Shadowsocks服务器，所以我们需要先购买一台Linux虚拟机，市面上有很多选择，比如linode，digitalocean，vultr等。创建虚拟机的时候推荐使用较新版本的Linux发行版，比如Ubuntu 17.04 LTS，这样内核版本比较新，方便优化。

## 安装和启动Shadowsocks服务器

其实安装shadowsocks不复杂，三行命令就可以搞定，参考[Shadowsocks中文文档](https://github.com/shadowsocks/shadowsocks/wiki/Shadowsocks-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)

首先安装python包管理软件pip

	apt-get install python-pip

然后安装python-setuptools

	apt-get install python-setuptools

安装shadowsocks服务器

	pip install shadowsocks

启动Shadowsocks服务器，password需要自行替换

	sudo ssserver -p 443 -k password -m rc4-md5 --user nobody -d start

然后就可以打开客户端连接服务器了。

# 使用

Shadowsocks在不同的平台上都有客户端。[Windows版本](https://github.com/shadowsocks/shadowsocks-windows)需要window7 sp1和.net framework 4.6.2 以上。

iso客户端推荐使用免费版wingy

# 优化

## 官方优化指南

首先可以参考[Optimizing Shadowsocks](https://github.com/shadowsocks/shadowsocks/wiki/Optimizing-Shadowsocks)，按照指南把参数都调整一下

## 启用BBR-TCP算法

BBR-TCP是google研究出来的TCP阻塞算法，开启之后有明显的性能提升。已经被包含在Linux4.9以后的内核之中，所以只要安装了比较新的Linux发行版，只需要去启用BBR。

使用`uname -r`来查看Linux内核版本。4.9以上就可以，否则就要升级内核。

执行 `lsmod | grep bbr`，如果结果中没有 tcp_bbr 的话就先执行

	modprobe tcp_bbr
	echo "tcp_bbr" >> /etc/modules-load.d/modules.conf

执行命令，将内核配置参数添加到配置文件中

	echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
	echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf

保存生效

	sysctl -p

检验结果

	sysctl net.ipv4.tcp_available_congestion_control
	sysctl net.ipv4.tcp_congestion_control

## 效果

播放youtube视频时，右键有个统计信息，可以很直观的看出修改后性能提升很大。我自用的服务器是在洛杉矶，ping值200以上，原本看480p的youtube视频都有些卡，优化好之后可以流畅看720p的视频。

# 番外

直接访问[shadowsocks在github的repo](https://github.com/shadowsocks/shadowsocks)的话, 看到的是

> Removed according to regulations.

但点开branch之后会发现其实这只是一个伪装的分支

![ss git branch]({{ site.url }}/images/ss-branch.png)

第一次看到的时候笑喷了。

# 总结

以上就是安装，使用和优化shadowsocks的一些经验。最近评论服务多说关了，disqus太重懒得装，欢迎来[twitter](https://twitter.com/pp2moonbird/status/883884549922365440)讨论吧。
