title:  关于移动端界面在PC端显示的实现
date: 2016-02-27 14:11:20
description: 
categories:
- Mobile
tags:
- Mobile
toc:
author:
comments:
original:
permalink: 
---
　　**概况：**近阶段，移动端的开发十分火热，由于移动手机市场的宏大，在PC端浏览自己的移动端页面，如果不是响应式布局，样式会十分难看。
<!-- more -->


| Mobile | pad | PC |
| :----:|:----:| :----:|
|  320px - 640px  |  640px - 1024px   |  1024px - 2800px   |


## PC端显示
[Demo](/CSS3/WeiUI/ "PC端显示移动页面")

```
@media screen and (min-width: 1024px) {
  .container {
    background: url(../images/iPhone-6S.png);
    background-repeat: no-repeat;
    background-size: 351px;
    margin: -8px auto;
    width: 352px;
    height: 739px;
    overflow: visible;
  }
  .page {
    /*overflow-y: auto;*/
    -webkit-overflow-scrolling: touch;
    /* margin: auto; */
    margin: 67px 0px 0px 17px;
    width: 324px;
    height: 602px;
    /* overflow-y: hidden; */
  }
}
```


## 针对不同移动设备-响应式设计

```

device-pixel-ratio：定义输入设备屏幕的可视宽度与可见高度比率。
device-width：输入设备屏幕的可视宽度。
orientation ：屏幕横竖屏定向。landscape 是横向，portrait 是纵向【ipad 相反】
 

/* iPhone 4 */

@media
only screen and (-webkit-min-device-pixel-ratio : 1.5),
only screen and (min-device-pixel-ratio : 1.5) {
/* Styles */
}
/* iPads (portrait) */

@media only screen
and (min-device-width : 768px)
and (max-device-width : 1024px)
and (orientation : portrait) {
/* Styles */
}
/* 智能手机 (portrait and landscape) */

@media only screen
and (min-device-width : 320px)
and (max-device-width : 480px) {
/* Styles */
}
/* 智能手机 (landscape) */

@media only screen
and (min-width : 321px) {
/* Styles */
}
/* 智能手机 (portrait) */

@media only screen
and (max-width : 320px) {
/* Styles */
}
/* iPads (portrait and landscape) */

@media only screen
and (min-device-width : 768px)
and (max-device-width : 1024px) {
/* Styles */
}
/* iPads (landscape) */

@media only screen
and (min-device-width : 768px)
and (max-device-width : 1024px)
and (orientation : landscape) {
/* Styles */
}
/* iPads (portrait) */

@media only screen
and (min-device-width : 768px)
and (max-device-width : 1024px)
and (orientation : portrait) {
/* Styles */
}
/* Desktops and laptops */

@media only screen
and (min-width : 1224px) {
/* Styles */
}
/* Large screens */

@media only screen
and (min-width : 1824px) {
/* Styles */
}
/* iPhone 4 */

@media
only screen and (-webkit-min-device-pixel-ratio : 1.5),
only screen and (min-device-pixel-ratio : 1.5) {
/* Styles */
}
```