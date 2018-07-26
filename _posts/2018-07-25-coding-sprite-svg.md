---
layout: post
title: "通过代码层面管理并编辑svg图片-sprites"
subtitle:   "关于svg格式的学习和应用"
description: "设计开发"
keyword: "设计文档"
date: 2018-7-25 23:34
comments: true
header-img: "assets/common/coding-sprite-svg-bg.jpg"
thumb-img: "assets/common/coding-sprite-svg-thumb.jpg"
author:     "youngbeom"
tags:
    design 
    workflow
    vector file
    design_system

---

# 通过代码层面管理并编辑svg图片-sprites

单词数量：1360  阅读时间：6m 48s

## 发现问题：操作不规范导致finder中svg图像显示大小不同
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-1.png)

上图是我在管理sprites image时发现矢量文件显示出现问题，我们知道svg是基于xml的代码，出现这个问题的时候最先想到的是表现形式的不同一定是因为内部代码的格式或者是写法不同的，所以用sublime打开两个svg文件，发现内部的代码确实是不同的。

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-2.png)

通过分析可以看到，大图svg的代码是一行写出来的，而小图svg的代码是用了6行，还有在代码的细节上也有些许差异，不光是代码层面，在我用AI打开svg文件的时候发现图层上的表现也是不一样的。
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-3.png)

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-4.png)

## 猜想可能出现问题的原因
1. 图层命名导致
2. 因为存在多余的无用图层
3. 图层顺序导致
4. 代码行数导致
5. 代码内容出错

## 验证猜想

### 1. layer图层命名导致
通过分析accessories_11和aerialway_11的图层命名不同，想通过更改并统一命名来调试达到目的，发现并不能实现最终效果，猜想错误。

### 2. 因为存在多余的无用图层
没有实际路径的图层在两个文件内都存在，但是删除了无用图层之后再次导出为svg发现还是没有变成大图。猜想错误。

### 3. 图层顺序导致 
因为aerialway_11的图层中复合路径的图层在最上面，所以认为是否因为顺序导致大小的不同，但是试验过后并没有得到验证。再后来查看代码上面<path>字段的时候发现，我们设计软件最底部的图层会在代码的最上面开始显示，也就是顺序设计软件和代码是相反的。

### 4. 代码行数导致
通过sublime将accessories_11的代码从6行合并成1行再存储发现还是没有变成大图，和是否是多行但行还是没有关系。代码行数的不同在后文会有解释说明，主要是再导出的时候框选了minify导致丢失原有的格式。但是格式的不同并不会在设计软件的显示上出现差别，都是一样的图形显示。

### 5. 代码内容出错
经过上面的实验，最终还是将问题集中在代码的内容上，发现两者在viewbox附近的代码存在不同，accessories_11部分相比aerialway_11在viewbox前面多了一段`width="19" height="19”`代码，我试着将这一段代码删除再存储，发现问题得到解决，基本可以判定是这段代码使文件在显示上存在差异。

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-5.png)

后来在实际操作illustrator的时候发现需要框选responsive，这样最终在finder中看到的都是大图的图标，代码中也不会带有width和height，另外一个如果是框选minify的话会让svg的代码变成一行，丢掉原有的对其格式。也就是上文提及的代码行数问题。
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-6.png)
::上图为标准导出设定::



![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-7.png)
::选择minify选项的svg代码::


![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-8.png)
::没有选择minify选项的svg代码::




## 统一代码格式
现在剩下的就是希望我们的svg文件都能以大视图的方式显示在finder中，这对我们去操作查找图标帮助非常大，所以我们要批量将文件夹内的400多个svg文件中的`width="19" height="19”`代码删除，我想通过sublime查找和替换的方式去批量操作。

## 导出规范
1. layer name=file name！
2. 用export as
3. Use Artboards
4. styleing：Presentation Attributes
Font：svg
Image：Preserve
Object IDs：Layer Names
Decimal：3
Responsive勾选，Minify不勾选

