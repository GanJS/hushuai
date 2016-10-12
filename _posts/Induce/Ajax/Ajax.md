title: Ajax学习计划
date: 2016-01-27 14:11:20
description: 
categories:
- Ajax
tags:
- Ajax
toc: true
author:
comments:
original:
permalink: 
---

　　**AJAX：**Asynchronous Javascript And XML（异步JavaScript和XML）。是指一种创建交互式网页应用的网页开发技术。 AJAX = 异步 JavaScript和XML（标准通用标记语言的子集）。 AJAX 是一种用于创建快速动态网页的技术。 通过在后台与服务器进行少量数据交换，AJAX 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。 传统的网页（不使用 AJAX）如果需要更新内容，必须重载整个网页页面。

<!-- more -->

## Ajax介绍

### 特点：

```
什么是服务器：
搭建简单的本地服务器软件Wamp、XAMPP，提供简单的用户服务，读取数据。
```

### 使用Ajax

```
基础：请求并显示静态TXT、json文件
字符集编码：UTF-8、GB2312，使用相同的编码。
缓存：chrome下的缓存还不是很严重，IE下的缓存比较严重，除非关闭浏览器。

缓存的工作原理：通过URL进行缓存的。通常可以使用URL?t= + new Date().getTime()
```

```
window.onload = function (){
	var oBtn = document.getElementById('Btn1');

	oBtn.onclick = function (){
		ajax('aa.txt?t=' + new Date().getTime(),
			function(str){
				alert(str);
			},function(){
				alert('失败');
			});
	}
}
```

#### 通过Ajax读取的都是字符串

```
通过eval()将文件内容解析成JS可以识别的内容
window.onload = function (){
	var oBtn = document.getElementById('Btn1');

	oBtn.onclick = function (){
		ajax('aa.txt?t=' + new Date().getTime(),
			function(str){
				var SA = eval(str);
				alert(SA[1]);
			},function(){
				alert('失败');
			});
	}
}
```

#### 读取Json文件

```
window.onload = function (){
	var oBtn = document.getElementById('Btn1');
	var oUls = document.getElementById('ul1');

	oBtn.onclick = function (){
		ajax('aa.txt?t=' + new Date().getTime(),
			function(str){
				var SA = eval(str);

				for(var i=0;i<SA.length;i++){
					var oLi = document.createElement('li');
					oLi.innnerHTML='用户名：<strong>' + SA[i].name +'</strong>密码：<span>' + SA[i].pass + '</span>';
					//添加到Ul里
					oUl.appenChild(oLi);
				}
				alert(SA[1]);
			},function(){
				alert('失败');
			});
	}
}
```

```
HTTP请求的方法
GET：用于获取数据（如：浏览贴子）
POST：用于上传数据（如：用户注册）
区别：
get是在URL里传送数据：安全性低、容量有限（2000字符），有缓存，适合请求信息
post是通过HTTP请求，安全性好一点，无缓存，适合传递信息
安全的方式使用HTTPS。
GET方式：
?name=word&password=password
```

## Ajax进阶


### 创建Ajax

```
IE6
var oAjax = new ActiveXObject("Microsoft.XMLHTTP");

var oAjax = new XMLHttpRequest();
```

```
注意：

//使用没有定义的变量——报错
alert(a);

//使用没有定义的属性——undefined
alert(window.a);
```

```
function (){
	if(window.XMLHttpRequest){
		var oAjax = new XMLHttpRequest();
	}else{
		var oAjax = new ActiveXObject("Microsoft.XMLHTTP");
	}
}
```

### 连接服务器

```
open（方法，连接的文件名，同步/async异步true）ajxa其实都是异步的
open(method,url,async);
oAjax.opan('GET','a.text?=t'+new Date().getTime(),true);



同步和异步的区别?


同步：（一次加载）浏览器访问服务器请求，用户看得到页面刷新，重新发请求,等请求完，页面刷新，新内容出现，用户看到新内容,j进行下一步操作。

异步：（同时加载）浏览器访问服务器请求，用户正常操作，浏览器后端进行请求。等请求完，页面不刷新，新内容也会出现，用户看到新内容。

（待完善）
```


### 发送请求

```
oAjax.send();
send(string);
```

### 接收返回

```
oAjax.onreadystatechange = function(){
	//浏览器和服务器，进行到哪一步了
	if(oAjax.readyState==4){
		if(oAjax.status==200){
			alert('成功：'+oAjax.status);
		}else{
			alert('失败：'+oAjax.status);
		}
	}
}
```

```
0 （未初始化）
1 （载入）
2 （载入完成）send()方法完成，已接收全部信息
3 （解析）正在解析响应
4 （完成）完成但不代表成功
```

```
Ajax Status请求状态

200 成功
301
304
404
```


```
IE6
var oAjax = new ActiveXObject("Microsoft.XMLHTTP");

var oAjax = new XMLHttpRequest();
```

```
封装函数

function ajax(url,fnSucc,fnFaild){
	if(window.XMLHttpRequest){
		var oAjax = new XMLHttpRequest();
	}else{
		var oAjax = new ActiveXObject("Microsoft.XMLHTTP");
	}

	oAjax.opan('GET','url?=t'+new Date().getTime(),true);

	oAjax.send();

	oAjax.onreadystatechange = function(){
		if(oAjax.readyState==4){
			if(oAjax.status==200){
				fnSucc(oAjax.responseText);
			}else{
				if(fnFaild){
					fnFaild(oAjax.status);
				}
			}
		}
	}
}

ajax('a.txt',function(str){
	alert(str);
})
```


```
封装函数

function ajax(url,data,fnSucc,fnFaild){
	if(window.XMLHttpRequest){
		var oAjax = new XMLHttpRequest();
	}else{
		var oAjax = new ActiveXObject("Microsoft.XMLHTTP");
	}

	oAjax.opan('POST','url',true);

	oAjax.setRequestHeader("Content-type","application/x-www-form-urlencoded");

	oAjax.send(data);

	oAjax.onreadystatechange = function(){
		if(oAjax.readyState==4){
			if(oAjax.status==200){
				fnSucc(oAjax.responseText);
			}else{
				if(fnFaild){
					fnFaild(oAjax.status);
				}
			}
		}
	}
}

ajax('a.txt','name=' + document.getElementById("staffName").value + '&number=' + document.getElementById("staffNumber").value + '&sex=' + document.getElementById("staffSex").value + '&job=' + document.getElementById("staffJob").value,function(str){
	alert(str);
})
```

## Ajax数据

```
XML、Json：同等数据量，XML更大
```