layout: post
title: HTML字体之ICON-font
categories:
- HTML
tags:
- font
toc: true
author: luuman
date: 2016-01-13 13:58:41
description:
---

　　**ICON图标：**就像GitHub一样，很早就了解到这个用法，但是一直只是用，没有静下心来，整理一下，扩展知识的广度。
　　使用ICON图标，可以统一管理自己使用的图标，不用担心图标失真，效果会更好。
<!-- more -->

# 前言
    据不完全统计，大部分的网站，都使用ICON小图标，但是这些小图标的用法，却不经相同。

# Css sprite
使用雪碧图，来管理你的小图标。
优点：减少文件的体积，减少对服务器的请求。
知识点：
  background-image:
  background-position:
特点：
1. 相对于单个小图标，它节省文件的体积、缓解了服务器的请求。
1. 一般情况下，需要保存成PNG-24的文件格式。
1. 可以设计出丰富的颜色图标。

难题：
1. 你需要预先确定图标的大小。

使用：
通过background-image:调用sprite图标../image/sprite.png
通过background-position:调用指定位置的图标内容。

使用Jquery,获取小图标的高度，统一设置小图的高度。

```
$(function){
  var iconH = $(".sprite").find("s").height(),
      triggerLi = $(".sprite").children("li");
      // console.log(iconH);
      triggerLi.each(function(){
          var $this = $(this),
              $index = $this.index();
              //console.log($index)
              // console.log(iconH*$index);

              $this.children("s").css("background-position","0 -"+iconH*$index+"px");

              $this.hover(function){
                // 鼠标移入
                $this.children("s").css("background-position","-24px -"+iconH*$index+"px");
              },function(){
                // 鼠标移除
                $this.children("s").css("background-position","0 -"+iconH*$index+"px");
              }
      })
}







# Font+HTML

通过图标字体，
优点：
1. 灵活性
1. 可扩展性
1. 矢量性
1. 兼容性
1. 本地使用

字体格式：
EOT：IE专用字体
WOFF：W3C组织推荐标准，开放的TrueType/OpenType的压缩版本。最佳格式。
TTF：在IE9以上及其他主流浏览器支持。由Microsoft、Apple公司制作的字体标准
SVG: 用于SVG字体渲染的一种格式，由W3C制作的开放标准图形格式。


| ABCD | EFGH | IJKL | ABCD | EFGH | IJKL |
| -----|:----:| ----:| -----|:----:| ----:|
| a    | b    | c    | a    | b    | c    |
| d    | e    |  f   | d    | e    |  f   |
| g    | h    |   i  | g    | h    |   i  |
| g    | h    |   i  | g    | h    |   i  |



## Icon Font介绍  ****

图标字体，网络中也有很多的种类，比如[IcoMoon](http://keyamoon.com/icomoon/app/)、[fontawesome](http://fontawesome.io/)

### 关于fontawesome的使用：
link引入：font-awesome.css、font-awesome.min.css（压缩版本）

HTML代码指定：

```
<a href="#" class="fa fa-weibo" data-cmd="tsina" title="分享到新浪微博"></a>

fa：

.fa {
    display: inline-block;
    font: normal normal normal 14px/1 FontAwesome;
    font-size: inherit;
    text-rendering: auto;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

fa-weibo：

.fa-weibo:before {
    content: "\f062";
}
```

样式引入字体声明：
```
@font-face {
  font-family: 'FontAwesome';
  src: url('../fonts/fontawesome-webfont.eot?v=4.5.0');/* 兼容IE9 */
  src: url('../fonts/fontawesome-webfont.eot?#iefix&v=4.5.0') format('embedded-opentype'), /* 兼容IE6 */
       url('../fonts/fontawesome-webfont.woff2?v=4.5.0') format('woff2'), 
       url('../fonts/fontawesome-webfont.woff?v=4.5.0') format('woff'), 
       url('../fonts/fontawesome-webfont.ttf?v=4.5.0') format('truetype'), 
       url('../fonts/fontawesome-webfont.svg?v=4.5.0#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
```
### IconMoon图标

#### 下载文件类型
1. 

# 参考资料：
[]()