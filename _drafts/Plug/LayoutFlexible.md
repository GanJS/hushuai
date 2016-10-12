title: 使用Flexible实现手淘H5页面的终端适配
date: 2016-04-02 14:11:20
description: 
categories:
- Plug
tags:
- Flexible
toc: true
author:
comments:
original:
permalink: 
---

　　**：**

<!-- more -->



[再来一波DEMO页](http://huodong.m.taobao.com/act/yibo.html "")
```

跳转到主要内容
w3cplus
CSS3MobileSassJavaScriptResponsive译文SVG工具标签云


你在这里
首页 » 博客 » Airen的博客
使用Flexible实现手淘H5页面的终端适配

作者：大漠 日期：2015-11-19 点击：48225
双11前端技术连载Layoutmobile

小编推荐：掘金是一个高质量的技术社区，从 ECMAScript 6 到 Vue.js，性能优化到开源类库，让你不错过前端开发的每一个技术干货。各大应用市场搜索「掘金」即可下载APP，技术干货尽在掌握中。
曾几何时为了兼容IE低版本浏览器而头痛，以为到Mobile时代可以跟这些麻烦说拜拜。可没想到到了移动时代，为了处理各终端的适配而乱了手脚。对于混迹各社区的偶，时常发现大家拿手机淘宝的H5页面做讨论——手淘的H5页面是如何实现多终端的适配？

那么趁此Amfe阿里无线前端团队双11技术连载之际，用一个实战案例来告诉大家，手淘的H5页面是如何实现多终端适配的，希望这篇文章对大家在Mobile的世界中能过得更轻松。

目标

拿一个双11的Mobile页面来做案例，比如你实现一个类似下图的一个H5页面：

Flexible实现手淘H5页面的终端适配

目标很清晰，就是做一个这样的H5页面。

DEMO

请用手机扫下面的二维码

DEMO

痛点

虽然H5的页面与PC的Web页面相比简单了不少，但让我们头痛的事情是要想尽办法让页面能适配众多不同的终端设备。看看下图你就会知道，这是多么痛苦的一件事情：

Flexible实现手淘H5页面的终端适配

点击这里查看更多终端设备的参数。

再来看看手淘H5要适配的终端设备数据：

Flexible实现手淘H5页面的终端适配

看到这些数据，是否死的心都有了，或者说为此捏了一把汗出来。

手淘团队适配协作模式

早期移动端开发，对于终端设备适配问题只属于Android系列，只不过很多设计师常常忽略Android适配问题，只出一套iOS平台设计稿。但随着iPhone6，iPhone6+的出现，从此终端适配问题不再是Android系列了，也从这个时候让移动端适配全面进入到“杂屏”时代。

Flexible实现手淘H5页面的终端适配

上图来自于paintcodeapp.com

为了应对这多么的终端设备，设计师和前端开发之间又应该采用什么协作模式？或许大家对此也非常感兴趣。

而整个手淘设计师和前端开发的适配协作基本思路是：

选择一种尺寸作为设计和开发基准
定义一套适配规则，自动适配剩下的两种尺寸(其实不仅这两种，你懂的)
特殊适配效果给出设计效果
还是上一张图吧，因为一图胜过千言万语：

Flexible实现手淘H5页面的终端适配

在此也不做更多的阐述。在手淘的设计师和前端开发协作过程中：手淘设计师常选择iPhone6作为基准设计尺寸，交付给前端的设计尺寸是按750px * 1334px为准(高度会随着内容多少而改变)。前端开发人员通过一套适配规则自动适配到其他的尺寸。

根据上面所说的，设计师给我们的设计图是一个750px * 1600px的页面：

Flexible实现手淘H5页面的终端适配

前端开发完成终端适配方案

拿到设计师给的设计图之后，剩下的事情是前端开发人员的事了。而手淘经过多年的摸索和实战，总结了一套移动端适配的方案——flexible方案。

这种方案具体在实际开发中如何使用，暂时先卖个关子，在继续详细的开发实施之前，我们要先了解一些基本概念。

一些基本概念

在进行具体实战之前，首先得了解下面这些基本概念(术语)：

视窗 viewport

简单的理解，viewport是严格等于浏览器的窗口。在桌面浏览器中，viewport就是浏览器窗口的宽度高度。但在移动端设备上就有点复杂。

移动端的viewport太窄，为了能更好为CSS布局服务，所以提供了两个viewport:虚拟的viewportvisualviewport和布局的viewportlayoutviewport。

George Cummins在Stack Overflow上对这两个基本概念做了详细的解释。

而事实上viewport是一个很复杂的知识点，上面的简单描述可能无法帮助你更好的理解viewport，而你又想对此做更深的了解，可以阅读PPK写的相关教程。

物理像素(physical pixel)

物理像素又被称为设备像素，他是显示设备中一个最微小的物理部件。每个像素可以根据操作系统设置自己的颜色和亮度。正是这些设备像素的微小距离欺骗了我们肉眼看到的图像效果。

Flexible实现手淘H5页面的终端适配

设备独立像素(density-independent pixel)

设备独立像素也称为密度无关像素，可以认为是计算机坐标系统中的一个点，这个点代表一个可以由程序使用的虚拟像素(比如说CSS像素)，然后由相关系统转换为物理像素。

CSS像素

CSS像素是一个抽像的单位，主要使用在浏览器上，用来精确度量Web页面上的内容。一般情况之下，CSS像素称为与设备无关的像素(device-independent pixel)，简称DIPs。

屏幕密度

屏幕密度是指一个设备表面上存在的像素数量，它通常以每英寸有多少像素来计算(PPI)。

设备像素比(device pixel ratio)

设备像素比简称为dpr，其定义了物理像素和设备独立像素的对应关系。它的值可以按下面的公式计算得到：

设备像素比 ＝ 物理像素 / 设备独立像素
在JavaScript中，可以通过window.devicePixelRatio获取到当前设备的dpr。而在CSS中，可以通过-webkit-device-pixel-ratio，-webkit-min-device-pixel-ratio和 -webkit-max-device-pixel-ratio进行媒体查询，对不同dpr的设备，做一些样式适配(这里只针对webkit内核的浏览器和webview)。

dip或dp,（device independent pixels，设备独立像素）与屏幕密度有关。dip可以用来辅助区分视网膜设备还是非视网膜设备。

缩合上述的几个概念，用一张图来解释：

Flexible实现手淘H5页面的终端适配

众所周知，iPhone6的设备宽度和高度为375pt * 667pt,可以理解为设备的独立像素；而其dpr为2，根据上面公式，我们可以很轻松得知其物理像素为750pt * 1334pt。

如下图所示，某元素的CSS样式：

width: 2px;
height: 2px；
在不同的屏幕上，CSS像素所呈现的物理尺寸是一致的，而不同的是CSS像素所对应的物理像素具数是不一致的。在普通屏幕下1个CSS像素对应1个物理像素，而在Retina屏幕下，1个CSS像素对应的却是4个物理像素。

有关于更多的介绍可以点击这里详细了解。

看到这里，你能感觉到，在移动端时代屏幕适配除了Layout之外，还要考虑到图片的适配，因为其直接影响到页面显示质量，对于如何实现图片适配，再此不做过多详细阐述。这里盗用了@南宮瑞揚根据mir.aculo.us翻译的一张信息图：

Flexible实现手淘H5页面的终端适配

meta标签

<meta>标签有很多种，而这里要着重说的是viewport的meta标签，其主要用来告诉浏览器如何规范的渲染Web页面，而你则需要告诉它视窗有多大。在开发移动端页面，我们需要设置meta标签如下：

<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
代码以显示网页的屏幕宽度定义了视窗宽度。网页的比例和最大比例被设置为100%。

留个悬念，因为后面的解决方案中需要重度依赖meta标签。

CSS单位rem

在W3C规范中是这样描述rem的:

font size of the root element.
简单的理解，rem就是相对于根元素<html>的font-size来做计算。而我们的方案中使用rem单位，是能轻易的根据<html>的font-size计算出元素的盒模型大小。而这个特色对我们来说是特别的有益处。

前端实现方案

了解了前面一些相关概念之后，接下来我们来看实际解决方案。在整个手淘团队，我们有一个名叫lib-flexible的库，而这个库就是用来解决H5页面终端适配的。

lib-flexible是什么？

lib-flexible是一个制作H5适配的开源库，可以点击这里下载相关文件，获取需要的JavaScript和CSS文件。

当然你可以直接使用阿里CDN：

<script src="http://g.tbcdn.cn/mtb/lib-flexible/{{version}}/??flexible_css.js,flexible.js"></script>
将代码中的{{version}}换成对应的版本号0.3.4。

使用方法

lib-flexible库的使用方法非常的简单，只需要在Web页面的<head></head>中添加对应的flexible_css.js,flexible.js文件：

第一种方法是将文件下载到你的项目中，然后通过相对路径添加:

<script src="build/flexible_css.debug.js"></script>
<script src="build/flexible.debug.js"></script>
或者直接加载阿里CDN的文件：

<script src="http://g.tbcdn.cn/mtb/lib-flexible/0.3.4/??flexible_css.js,flexible.js"></script>
另外强烈建议对JS做内联处理，在所有资源加载之前执行这个JS。执行这个JS后，会在<html>元素上增加一个data-dpr属性，以及一个font-size样式。JS会根据不同的设备添加不同的data-dpr值，比如说2或者3，同时会给html加上对应的font-size的值，比如说75px。

如此一来，页面中的元素，都可以通过rem单位来设置。他们会根据html元素的font-size值做相应的计算，从而实现屏幕的适配效果。

除此之外，在引入lib-flexible需要执行的JS之前，可以手动设置meta来控制dpr值，如：

<meta name="flexible" content="initial-dpr=2" />
其中initial-dpr会把dpr强制设置为给定的值。如果手动设置了dpr之后，不管设备是多少的dpr，都会强制认为其dpr是你设置的值。在此不建议手动强制设置dpr，因为在Flexible中，只对iOS设备进行dpr的判断，对于Android系列，始终认为其dpr为1。

if (!dpr && !scale) {
    var isAndroid = win.navigator.appVersion.match(/android/gi);
    var isIPhone = win.navigator.appVersion.match(/iphone/gi);
    var devicePixelRatio = win.devicePixelRatio;
    if (isIPhone) {
        // iOS下，对于2和3的屏，用2倍的方案，其余的用1倍方案
        if (devicePixelRatio >= 3 && (!dpr || dpr >= 3)) {                
            dpr = 3;
        } else if (devicePixelRatio >= 2 && (!dpr || dpr >= 2)){
            dpr = 2;
        } else {
            dpr = 1;
        }
    } else {
        // 其他设备下，仍旧使用1倍的方案
        dpr = 1;
    }
    scale = 1 / dpr;
}
flexible的实质

flexible实际上就是能过JS来动态改写meta标签，代码类似这样：

var metaEl = doc.createElement('meta');
var scale = isRetina ? 0.5:1;
metaEl.setAttribute('name', 'viewport');
metaEl.setAttribute('content', 'initial-scale=' + scale + ', maximum-scale=' + scale + ', minimum-scale=' + scale + ', user-scalable=no');
if (docEl.firstElementChild) {
    document.documentElement.firstElementChild.appendChild(metaEl);
} else {
    var wrap = doc.createElement('div');
    wrap.appendChild(metaEl);
    documen.write(wrap.innerHTML);
}
事实上他做了这几样事情：

动态改写<meta>标签
给<html>元素添加data-dpr属性，并且动态改写data-dpr的值
给<html>元素添加font-size属性，并且动态改写font-size的值
案例实战

了解Flexible相关的知识之后，咱们回到文章开头。我们的目标是制作一个适配各终端的H5页面。别的不多说，动手才能丰衣足食。

创建HTML模板

<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta content="yes" name="apple-mobile-web-app-capable">
        <meta content="yes" name="apple-touch-fullscreen">
        <meta content="telephone=no,email=no" name="format-detection">
        <script src="http://g.tbcdn.cn/mtb/lib-flexible/0.3.4/??flexible_css.js,flexible.js"></script>
        <link rel="apple-touch-icon" href="favicon.png">
        <link rel="Shortcut Icon" href="favicon.png" type="image/x-icon">
        <title>再来一波</title>
    </head>
    <body>
        <!-- 页面结构写在这里 -->
    </body>
</html>
正如前面所介绍的一样，首先加载了Flexible所需的配置：

<script src="http://g.tbcdn.cn/mtb/lib-flexible/0.3.4/??flexible_css.js,flexible.js"></script>
这个时候可以根据设计的图需求，在HTML文档的<body></body>中添加对应的HTML结构，比如：

<div class="item-section" data-repeat="sections">
    <div class="item-section_header">
        <h2><img src="{brannerImag}" alt=""></h2>
    </div>
    <ul>
        <li data-repeat="items" class="flag" role="link" href="{itemLink}">
            <a class="figure flag-item" href="{itemLink}">
                <img src="{imgSrc}" alt="">
            </a>
            <div class="figcaption flag-item">
                <div class="flag-title"><a href="{itemLink}" title="">{poductName}</a></div>
                <div class="flag-price"><span>双11价</span><strong>¥{price}</strong><small>({preferential})</small></div>
                <div class="flag-type">{activityType}</div>
                <a class="flag-btn" href="{shopLink}">{activeName}</a>
            </div>
        </li>
    </ul>
</div>
这仅是一个示例文档，大家可以根据自己风格写模板。

为了能更好的测试页面，给其配置一点假数据：

//define data
var pageData = {
    sections:[{
        "brannerImag":"http://xxx.cdn.com/B1PNLZKXXXXXaTXXXXXXXXXXXX-750-481.jpg",
        items:[{
            "itemLink": "##",
            "imgSrc": "https://placeimg.com/350/350/people/grayscale",
            "poductName":"Carter's1年式灰色长袖连体衣包脚爬服全棉鲸鱼男婴儿童装115G093",
            "price": "299.06",
            "preferential": "满400减100",
            "activityType": "1小时内热卖5885件",
            "shopLink":"##",
            "activeName": "马上抢！"
        }
            ....
        }]
    }]
}
接下来的工作就是美化工作了。在写具体样式之前，有几个点需要先了解一下。

把视觉稿中的px转换成rem

读到这里，大家应该都知道，我们接下来要做的事情，就是如何把视觉稿中的px转换成rem。在此花点时间解释一下。

首先，目前日常工作当中，视觉设计师给到前端开发人员手中的视觉稿尺寸一般是基于640px、750px以及1125px宽度为准。甚至为什么？大家应该懂的（考虑Retina屏）。

正如文章开头显示的示例设计稿，他就是一张以750px为基础设计的。那么问题来了，我们如何将设计稿中的各元素的px转换成rem。

Flexible实现手淘H5页面的终端适配

我厂的视觉设计师想得还是很周到的，会帮你把相关的信息在视觉稿上标注出来。

目前Flexible会将视觉稿分成100份（主要为了以后能更好的兼容vh和vw），而每一份被称为一个单位a。同时1rem单位被认定为10a。针对我们这份视觉稿可以计算出：

1a   = 7.5px
1rem = 75px 
那么我们这个示例的稿子就分成了10a，也就是整个宽度为10rem，<html>对应的font-size为75px：

Flexible实现手淘H5页面的终端适配

这样一来，对于视觉稿上的元素尺寸换算，只需要原始的px值除以rem基准值即可。例如此例视觉稿中的图片，其尺寸是176px * 176px,转换成为2.346667rem * 2.346667rem。

如何快速计算

在实际生产当中，如果每一次计算px转换rem，或许会觉得非常麻烦，或许直接影响大家平时的开发效率。为了能让大家更快进行转换，我们团队内的同学各施所长，为px转换rem写了各式各样的小工具。

CSSREM

CSSREM是一个CSS的px值转rem值的Sublime Text3自动完成插件。这个插件是由@正霖编写。先来看看插件的效果：

Flexible实现手淘H5页面的终端适配

有关于CSSREM如何安装、配置教程可以点击这里查阅。

CSS处理器

除了使用编辑器的插件之外，还可以使用CSS的处理器来帮助大家处理。比如说Sass、LESS以及PostCSS这样的处理器。我们简单来看两个示例。

Sass

使用Sass的同学，可以使用Sass的函数、混合宏这些功能来实现：

@function px2em($px, $base-font-size: 16px) {
    @if (unitless($px)) {
        @warn "Assuming #{$px} to be in pixels, attempting to convert it into pixels for you";
        @return px2em($px + 0px); // That may fail.
    } @else if (unit($px) == em) {
        @return $px;
    }
    @return ($px / $base-font-size) * 1em;
}
除了使用Sass函数外，还可以使用Sass的混合宏：

@mixin px2rem($property,$px-values,$baseline-px:16px,$support-for-ie:false){
    //Conver the baseline into rems
    $baseline-rem: $baseline-px / 1rem * 1;
    //Print the first line in pixel values
    @if $support-for-ie {
        #{$property}: $px-values;
    }
    //if there is only one (numeric) value, return the property/value line for it.
    @if type-of($px-values) == "number"{
        #{$property}: $px-values / $baseline-rem;
    }
    @else {
        //Create an empty list that we can dump values into
        $rem-values:();
        @each $value in $px-values{
            // If the value is zero or not a number, return it
            @if $value == 0 or type-of($value) != "number"{
                $rem-values: append($rem-values, $value / $baseline-rem);
            }
        }
        // Return the property and its list of converted values
        #{$property}: $rem-values;
    }
}
有关于更多的介绍，可以点击这里进行了解。

PostCSS(px2rem)

除了Sass这样的CSS处理器这外，我们团队的@颂奇同学还开发了一款npm的工具px2rem。安装好px2rem之后，可以在项目中直接使用。也可以使用PostCSS。使用PostCSS插件postcss-px2rem：

var gulp = require('gulp');
var postcss = require('gulp-postcss');
var px2rem = require('postcss-px2rem');

gulp.task('default', function() {
    var processors = [px2rem({remUnit: 75})];
    return gulp.src('./src/*.css')
        .pipe(postcss(processors))
        .pipe(gulp.dest('./dest'));
});
除了在Gulp中配置外，还可以使用其他的配置方式，详细的介绍可以点击这里进行了解。

配置完成之后，在实际使用时，你只要像下面这样使用：

.selector {
    width: 150px;
    height: 64px; /*px*/
    font-size: 28px; /*px*/
    border: 1px solid #ddd; /*no*/
}
px2rem处理之后将会变成：

.selector {
    width: 2rem;
    border: 1px solid #ddd;
}
[data-dpr="1"] .selector {
    height: 32px;
    font-size: 14px;
}
[data-dpr="2"] .selector {
    height: 64px;
    font-size: 28px;
}
[data-dpr="3"] .selector {
    height: 96px;
    font-size: 42px;
}
在整个开发中有了这些工具之后，完全不用担心px值转rem值影响开发效率。

字号不使用rem

前面大家都见证了如何使用rem来完成H5适配。那么文本又将如何处理适配。是不是也通过rem来做自动适配。

显然，我们在iPhone3G和iPhone4的Retina屏下面，希望看到的文本字号是相同的。也就是说，我们不希望文本在Retina屏幕下变小，另外，我们希望在大屏手机上看到更多文本，以及，现在绝大多数的字体文件都自带一些点阵尺寸，通常是16px和24px，所以我们不希望出现13px和15px这样的奇葩尺寸。

如此一来，就决定了在制作H5的页面中，rem并不适合用到段落文本上。所以在Flexible整个适配方案中，考虑文本还是使用px作为单位。只不过使用[data-dpr]属性来区分不同dpr下的文本字号大小。

div {
    width: 1rem; 
    height: 0.4rem;
    font-size: 12px; // 默认写上dpr为1的fontSize
}
[data-dpr="2"] div {
    font-size: 24px;
}
[data-dpr="3"] div {
    font-size: 36px;
}
为了能更好的利于开发，在实际开发中，我们可以定制一个font-dpr()这样的Sass混合宏：

@mixin font-dpr($font-size){
    font-size: $font-size;

    [data-dpr="2"] & {
        font-size: $font-size * 2;
    }

    [data-dpr="3"] & {
        font-size: $font-size * 3;
    }
}
有了这样的混合宏之后，在开发中可以直接这样使用：

@include font-dpr(16px);
当然这只是针对于描述性的文本，比如说段落文本。但有的时候文本的字号也需要分场景的，比如在项目中有一个slogan,业务方希望这个slogan能根据不同的终端适配。针对这样的场景，完全可以使用rem给slogan做计量单位。

CSS

本来想把这个页面的用到的CSS(或SCSS)贴出来，但考虑篇幅过长，而且这么简单的页面，我想大家也能轻而易举搞定。所以就省略了。权当是给大家留的一个作业吧，感兴趣的可以试试Flexible能否帮你快速完成H5页面终端适配。

效果

最后来看看真机上显示的效果吧。我截了两种设备下的效果：

iPhone4

Flexible实现手淘H5页面的终端适配

iPhone6+

Flexible实现手淘H5页面的终端适配

总结

其实H5适配的方案有很多种，网上有关于这方面的教程也非常的多。不管哪种方法，都有其自己的优势和劣势。而本文主要介绍的是如何使用Flexible这样的一库来完成H5页面的终端适配。为什么推荐使用Flexible库来做H5页面的终端设备适配呢？主要因为这个库在手淘已经使用了近一年，而且已达到了较为稳定的状态。除此之外，你不需要考虑如何对元素进行折算，可以根据对应的视觉稿，直接切入。

当然，如果您有更好的H5页面终端适配方案，欢迎在下面的评论中与我们一起分享。如果您在使用这个库时，碰到任何问题，都可以在Github给我们提Issue。我们团队会努力解决相关需Issues。

更新

同学们反馈需要一个在线演示的DEMO。那么花了点时间写了个demo，希望对有需要的同学有所帮助。友情提示：DEMO未经过所有设备测试，可能在部分设备上有细节上的差异

DEMO

请用手机扫下面的二维码

DEMO

更新【2016年01月13日】

首先，由衷的感谢@完颜 帮忙踩了这个坑，回想起iOS从7~8，从8~9，都踩过只至少一个坑，真的也是醉了。

手淘这边的flexible方案临时升级如下：

针对OS 9_3的UA，做临时处理，强制dpr为1，即scale也为1，虽然牺牲了这些版本上的高清方案，但是也只能这么处理了
这个版本不打算发布到CDN（也不发不到tnpm），所以大家更新的方式，最好手动复制代码内联到html中，具体代码可以点击这里下载

大漠
常用昵称“大漠”，W3CPlus创始人，目前就职于手淘。中国Drupal社区核心成员之一。对HTML5、CSS3和Sass等前端脚本语言有非常深入的认识和丰富的实践经验，尤其专注对CSS3的研究，是国内最早研究和使用CSS3技术的一批人。CSS3、Sass和Drupal中国布道者。2014年出版《图解CSS3：核心技术与案例实战》。
如需转载，烦请注明出处：http://www.w3cplus.com/mobile/lib-flexible-for-html5-layout.html

上一篇: SVG图案:通过图片、属性和嵌套构建更复杂的图案 | 下一篇: 如何创建SVG箭头和polymarker——`marker`元素
(^_^)打个赏喝个咖啡(^_^) (^_^)如果您觉得此文对您有帮助，打个赏喝个咖啡(^_^) (^_^)欢迎关注我们(^_^) 欢迎关注我们
 已喜欢16 人喜欢
被顶起来的评论
y
y
受益良多，大漠辛苦~写了个demo，大家可以参考下：http://www.cnblogs.com/jiujiaoyangkang/p/4998518.html
2015年11月26日回复顶(5)转发
张三
张三
现在的在750分辨率是54px，我应该除以54还是75啊，搞糊涂了
1月13日回复顶(1)转发
w3cplus
w3cplus
回复 张三: 你不需要在意他是多少，你做的时候只需要根据你的设计图尺寸去做，其他的事情交给客户端处理就OK了
1月13日回复顶(1)转发
最新最早最热
241条评论 42条新浪微博
树上有云
树上有云
顶，一直用的这个库，非常感谢。有的机型会遇到 计算出来的 html上的 font-size 出现误差 是不是 webView 设置的页面宽度的问题
2015年11月22日回复顶转发
黑白头像的悲哀
黑白头像的悲哀
传世好文 收了！
2015年11月22日回复顶转发
Jeremy
Jeremy
这是不是一维这在切图的时候设计图是多大的我切的图就是大的的？比如给我的container定宽750px?
2015年11月23日回复顶转发
w3cplus
w3cplus
并不要给容器定宽的，原理时把750px分成10等份，每个等份为1rem，也就是75px.那么其他元素按这个比例进行计算。
2015年11月23日回复顶转发
Jeremy
Jeremy
也就是我每个元素设置宽度XXrem是吧？也就是相当于外层容器宽度为10rem？ flexible.js会自动计算来确定这个基数是75px还是别的XXpx是吧？
2015年11月23日回复顶转发
w3cplus
w3cplus
制作的时候根据你的设计图，打个比方，你的设计图是750px的，那么html的font-size默认情况下是75px,这个时候也是你的制作时候的基数。比如页面上某个元素的大小是150px * 150px，那么它就width: 2rem;height:2rem。其他终端是多少，你不需要去管，flxeible.js会帮你解决。你只要制作的时候注意别换算错。当然元素高度根据实际情况，决定要不要显式的指定值。
2015年11月24日回复顶转发
ll
ll
那flexible.js怎么知道你设计稿大小，从而判断html的font-size大小
2015年11月25日回复顶转发
故事与你
故事与你
那请问我怎么才能设置字体的大小默认是75px呢
8月16日回复顶转发
Bonnie
Bonnie
能不能给一个完整的demo？文章里面的demo运行起来看不到效果（只能看出这个库做的三件事）。用了这个库，意思是不是单位都用rem, 比如图片176px 176px, 那么在"px_to_rem": 40 的情况下css是这样的： width：(176/40)4.4rem; height:4.4rem ?
2015年11月23日回复顶转发
w3cplus
w3cplus
如无特殊情况，width/height/padding/margin都使用`rem`，border-width和font-size使用px
2015年11月24日回复顶转发
黑白头像的悲哀
黑白头像的悲哀
哈哈 豁然开朗
2015年11月25日回复顶转发
黑白头像的悲哀
黑白头像的悲哀
不准啊 那个第一个转换px=》的插件计算有很大偏差啊
2015年11月25日回复顶转发
w3cplus
w3cplus
你确认你使用方法是正确的吗？这个插件我们团队已使用一年多时间了，并没有碰到你所说的计算有误差。
2015年11月25日回复顶转发
黑白头像的悲哀
黑白头像的悲哀
是我姿势不对，默认是750px的设计稿，1rem默认就是75px，我是拿了一张640宽度的设计稿来写，所以没对上，后来知道要改配置问价，把75改成64
1月7日回复顶转发
黑白头像的悲哀
黑白头像的悲哀
是我姿势不对，默认是750px的设计稿，1rem默认就是75px，我是拿了一张640宽度的设计稿来写，所以没对上，后来知道要改配置文件，把75改成64
1月7日回复顶转发
w3cplus
w3cplus
DEMO: http://huodong.m.taobao.com/act/yibo.html

yiboqr.png
2015年11月27日回复顶转发
子墨
子墨
谢谢大漠大神，这里简直就是前端技术的殿堂，打算买《图解CSS3：核心技术与案例实战》拜读啦。 [嘻嘻]
2015年11月27日回复顶转发
随意_
随意_
我有一点不懂 为什么除了ios设备外的dpr都为1 ~ 是因为安卓设备兼容问题? 我用了几款市场主流安卓机器看了没问题 并且去谷歌找了关于安卓这个的bug问题也找不到。求解
2015年11月25日回复顶转发
东方
东方
字体大小已设置成24px或者30px在谷歌浏览器测试没有问题，但是在真机测试发现会很大，这是为什么？具体怎么做可以教一下吗，谢谢了
2015年11月25日回复顶转发
w3cplus
w3cplus
你应该没有仔细看文章，文章都介绍了字号怎么设置
2015年11月25日回复顶转发
东方
东方
还是想问一下，如果设计图标题的文字大小是28px,段落的字体大小是20px,那我直接div {
font-size: 12px; // 默认写上dpr为1的fontSize
}
[data-dpr="2"] div {
font-size: 24px;
}
[data-dpr="3"] div {
font-size: 36px;
}这样写吗？ 还是写28px、26px 我太笨了，没理解到你的意思，希望和我再说说好吗？
2015年11月25日回复顶转发
w3cplus
w3cplus
根据你的设计稿的尺寸来。假设你的设计稿是2倍尺寸的，那么你的段落在设计稿中的字号是20px，在实际应用中应该是这样：

p {font-size: 10px;}

[data-dpr="2"] p {font-size: 20px;}

[data-dpr="3"] p {font-size: 30px;}

如果你是使用Sass这样的处理器，你完全可以这样使用：

p {@include font-dpr(10px)}

其实在文章中都有介绍，不知道是我介绍的不清楚呢？还是读者没有仔细阅读。
2015年11月25日回复顶转发
李金鹏
李金鹏
大漠老师，对于字体的问题我有两个疑问。
1.对于iphone 3G和4来说，3G中，1rem=32px，4中，1rem=64px，只不过4的初始缩放比例是0.5。在字体尺寸相同的情况（比如说0.24rem）下，（抛开字体最小尺寸的限制以及rem换算导致的奇葩尺寸问题），在4和在3G上边显示的字体应该是一样大的吧？
2.在相同dpr的情况下（例如大部分安卓），字体使用像素设置，例如 p{font-size:10px}，在不同屏幕大小的设备上字体显示的大小是一致的，但是页面其他部分的布局是rem来布局的，这样子字体部分的布局不会破坏掉其他的部分的布局吗？还有不同设备上采用相同大小的文字是合适的吗？
2月29日回复顶转发
Jay
Jay
你好,大漠大神。我在使用《Flexible实现手淘H5页面的终端适配 》时在小米的浏览器不能适配,请问是什么原因
2015年11月26日回复顶转发
w3cplus
w3cplus
你确认你使用的方法是对的？无码无真相。我们在小米手机上跑一切正常
2015年11月26日回复顶转发
冰宇
冰宇
跑着正常是因为小米默认的浏览器标识是iphone.调到其他标识就不太好用了。这个有没有好的解决办法
2015年12月10日回复顶转发
y
y
受益良多，大漠辛苦~写了个demo，大家可以参考下：http://www.cnblogs.com/jiujiaoyangkang/p/4998518.html
2015年11月26日回复顶(5)转发
w3cplus
w3cplus
谢谢分享
2015年11月26日回复顶转发
jnxag493
jnxag493
请问这个rem的计算插件怎么弄不会设置
1月4日回复顶转发
liu
liu
你的demo在IPAD上面有问题啊
3月15日回复顶转发
一瓶珍情
一瓶珍情
分析了下网易移动端的做法，他的设计稿应该是640x1136，然后font-size设为50px，这样px和rem就是1:1的关系，开发的时候转换就简单了。大漠老师，能评论下这种做法吗？
2015年11月27日回复顶转发
Andy
Andy
html的font-sze设置为640px，这样写的时候才能px和rem为1:1的吧？
4月6日回复顶转发
故事与你
故事与你
怎么才能设置字体默认是多少呀
8月16日回复顶转发
oldfu
oldfu
值得借鉴，这个周末好好研究一下
2015年11月27日回复顶转发
csywweb
csywweb
大漠老师，我有个问题，在字体适配的时候，使用根据dpr使用不同px的字体，那么我也可以根据dpr使用不同rem的字体是不是也可以呢
2015年11月27日回复顶转发
w3cplus
w3cplus
没有尝试过。按理说是可以，但不知道会不会影响。你可以测试一下。
2015年11月27日回复顶转发
虞
虞
用这种rem的布局，就不好用css sprites了吧，有什么好的解决方案吗
2015年11月27日回复顶转发
w3cplus
w3cplus
从我们团队的经验来说，我们的建议是请不要再使用CSS Sprites。有关于相关的介绍，可以看看下面两篇文章中有关于CSS Sprites的介绍：

https://github.com/amfe/article/issues/21
http://www.w3cplus.com/css/web-icons.html
2015年11月27日回复顶转发
jiaojiao085
jiaojiao085
大漠老师，我也碰到过这种问题，用flexible布局不好再用sprites.有什么解决办法么
3月23日回复顶转发
杨潮奔
杨潮奔
谢谢分享，就是字体设置的时候要注意，貌似一次只能针对一个元素设置，如[data-dpr="3"] p，写成[data-dpr="3"] p，div的话就不行了
2015年11月27日回复顶转发
w3cplus
w3cplus
你选择器的用法都没用对。这怎么说好呢？建议看看CSS选择器怎么用吧。
2015年11月27日回复顶转发
杨潮奔
杨潮奔
这个……，只是回复的时候输入的中文逗号。我实测真的会有问题。我用chrome调试测过了，dpr2的情况下，dpr3样式依旧会覆盖
2015年11月27日回复顶转发
杨潮奔
杨潮奔
不好意思，我知道错在哪了，让前辈见笑了。
2015年11月27日回复顶转发
杨潮奔
杨潮奔
不好意思，刚刚才发现到，应该写成[data-dpr="3"] p，[data-dpr="3"]div，让前辈见笑了
2015年11月27日回复顶转发
钟玲玉
钟玲玉
膝盖送上！大神！上班随便看了一遍，觉得受益匪浅，收藏了，准备细细研读！
2015年11月27日回复顶转发
天涯
天涯
请教一个问题：如果一个页面在PC下和移动端下的布局不同，该怎么弄，因为用了这个JS后，不能用这句了，否则data-dpr总是1，那这样的话，就没办法用media query了，像这种问题该怎么解决？
2015年11月27日回复顶转发
天涯
天涯
不能插代码吗？好吧，再发一次，网管把上面那个删掉吧。
请教一个问题：如果一个页面在PC下和移动端下的布局不同，该怎么弄，因为用了这个JS后，不能用meta content="width=device-width,initial-scale=1.0,user-scalable=yes,minimum-scale=1.0,maximum-scale=3.0" name="viewport"’这句了，否则data-dpr总是1，那这样的话，就没办法用media query了，像这种问题该怎么解决？’
2015年11月27日回复顶转发
w3cplus
w3cplus
我要是没估计错，你是想整Responsive Design吧。那样的话这个库就不能用了，这个是针对于移动端的布局。
2015年11月27日回复顶转发
轰轰轰
轰轰轰
大神 请问下我看手淘的网站 他们的div里有一个data-dpr的属性 修改谷歌测试工具的dpr刷新他会跟着变 这个是什么来的？
还有就是px2rem 和 PostCSS 这两个是不是用来转换rem的 具体怎么使用 我一直没做对
2015年12月2日回复顶转发
w3cplus
w3cplus
data-dpr是用下设置设备dpr值，这个值是flexible.js根据设备判断出来的。px2rem和PostCSS的关系，PostCSS有一个插件叫px2rem，那么你的环境中有PostCSS的话，你可以按照px2rem的api写你的代码，编译之后会自动转译出来需要的rem。
2015年12月2日回复顶转发
轰轰轰
轰轰轰
px2rem 是要通过npm来安装吗 我在项目中始终用不上这个插件
2015年12月2日回复顶转发
w3cplus
w3cplus
对应的链接都讲的非常清楚。这种操作按作官方提供的api，不是很好的操作吗？
2015年12月2日回复顶转发
段亮自媒体博客
段亮自媒体博客
大漠老师，请教个问题。如果我的设计稿是640的话，那么兑换比例，是不是还是按照原有的宽度/75就可以了？JS可以自动计算匹配吗？
2015年12月2日回复顶转发
w3cplus
w3cplus
你作的时候把html的font-size:64px就行了，flexible.js会根据设备自动匹配的。
2015年12月2日回复顶转发
段亮自媒体博客
段亮自媒体博客
flexible.js难道不是根据设备进行自动匹配的么？我先说下我的理解：按照您文章说的，假设效果图是750的标准来的话，我有一张banner图的实际宽度为581px居中显示。那么，按照兑换比例的话，大约就是7.7466rem.那么在iphone6确实能正常匹配，在iphone5、4以及6plus却不能正常匹配。求解释下。
2015年12月2日回复顶转发
w3cplus
w3cplus
你确认要加载的都加载了，我至今没有碰到你所说的这种现象。flexible.js是会根据设备自动匹配的。
2015年12月2日回复顶转发
段亮自媒体博客
段亮自媒体博客
嗯，原因找到了，谢谢，是因为样式没控制到图片的原因，造成的！
2015年12月2日回复顶转发
随便吧
随便吧
请问下这个750的设计稿和flexible， 只为手机端设计的么？ipad端可以用么？
2015年12月4日回复顶转发
w3cplus
w3cplus
iPad不适用这个库
2015年12月5日回复顶转发
黑眼圈
黑眼圈
我也发现了，ipad上都很小，明显不够，那么请问对于ipad你们是怎么适配的呢？单独写么还是有另外的库？
2015年12月10日回复顶转发
Leon
Leon
大神，这个库怎么看起来就是通过rem和css把距离，字体等放大了若干倍（2倍，3倍），然后再通过viewport把页面缩小相应的倍数？怎么再我看来什么都没做呢？这里没理解清楚，被绕进去了，能帮忙解释下么？
2015年12月11日回复顶(1)转发
w3cplus
w3cplus
文章中已附实例，自己动手做两个试试
2015年12月11日回复顶转发
Leon
Leon
我好像明白了，字体放大是按屏幕尺寸来的，各个设备的viewport是不一样的，所以放大是按viewport比例放大的，缩小是按dpr缩小的。所以是不一样的
2015年12月11日回复顶转发
unclefeng
unclefeng
第一，我觉得通过viewport的scale的意义是虽然页面缩小，但呈现的内容增大的。事实这参数，让我们看到的范围增加，就像放大镜一样。
第二，那么放大宽度范围的原因是为什么了？因为要文档宽度和物理像素对等，这样才能有更好的图片显示效果
第三，当文档宽度增加，最好适配，使所有的内容跟随文档内容一起放缩，rem就是实现这样的功能，他是一个相对单位，所有的值是相对于font-size计算的，所以动态计算即可。
第四，以上纯属游客的浅显的想法，希望对你有用。
1月5日回复顶转发
光明领域2012
光明领域2012
大漠老师,使用chrome模拟iphone ,dpr=2的时候,同样大小的字体,同一个页面上表现出来的大小不一致是个什么情况....
模拟android,dpr=1的时候是正常的

64cfe490gw1eyvk7en7jrj20qe07w0uy.jpg64cfe490gw1eyvk7drgv3j20qu0fwaey.jpg64cfe490gw1eyvk7eenkfj20uw0inafh.jpg

dpr=2, initial-scale=0.5 有 [data-dpr="2"] .info {font-size: 24px;}实际显示是不是应该还是12px的大小吧,但是这里这里 24px的比28px的还要大......

64cfe490gw1eyvk7e15glj20ph0gwdl3.jpg

同一个地方的,我把 display: inline-block; 去掉之后字体也变大了.......
2015年12月11日回复顶转发
麽麽12345
麽麽12345
我也遇到这个问题了，非得写上display:inline-block;去掉之后字体打下就显示不正常了
2月3日回复顶转发
camo
camo
我也遇到这个问题了，你是如何解决的？
3月22日回复顶转发
yler
yler
我也遇到这个问题了，你的解决方法是什么啊
6月1日回复顶转发
崩坏的信仰
崩坏的信仰
= = 我遇到这个问题，但是我用盆友的iphone实际测试了一下 发现没有这个问题
8月8日回复顶转发
四月
四月
我也碰到这个问题了，好像新版本的android系统和IOS他这个方法都不适用、
8月18日回复顶转发
Leon
Leon
请问如果是android的高分别率的屏，比如某个android设备的dpr为2. 这种情况下flexible对viewport进行处理，岂不是用rem写的size会变得很大。这个这面会变形啊。这个是怎么处理的？
2015年12月11日回复顶转发
w3cplus
w3cplus
所有android设备都强制设置了dpr值为1，font-size设置了一个最佳实验值54px
3月1日回复顶转发
自由人
自由人
为什么Android要强制设置dpr值为1
3月2日回复顶转发
w3cplus
w3cplus
可以先自己了解一下Android下的dpr，他不只是有1,2,3还有1.5之类的
3月2日回复顶转发
yler
yler
大漠老师，android上强制dpr为1后，那么在dpr大于1的机器上，1px的边框就会显示的比较粗了，这个有什么好的解决方法吗
6月13日回复顶转发
江潮
江潮
终端适配
2015年12月14日回复顶转发
jnxag493
jnxag493
CSSREM怎么下载这个插件，全是英文看不懂啊、、、、
2015年12月22日回复顶转发
w3cplus
w3cplus
那我也帮不了你了
2015年12月22日回复顶转发
jnxag493
jnxag493
额。。。。能不能善良点。。求指导！！！
2015年12月24日回复顶转发
jnxag493
jnxag493
下载这个插件是不是需要注册交钱啊？？？
2015年12月24日回复顶转发
jnxag493
jnxag493
我弄好啦，谢啦
2015年12月24日回复顶转发
liu
liu
大漠老师为什么我下载好了却没有反应呢？A3F13PL(]IOL)MG(BK]M_3H.png
3月16日回复顶转发
Bug
Bug
cssRem是 sublime text 的一个插件，你先看看怎么sublime 插件安装教程，安装成功后在配置文件里设置默认的基准值，之后就是爽歪歪的编码了！
1月11日回复顶转发
晏丽君
晏丽君
请问下：在三星GalaxyS5下 宽度设置成10rem时页面会左右移动是什么原因？其他机型没有这个问题。
2015年12月24日回复顶转发
w3cplus
w3cplus
你在最外面设置了width: 10rem的容器上加上一个margin-left: auto; margin-right: auto看看
2015年12月24日回复顶转发
四月
四月
三星的我也碰到这个问题，凡是通过缩放来处理的页面，都有这种问题，其它要做精细一些，最好不要用这种缩放的方式来处理
PNG图片也是，会呈现变化的锯齿状
8月17日回复顶转发
晏丽君
晏丽君
请问下：在三星GalaxyS5下设置了宽度10rem后会出现页面左右移动的问题，怎么解决好呢？其他机型没有这个问题。
2015年12月24日回复顶转发
jnxag493
jnxag493
请问大漠老师这个计算的px2rem-master是直接加这个代码么？（）我不会用这个插件？？不知道该写什么才能用。下载下来之后里面有好多文件的js
2015年12月24日回复顶转发
许大伟
许大伟
漠大大，移动端使用图片 你的建议是像列子中的img标签写入 还是通过background呢
2015年12月31日回复顶转发
w3cplus
w3cplus
这得根据实际情况呀，并不是所有图片都是用background。
1月1日回复顶转发
蓝格调
蓝格调
很好用 安卓和IOS 唯一不同的是 li 上面的 margin-bottom: 1px; 不知道淘宝对于1像素的边框有什么更好的解决方案 [嘻嘻]
1月4日回复顶转发
秋明的思念
秋明的思念
想问下，那个cssrem怎么支持scss文件呢?刚修改了配置，貌似没生效
1月6日回复顶转发
秋明的思念
秋明的思念
scss怎么使用cssrem那个插件呢？安装之后，发现用不了哦，有办法解决吗
1月6日回复顶转发
w3cplus
w3cplus
那个是sublime text3的插件，在SCSS中使用，你可以直接使用SCSS的function或者mixin
1月7日回复顶转发
波波
波波
又是一个坑，。简单问题复杂化
1月7日回复顶转发
allen
allen
https://www.npmjs.com/package/postcss-px2rem
现在最新版本会把border也转成rem？1px 会转成很小的rem，android上都看不到
1月9日回复顶转发
w3cplus
w3cplus
这个插件在编码时，你可以后面加一个注释，让border的px不转换成rem。请君仔细看看他的使用文档。
1月9日回复顶转发
allen
allen
大哥每个地方都要写上 /*no*/吗，这样好麻烦阿 而且我引入了一些css框架，有没有方便的方式，能够直接把所有border不进行rem转换
1月9日回复顶转发
allen
allen
我的留言消失咯，我想全局的使border不转换怎么办呢
1月9日回复顶转发
w3cplus
w3cplus
不用px2rem的插件，这样就可以不转换了，你可以用CSSREM（sublime text插件）或者你使用Sass的function。方法好多种呀
1月9日回复顶转发
Allen丶Dong
Allen丶Dong
额 其实这样要改的地方感觉更多，好的 我知道拉!
1月9日回复顶转发
Allen丶Dong
Allen丶Dong
大神 子留言老是被删掉不知道怎么了，我想全局的使border不转换有办法吗
1月9日回复顶转发
秋明的思念
秋明的思念
目前Flexible会将视觉稿分成100份（主要为了以后能更好的兼容vh和vw） 能具体解释下这里的原因吗？
1月11日回复顶转发
w3cplus
w3cplus
因为1vw 就是viewport宽度除以100
3月1日回复顶转发
轰轰轰
轰轰轰
请问下brackets这个编辑器有没有类似cssrem这个自动换算的插件?
1月12日回复顶转发
w3cplus
w3cplus
没有，只有sublime text3
1月12日回复顶转发
张三
张三
为什么我调用后在750下面是54px而不是75px呢
1月13日回复顶(1)转发
ulove
ulove
肯定是哪个基准设错了。
1月13日回复顶(1)转发
w3cplus
w3cplus
你不需要在意他是多少，你做的时候只需要根据你的设计图尺寸去做，其他的事情交给客户端处理就OK了
1月13日回复顶(1)转发
张三
张三
按你上面说的750px的稿应该html设置的是75px，现在变成54px了，那转px的时候应该除以75还是54呀
1月13日回复顶转发
w3cplus
w3cplus
你在编码时，你根据你的设计图来定，如果你的设计图是750px的，那按75px来计算；如果你的设计是640的，你按64px来计算。其他的你就可以不理会了。
1月13日回复顶转发
张三
张三
那应该除以75还是54
1月13日回复顶转发
故事与你
故事与你
我是不是引用JS少了什么，为什么不会自己转换成REM单位的？
8月16日回复顶转发
ulove
ulove
大漠哥，这个列表右边的宽度是否有问题呀？我自己写出来的却是6.9rem，而不是133.3rem，求解~
602cf753jw1ezxwdzvfdvj20x40mfjz0.jpg
1月13日回复顶转发
ulove
ulove
图上半部分为你的demo
1月13日回复顶转发
w3cplus
w3cplus
右边其实你没有必要定宽度的。就算定宽度，你按你编码中的定了，浏览器或者说js是不会对你的代码做处理的。
1月13日回复顶转发
麽麽12345
麽麽12345
我也遇到这个问题了，非得写上display:inline-block;去掉之后字体打下就显示不正常了
2月3日回复顶转发
yler
yler
我也遇到字体变大这个问题了，还有别的解决方法吗
6月1日回复顶转发
y y
y y
Font Boosting 搜索下
字体设置max-height: 9999px;可以解决此问题
6月2日回复顶转发
yler
yler
嗯嗯，在后面的评论中找到了原因和答案，写了max-height:100%解决了该问题
6月13日回复顶转发
小呗就是我
小呗就是我
这个叼，学习了
1月13日回复顶转发
张三
张三
现在的在750分辨率是54px，我应该除以54还是75啊，搞糊涂了
1月13日回复顶(1)转发
w3cplus
w3cplus
你计算是按75计算呀，教程都说得很清楚的。
3月1日回复顶转发
11111
11111
应该是54
4月27日回复顶转发
FreeRide_Joe
FreeRide_Joe
10rem=750px，1px=10/750rem，54px=10/750*54rem 。
6月15日回复顶转发
孙莎莎
孙莎莎
mark，受益匪浅
1月15日回复顶转发
僦讓莪執蒾吥誨
僦讓莪執蒾吥誨
大神，1rem=75px; 这个值是不变的么？宽度为750px时 1rem=75px;如果页面宽度为900px 这个比例也是1rem=75px吗？
1月18日回复顶转发
w3cplus
w3cplus
移动端的设计稿一般是640px/750px/1125px,那么转换对应的基数是64px/75px/112.5px,建议先将1125转换成750
1月18日回复顶转发
尼古拉斯~颜鸿飞
尼古拉斯~颜鸿飞
这个js也会根据 dpr 给 body设置字体大小，这个是所有默认的12px？今天做的东西有张640的设计稿里段落字体是18px，难道我写成p{font-size：9px} ？不是最小不能小于12px吗？
1月18日回复顶转发
僦讓莪執蒾吥誨
僦讓莪執蒾吥誨
Flexible会将视觉稿分成100份，可不可以这么理解，宽度为1125px，比例就是1rem=112.5px？
Fexible是否使用pc端的网站？也需要转换成750吗？
1月19日回复顶转发
w3cplus
w3cplus
是这种意思，但不适合PC端网站。
1月19日回复顶转发
僦讓莪執蒾吥誨
僦讓莪執蒾吥誨
谢谢大漠老是，我去试过了，确实不太理想的
1月19日回复顶转发
僦讓莪執蒾吥誨
僦讓莪執蒾吥誨
mark,已经在用了，感谢楼主
1月18日回复顶转发
四次方_产品设计
四次方_产品设计
是不是引入这个框架媒体查询就没有用了？@media screen and (width:320px) and (height:480px) {
1月26日回复顶转发
Azhun
Azhun
mark
1月27日回复顶转发
ヤ一枚夲蛋o○
ヤ一枚夲蛋o○
我的是win7系统，安装了sublime text 3后安装cssrem时发现并没有介绍的Sublime Text -> Preferences -> Browse Packages..文件路径，我换了好几个版本安装都是这样，像这样的是不是就没法安装cssrem了？
1月29日回复顶转发
w3cplus
w3cplus
看看这个吧：http://www.w3cplus.com/blog/692.html 不过sublime text3的package control安装不太一样，你可以先搜索一下如何安装sublime text3的package control先。这些操作都是最基本的，而且在网上相关的资料也很多。建议先google一下
1月29日回复顶转发
梦想
梦想
大神，我把安装包丢进去了，重启了，还是没有提示啊，帮帮忙，谢谢
3月3日回复顶转发
一紧张就流汗
一紧张就流汗
Sublime Text -> Preferences -> Browse Packages..这个文件路径在sublime软件里面打开，在上面的菜单栏目里面，你把下载好的cssrem文件丢进去就行了。
1月30日回复顶转发
梦想
梦想
丢进去了没反应啊，怎么样才会有提示
3月3日回复顶转发
htne
htne
大神 把下载的包丢进去了啊 还是没有提示 是怎么回事呀？
5月6日回复顶转发
喵咪控
喵咪控
[阴险]
1月30日回复顶转发
喵咪控
喵咪控
我做适配的时候就用的css3的媒体查询做的适配 感觉也没出现过大问题呢。 [思考]
1月30日回复顶转发
只修电脑
只修电脑
说句不合时宜的话 直接用vw不就行了 什么 你不会兼容 自己去想吧 滑稽
1月31日回复顶转发
发的身份
发的身份
不知道我理解对不对，既然已经用了rem 为什么不直接按1倍的算，2倍3倍 变换的只是跟字体的大小。最终还是要缩小 0.5 0.3
2月3日回复顶转发
1 2 3
帐号管理世平阜康
世平阜康

说点什么吧…
 分享到:
发布
W3CPLUS正在使用多说

请输入关键字
搜索



GitHub


Airen
@W3cplus
⚲ China
807
Followers
113
Following
3
Repositories
Top repositories
jsStudy
HTML
★46
article
Unknown
★2
mobileTech
Unknown
★0

Follow
Last active: 15 day(s) ago
关注我们



合作网站

JavaScript学习案例
墨鱼前端培训
HTML5梦工场
Sass入门指南
CSS解决方案
W3ctech
Drupal中国
友情链接

在线图片压缩
java源代码学习
墨鱼前端开发培训
猪八戒网
HTML5梦工场
PHP教程
程序员客栈
imweb 前端社区
前端笔记
Drupal大学
关于我们

W3cplus
W3cplus是一个致力于推广国内前端行业的技术博客。它以探索为己任，不断活跃在行业技术最前沿，努力提供高质量前端技术博文；其文章范围广泛，主要以CSS3、HTML5、Sass、Mobile和各类DEMO为主。

W3cplus具有一支强大的团队，提供长期的前端项目外包，Drupal建站，Drupal主题制作服务，以及提供企业广告展示与招聘发布，有需要的请联系：QQ:81059347，E-mail:w3cplus@hotmail.com

关于站长

大漠

常用昵称“大漠”，W3CPlus创始人，目前就职于淘宝。中国Drupal社区核心成员之一。对HTML5、CSS3和Sass等前端脚本语言有非常深入的认识和丰富的实践经验，尤其专注对CSS3、Sass和Mobile的研究，是国内最早研究和使用CSS3和Sass技术的一批人。CSS3、Sass和Drupal中国布道者。2014年出版《图解CSS3：核心技术与案例实战》。

github weibo facebook google twitter linkedin
 

我的作品

图解CSS3
本书是国内著名的Web前端专家历时2载的心血之作，根据最新的CSS3撰写，融入了作者在CSS领域多年的使用经验，旨在将本书打造成为CSS3领域最权威和实用的专业著作，供没有经验的读者系统学习，供有经验的读者参考备查。

本书理论知识系统全面，详细讲解了选择器、伸缩布局盒模型、渐变、过渡、动画等主题下涵盖的所有CSS3新特性。

湘ICP备13003850号-12，版权所有 衡阳瑞思信息技术有限公司 © 2011-2016 W3CPLUS，感谢Drupal开源技术。感谢七牛云存储提供静态资源空间。
返回顶部
```