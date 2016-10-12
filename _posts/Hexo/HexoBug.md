title: Hexo bug
date: 2015-12-27 18:29:00
description: 
categories:
- Hexo
tags:
- Hexo
toc: true
author:
comments:
original:
permalink: 
---
　　** 自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why
　　最近，使用Hexo遇到了很多问题，在设立进行整理。
<!-- more -->
[]()
[首页文章摘要](https://github.com/MOxFIVE/hexo-theme-yelee/commit/2083b8a63e43c8d682e86ce788790ba93f96fc05)
[]()
[hexo生成JSON内容](https://github.com/alexbruno/hexo-generator-json-content)
[hexo-generator-search](https://github.com/PaicHyperionDev/hexo-generator-search)

### Wiki

聚沙成塔，记录碎片化信息，构筑个人知识体系

### 圆圈导航JS出现问题

有时候不出现

### 多说表情溢出
移动端，多说表情溢出，将页面撑开。

### 标签显示数量
移动端，标签显示数目有限，PC端也有这样的问题。

### Instagram图片显示
移动端图片显示效果有待修改，应该不可以滑动，全屏填充。

### 1-3 想办法添加作品介绍页面

界面不够完美，有待于修改！

> - [[W]][10] 

[12]: ht "hexo"


### IE 低版本浏览器不支持

    <!--[if lt IE 10]>
    <script>window.location.href="http://luuman.github.io/Works/PC/IE/";</script>
    <![endif]-->

    <!-- Google Analytics -->
    <script>
        (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
                (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
            m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
        })(window,document,'script','js/eed8ec65a6dd9b05eed6d4a02e1439e4.js','ga');
 
        ga('create', 'UA-65952334-1', 'auto');
        ga('send', 'pageview');
    </script>

### 2016 年 01 月

### 1-28 TitleTip描述信息显示
> - [[W]][9] 对A标签的title属性进行设置，将文本内容去除，使用div进行集中显示。
> - [[W]][10] J:\Hexo\Hexo\themes\spfk\source\css\_partial\tagcloud.styl

[12]: https://github.com/luuman/Hexo/blob/master/themes/spfk/source/css/_partial/tagcloud.styl#L365 "tagcloud.styl"
[13]: http://luuman.github.io/Native-JS/TitleTip/ "TitleTip原生JS Demo"

### 1-7 首页添加loading效果
> - [[W]][9] loading效果
> - [[W]][10] Hexo\themes\landscape\source\css\_partial\highlight.styl

[12]: ht "hexo"
[12]: ht "hexo"

### 1-5 语法高亮样式修改
> - [[W]][9] code highlight 代码高亮
> - [[W]][10] Hexo\themes\landscape\source\css\_partial\highlight.styl

[12]: ht "hexo"
[12]: ht "hexo"

### 1-3 想办法添加作品介绍页面
根据[Hexo][ ]官网的主题介绍，添加标签、名称、图片、介绍放置自己的作品。
最终还是把这个页面弄出来了，但是还有很多地方需要修改，因为是响应式的页面，还有很多地方要优化。还有window.serch.index没有解决。

> - [[W]][9] 为Hexo博客添加作品介绍页面
> - [[W]][10] 为Hexo site[[W]][11][[W]][12]添加目录

[12]: https://github.com/hexojs/site/blob/master/themes/navy/layout/partial/theme.swig "hexo site"
[11]: https://github.com/hexojs/site/blob/master/themes/navy/layout/partial/plugin.swig "hexo site"
[10]: https://github.com/hexojs/site/blob/master/themes/navy/layout/plugins.swig "hexo site"
[9]: http://luuman.github.io/2015/12/27/Hexo-plug/#u63D2_u5165_u81EA_u5B9A_u4E49_u9875_u9762 "hexo plug"

### 1-2 添加目录

> - [W][Hexo博客系统][7] Hexo博客系统的核心支持生成目录（Table of Contents），但其默认的主题Landscape并不支持目录的显示。
> - [[W]][7]  为Hexo博客添加目录
> - [[W]][8] 为Hexo博客添加目录

[8]: /2015/12/27/Hexo-plug/#u4E3AHexo_u535A_u5BA2_u6DFB_u52A0_u76EE_u5F55 "为Hexo博客添加目录 left-col.ejs"
[7]: http://kuangqi.me/tricks/enable-table-of-contents-on-hexo/ "为Hexo博客添加目录 left-col.ejs"

### 2015 年 12 月

### 12-31 社交账号图标修改
去除图片，将图标更换成字体文件，通过查看，得知系统通过自己设定的社交账号链接，进行自动生成\themes\spfk\layout\_partial\left-col.ejs

> - [[W]][6] 社交账号图标修改
结果发现还有很多图标，fontawesome-webfont没有，了解图标的逻辑。

[6]: /2015/12/27/Hexo-plug/#u5B89_u88C5_u5206_u4EAB_u6309_u94AE "社交账号图标修改 left-col.ejs"

### 12-31 百度分享图片修改
由于博客已经建站，字体包，将class的名称就改了，改变分享效果

> - [[W]][5] 百度分享美化

[5]: /2015/12/27/Hexo-plug/#u5B89_u88C5_u5206_u4EAB_u6309_u94AE "百度分享美化 article.ejs"

### 12-30 添加版权声明
参照M的版权声明，进行修改！
> - [[W]][4] 添加版权声明，修改样式

[4]: /2015/12/27/Hexo-plug/#u6DFB_u52A0_u7248_u6743_u58F0_u660E "添加版权声明 nav.ejs"

### 12-29 侧边栏
侧边栏图片背景的设置，要和？再次看了感觉还好，就不改了。

### 12-28 instagram图片拉取
添加instagram图片，展示自己的摄影爱好。
> - [[W]][0] instagram总结
> - [[W]][1] instagram图片拉取小经验
> - [[W]][2] 管理客户端页面
> - [[W]][3] Lookup Your Instagram User ID

[3]: http://jelled.com/instagram/lookup-user-id "Lookup Your Instagram User ID"
[2]: http://instagram.com/developer/clients/manage/ "管理客户端页面"
[1]: http://litten.github.io/2014/03/03/instagram-api-ex/ "instagram图片拉取小经验"
[0]: /2015/12/27/Hexo-plug/#u540C_u6B65instagram_u56FE_u7247 "instagram: 教程总结"


### 12-27 多说样式修改
多说样式，被顶起的页面显示效果，还是不太好。
具体样式请参照：[多说.css](https://github.com/luuman/Hexo/blob/master/themes/spfk/source/css/%E5%A4%9A%E8%AF%B4.css)