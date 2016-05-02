---
layout: post
title: "Hack: 简化Firefox阅读模式"
date : 2016-05-02 09:47:21 +8000
categories: hack
---


Firefox和Pocket都是我很喜欢的装机必备软件, 所以都没有注意到原来Firefox 40+之后都已经默认集成了Pocket插件, 除了提供保存网页到Pocket之外, 还提供了阅读模式(Reader View)的功能, 可以直接以Pocket优化过的页面形式来展现文章的正文.

这个功能很方便, 但是还有一些优化的空间, 比如维基百科的页面: [维基百科-文艺复兴](https://en.wikipedia.org/wiki/Renaissance). 如果你直接打开的话就会发现维基百科的页面不适合阅读, 特别是使用大显示器的时候, 整个页面会显示的非常长, 不是很好阅读. 使用阅读模式之后, Pocket就提取了正文, 对排版也进行了优化. 但是, 还是有另外一个问题, 我认为链接的样式太过亮眼, 需要进行弱化. 其实默认的链接的样式是蓝色加下划线, 对一般的网页来说, 并没有什么问题, 但是对维基百科这种交叉引用非常多的页面来说, 太多的链接会干扰读者的注意力. 我就想去修改阅读模式的css.

我找到的方法是使用[Stylish](https://addons.mozilla.org/en-us/firefox/addon/stylish/)这个Firefox插件来调整阅读模式的样式.

具体的方法如下:
1. 安装Stylish插件
2. 创建一个新的配置
3. 代码如下

    @namespace url(http://www.w3.org/1999/xhtml);

    @-moz-document url-prefix("about:reader?") {

        a,
        a:visited,
        a:hover,
        a:active {
          color: #738FA7 !important;
          text-decoration: none !important;
        }

    }


我去掉了链接的下划线, 同时降低了链接的字体颜色的亮度和饱和度, 让链接不再那么出挑.

以下是对比图

修改Firefox阅读模式链接样式前:
![WorldHistory]({{ site.url }}/image/Firefox-reader-view-before.png)

修改Firefox阅读模式链接样式后:
![WorldHistory]({{ site.url }}/image/Firefox-reader-view-after.png)

希望对你有帮助



