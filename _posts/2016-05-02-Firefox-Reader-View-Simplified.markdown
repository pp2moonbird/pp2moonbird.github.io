---
layout: post
title: "优化Firefox阅读模式"
date : 2016-05-04 09:47:21 +8000
categories: 设计
---




我是Firefox和Pocket的忠实用户, 甚至都没有注意到Firefox最近的版本都开始默认集成了Pocket插件. Pocket插件主要提供了这些功能: 1. 将网页保存到Pocket服务器, 在不同设备间进行同步. 2. 提取网页的内容, 去除干扰, 渲染成更适合阅读的版式. Firefox集成Pocket之后, 对于一些已经优化过的站点, 用户可以直接点击地址栏旁边的阅读模式按钮, 以阅读模式查看网页. 这个功能非常方便, 比如, 维基百科桌面版的字体比较小, 行的宽度太宽, 整体阅读体验不是很好, 转换成阅读模式后, 网页就被Pocket转换的更加容易阅读了.

# 链接样式的问题

虽然阅读模式已经大幅度的提升了维基百科的阅读体验, 但是还有进一步提升的空间. 我个人认为最大的问题是: 超链接的显示效果. 普通的网页的正文当中超链接的数量不会太多, 基本上只有三四处引用到别人地方会加上超链接, 而维基百科的内容页面中会有非常多的交叉引用和参考文献, 这些引用从内容的角度, 只是为读者提供辅助的相关信息, 提升文章的可信度. 但是Firefox的阅读模式, 会对这些超链接渲染成带下划线和亮蓝色的格式, 我认为, 这样的超链接, 是画蛇添足, 分散了用户的注意力, 应该进行修改.

# 我的设计方案

通常来说, 蓝色带下划线是超链接的默认样式, 在《点石成金》这本用户体验的书中, 作者告诉我们保持用户习惯的样式是最好. 但是在阅读模式里, 我们更关注的是文章本身的内容, 而不是内部的链接, 所以需要削弱链接的存在感.

从设计的角度来说, Firefox阅读模式的超链接同时使用了下划线和文字颜色两个设计元素, 所以, 要弱化的话, 只要两者取其一进行弱化就可以了. 第一种方案是保留下划线, 文字颜色与正文保持相同, 目前比较热门的博客服务[medium](https://www.medium.com)就是这样做的. [feedly](https://www.feedly.com)是google reader关闭之后我选用的rss阅读服务, 它也提供了提取正文, 重新排版的功能, 在feedly中, 超链接的下划线的灰度一开始比较淡, 当鼠标悬停上去后, 灰度会更深一些.

第二种设计的方案是, 去掉下划线, 修改文字的颜色, 我觉得这种方案更适合维基百科这种有大量超链接的页面, 毕竟大量的线条也会干扰读者的视线. 接下来是颜色的选择. 我记得在以前学习图像学的时候, 曾经学到过人眼对亮度的变化更加敏感, 而这里我想要达到的效果就是弱化正文和引用的对比, 所以, 只要把亮度控制在相同的范围, 两者的对比就会小很多. 这里使用了[Adobe的色彩服务](https://color.adobe.com/), 可以快速的调色. 最后可以学习feedly的设计, 在用户鼠标悬停的时候对超链接加上下划线, 进行补偿.

# 实现方法

设计思路有了之后, 我去寻找实现方法, 很快就google到了解决方法: 使用[Stylish](https://addons.mozilla.org/en-us/firefox/addon/stylish/)这个Firefox插件来覆盖网页的css样式. 具体来说, 就是这样的步骤:

1. 安装Stylish插件
2. 创建一个新的配置
3. 代码如下

新的stylish配置:

{% highlight css %}
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
{% endhighlight %}

我去掉了链接的下划线, 同时降低了链接的字体颜色的亮度和饱和度, 让链接不再那么出挑.

以下是对比图

修改Firefox阅读模式链接样式前:
![WorldHistory]({{ site.github.url }}/images/Firefox-reader-view-before.png)

修改Firefox阅读模式链接样式后:
![WorldHistory]({{ site.github.url }}/images/Firefox-reader-view-after.png)

# 总结
通过Stylish插件, 弱化了Firefox阅读模式的超链接显示效果, 提升了阅读维基百科时的体验.

希望对你有帮助



