title:  原生JS TitleTip
date: 2016-01-19 13:58:41
description: 
categories:
- HTML
tags:
- JavaScript
toc:
author:
comments:
original:
permalink: 
---
　　** 自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why
<!-- more -->
## 原生JS TitleTip

为了实现对特定的A标签Title的美化，使其可以按照我们想要的样式显示。

方案一：

[Demo](/Native-JS/TitleTip)
<iframe width="100%" src="/Native-JS/TitleTip"></iframe>
```
<a href="#" class="TitleTip" title="BI Scp" >A标签TitleTip</a>
```

```
<script type="text/javascript">
	var Common = {
		getItself: function(id) {
			return "string" == typeof id ? document.getElementById(id) : id;
		},
		getTextSize: function(text) {
			var span = document.createElement("span");
			var result = {};
			result.width = span.offsetWidth;
			result.height = span.offsetWidth;
			span.style.visibility = "hidden";
			document.body.appendChild(span);
			if (typeof span.textContent != "undefined") span.textContent = text;
			else span.innerText = text;
			result.width = span.offsetWidth - result.width;
			result.height = span.offsetHeight - result.height;
			span.parentNode.removeChild(span);
			return result;
		}
	}
	var TitleTip = {
		showTitleTip: function(param, linkObj, e) {
			var div;
			if (document.getElementById("TitleTipDiv")) {
				document.body.removeChild(document.getElementById("TitleTipDiv"));
			}
			div = document.createElement("div");
			div.id = "TitleTipDiv";
			// div.style.cssText = "text-align: center; color: #fff; background: rgba(0,0,0,.8); position: absolute; z-index: 100; padding: 5px 15px; font-size: 12px; line-height: 20px; transform: translate(-50%); border-radius: 6px;";
			div.innerHTML = linkObj.tip;
			document.body.appendChild(div);

			if (param && param.width) { //如未设置，默认一行显示
				if (Common.getTextSize(div.innerHTML).width < param.width) {
					div.style.maxWidth = param.width + "px";
				} else {
					div.style.width = param.width + "px";
				}
			}

			//must before set opr to get offsetHeight...
			div.style.display = ""; 

			///set TitleTip position
			// console.log("a W"+linkObj.offsetWidth);
			// console.log("a H"+linkObj.offsetHeight);
			// console.log("a X"+linkObj.offsetTop);
			// console.log("a Y"+linkObj.offsetLeft);
			// console.log("Tip W"+div.offsetWidth);
			// console.log("Tip H"+div.offsetHeight);

			div.style.top = linkObj.offsetTop + linkObj.offsetHeight + 8 + "px";
			div.style.left = linkObj.offsetLeft + linkObj.offsetWidth/2 + "px";

			///hide TitleTip after some time
			if (param && param.time) {
				setTimeout(this.hidTitleTip, param.time);
			}
		},
		hidTitleTip: function() {
			if (document.getElementById("TitleTipDiv")) {
				document.getElementById("TitleTipDiv").style.display = "none";
			}
		},
		addTips: function(param) {
			var linkArr = document.getElementsByTagName("a");
			if (!linkArr) {
				return false;
			}
			for (i = 0; i < linkArr.length; i++) {
				if (linkArr[i].className == "TitleTip") {
					linkArr[i].tip = linkArr[i].title;
					var tipObj = this;
					linkArr[i].onmouseover = function(e) {
						tipObj.showTitleTip(param, this, e);
					}
					linkArr[i].onmouseout = tipObj.hidTitleTip;
					if (param && param.moveable == true) { //默认不滚动
						linkArr[i].onmousemove = function(e) {
							tipObj.showTitleTip(param, this, e);
						}
					}
					linkArr[i].title = "";
				}
			}
		}
	}
	window.onload = function() {
		TitleTip.addTips({
			width: 200
		}); 
		// time:5000, moveable: true 
	}
</script>
```


[]()