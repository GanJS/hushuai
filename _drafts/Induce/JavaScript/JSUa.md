title: 浏览器版本判断
date: 2016-02-27 18:29:00
description: 
categories:
- JavaScript
tags:
- JavaScript
toc: true
author:
comments:
original:
permalink: 
---

　　**自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why

<!-- more -->
## 判断浏览器为移动端

<script type="text/javascript">
    browserRedirect();  
    function browserRedirect(){
        var sUA = navigator.userAgent.toLowerCase();
        var bIsIpad = sUA.match(/ipad/i) == 'ipad';
        var bIsIphoneOs =  sUA.match(/iphone os/i) == 'iphone os';
        var bIsMidp = sUA.match(/midp/i) == 'midp';
        var bIsUc7 = sUA.match(/rv:1.2.3.4/i) == 'rv:1.2.3.4';
        var bIsUc = sUA.match(/ucweb/i) == 'ucweb';
        var bIsAndroid = sUA.match(/android/i) == 'android';
        var bIsCE = sUA.match(/windows ce/i) == 'windows ce';
        var bIsWM = sUA.match(/windows mobile/i) == 'windows mobile';

        if(bIsIpad || bIsIphoneOs || bIsMidp || bIsUc7 || bIsUc || bIsAndroid || bIsCE || bIsWM){
            //phone
        }else{
            //PC
        }
    }
</script>