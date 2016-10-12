layout: post
title: HTML结构零散
keywords:
- HTML
categories:
- HTML
tags:
- HTML
toc: true
author: luuman
date: 2016-01-13 13:58:41
description:
---
　　**HTML结构零散：**头部分的标签、元素有很多，涉及到浏览器对网页的渲染，SEO 等等，而各个浏览器内核以及各个国内浏览器厂商都有些自己的标签元素,这就造成了很多差异性。移动互联网时代，head 头部结构，移动端的 meta 元素，显得更为重要。了解每个标签的意义，写出满足自己需求的 head 头标签，是本文的目的。本篇以一丝的文章为基础，进行扩展总结介绍常用的 head 中各个标签、元素的意义以及使用场景。
<!-- more -->
### 版权声明

DOCTYPE(Document Type)，该声明位于文档中最前面的位置，处于 html 标签之前，此标签告知浏览器文档使用哪种 HTML 或者 XHTML 规范。
DTD(Document Type Definition) 声明以 <!DOCTYPE> 开始，不区分大小写，前面没有任何内容，如果有其他内容(空格除外)会使浏览器在 IE 下开启怪异模式(quirks mode)渲染网页。公共 DTD，名称格式为注册//组织//类型 标签//语言,注册指组织是否由国际标准化组织(ISO)注册，+表示是，-表示不是。组织即组织名称，如：W3C。类型一般是 DTD。标签是指定公开文本描述，即对所引用的公开文本的唯一描述性名称，后面可附带版本号。最后语言是 DTD 语言的 ISO 639 语言标识符，如：EN 表示英文，ZH 表示中文。XHTML 1.0 可声明三种 DTD 类型。分别表示严格版本，过渡版本，以及基于框架的 HTML 文档。
>XHTML

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" >
```

>HTML

```
<!-- HTML 4.01 strict -->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">

<!-- HTML 4.01 Transitional -->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">

<!-- HTML 4.01 Frameset -->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
```

>HTML 5

```
<!-- HTML 5 -->
<!DOCTYPE html>
<html>
```

```
<!-- HTML 5 -->
<!DOCTYPE html>
<html lang='en' xmlns='http://www.w3.org/1999/xhtml'>
```

HTML5兼容

```
引用Google的html5.js文件

<!--[if IE]>
<script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
<![endif]-->

将上代码复制到head部分，记住一定要是head部分（因为IE必须在元素解析前知道这个元素，所以这个js文件不能在其他位置调用，否则失效）

最后在css里面加上这段：

/*html5*/
article,aside,dialog,footer,header,section,footer,nav,figure,menu{display:block}

主要是让这些html5标签成块状，像div那样。
```
### 语言

```
<!-- 英文 -->
<html lang='en'>

<!-- 简体中文 -->
<html lang="zh-cmn-Hans">

<!-- 繁体中文 -->
<html lang="zh-cmn-Hant">


```

[网页头部语言](http://www.zhihu.com/question/20797118 "网页头部的声明应该是用 lang="zh" 还是 lang="zh-cn"？")

## HTML

## HEAD

### 标题SEO

```
<!-- 标题 -->
<title>HTML Base</title>
```

### base默认地址

```
<base> 标签为页面上的所有链接规定默认地址或默认目标。
使用 <base> 标签可以改变这一点。
浏览器随后将不再使用当前文档的 URL，而使用指定的基本 URL 来解析所有的相对 URL。
这其中包括 <a>、<img>、<link>、<form> 标签中的 URL。
在 HTML 中，<base> 标签没有结束标签；在 XHTML 中，<base> 标签必须被正确地关闭。
但是还是建议要闭合标签，这样不同浏览器兼容不容。

```

```
该标签将会控制所有链接，围棋添加默认的链接。
默认的链接
<base href="http://www.w3school.com.cn/i/" />
默认的链接打开方式
<base target="_blank" />

