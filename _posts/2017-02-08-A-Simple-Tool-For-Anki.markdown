---
layout: post
title: "造轮子：Anki卡片输入工具"
date : 2017-02-08 20:47:21 +8000
categories: meta
---


看《学习之道》([我的读书笔记](http://www.pprollingstar.com/meta/2017/01/28/Learning-How-to-Learn.html))的时候，了解到anki这个工具。
这里给大家share一个我自己写的小工具，用来生成anki卡片，然后可以把卡片导出成`CSV`文件，最后导入到anki中。

[anki](https://apps.ankiweb.net/)是一个用来学习和记忆的工具，它的原理是把需要记忆的信息变成问题和回答，分别写在卡片的正面和反面。
进入anki的界面后，anki会显示每个卡片的问题部分，然后你可以回想这个问题的答案，再选择显示卡片的回答部分。anki会根据你能否回忆起这个卡片的答案来安排下一次复习的时间。

anki是跨平台的软件，有web版，windows版，ios版（收费）和android版（第三方开发的免费软件）。
更多关于anki本身的资料可以参考[anki官网的文档](https://apps.ankiweb.net/docs/manual.html)和这本《[Anki Essentials](https://alexvermeer.com/anki-essentials/)》

## 卡片输入工具

anki本身自带比较简单的卡片编辑功能，但是基本算是纯文本的。另外也支持从csv中导入卡片，并且如果导入的卡片是html格式的也能被正确显示。
所以我就写了一个简单的卡片输入工具。本质上一个vuejs的单页应用，所有的数据都存放在浏览器的localStorage当中。

![]({{ site.url }}/images/anki-ui.png)

## 安装和使用

### 安装

代码在github上，首先你需要Clone这个repository

    git clone https://github.com/pp2moonbird/anki

然后安装python3和一些依赖的包

    pip install flask
    pip install pandas

### 使用

运行 `anki.py` 或者 `anki.bat`

简单模式：创建一个新的卡片，问题和答案用分号`;`隔开

![SimpleMode]({{ site.url }}/images/anki-simple.png)

高级模式：编辑问题和答案的时候配有markdown编辑器，导出到csv的时候会导出编译的html

![AdvancedMode]({{ site.url }}/images/anki-md.png)

导出csv和导入进anki

点击deck的导出按钮后，这个工具会创建一个csv文件到`\data`目录下面，如果你想修改导出的文件夹位置，可以修改`\config\config.txt`

导入到anki的时候，请勾选“允许在字段中使用HTML”，这样markdown的效果就能被正确显示了。

![AdvancedMode]({{ site.url }}/images/anki-html.png)

## 感谢

感谢以下软件/工具的开发人员

- anki
- flask
- vue
- bootstrap
- flask
- pandas

