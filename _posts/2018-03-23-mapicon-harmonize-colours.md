---
layout: post
title: "地图poi_name与marki配色"
subtitle:   "design-符合WCAG标准的配色方案"
description: "符合WCAG标准的配色方案"
keyword: "设计文档"
date: 2018-3-23 16：00
comments: true
header-img: "assets/common/harmonize_colours-bg.jpg"
thumb-img: "assets/common/harmonize_colours-thumb.jpg"
author:     "youngbeom"
tags:
    design 
    color 

---
阅读时长：3min16s 单词：656

在稀客地图中有大量的视觉设计工作，其中一项比较重要的工作就是地图样式的配色工作，地图样式的配色和视觉层级的调整是比较复杂且精密的一项工程，每一项图层出现的层级、出现的顺序、以及各自的颜色对用户带来的感受差别都是很大的，但是因为有比较完整的设计文档可供查阅是比较大的帮助。

地图设计是典型的数据驱动设计的一种形式，[地图属性](http://wiki.openstreetmap.org/wiki/Map_Features)就像是我们常用的设计工具Photoshop中的图层一样，从最低的陆地、海洋一层一层到草地、雪地、再到上面的建筑和POI（兴趣点），我们要设定每一种属性出现的层级和他的颜色等信息，数据的形式主要有三种，[点（node）](https://wiki.openstreetmap.org/wiki/Node)、[线（way）](https://wiki.openstreetmap.org/wiki/Way)、[面（area）](https://wiki.openstreetmap.org/wiki/Area)，完全就是设计基础课上的三大构成…

三种属性都可以赋予一定的属性，这里我们主要设计的是poi（兴趣点）的属性，兴趣点的数据类型是点，展示方式我们可以设定为symbol，只有它可以在一个点上添加marki（图标），在稀客地图中主要将poi的类型分成了主要的**吃** **购** **生活** **特殊** **玩** **行** **游** **住**这几个类型。每种类型用不同的颜色表示赋予颜色识别性。如下图…
![](http://blog.youngbeom.com/assets/2018/06/harmonize_colours-1.jpg)



## 颜色选取

![](http://blog.youngbeom.com/assets/2018/06/harmonize_colours-2.jpg)
颜色的选取主要是通过（HSB）色相、彩度和明度的调节来进行选择，色相的选择首先是基于我们所有大的类型一共有8种，所以在0～360的色相范围内均匀分布就可以，这样能保证在地图上冷暖的搭配比较均匀。

其次在彩度上有一个范围设定，色彩过于饱和会对视觉造成疲劳，每种类型色彩的彩度根据实际不同的视觉效果设定在40～60之间，青色和绿色的色彩饱和度触发神经兴奋的临界值比较高，所以他们的色彩饱和度比其他颜色比较低，所以尽量保证全局保证既不会出现色彩暗淡或者过于饱和的情况。
![](http://blog.youngbeom.com/assets/2018/06/harmonize_colours-3.jpg)

在明度上也有一些考虑的原因是要根据地图底色和poi色彩的对比来进行设定，为了突出地图上的poi的重要性，一般底图底层的色彩彩度不会很高，明度也是为了使文字和poi的显示不会太亮。[Sketch-Color-Contrast-Analyser](https://github.com/getflourish/Sketch-Color-Contrast-Analyser)在这里安利大家一个sketch插件，这个插件是为了满足WCAG（[web内容无障碍指南](https://www.w3.org/Translations/WCAG20-zh/)），在这份指南中，有标准的分级，比如字幕属于AA级，它对应的背景和文字的对比度数值需要在4.5:1或者3.0:1以上。

这份指南的目的是为了更有好的设计，为了一些特殊人群的照顾，稀客地图也秉承着design for all的思想进行设计，因为在室外使用的频次也比较高，所以不得不考虑这些问题。

最后在图标和文字的明度上稍有区别，图标的主要目的是为了用户首先认知某的点的类型，但是文字的主要目标是让用户便于快速阅读，所以文字在明度上区间都会比图标要小一些，也就是暗一些，为了阅读时的舒适度。

以上就是在稀客地图在poi marki和 poi name上的设计思考。

最后附上网上一篇网上的文章 [web页面文字的色彩与可读性研究](http://www.5icool.org/a/201006/531.html)

2018年3月23日 下午4:00

#4-设计