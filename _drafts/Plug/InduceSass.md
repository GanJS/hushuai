title: sass语法
date: 2015-12-25 18:29:00
description: 
categories:
- sass
tags:
- sass
toc: true
author:
comments:
original:
permalink: 
---
　　**移动适配：**
<!-- more -->

sass语法


### 文件后缀名

```
//一种后缀名为sass，不使用大括号和分号；
body
	background: #eee
	font-size:12px
p
	background: #0982c1

//scss文件这种和我们平时写的css文件格式差不多，使用大括号和分号
body {
	background: #eee;
	font-size:12px;
}
p{
	background: #0982c1;
} 
```

#### 设置rem，控制width
@function size($size) {
  $width: 375;
  $scale: 10;
  @return ($size / $width * $scale) * 1rem;
}