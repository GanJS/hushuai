title: BOOS信息展示与收缩
date: 2016-03-02 18:29:00
description: 
categories:
- Demo
tags:
- JavaScript
toc: true
author:
comments:
original:
permalink: 
---
　　**BOOS直聘：**最近在找工作，用BOOS直聘，感觉用户体验很好，看到那个显示部分信息，就想用原生写写看看。
<!-- more -->
## 展示效果

[Demo](/Native-JS/TextShow/ "BOOS信息展示与收缩")
<iframe width="100%" height="600px" src="/Native-JS/TextShow/"></iframe>

### HTML

```
<div class="container">
    <div class="page">
        <div class="con-text">
            <div class="job-text">
                <div class="job-top color1">
                    <span>职位描述</span>
                    <i class="weui_icon_checked"></i>
                </div>
                <div id="text-mian" class="job-main">
                你好忙
                </div>
                <div id="Btns" class="job-bot color1">显示全部</div>
            </div>
        </div>
        <div class="con-text">
            <div class="job-text">
                <div class="job-top color1">
                    <span>职位描述</span>
                    <i class="weui_icon_checked"></i>
                </div>
                <div id="text-mians" class="job-main">                    
                    1.参与产品的前端开发，与后端工程师协作，高质高效完成产品的数据交互、动态信息展现；<br />
                    2.提升产品的用户体验、前端性能以及团队的开发效率；<br />
                    3.研究和探索创新的开发思路和前沿的前端技术，应用到团队与产品中。<br />

                    1.熟练掌握各种Web前端技术（HTML/CSS/Javascript）和跨浏览器、跨终端的开发；<br />
                    2.深刻理解Web标准，对前端性能、可访问性、可维护性等相关知识有实践的了解和实践经验；<br />
                    3.熟悉HTML5，前沿JS类库和MVC框架者优先；<br />
                    4.熟练使用一门非前端脚本语言（如：NodeJS、Python、PHP等），并有实践项目；<br />
                    5.在博客或GitHub上有技术沉淀者优先； 
                </div>      
                <div id="Btnss" class="job-bot color1">显示全部</div>
            </div>
        </div>
        <div class="Bottom"></div>
    </div>
    <div class="con-bot">
        <div class="Bleft">
            <a href="javascript:;"><i></i><span>+收藏</span></a>
        </div>
        <div class="Bright">
            <a href="javascript:;"><i></i><span>立即沟通</span></a>
        </div>
    </div>
</div>

<div class="sidebar-section">
    <div class="section-detail">
        <p class="text-center shop-detail"><strong>手机扫码访问</strong></p>
        <p class="text-center weixin-title">微信“扫一扫”分享到朋友圈</p>
        <p class="text-center qr-code">
            <img width="140" height="140" src="images/create.png">
        </p>
    </div>
</div>
```

### JavaScript

```
function TextShow(ID,Btns){
    var DivT = document.getElementById(ID);
    var Texts = DivT.innerHTML;
    var NewT = document.createElement("div");
    var Btn = document.getElementById(Btns);

    // 判断页面文字
    if(Texts.length < 200){
        Btn.style.display = "none";
    }else{
        NewT.innerHTML = Texts.substring(0,200) + "……";
        Btn.innerHTML = Texts.length > 200 ? "显示全部" : "";

        Btn.onclick = function(){
            if(Btn.innerHTML == "显示全部"){
                Btn.innerHTML = "收起";
                NewT.innerHTML = Texts;
            }else{
                Btn.innerHTML = "显示全部";
                NewT.innerHTML = Texts.substring(0,200) + "……";
            }
        }
        DivT.innerHTML = "";
        DivT.appendChild(NewT);
    }
}
//文字部分显示：文字、按钮
TextShow("text-mian","Btns");
TextShow("text-mians","Btnss");
```