这里的Responsive就是会在导出的代码中不包含`width="19" height="19”`，会通过自适应的方式而不是去限定高宽的数值，这是在软件层面操作的时候设定的方式，但是如果在sublime中直接编辑删除上面的代码则是省去了打开AI的时间，甚至比Adobe的批处理更省时间。
规范制订的目的是为了防止数量特别多时也能快速的找到相应的位置和标记的代码，方便修改和做进一步的操作。


## 应用：通过sublime批量操作修改icon
通过sublime操作去修改svg的主要原因是因为省去了打开操作设计软件的步骤，直接查找替换会快速很多，节省了大量的时间。
### 操作说明
首先我们频繁会改动的svg主要集中在默认的icon，不包含世界杯地图等这样的特殊样式地图，以交通类目下的bicycle为例，icon主要是分为两个部分，交通主题色圆形的背景部分`<circle cx="9.5" cy="9.5" r="9.5" fill="#6c7"/>`和背景上面的自行车图形部分`<path d="M10.5,5.5a.5.5,0,0,0,0,1H11v.7L8.3,8.8,7.7,7.5h.7a.5.5,0,0,0,0-1h-2a.5.5,0,0,0,0,1h.2L7,8.6c-.2,0-.4-.1-.6-.1A2.475,2.475,0,0,0,4,11.046L4,11.1a2.6,2.6,0,0,0,2.5,2.4A2.476,2.476,0,0,0,9,11.049V11H9a2.011,2.011,0,0,0-.4-1.3l2.5-1.4.4.4A2.526,2.526,0,0,0,10,11a2.5,2.5,0,1,0,2.7-2.5L12,7.8V6a.457.457,0,0,0-.4-.5Zm-4,4A1.5,1.5,0,1,1,5,11,1.5,1.5,0,0,1,6.5,9.5Zm6,0h0A1.454,1.454,0,0,1,14,10.9V11a1.5,1.5,0,0,1-3,0,1.473,1.473,0,0,1,1.445-1.5Z" fill="#fff"/>`  这两部分的代码会经常修改的是里面的颜色部分，为了方便归类和修改我讲所有的icon都分成了几大类
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-9.png)
在默认主题下是上述代码中的颜色，但是在新的样式light主题中icon如果太过鲜艳会吸引过多的视觉注意，这违背了最初的设计目标，所以我们选择了灰色背景白色图标的方式，在sublime修改几十个图标颜色替换的操作只需要不到一分钟，下面分解具体的操作。
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-10.jpg)


1. **用sublime打开交通类图标所在的文件夹**
 file——open——图标所在文件夹
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-11.png)
2. **在文件内查找**
find—find in files(com+shift+F)—输入要替换的内容
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-12.png)

3. **分别替换背景和图标颜色**
在find输入框中填写需要替换的16进制颜色代码，在replace输入框中填写新的代码，之后点击右下角的::Replace::之后点击file—save all，操作完成后就能在文件夹内看到变化后的图标。
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-13.png)

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/coding-sprite-svg-14.png)

4. 之后就可以通过脚本命令行来制作sprites了，在sourcetree中提交万修改就能在测试服务器中看到新的效果了。

## 总结
### 简单高效
通过代码层面去管理和编辑svg是新的一种尝试，能让我们更加了解svg这种特殊的矢量格式，也能通过这种方式大大增加工作效率，最初接触这项任务时完成四百多张图标的操作用了将近两个工作日，而现在只需要不到十分钟就能操作完成并且部署看到新的效果。
### 便于管理
通过发现的问题简单的操作了一下关于图标的管理及制作的一些小细节，发现通过整理和归类对于svg的管理也带来了帮助，通过文件夹的归类方式上也能让设计思维得到表达，但是在具体在设计实施的过程中也可能会因为一些需求进行相应的变化，目前的方案只是适用于比较简单重复性比较高的任务，如果后期变得复杂还需要引入正则表达式的方式进行增删、查找和编辑，但是最终目标还是提高效率和设计质量，如果对于上述方案有新的想法和建议欢迎在评论区补充！

(评论系统在翻墙时可见…)

