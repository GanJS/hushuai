title: 淘宝移动端适配
date: 2015-12-25 18:29:00
description: 
categories:
- 移动适配
tags:
- 移动适配
toc: true
author:
comments:
original:
permalink: 
---
　　**移动适配：**
<!-- more -->

### YO

### Yo
Yo 是基于 Mobile First 的策略而设计，并使用 Sass 开发的 CSS Framework，具备轻量，易用，可配置，强扩展等特性，同时也适应于PC端的高级浏览器。

### 环境搭建


1. 动态设置viewport的scale

```
var scale = 1 / devicePixelRatio;
document.querySelector('meta[name="viewport"]').setAttribute('content','initial-scale=' + scale + ', maximum-scale=' + scale + ', minimum-scale=' + scale + ', user-scalable=no');
```
2. 动态计算html的font-size

```
document.documentElement.style.fontSize = document.documentElement.clientWidth / 10 + 'px';
```
3. 布局的时候，各元素的css尺寸=设计稿标注尺寸/设计稿横向分辨率/10

4. font-size可能需要额外的媒介查询，并且font-size不使用rem，这一点跟网易是一样的。

[Doyoe](http://blog.doyoe.com/ "CSS探索之旅")

[Yo](http://ued.qunar.com/mobile/qapp/doc/ "Yo 是基于 Mobile First 的策略而设计，并使用 Sass 开发的 CSS Framework，具备轻量，易用，可配置，强扩展等特性，同时也适应于PC端的高级浏览器。")
[Demo](http://blog.doyoe.com/Yo/demo/ "Yo Demo展示")
[sass](http://sass-lang.com/ "")

http://www.kejik.com/article/36278.html