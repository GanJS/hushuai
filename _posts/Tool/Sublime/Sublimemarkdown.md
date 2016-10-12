title: Markdown使用指南
date: 2015-12-24 18:29:00
description: 
categories:
- Tool
tags:
- Markdown
toc: false
author: 世平阜康
comments:
original:
permalink: 
---
　　**自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why
<!-- more -->
## Markdown使用指南
### 标题
```
Markdown语法：

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
大标题
=
小标题
-
```

预览效果：

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
大标题
=
小标题
-

### 粗体、斜体
```
Markdown语法：

**粗体**
__粗体__
*斜体*
_斜体_
```
预览效果：

**粗体**
__粗体__
*斜体*
_斜体_

### 分割线
```
Markdown语法：
---
***
~~文字删除线~~
```
预览效果：

---
***
~~文字删除线~~

### 列表
```
Markdown语法：

- 无序列表项目
- 无序列表项目
- 无序列表项目

* 无序列表项目
* 无序列表项目
* 无序列表项目

1. 有序列表项目
2. 有序列表项目
3. 有序列表项目

- 外层列表项目
 + 内层列表项目
 + 内层列表项目
 + 内层列表项目
- 外层列表项目
```

预览效果：

- 无序列表项目
- 无序列表项目
- 无序列表项目

* 无序列表项目
* 无序列表项目
* 无序列表项目

1. 有序列表项目
2. 有序列表项目
3. 有序列表项目

- 外层列表项目
 + 内层列表项目
 + 内层列表项目
 + 内层列表项目
- 外层列表项目

### 添加超链接、图片
```
Markdown语法：

[简书](链接地址 "描述")
![简书slogan](https://raw.githubusercontent.com/luuman/luuman.github.io/master/resoures/luuman-ipad-iphone.jpg "描述")

[简书][1]
![简书slogan][2]

[1]:链接地址 "描述"
[2]:链接地址 "描述"

[无链接的链接][null-link]
[null-link]: chrome://not-a-link

```
效果预览：

[简书](链接地址 "描述")