注意：
通常通常情况下，默认链接会自动添加到链接的前面。但是，也有特例：
<base href="http://www.w3school.com.cn/i/" />
<link rel="stylesheet" href="css/root.css"/>
http://www.w3school.com.cn/i/css/root.css

但是，如果添加根目录（绝对路径），链接会自动根据默认链接进行根目录的查询指定。
<base href="http://www.w3school.com.cn/i/" />
<link rel="stylesheet" href="/css/root.css"/>
http://www.w3school.com.cn/css/root.css
```

### meta

#### 编码格式

```
<!-- 编码格式 -->
<meta charset="utf-8">
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<meta http-equiv="Content-Type" content="text/html; charset=gb2312" />
```

#### 编码格式

```
<meta http-equiv="X-UA-Compatible" content="IE=7">  
<!-- 指定网页的兼容性模式设置 -->

<meta http-equiv="X-UA-Compatible" content="IE=8">  
<!-- 以上代码告诉IE浏览器，无论是否用DTD声明文档标准，IE8/9都会以IE7引擎来渲染页面。   -->

<meta http-equiv="X-UA-Compatible" content="IE=edge">  
<!-- 以上代码告诉IE浏览器，IE8/9都会以IE8引擎来渲染页面。   -->

<meta http-equiv="X-UA-Compatible" content="IE=7,IE=9">  
<!-- 以上代码告诉IE浏览器，IE8/9及以后的版本都会以最高版本IE来渲染页面。   -->

<meta http-equiv="X-UA-Compatible" content="IE=7,9">  
<meta http-equiv="X-UA-Compatible" content="IE=Edge,chrome=1">
<!-- 以上代码IE=edge告诉IE使用最新的引擎渲染网页，chrome=1则可以激活Chrome Frame. -->
```

#### 渲染页面

```
<meta name="renderer" content="webkit">
<!-- 默认webkit内核 -->
<!-- 360 使用Google Chrome Frame -->
<meta name="renderer" content="ie-comp">
<!-- 默认IE兼容模式 -->
<meta name="renderer" content="ie-stand">
<!-- 默认IE标准模式 -->
```

#### 页面关键词SEO

```
<!-- 关键词 -->
<meta name="keywords" content="" />
```

#### 页面描述SEO

```
每个网页都应有一个不超过 150 个字符且能准确反映网页内容的描述标签。

<!-- 描述 -->
<meta name="description" content="" />
```

```
<meta name="author" content="作者"> 
<meta name="build" content="日期"> 
<meta name="coprright" content="版权"> 
<meta name="reply-to" content="email"> 
```

#### 搜索引擎索引方式

```
Robots用来告诉搜索机器人哪些页面需要索引，哪些页面不需要索引。Content的参数有all、none、index、noindex、follow、nofollow。默认是all。

<meta name="robots" content="index,follow" />

<!--
all：文件将被检索，且页面上的链接可以被查询；
none：文件将不被检索，且页面上的链接不可以被查询；
index：文件将被检索；
follow：页面上的链接可以被查询；
noindex：文件将不被检索；
nofollow：页面上的链接不可以被查询。
-->
```

#### 页面重定向和刷新

```
content内的数字代表时间（秒），既多少时间后刷新。
如果加url,则会重定向到指定网页（搜索引擎能够自动检测，也很容易被引擎视作误导而受到惩罚）。

<meta http-equiv="refresh" content="5;url=http://luuman.github.io/" /> 
```

#### 页面期限

```
可以用于设定网页的到期时间。一旦网页过期，必须到服务器上重新传输，必须使用GMT的时间格式。

<meta http-equiv="expires" Content="Wed, 26 Feb 1997 08:21:57 GMT"> 
```

#### 页面Cookie设定

```
如果网页过期，那么存盘的cookie将被删除。

<meta http-equiv="Set-Cookie" content="cookievalue=xxx; expires=Friday, 12-Jan-2001 18:18:18 GMT； path=/">
```

#### 页面Cache模式

```
禁止浏览器从本地计算机的缓存中访问页面内容。

