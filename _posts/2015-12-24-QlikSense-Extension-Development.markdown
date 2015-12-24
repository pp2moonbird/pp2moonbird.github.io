---
layout: post
title: "笔记：开发QlikSense扩展"
date : 2015-12-24 21:47:21 +8000
categories: visualization
---



上周末，我在[可视化世界历史](http://www.pprollingstar.com/visualization/2015/12/23/World-History-Visualized.html)，主要使用了QlikSense和QlikSense的扩展。然而我遇到了一个问题，不得不深入了解QlikSense扩展的实现原理，从而修改这个插件，满足我的需求。这里记录一下目前对QlikSense扩展开发的认识。

## 问题

我的世界历史可视化作品，最早的文明是公元前3300年的古埃及，等到我输入到Excel之后，才发现，Excel只支持公元1900年之后的年份。于是我在数据源表格中只记录历史节点的年份信息，然后在QlikSense中使用创建日期的函数`MakeDate(Year, 1, 1)`来创建日期，没想到，QlikSense也只支持公元后的年份。于是，我被迫使用这么一种变通方法：将最早的公元前年份加上一个Offset，伪装成一个公元后的日期，等到在Dashboard中展示的时候，通过`Dual`函数，减去Offset，重新渲染成带公元前后的字符串。

这招对QlikSense自带的折线图是有效的，但是对我采用的[Timeline扩展](https://github.com/ralfbecher/QlikSense_Extension_Timeline)确没有起效，于是，我不得不分析QlikSense扩展的实现原理。这里主要参考的是[@stefanwalther](https://github.com/stefanwalther)在github上的[QlikSense扩展开发教程](https://github.com/stefanwalther/qliksense-extension-tutorial)

## QlikSense Extension开发的一些知识 ##

[@stefanwalther](https://github.com/stefanwalther)老师这个教程本身还处在连载状态，我学习到足够修改Timeline插件的知识之后，就暂时先放下了。这里记录一些学习到的知识，以备后用。

## QlikSense Extension的核心 ##

其实QlikSense扩展的核心有两部分，一个是`.qext`元数据文件，里面包含了扩展的名称，图标，说明等信息。还有一个是JavaScript脚本文件，这个才是重头戏，负责渲染图形，处理各种事件。

{% highlight javascript %}
define( [ /* dependencies */ ],
	function ( /* returned dependencies as arguments */ ) {
		'use strict';
		return {

			// Paint resp.Rendering logic
			paint: function ( $element, layout ) {
				// Your rendering code goes here ...				
			}
		};
	} );
{% endhighlight %}

这个就是扩展脚本的整体框架，核心就是`paint`函数，里面有两个重要的参数

- $element, 其实就是被渲染的HTML结构
- layout, 包含了数据和属性信息

## 调试 ##

1. 可以在桌面版QlikSense里，按住`Ctrl` + `Shift` + 右键，点击`Show DevTools`
2. 打开一个QlikSense应用之后，用自己的浏览器访问`localhost:4848/hub`，这样还可以使用自己熟悉的前端调试工具，比如FireBug
3. 可以使用`console.log('someMessage', someObject)`来打印调试信息

## 从Qlik Engine中获得数据 ##

接下来的问题是，扩展是怎么样从QlikSense中获得数据的呢？

数据可以通过`layout.qHyperCube`获得

- `layout.qHyperCube.qDimensionInfo`， 包含了使用到的维度的信息
- `layout.qHyperCube.qMeasureInfo`，包含了使用到的度量的信息
- `layout.qHyperCube.qDataPages`，详细的数据

`hc.qDimensionInfo[i].qFallbackTitle`就是dimension的名字

`hc.qDataPages[0].qMatrix`可能没有全量的数据，可以随着图表的滚动，来获得新的数据。

## Timeline扩展的分析 ##

通过以上的知识，可以知道，QlikSense扩展的核心是`paint`函数，在Timeline脚本的284行，作者把qMatrix中的数据，转换成一个dataset，然后赋给`vis.DataSet`，就会调用vis这个第三方可视化库，创建最终的图形。


{% highlight javascript %}
var dataItems = new vis.DataSet(dataSet);
var container = document.getElementById(containerId);
var timeline = new vis.Timeline(container);
timeline.setOptions(options);
if (useGroups) timeline.setGroups(groups);
timeline.setItems(dataItems);
{% endhighlight %}

构造这个DataSet，使用的是这些数据：

{% highlight javascript %}
var dataItem = {
	id: e[0].qElemNumber,
	content: e[1].qText,
	start: dateFromQlikNumber(e[2].qNum)
};
{% endhighlight %}

所以，最终，只要修改dateFromQlikNumber，加上我的workaround，把QlikSense中得到的日期时间，减去Offset，就可以让公元前的日期显示为一个负数。