![简书slogan](https://raw.githubusercontent.com/luuman/luuman.github.io/master/resoures/luuman-ipad-iphone.jpg "描述")

[简书][1]

![简书slogan][2]

[1]:链接地址 "描述"
[2]:https://raw.githubusercontent.com/luuman/luuman.github.io/master/resoures/luuman-ipad-iphone.jpg "描述"
[无链接的链接][null-link]
[null-link]: chrome://not-a-link

### 添加表格
```
Markdown语法：

| ABCD | EFGH | IJKL |
| -----|:----:| ----:|
| a    | b    | c    |
| d    | e    |  f   |
| g    | h    |   i  |

ABCD | EFGH | IGKL
-----|------|----
a    | b    | c
d    | e    | f
g    | h    | i
```
预览效果：

| ABCD | EFGH | IJKL |
| -----|:----:| ----:|
| a    | b    | c    |
| d    | e    |  f   |
| g    | h    |   i  |

ABCD | EFGH | IGKL
-----|------|----
a    | b    | c
d    | e    | f
g    | h    | i

### 添加代码
```
Markdown语法：

`字符`（简短文字添加代码框）

`Tab`或
    四个空格（大段文字添加代码框，每行前添加）
```
预览效果：

`字符`（简短文字添加代码框）

`Tab`或
    四个空格（大段文字添加代码框，每行前添加）

### 引用
```
Markdown语法：

> 引用的文字
> 引用的文字
> 引用的文字

---
> 引用的文字引用的文字引用的文字引用的文字引用的文字引用的文字引
用的文字引用的文字引用的文字引用的文字引用的文字引用的文字引用
的文字引用的文字引用的文字

---
> 引用的文字引用的文字引用的文字引用的文字引用的文字

---
 >> 引言内的引言引言内的引言引言内的引言

---
> 引用的文字引用的文字引用的文字引用的文字引用的文字
```
预览效果：

> 引用的文字
> 引用的文字
> 引用的文字

---
> 引用的文字引用的文字引用的文字引用的文字引用的文字引用的文字引
用的文字引用的文字引用的文字引用的文字引用的文字引用的文字引用
的文字引用的文字引用的文字

---
> 引用的文字引用的文字引用的文字引用的文字引用的文字

---
 >> 引言内的引言引言内的引言引言内的引言

---
> 引用的文字引用的文字引用的文字引用的文字引用的文字

### 单行长文字
```
Markdown语法：

在需要以单行长文字显示的文字两段各加三个`~`,即`~~~`

在需要以单行长文字显示的文字段落前加四个空格
```
预览显示：
```
单行长文字单行长文字单行长文字单行长文字单行长文字单行长文字单行长文字单行长文字单行长文字单行长文字单行长文字单行长文字单行长文字单行长文字
```
### 首行缩进
```
Markdown语法：

 缩进一个字符缩进一个字符缩进一个字符缩进一个字符缩进一个字符缩进一个字符

 缩进两个字符缩进两个字符缩进两个字符缩进两个字符缩进两个字符缩进两个字符

  缩进四个字符缩进四个字符缩进四个字符缩进四个字符缩进四个字符缩进四个字符

预览效果：

 缩进一个字符缩进一个字符缩进一个字符缩进一个字符缩进一个字符缩进一个字符

 缩进两个字符缩进两个字符缩进两个字符缩进两个字符缩进两个字符缩进两个字符

  缩进四个字符缩进四个字符缩进四个字符缩进四个字符缩进四个字符缩进四个字符
```
### 添加脚注
```
Markdown语法：

![添加脚注](http://upload-images.jianshu.io/upload_images/1064727-49caf145bf6c2a97.png)添加脚注
```
预览效果：

A [[1]](http://www.jianshu.com/p/21d355525bdf#fn_lemma_a "描述")

### 创建链接
```
为输入的URL或邮箱自动创建链接，如test@domain.com。
Markdown语法：

<test@domain.com>
```
预览效果：

<test@domain.com>

### 转义字符
```
在特殊字符，如*、[、>等前面加\可使特殊格式字符转换为正常字符打出（有序列表符号如1.，须在. 前加\）。

Markdown语法：

\\
\`
\*
\_
\{\}
\[\]
\(\)
\#
\+
\-
\.
\!
```
预览效果：

\\
\`
\*
\_
\{\}
\[\]
\(\)
\#
\+
\-
\.
\!
### 小型文本
```
Markdown语法：

<small>文本内容</small>
```
预览效果：

<small>文本内容</small>



## 参考资料：
在线编辑
[gitbook](https://www.gitbook.com/)

新手指南
[Markdown入门学习小结](http://www.jianshu.com/p/21d355525bdf)
[Markdown 简明教程](http://www.jianshu.com/p/7bd23251da0a#)
[Markdown語法說明（繁體中文版）](http://markdown.tw/)
[Markdown 语法说明（简体中文版）](http://wowubuntu.com/markdown/)
[维基百科](http://zh.wikipedia.org/wiki/Wikipedia:%E9%A6%96%E9%A1%B5)：[Markdown词条](http://zh.wikipedia.org/wiki/Markdown)

[hexo你的博客](http://ibruce.info/2013/11/22/hexo-your-blog/)
[如何搭建一个独立博客——简明Github Pages与Hexo教程](http://www.jianshu.com/p/05289a4bc8b2#)

[简书](http://www.jianshu.com/users/yZq3ZV/latest_articles)：[献给写作者的 Markdown 新手指南](http://www.jianshu.com/p/q81RER)
[Lawrence Li](https://twitter.com/liruyi)：[为什么作家应该用 Markdown 保存自己的文稿](http://www.jianshu.com/p/qqGjLN)
[阳志平](http://weibo.com/ouyangzhiping)：[「Markdown写作浅谈」](http://www.jianshu.com/p/PpDNMG)
[Casa Nova](http://www.douban.com/people/casa_nova/)：[為什麼文科生也該用markdown寫作?](http://www.douban.com/note/221187015/)
[Gnat](http://www.jianshu.com/users/faa44ac9e895/latest_articles)：[Markdown 简明教程](http://www.jianshu.com/p/7bd23251da0a)
[Gnat](http://www.jianshu.com/users/faa44ac9e895/latest_articles)：[Markdown 写作规范参考](http://www.jianshu.com/p/3bd994e702a7)
[Te_Lee](http://www.jianshu.com/users/ea86ff9520da/latest_articles)：[Markdown——入门指南](http://www.jianshu.com/p/1e402922ee32)
[怀瑾握瑜](http://www.jianshu.com/users/a3365067ff28/latest_articles)：[Markdown语法纪要](http://www.jianshu.com/p/0752bd0418df)
[唐衣可俊](http://www.jianshu.com/users/7e669eb8f84f/latest_articles)：[MarkDown使用小技巧](http://www.jianshu.com/p/9d94660a96f1)
[温谦](http://www.ituring.com.cn/users/81963)：[怎样使用Markdown](http://www.ituring.com.cn/article/23)
[Leo Chin ](http://home.cnblogs.com/u/hnrainll/)：[Markdown 11种基本语法](http://www.cnblogs.com/hnrainll/p/3514637.html)
[Equation 85](http://equation85.github.io/)：[Markdown语法示例](http://equation85.github.io/blog/markdown-examples/)


Markdown 免费编辑器

在线编辑器
[MaHua](http://mahua.jser.me/ "小众软件推荐，界面有些简陋")
[Dillinger.io](http://dillinger.io/ "漂亮强大，支持md, html, pdf 文件导出。支持dropbox, onedrive，google drive, github. 来自国外，可能不够稳定。")
[Markable.in](http://markable.in/ "一个显著的markdown编辑器")
[marxi](http://marxi.co/ "马克飞象")

浏览器插件
[MaDe](https://chrome.google.com/webstore/detail/oknndfeeopgpibecfjljjfanledpbkog "Chrome")

Windows 平台
[GitHub Atom](https://atom.io/)
[MarkdownPad](http://markdownpad.com/)
[MarkPad](http://code52.org/DownmarkerWPF/)

Linux 平台
[ReText](http://sourceforge.net/p/retext/home/ReText/)

Mac 平台
[Mou](http://mouapp.com/)

高级应用(Sublime Text 2 + MarkdownEditing 教程)
[Sublime Text 2](http://www.sublimetext.com/2)
[MarkdownEditing](http://ttscoff.github.com/MarkdownEditing/)
[教程](http://lucifr.com/2012/07/12/markdownediting-for-sublime-text-2/)