<meta http-equiv="Pragma" content="no-cache">
```

#### 显示窗口的设定

```
强制页面在当前窗口以独立页面显示，用来防止别人在框架里调用自己的页面。

<meta http-equiv="Window-target" content="_top">
```

#### 可视区域（移动端）

```
<!-- 可视区域 -->
<meta name="viewport" content="width=device-width,height=device-height,initial-scale=1.0,maximum-scale=1.0,user-scalable=no">

width - viewport的宽度 
height - viewport的高度 
initial-scale - 初始的缩放比例 
minimum-scale - 允许用户缩放到的最小比例 
maximum-scale - 允许用户缩放到的最大比例 
user-scalable - 用户是否可以手动缩放

minimal-ui iOS 7.1 beta 2 中新增属性，可以在页面加载时最小化上下状态栏。这是一个布尔值，可以直接这样写：

<meta name="viewport" content="width=device-width, initial-scale=1, minimal-ui">
```

#### 禁止了把数字转化为拨号链接

```
<!-- 禁止了把数字转化为拨号链接 -->
<meta name="format-detection" content="telephone=no" />
```

#### 忽略识别邮箱

```
<!-- 禁止了识别邮箱 -->
<meta name="format-detection" content="email=no" />
```

#### 关键词

```
<!-- 删除默认的苹果工具栏和菜单栏 -->
<meta name="apple-mobile-web-app-capable" content="yes" />
```

#### 关键词

```
<!-- 控制状态栏显示样式 -->
<meta name="apple-mobile-web-app-status-bar-style" content="default" />
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />

默认：default（白色）
black（黑色）
black-translucent（灰色半透明）
```

#### Iphone的Safari浏览器

```
<!-- iphone的safari浏览器 -->
<meta name="apple-itunes-app" content="app-id=432274380" />
<!-- <meta name="znonce" content="74810a1113ff4cf49d97f2616bdfe158"> -->
```

#### 添加Meta声明

```
<!-- 用于添加Meta声明；无对应关系的PC页面无需添加Meta -->
<meta http-equiv="mobile-agent" content="format=[wml|xhtml|html5]; url=url">
<meta http-equiv="mobile-agent" content="format=html5;url=http://www.z.com/">
```

#### 网站所有者

```
<!-- 验证网站所有者的一种方式 -->
<meta property="wb:webmaster" content="8e9c4b702508b902" />
```

#### 其他

```
<!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->  
<meta name="HandheldFriendly" content="true">  

<!-- 微软的老式浏览器 -->  
<meta name="MobileOptimized" content="320">  

<!-- uc强制竖屏 -->  
<meta name="screen-orientation" content="portrait">  

<!-- QQ强制竖屏 -->  
<meta name="x5-orientation" content="portrait">  

<!-- UC强制全屏 -->  
<meta name="full-screen" content="yes">  

<!-- QQ强制全屏 -->  
<meta name="x5-fullscreen" content="true">  

<!-- UC应用模式 -->  
<meta name="browsermode" content="application">  

<!-- QQ应用模式 -->  
<meta name="x5-page-mode" content="app">  

<!-- windows phone 点击无高光 -->  
<meta name="msapplication-tap-highlight" content="no">  
```

#### 社交分享（富媒体对象）

```
网页内容可以被其他社会化网站引用等，目前这种协议被SNS网站如Fackbook、renren采用。

