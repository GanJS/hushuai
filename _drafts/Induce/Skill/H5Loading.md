title: H5性能优化
date: 2015-12-25 18:29:00
description: 
categories:
- Report
tags:
- Report
toc: true
author:
comments:
original:
permalink: 
---

　　**自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why
<!-- more -->

做H5移动端活动页面，想必大家都会遇到图片还没有加载出来的情况。通常原因都有很多，但主要原因还是图片太多、太大。
优化思路：
1. 合并HTTP请求
2. 缓存管理
3. 图片压缩
1. 对页面部分图片做预加载处理
1. Loading首屏显示加载效果，等待加载完毕。

实现思路：
1. 进度问题
由于页面加载过程时间不较长，而用户不能通过页面loading效果看出加载的进度怎样，所以要在页面中显示现在，页面中的进度如何。
实现方式：
	1. 比较总文件大小与加载文件的大小（没有原生的方法？）
	2. 比较总文件数目与加载文件的数目
1. 加载失败
如果文件中有文件因为网络原因加载失败，或者是图片没有加载出来。不因引响加载器的功能。

1. 加载超时问题
图片不能加载太久，否则用户一直停留在加载效果上看不到主内容，用户的等待时间不可控制地延长，导致用户体验下降，这样就有悖加载器的初衷了。所以应该给每个图片设置一个加载的超时时间，如果在所有图片的超时时间之后，还没加载完，就应该主动放弃加载，通知外部上下文加载完毕，显示主内容。

[]()

[利用简洁的图片预加载组件提升h5移动页面的用户体验](http://www.cnblogs.com/lyzg/p/5264028.html)



Cookie

同一个网站，只有一套Cookie
适浏览器而定：
Cookie的大小4kb-10kb，大小十分有限
网站不会超过50条
不用的Cookie要删除，条数有限

过期时间
用Firefox进行测试，Chrome、IE都会把本地Cookie干掉。

JS
//属性
document.cookie

编辑

//添加Cookie
document.cookie='user=bus';
document.cookie='pass=sbus';//不是赋值

过期时间
//
var oDate = new Date();
oDate.setDate(oDate.getDate()+14);

//传入名称、值、时间
function setCookie(name,value,iDay){
	var oDate = new Date();
	oDate.setDate(oDate.getDate()+iDay);//过期时间多少天

	document.cookie = name + '=' + value + ';expires=' + oDate;
}
setCookie('userName','Luumans',12);

//获取Cookie值
function getCookie(name){
	//字符串分割
	var aType = document.cookie.split('; ');
	
	for(var i=0;i<aType.length;i++){
		//字符串分割
		var aName = aType[i].split('=');
		//判断名称
		if(aName[0]==name){
			return aName[1];
		}
	}
	return '';//Null
}
alert(getCookie('name'));

//删除Cookie

function removeCookie(name){
	setCookie(name,1,-1);
}
removeCookie('name');



//实例登录

<form action="http://www.baidu.com">
	<input type="text" name="user" /><br />
	<input type="password" name="pass" /><br />
	<input type="submit" value="登录" />
</form>

<script type="text/javascript">
	window.onload = function(){
		var uForm = document.getElementById('from1');
		var oUser = document.getElementById('user')[0];

		uForm.onsubmit = function(){
			setCookie('user',oUser.value,14);
		};
		oUser.value = getCookie('user')
	}
	function setCookie(name,value,iDay){
		var oDate = new Date();
		oDate.setDate(oDate.getDate()+iDay);//过期时间多少天

		document.cookie = name + '=' + value + ';expires=' + oDate;
	}
</script>


淘宝、百度的Cookie病毒式使用：ACookie、

H5：存储localstrang

获取两个标签的共同的父标签
function getTag(A,B){
	var AID = document.getElementById('A').
}

计算字符串中出现最多的字符的个数
function getString(){
}