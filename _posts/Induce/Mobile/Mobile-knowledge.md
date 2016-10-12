title:  移动前端知识总结
date: 2016-01-28 14:11:20
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
　　移动时代本以为到移动端，就再也不用担心IE兼容问题，可是移动的设备，其实是更大的坑。面对这些问题，一开始我们只能在未知中试错，知道错误的方案，才能更容易寻找正确的解决问题思路。可看到移动web在业界不断趋向于成熟，各种框架和解决方案，不断的涌现让移动端开发不再是个噩梦。
这几天把想到的一点经验先罗列出来，后续会持续更新，这篇文章可以给刚接触webapp开发的同学带来帮助，任何疑问欢迎留言探讨！
<!-- more -->

| 前因 | 后果 |
|  ---- | ---- |
|设备更新换代快    |  低端机遗留下问题、高端机带来新挑战
|浏览器厂商不统一  |  兼容问题多
|网络更复杂        |  弱网络，页面打开慢
|低端机性能差      |  页面操作卡顿
|HTML5新技术多     |  学习成本不低
|未知问题          |  坑多

### 常见问题

```
移动端如何定义字体font-family
中文字体使用系统默认即可，英文用Helvetica
/* 移动端定义字体的代码 */body{font-family:Helvetica;}
```

参考《[移动端使用字体的思考](http://www.cnblogs.com/PeunZhang/p/3592096.html)》
移动端字体单位font-size选择px还是rem

```
对于只需要适配少部分手机设备，且分辨率对页面影响不大的，使用px即可
对于需要适配各种移动设备，使用rem，例如只需要适配iPhone和iPad等分辨率差别比较挺大的设备
```

### meta基础知识
#### H5页面窗口自动调整到设备宽度，并禁止用户缩放页面

```
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />
```

#### 忽略将页面中的数字识别为电话号码

```
<meta name="format-detection" content="telephone=no" />
```

#### 忽略Android平台中对邮箱地址的识别

```
<meta name="format-detection" content="email=no" />
```

#### 当网站添加到主屏幕快速启动方式，可隐藏地址栏，仅针对ios的safari

```
<meta name="apple-mobile-web-app-capable" content="yes" />
<!-- ios7.0版本以后，safari上已看不到效果 -->
```

体验demo，解决在主屏幕打开页面后，点击页面链接不会跳转到系统自带的Safari
![](http://upload-images.jianshu.io/upload_images/1064727-354d2f3142523da6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 将网站添加到主屏幕快速启动方式，仅针对ios的safari顶端状态条的样式

```
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<!-- 可选default、black、black-translucent -->
```

### viewport模板
#### viewport模板——通用


```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no" name="viewport">
<meta content="yes" name="apple-mobile-web-app-capable">
<meta content="black" name="apple-mobile-web-app-status-bar-style">
<meta content="telephone=no" name="format-detection">
<meta content="email=no" name="format-detection">
<title>标题</title>
<link rel="stylesheet" href="index.css">
</head>
<body>这里开始内容</body>
</html>
```


#### viewport模板 - target-densitydpi=device-dpi，android 2.3.5以下版本不支持


```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=750, user-scalable=no, target-densitydpi=device-dpi">
<!-- width取值与页面定义的宽度一致 -->
<meta content="yes" name="apple-mobile-web-app-capable">
<meta content="black" name="apple-mobile-web-app-status-bar-style">
<meta content="telephone=no" name="format-detection">
<meta content="email=no" name="format-detection">
<title>标题</title>
<link rel="stylesheet" href="index.css">
</head>
<body>这里开始内容</body>
</html>
```


参考案例：[http://action.weixin.qq.com/payact/readtemplate?t=mobile/2015/wxzfsht/index_tmpl](http://action.weixin.qq.com/payact/readtemplate?t=mobile/2015/wxzfsht/index_tmpl)



### rem配置参考：

```
html{
font-size:10px}@media screen and (min-width:321px) and (max-width:375px){
html{
font-size:11px}}@media screen and (min-width:376px) and (max-width:414px){
html{
font-size:12px}}@media screen and (min-width:415px) and (max-width:639px){
html{
font-size:15px}}@media screen and (min-width:640px) and (max-width:719px){
html{
font-size:20px}}@media screen and (min-width:720px) and (max-width:749px){
html{
font-size:22.5px}}@media screen and (min-width:750px) and (max-width:799px){
html{
font-size:23.5px}}@media screen and (min-width:800px){
html{
font-size:25px}}
```

体验demo：[http://1.peunzhang.sinaapp.com/demo/rem/index.html](http://1.peunzhang.sinaapp.com/demo/rem/index.html)

```
移动端touch事件(区分webkit 和 winphone)
当用户手指放在移动设备在屏幕上滑动会触发的touch事件
以下支持webkit
touchstart——当手指触碰屏幕时候发生。不管当前有多少只手指
touchmove——当手指在屏幕上滑动时连续触发。通常我们再滑屏页面，会调用event的preventDefault()可以阻止默认情况的发生：阻止页面滚动
touchend——当手指离开屏幕时触发
touchcancel——系统停止跟踪触摸时候会触发。例如在触摸过程中突然页面alert()一个提示框，此时会触发该事件，这个事件比较少用
```

```
TouchEvent
touches：屏幕上所有手指的信息
targetTouches：手指在目标区域的手指信息
changedTouches：最近一次触发该事件的手指信息
touchend时，touches与targetTouches信息会被删除，changedTouches保存的最后一次的信息，最好用于计算手指信息
```

参数信息(changedTouches[0])
clientX、clientY在显示区的坐标
target：当前元素

参考：[https://developer.mozilla.org/en-US/docs/Web/API/TouchEvent](https://developer.mozilla.org/en-US/docs/Web/API/TouchEvent)
以下支持winphone 8
MSPointerDown——当手指触碰屏幕时候发生。不管当前有多少只手指
MSPointerMove——当手指在屏幕上滑动时连续触发。通常我们再滑屏页面，会调用css的html{
-ms-touch-action: none;}可以阻止默认情况的发生：阻止页面滚动
MSPointerUp——当手指离开屏幕时触发

移动端click屏幕产生200-300 ms的延迟响应
移动设备上的web网页是有300ms延迟的，玩玩会造成按钮点击延迟甚至是点击失效。
以下是历史原因，来源一个公司内一个同事的分享：
2007年苹果发布首款iphone上IOS系统搭载的safari为了将适用于PC端上大屏幕的网页能比较好的展示在手机端上，使用了双击缩放(double tap to zoom)的方案，比如你在手机上用浏览器打开一个PC上的网页，你可能在看到页面内容虽然可以撑满整个屏幕，但是字体、图片都很小看不清，此时可以快速双击屏幕上的某一部分，你就能看清该部分放大后的内容，再次双击后能回到原始状态。
双击缩放是指用手指在屏幕上快速点击两次，iOS 自带的 Safari 浏览器会将网页缩放至原始比例。

```
原因就出在浏览器需要如何判断快速点击上，当用户在屏幕上单击某一个元素时候，例如跳转链接<a href="#">
</a>，此处浏览器会先捕获该次单击，但浏览器不能决定用户是单纯要点击链接还是要双击该部分区域进行缩放操作，所以，捕获第一次单击后，浏览器会先Hold一段时间t，如果在t时间区间里用户未进行下一次点击，则浏览器会做单击跳转链接的处理，如果t时间里用户进行了第二次单击操作，则浏览器会禁止跳转，转而进行对该部分区域页面的缩放操作。那么这个时间区间t有多少呢？在IOS safari下，大概为300毫秒。这就是延迟的由来。造成的后果用户纯粹单击页面，页面需要过一段时间才响应，给用户慢体验感觉，对于web开发者来说是，页面js捕获click事件的回调函数处理，需要300ms后才生效，也就间接导致影响其他业务逻辑的处理。
```
解决方案：
fastclick可以解决在手机上点击事件的300ms延迟
zepto的touch模块，tap事件也是为了解决在click的延迟问题

触摸事件的响应顺序
1、ontouchstart 2、ontouchmove 3、ontouchend 4、onclick

解决300ms延迟的问题，也可以通过绑定ontouchstart事件，加快对事件的响应
什么是Retina 显示屏，带来了什么问题
retina：一种具备超高像素密度的液晶屏，同样大小的屏幕上显示的像素点由1个变为多个，如在同样带下的屏幕上，苹果设备的retina显示屏中，像素点1个变为4个
在高清显示屏中的位图被放大，图片会变得模糊，因此移动端的视觉稿通常会设计为传统PC的2倍
那么，前端的应对方案是：
设计稿切出来的图片长宽保证为偶数，并使用backgroud-size把图片缩小为原来的1/2
//例如图片宽高为：200px*200px，那么写法如下.css{width:100px;height:100px;background-size:100px 100px;}

其它元素的取值为原来的1/2，例如视觉稿40px的字体，使用样式的写法为20px
.css{font-size:20px}

参考《[高清显示屏原理及设计方案](http://www.cnblogs.com/PeunZhang/p/3441110.html)》
ios系统中元素被触摸时产生的半透明灰色遮罩怎么去掉
ios用户点击一个链接，会出现一个半透明灰色遮罩, 如果想要禁用，可设置-webkit-tap-highlight-color的alpha值为0，也就是属性值的最后一位设置为0就可以去除半透明灰色遮罩
a,button,input,textarea{-webkit-tap-highlight-color: rgba(0,0,0,0;)}

部分android系统中元素被点击时产生的边框怎么去掉
android用户点击一个链接，会出现一个边框或者半透明灰色遮罩, 不同生产商定义出来额效果不一样，可设置-webkit-tap-highlight-color的alpha值为0去除部分机器自带的效果
a,button,input,textarea{-webkit-tap-highlight-color: rgba(0,0,0,0;)-webkit-user-modify:read-write-plaintext-only; }

-webkit-user-modify有个副作用，就是输入法不再能够输入多个字符
另外，有些机型去除不了，如小米2
对于按钮类还有个办法，不使用a或者input标签，直接用div标签
参考《[如何去除android上a标签产生的边框](http://www.cnblogs.com/PeunZhang/archive/2013/02/28/2907708.html)》

#### winphone系统a、input标签被点击时产生的半透明灰色背景怎么去掉

```
<meta name="msapplication-tap-highlight" content="no">
```

#### webkit表单元素的默认外观怎么重置

```
.css{-webkit-appearance:none;}
```

#### webkit表单输入框placeholder的颜色值能改变么

```
input::-webkit-input-placeholder{color:#AAAAAA;}input:focus::-webkit-input-placeholder{color:#EEEEEE;}
```

#### webkit表单输入框placeholder的文字能换行么

```
ios可以，android不行~
在textarea标签下都可以换行~
IE10（winphone8）表单元素默认外观如何重置
禁用 select 默认下拉箭头
::-ms-expand 适用于表单选择控件下拉箭头的修改，有多个属性值，设置它隐藏 (display:none) 并使用背景图片来修饰可得到我们想要的效果。
select::-ms-expand {display: none;}
```

#### 禁用 radio 和 checkbox 默认样式

```
::-ms-check 适用于表单复选框或单选按钮默认图标的修改，同样有多个属性值，设置它隐藏 (display:none) 并使用背景图片来修饰可得到我们想要的效果。
input[type=radio]::-ms-check,input[type=checkbox]::-ms-check{display: none;}
```

#### 禁用PC端表单输入框默认清除按钮

```
当表单文本输入框输入内容后会显示文本清除按钮，
::-ms-clear 适用于该清除按钮的修改，同样设置使它隐藏 (display:none) 并使用背景图片来修饰可得到我们想要的效果。
input[type=text]::-ms-clear,input[type=tel]::-ms-clear,input[type=number]::-ms-clear{display: none;}
```
#### 禁止ios 长按时不触发系统的菜单，禁止ios&android长按时下载图片

```
.css{-webkit-touch-callout: none}
```

#### 禁止ios和android用户选中文字

```
.css{-webkit-user-select:none}
```

参考《[如何改变表单元素的外观(for Webkit and IE10)](http://www.cnblogs.com/PeunZhang/p/3522603.html)》
#### 打电话发短信写邮件怎么实现

```
打电话
<a href="tel:0755-10086">打电话给:0755-10086</a>
```


```
发短信，winphone系统无效
<a href="sms:10086">发短信给: 10086</a>
```

写邮件，可参考《[移动web页面给用户发送邮件的方法](http://www.cnblogs.com/PeunZhang/p/4952783.html)》

```
<a href="mailto:peun@foxmail.com">peun@foxmail.com</a>
```

 
#### 模拟按钮hover效果

移动端触摸按钮的效果，可明示用户有些事情正要发生，是一个比较好体验，但是移动设备中并没有鼠标指针，使用css的hover并不能满足我们的需求，还好国外有个激活css的active效果，代码如下，


```
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no" name="viewport">
	<meta content="yes" name="apple-mobile-web-app-capable">
	<meta content="black" name="apple-mobile-web-app-status-bar-style">
	<meta content="telephone=no" name="format-detection">
	<meta content="email=no" name="format-detection">
	<style type="text/css">
	a{
		-webkit-tap-highlight-color: rgba(0,0,0,0);
	}
	.btn-blue{
		display:block;
		height:42px;
		line-height:42px;
		text-align:center;
		border-radius:4px;
		font-size:18px;
		color:#FFFFFF;
		background-color: #4185F3;
	}
	.btn-blue:active{
		background-color: #357AE8;
	}
	</style>
</head>
<body>
	<div class="btn-blue">按钮</div>
	<script type="text/javascript">
		document.addEventListener("touchstart", function(){
		}, true)
	</script>
</body>
</html>
```


兼容性ios5+、部分android 4+、winphone 8
要做到全兼容的办法，可通过绑定ontouchstart和ontouchend来控制按钮的类名


```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no" name="viewport">
<meta content="yes" name="apple-mobile-web-app-capable">
<meta content="black" name="apple-mobile-web-app-status-bar-style">
<meta content="telephone=no" name="format-detection">
<meta content="email=no" name="format-detection">
<style type="text/css">a{-webkit-tap-highlight-color: rgba(0,0,0,0);}.btn-blue{display:block;height:42px;line-height:42px;text-align:center;border-radius:4px;font-size:18px;color:#FFFFFF;background-color: #4185F3;}.btn-blue-on{background-color: #357AE8;}</style>
</head>
<body>
<div class="btn-blue">按钮</div>
<script type="text/javascript">var btnBlue = document.querySelector(".btn-blue");btnBlue.ontouchstart = function(){ this.className = "btn-blue btn-blue-on"}btnBlue.ontouchend = function(){ this.className = "btn-blue"}</script>
</body>
</html>
```


屏幕旋转的事件和样式

```
事件
window.orientation，取值：正负90表示横屏模式、0和180表现为竖屏模式；

window.onorientationchange = function(){
	switch(window.orientation){
		case -90: case 90: alert("横屏:" + window.orientation);
		case 0: case 180: alert("竖屏:" + window.orientation);
		break;
	}
} 
```

```
样式

//竖屏时使用的样式

@media all and (orientation:portrait) {
	.css{}
}

//横屏时使用的样式
@media all and (orientation:landscape) {
	.css{}
}
```

audio元素和video元素在ios和andriod中无法自动播放
应对方案：触屏即播

```
$('html').one('touchstart',function(){ audio.play()})
```

可参考《[无法自动播放的audio元素](http://www.cnblogs.com/PeunZhang/archive/2013/02/05/2893093.html)》


摇一摇功能

HTML5 deviceMotion：封装了运动传感器数据的事件，可以获取手机运动状态下的运动加速度等数据。

体验demo：[](http://1.peunzhang.sinaapp.com/demo/deviceMotion/index.html)
![](http://upload-images.jianshu.io/upload_images/1064727-8f498bb8f55c4844.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

手机拍照和上传图片

```
<input type="file">的accept 属性
```

```
<!-- 选择照片 -->
<input type=file accept="image/*">
<!-- 选择视频 -->
<input type=file accept="video/*">
```

#### 使用总结：

```
ios 有拍照、录像、选取本地图片功能
部分android只有选取本地图片功能
winphone不支持
input控件默认外观丑陋

微信浏览器用户调整字体大小后页面矬了，怎么阻止用户调整
原因
android侧是复写了layoutinflater 对textview做了统一处理
ios侧是修改了body.style.webkitTextSizeAdjust值

解决方案：
android使用以下代码，该接口只在微信浏览器下有效(感谢jationhuang同学提供)


/ * 页面加入这段代码可使Android机器页面不再受到用户字体缩放强制改变大小 * 但是会有一个1秒左右的延迟，期间可以考虑通过loading展示 * 仅供参考 */(function(){ if (typeof(WeixinJSBridge) == "undefined") { document.addEventListener("WeixinJSBridgeReady", function (e) { setTimeout(function(){ WeixinJSBridge.invoke('setFontSizeCallback',{"fontSize":0}, function(res) { alert(JSON.stringify(res)); }); },0); }); } else { setTimeout(function(){ WeixinJSBridge.invoke('setFontSizeCallback',{"fontSize":0}, function(res) { alert(JSON.stringify(res)); }); },0); }})();
```

#### ios使用-webkit-text-size-adjust禁止调整字体大小

```
body{-webkit-text-size-adjust: 100%!important;}

最好的解决方案：
整个页面用rem或者百分比布局
```

#### 消除transition闪屏

```
网络都是这么写的，但我并没有测试出来
.css{/*设置内嵌的元素在 3D 空间如何呈现：保留 3D*/-webkit-transform-style: preserve-3d;/*（设置进行转换的元素的背面在面对用户时是否可见：隐藏）*/-webkit-backface-visibility: hidden;}
开启硬件加速
解决页面闪白
保证动画流畅
```

```
.css { -webkit-transform: translate3d(0, 0, 0); -moz-transform: translate3d(0, 0, 0); -ms-transform: translate3d(0, 0, 0); transform: translate3d(0, 0, 0);}
```

参考《[用CSS开启硬件加速来提高网站性能](http://www.cnblogs.com/PeunZhang/p/3510083.html)》
取消input在ios下，输入的时候英文首字母的默认大写

```
<input autocapitalize="off" autocorrect="off" />
```

android 上去掉语音输入按钮
input::-webkit-input-speech-button {display: none}

android 2.3 bug
@-webkit-keyframes 需要以0%开始100%结束，0%的百分号不能去掉
after和before伪类无法使用动画animation
border-radius不支持%单位
translate百分比的写法和scale在一起会导致失效，例如-webkit-transform: translate(-50%,-50%) scale(-0.5, 1)

android 4.x bug
三星 Galaxy S4中自带浏览器不支持border-radius缩写
同时设置border-radius和背景色的时候，背景色会溢出到圆角以外部分
部分手机(如三星)，a链接支持鼠标:visited事件，也就是说链接访问后文字变为紫色
android无法同时播放多音频audio

参考《[border-radius 移动之伤](https://github.com/yisibl/blog/issues/2)》
设计高性能CSS3动画的几个要素
尽可能地使用合成属性transform和opacity来设计CSS3动画，不使用position的left和top来定位
利用translate3D开启GPU加速

参考《[High Performance Animations](http://www.html5rocks.com/en/tutorials/speed/high-performance-animations/)》
fixed bug
ios下fixed元素容易定位出错，软键盘弹出时，影响fixed元素定位
android下fixed表现要比iOS更好，软键盘弹出时，不会影响fixed元素定位
ios4下不支持position:fixed

解决方案
可用isroll.js，暂无完美方案

参考
[《移动端web页面使用position:fixed问题总结》](https://github.com/maxzhang/maxzhang.github.com/issues/2)
[《使用iScroll.js解决ios4下不支持position:fixed的问题》](http://www.cnblogs.com/PeunZhang/archive/2013/06/14/3117589.html)

#### 如何阻止windows Phone的默认触摸事件
winphone下默认触摸事件事件使用e.preventDefault是无效的
目前解决方法是使用样式来禁用
html{-ms-touch-action: none;}/* 禁止winphone默认触摸事件 */


《[Windows phone 8 touch support](http://stackoverflow.com/questions/13396297/windows-phone-8-touch-support "播放视频不全屏")



```
<!--1.目前只有ios7+、winphone8+支持自动播放2.支持Airplay的设备（如：音箱、Apple TV)播放x-webkit-airplay="true" 3.播放视频不全屏，ios7+、winphone8+支持，部分android4+支持（含华为、小米、魅族）webkit-playsinline="true" -->
<video x-webkit-airplay="true" webkit-playsinline="true" preload="auto" autoplay src="http://">
</video>
```


[体验demo：](http://1.peunzhang.sinaapp.com/demo/video/index.html)

#### 常用的移动端框架

zepto.js
语法与jquery几乎一样，会jquery基本会zepto~
最新版本已经更新到1.16
[官网：](http://zeptojs.com/)
[中文(非官网)：](http://www.css88.com/doc/zeptojs_api/)

常使用的扩展模块：
[浏览器检测：](https://github.com/madrobby/zepto/blob/master/src/detect.js)
[tap事件：](https://github.com/madrobby/zepto/blob/master/src/touch.js)

iscroll.js
解决页面不支持弹性滚动，不支持fixed引起的问题~
实现下拉刷新，滑屏，缩放等功能~
最新版本已经更新到5.0
[官网：](http://cubiq.org/iscroll-5)

underscore.js
笔者没用过，不过听说好用，推荐给大家~
该库提供了一整套函数式编程的实用功能，但是没有扩展任何JavaScript内置对象。
最新版本已经更新到1.8.2
[官网：](http://underscorejs.org/)

滑屏框架

适合上下滑屏、左右滑屏等滑屏切换页面的效果
[slip.js](https://github.com/peunzhang/slip.js)
[iSlider.js](https://github.com/peunzhang/iSlider)
[fullpage.js](https://github.com/peunzhang/fullpage)
[swiper.js](http://www.swiper.com.cn/)

#### flex布局
flex布局目前可使用在移动中，并非所有的语法都全兼容，但以下写法笔者实践过，效果良好~

```
flex：定义布局为盒模型 
flex-v：盒模型垂直布局 
flex-1：子元素占据剩余的空间 
flex-align-center：子元素垂直居中 
flex-pack-center：子元素水平居中 
flex-pack-justify：子元素两端对齐 
兼容性：ios 4+、android 2.3+、winphone8+ 

.flex{
	display:-webkit-box;
	display:-webkit-flex;
	display:-ms-flexbox;
	display:flex;
}
.flex-v{
	-webkit-box-orient:vertical;
	-webkit-flex-direction:column;
	-ms-flex-direction:column;
	flex-direction:column;
}
.flex-1{
	-webkit-box-flex:1;
	-webkit-flex:1;
	-ms-flex:1;
	flex:1;
}
.flex-align-center{
	-webkit-box-align:center;
	-webkit-align-items:center;
	-ms-flex-align:center;
	align-items:center;
}
.flex-pack-center{
	-webkit-box-pack:center;
	-webkit-justify-content:center;
	-ms-flex-pack:center;
	justify-content:center;
}
.flex-pack-justify{
	-webkit-box-pack:justify;
	-webkit-justify-content:space-between;
	-ms-flex-pack:justify;
	justify-content:space-between;
}
```


#### 示例：两端对齐

```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no" name="viewport">
<meta content="yes" name="apple-mobile-web-app-capable">
<meta content="black" name="apple-mobile-web-app-status-bar-style">
<meta content="telephone=no" name="format-detection">
<meta content="email=no" name="format-detection">
<style type="text/css">
/* 
flex：定义布局为盒模型
flex-v：盒模型垂直布局
flex-1：子元素占据剩余的空间
flex-align-center：子元素垂直居中
flex-pack-center：子元素水平居中
flex-pack-justify：子元素两端对齐 兼容性：ios 4+、android 2.3+、winphone8+  */

.flex{
	display:-webkit-box;display:-webkit-flex;display:-ms-flexbox;display:flex;}.flex-v{-webkit-box-orient:vertical;-webkit-flex-direction:column;-ms-flex-direction:column;flex-direction:column;}.flex-1{-webkit-box-flex:1;-webkit-flex:1;-ms-flex:1;flex:1;}.flex-align-center{-webkit-box-align:center;-webkit-align-items:center;-ms-flex-align:center;align-items:center;}.flex-pack-center{-webkit-box-pack:center;-webkit-justify-content:center;-ms-flex-pack:center;justify-content:center;}.flex-pack-justify{-webkit-box-pack:justify;-webkit-justify-content:space-between;-ms-flex-pack:justify;justify-content:space-between;}</style>
</head>
<body>
<div class="flex flex-pack-justify"> <div>模块一</div> <div>模块二</div> <div>模块三</div> <div>模块四</div>
</div>
</body>
</html>
```


使用注意：
flex下的子元素必须为块级元素，非块级元素在android2.3机器下flex失效
flex下的子元素宽度和高度不能超过父元素，否则会导致子元素定位错误，例如水平垂直居中

参考：
[flexyboxes](http://the-echoplex.net/flexyboxes/)
[“老”的Flexbox和“新”的Flexbox](http://www.w3cplus.com/css3/old-flexbox-and-new-flexbox.html)
[跨浏览器的Flexbox](http://www.w3cplus.com/css3/advanced-cross-browser-flexbox.html)
FastClick
消除在移动浏览器上触发click事件与一个物理Tap(敲击)之间的300延迟
参考《[FastClick](https://github.com/ftlabs/fastclick)》
Sea.js 
提供简单、极致的模块化开发体验
简单友好的模块定义规范：Sea.js 遵循 [CMD](https://github.com/cmdjs/specification/blob/master/draft/module.md) 规范，可以像 [Node.js](http://nodejs.org/) 一般书写模块代码。
自然直观的代码组织方式：依赖的自动加载、配置的简洁清晰，可以让我们更多地享受编码的乐趣。

地址：[http://seajs.org/docs/](http://seajs.org/docs/)


目录（更新于20160128）
[meta基础知识](http://www.cnblogs.com/PeunZhang/p/3407453.html#meta)
[H5页面窗口自动调整到设备宽度，并禁止用户缩放页面](http://www.cnblogs.com/PeunZhang/p/3407453.html#meta_1)
[忽略将页面中的数字识别为电话号码](http://www.cnblogs.com/PeunZhang/p/3407453.html#meta_2)
[忽略Android平台中对邮箱地址的识别](http://www.cnblogs.com/PeunZhang/p/3407453.html#meta_3)
[当网站添加到主屏幕快速启动方式，可隐藏地址栏，仅针对ios的safari](http://www.cnblogs.com/PeunZhang/p/3407453.html#meta_4)
[将网站添加到主屏幕快速启动方式，仅针对ios的safari顶端状态条的样式](http://www.cnblogs.com/PeunZhang/p/3407453.html#meta_5)
[viewport模板](http://www.cnblogs.com/PeunZhang/p/3407453.html#meta_6)

[常见问题](http://www.cnblogs.com/PeunZhang/p/3407453.html#question)
[移动端如何定义字体font-family](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_1)
[移动端字体单位font-size选择px还是rem](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_2)
[移动端touch事件(区分webkit 和 winphone)](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_3)
[移动端click屏幕产生200-300 ms的延迟响应](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_4)
[触摸事件的响应顺序](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_5)
[什么是Retina 显示屏，带来了什么问题](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_6)
[ios系统中元素被触摸时产生的半透明灰色遮罩怎么去掉](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_7)
[部分android系统中元素被点击时产生的边框怎么去掉](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_8)
[winphone系统a、input标签被点击时产生的半透明灰色背景怎么去掉](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_9)
[webkit表单元素的默认外观怎么重置](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_10)
[webkit表单输入框placeholder的颜色值能改变么](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_11)
[webkit表单输入框placeholder的文字能换行么](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_12)
[IE10（winphone8）表单元素默认外观如何重置](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_13)
[禁止ios 长按时不触发系统的菜单，禁止ios&android长按时下载图片](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_14)
[禁止ios和android用户选中文字](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_15)
[打电话发短信写邮件怎么实现](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_16)
[模拟按钮hover效果](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_17)
[屏幕旋转的事件和样式](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_18)
[audio元素和video元素在ios和andriod中无法自动播放](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_19)
[摇一摇功能](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_20) 
[手机拍照和上传图片](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_21)
[微信浏览器用户调整字体大小后页面矬了，怎么阻止用户调整](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_22)
[消除transition闪屏](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_23)
[开启硬件加速](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_24)
[取消input在ios下，输入的时候英文首字母的默认大写](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_25)
[android上去掉语音输入按钮](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_26)
[android 2.3 bug](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_27)
[android 4.x bug](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_28)
[设计高性能CSS3动画的几个要素](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_29)
[fixed bug](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_30)
[如何阻止windows Phone的默认触摸事件](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_31)
[播放视频不全屏](http://www.cnblogs.com/PeunZhang/p/3407453.html#question_32)

[常用的移动端框架](http://www.cnblogs.com/PeunZhang/p/3407453.html#api)
[zepto.js](http://www.cnblogs.com/PeunZhang/p/3407453.html#api_zepto)
[iscroll.js](http://www.cnblogs.com/PeunZhang/p/3407453.html#api_iscroll)
[underscore.js](http://www.cnblogs.com/PeunZhang/p/3407453.html#api_underscore)
[滑屏框架](http://www.cnblogs.com/PeunZhang/p/3407453.html#api_slide)
[flex布局](http://www.cnblogs.com/PeunZhang/p/3407453.html#api_flex)
[FastClick](http://www.cnblogs.com/PeunZhang/p/3407453.html#api_FastClick)
[Sea.js](http://www.cnblogs.com/PeunZhang/p/3407453.html#seajs)


移动布局：

[MDN:手机网页开发](https://developer.mozilla.org/zh-CN/docs/Web/Guide/Mobile)
[MDN:在移动浏览器中使用viewport元标签控制布局](https://developer.mozilla.org/zh-CN/docs/Mobile/Viewport_meta_tag)
[移动前端开发和 Web 前端开发的区别是什么](https://www.zhihu.com/question/20269059)
[Alloyteam移动开发规范概述](http://alloyteam.github.io/Spirit/modules/Standard/)
[手机/移动前端开发需要注意的20个要点](http://sentsin.com/web/54.html)
[w3cplus响应式技术资源](http://www.w3cplus.com/responsive)
[浅谈移动Web开发](http://www.infoq.com/cn/articles/development-of-the-mobile-web-deep-concept)
[Alloyteam Mars](https://github.com/AlloyTeam/Mars)
[移动WEB开发入门](http://junmer.github.io/mobile-dev-get-started/)
[移动开发资源集合](https://github.com/jtyjty99999/mobileTech)
[The Mobile Web Handbook](http://quirksmode.org/mobilewebhandbook/)
[MobileWeb 适配总结](http://www.w3ctech.com/topic/979)
[移动前端不得不了解的html5 head 头标签](http://www.css88.com/archives/5480)