<meta property="og:type" content="article">
<meta property="og:title" content="HTML结构零散">
<meta property="og:url" content="http://yoursite.com/2016/01/13/HTMLbase/index.html">
<meta property="og:site_name" content="Luuman's Blog">
<meta property="og:description" content="自用笔记：本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why　　最近，使用Hexo遇到了很多问题，在设立进行整理。">
<meta property="og:updated_time" content="2016-01-20T16:59:08.000Z">
```

```
-----------Base Element基本类型-----------
1、og:type 网页资源类型标识
content enum: 
● video 视频
● audio 音频
● link 链接
● photo 图片
● product 产品
2、og:title 标题描述
3、og:image 缩略图
4、og:url 当前内容链接
5、rr:appid 如果您的网站是CONNECT到renren.com的，请提供该ID 
6、rr:appid 如果您的网站是CONNECT到renren.com的，请提供该ID 
7、og:width 视频的宽度
8、og:height 视频的高度
-----------Audio Element 音频------------
1、og:audiosrc 音乐资源链接，例如可是播放歌曲的flash地址
2、og:artist 音乐家
-----------Commen Page Element 普通网页------------
1、og:abstract 内容摘要

2、og:contentid 内容主体的ID，用来标识当前页面主要内容所处的HTML标签的ID 
-----------Graphic Element 图片------------

1、og:photo 图片列表

2、og:width 图片宽度
3、og:height 图片高度

-----------Product Element 商品-----------

1、og:price 产品价格
2、og:description 产品描述
3、og:nick 店铺名

4、og:postfee 运费
```

```
<meta property="fb:admins" content="100001422224225">
<meta property="fb:page_id" content="241333394220">
```

#### 访问时以兼容模式访问

```
国内浏览器很多都是双内核（webkit和Trident），webkit内核高速浏览，IE内核兼容网页和旧版网站。而添加meta标签的网站可以控制浏览器选择何种内核渲染。

<!-- 访问时以兼容模式访问 -->

<!-- 默认webkit内核 -->
<meta name="renderer" content="webkit">
<!-- 默认IE兼容模式 -->
<meta name="renderer" content="ie-comp">
<!-- 默认IE标准模式 -->
<meta name="renderer" content="ie-stand">

国内双核浏览器默认内核模式如下：

1. 搜狗高速浏览器、QQ浏览器：IE内核（兼容模式）
2. 360极速浏览器、遨游浏览器：Webkit内核（极速模式）
```

#### 创建一个推特卡

```
<meta name="twitter:card" content="summary" />
<meta name="twitter:url" content="http://www.peerflyoffers.com/offer.php?id=7351" />
<meta name="twitter:title" content="Tara Astrology - US" /><br /><meta name="twitter:description" content="Payout: $1.30 - CR: 28.91% - EPC: $0.38 - Get your free reading! Target demo is women 25+. Converts on first page." />
<meta name="twitter:image" content="http://s.wordpress.com/mshots/v1/http%3A%2F%2Fpeerfly.com%2Fpreview.php%3Foffer%3D7351?w=400&amp;height=400" />
<meta name="twitter:site" content="@peerflyoffers" />
<meta name="twitter:creator" content="@LukePeerFly" />
```

#### Windows 8

```
<!-- Windows 8 磁贴颜色 -->
<meta name="msapplication-TileColor" content="#000"/>

<!-- Windows 8 磁贴图标 --> 
<meta name="msapplication-TileImage" content="icon.png"/>
```

#### 手机页URL

```
<meta name="mobile-agent" content="format=[wml|xhtml|html5]; url=url">
<!--
[wml|xhtml|html5]根据手机页的协议语言，选择其中一种；url="url" 后者代表当前PC页所对应的手机页URL，两者必须是一一对应关系。
--> 
```

#### 百度

```
用百度打开网页可能会对其进行转码（比如贴广告）

<meta http-equiv="Cache-Control" content="no-siteapp" />
```
### 引入link

#### Icon link

```
<!-- Icon link -->
<link rel="shortcut icon" href="favicon.ico">

<!-- 添加到主屏上的图标会使用指定的图片 -->
<link rel="apple-touch-icon" href="templets/default/images/ico/apple-touch-icon.png">

<!-- ipad -->
<link rel="apple-touch-icon" sizes="72x72" href="templets/default/images/ico/apple-touch-icon-72.png">

