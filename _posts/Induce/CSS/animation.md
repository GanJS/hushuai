title: CSS3动画探秘
date: 2016-02-20 18:29:00
description: 
categories:
- HTML
tags:
- CSS3
toc: true
author:
comments:
original:
permalink: 
---
　　**CSS3动画探秘：**Canvas 实现也是可以的，这里不做介绍，本次主题是 css3 动画
<!-- more -->
## CSS3实现

[Demo](/CSS3/Animation/Gifs/ "GIF动画")
来自 [dribbble](https://dribbble.com/ "为设计师展示和讲述") 某位大师的作品
<iframe width="100%" height="600px" src="/CSS3/Animation/Gifs/"></iframe>


### 方式一：切换图片

```
@-webkit-keyframes GIF{
    0% {background-image: url(GIF_1.png);}
    14.3% {background-image: url(GIF_2.png);}
    28.6% {background-image: url(GIF_3.png);}
    42.9% {background-image: url(GIF_4.png);}
    57.2% {background-image: url(GIF_5.png);}
    71.5% {background-image: url(GIF_6.png);}
    85.8% {background-image: url(GIF_7.png);}
    100% {background-image: url(GIF_1.png);}
}
```
### 方式二：切换背景图片位置

```
@-webkit-keyframes GIF{
    0% {background-position: 0 0;}
    14.3% {background-position: -180px 0;}
    28.6% {background-position: -360px 0;}
    42.9% {background-position: -540px 0;}
    57.2% {background-position: -720px 0;}
    71.5% {background-position: -900px 0;}
    85.8% {background-position: -1080px 0;}
    100% {background-position: 0 0;}
}
```

### 方法分析：
方式一：实现起来会比较简单，但带来额外的请求数，图片体积较大
方式二：需要设计雪碧图，并量取背景位置，请求数少，压缩图片体积


[CSS3动画帧数计算器](http://tid.tenpay.com/labs/css3_keyframes_calculator.html "请在Chrome中打开")

```
案例分析：单向循环

利用这个step阶梯函数我们可以做出像一开始我们做出的逐帧动画的效果 


雪碧图内图标个数：23==帧数
则动作个数：24
由于是人物动作，所以要没有停顿效果

动作个数：24
动作过渡帧数：4.3
animation: anim-name 1s linear infinite;
    
动画标准是一秒24帧

@-webkit-keyframes anim-name{
    0%{  /* 动作1 */  }
    4.3%{  /* 动作2 */  }
    8.6%{  /* 动作3 */  }
    12.9%{  /* 动作4 */  }
    17.2%{  /* 动作5 */  }
    21.5%{  /* 动作6 */  }
    25.8%{  /* 动作7 */  }
    30.1%{  /* 动作8 */  }
    34.4%{  /* 动作9 */  }
    38.7%{  /* 动作10 */  }
    43%{  /* 动作11 */  }
    47.3%{  /* 动作12 */  }
    51.6%{  /* 动作13 */  }
    55.9%{  /* 动作14 */  }
    60.2%{  /* 动作15 */  }
    64.5%{  /* 动作16 */  }
    68.8%{  /* 动作17 */  }
    73.1%{  /* 动作18 */  }
    77.4%{  /* 动作19 */  }
    81.7%{  /* 动作20 */  }
    86%{  /* 动作21 */  }
    90.3%{  /* 动作22 */  }
    94.6%{  /* 动作23 */  }
    100%{  /* 动作24 */  }
}

.GIF{
    width: 800px;
    height: 600px;
    margin: auto;
    background: url(../img/charector.png) 0 0 no-repeat;
    animation: GIF 1s step-start infinite;
    -webkit-animation: GIF 1s step-start infinite;
}
```
![循环方式](http://image.uisdc.com/wp-content/uploads/2014/06/9.jpg)


```
用CSS代码的方式表示，就是：

单向循环： animation-iteration-count: infinite; animation-direction: normal;

双向循环： animation-iteration-count: infinite; animation-direction: alternate;
```

## 雪碧图合成

[HTML5在线雪碧图片合成工具](http://www.alloyteam.com/2012/05/gopng-sprite-figure-synthesis-tool-another-html5-app/ "GoPng By Alloy")

[使用Compass生成雪碧图](http://www.w3cplus.com/preprocessor/compass-image-sprite.html "")
[SmartSprites 智能批量合并 CSS 雪碧图](http://www.cnblogs.com/twoer/p/3413170.html "")
[ispriter](https://github.com/iazrael/ispriter "")
[csssprites](http://csssprites.org/ "")

[animation](http://www.uisdc.com/css3-animation-calculate "")


## 动画

[H5动效的常见制作手法](http://isux.tencent.com/h5active.html?variant=zh-hans "")
[css3-animation](https://www.qianduan.net/css3-animation/ "css3-animation来制作逐帧动画")
[多屏CSS动画精进技巧](http://www.iguoguo.net/2015/52669.html)


