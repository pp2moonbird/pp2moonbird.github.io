---
layout: post
title: "Visual Studio Code 轻便好用的代码编辑器"
date : 2016-11-26 08:47:21 +8000
categories: tool
---

Visual Studio Code是微软发布的一个轻量级代码编辑器, 我最早是在HackerNews上看到发布新版本的帖子, 然后就下载下了尝尝鲜. 最近正好在写一个Vuejs的weekend project, 发现用VSCode写小型项目非常好用, 使用的过程中发现VSCode越来越多的优点. 

# 界面

VSCode跨平台, 而且安装包很小, 40MB左右, 安装完成打开后, 第一眼看到的界面就让人觉得非常酷炫. 默认是纯黑的Dark Theme, 配有一些蓝色的配色. 整体界面很简洁, 左侧有五个大的按钮可以打开左侧的功能面板, 分别是资源管理器, 全局搜索, git版本控制, 调试器和插件. 
系统自带的代码高亮配色也非常美观. 

![visual studio screenshot](https://code.visualstudio.com/home/home-screenshot-win-lg.png)

# 编程

VSCode源自Visual Studio家族, 包含了微软非常强大的IntelliSense技术, 也就是各种代码补全和提示的功能. 原生支持JavaScript语言, 也可以通过插件来支持其他语音, 比如Python, Go等. 

# Git 

VSCode对git的支持做的很好, 首先, 左侧的Git面板覆盖了大多数常用的git命令, 比如`add`, `commit`, `pull`, `pull`等等. 还可以用`Ctrl + Shift + P`呼出命令功能, 然后键入其他的git命令, 比如`git checkout`, `git branch`等等. 
不过一些复杂的命令并不能支持, 比如从一个branch checkout 一些文件到另外一个branch, 还是需要在git bash下自己执行. 

另外, VSCode提供的文件比较功能很清晰. 

# 其他功能

VSCode还有一些比较便利的功能

- Markdown 预览
- 写HTML的时候可以使用Emmet(ZenCoding)的快速填充功能
- 项目文件夹全局搜索, 支持正则表达式

# 性能

最让我满意的是, 整个VSCode性能很好, 启动速度快, 占用内存小, 各种命令执行速度很快, 全局搜索的速度也不错. 

安利了这么多, 还不赶紧去[Visual Studio Code官网](https://code.visualstudio.com)下载一个?