<!-- iPhone、iTouch -->
<link rel="apple-touch-icon" sizes="114x114" href="templets/default/images/ico/apple-touch-icon-114.png">

<!-- precomposed -->
<link rel="apple-touch-icon-precomposed" href="static/img/ios/zhihu(57px).png" />
<link rel="apple-touch-icon-precomposed" sizes="72x72" href="templets/default/images/ico/apple-touch-icon-72.png">
<link rel="apple-touch-icon-precomposed" sizes="114x114" href="templets/default/images/ico/apple-touch-icon-114.png">
```

#### section

```
<!-- 把搜索功能放到浏览器的快捷搜索工具上 -->
<link rel="search" type="application/opensearchdescription+xml" href="static/search.xml" title="知乎" />
```

#### section

```
<link rel="stylesheet" href=".css">
```

#### 添加 RSS 订阅

```
<!-- 添加 RSS 订阅 -->
<link rel="alternate" type="application/rss+xml" title="RSS" href="/rss.xml" />
```

### 引入JavaScript

```
<!-- JavaScript -->
<script type="text/javascript"></script>
```

### 引入style


### 移动端

```
<!DOCTYPE html> <!-- 使用 HTML5 doctype，不区分大小写 -->
<html lang="zh-cmn-Hans"> <!-- 更加标准的 lang 属性写法 http://zhi.hu/XyIa -->
<head>
    <!-- 声明文档使用的字符编码 -->
    <meta charset='utf-8'>
    <!-- 优先使用 IE 最新版本和 Chrome -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>
    <!-- 页面描述 -->
    <meta name="description" content="不超过150个字符"/>
    <!-- 页面关键词 -->
    <meta name="keywords" content=""/>
    <!-- 网页作者 -->
    <meta name="author" content="name, email@gmail.com"/>
    <!-- 搜索引擎抓取 -->
    <meta name="robots" content="index,follow"/>
    <!-- 为移动设备添加 viewport -->
    <meta name="viewport" content="initial-scale=1, maximum-scale=3, minimum-scale=1, user-scalable=no">
    <!-- `width=device-width` 会导致 iPhone 5 添加到主屏后以 WebApp 全屏模式打开页面时出现黑边 http://bigc.at/ios-webapp-viewport-meta.orz -->
 
    <!-- iOS 设备 begin -->
    <meta name="apple-mobile-web-app-title" content="标题">
    <!-- 添加到主屏后的标题（iOS 6 新增） -->
    <meta name="apple-mobile-web-app-capable" content="yes"/>
    <!-- 是否启用 WebApp 全屏模式，删除苹果默认的工具栏和菜单栏 -->
 
    <meta name="apple-itunes-app" content="app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL">
    <!-- 添加智能 App 广告条 Smart App Banner（iOS 6+ Safari） -->
    <meta name="apple-mobile-web-app-status-bar-style" content="black"/>
    <!-- 设置苹果工具栏颜色 -->
    <meta name="format-detection" content="telphone=no, email=no"/>
    <!-- 忽略页面中的数字识别为电话，忽略email识别 -->
    <!-- 启用360浏览器的极速模式(webkit) -->
    <meta name="renderer" content="webkit">
    <!-- 避免IE使用兼容模式 -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
    <meta name="HandheldFriendly" content="true">
    <!-- 微软的老式浏览器 -->
    <meta name="MobileOptimized" content="320">
    <!-- uc强制竖屏 -->
    <meta name="screen-orientation" content="portrait">
    <!-- QQ强制竖屏 -->
    <meta name="x5-orientation" content="portrait">
    <!-- UC强制全屏 -->
    <meta name="full-screen" content="yes">
    <!-- QQ强制全屏 -->
    <meta name="x5-fullscreen" content="true">
    <!-- UC应用模式 -->
    <meta name="browsermode" content="application">
    <!-- QQ应用模式 -->
    <meta name="x5-page-mode" content="app">
    <!-- windows phone 点击无高光 -->
    <meta name="msapplication-tap-highlight" content="no">
    <!-- iOS 图标 begin -->
    <link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-57x57-precomposed.png"/>
    <!-- iPhone 和 iTouch，默认 57x57 像素，必须有 -->
    <link rel="apple-touch-icon-precomposed" sizes="114x114" href="/apple-touch-icon-114x114-precomposed.png"/>
    <!-- Retina iPhone 和 Retina iTouch，114x114 像素，可以没有，但推荐有 -->
    <link rel="apple-touch-icon-precomposed" sizes="144x144" href="/apple-touch-icon-144x144-precomposed.png"/>
    <!-- Retina iPad，144x144 像素，可以没有，但推荐有 -->
    <!-- iOS 图标 end -->
 
    <!-- iOS 启动画面 begin -->
    <link rel="apple-touch-startup-image" sizes="768x1004" href="/splash-screen-768x1004.png"/>
    <!-- iPad 竖屏 768 x 1004（标准分辨率） -->
    <link rel="apple-touch-startup-image" sizes="1536x2008" href="/splash-screen-1536x2008.png"/>
    <!-- iPad 竖屏 1536x2008（Retina） -->
    <link rel="apple-touch-startup-image" sizes="1024x748" href="/Default-Portrait-1024x748.png"/>
    <!-- iPad 横屏 1024x748（标准分辨率） -->
    <link rel="apple-touch-startup-image" sizes="2048x1496" href="/splash-screen-2048x1496.png"/>
    <!-- iPad 横屏 2048x1496（Retina） -->
 
    <link rel="apple-touch-startup-image" href="/splash-screen-320x480.png"/>
    <!-- iPhone/iPod Touch 竖屏 320x480 (标准分辨率) -->
    <link rel="apple-touch-startup-image" sizes="640x960" href="/splash-screen-640x960.png"/>
    <!-- iPhone/iPod Touch 竖屏 640x960 (Retina) -->
    <link rel="apple-touch-startup-image" sizes="640x1136" href="/splash-screen-640x1136.png"/>
    <!-- iPhone 5/iPod Touch 5 竖屏 640x1136 (Retina) -->
    <!-- iOS 启动画面 end -->
 
    <!-- iOS 设备 end -->
    <meta name="msapplication-TileColor" content="#000"/>
    <!-- Windows 8 磁贴颜色 -->
    <meta name="msapplication-TileImage" content="icon.png"/>
    <!-- Windows 8 磁贴图标 -->
 
    <link rel="alternate" type="application/rss+xml" title="RSS" href="/rss.xml"/>
    <!-- 添加 RSS 订阅 -->
    <link rel="shortcut icon" type="image/ico" href="/favicon.ico"/>
    <!-- 添加 favicon icon -->
 
    <title>标题</title>
</head>

```

```
<style>
</style>
```

### hack IE
用于解决IE兼容性问题的特殊方案，只有满足条件，才会执行代码，否则视为注释。

```
<!-- hack IE -->
<!--[if lt IE 9]>
<script src="http://cdn.bootcss.com/html5shiv/3.7.2/html5shiv.min.js"></script>
<![endif]-->
```

```
</head>
```

## Body

```
<body>
```

>audio声音事件
[美团外卖商家中心](http://e.waimai.meituan.com/#/v2/order/pre)

```
<audio id="main_audio" preload="auto" volume="1.0" loop
data-type="waimai">
<source src="meituan://waimai.ogg" type="audio/ogg"/>
<source src="static/media/waimai.ogg" type="audio/ogg"/>
</audio>
<!-- 加入refundloop的判断 -->
<audio id="refund-audio" preload="auto" volume="1.0" 
data-type="one">
<source src="meituan://refund.ogg" type="audio/ogg"/>
<source src="static/media/refund.ogg" type="audio/ogg"/>
</audio>
```