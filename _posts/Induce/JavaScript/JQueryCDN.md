title: CDN公共库
date: 2015-12-21 18:29:10
description: 来到GitHub这么长时间，才开始真真的了解GitHub，这个国外的代码托管平台，充满着大牛的身影。
categories:
- HTML
tags:
- CDN
toc: true
author:
comments:
original:
permalink:
---
　　**CDN公共库**是指将常用的JS库存放在CDN节点，以方便广大开发者直接调用。与将JS库存放在服务器单机上相比，CDN公共库更加稳定、高速。
一般的CDN公共库都会包含全球所有最流行的开源JavaScript库，你可以在自己的网页上直接通过script标记引用这些资源。这样做不仅可以为您节省流量，还能通过CDN加速，获得更快的访问速度。

<!-- more -->

[百度静态资源公共库](http://cdn.code.baidu.com/)

百度jquery地址公共库,百度jquery cdn引用地址

稳定，快速由百度遍布全国各地100+个CDN节点提供加速服务。让开源库享受与百度首页静态资源同等待遇。
全面，开源收录超过180+开源库，并且这个数字正在不断增加。百度静态资源公共库服务不仅在Github开源库上接受任何人的提交请求，同时实时同步国外如CDNJS上优秀的开源库。
百度在之前推出了CDN公共库，同时最近google的公共库经常性的出现无法访问的问题，所以对自己站点的公共库文件进行了更新了。

当然BAE的公共库也有几个问题，主要是一下两个问题：

百度公共库目前还不支持 HTTPS 加密访问，如果有这个需求的话就需要考虑下了！百度公共库更新不是很即时，部分库的版本还是比较老，并没有提供最新版本的CDN。

资源列表

使用方法: 加载JS库，复制HTML代码片段（如下所示）到网页。例如，要加载jQuery，将如下所示的代码嵌入到你的网页中即可。

```
<script src="http://libs.baidu.com/jquery/1.9.0/jquery.js"></script>
```
## backbone

```
加载地址：

未压缩：
<script src="http://libs.baidu.com/backbone/0.9.2/backbone.js"></script>
压缩：
<script src="http://libs.baidu.com/backbone/0.9.2/backbone-min.js"></script>
官网：http://documentcloud.github.com/backbone/
```

支持的版本：0.9.2

## Bootstrap

```
加载地址：

未压缩：
<script src="http://libs.baidu.com/bootstrap/3.0.3/js/bootstrap.js"></script>
<link href="http://libs.baidu.com/bootstrap/3.0.3/css/bootstrap.css" rel="stylesheet">
压缩：
<script src="http://libs.baidu.com/bootstrap/3.0.3/js/bootstrap.min.js"></script>
<link href="http://libs.baidu.com/bootstrap/3.0.3/css/bootstrap.min.css" rel="stylesheet">
官网：https://github.com/twitter/bootstrap/
```

支持的版本：2.0.4 ，2.0.3 ，2.0.2 ，2.1.1，2.2.1，2.3.1，2.3.2, 3.0.3

## dojo

```
加载地址：

压缩：
<script src="http://libs.baidu.com/dojo/1.8.0/dojo.js"></script>
官网：http://dojotoolkit.org/
```

支持的版本：1.8.3, 1.8.2, 1.8.1, 1.8.0, 1.7.4, 1.7.3, 1.7.2, 1.7.1, 1.7.0, 1.6.1, 1.6.0, 1.5.2, 1.5.1, 1.5.0, 1.4.4, 1.4.3, 1.4.1, 1.4.0, 1.3.2, 1.3.1, 1.3.0, 1.2.3, 1.2.0, 1.1.1

## ext-core

```
加载地址：

压缩：
<script src="http://libs.baidu.com/ext-core/3.1.0/ext-core.js "></script>
官网：http://www.sencha.com/products/extjs/
```
支持的版本：3.1.0，3.0.0

## Highcharts

```
加载地址：

压缩：
<script src="http://libs.baidu.com/highcharts/2.2.5/highcharts.js"></script>
官网：http://www.highcharts.com/
```

支持的版本：2.3.5, 2.2.5

## Highstock

```
加载地址：

压缩：
<script src="http://libs.baidu.com/highstock/1.2.5/highstock.js"></script>
官网：http://www.highcharts.com/
```

支持的版本：1.2.5

## jqMobi

```
加载地址： 压缩：

<script src="http://libs.baidu.com/jqmobi/1.0.0/jq.ui.min.js "></script>
<script src="http://libs.baidu.com/jqmobi/1.0.0/jq.mobi.min.js "></script>
官网：http://www.jqmobi.com/
```

支持的版本：1.0.0

## jQuery

```
加载地址：

未压缩：
<script src="http://libs.baidu.com/jquery/2.0.0/jquery.js"></script>
压缩：
<script src="http://libs.baidu.com/jquery/2.0.0/jquery.min.js"></script>
官网： http://jquery.com/
```

支持的版本： 2.0.3, 2.0.2, 2.0.1, 2.0.0, 1.10.2, 1.10.1, 1.10.0, 1.9.1, 1.9.0, 1.8.3, 1.8.2, 1.8.1, 1.8.0, 1.7.2, 1.7.1, 1.7.0, 1.6.4, 1.6.3, 1.6.2, 1.6.1, 1.6.0, 1.5.2, 1.5.1, 1.5.0, 1.4.4, 1.4.3, 1.4.2, 1.4.1, 1.4.0, 1.3.2, 1.3.1, 1.3.0, 1.2.6, 1.2.3

## jQuerymobile

```
加载地址：

未压缩：
<script src="http://libs.baidu.com/jquerymobile/1.3.0/jquery.mobile-1.3.0.js"></script>
压缩：
<script  src="http://libs.baidu.com/jquerymobile/1.3.0/jquery.mobile-1.3.0.min.js"></script>
官网：http://jquerymobile.com/
```

支持的版本：1.3.0, 1.1.1, 1.0.1

## jQuerytools

```
加载地址：

压缩：
<script src="http://libs.baidu.com/jquerytools/1.2.7/jquery.tools.min.js"></script>
官网：http://jquerytools.org/
```

支持的版本：1.2.7

## jQueryui

```
加载地址：

压缩：
<script src="http://libs.baidu.com/jqueryui/1.8.22/jquery-ui.min.js "></script>
官网：http://jqueryui.com/
```
支持的版本：1.10.2, 1.10.1, 1.10.0, 1.9.2, 1.9.1, 1.9.0, 1.8.24, 1.8.23, 1.8.22, 1.8.21, 1.8.20, 1.8.19, 1.8.18, 1.8.17, 1.8.16, 1.8.15, 1.8.14, 1.8.13, 1.8.12, 1.8.11, 1.8.10, 1.8.9, 1.8.8, 1.8.7, 1.8.6, 1.8.5, 1.8.4, 1.8.2, 1.8.1, 1.8.0, 1.7.3, 1.7.2, 1.7.1, 1.7.0, 1.6.0, 1.5.3, 1.5.2

## JSON

```
加载地址：

未压缩：
<script src=" http://libs.baidu.com/json/json2/json2.js"></script>
官网：https://github.com/douglascrockford/JSON-js
```

支持的版本：json2

## lesscss

```
加载地址：

压缩：
<script src="http://libs.baidu.com/lesscss/1.3.0/less.min.js"></script>
官网：http://www.lesscss.net/
```

支持的版本：1.3.0

## mootools

```
加载地址：

压缩：
<script src="http://libs.baidu.com/mootools/1.4.5/mootools-yui-compressed.js"></script>
官网：http://mootools.net/
```

支持的版本：1.4.5, 1.4.4, 1.4.3, 1.4.2, 1.4.1, 1.4.0, 1.3.2, 1.3.1, 1.3.0, 1.2.5, 1.2.4, 1.2.3, 1.2.2, 1.2.1, 1.1.2, 1.1.1

## prototype

```
加载地址：

未压缩：
<script src="http://libs.baidu.com/prototype/1.7.1.0/prototype.js"></script>
官网：http://prototypejs.org/
```

支持的版本：1.7.1.0, 1.7.0.0, 1.6.1.0, 1.6.0.3, 1.6.0.2

## QUnit

```
加载地址：

未压缩：
<script src="http://libs.baidu.com/quint/1.9.0/qunit.js"></script>
官网：http://docs.jquery.com/QUnit
```

支持的版本：1.4.0，1.5.0，1.6.0，1.7.0，1.8.0，1.9.0

## scriptaculous

```
加载地址：

未压缩：
<script src="http://libs.baidu.com/scriptaculous/1.9.0/scriptaculous.js "></script>
官网：http://script.aculo.us/
```

支持的版本：1.9.0, 1.8.3

## swfobject

```
加载地址：

压缩：
<script src="http://libs.baidu.com/swfobject/2.2/swfobject.js"></script>
官网：http://code.google.com/p/swfobject/
```

支持的版本：2.1，2.2

## UNDERSCORE

```
加载地址：

未压缩：
<script src="http://libs.baidu.com/underscore/1.3.3/underscore.js"></script>
压缩：
<script src="http://libs.baidu.com/underscore/1.3.3/underscore-min.js"></script>
官网：http://underscorejs.org/
```

支持的版本：1.3.3

## webfont

```
加载地址：

压缩：
<script src="http://libs.baidu.com/webfont/1.0.28/webfont.js"></script>
官网：https://developers.google.com/webfonts/docs/webfont_loader
```

支持的版本： 1.3.0, 1.1.2, 1.1.1, 1.1.0, 1.0.31, 1.0.30, 1.0.29, 1.0.28, 1.0.27, 1.0.26, 1.0.25, 1.0.24, 1.0.23, 1.0.22, 1.0.21, 1.0.19, 1.0.18, 1.0.17, 1.0.16, 1.0.15, 1.0.14, 1.0.13, 1.0.12, 1.0.11, 1.0.10, 1.0.9, 1.0.6, 1.0.5, 1.0.4, 1.0.3, 1.0.2, 1.0.1, 1.0.0

## yui

```
加载地址：

未压缩：
<script src="http://libs.baidu.com/yui/3.4.1/yui.js"></script>
压缩：
<script src="http://libs.baidu.com/yui/3.4.1/yui-min.js"></script>
官网：http://yuilibrary.com/
```

支持的版本：3.4.1，3.3.0

## zepto

```
加载地址：

压缩：
<script src="http://libs.baidu.com/zepto/0.8/zepto.min.js"></script>
官网：http://zeptojs.com/
```

支持的版本：0.8，1.0rc

## Font Awesome

```
加载地址：

压缩：
<link href="//libs.baidu.com/fontawesome/4.0.3/css/font-awesome.min.css" rel="stylesheet">

未压缩：
<link href="//libs.baidu.com/fontawesome/4.0.3/css/font-awesome.css" rel="stylesheet">

官网：http://fontawesome.io/
```