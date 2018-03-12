---
title: 试水之作：Choochoo
tags: 
- CocosCreator
- Game
date: 2017-01-20 14:35:13
---

{% asset_img choochoo.jpg choochoo %}

> 我的第一款游戏，使用 CocosCreator 制作。
> 
> Appstore : https://itunes.apple.com/app/id1189428283

<!-- more -->

# 动图效果

简易教学关卡动效
{% asset_img gif/1.gif 1.gif %}

游戏关卡动效
{% asset_img gif/2.gif 2.gif %}

结束感谢关卡动效
{% asset_img gif/3.gif 3.gif %}

# 使用到的技术

## TweenLite
在这个游戏中用到了比较多的动画，而这些动画都是由代码动态生成的，包括开场和结尾的文字特效。由程序控制的动画可以做出非常细腻的效果，并且可以根据环境动态调整。   

cocos 本身的动画库就是 action 那一套，这套系统本身是从 cocos2d-x 里迁移过来的，并没有很好的利用 js 语法的优势。比如说想同时修改节点颜色和位置，得记住每一个属性对用的 action 的名字，还得用类似 cc.sequence 的 action 串联起来，实在是很累。  

在这里我选用的是 [TweenLite](https://greensock.com/docs/#/HTML5/GSAP/TweenLite/) 动画库，它可以很好地运行在 web 和 native 端上。
使用方法很简单，只需要记住 `TweenLite.to` 这个方法就差不多了。

例：
```javascript
TweenLite.to(node, 2, {x:200, y:200});
```


TweenLite 是基础动画库，Greensock 还有加强版的动画库： TweenMax, TimelineLite, TimelineMax。更详细的相关介绍可以到 [GASP](https://greensock.com/docs/#/HTML5/GSAP) 上看。

## 关卡编辑
为了更快捷的编辑关卡，特地在 Creator 中为 Choochoo 定制了一个关卡编辑器，使用的是 **自定义 Gizmo** 技术。
实现起来很简单，在关卡编辑器中画出所有可能的点和路线，点击相关的点和路线生成相应的数据，再根据新的数据更新绘图。
再配合上 inspector 上的属性编辑，编辑一个关卡就变得非常简单了。

{% asset_img choochoo-editor.gif choochoo %}

