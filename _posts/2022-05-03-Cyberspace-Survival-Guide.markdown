---
layout: post
title: "疫情时代的数码生存指南"
date : 2022-05-03 8:47:21 +8000
categories: 工具
---

人在上海，因为这波疫情已经被关了五十多天了。物理上受到限制后，就被迫在数码空间中进行更多的工作、娱乐和信息交流。这里分享一些我减少噪音、提升效率和获得内心平静的经验心得。

### 使用折叠微信群功能减少微信的噪音

疫情发生后，就不得不加入小区群、楼栋群获取小区相关的信息，还要加入各种团购群进行物品采购。林子大了就什么鸟都有，有人发送不实信息，有人发送阴阳怪气鼓吹共存的文章，也有发送各种上海人民受苦受难的消息的。发前两种消息的人不是蠢就是坏，最后一种消息虽然确实是事实，但是看多了对自己的身心健康也没有好处。

对策：我后面就明白应该使用**折叠微信群**的功能来屏蔽这些群，微信时间线上一下清静了许多。

![折叠微信群]({{ site.github.url }}/images/cyber/wechat-hide-group.png){:loading="lazy"}

### 使用RSS阅读器来订阅Youtube频道

Youtube是个好东西，里面有很多好的内容，但问题是它有首页和侧边栏，通过推荐算法不停的推荐有趣的内容，用户可以不断的滚动鼠标，看到源源不断的好看好玩的视频。

有问题吗？有。人会推荐算法的傀儡，像吸毒一样上瘾，不断的去点击下一个好看的内容。

* 对策1：使用rss阅读器查看Youtube频道

获取主动权的第一个办法是把无限的列表变成有限的列表，使用rss阅读器（如[feedly](feedly.com)）可以订阅各个youtube频道，这样不登陆youtube也能获得各个频道的更新，同时不会掉入到youtube的无限推送的陷阱中。

* 对策2：使用unhook浏览器插件来删除Youtube推荐功能

另外一个策略是安装[unhook](https://addons.mozilla.org/zh-CN/firefox/addon/youtube-recommended-videos/)浏览器插件，删除youtube网页中的推荐元素，登录youtube首页后，就是空白一片，只能通过搜索来找到相关的视频，播放视频的时候也没有相关推荐。

### 通过block插件来屏蔽一些网站

这里以知乎为例，曾几何时知乎上有很多有趣的内容，但是最近的整个社区上的内容越来越差，榜单上推送的到处都是引战的话题。我决定先戒掉这个网站，减少自己在这个网站上浪费时间。

对策：可以通过BlockSite等插件来屏蔽这些网站，减少对部分网站的依赖，或者可以设置定时的规则，在某些时间段来屏蔽网站。

### 使用快捷键启动Windows的全屏模式

Windows上其实可以通过隐藏任务栏来达到全屏运行程序的效果，这样在工作时就可以避免被任务栏上的快捷方式和消息通知分心。

方法是这样的：

1. 建立一个文件夹，将文件夹路径加入到Windows的Path环境变量中，这样这个文件夹中的可执行文件可以直接通过Win + R快速启动
2. 在第一步的文件夹中建立两个bat文件，比如`h.bat`, `u.bat`，输入隐藏任务栏和显示任务栏的Powershell命令
3. 使用`Win + R`开启Windows启动窗口，输入`h`，回车后，就会隐藏任务栏

隐藏任务栏：

```
powershell -command "&{$p='HKCU:SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\StuckRects3';$v=(Get-ItemProperty -Path $p).Settings;$v[8]=3;&Set-ItemProperty -Path $p -Name Settings -Value $v;&Stop-Process -f -ProcessName explorer}"
```

显示任务栏：

```
powershell -command "&{$p='HKCU:SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\StuckRects3';$v=(Get-ItemProperty -Path $p).Settings;$v[8]=2;&Set-ItemProperty -Path $p -Name Settings -Value $v;&Stop-Process -f -ProcessName explorer}"
```

方法来自Stackoverflow的这个[回答](https://stackoverflow.com/questions/31416438/how-to-auto-hide-the-taskbar-from-the-command-line)

### 物理对策

* 使用手表进行记时

使用手表来设定一个时间范围，到点之后就停下来休息。可以配合番茄工作法来进行工作、休息的切换。

* 使用专用的物理设备

我想到还有一种方式是通过不同的物理设备进行娱乐，做到工作、生活、娱乐的切割。虽然自己并没有这么做。

### 其他优化插件

顺便推荐一些提升体验的浏览器插件

* [Mobile Wikipedia](https://addons.mozilla.org/zh-CN/firefox/addon/mobile-wikipedia-webextension)

安装这个Mobile Wikipedia插件后，可以把访问的维基百科页面重定向到相应移动端版本（其实就是在链接中增加一个m），[移动版维基百科](https://zh.m.wikipedia.org/wiki/%E7%BB%B4%E5%9F%BA%E7%99%BE%E7%A7%91)的版式设计更好，阅读体验更佳。

* [转换至简体](https://addons.mozilla.org/zh-CN/firefox/addon/%E8%BD%AC%E6%8D%A2%E8%87%B3%E7%AE%80%E4%BD%93)

有的时候我会访问一些繁体中文的博客，比如[电脑玩物](https://www.playpcesor.com/)（数字工具和效率）以及[王孟源](https://blog.udn.com/MengyuanWang/article)（国际政治），阅读时还是用插件转换成简体字后更方便。这个插件的好处是一点权限都没有要，非常的干净，让人放心。

![firefox-addons]({{ site.github.url }}/images/cyber/addons.png){:loading="lazy"}

### 总结

以上就是一些数字生活断舍离的方法。简单来说，就是通过各种小工具和软件，减少噪音。




