title: 移动端横屏提示动画
date: 2016-02-28 18:29:00
description: 
categories:
- Demo
tags:
- CSS3
toc: true
author:
comments:
original:
permalink: 
---
　　**移动端横屏问题：**由于屏幕的问题，在特定的开发条件下，实际上要求我们必须竖屏查看H5展示。
<!-- more -->
## 展示效果

[Demo](/CSS3/MobileRotate/ "移动端横屏提示动画")
<iframe width="100%" height="600px" src="/CSS3/MobileRotate/"></iframe>

### 强制竖屏

```
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
<!-- 适应移动端end -->
```

## HTML代码

```
<div id="MoblileR" class="mob-con">
    <div class="mob-cen">
        <i></i>
        <div>为了更好的体验，请将手机/平板竖过来</div>
    </div>
</div>
```

## CSS代码

```
.mob-con{
    width: 100%;
    height: 100%;
    display: none;
    position: absolute;
    left: 0;
    top: 0;
    background: #32373b;
    z-index: 9990;
}
.mob-cen{
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
    z-index: 9999;
}
.mob-cen i{
    margin: auto;
    display: block;
    width: 128px;
    height: 194px;
    /*background: url(../images/hengping.png 0 0 no-repeat);*/
    background: url(images/hengping.png);
    background-size: 128px 194px;
    animation: mobileR 1.5s ease infinite alternate;
    -webkit-animation: mobileR 1.5s ease infinite alternate;
}
.mob-cen div{
    font-size: 22px;
    margin-top: 20px;
    color: #ffd40a;
}
@keyframes mobileR{
    0% {
        -webkit-transform: rotate(-90deg);
    }
    30% {
        -webkit-transform: rotate(-90deg);
    }
    70% {
        -webkit-transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(0deg);
    }
}
@-webkit-keyframes mobileR{
    0% {
        -webkit-transform: rotate(-90deg);
    }
    30% {
        -webkit-transform: rotate(-90deg);
    }
    70% {
        -webkit-transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(0deg);
    }
}
```

## 屏幕判断

### 方法一

```
/*方法一：*/
/* 媒体查询 orientation,定义'height'是否大于或等于'width'。值portrait代表是,landscape代表否  */
@media screen and (orientation:landscape) {
    .mob-con{
        display: block;
    }
}
```

### 方法二

```
<!-- 方法二： -->
//判断屏幕横屏
function oMobl(){
    if(document.documentElement.clientHeight >= document.documentElement.clientWidth){
        return "protrait";
    }else{
        return "landscape";
    }
}
//显示实例提示
function oMobx(){
    var MoblieR = document.getElementById("MoblileR");
    var oMobs = oMobl();
    if(oMobs == "protrait"){
        MoblieR.style.display = "none";
    }else{
        MoblieR.style.display = "block";
    }
}
function oInit(){
    oMobx();
    window.addEventListener("onorientationchange" in window ? "orientationchange" : "resize",function(){
        setTimeout(oMobx,200);
    })
}
oInit();
```

[Mobile Web开发基础之四————处理设备的横竖屏](http://blessdyb.iteye.com/blog/1537076 "window.orientation属性与onorientationchange事件")
[检测移动设备横竖屏](http://www.cnblogs.com/xbf321/p/4081829.html "检测移动设备横竖屏")