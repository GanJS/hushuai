title: 前端插件使用
date: 2016-04-02 14:11:20
description: 
categories:
- Plug
tags:
- Plug
toc: true
author:
comments:
original:
permalink: 
---

　　**前端插件使用：**

<!-- more -->

# 插件使用：


## 插件：懒加载
文档：[vvo/lazyload](https://github.com/vvo/lazyload "")
条件：
```javascript
<script src="http://v2.jingqubao.com/apps/w3g/_static/js/lib/LazyLoad/lazyload_base.js"></script>
```

```html
<img onload="lzld(this)" data-src="real/image/src.jpg" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">
```

## 插件：图片懒加载插件 Vue-Lazyload，现在支持 Vue2.0 的啦
文档：[图片懒加载插件 Vue-Lazyload，现在支持 Vue2.0 的啦](http://gold.xitu.io/entry/57b5c3585bbb50006305becb/detail?utm_source=gold_browser_extension "")
条件：
```javascript
```

```html
```

```scss
```

## 插件：轮播图
文档：[]( "")
[API]( "")
条件：独立
```javascript
<script src="http://v2.jingqubao.com/apps/w3g/_static/js/lib/swipeSlide.min.js"></script>

<script type="text/javascript">
function SwipeSlide(){
    $('.banner').swipeSlide({
        continuousScroll: true,
        speed : 10000000000000000,
        transitionType : 'cubic-bezier(0.22, 0.69, 0.72, 0.88)',
        // cubic-bezier(.87,.13,.95,.57)
        callback : function(i){
            $('.dot').children().eq(i).addClass('cur').siblings().removeClass('cur');
        }
    });
    $(function(){
        var oDot = $('.banner').find("li");
        var oDiv = '<span class="cur"></span>';
        for(i=3;i<oDot.length;i++){oDiv = oDiv + '<span></span>';}
        $('.dot').html(oDiv);
    });
}
SwipeSlide();
</script>
```

```html
<div class="banner">
    <ul>
        <li><a href="javascript:;"><img data-src="http://7u2psp.com2.z0.glb.qiniucdn.com/57352b4f2d84a807346.jpeg?imageView2/1/w/640/h/600/q/100" onload="lzld(this)" src="http://7u2psp.com1.z0.glb.clouddn.com/app/loading.jpg?imageView2/1/w/640/h/600/q/80" /></a></li>
        <li><a href="javascript:;"><img data-src="http://7u2psp.com2.z0.glb.qiniucdn.com/573be1ddeb78e629541.jpeg?imageView2/1/w/640/h/600/q/100" onload="lzld(this)" src="http://7u2psp.com1.z0.glb.clouddn.com/app/loading.jpg?imageView2/1/w/640/h/600/q/80" /></a></li>
        <li><a href="javascript:;"><img data-src="http://7u2psp.com2.z0.glb.qiniucdn.com/573a847bd02ee355436.jpg?imageView2/1/w/640/h/600/q/100" onload="lzld(this)" src="http://7u2psp.com1.z0.glb.clouddn.com/app/loading.jpg?imageView2/1/w/640/h/600/q/80" /></a></li>
        <li><a href="javascript:;"><img data-src="http://7u2psp.com2.z0.glb.qiniucdn.com/573552718cde5938193.jpeg?imageView2/1/w/640/h/600/q/100" onload="lzld(this)" src="http://7u2psp.com1.z0.glb.clouddn.com/app/loading.jpg?imageView2/1/w/640/h/600/q/80" /></a></li>
        <li><a href="javascript:;"><img data-src="http://7u2psp.com2.z0.glb.qiniucdn.com/Ft-W6_ohnPn4it5HqBm-W0tmnoM9?imageView2/1/w/640/h/600/q/100" onload="lzld(this)" src="http://7u2psp.com1.z0.glb.clouddn.com/app/loading.jpg?imageView2/1/w/640/h/600/q/80" /></a></li>
        <li><a href="javascript:;"><img data-src="http://7u2psp.com2.z0.glb.qiniucdn.com/57352e64250ab525310.jpeg?imageView2/1/w/640/h/600/q/100" onload="lzld(this)" src="http://7u2psp.com1.z0.glb.clouddn.com/app/loading.jpg?imageView2/1/w/640/h/600/q/80" /></a></li>
    </ul>
    <div class="dot"></div>
</div>
```

```scss
.banner{
  width: size(375);
  height: size(300);
  position: relative;
  overflow: hidden;
  ul{
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    li{
      list-style: none;
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      :first-child{
        z-index: 1;
      }
      a{
        display: block;
        overflow: hidden;
      }
      img{
        width: 100%;
        border: none;
      }
      p{
        text-align: center;
        background: $font-c-1;
        padding: 6px 0;
        @include font-size(14px);
      }
    }
  }
  .dot{
    position: absolute;
    left: 50%;
    width: 100%;
    bottom: size(8);
    text-align: center;
    font-size: 0;
    transform: translate(-50%,0);
    -webkit-transform: translate(-50%,0);
    -ms-transform: translate(-50%,0);
    span{
      display: inline-block;
      width: size(8);
      height: size(8);
      margin-left: size(8);
      border-radius: size(8);
      background: $bg-c-2;
    }
    .cur{
      background: $bg-c-1;
    }
  }
}
```

## 插件：平滑卡片
Github swiper 最现代的移动触摸滑块
文档：[nolimits4web/Swiper](https://github.com/nolimits4web/swiper/ "")
[API](https://github.com/nolimits4web/Swiper/blob/Swiper2/API.md "")
条件：独立
```javascript
<script src="http://v2.jingqubao.com/apps/w3g/_static/js/lib/swiper/swiper.min.js"></script>
<script type="text/javascript">
new Swiper('.swiper-container.items', {
    slidesPerView: 'auto',
    // spaceBetween: 20,//设置卡片之间的距离
    grabCursor: true,
    breakpoints: {
        320: {
            // spaceBetween: 15
        }
    }
});
</script>
```

```html
<div class="swiper-container items">
    <div class="swiper-wrapper">
        <div class="swiper-slide">内容部分</div>
        <div class="swiper-slide">内容部分</div>
        <div class="swiper-slide">内容部分</div>
        <div class="swiper-slide">内容部分</div>
    </div>
</div>
```

```scss
.swipz{
  overflow: hidden;
  .swiper-container{
    margin: 0 auto;
    position: relative;
    overflow: hidden;
    z-index: 1;
    background: $bg-c-1;
    .swiper-wrapper{
      display: inline-block;
      position: relative;
      width: size(160);
      height: 100%;
      z-index: 1;
      display: flex;
      transition-property: transform;
      box-sizing: content-box;
      transform: translate3d(0,0,0);
      .swiper-slide{
        padding: size(10);
        margin: size(10);
        -webkit-flex-shrink: 0;
        -ms-flex: 0 0 auto;
        flex-shrink: 0;
        width: 100%;
        position: relative;
        border-radius: size(6);
        box-shadow: 0 1px 4px 0 rgba(0,26,47,.18);
        background: $bg-c-2;
        color: $bg-c-1;
        h1{
          @include font-size(20px);
          line-height: size(40);
          text-align: center;
          font-weight: bold;
        }
        p{
          line-height: size(28);
          @include font-size(12px);
          span{
            font-weight: bold;
          }
        }
      }
    }
  }
  .items{
    overflow: visible;
    .swiper-slide{
      width: auto;
    }
  }
}
```









## 插件：
文档：[]( "")
条件：
```javascript
```
```html
```
```scss
```





DOM
document.title = '网页标题';

getAttribute vs setAttribute

oDiv.className = '类名';

<!-- 创建html元素 -->
document.createElement("div");

<!-- 将元素添加到 -->
document.body.appendChild(oDiv);

<!-- 将元素从移除 -->
document.body.removeChild(oDiv);

window
window.location
<!-- 链接 -->
window.location.href
<!-- #锚点名 -->
window.location.hash
<!-- 查询参数 -->
window.location.search
<!-- 域名中的路径 -->
window.location.pathname

<!-- 获取字符串“——”之后的内容 -->
sum.substring(sum.indexOf('_') + 1, sum.length)
<!-- 获取字符串中到制定字符截取 -->
sum.substring(0,sum.indexOf('_'))

```
<script type="text/javascript">
function GetRequest() { 
    var ourl = location.search;
    var theRequest = new Object();
    if(ourl.indexOf('?') != -1){
        var str = ourl.substr(1);
        var strs = str.split('&');
        for(var i=0;i<strs.length;i++){
            theRequest[strs[i].split('=')[0]] = unescape(strs[i].split('=')[1]);
        }
    }
    return theRequest;
}
<!-- 将链接中的查询参数存储中数组 -->
var Request = new GetRequest();
</script>
```