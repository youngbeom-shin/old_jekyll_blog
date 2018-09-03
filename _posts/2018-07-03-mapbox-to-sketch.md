---
layout: post
title: "地图UI设计工作流-从mapbox到sketch"
subtitle:   "设计开发"
description: "设计开发"
keyword: "设计文档"
date: 2018-7-03 00：27
comments: true
header-img: "assets/common/mapbox-to-sketch-bg.jpg"
thumb-img: "assets/common/mapbox-to-sketch-thumb.jpg"
author:     "youngbeom"
tags:
    development 
    地图设计
    mapbox
    sketch

---

单词数量：1812  阅读时间：9m 03s


# 地图UI设计工作流-从mapbox到sketch
## 前言
因为公司主要产品是一款旅游地图应用-稀客地图，每年服务于出境自由行的中国用户，给用户提供精准的导航服务和语音讲解等功能，所以在毕业后到现在的两年时间，除了做产品的交互界面还有其他的一些视觉设计之外，还接触到了mapbox，mapbox是一款非常便捷的地图开发设计工具，除了基础的地图样式设计以外，其开发的[AR SDK](https://www.mapbox.com/augmented-reality/)包以及[自动驾驶](https://www.mapbox.com/automotive/)相关的一些项目都做的非常赞。这家初创公司还拿到了软银的投资，后来包括谷歌还有特斯拉等公司的一些高管和精英都加入了mapbox这家公司。

## carto css
起初在还未接触mapbox的时候还没有设计地图的概念，最开始的时候地图样式是通过[carto css](https://tumluliu.gitbooks.io/carto_zh-cn/)渲染出来的，样式还是有些杂乱，色彩的使用和搭配也是没有制定规范，设计和开发人员前期主要任务是将信息呈现在地图上，有很多细节还没有打磨，翻出来前期的地图样式，效果就是下面这样的。

### 项目初期样式效果
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-1.jpg)


### 改版后地图样式
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-2.jpg)

### 设计中对地图的需求
在很多之前的设计稿中，我需要在设计中用到地图界面时都会去其他地图平台截取所需的区域，然后将它粘贴到我的设计稿中，但是这样做的缺点就是我们无法做到个性化，没有办法去“设计”地图，包括整体的色板、图标、文字样式等。

## snazzy maps
[snazzy map](https://snazzymaps.com/)是基于谷歌地图重新设计样式的一个网站，网站内有非常多的样式可以学习，虽然很大程度上达到了定制化的目的，但是还是有非常多的限制，不能在数据或者更细节的样式上做调整，对于图层的支持上也不是很多。

## 使用mapbox

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-3.jpg)

通过mapbox的官网介绍可以知道，他们是一家为web及移动应用提供位置服务及导航的平台。mapbox已经是一款非常强大的平台，对于我这样的设计师来讲已经满足了我几乎所有的需求(除了数据获取，数据获取建议[openstreetmap](https://www.openstreetmap.org/#map=12/26.3409/128.1461))，可定制部分包括地图颜色、图标定制、字体库等。对于新上手的设计师mapbox studio也有一些设计样本供学习和使用。

### 使用mapbox studio设计地图样式

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-4.jpg)

首先你需要注册一个账号，通过这个账号会保留你所设计的样式，同时这个账号也是一个开发者账号，你可以通过平台提供的access token来将你设计的样式应用在网页或者移动应用当中。
注册完成后可以看到右上角有几个入口：
* home
* styles
* tilesets
* datasets

### 设计一款全新的地图样式
点击style(样式)，进入后可以看到你设计过的全部的样式文件，如果你还没有设计过地图样式，这个部分会是空白的，点击create创建一款全新的地图，在这里你可以选择利用mapbox给你提供的基础样式的基础上进行创作，或者选择一款空白的地图来手动添加图层。
也可以选择第二种方式就是上传已有的样式文件来生成地图，这里的上传格式要求json格式的文件。
对于第一次操作的设计师来讲，最好的建议是先去观察体验基础款的地图样式设计，因为在这份地图里面包含了几乎所有的地图图层，包括道路，植被类型，用地类型，甚至兴趣点的数据和样式图标都是按照规范设定好的，这样就能知道数据的结构和mapbox的设计逻辑，其实进入设计面板大家很容易就能看到左边的图层栏很像Adobe的layer，就是一层一层覆盖的，从最基础的土地类型到覆盖在上面的植被到道路最后建筑和兴趣点，这就方便我们去理解他的设计原理了。


![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-5.jpg)

点击creat就会打开**地图样式编辑器**这里就是所有的UI样式展现的地方，最核心的样式设计的界面！


![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-6.jpg)

点击左上角的**add layer**按钮去添加一个新的图层，点击**No tileset，click to select.**就会去手动的添加一个数据来源，这里的tile中文翻译过来是瓷砖 瓦片的意思，地图的样式就是一个一个的“瓦片”构成，如果大家在网络状态不好的时候打开一款地图应用就会发现界面的加载是一块一块的，这个就是瓦片。在mapbox中提供多种的数据来源比如：
* Mapbox Satellite
* Mapbox Streets v7
* Mapbox Traffic V1
* Mapbox Terrain V2
* 也可以手动上传自己本地已有的数据


![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-7.jpg)

在这里我选择了Mapbox Streets v7里面的**water**类型的数据，有了数据源我们就可以创建图层对数据进行样式的编辑了。颜色可以设置在不同的zoom级显示不同的颜色，比如zoom比较小时海洋的颜色浅一些，zoom放大到高一些的时候颜色变成深蓝色，等等。除此之外还可以给海洋加上一些图案，比如波纹，设置透明度，描边等等…


![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-8.jpg)

对mapbox赋予颜色比如我给海洋的颜色赋值**HSL(210,29,80)**这样它就和陆地的视觉上出现差异，渐渐有了地图的雏形。


![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-9.jpg)
接下来我们可以添加更多的图层，比如国境线，我们在tileset里面选择**admin** 之后可以选择让他出现的层级，比如国境线让他在0～22的层级上出现，这样就会在放大到最大的层级时都有数据展现。

### 数据的展现方式
根据数据的不同类型mapbox给出了不同的展现方式，
* fill
* fill extrusion
* line
* circle
* symbol
* heatmap
这都是数据在地图上的不同展现类型，比如国境线是line，草坪是fill，带图标的兴趣点是symbol，或者如果你有纽约的出租车运营数据，你也可以将数据以热力图的形式用heatmap类型来展现。

### 创新的方式去设计地图样式-Cartogram

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-10.jpg)

