title: WEB前端面试题整理
date: 2015-12-25 18:29:00
description: 
categories:
- Interview
tags:
- Test
toc: true
author:
comments:
original:
permalink: 
---

　　**自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why
<!-- more -->
[]()

1. 列举你工作中遇到的IE6 BUG，谈谈解决方案。

	1.IE6下图片下有空隙产生
	解决这个BUG的方法也有很多,可以是改变html的排版,或者设置img 为display:block 或者设置vertical-align 属性为 vertical-align:top | bottom |middle |text-bottom 都可以解决.
	2.IE捉迷藏的问题 
	当div应用复杂的时候每个栏中又有一些链接，DIV等这个时候容易发生捉迷藏的问题。 
	有些内容显示不出来，当鼠标选择这个区域是发现内容确实在页面。解决办法：对#layout使用line-height属性或者给#layout使用固定高和宽。页面结构尽量简单。

	3.DIV浮动IE文本产生3象素的bug 
	　左边对象浮动，右边采用外补丁的左边距来定位，右边对象内的文本会离左边有3px的间距. 
	#box{ float:left; width:800px;} 
	#left{ float:left; width:50%;} 
	#right{ width:50%;} 
	*html #left{ margin-right:-3px; //这句是关键} 
	负margin技术及其应用

	在margin所有的实际应用中，负margin技术是我学习css路上最重要一课之一，许多高

	级应用和页面上的疑难杂症都可以用负margin技术来实现。
	IE6中双边距Bug：
	发生场合：当给父元素内第一个浮动元素设置margin-left（元素float:left）或margin-

	right（元素float:right）时margin加倍。

	解决方法：是给浮动元素加上display:inline;CSS属性；或者用padding-left代替

	margin-left。

	原理分析：块级对象默认的display属性值是block，当设置了浮动的同时，还设置了它

	的外边距就会出现这种情况。也许你会问：“为什么之后的对象和第一个对象之间就不

	存在双倍边距的Bug”？因为浮动都有其相对应的对象，只有相对于其父对象的浮动对象

	才会出现这样的问题。第一个对象是相对父对象的，而之后对象是相对第一个对象的，

	所以之后对象在设置后不会出现问题。为什么display:inline可以解决这个双边距bug，

	首先是inline元素或inline-block元素是不存在双边距问题的。然后，float:left等浮动属

	性可以让inline元素haslayout，会让inline元素表现得跟inline-block元素的特性一样，

	支持高宽，垂直margin和padding等，所以div class的所有样式可以用在这个display

	inline的元素上。
	IE6中浮动元素3px间隔Bug：

	发生场合：发生在一个元素浮动，然后一个不浮动的元素自然上浮与之靠近会出现的

	3px的bug。

	解决方法：右边元素也一起浮动；或者为右边元素添加IE6 Hack _margin-left:-3px;

	从而消除3px间距。

	原理分析：IE6浏览器缺陷Bug。
	IE6/7负margin隐藏Bug：

	发生场合：当给一个有hasLayout的父元素内的非hasLayout元素设置负margin时，超

	出父元素部分不可见。

	解决方法：去掉父元素的hasLayout；或者赋hasLayout给子元素,并添加

	position:relative;

	原理分析：IE6/7独有的hasLayout产生问题。
	IE6/7下ul/ol标记消失bug：

	发生场合：当ul/ol触发了haslayout并且是在ul/ol上写margin-left，前面默认的ul/ol标

	记会消失。

	解决方法：给li设置margin-left，而不是给ul/ol设置margin-left。

	原理分析：IE6/7浏览器Bug

	IE6/7下margin与absolute元素重叠bug：

	发生场合：双栏自适应布局中，左侧元素absolute绝对定位，右侧的margin撑开距离定

	位。在IE6/7下左侧应用了absolute属性的块级元素与右边的自适应的文字内容重叠。

	解决方法：把左侧块级元素更改为内联元素，比如把div更换为span。

	原理分析：这是由于IE6/IE7浏览器将inline水平标签元素和block水平的标签元素没有

	加以区分一视同仁渲染了。属于IE6/7浏览器渲染Bug。

	IE6/7/8下auto margin居中bug：

	发生场合：给block元素设置margin auto无法居中

	解决方法：出现这种bug的原因通常是没有Doctype，然后触发了ie的quirks mode，

	加上Doctype声明就可以了。在《打败IE的葵花宝典》里给出的方法是给block元素添加

	一个width能够解决，但根据本人亲测，加with此种方法是无效的，如果没有Doctype

	即使给元素添加width也无法让block元素居中。

	原理分析：缺少Doctype声明。

	IE8下input[button | submit] 设置margin:auto无法居中

	发生场合：ie8下，如果给像button这样的标签（如button input[type="button"]

	input[type="submit"]）设置{ display: block; margin:0 auto; }如果不设置宽度的

	话无法居中。

	解决方法：可以给为input加上宽度

	原理分析：IE8浏览器Bug。


	IE8百分比padding垂直margin bug：

	发生场合：当父元素设置了百分比的padding，子元素有垂直的margin的时候，就好像

	父元素被设置了margin一样。

	解决方法：给父元素加一个overflow:hidden/auto。

	原理分析：IE8浏览器Bug。
	Firefox浏览器中无法撑开高度问题的解决方法。 [解决bug的方法和对浏览器兼容性的技能

	标准浏览器中固定高度值的容器是不会象IE6里那样被撑开的,那我又想固定高度,又想能被撑开需要怎样设置呢？办法就是去掉height设置min-height:200px; 这里为了照顾不认识min-height的IE6 可以这样定义:

	{
	height:auto!important;
	height:200px;
	min-height:200px;
	}
	IE6 盒子模型中，盒子的尺寸包含了 内容区，padding， border 和 margin 这四个部分，而 W3C 的盒子模型中，盒子的尺寸只包含内容区，padding，border 和 margin 被排除在盒子尺寸之外。
	为什么 IE6 的盒子模型更合理
	在现实世界中，我们描述一个物理盒子的时候，如果谈到尺寸，是不会只计算其盛放的物体的尺寸的，我们还会算上空隙与盒体本身。拿集装箱装箱为例，我们有 100 只花瓶，每只花瓶用1个纸盒包装，为了防止花瓶破碎，我们在花瓶周围塞上泡沫，这相当于 padding，纸盒的外围纸板相当于 border，在装集装箱的时候，为了防止纸盒之间相互碰撞，纸盒之间塞上稻草，这相当于 margin，很显然，我们向货运公司报告我们货物尺寸的时候，是要将整个纸盒的尺寸，连同纸盒之间需要塞稻草的空隙都告诉他们的，倘若只报告花瓶的尺寸，货运公司是没有办法装箱的。
	再举一个例子，假若我们有一面墙，要在上面挂10幅油画，油画是用相框裱糊的，相框的边框相当于 border，油画和边框之间的距离相当于 padding，相框之间的间隔相当于 margin，这个例子和 Web 布局设计已经很接近了，对任何人来说，使用 IE6 的盒子模型，将整个相框，包括油画当做一个整体更容易布局，当你知道了整个相框的尺寸后，不必再去考虑 padding, border, margin 这个因素的影响，每个相框就是一个整体，至于 padding, border 与 margin，这是浏览器自己事，不需要设计者去关心。
	在具体的 Web 设计中
	在具体 Web 设计中，尤其牵扯到复杂网格布局的时候，IE6 的盒子模型更容易控制，我们不妨看看以下几个设计场景。
	1. 面板式界面设计
	页面上包含几个面板，比如一个登录面板，一个最新新闻面板，一个投票面板，这类设计典型的做法是，用背景图的方式，首先逐个设计出这些面板的外观图，将需要用具体内容替换的地方空着，这些面板，无非就是一些使用面板外观图片做背景图的盒子，然后，在这些盒子里面，放上具体的内容，使用 padding 控制内容的摆放位置，使用 margin 调整面板本身的摆放位置，由于面板的尺寸是固定的，我们依此确立了盒子的尺寸之后，就无需再关心尺寸问题，然后，不论你怎样调整 padding 和 margin，都不会影响面板本身的结构。这是 IE6 盒子模型。
	而在 W3C 的盒子模型中，调整 padding 和 margin ，都会影响盒子的尺寸，你在调整内容摆放位置的同时，极有可能打乱面板本身的结构。
	2. 百分比级尺寸 + 像素级边界问题
	W3C 盒子模型在设计中最让人头疼的是，假如你有一个不确定宽度的容器，想在里面放置两个同样大小的盒子，最合理的的做法当时是设置每个盒子的宽度为 50%，这样，不管你的容器宽度为多大，这两个盒子总能自动适应这个宽度，然而，前提是你不要设置任何 padding 或 border，而，现实中，为了防止两个盒子中的内容互相挨得太近，你肯定要设置 padding，一旦设置了 padding，就会发现你的容器被撑破了。
	当然你会说，每个盒子的宽度不要设为 50%，可以设为 45%，然后为每个盒子再加一个 5% 的 padding，这是一个解决办法，但我们在设计中经常有这样的习惯，虽然一段内容的宽度可能不确定，但我们总喜欢它拥有固定 padding，我们并不希望 padding 自动适应，况且，在很多时候，我们希望为一个自适应宽度的盒子，设置一个 1 像素的 border，在这种情形，W3C 盒子模型将陷入困境。
	而遇到这种情形，IE6 盒子模型不需要任何周折，你只管将每个盒子的宽度设置为 50%，它们会自动适应容器的宽度，然后，不管你你怎样设置 padding 和 border，都不会撑破你的容器。
	W3C 在盒子模型上迷途知返
	虽然 W3C 永远都不会承认，但他们显然意识到了这个问题，重新定义盒子模型是不可能了，所以，在 CSS3 中，我们看到了下面这个属性：
	box-sizing
	box-sizing 有两个可选值，一个是默认的 content-box 一个是 border-box，选用后者，盒子模型将按 IE6 的方式进行处理。
1. 如何用CSS分别单独定义IE6、7、8的width属性。

	```
	所有浏览器 通用
	height: 100px;
	IE6 专用
	_height: 100px;
	IE6 专用
	*height: 100px;
	IE7 专用
	*+height: 100px;
	IE7、FF 共用
	height: 100px !important;
	```

1. CSS中哪些属性可以同父元素继承。

	继承：(X)HTML元素可以从其父元素那里继承部分CSS属性，即使当前元素并没有定义该属性
	Color;font-size;

1. 你如何理解HTML结构的语意化。



1. 去掉或样式丢失的时候能让页面呈现清晰的结构：

	```
	html本身是没有表现的，我们看到例如<h1>是粗体，字体大小2em，加粗；
	<strong>是加粗的，不要认为这是html的表现，这些其实html默认的css样式在起作用，
	所以去掉或样式丢失的时候能让页面呈现清晰的结构不是语义化的HTML结构的优点，
	但是浏览器都有有默认样式，默认样式的目的也是为了更好的表达html的语义，可以说浏览器的默认样式和语义化的HTML结构是不可分割的。
	```

1. 屏幕阅读器（如果访客有视障）会完全根据你的标记来“读”你的网页.

	```
	例如，如果你使用的含语义的标记，屏幕阅读器就会“逐个拼出”你的单词，而不是试着去对它完整发音.
	```

1. PDA、手机等设备可能无法像普通电脑的浏览器一样来渲染网页（通常是因为这些设备对CSS的支持较弱）.

	```
	使用语义标记可以确保这些设备以一种有意义的方式来渲染网页。
	理想情况下，观看设备的任务是符合设备本身的条件来渲染网页。
	语义标记为设备提供了所需的相关信息，就省去了你自己去考虑所有可能的显示情况（包括现有的或者将来新的设备）。
	例如，一部手机可以选择使一段标记了标题的文字以粗体显示。而掌上电脑可能会以比较大的字体来显示。
	无论哪种方式一旦你对文本标记为标题，您就可以确信读取设备将根据其自身的条件来合适地显示页面。
	```

1. 搜索引擎的爬虫也依赖于标记来确定上下文和各个关键字的权重.

	```
	过去你可能还没有考虑搜索引擎的爬虫也是网站的“访客”，但现在它们他们实际上是极其宝贵的用户.没有他们的话，搜索引擎将无法索引你的网站，然后一般用户将很难过来访问.
	```

1. 你的页面是否对爬虫容易理解非常重要，因为爬虫很大程度上会忽略用于表现的标记，而只注重语义标记。

	```
	因此，如果页面文件的标题被标记，而不是，那么这个页面在搜索结果的位置可能会比较靠后。除了提升易用性外，语义标记有利于正确使用CSS和JavaScript，因为其本身提供了许多“钩钩”来应用页面的样式与行为。
	SEO主要还是靠你网站的内容和外部链接的。(转载请注明出处：WEB前端开发 http://www.css88.com/)
	```


1. 便于团队开发和维护

	```
	W3C给我们定了一个很好的标准，在团队中大家都遵循这个标准，可以减少很多差异化的东西，方便开发和维护，提高开发效率，甚至实现模块化开发。
	```

## Javascript

1. js是什么，js和html 的开发如何结合？
 
1. 怎样添加、移除、移动、复制、创建和查找节点
1. 怎样使用事件以及IE和DOM事件模型之间存在哪些主要差别
1. 面向对象编程:b怎么继承a
1. 看看下面alert的结果是什么

	```
	view sourceprint?1.function b(x, y, a) { 
	.arguments[2] = 10; 
	.alert(a); 
	} 
	b(1, 2, 3);
	如果函数体改成下面，结果又会是什么？
	a = 10; 
	alert(arguments[2] );
	```
 
1. 请编写一个JavaScript函数 parseQueryString，它的用途是把URL参数解析为一个对象

	```
	var obj = parseQueryString(url); 
	alert(obj.key0)  // 输出0
	```
	 
1. ajax是什么?  ajax的交互模型? 同步和异步的区别? 如何解决跨域问题?
 
1. 什么是闭包？下面这个ul，如何点击每一列的时候alert其index?

	```
	<ul id=”test”> 
	<li>这是第一条</li><li>这是第二条</li><li>这是第三条</li> 
	</ul>
	```
 
1. 最近看的一篇Javascript的文章是？
 
1. 常使用的库有哪些？常用的前端开发工具？开发过什么应用或组件？
 
1. 说说YSlow(可以详细一点)
















```
 

2011-11-16 11:20


6、谈谈以前端角度出发做好SEO需要考虑什么。
1、了解搜索引擎如何抓取网页和如何索引网页
　　你需要知道一些搜索引擎的基本工作原理，各个搜索引擎之间的区别，搜索机器人（SE robot 或叫 web crawler）如何进行工作，搜索引擎如何对搜索结果进行排序等等。
　　2、Meta标签优化
　　主要包括主题（Title)，网站描述(Description)，和关键词（Keywords）。还有一些其它的隐藏文字比如Author（作者），Category（目录），Language（编码语种）等。
　　3、如何选取关键词并在网页中放置关键词
　　搜索就得用关键词。关键词分析和选择是SEO最重要的工作之一。首先要给网站确定主关键词（一般在5个上下），然后针对这些关键词进行优化，包括关键词密度（Density），相关度（Relavancy），突出性（Prominency）等等。
　　4、了解主要的搜索引擎
　　虽然搜索引擎有很多，但是对网站流量起决定作用的就那么几个。比如英文的主要有Google，Yahoo，Bing等；中文的有百度，搜狗，有道等。不同的搜索引擎对页面的抓取和索引、排序的规则都不一样。还要了解各搜索门户和搜索引擎之间的关系，比如AOL网页搜索用的是Google的搜索技术，MSN用的是Bing的技术。
　　5、主要的互联网目录
　　Open Directory自身不是搜索引擎，而是一个大型的网站目录，他和搜索引擎的主要区别是网站内容的收集方式不同。目录是人工编辑的，主要收录网站主页；搜索引擎是自动收集的，除了主页外还抓取大量的内容页面。
　　6、按点击付费的搜索引擎
　　搜索引擎也需要生存，随着互联网商务的越来越成熟，收费的搜索引擎也开始大行其道。最典型的有Overture和百度，当然也包括Google的广告项目Google Adwords。越来越多的人通过搜索引擎的点击广告来定位商业网站，这里面也大有优化和排名的学问，你得学会用最少的广告投入获得最多的点击。
　　7、搜索引擎登录
　　网站做完了以后，别躺在那里等着客人从天而降。要让别人找到你，最简单的办法就是将网站提交（submit）到搜索引擎。如果你的是商业网站，主要的搜索引擎和目录都会要求你付费来获得收录（比如Yahoo要299美元），但是好消息是（至少到目前为止）最大的搜索引擎Google目前还是免费，而且它主宰着60％以上的搜索市场。
　　8、链接交换和链接广泛度（Link Popularity）
　　网页内容都是以超文本（Hypertext）的方式来互相链接的，网站之间也是如此。除了搜索引擎以外，人们也每天通过不同网站之间的链接来Surfing（“冲浪”）。其它网站到你的网站的链接越多，你也就会获得更多的访问量。更重要的是，你的网站的外部链接数越多，会被搜索引擎认为它的重要性越大，从而给你更高的排名。
　　9、标签的合理使用
7、我们知道可以以外链的方式引入CSS文件，请谈谈外链引入CSS有哪些方式，这些方式的性能有区别吗。
要说出CSS的引入方式，没有什么难度，但要说到为什么使用不同的引入方式，就有些学问在里面了。

CSS的引入方式最常用的有三种，

第一：在head部分加入<link  rel="stylesheet" type="text/css" href="my.css"/>,引入外部的CSS文件。

这种方法可以说是现在占统治地位的引入方法。如同IE与浏览器。这也是最能体现CSS特点的方法；最能体现DIV+CSS中的内容与显示分离的思想，也最易改版维护，代码看起来也是最美观的一种。

第二：在head部分加入 
<style type="text/css">
div{margin: 0;padding: 0;border:1px red solid;}
</style>

这种方法的使用情况要少的多，最长见得就是访问量大的门户网站。或者访问量较大的企业网站的首页。与第一种方法比起来，优点突出，弊端也明显。优点：速度快，所有的CSS控制都是针对本页面标签的，没有多余的ＣＳＳ命令；再者不用外链ＣＳＳ文件。直接在ＨＴＭＬ文档中读取样式。缺点就是改版麻烦些，单个页面显得臃肿，ＣＳＳ不能被其他ＨＴＭＬ引用造成代码量相对较多，维护也麻烦些。　但是采用这种方法的公司大多有钱，对他们来说用户量是关键，他们不缺人进行复杂的维护工作。

第三：直接在页面的标签里加　<div style="border:1px red solid;">测试信息</div>

这种方法现在用的很少，很多公司不了解前端技术的领导还对这种写法很痛恨。认为ＨＴＭＬ里不能出现ＣＳＳ命令。其实有时候使用下也没有什么大不了。比如通用性差，效果特殊，使用ＣＳＳ命令较少，并且不常改动的地方，使用这种方法反而是很好的选择。

除了这三种常用的ＣＳＳ引入方式，还有种很多人都没有见过的引入方式
<style type="text/css">
@import url(my.css);
</style>

这就是第四种引入方式。在ＩＢＭ工作的时候，只能使用一种Ajax框架，就是ＤＯＪＯ。而ＤＯＪＯ的CSS引用，就是采用了@import的方式。这种情况非常少，主要用在CSS文件数量庞大的负责的系统中。另外@important本身是一个CSS命令，是放在CSS文件里的，这个跟LINK标签有很大的区别。
8、CSS Sprite是什么，谈谈这个技术的优缺点。
CSSSprites在国内很多人叫css精灵，是一种网页图片应用处理方式。它允许你将一个页面涉及到的所有零星图片都包含到一张大图中去，这样一来，当访问该页面时，载入的图片就不会像以前那样一幅一幅地慢慢显示出来了。对于当前网络流行的速度而言，不高于200KB的单张图片的所需载入时间基本是差不多的，所以无需顾忌这个问题。 
加速的关键，不是降低重量，而是减少个数。传统切图讲究精细，图片规格越小越好，重量越小越好，其实规格大小无所谓，计算机统一都按byte计算。客户端每显示一张图片都会向服务器发送请求。所以，图片越多请求次数越多，造成延迟的可能性也就越大。
CSS Sprites优缺点
　　利用CSS Sprites能很好地减少了网页的http请求，从而大大的提高了页面的性能，这也是CSS Sprites最大的优点，也是其被广泛传播和应用的主要原因； 
　　CSS Sprites能减少图片的字节，曾经比较过多次3张图片合并成1张图片的字节总是小于这3张图片的字节总和。 
　　解决了网页设计师在图片命名上的困扰，只需对一张集合的图片上命名就可以了，不需要对每一个小元素进行命名，从而提高了网页的制作效率。 
　　更换风格方便，只需要在一张或少张图片上修改图片的颜色或样式，整个网页的风格就可以改变。维护起来更加方便。 
　　诚然CSS Sprites是如此的强大，但是也存在一些不可忽视的缺点，如下： 
　　在图片合并的时候，你要把多张图片有序的合理的合并成一张图片，还要留好足够的空间，防止板块内不会出现不必要的背景；这些还好，最痛苦的是在宽屏，高分辨率的屏幕下的自适应页面，你的图片如果不够宽，很容易出现背景断裂； 
　　CSS Sprites在开发的时候比较麻烦，你要通过photoshop或其他工具测量计算每一个背景单元的精确位置，这是针线活，没什么难度，但是很繁琐；幸好腾讯的鬼哥用RIA开发了一个CSS Sprites 样式生成工具，虽然还有一些使用上的不灵活，但是已经比photoshop测量来的方便多了，而且样式直接生成，复制，拷贝就OK！ 
　　CSS Sprites在维护的时候比较麻烦，如果页面背景有少许改动，一般就要改这张合并的图片，无需改的地方最好不要动，这样避免改动更多的css，如果在原来的地方放不下，又只能（最好）往下加图片，这样图片的字节就增加了，还要改动css。 
　　CSS Sprites非常值得学习和应用，特别是页面有一堆ico（图标）。总之很多时候大家要权衡一下利弊，再决定是不是应用CSS Sprites。
9、以CSS3标准定义一个webkit内核浏览器识别的圆角（尺寸随意）
-moz-border-radius: 10px; -webkit-border-radius: 10px; border-radius:10px;。
10、有这么一段HTML，请挑毛病：
<P>  哥写的不是HTML，是寂寞。<br><br>  我说：<br>不要迷恋哥，哥只是一个传说
 缺少p标记的结束标记。
===========================================================================================
1.	Doctype? 严格模式与混杂模式-如何触发这两种模式，区分它们有何意义? 
Doctype声明位于文档中的最前面的位置，处于标签之前。此标签可告知浏览器文档使用哪种 HTML 或 XHTML 规范。该标签可声明三种DTD 类型，分别表示严格版本、过渡版本以及基于框架的 HTML 文档。
当浏览器厂商开始创建与标准兼容的浏览器时，他们希望确保向后兼容性。为了实现这一点，他们创建了两种呈现模式：标准模式和混杂模式（quirks mode）。在标准模式中，浏览器根据规范呈现页面；在混杂模式中，页面以一种比较宽松的向后兼容的方式显示。混杂模式通常模拟老式浏览器（比如Microsoft IE 4和Netscape Navigator 4）的行为以防止老站点无法工作。
浏览器根据DOCTYPE是否存在以及使用的哪种DTD来选择要使用的呈现方法。如果XHTML文档包含形式完整的DOCTYPE，那么它一般以标准模式呈现。对于HTML 4.01文档，包含严格DTD的DOCTYPE常常导致页面以标准模式呈现。包含过渡DTD和URI的DOCTYPE也导致页面以标准模式呈现，但是有过渡DTD而没有URI会导致页面以混杂模式呈现。DOCTYPE不存在或形式不正确会导致HTML和XHTML文档以混杂模式呈现。
2：行内元素有哪些？块级元素有哪些？CSS的盒模型？
行内元素有：a b span I bem img input select strong
级元素有：div ul ol lidl dt dd h1 h2 h3 h4…p
盒模型：margin border padding width
3.CSS引入的方式有哪些? link和@import的区别是?
1.        使用 LINK标签
将样式规则写在.css的样式文件中，再以<link>标签引入。
<link rel=stylesheet type="text/css" href="example.css">
2.        使用@import引入
跟link方法很像，但必须放在<STYLE>...</STYLE> 中
<STYLE TYPE="text/css">
<!--
　　@import url(css/example.css);
-->
</STYLE>
3.        使用STYLE标签
将样式规则写在<STYLE>...</STYLE>标签之中。
<STYLE TYPE="text/css">
<!--
body {color: #666;background: #f0f0f0;font-size: 12px;}
td,p {color:#c00;font-size: 12px;}
-->
</STYLE>
4.        使用STYLE属性
将STYLE属性直接加在个别的元件标签里，<元件(标签) STYLE="性质(属性)1: 设定值1;  性质(属性)2: 设定值2; ...}
5.        使用<span></span>标记引入样式
<span style="font:12px/20px  #000000;">cnwebshow.com</span>
 
两者区别：加载顺序的差别。当一个页面被加载的时候，link引用的CSS会同时被加载，而@import引用的CSS会等到页面全部被下载完再被加载。@import可以在css中再次引入其他样式表，比如可以创建一个主样式表，在主样式表中再引入其他的样式表，如：
 
main.css
———————-
@import“sub1.css”;
@import“sub2.css”;
这样做有一个缺点，会对网站服务器产生过多的HTTP请求，以前是一个文件，而现在却是两个或更多文件了，服务器的压力增大，浏览量大的网站还是谨慎使用。

4.CSS选择符有哪些？哪些属性可以继承？优先级算法如何计算？内联和important哪个优先级高？

5:前端页面有哪三层构成，分别是什么？作用是什么？
网页分成三个层次，即：结构层、表示层、行为层。
网页的结构层（structurallayer）由HTML 或XHTML 之类的标记语言负责创建。标签，也就是那些出现在尖括号里的单词，对网页内容的语义含义做出了描述，但这些标签不包含任何关于如何显示有关内容的信息。例如，P标签表达了这样一种语义：“这是一个文本段。”
网页的表示层（presentationlayer）由CSS 负责创建。CSS 对“如何显示有关内容”的问题做出了回答。
网页的行为层（behaviorlayer）负责回答“内容应该如何对事件做出反应”这一问题。这是Javascript 语言和DOM 主宰的领域。
6:css的基本语句构成是？
 
8：你做的页面在哪些流览器测试过？这些浏览器的内核分别是什么?经常遇到的浏览器的兼容性有哪些？怎么会出现？解决方法是什么？
 
 
9.如何居中一个浮动元素?
设置容器的浮动方式为相对定位，然后确定容器的宽高，比如宽500 高 300 的层，然后设置层的外边距。
div{Width:500px;height:300px;Margin: -150px 0 0-250px;position:relative;left:50%;top:50%;}
10.有没有关注HTML5和CSS3?如有请简单说一些您对它们的了解情况！
HTML5标签的改变：<header>,<footer>, <dialog>, <aside>, <figure>, <section> 等
IE9以上开始支持
CSS3实现圆角，阴影，对文字加特效，增加了更多的CSS选择器。
11.你怎么来实现下面这个设计图,主要讲述思路 （效果图省略）
13:如果让你来制作一个访问量很高的大型网站，你会如何来管理所有CSS文件、JS与图片？
14：你对前端界面工程师这个职位是怎么样理解的？它的前景会怎么样？
 
 
 

 
 
 
===========================================================================================
 
　Class 可继承 
　　4.CSS选择符有哪些？哪些属性可以继承？优先级算法如何计算？内联和important哪个优先级高？ 回答：ID 和 CLASS 
　　伪类A标签可以继承 
　　列表 UL LIDL DD DT可继承 
　　优先级就近原则，样式定义最近者为准 
　　载入样式以最后载入的定位为准 
　　优先级为 
　　!important > [ id > class > tag ] 
　　Important 比内联优先级高 
　　5:前端页面有哪三层构成，分别是什么？作用是什么？ 
　　回答：结构层，表现层，定义层； 
　　6:css的基本语句构成是？ 
　　回答：选择器、属性和属性值。 
　　8：你做的页面在哪些流览器测试过？这些浏览器的内核分别是什么?经常遇到的浏览器的兼容性有哪些？怎么会出现？解决方法是什么？ 
　　回答：涉及到效率一般就在IEtext firefox 3.5 软件上测试模拟 IE6 IE7 IE8内核是IE7 的 
　　浏览器PNG8格式背景图透明 JS 报错，浏览器本身的兼容问题有些电脑IE7IE6 下正常，有些提示错误 
　　9.如何居中一个浮动元素? 
　　回答：设置容器的浮动方式为相对定位 
　　然后确定容器的宽高比如宽500 高 300 的层 
　　然后设置层的外边距 
　　.Div 
　　{ 
　　Width:500px ; height:300px; 
　　Margin: -150px 0 0 -250px; 
　　position: absolute; 
　　left:50%; 
　　top:50%; 
　　} 
　　10.有没有关注HTML5和CSS3?如有请简单说一些您对它们的了解情况！ 
　　回答：HTML5 没有关注CSS3 有关注 
　　比如对多背景图圆角投影等样式的关注 
　　13:如果让你来制作一个访问量很高的大型网站，你会如何来管理所有CSS文件、JS与图片？ 
　　回答：涉及到人手、分工、同步； 
　　先期团队必须确定好全局样式（globe.css），编码模式(utf-8) 等 
　　编写习惯必须一致（例如都是采用继承式的写法，单样式都写成一行）； 
　　标注样式编写人，各模块都及时标注（标注关键样式调用的地方）； 
　　页面进行标注（例如页面模块开始和结束）； 
　　CSS跟HTML 分文件夹并行存放，命名都得统一（例如style.css） 
　　JS 分文件夹存放命民以该JS 功能为准英文翻译； 
　　图片采用整合的 images.pngpng8 格式文件使用尽量整合在一起使用方便将来的管理 
　　14：你对前端界面工程师这个职位是怎么样理解的？它的前景会怎么样？ 
　　是策划 UI设计需要转换成程序可实施中的必须的中间环节，这个环节直接关系到页面的正确高效稳定还原策划和UI 设计的效果，同时为程序套接做好程序表现基础载体。这个工作的前景，只能是深造技术流的，模块化管理，新的技术不断更新，对于向后兼容思维的逐步放弃，比如真的淘汰掉IE6后，向前的空间还是有的。前端开发工程师的前景是非常不错的。现在各大IT企业都在招聘这方面的人才。WEB2.0的普及会更加促进本行业本工种的繁荣。 
 
===========================================================================================================
 
一、填空题（40分）
1、目前常用的WEB标准静态页面语言是__ ______。（4分）html
2、改变元素的外边距用________，改变元素的内填充用________。（6分）margin  padding
3、在Table中，TR是________，TD是________。（6分）行列
4、如果给一行两列的表格（table）定义高度样式，在________标签中定义最合理，最能减少代码的臃肿。（5分）css样式也有说tr
5、对ul li的样式设成无，应该是用什么属性________。（6分）list-styl-type：none；
6、在新窗口打开链接的方法是________。（4分）target=_bank
7、Color:#666666;可缩写为________。（2分）color：#666
8、合理的页面布局中常听过结构与表现分离，那么结构是________，表现是________。（9分）div css
 
 
二、选择题（20分）
1

1、	列举常用的浏览器类型以及他们使用的内核还有对应的调试工具 
常用的有IE(6,7,8,9,10,FF,chrome ) 
IE常用的调试工具有 IEWebDeveloper (IE9默认有安装) 
Firefox大家估计用的最多。firefox 
chrome(内核webkit) 自带的有google 开发的内置调试工具。 
三者内核各不相同。 
其它还有opera，遨游，世界之窗等； 
chrome内核跑的比较快，安全。Firefox做调试是最棒的。

4、html5和css3有什么新特性 
html5强化了 Web 网页的表现性能，如:nav header section canvas等，语义化更强 
css3新特性有阴影特效，圆角处理等，都是非常不错的效果；
5、说出其他浏览器和IE浏览器在页面元素引用有什么区别？ 
这个和内核有关系，及是否w3c来定制，不同浏览器渲染结果不同。 
目前国内还有大部份使用IE6，常常web在制作的时候碰到兼容性的问题： 
如： 
display-block, padding, margin 等盒子模型比较多。还有不同的字间距等产生的问题； 
常用解决的方法： 
IE6：_xxx:{} 
IE7：* 
等处理不IE和其它不同浏览器间的差异；
4、请选择对javascript理解有误的：(        )
A. javascript是网景公司开发的一种基于事件和驱动网页脚本语言
B. JScript是javascript的简称
C.FireFox和IE存在大量兼容性问题的主要原因在于他们对javascript的支持不同上
D.AJAX技术一定要使用javascript技术 
5、在Jquery中下面哪一个是用来追加到指定元素的末尾的？(     )
A、insertAfter() B、append() C、appendTo() D、after()
6、在javascript中定义变量 var a=”35”, var b=”7” 运算 a %  b的结果为（      ）
A、357  B、57 C、0  D、5
7、下面哪种不属于jquery的筛选？（     ）
A、过滤 B、自动 C、查找 D、串联
8、  有这样一个表单元素，想要找到这个hidden元素，下面哪个是正确的？(      )
A、visible B、hidden C、visible() D、overflow
9、下面哪个属于javascript的布尔型（        ）
A、1.2 B、“true” C、false D、null
10、onload事件是 window 的事件，但是在 HTML 中指定事件处理程序的时候，我们是把它写在（      ）标记中的。
A、<body>   B、<head>   C、<form>   D、<script>
11、请选择结果为真的表达式：（        ）
A、null instanceof Object  B、null === undefined  C、C.null == undefined
D、NaN == NaN
12、下列哪个对象是用来代表特定的窗口URL信息（        ）
A、location  B、history   C、form    D、frame
13、（     ）是一个可以执行的JavaScript代码段。
A、对象  B、方法  C、事件   D、函数
14、在window 窗口对象中，（        ）使焦点从窗口移走，窗口变为“非活动窗口”。
A、focus( ) B、blur( )   C、password（） D、check（）
15、下面哪个属于javascript的字符型（       ）
A、false B、你好C、“123” D、null
16、下列运算方式不属于逻辑运算的是（          ）
A、!a  B、a&&b  C、a ‖ b  D、a>b
17、关于变量的声明，下列选项阐述不正确的是（       ）
A、变量声明时，所有类型均由小写var声明，如 var  name=“张勇” sex=“女生”
B、可以以字母、下划线或者数字开头  C、变量名区分大小写  D、变量名不能是Javascript的保留字
18、（       ）指浏览器的浏览历史对象
A、history   B、location   C、window   D、protocol
19、JavaScript是一种基于（      ）的安全脚本语言。
A、对象 B、方法 C、事件 D、对象和事件驱动

1. HTTP协议的状态消息都有哪些?(如200、302对应的描述)

2. AJAX是什么? AJAX的交互模型(流程)? AJAX跨域的解决办法?

3. 同步和异步的区别?

4. 简述JavaScript封装。

5. JavaScript继承有哪两种形式形式，进行描述。

6. 什么是闭包?以下代码点击<p> 会输出什么?为什么?能大概说明白的话继续问能想出几种解决办法。

<!DOCTYPE HTML> <html> <head> <meta charset="utf-8" /> <title>闭包演示</title> <style type="text/css">     p {background:gold;}  </style> <script type="text/javascript">   function init() {          var pAry = document.getElementsByTagName("p");          for( var i=0; i<pAry.length; i++ ) {               pAry[i].onclick = function() {               alert(i);          }     }  }  </script>   </head>   <body onload="init();">   <p>产品 0</p>   <p>产品 1</p>   <p>产品 2</p>   <p>产品 3</p>   <p>产品 4</p>   </body>   </html>  7. 在JS中this关键字的使用场合和用法(如在构造函数中、setTimeout中等)。

8. 简述下cookie的操作，还有cookie的属性都知道哪些。

9. IE与FF的JS兼容性都知道哪些。

10. DOM操作 - 怎样添加、移除、移动、复制、创建和查找节点(这个问题真心是基础题，一般不会问)。

jQuery相关

1. jQuery源码是否尝试去读过?说说基本的架构或者 jQuery.fn.init 中都做了哪些判断。

2. 都知道哪些不好的jQuery书写方式。

3. Sizzle是否有读过?

其它相关的加分项：

1. 都使用和了解过哪些编辑器?都使用和了解过哪些日常工具?

2. 都知道有哪些浏览器内核?开发过的项目都兼容哪些浏览器?

3. 国内外的JS牛人都知道哪些?

4. 瀑布流布局或者流式布局是否有了解

4. 正则表达式有系统学习过吗(看书或网上教程)?有的话就问问简单点的邮箱验证、URL验证， 或者问问 贪婪匹配与懒惰匹配 的理论知识。

5. Node.js是否有过尝试?到什么程度?说说个人理解的看法?

6. HTML5都有哪些新的JS API?

7. 前端优化知识都知道哪些?

8. 基础算法题(如快速排序，能否一两句说说重要的核心原理或者数组消重等)。

9. 是否有接触过或者了解过重构。
一、	 
1、javascript的数据类型不包括 （   a    ）
A. 汉字型          B. 数值型           C. 对象型           D. 布尔型
2、以下哪条语句不能创建对象：（       ）
A.var obj = ();      B.var obj = [];   C.var obj = {};     D.var obj = //;
3、javascript的单行注释方式（    c     ）
A. {}               B. <!-->          C.   //            D.  /* * * * */
20、关于下列运算符与表达式叙述不正确的是（      ）
A、delete是用来删除对象、属性、数组、变量，删除成功返回true，删除失败返回false
B、typeof是用来判断操作数类型
C、this代表当前对象，因此在不同的地方就有不同的结果
D、new能用来声明变量，并给变量赋值
21、写 "Hello World" 的正确 Javascript 语法是（        ）
A、("Hello World")  B、"Hello World" C、response.write("Hello World") 
D、document.write("Hello World")
22、如何在警告框中写入 "Hello World"？（      ）
A、alertBox="Hello World"  B、msgBox("Hello World”)  C、alert("Hello World”)
D、alertBox("Hello World”)
23、如何创建函数（         ）
A、function:myFunction()  B、function myFunction()  C、function=myFunction() 
24、如何调用名为 "myFunction" 的函数(       )
A、call function myFunction   B、call myFunction()  C、myFunction() 
25、如何编写当 i 等于 5 时执行一些语句的条件语句？（       ）
A、if (i==5)  B、if i=5 then  C、if i=5  D、if i==5 then
26、jQuery中如果需要匹配包含文本的元素，用下面哪种来实现？(     )
A、text() B、contains() C、input() D、attr(name)
27、在 JavaScript 中，有多少种不同类型的循环(      )
A、两种。for 循环和 while 循环。 
B、三种。for 循环、while 循环、do...while 。
C、一种。for 循环。 
28、for 循环如何开始(        )
A、if (i != 5)   B、for (i <= 5; i++)  C、for (i = 0; i <= 5; i++)  D、for i = 1 to 5
29、定义 JavaScript 数组的正确方法是 (      )
A、var txt = new Array="George","John","Thomas"
B、var txt = new Array(1:"George",2:"John",3:"Thomas")
C、var txt = new Array("George","John","Thomas")  
D、var txt = new Array:1=("George")2=("John")3=("Thomas")
30、如何把 7.25 四舍五入为最接近的整数(         )
A、round(7.25)   B、rnd(7.25)  C、Math.rnd(7.25)  D、Math.round(7.25)
31、 如何求得 2 和 4 中最大的数？(      )
A、Math.ceil(2,4)  B、Math.max(2,4)  C、ceil(2,4)   D、top(2,4)
32、在jquey中，如果想要从DOM中删除所有匹配的元素，下面哪一个是正确的？（    ）
A、delete() B、empty() C、remove() D、removeAll()
33、如何在浏览器的状态栏放入一条消息(      )
A、statusbar = "put your message here"
B、window.status = "put your message here"
C、window.status("put your message here")
D、status("put your message here")
34如何获得客户端浏览器的名称(      )
A、client.navName  B、navigator.appName   C、browser.name
D、status("put your message here")
35、在JQUERY中以下方法，哪一个可以直接设置高度收缩展开：（      ）
A、show()和hide()  B、fadeIn()和fadeOut()  C、slideUp()和slideDown()
D、animate()
36、jQuery中使用cookie插件设置cookie的正确写法是（        ）
A、$(“cookieName”)            B、$.cookie(“name”,”value”,{path:”/”,expires:10})
C、$.cookie(“name”, path:”/”,expires:10})          D、setCookie(“name”)
37、在jquery中，想要给第一个指定的元素添加样式，下面哪一个是正确的？（        ）
A、first B、eq(1) C、css(name) D、css(name,value)型
38、在一个表单中，如果将所有的div元素都设置为绿色，实现功能是（     ）
A $(“div”).css(“color”,”green”)  B $(“div”).cssStyle(“color”,”green”)
C $(“div”).addCss(“color”,”green”) D $(“div”).css(”green”)
39、 下列方法可以来回切换点击事件的是（      ）
A toggle()  B hover()  C change()   D Click(  )
40、（         ） 提交按钮对象 由“<input type="submit">指定。
Ａ、Submit 　Ｂ、Button   C、Form　　Ｄ、object
1.	（        ）事件发生在窗口得到焦点的时候。
2.	document.（         ）是在当前文档中写入
3.	（          ） 发生在窗口失去焦点的时候。
4.	（        ）发生在用户把鼠标放在对象上鼠标键被按下的情况下，放开鼠标键的时候。
5.	在数组对象中（          ）属性可以获取数组元素的个数。
6.	字符串对象中（          ）方法可以获取字符串在字符串中出是否出现。
7.	正则表达式中（          ） 方法检查在字符串中是否存在这个模式，如果存在则返回 true，否则就返回 false。  
8.	window对象中的（         ）方法，用以指定在一段特定的时间后重复执行某段程序。
9.	给图片<img   />设置路径 src 的值为 1.gif 的jquery写法为(                      )
10.	(          ） 发生在对象被单击的时候。
11.	根据变量的作用域，可以将变量分为（        ）和（           ）。
12.	日期对象中getMonth()方法获取的取值范围是（           ）。
13.	（            ）发生在用户把鼠标放在对象上按下鼠标键的时候。
14.	可以用（           ）来创建一个新的对象，并指定对象的类型。
15.	JQUERY中可以用（         ）方法触发事件
16.	jQuery中，（          ）方法可以得到该元素的下一个兄弟节点
17.	jQuery中（           ）方法可以插入一个节点
18.	jQuery中（          ）方法 和 （           ）可以产生淡入淡出动画
 
1.	Jquery的实质仍然是javascript。                （      ）
2.	window.onload是指当文档加载的时候，在一个javascript文件中可以出现多次（      ）
3.	JavasScript不存在兼容问题                            （       ）
4.	CSS Sprite技术的应用为了达到更好的加载速度和更好的用户体验，是将多个切图应用在一张图片上利用background-position定位背景（      ）
5.	 日期对象的	Month()方法可以获取月份，获取的值为1-12  （       ）
6.	 正则表达式的test()方法可以使用正则表达式模式在字符串中运行查找，并返回包含该查找结果的一个数组。（   ）
7.	 javascript中  “+” 只能作为算术运算符应用                        （        ）
8.	 onblur()事件是指当获取光标的时候                        （         ） 
9.	onmouseout 事件发生在用户把鼠标放在对象上按下鼠标键的时候。（          ）
10.	在 Link 对象的 onclick 事件处理程序中返回 false 值（return false），能阻止浏览器打开此连接。                                                              （        ）
 
 
    


1. W3C标准有哪些？
 W3C推行的主要规范有HTML，CSS，XML，XHTML和DOM（Document Object Model）。
2. 谈谈Js的内存泄露问题。
3. 谈谈对Html 5的了解。
4. 谈谈对CSS 3的了解。
5. 用js实现随即选取10--100之间的10个数字，存入一个数组，并排序。
var iArray = []; 
funtion getRandom(istart, iend){
        var iChoice = istart - iend +1;
        return Math.floor(Math.random() * iChoice + istart;
}
for(var i=0; i<10; i++){
        iArray.push(getRandom(10,100));
}
iArray.sort();
6. 把两个数组合并，并删除第二个元素。
var array1 = ['a','b','c'];
var bArray = ['d','e','f'];
var cArray = array1.concat(bArray);
cArray.splice(1,1);
7. Js面向对象的几种方式。
8. 请谈谈原型方式构造对象的特点。
9. 在Css中那个属性会影响dom读取文档流的顺序。
答： float属性。
10. 请介绍几种用div实现两列布局的方案（兼容），另外要考虑文档流的加载。
11. 谈谈css在浏览器中的兼容问题，详细谈谈IE6的一些bug,以及解决方案。
12. 谈谈你对闭包的理解。以及如何实现js方法的重写。

[HTML && CSS]
1.Doctype? 严格模式与混杂模式-如何触发这两种模式，区分它们有何意义? 
首先我讲讲如何触发两种模式：        加入xml头部声明可以触发IE浏览器的Quirks mode，触发之后，浏览器解析方式就和IE5.5一样，拥有IE5.5一样的bug和其他问题，行为（Javascript）也是如此。          IE6的触发        在XHTML的DOCTYPE前加入XML声明  <?xml version="1.0" encoding="utf-8"?>  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">          IE7的触发        在XML声明和XHTML的DOCTYPE之间加入HTML注释    <?xml version="1.0" encoding="utf-8"?>  <!-- ... and keep IE7 in quirks mode -->  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">          IE6和IE7都可以触发的        在HTML4.01的DOCTYPE文档头部加入HTML注释    <!-- quirks mode -->  <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">    其次是这样的意义  各个浏览器的混杂模式，基本就是各个浏览器的私有模式，不相互兼容。所以，除非是为了兼容的问题，比如你不想修改很久很久以前做的IE ONLY的网页，否则刻意触发混杂模式没有任何意义。


2：行内元素有哪些？块级元素有哪些？CSS的盒模型？
一.行内元素和块级元素有哪些？
块级元素
	
<address>	information on author
<blockquote>	long quotation
<button>	push button
<caption>	table caption
<dd>	definition description
<del>	deleted text
<div>	generic language/style container
<dl>	definition list
<dt>	definition term
<fieldset>	form control group
<form>	interactive form
<h1>	heading
<h2>	heading
<h3>	heading
<h4>	heading
<h5>	heading
<h6>	heading
<hr>	horizontal rule
<iframe>	inline subwindow
<ins>	inserted text
<legend>	fieldset legend
<li>	list item
<map>	client-side image map
<noframes>	alternate content container for non frame-based rendering
<noscript>	alternate content container for non script-based rendering
<object>	generic embedded object
<ol>	ordered list
<p>	paragraph
<pre>	preformatted text
<table>	table
<tbody>	table body
<td>	table data cell
<tfoot>	table footer
<th>	table header cell
<thead>	table header
<tr>	table row
<ul>	unordered list
 行内元素
	
<a>	anchor
<abbr>	abbreviated form
<acronym>	acronym
<b>	bold text style
<bdo>	I18N BiDi over-ride
<big>	large text style
<br>	forced line break
<button>	push button
<cite>	citation
<code>	computer code fragment
<del>	deleted text
<dfn>	instance definition
<em>	emphasis
<i>	italic text style
<iframe>	inline subwindow
<img>	Embedded image
<input>	form control
<ins>	inserted text
<kbd>	text to be entered by the user
<label>	form field label text
<map>	client-side image map
<object>	generic embedded object
<q>	short inline quotation
<samp>	sample program output, scripts, etc.
<select>	option selector
<small>	small text style
<span>	generic language/style container
<strong>	strong emphasis
<sub>	subscript
<sup>	superscript
<textarea>	multi-line text field
<tt>	teletype or monospaced text style
<var>	instance of a variable or program argument
 二.行内元素与块级元素有什么不同？
1.尺寸-块级元素和行内元素之间的一个重要的不同点 
行内元素和width
W3C CSS2 标准规定行内元素、非置换元素不会应用width属性。
以下例子中，对行内元素<a>应用了width:200px,你可以看到，根本就没有什么效果。
 
行内元素和height
W3C CSS2 标准规定行内元素、非置换元素不会应用height属性，但是盒子高度可以通过line-height来指定。
以下例子，对行内元素<a>应用了height:50px,你可以看到什么效果都没。
 
行内元素和padding
你可以给行内元素设置padding，但只有padding-left和padding-right生效。
以下例子，行内元素<a>应用了padding:50px。你可以看到对左右的内容有影响，但是对上下没影响。
 
行内元素和marging
margin属性也是和padding属性一样，对行内元素左右有效，上下无效。
下面的例子,对<a>应用了margin:50px，你可以看到左右边缘是生效了但是内容上下却没有。
 
  记住对行内元素
设置宽度width   无效。
设置高度height  无效，可以通过line-height来设置。
设置margin 只有左右margin有效，上下无效。
设置padding 只有左右padding有效，上下则无效。注意元素范围是增大了，但是对元素周围的内容是没影响的，看图上效果就知道了 
盒子模型
W3C 组织建议把所有网页上的对像都放在一个盒(box)中，设计师可以通过创建定义来控制这个盒的属性，这些对像包括段落、列表、标题、图片以及层。盒模型主 要定义四个区域：内容(content)、边框距(padding)、边界(border)和边距(margin)。对于初学者，经常会搞不清楚 margin，background-color，background- image，padding，content，border之间的层次、关系和相互影响。这里提供一张盒模型的3D示意图，希望便于你的理解和记忆。
 
 
每个HTML元素都可以看作一个装了东西的盒子，盒子里面的内容到盒子的边框之间的距离即填充（padding），盒子本身有边框（border），而盒子边框外和其他盒子之间，还有边界（margin）。
 
 
盒模型的实际宽度
 
关于盒模型，还有以下几点需要注意：
　　•对于块级元素（display:block），未浮动的垂直相邻元素的上边界和下边界会被压缩，例如：有上下2个元素，上元素的下边界为5px，下面元素的上边界为20px，则实际2个元素的间距为20px（2个边界值中较大的值）。如图所示。
 
注1. 块级元素（display： block）
每个块级元素都从一个新行开始，而且其后的元素也需另起一行开始，标题、段落、表格、层、body等都是块级元素。块级元素只能作为其他块级元素的子元素，而且需要一定的条件。
　　•内联元素，例如<a>、<span>等，定义上下边界不会影响到行高（line-height），内联元素距离上一行元素的距离由行高决定，而不是填充或边界。
注2. 内联元素（display：inline）
内联元素不需要在新行内显示，而且也不强迫其后的元素换行，如a、em、span等都为内联元素。内联元素可以为任何其他元素的子元素。
　　•浮动元素（无论左或者右浮动）边界不压缩，且若浮动元素不声明宽度，则其宽度趋向于0，即压缩到其内容能承受的最小宽度。
　　•如果盒中没有内容，则即使定义了宽度和高度都为100%，实际上只占0%，因此不会被显示，此点在采取层布局的时候需特别注意。
　　•边界值可为负，其显示效果各浏览器可能不相同。
　　•填充值不可为负。
　　•边框默认的样式（border-style）为不显示（none）。

3.CSS引入的方式有哪些? link和@import的区别是?
本质上，这两种方式都是为了加载CSS文件，但还是存在着细微的差别。
差别1：老祖宗的差别。link属于XHTML标签，而@import完全是CSS提供的一种方式。
link标签除了可以加载CSS外，还可以做很多其它的事情，比如定义RSS，定义rel连接属性等，@import就只能加载CSS了。
差别2：加载顺序的差别。当一个页面被加载的时候（就是被浏览者浏览的时候），link引用的CSS会同时被加载，而@import引用的CSS会等到页面全部被下载完再被加载。所以有时候浏览@import加载CSS的页面时开始会没有样式（就是闪烁），网速慢的时候还挺明显（梦之都加载CSS的方式就是使用@import，我一边下载一边浏览梦之都网页时，就会出现上述问题）。
差别3：兼容性的差别。由于@import是CSS2.1提出的所以老的浏览器不支持，@import只有在IE5以上的才能识别，而link标签无此问题。
差别4：使用dom控制样式时的差别。当使用javascript控制dom去改变样式的时候，只能使用link标签，因为@import不是dom可以控制的。
大致就这几种差别了（如果还有什么差别，大家告诉我，我再补充上去），其它的都一样，从上面的分析来看，还是使用link标签比较好。
标准网页制作加载CSS文件时，还应该选定要加载的媒体（media），比如screen，print，或者全部all等。这个我到CSS高级教程中再给大家介绍。
注：
1，网友comehope在留言中提出了另一种区别。
差别5：@import可以在css中再次引入其他样式表，比如可以创建一个主样式表，在主样式表中再引入其他的样式表，如：
main.css
———————-
@import “sub1.css”;
@import “sub2.css”;
sub1.css
———————-
p {color:red;}
sub2.css
———————-
.myclass {color:blue}
这样更利于修改和扩展．
猴 子提示：这样做有一个缺点，会对网站服务器产生过多的HTTP请求，以前是一个文件，而现在却是两个或更多文件了，服务器的压力增大，浏览量大的网站还是 谨慎使用。有兴趣的可以观察一下像新浪等网站的首页或栏目首页代码，他们总会把css或js直接写在html里，而不用外部文件。

4.CSS选择符有哪些？哪些属性可以继承？优先级算法如何计算？内联和important哪个优先级高？

5:前端页面有哪三层构成，分别是什么？作用是什么？
最准确的网页设计思路是把网页分成三个层次，即：结构层、表示层、行为层。
网页的结构层（structural layer）由 HTML 或 XHTML 之类的标记语言负责创建。标签，也就是那些出现在尖括号里的单词，对网页内容的语义含义做出了描述，但这些标签不包含任何关于如何显示有关内容的信息。例如，P 标签表达了这样一种语义：“这是一个文本段。”
网页的表示层（presentation layer） 由 CSS 负责创建。 CSS 对“如何显示有关内容”的问题做出了回答。
网页的行为层（behavior layer）负责回答“内容应该如何对事件做出反应”这一问题。这是 Javascript 语言和 DOM 主宰的领域。


8：你做的页面在哪些流览器测试过？这些浏览器的内核分别是什么?经常遇到的浏览器的兼容性有哪些？怎么会出现？解决方法是什么？
点评：css的兼容性也是大家关注的热点。大家一定要注意多测试。Javascript 多浏览器兼容性问题及解决方案
兼容性处理要点 
1、DOCTYPE 影响 CSS 处理 
2、FF: 设置 padding 后， div 会增加 height 和 width， 但 IE 不会， 故需要用 !important 多设一个 height 和 width 
3、FF: 支持 !important， IE 则忽略， 可用 !important 为 FF 特别设置样式 
4、div 的垂直居中问题: vertical-align:middle; 将行距增加到和整个DIV一样高 line-height:200px; 然后插入文字，就垂直居中了。缺点是要控制内容不要换行 
5、在mozilla firefox和IE中的BOX模型解释不一致导致相差2px解决方法： 
div{margin:30px!important;margin:28px;} 
注意这两个margin的顺序一定不能写反，!important这个属性IE不能识别，但别的浏览器可以识别。所以在IE下其实解释成这样： 
div{maring:30px;margin:28px} 
重复定义的话按照最后一个来执行，所以不可以只写margin:XXpx!important; 
浏览器差异 
1、ul和ol列表缩进问题 
消除ul、ol等列表的缩进时，样式应写成：list-style:none;margin:0px;padding:0px; 
其中margin属性对IE有效，padding属性对FireFox有效。 
[注] 经验证，在IE中，设置margin:0px可以去除列表的上下左右缩进、空白以及列表编号或圆点，设置padding对样式没有影响；在 Firefox 中，设置margin:0px仅仅可以去除上下的空白，设置padding:0px后仅仅可以去掉左右缩进，还必须设置list- style:none才 能去除列表编号或圆点。也就是说，在IE中仅仅设置margin:0px即可达到最终效果，而在Firefox中必须同时设置margin:0px、 padding:0px以及list-style:none三项才能达到最终效果。 
2、CSS透明问题 
IE：filter:progid:DXImageTransform.Microsoft.Alpha(style=0,opacity=60)。 
FF：opacity:0.6。 
[注] 最好两个都写，并将opacity属性放在下面。 
3、CSS圆角问题 
IE：ie7以下版本不支持圆角。 
FF： -moz-border-radius:4px，或者-moz-border-radius-topleft:4px;-moz- border- radius-topright:4px;-moz-border-radius-bottomleft:4px;-moz- border- radius- bottomright:4px;。 
[注] 圆角问题是CSS中的经典问题，建议使用JQuery框架集来设置圆角，让这些复杂的问题留给别人去想吧。不过jQuery的圆角只看到支持整个区域的圆角，没有支持边框的圆角，不过这个边框的圆角可以通过一些简单的手段来实现，下次有机会介绍下。 
4、cursor:hand VS cursor:pointer 
问题说明：firefox不支持hand，但ie支持pointer ，两者都是手形指示。 
解决方法：统一使用pointer。 
5、字体大小定义不同 
对字体大小small的定义不同，Firefox中为13px，而IE中为16px，差别挺大。 
解决方法：使用指定的字体大小如14px。 
并列排列的多个元素（图片或者链接）的div和div之间，代码中的空格和回车在firefox中都会被忽略，而IE中却默认显示为空格（约3px）。 
6、CSS双线凹凸边框 
IE：border:2px outset;。 
FF： -moz-border-top-colors: #d4d0c8 white;-moz-border-left-colors: #d4d0c8 white;-moz-border-right-colors:#404040 #808080;-moz-border-bottom-colors:#404040 #808080; 
浏览器bug 
1、IE的双边距bug 
设置为float的div在ie下设置的margin会加倍。这是一个ie6都存在的bug。 
解决方案：在这个div里面加上display:inline; 
例如： 
<#div id=”imfloat”> 
相应的css为 
以下为引用的内容： 
复制代码代码如下:
#IamFloat{ 
float:left; 
margin:5px;/*IE下理解为10px*/ 
display:inline;/*IE下再理解为5px*/ 
} 
#IamFloat{ 
float:left; 
margin:5px;/*IE下理解为10px*/ 
display:inline;/*IE下再理解为5px*/ 
} 
关 于CSS中的问题实在太多了，甚至同样的CSS定义在不同的页面标准中的显示效果都是不一样的。一个合乎发展的建议是，页面采用标准XHTML标准编写， 较少使用table，CSS定义尽量依照标准DOM，同时兼顾IE、Firefox、Opera等主流浏览器。很多情况下，FF和 Opera的CSS解释标准更贴近CSS标准，也更具有规范性。 
2、IE选择符空格BUG 
今天在给博客的段落样式设置首字符样式的时候发现，原来一个空格也可以使样式失效。 
请看以下代码： 

复制代码代码如下:
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "//www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 
<html xmlns="//www.w3.org/1999/xhtml"> 
<head> 
<title></title> 
<style type="text/css"> 
<!-- 
p{font-size:12px;} 
p:first-letter{font-size:300%} 
--> 
</style> 
</head> 
<body> 
<p>对于世界而言，你是一个人；但是对于某个人，你是他的整个世界。纵然伤心，也不要愁眉不展，因为你不知是谁会爱上你的笑容。</p> 
</body> 
</html> 
[/code] 

复制代码代码如下:
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "//www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 
<html xmlns="//www.w3.org/1999/xhtml"> 
<head> 
<title></title> 
<style type="text/css"> 
<!-- 
p{font-size:12px;} 
p:first-letter{font-size:300%} 
--> 
</style> 
</head> 
<body> 
<p>对于世界而言，你是一个人；但是对于某个人，你是他的整个世界。纵然伤心，也不要愁眉不展，因为你不知是谁会爱上你的笑容。</p> 
</body> 
</html> 
这 段代码对<p>的首字符样式定义在IE6上看是没有效果的（IE7没测试），而在p:first-letter和{font- size:300%}加上空格，也就是p:first-letter {font-size:300%}后，显示就正常了。但是同样的代码，在FireFox下看是正常的。按道理说，p:first- letter{font-size:300%}的写法是没错的。那么问题出在哪里呢？答案是伪类中的连字符”-”。IE有个BUG，在处理伪类时，如果伪 类的名称中带有连字符”-”，伪类名称后面就得跟一个空格，不然样式的定义就无效。而在FF中，加不加空格都可以正常处理。

对css缩写的支持问题： 
不论是ie 还是ff对css的缩写都有一小点问题 
比如 
border: 0xp solid #fff;两个浏览器支持都没有问题 
但对于四个边的magin不同情况下，就不能用这种缩写了，无论是ie还是ff又会出现边界解释错误，而导致页面变形 
正确缩写： 
border-width:0px 1px 2px 3px; 
border-style:solid; 
border-color:#fff;
第二点是 ie对于css的magin padding 等默认值为0px，但ff却不一样，为了保持外观的统一性，即使padding为0你也要写上，以免ff在浏览中的错位。
 
IE与Firefox的CSS兼容大全
1.DOCTYPE 影响 CSS 处理 
2.FF: div 设置 margin-left, margin-right 为 auto 时已经居中, IE 不行 
3.FF: body 设置 text-align 时, div 需要设置 margin: auto(主要是 margin-left,margin-right) 方可居中 
4.FF: 设置 padding 后, div 会增加 height 和 width, 但 IE 不会, 故需要用 !important 多设一个 height 和 width
5.FF: 支持 !important, IE 则忽略, 可用 !important 为 FF 特别设置样式，值得注意的是，一定要将xxxx !important 这句放置在另一句之上 
6.div 的垂直居中问题: vertical-align:middle; 将行距增加到和整个DIV一样高 line-height:200px; 然后插入文字，就垂直居中了。缺点是要控制内容不要换行 
7.cursor: pointer 可以同时在 IE FF 中显示游标手指状， hand 仅 IE 可以 
8.FF: 链接加边框和背景色，需设置 display: block, 同时设置 float: left 保证不换行。参照 menubar, 给 a 和 menubar 设置高度是为了避免底边显示错位, 若不设 height, 可以在 menubar 中插入一个空格。
9.在mozilla firefox和IE中的BOX模型解释不一致导致相差2px解决方法：div{margin:30px!important;margin:28px;} 
注意这两个margin的顺序一定不能写反，据阿捷的说法!important这个属性IE不能识别，但别的浏览器可以识别。所以在IE下其实解释成这样：div{maring:30px;margin:28px} 
重复定义的话按照最后一个来执行，所以不可以只写margin:XXpx!important;
 
10.IE5 和IE6的BOX解释不一致 
IE5下div{width:300px;margin:0 10px 0 10px;} 
div 的宽度会被解释为300px-10px(右填充)-10px(左填充)最终div的宽度为280px，而在IE6和其他浏览器上宽度则是以 300px+10px(右填充)+10px(左填充)=320px来计算的。这时我们可以做如下修改div{width:300px!important;width :340px;margin:0 10px 0 10px} 
关于这个是什么我也不太明白，只知道IE5和firefox都支持但IE6不支持，如果有人理解的话，请告诉我一声，谢了！：）
 
11.ul标签在Mozilla中默认是有padding值的,而在IE中只有margin有值所以先定义ul{margin:0;padding:0;} 
就能解决大部分问题
注意事项：
 1、float的div一定要闭合。
例如：(其中floatA、floatB的属性已经设置为float:left;)<#div id=\"floatA\" > 
<#div id=\"floatB\" > 
<#div id=\"NOTfloatC\" > 
这里的NOTfloatC并不希望继续平移，而是希望往下排。 
这段代码在IE中毫无问题，问题出在FF。原因是NOTfloatC并非float标签，必须将float标签闭合。 
在<#div class=\"floatB\"> 
<#div class=\"NOTfloatC\"> 
之间加上<#div class=\"clear\"> 
这个div一定要注意声明位置，一定要放在最恰当的地方，而且必须与两个具有float属性的div同级，之间不能存在嵌套关系，否则会产生异常。 
并且将clear这种样式定义为为如下即可：.clear{ 
clear:both;}
此外，为了让高度能自动适应，要在wrapper里面加上overflow:hidden;

9.如何居中一个浮动元素?
设置容器的浮动方式为相对定位
然后确定容器的宽高 比如宽500 高 300 的层
然后设置层的外边距
Div{
Width:500px ;
height:300px; 
Margin: -150px 0 0 -250px;
position: absolute;
left:50%;
top:50%;
}


10.有没有关注HTML5和CSS3?如有请简单说一些您对它们的了解情况！
在HTML 5平台上，视频，音频，图象，动画，以及同电脑的交互都被标准化。那么我们来看一下HTML5的技术概览有哪些： 
HTML5新增和移除的元素
HTML5新增了很多多媒体和交互性元素如video, audio，在HTML4当中如果要嵌入一个视频或是音频的话需要引入一大段的代码，还有兼容各个浏览器，而HTML5只需要通过引入一个标签就可以，就像img标签一样方便。
HTML5对表单的支持
HTML5 提供了强大的控件类型如url, email, date, tel等，强大的约束属性，如required表示必填，文件上传的accept属性，以及一些表单重复元素模型的支持，HTML5在提交表单的时候还可 以设置提交的方式为XML提交方式，这样服务器端接收到的数据将是XML格式，HTML5的表单被定义为“Web Forms 2.0”，目前opera9.5+对Web Forms 2.0的支持较为完美。
HTML5 DOM变化
HTML5的Javascript APIs
HTML5在Javascript上面新增了哪些API呢？
Video/Audio: HTML5为Video和Audio提供了API来让开发者控制他们自己的用户界面，如可以播放或暂停媒体内容。
CSS3
CSS3对于我们Web开发者来说不只是新奇的技术，更重要的是这些全新概念的web应用给我们带来更多无限的可能性，也极大地提高了我们的开发效率。我们将不必再依赖图片或者Javascript 去完成圆角、多背景、用户自定义字体、3D动画、渐变、盒阴影、文字阴影、透明度等提高Web设计质量的特色应用。
CSS3对于动画的支持
CSS3 支持的动画类型有：transform(变换)、transition(过渡)和animation(动画)。你可以对特定的属性设置 transition，transiton和animation的区别不大，animation的动画是自己定义的，面向的更多的是脚本开发者，往往更加 复杂。

11.你怎么来实现下面这个设计图,主要讲述思路 （效果图省略）

13:如果让你来制作一个访问量很高的大型网站，你会如何来管理所有CSS文件、JS与图片？
14：你对前端界面工程师这个职位是怎么样理解的？它的前景会怎么样？



[Javascript]
1：js是什么，js和html 的开发如何结合？

2.怎样添加、移除、移动、复制、创建和查找节点
3.怎样使用事件以及IE和DOM事件模型之间存在哪些主要差别
4.面向对象编程:b怎么继承a
5.看看下面alert的结果是什么
view sourceprint?1.function b(x, y, a) { 
.arguments[2] = 10; 
.alert(a); 
} 
b(1, 2, 3);
如果函数体改成下面，结果又会是什么？
a = 10; 
alert(arguments[2] );

6.请编写一个JavaScript函数 parseQueryString，它的用途是把URL参数解析为一个对象
var obj = parseQueryString(url); 
alert(obj.key0)  // 输出0

7.ajax是什么?  ajax的交互模型? 同步和异步的区别? 如何解决跨域问题?
ajax(动态网站静态化)伴随的goole 的推动，越来越多的站点开始使用了，在开大ajax(动态网站静态化)程序的时候会遇到很多的问题，主要有以下几个方面： 
    1.跨浏览器问题 
    2.历史后退状态问题 

    3.跨域问题 
    跨浏览器的问题因为现在有很多的开元的框架已经解决了，我们无需为此而烦恼。
    历史后退状态问题我们可以使用一个数组来保存历史纪录，然后把这些数据村到历史对象中去，中的也可以解决，并且还有很多的开元框架给与支持，这样问题就不是很大。 
    跨域的问题就不是很好的解决，但是还是有办法的，一下给出一些基本的解决方案供大家选择： 
    1.使用代理，你可以使用web端的程序编写代理程序，把所有的ajax(动态网站静态化)请求的数据进行转发，web程序可以使php(做为现在的主流 开发语言)，jsp(SUN企业级应用的首选)，asp等所有的编程语言。相信大家对这种方式一定很熟悉，这里就不详细的介绍了。 
    2.使用iframe的方式来定势的刷新叶面，这种方式只是取得数据来显示，并不能真正的和求得的数据进行交互，转化成本页面的动态数据，不是很可取，应用也不是很多，我也忽略不去讨论了。 
    3.使用apache(Unix平台最流行的WEB服务器平台)的代理功能，主要就是apache(Unix平台最流行的WEB服务器平台)的方向代理， 或者是url从定向，你也可以把其他的站点直接的挂在自己的网站上，这样的方式可能会友邦权的问题，多的九部介绍了，有兴趣的本有可以自己实践以下。 
    4.使用《script》标签的方式，这样的话就可以保正使用真正的ajax(动态网站静态化)来跨域，并且可以使用返回来的数据，发誓很简单，在我们的后台程序处理后的到的结果都直接的用javascript 的方式返回，在我们的html中直接的使用返回数据的变量就可以了一个简单的例子 

8.什么是闭包？下面这个ul，如何点击每一列的时候alert其index?
<ul id=”test”> 
<li>这是第一条</li><li>这是第二条</li><li>这是第三条</li> 
</ul>

9.最近看的一篇Javas 
cript的文章是？

10.常使用的库有哪些？常用的前端开发工具？开发过什么应用或组件？
pageSpeed .Yslow,Fiddler、fireBug
11.说说YSlow(可以详细一点) 
 这个插件可以分析网站的页面，并告诉你为了提高网站性能，如何基于某些规则而进行优化。
网页制作方向的题目
1.什么是网站重构？div+css的布局较table布局有什么优点？
2.如何理解css盒模型？
3.平时做网页经常使用哪些hack?
4.如何理解表现与内容相分离？
5.如何解决ie6的双边距问题？
6. 如何定义高度为1px的容器？{heigh：1px; width:10px; background:#000; overflow:hidden}ie6下这个问题是默认行高造成的，overflow:hidden | zoom:0.08 | line- height:1px这样也可以解决
7.如何实现一个层在浏览器中垂直左右居中？margin：auto
8.如何解决ie6的3像素问题？_zoom:1; margin-left: value; _margin-left: value-3px;
9.为什么FF下文本无法撑开容器的高度?如何解决？ 清楚浮动
10. 怎么样才能让层显示在FLASH之上呢? 解决的办法是给FLASH设置透明属性<param name="wmode" value="transparent" />或者<param name="wmode" value="opaque" />
 
1、 答：把"未采用CSS，大量使用HTML进行定位、布局，或者虽然已经采用CSS，但是未遵循HTML结构化标准的站点"变成"让标记回归标记的原本意 义。通过在HTML文档中使用结构化的标记以及用CSS控制页面表现，使页面的实际内容与它们呈现的格式相分离的站点。"的过程就是网站重构
网站为什么要进行重构（网站重构的好处）
a、使页面加载得更快速；
b、降低带宽带来的费用：节约成本；
c、让你在修改设计时更有效率而代价更低；
d、帮助你的整个站点保持视觉的一致性；
e、更利于搜索引擎的检索（符合SEO的规范）；
f、令站点更容易被各种浏览器和用户访问（包括手机、PDA和残障人士使用的文字浏览器）；
g、兼容不容忽视的Mozilla系浏览器（Firefox份额）；
h、提高你的职场竞争实力(事实上也就是降低失业的风险)。
div+css的布局较table布局有什么优点:
1、改版的时候更方便 只要改css文件。2、页面加载速度更快、结构化清晰、页面显示简洁。3、表现与结构相分离。4、易于优化（seo）搜索引擎更友好，排名更容易靠前。
 
答：2.如何理解css盒模型 ： 每个HTML元素都是长方形盒子 外边局(margin)、内边距(padding)、边框(border);
答：3.平时做网页用的css hack 
  Ie6 * _; ie7 *, *+,!important; ff !important.
 
 
答：4.表现与结构相分离简单的说就是HTML中只有标签元素 表现完全是由CSS文件控制的
 
答：5.解决ie6双边距问题块级元素就加display：inline；行内元素转块级元素display：inline后面再加display：table
 6.如何定义高度为1px的容器？
{heigh：1px; width:10px; background:#000; overflow:hidden}ie6下这个问题是默认行高造成的，overflow:hidden | zoom:0.08 | line-height:1px这样也可以解决
7.如何实现一个层在 浏览器中垂直左右居中？
margin：auto
8.如何解决ie6的3像素 问题？
_zoom:1;  margin-left: value; _margin-left: value-3px;
9.为什么FF下文本无法撑开容器的高度?如何解决？
清除浮动 .clear{ clear:both; height:0px; overflow:hidden;}

10.怎么样才能让层显示在FLASH之上呢? 
解决的办法是给FLASH设置透明属性
<param name="wmode" value="transparent" />或者<param name="wmode" value="opaque" />

补充:
1、margin-left:10px在FF和IE6下显示问题。IE6显示 20px,FF显示10px。
   用!important就可以解决了。margin-left:10px !important;margin-left:5px;
2、cursor:hand在FF不显示小手，如何解决？
   一句话：cursor;pointer;
3、要求在FF显示height为20px;IE6下显示height为25px;IE7下显示height为30px.

   #test{height:20px;}
   *html #test{height:25px;}
   *+html #test{height:30px;}
   这个以前我们说过，请参考【IE6的疯狂Bug之九】解决CSS兼容性最常用的"Haker"
   三个就写上，FF只认识第一个#test,IE6只认识第二个*html #test，IE7只认识第三个*+html #test
  PS：DTD必须加上<!DOCTYPE HTML PUBLIC “-//W3C//DTD HTML 4.01 Transitional//EN”　”http://www.w3.org/TR/html4/loose.dtd“>要不还是不认。

4、在IE中内容会自适应高度，而FF不会自适应高度。
在要自适应高度的层中加一个层，样式为
.clear{clear:both;font-size:0px;height:1px}，
这样解决有一个小小的问题，高度会多一个像素。还有一种解决方法，给当前层加上一个伪类
#test:after {content: "."; display: block;   height: 0; clear: both; visibility: hidden;}
 
1.超链接访问过后hover样式就不出现的问题?
被点击访问过的超链接样式不在具有hover和active了,解决方法是改变CSS属性的排列顺序: L-V-H-A
2.IE6的双倍边距BUG
例如:
<style type="text/css">
    body {margin:0}
    div { float:left; margin-left:10px; width:200px; height:200px; border:1px solid red }
</style>
浮动后本来外边距10px,但IE解释为20px,解决办法是加上display:inline
3.为什么FF下文本无法撑开容器的高度?
标准浏览器中固定高度值的容器是不会象IE6里那样被撑开的,那我又想固定高度，又想能被撑开需要怎样设置呢？办法就是去掉he ight设置min-height:200px; 这里为了照顾不认识min-height的IE6 可以这样定义：
div { height:auto!important; height:200px; min-height:200px; }
4.为什么web标准中IE无法设置滚动条颜色了?
原来样式设置：
<style type="text/css">
body { scrollbar-face-color:#f6f6f6; scrollbar-highlight-color:#fff; scrollbar-shadow-color:#eeeeee; scrollbar-3dlight-color:#eeeeee; scrollbar-arrow-color:#000; scrollbar-track-color:#fff; scrollbar-darkshadow-color:#fff; }
</style>
解决办法是将body换成html
5.为什么无法定义1px左右高度的容器?
IE6下这个问题是因为默认的行高造成的，解决的方法也有很多，例如：overflow:hidden | zoom:0.08 | line-height:1px
6.怎么样才能让层显示在FLASH之上呢?
解决的办法是给FLASH设置透明:
<param name="wmode" value="transparent" />
7.怎样使一个层垂直居中于浏览器中?
<style type="text/css">
<!--
div {
position:absolute;
top:50%;
left:50%;
margin:-100px 0 0 -100px;
width:200px;
height:200px;
border:1px solid red;
}
-->
</style>
这里使用百分比绝对定位，与外补丁负值的方法，负值的大小为其自身宽度高度除以二
8、firefox嵌套div标签的居中问题的解决方法
假定有如下情况：
<div id="a">
    <div id="b"> </div>
</div>
如果要实现b在a中居中放置，一般只需用CSS设置a的text-align属性为center。这样的方法在IE里看起来一切正常；但是在Firefox中b却会是居左的。
解决办法就是设置b的横向margin为auto。例如设置b的CSS样式为：margin: 0 auto;。


```