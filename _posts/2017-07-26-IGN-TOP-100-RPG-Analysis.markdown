---
layout: post
title: "IGN百大RPG榜单分析"
date : 2017-07-26 08:47:21 +8000
categories: game
---

# IGN百大RPG榜单介绍

著名游戏媒体IGN在2017年5月的时候发布了百大角色扮演游戏(RPG)的榜单，链接地址：[The Top 100 RPGs of All Time (IGN)](http://www.ign.com/lists/top-100-rpgs)。我把整个榜单爬了下来，做了一些分析，总共一百个游戏横跨了30年，可以称得上是30年游戏行业的一个缩影。

# 游戏行业生态系统介绍

在进入具体的分析之前，首先科普一些概念。

- **Platform (平台)** 指的是游戏运行的平台，主要有PC和游戏主机(Console)。有能力开发游戏平台的公司屈指可数，目前主要是任天堂(Nintendo), 索尼(Sony)和微软(Microsoft)这三家。按照游戏平台的性能或发行时间，不同时代的游戏平台被归类到不同的世代(Generation)中，目前在市面上流通的已经是[第8代游戏主机](https://en.wikipedia.org/wiki/Eighth_generation_of_video_game_consoles)了，分别是WiiU, PS4, XBOXONE。
- **Publisher (发行商)** 通常我们说游戏公司的时候，其实是一个更宽泛的概念，有可能是游戏发行商，也有可能是游戏的制作团队。具体的职能上，发行商侧重于游戏的实体商品生产，营销和分发。大的游戏公司，比如Square-Enix本身就是发行商，同时会有自己的内部制作团队，也会为小公司进行游戏发行。这次百大RPG的原始数据中只有制作团队的信息，而没有发行商的信息，但是对分析的影响不是很大。
- **Developer (制作团队)** 就如上面所说，游戏制作团队有可能是发行商自己的内部团队，也可能是独立的开发公司，或者是外包公司，制作团队在完成游戏的开发之后，一般会将游戏交给发行商进行发行。
- **Game (游戏)** 游戏有不同的类型(**genre**)，这个榜单主要的对象是RPG游戏。IGN评选RPG的标准是这样的:
>- Persistent character progression (including player-exposed stats) / 需要有角色的成长
>- Combat that is a significant part of the experience / 战斗是游戏体验的重要部分
>- Choices and consequences / 选择与结果
>- Story / 故事
>- Exploration / 探索
>- Character building and customization / 角色的培养

# 榜单分析 - 平台部分

首先来看一下榜单整体的情况。下图横坐标是入选游戏的首次发行年份，横跨了30年，纵坐标游戏是在榜单的排名，颜色是根据发布平台的公司来设置的。这张图只是为你提供一个大致的印象，不需要仔细看，我在文章最后有一个tableau public的工作簿，你可以互动式的查看这些信息。

![ign-top-100-rpg-scatter-plot]({{ site.url }}/images/game/ign-top-100-rpg-scatter-plot.png)

接下来我们按照平台公司进行细分，这个时候，一些有趣的规律开始浮现出来了。譬如说，任天堂在1990-2000年间有着非常强势的地位，特别是SFC平台，除了入选的作品数量多之外，还占据了整个榜单冠军的位置，没错，就是Chrono Trigger（超时空之链）！然而，主机的RPG霸主地位从2000左右开始移交到了索尼。在榜单上还出现了已经消失的硬件平台厂商：世嘉。

![rpg-scatter-by-family]({{ site.url }}/images/game/rpg-scatter-by-family.png)

下图是按照平台对上榜游戏的统计，如果是跨平台发售的游戏会被同时计入多个平台当中
![top-rpg-count-by-platform]({{ site.url }}/images/game/top-rpg-count-by-platform.png)

接下来是对每个平台厂商的具体分析

## 任天堂 Nintendo

![ign-top-rpg-100-nintendo]({{ site.url }}/images/game/ign-top-rpg-100-nintendo.png)

任天堂在RPG领域的成就可谓是高开低走，上图表现的非常清楚。高开表现在它的第二代主机SFC的巨大成功。16位主机带来了更强的画面和更好的音效，众多的RPG巨头，比如Square，Enix纷纷挖掘2D RPG的最大潜力，推出许多了广受好评的佳作。如果你再看上上面那张图，SFC是仅次于PC, PS后面第三多入选的游戏平台，并且摘得了整个榜单的金牌和银牌。

然而，任天堂在SFC成功背后，还有对第三方厂商各种蛮横的规定与剥削，等到索尼推出PS的时候，第三方厂商应声而起，纷纷加入索尼阵营。任天堂的后面两代家用主机N64和NGC与索尼阵营的PS, PS2比较起来，销量可谓是十分惨淡。这也表现在图表上面一行任天堂家用主机上优秀的RPG乏善可陈。

但是任天堂家用主机不成，却开拓了掌机这个新市场，并且在掌机领域取得了不错的成绩。榜单中任天堂后期入选的游戏基本都属于掌机游戏。

## 索尼 PlayStation

Sony的主机事业一路发展都很迅猛。根据[vgchartz的数据](http://www.vgchartz.com/analysis/platform_totals/Hardware/Global/), PS2是世上最畅销的家用主机平台
![sony-hardware-sales]({{ site.url }}/images/game/sony-hardware-sales.png)

就像上文讨论任天堂的部分所说，初代PS发售之初，就收到很多第三方游戏公司的支持，在这个榜单中也反映在PS具有非常多的上榜游戏。

总体来看，PS阵营是整个RPG游戏的中流砥柱，在PS家族上发布的游戏不论在时间和榜单排行上都分布的非常均匀。但是PS还是有一个问题：后期好评的游戏都是跨平台的。比如评分最高的近期游戏巫师3，就是PS4, XBOXONE, PC跨平台发售的。如果将平台独占作为一个维度进行区分的话，PS系列的排行的中位数就下降到58.5了。
![ign-top-100-rpg-sony]({{ site.url }}/images/ign-top-100-rpg-sony.png)

## 微软 Xbox

![ign-top-100-rpg-xbox]({{ site.url }}/images/game/ign-top-100-rpg-xbox.png)

微软独占的上榜作品只有5作。

## PC
![ign-top-100-rpg-pc]({{ site.url }}/images/game/ign-top-100-rpg-pc.png)

PC部分有这么几个特征

- 有几部上古时期的作品
- 2000年左右有个爆发时期
- 2010左右开始的跨平台大作
- 上榜了3部独立游戏：星露谷物语，传说之下，黑暗地牢。传说之下所致敬的地球冒险2(SFC)也在榜单中，但是牧场物语没有出现在榜单当中

## 游戏平台总结

![platform-by-year]({{ site.url }}/images/game/platform-by-year.png)

把数据整合起来，就能看到一些在时间上的趋势，总的来说，任天堂在SFC时代表现最抢眼，PS从诞生以来，发挥都很稳定。微软最近有些疲软。PC在2000年有个爆发，最近也有上升的趋势。

# 榜单分析 - 开发者部分

## 日本与西方游戏公司

![japan-vs-western]({{ site.url }}/images/game/japan-vs-western.png)

我把游戏公司按照日本和西方进行了聚合，整体上看日本具有微弱的优势。

![japan-vs-western-trend]({{ site.url }}/images/game/japan-vs-western-trend.png)

但实际上这种优势主要体现在90年早期日本主机游戏上，从2000年开始，基本上日本和西方上榜的游戏数量是接近的。从平台的角度看，入选的日本游戏基本都是发行在家用主机上，而西方游戏主要在PC上发行，并且在最近几年跨平台到了主机上。

## 制作公司

Square, Enix, 以及两家公司合并后成立的Square-Enix曾经是RPG领域当之无愧的领导者，但是很尴尬的是，从2007年之后就再也没有新的游戏上榜了。最后一部上榜作品是最终幻想12，最近刚刚复刻到PS4上，结果评价比最终幻想15还要好。顺便提一下，勇者斗恶龙系列都是外包给别的公司开发的，比如Chunsoft。

![square-enix]({{ site.url }}/images/game/square-enix.png)

Bioware是欧美RPG的巨头

![bioware]({{ site.url }}/images/game/bioware.png)

下图挑选了一些新上榜的公司或者IP，FromSoftware的魂系列和CD Project RED的巫师系列表现最抢眼。入榜的新游戏中，传说之下，星露谷物语和黑暗地牢都是独立游戏，能取得这样的好成绩非常厉害了。

![new-developer-and-ip]({{ site.url }}/images/game/new-developer-and-ip.png)

## 游戏系列

这里把入榜多次的游戏系列列了出来，颜色越深，说明排名越靠前
![top-rpg-game-series]({{ site.url }}/images/game/top-rpg-game-series.png)

## 制作人：松野泰己

在整个大公司都可能只上榜一两作的榜单上，有一位制作人制作或参与了5部作品入榜，并且排名都在40位之前，这个制作人就是松野泰己。松野泰己的游戏特点是他设计的架空世界观，入榜的最终幻想战略版，放浪冒险谭，最终幻想12都是基于伊瓦利斯世界。最近，网游最终幻想14的4.1版本据说也要搞一个RETURN OF IVALICE的大型副本。

![matsuno]({{ site.url }}/images/game/matsuno.png)

遗憾的是，他在担当最终幻想12制作人的时候，称病离开了Square-Enix，后面辗转与各家游戏公司，但是没有更亮眼的新作出现。

# 榜单分析 - 游戏部分

榜单中前20名
![top-20-rpg]({{ site.url }}/images/game/top-20-rpg.png)

最近十年发售的作品
![recent-10-years]({{ site.url }}/images/game/recent-10-years.png)

## 分析

通过TOP20的图表，能够看到2002年之后入选的作品不多，最近十年竟然只有4部作品入选。而近十年间，好评的作品大多数是跨平台作品，独占作品的平均排名是60位左右。

这些趋势其实反映了游戏玩家，游戏市场和游戏开发公司的一些变化。

### 游戏市场

角色扮演游戏(RPG)只是整个游戏类型中的一种，实际上，最近几年最受欢迎的游戏类型是动作，体育和射击游戏。

下面的图表是基于[vgcharts每年的百大游戏销售排行](http://www.vgchartz.com/yearly/2017/Global/)。日本的数据从1990年开始统计，而全球的数据从2005年开始统计

![best-selling-games-japan]({{ site.url }}/images/game/best-selling-games-japan.png)

![best-selling-games-worldwide]({{ site.url }}/images/game/best-selling-games-worldwide.png)

虽然RPG在日本一直处于领先地位，但是最近也被动作游戏超越了。而在全球范围内，体育，动作和射击游戏的销量超过RPG一倍多。游戏的销量一定会改变游戏制作公司将来制作的倾向。

### 游戏玩家的变化

根据美国Entertainment Software Association的[报告](http://essentialfacts.theesa.com/)，美国的电子游戏玩家的平均年龄已经是35岁了。随着年龄的增长，玩家对游戏内容和口味的偏好也会发生变化。年少时玩的是少年拯救世界，到了30岁开始玩的是满世界找儿子（辐射4）和找女儿（巫师3）。另外，玩家的闲暇时间也发生了变化，成年人需要工作，闲暇时间变更少和更碎片化。RPG游戏通常需要40个小时以上才能通关，其他类型的游戏，则是以局为单位的，所消耗的时间少的多。最后，玩家对游戏的期待越来越高，剧情，制作水平，都要求制作公司不断精益求精。对应的，游戏公司需要更多的开发人员，更高的成本来完成一部游戏，同时，采用跨平台的策略来最大化自己的收益，这也是为什么最近的高评分的游戏都是跨平台的原因。

# 总结

以上的分析，总体是基于IGN的榜单来做的。IGN作为一家西方的游戏媒体，反映出来的自然是美国玩家的口味，跟中国或者日本游戏玩家心目中的TOP 100肯定是有些差距的。但是，整体上看，这个榜单的评选还是很均衡的。

30年弹指一挥间，感谢这些开发出优秀作品的制作人员。

# 全部榜单

<iframe src="https://public.tableau.com/views/IGNTop100RPGs/rpg?:showVizHome=no&:embed=true" frameborder="0" height="500px" width="90%"></iframe>