[Cartogram](https://www.mapbox.com/cartogram/)是mapbox官方提供的一款有意思的网站，他可以通过你拖拽一张图片去自动分析照片中的配色，然后给出他的一个配色选择，但是他也不是所有的图层都支持，现在的版本中Cartogram支持**land** **building**  **water** **label** 这四种图层类型占据了地图组成的大部分面积，所以四种类型的色彩发生变化对整个视觉的改变是非常大的，我们在设计的时候抓取风格调性可以通过这种方式来设计。

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-11.jpg)

我在这里使用的是mapbox cartogram默认的一张黑白照片，之后点击屏幕上方的**saved style**之后就可以在你的mapbox studio里面看到你的配色之后的地图了！非常的
方便快捷。

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-12.jpg)


![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-13.jpg)

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-14.jpg)

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-15.jpg)

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-16.jpg)


### 发布地图样式
通过上述的步骤，我们已经设计了一款个性化的地图，现在我们需要做的就是将设计好的地图**发布**出去，在mapbox studio中发布地图可以点击右上角的**publish your style**，点击发布之后你就可以通过点击**share，develop，and use your style**来使用这分地图。

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-17.jpg)
下图中的右下角有个**Style URL**，我们需要使用这个[链接](https://api.mapbox.com/styles/v1/youngbeom/cjjjpztvads5s2sm93o6x9zeo.html?fresh=true&title=true&access_token=pk.eyJ1IjoieW91bmdiZW9tIiwiYSI6ImNpc2ZxMXpvbTAxb2wzbm52cWI3d21xd3kifQ.-8V1Aipme2wTcp_9R95p7w#13.0/40.725100/-74.005100/0)来在我们的sketch中使用这份地图，我们点击复制！
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-18.jpg)

## 从mapbox到sketch
我们到这里就已经掌握了基础的mapbox studio的使用方法，接下来我们就要进入sketch当中，我们需要去下载一个[Sketch Maps](https://github.com/bouchenoiremarc/Sketch-Maps)插件。下载完成插件并安装之后，
1. 打开sketch并新建一个画布
2. 新建一个矩形
3. 选中矩形之后，点击**Plugins—Sketch Maps—Fill with Map**
4. 在插件弹出框内输入你要生成地图的地址，比如法国的埃菲尔铁塔
5. 设置地图的zoom level (地图缩放层级)，bearing (方位角度-最大360度)和pitch (视角，比如有3D模式的地图-最大60度)
6. 记住在mapbox设计完地图样式之后的 style URL，可以直接复制粘贴到插件弹窗内
7. 点击确认生成地图


![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-19.jpg)

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-20.jpg)

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/mapbox-to-sketch-21.jpg)

到这一步你就能看到亲自设计的地图样式已经填充到矩形里面了，这在一些页面的设计中会经常用到地图的填充，如果在这些页面中能用上自己品牌调性的地图也是非常提高产品体验的部分，绝对会是一个加分项，比如点评的境外地图部分就可以用mapbox提供的服务，在国外的应用中像snapchat和lonelyplanet已经开始使用mapbox的服务。其实mapbox收费是阶梯制的，对于个人开发者利用地图服务还是很划算的，这里是详细[价格说明](https://www.mapbox.com/pricing/)

## 结论
mapbox真的是一款非常强大的地图设计工具，如果你有一些数据想做为可视化的展现，或者你想将数据作为服务提供给客户，mapbox绝对可以满足大部分需求，下面有视频可以作为教材去更加深入的了解mapbox这款工具，油管的视频需要准备梯子。

<iframe width="560" height="315" src="https://www.youtube.com/embed/fpl4no2T1sQ" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

如果在尝试的过程遇到一些问题或者好玩的尝试欢迎交流讨论，希望遇到更多志同道合的人一起学习！


