title: 移动端设备显示限制，隐藏部分内容
date: 2016-04-19 14:11:20
description: 
categories:
- Mobile
tags:
- CSS
toc: true
author:
comments:
original:
permalink: 
---

　　**困惑：**移动端的开发，往往没有想象中的那么容易。不仅要考虑适配，还有不同场景的交互。开发手机版时，手机屏幕毕竟有限，文字过多时，往往采用一个折中的方法，将超出盒子width的部分用...代替。 

<!-- more -->

通过CSS判断，这个区域宽度

### 省略

```
<!-- 单行文本溢出 -->

text-overflow: ellipsis;
white-space: nowrap;
overflow: hidden;
```

### 一行省略

```
<!-- 多行文本溢出 -->

display: -webkit-box !important;
overflow: hidden;
text-overflow: ellipsis;
word-break: break-all;
-webkit-box-orient: vertical;
-webkit-line-clamp: 2;
```