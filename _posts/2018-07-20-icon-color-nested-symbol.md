---
layout: post
title: "sketch设计工作流-利用色板遮罩制作图标嵌套组件"
subtitle:   "design system"
description: "design system"
keyword: "设计文档"
date: 2018-7-20 17：45
comments: true
header-img: "assets/common/icon-color-nested-symbol-bg.jpg"
thumb-img: "assets/common/icon-color-nested-symbol-thumb.jpg"
author:     "youngbeom"
tags:
    design 
    界面设计
    sketch
    design_system
    nested_symbol

---
# sketch设计工作流-利用色板遮罩制作图标嵌套组件

单词数量：608  阅读时间：3m 02s

**symbol**也就是我们称之为的组件，是sketch中个人认为最提升效率的一个设计了，它将我们常用的设计控件都组件化，方便随时调用以及统一修改，并且可以导出统一的组件给团队内的任何一位设计师，这对版本管理和团队协同效率的提升是非常大的帮助，试想一下如果某个产品功能中有几十个界面中都用了同一个icon，但是改版时需要替换成新的样式，这时候如果没有利用组建而是一个个查找替换将是非常耗费时间的工作，刚毕业做项目时第一次接触到sketch就上手做了一些功能的设计，结果因为不规范导致项目设计进展很慢，后期通过学习[Brad Frost](http://bradfrost.com/)提出的**原子化设计理论**开始设计页面的组成，极大的锻炼了我的设计思维，让我的工作流程更加的顺畅，把更多的时间去留给思考设计。
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/icon-color-nested-symbol-1.png)
这里的“原子”就是最基本的元素，文字、颜色、icon等都是最基本的元素，我们称之为“原子”，一个按钮里面包含背景颜色、文字或者icon，这样的组建我们称之为“分子”，在sketch中我们称这样的“分子”为嵌套组件(nested symbol)。


## 创建一个icon组件
首先我们要做的第一步就是创建一个icon的组件，我在这里创建了一个星星的图标。
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/icon-color-nested-symbol-2.png)        
接下来将这个图标变成一个组件，点击右键创建组件并命名为icon/star（命名的规则十分重要，每一个/符号相当于是一个“文件夹”，是包含关系）。

## 添加颜色组件
在这里我们将颜色也制作成组件的原因是根据组件的特性临近命名的组件方便查找和替换，我在文件当中制作了四个颜色的组件。
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/icon-color-nested-symbol-3.png)

## 制作色板和图标的剪切蒙版
这一步在symbol图层内将色板的组件放置在图标组件上方，然后框选两个组件之后右键点击**蒙版**，这样我们的图标就带有颜色的属性了。
![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/icon-color-nested-symbol-4.png)

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/icon-color-nested-symbol-5.png)
这里需要注意的是icon不能为group的形式必须是唯一的path，如果是group内的多个path组成的icon，需要到路径工具里面合并成一个，像adobe的pathfinder一样，因为一个色板图层只能做一个路径的蒙版，还有要注意的一点是在symbol画板中图标路径上的色板需要是组件的形式覆盖在上面，完成以上的步骤我们的图标嵌套色板的组件就做完了。我们可以到page图层当中看效果了。

![](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/icon-color-nested-symbol-6.gif)


注意右边的oversides部分，我们一共设计了四个颜色的色板，他就可以变换四种颜色的icon，剩下的我们要做的就是将每一个设计的icon的组件都添加一层色板的蒙版以及看看icon的部件一共需要几种颜色展现。

## 拓展
我们还可以进一步拓展动态颜色icon的用法，讲我们常用的色板做成3种状态，即 default hover active ，这样我们就可以在设计图中将icon做成不同的三种状态。

## 结论
在设计小程序相关项目中亲测，为项目节省了大量的时间，对项目文件的规范化也是有非常大的提升，希望还可以发现更多有效的手段提升效率，避免将时间过多投入在重复性的劳动中。最后附上sketch[模板文件](http://youngbeom-cloud.oss-cn-shanghai.aliyuncs.com/blog/assets/2018/07/%E5%9B%BE%E6%A0%87%E5%B5%8C%E5%A5%97%E7%BB%84%E4%BB%B6.sketch)，希望有帮助。

相关文章：[Design workflow quick tip #7 — Step-by-step guide to use Color as a symbol override in a symbol in…](https://blog.yipl.com.np/design-workflow-quick-tip-7-step-by-step-guide-to-use-color-as-a-symbol-override-in-a-symbol-in-5e263cc5a862)