title: CSS学习计划
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

### transition

Internet Explorer 9 以及更早版本的浏览器不支持 transition 属性

transition 属性是一个简写属性，用于设置四个过渡属性：

* transition-property	规定设置过渡效果的 CSS 属性的名称。
* transition-duration	规定完成过渡效果需要多少秒或毫秒。
* transition-timing-function	规定速度效果的速度曲线。
* transition-delay	定义过渡效果何时开始。

```
-webkit-transition-duration: 0.5s;
transition-duration: 0.5s;

transition: property duration timing-function delay;

transition:width 2s;
/* Firefox 4 */
-moz-transition:width 2s; 
/* Safari and Chrome */
-webkit-transition:width 2s; 
/* Opera */
-o-transition:width 2s; 
```









input:focus, select, textarea {
  outline: none;
}

# CSS

```
/*首字母大写*/
text-transform:capitalize;

/*属性允许您以确切的方式定义适应某个区域的具体内容*/
box-sizing:border-box;
/* Firefox */
-moz-box-sizing:border-box;
/* Safari */
-webkit-box-sizing:border-box;

/* 清除所有a标签在点击时出现的特效：*/
a{
-webkit-tap-highlight-color:rgba(255,0,0,0);
}

/*删除线*/
text-decoration: line-through;



/* 内容将在边界内换行 */
word-wrap: break-word;


iframe无法全屏显示，html，设置高度100%。


CSS a标签，移动端显示方框


.f-img-light-wrap {
	overflow: hidden;
	position: relative
}

.f-img-light-wrap:after {
	content: '';
	height: 100%;
	width: 100px;
	transform: skewX(-25deg) translate3d(0,0,0);
	background: -moz-linear-gradient(left,rgba(255,255,255,0) 0,rgba(255,255,255,.3) 50%,rgba(255,255,255,0) 100%);
	background: -webkit-gradient(linear,left top,right top,color-stop(0%,rgba(255,255,255,0)),color-stop(50%,rgba(255,255,255,.3)),color-stop(100%,rgba(255,255,255,0)));
	background: -webkit-linear-gradient(left,rgba(255,255,255,0) 0,rgba(255,255,255,.3) 50%,rgba(255,255,255,0) 100%);
	background: -o-linear-gradient(left,rgba(255,255,255,0) 0,rgba(255,255,255,.3)50%,rgba(255,255,255,0) 100%);
	background: linear-gradient(left,rgba(255,255,255,0) 0,rgba(255,255,255,.3) 50%,rgba(255,255,255,0) 100%);
	position: absolute;
	left: -160%;
	top: 0;
	z-index: 9
}

.f-img-light-wrap:hover:after {
	transition: left 1s ease-in-out;
	left: 160%
}



```


```
<iframe src="http://sandbox.runjs.cn/show_square/587" allowtransparency="true" frameborder="0" scrolling="no" style=""></iframe>

iframe内联框架
<iframe src="http://sandbox.runjs.cn/show_square/611" allowtransparency="true" frameborder="0" scrolling="no" style=""></iframe>

scrolling
规定是否在 iframe 中显示滚动条。

name
规定 iframe 的名称。
name="main"
<a href="https://www.baidu.com/" target="main">评论管理1</a>

```




### 动画transform

#### 2D

定位translate

```
.div{
	transform:translate(X,Y);

	设置：XY轴的距离，12px，12%，-12px
	常用浏览器兼容：
	/* Safari 和 Chrome */
	-webkit-transform:translate(X,Y);
	/* Firefox */
	-moz-transform:translate(X,Y);
	/* IE 360 */
	-o-transform:translate(X,Y);
	/* Opera */
	-ms-transform:translate(X,Y);
}
```
旋转rotate

```
.div{
	transform:rotate(180deg);/* 180度 */
}
```

变化scale

```
.div{
	transform:scale(1,2);/* 宽度、高度 */
}
```

倾斜skew

```
.div{
	transform:skew(1,2);/* X轴角度、 Y轴角度*/
}
```

矩阵matrix

```
.div{
	transform:matrix();/*  */
}
```
#### 3D
旋转rotateX/rotateY

```
.div{
	transform:rotateX(100deg);/* 100度 */
}
```

### 动画过渡效果
transition

Internet Explorer 10、Firefox、Chrome 以及 Opera 支持 transition 属性。
Safari 需要前缀 -webkit-。
注释：Internet Explorer 9 以及更早的版本，不支持 transition 属性。
注释：Chrome 25 以及更早的版本，需要前缀 -webkit-。

```
.div{
	width: 100px;
	height: 100px;
	background-color: blue;
	transition: width
	transition-delay: 2s;/* 延时执行 */
}
```
### 动画效果animation

浏览器兼容性：
Internet Explorer 10、Firefox 以及 Opera 支持 @keyframes 规则和 animation 属性。
Chrome 和 Safari 需要前缀 -webkit-。
注释：Internet Explorer 9，以及更早的版本，不支持 @keyframe 规则或 animation 属性。

创建规则动画：
规定动画时间、规定动画名称

```
.div{
	animation: name 5s infinite alternate;
	/* infinite alternate */
}

@keyframes name{
	0%{
		background-color：#FFF;
	}
	25%{
		background-color：#FFF;
	}
	50%{
		background-color：#FFF;
	}
	100%{
		background-color：#FFF;
	}
}

@keyframes myfirst
{
	from {background:red;}
	to {background:yellow;}
}
```
```
@keyframes	规定动画

animation
所有动画属性的简写属性，除了 animation-play-state 属性
animation: name duration timing-function delay iteration-count direction;

animation-name
规定 @keyframes 动画的名称

animation-duration
规定动画完成一个周期所花费的秒或毫秒。默认是 0

animation-timing-function
规定动画的速度曲线。默认是 "ease"

	linear
	动画从头到尾的速度是相同的

	ease
	默认。动画以低速开始，然后加快，在结束前变慢

	ease-in
	动画以低速开始

	ease-out
	动画以低速结束

	ease-in-out
	动画以低速开始和结束

	cubic-bezier(n,n,n,n)
	在 cubic-bezier 函数中自己的值。可能的值是从 0 到 1 的数值。

steps(n,[ start | end ] ]?)这个阶梯函数，这个函数可以把动画平均划分为基本相等的，
这个n是一个自然数，意思就是把一个动画平均分成n等分，直到平均地走完这个动画，
这个要跟linear区别开来，因为linear是把动画作为一个整体，中间没有断点，而steps是把动画分段平均执行开来。

step-start等同于steps(1,start)，动画分成1步，动画执行时为开始左侧端点的部分为开始；
step-end等同于steps(1,end)：动画分成一步，动画执行时以结尾端点为开始，默认值为end。

animation-delay
规定动画何时开始。默认是 0数值

animation-iteration-count
规定动画被播放的次数。默认是 "1"数值、"infinite"无限次播放

animation-direction
规定动画是否在下一周期逆向地播放。默认是 "normal"正常播放、"alternate"动画应该轮流反向播放

animation-play-state
规定动画是否正在运行或暂停。默认是 "running"正在运行的动画、"paused"暂停动画

animation-fill-mode
规定对象动画时间之外的状态
```

### CSS多列

```
column-count
多列的个数
column-gap
每一列间隔距离
column-rule
每一列间隔线
```

### CSS选择器

:last-child