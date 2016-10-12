title:  原生JavaScript探索
date: 2016-01-15 13:58:41
description: 
categories:
- HTML
tags:
- JavaScript
toc: true
author:
comments:
original:
permalink: 
---
　　** 自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why
<!-- more -->

<iframe width="100%" height="100%" src="http://luuman.github.io/Native-JS/"></iframe>

## Title炫舞

为了实现Title的动态变化，使用document.title修改Title的内容。


方案一：
[Demo](/Native-JS/Title)
```
<!-- 用户浏览其他页面 -->
<script type="text/javascript">
	// window 失去焦点，停止输出
	var Title = document.title
	window.onblur=function(){
	   document.title="对面的女孩看过来";
	}
	// window 每次获得焦点
	window.onfocus = function() {
	    document.title=Title;
	}
</script>
```

[变态的标题](https://www.bh-lay.com/blog/14e6e855585)

方案二：

```
<script type="text/javascript">
	document.addEventListener('visibilitychange', function() {
	  document.title = document.hidden ? '出BUG了，快看！':'小剧客栈，剧中人的个人博客！'
	});
</script>

```

方案三：

```
<script type="text/javascript">
	document.addEventListener("keydown", function(a) {
		a = a || window.event;
		var b = parseInt(a.keyCode);
		!a.ctrlKey || 115 !== b && 83 !== b ? (123 === b || a.ctrlKey && a.shiftKey && 73 === b || a.ctrlKey && 85 === b) && (a.returnValue = !1, a.preventDefault(), p()) : (a.returnValue = !1, a.preventDefault(), p())
	}), document.addEventListener("contextmenu", function(a) {
		a = a || window.event, a.returnValue = !1, a.preventDefault()
	}, !1), document.addEventListener("visibilitychange", function() {
		document.title = document.hidden ? "看这里，看这里!" : "世平阜康的博客"
	})
</script>

```

```
<script type="text/javascript">
	var r = "记得回来点单哦！ - 饿了么",
	    n = document.title;
	angular.$(document).on("visibilitychange",function(){
	    document.title = "hidden"===document.visibilityState ? r : n
	})
</script>
```

## 禁用右键
[Demo](/Native-JS/Prevent-Right-click)

```
<script type="text/javascript">
	// 禁用右键
    document.oncontextmenu = function (){
        return (false);
    }
</script>
```
## 禁用F12

> 禁用F12

```
<script type="text/javascript">
	// 禁用F12
	document.onkeydown = document.onkeyup = document.onkeypress = function() {
		if (window.event.keyCode == 123) {
			window.event.returnValue = false;
			return (false);
		}
	}
</script>
```

>使用F12，弹出提示，关闭网页

[Demo](/Native-JS/Disable-F12)

```
<script type="text/javascript">
	// 禁用F12
	document.onkeydown = document.onkeyup = document.onkeypress = function() {
		if (window.event.keyCode == 123) {
			document.getElementById("Popup").innerHTML="<div><a href=#>这个真的没什么好看的，还是看内容吧！</a></div>";
			// 关闭窗口
			setTimeout(b, 2000);
			function b() {
				window.close();
			}
			window.event.returnValue = false;
			return (false);
		}
	}
</script>
```

## 自定义复制内容


修改用户复制文档的内容，添加版权申明等信息。


## 计时器


> Js 时间间隔计算(间隔天数)

```
function GetDateDiff(startDate,endDate)  
{  
    var startTime = new Date(Date.parse(startDate.replace(/-/g,   "/"))).getTime();     
    var endTime = new Date(Date.parse(endDate.replace(/-/g,   "/"))).getTime();     
    var dates = Math.abs((startTime - endTime))/(1000*60*60*24);     
    return  dates;    
}
```
>  计算网站运行的具体时间

错误理解：没有计算12月份的，好吧，是我理解错误，就好像周期一样，没有7,0就是星期天。

```
理解下时间的规则：

document.write(new Date + "<br />");
Fri Jan 15 2016 14:42:36 GMT+0800 (中国标准时间)

document.write(new Date(2016, 0, 12, 10, 0, 0) + "<br />");
Tue Jan 12 2016 10:00:00 GMT+0800 (中国标准时间)

设置几月的时候要减1，0代表一月。


document.write(Math.floor(((new Date).getTime() - new Date(2015, 10, 25, 10, 0, 0).getTime()) / 864e5) + "<br />")
51

年数
c = b % 31104e6,
月数
d = c % 2592e6,
天数
e = d % 864e5,
时间
f = e % 36e5;
```

[Demo](/Resume/H1/)

```
function b() {
	var b = (new Date).getTime() - new Date(2015, 10, 25, 10, 0, 0).getTime(),
		c = b % 31104e6,
		d = c % 2592e6,
		e = d % 864e5,
		f = e % 36e5;
	i = [Math.floor(b / 31104e6), Math.floor(c / 2592e6), Math.floor(d / 864e5), Math.floor(e / 36e5), Math.floor(f / 6e4), Math.floor(f % 6e4 / 1e3)], h.each(function(b, c) {
		a(c).css({
			backgroundPosition: "0 " + (-44 * i[b] + "px")
		})
	})
}
```

## 调用微博

```
function() {
        // 调用微博
        var oDiv = document.createElement("div");
        oDiv.style.width = "384px";
        oDiv.style.textAlign = "right";
        oDiv.style.margin = "5px auto 10px";
        oDiv.innerHTML = "<iframe width=\"117\" height=\"24\" frameborder=\"0\" allowtransparency=\"true\" marginwidth=\"0\" marginheight=\"0\" scrolling=\"no\" border=\"0\" src=\"http://widget.weibo.com/relationship/followbutton.php?language=zh_cn&width=136&height=24&uid=1844880617&style=2&btn=red&dpc=1\"></iframe>";
        document.body.appendChild(oDiv)
    }
```

## JS数据归类提取



[]()