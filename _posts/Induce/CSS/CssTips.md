title: CSS小技巧收藏
date: 2015-12-25 18:29:00
description: 
categories: 
- HTML
tags:
- CSS
toc: true
author:
comments:
original:
permalink: 
---

　　**自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why
<!-- more -->
[]()

## CSS动画


以下是我积累的一些常用的css代码，会不断更新，最新的代码会显示在最前面，同时我也会提供最新更新日期以便查阅。

居中对齐

很多时候我们需要把一个元素在其父级容器里水平、垂直居中对齐。以下我列出了常用的几种方法：

1.在知道子元素宽度与高度的情况下进行居中，采用位置定位：absolute + margin

```
.parent {
	position: relative;
}
.child {
	position: absolute;
	width: 100px;
	height: 60px;
	top: 50%;
	left: 50%;
	margin: -30px 0 0 -50px;
}
```

2.在不知道子元素高与宽的情况下，采用位置定位：absolute + transform


.parent {
	position: relative;
}
.child {
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
}
3.采用flexbox进行居中对齐


.parent {
    display: flex;
    justify-content: center;
    align-items: center;
}
.child {
	
}
选择某范围内的子元素

选择5-10的子元素


ul li:nth-child(n+5):nth-child(-n+10) {
    background-color: red;
}


最佳适应图片

这段代码非常适用于给文章列表加缩略图的时候用，能最好的避免图片比例不协调的问题，统一排版。你可以随意更改width与height来查看效果。



.thumbnail {
    width: 200px;
    height: 150px;
    background-image: url("https://s.yimg.com/uy/build/images/sohp/inspiration/sage3.jpg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}


占满全屏


.fullScreen {
    width: 100vw;
    height: 100vh;
}
演示效果：http://lab.liuxinyu.me/fullbg/index.html

自动分章节

文章正文里我们经常采用<h2>, <h3>, <h4>, <h5>这样的标签来分章，分节。这是一个非常不错的习惯，但常常只有字体粗细大小的不同，在这里我们为每个章节加上1,2,3这样的标注。以下代码在.document容器内有效。(其他需要计数的模块也可以用这样的方法)


自适应视频播放器

当在你自己的网站插入优酷这样的视频播放器后你会发现它的高宽都是固定的，而且你在用手机浏览的时候视频播放器还变形了，以下代码自动让播放器按16:9的比例显示并自适应各个设备。

CSS代码：


.media-wrap {
    position: relative;
    width: 100%;
    height: 0;
    padding-bottom: 56.25%;
}
.media-wrap iframe,
.media-wrap embed,
.media-wrap object {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
HTML代码：


<div class="media-wrap">
<iframe height=498 width=510 src="http://player.youku.com/embed/XMTQzOTUyNjAyMA==" frameborder=0 allowfullscreen></iframe>
</div>