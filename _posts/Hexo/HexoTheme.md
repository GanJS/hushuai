title:  Hexo 主题：SPFK
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
　　** Hexo 主题：**用了yilia主题一段时间，感觉还有很多可以提高的地方，就查阅资料，对其进行粗类的修改，
但是，有其实还有很多不完善的地方，欢迎大家前捧场。没想到，这么多人喜欢黑色版本的，建议不是每个人都喜欢我的这些功能，所以准备个基础版本，插件可以看教程自行安装。

<!-- more -->
## 使用

### 安装 

```
$ git clone https://github.com/luuman/hexo-theme-spfk.git themes/spfk
```

### 配置

修改hexo根目录下的 `_config.yml` ： `theme: spfk`

### 更新

```
cd themes/spfk
git pull
```

## 配置

关于配置文件，

主题配置文件在主目录下的`_config.yml`：[_config.yml](http://luuman.github.io/2015/12/21/GitHub+Hexo/ "主题配置文件")

相关插件的安装：请参照[Hexo插件安装](http://localhost:4000/2015/12/27/Hexo-plug/ "请参照安装")
```
### Header
J:\Hexo\Hexo\themes\spfk\_config.yml
menu:
  主页: /
  所有文章: /archives
  # 随笔: /tags/随笔

    #是否开启多说评论，填写你在多说申请的项目名称 duoshuo: duoshuo-key（http://duoshuo-key.duoshuo.com/）
    #若使用disqus，请在博客config文件中填写disqus_shortname，并关闭多说评论
    duoshuo: true

网页侧边栏背景:

# Background | 背景
## "background_sum": show images form /source/background/的图片数目background_sum: 24
## "on: true": 自动随机显示这5张图片
## "on: false": 自定义显示图片设置，background_image: 109
background:
  on: true
  #on: false
  background_sum: 24
  background_image: 109



```

### 多说评论

```
duoshuo: 
  on: true
  domain: luuman
  # 是否开启多说评论，http://duoshuo.com/create-site/
  # 使用上面网址登陆你的多说，然后创建站点，在 domain 中填入你设定的域名前半部分
  # http://<要填的部分>.duoshuo.com (domain只填上<>里的内容，不要填整个网址)

J:\Hexo\Hexo\themes\spfk\source\css\多说.css
```
#### 添加方法：
添加方法：打开「后台」 > 「多说评论」 > 「设置」 > 「基本设置」 > 然后把样式粘贴到「自定义CSS」文本框 > 「保存」

具体样式请参照：[多说.css](https://github.com/luuman/luuman.github.io/blob/master/resoures/%E5%A4%9A%E8%AF%B4.css "多说CSS样式集合")

### 头像

```
头像尺寸大概200*200px
E:\Github\Hexo\themes\spfk\source\img\head.jpg
```
### Apple Touch icon 苹果图标:

```
替换路径: /spfk/source/apple-touch-icon.png

E:\Github\Hexo\themes\spfk\source\img\favicon.png
```

### 背景

```
# Background | 背景
## "background_sum": show images form /source/background/的图片数目
## "on: true": 自动随机显示这5张图片
## "on: false": 自定义显示图片设置 background_image: 5
background:
  on: true
  #on: false
  background_sum: 24
  background_image: 109
```

### 文章摘要

```
title: 前端知识体系
date: 2016-01-16 13:58:41
description: 
categories:
- HTML 书籍
- HTML 书籍
tags:
- HTML 标签 
- HTML 标签
toc: true 文章目录
author:
comments:
original:
permalink: 
---
　　** 前端知识体系：**<Excerpt in index | 首页摘要> 

+ <!-- more -->
<The rest of contents | 余下全文>

```

### 404 Page:

```
hexo new page 404
And then set permalink: /404 in /source/404/index.md front matter.
在 Hexo 中创建匹配主题的404页面
```
[404.html](https://github.com/luuman/Hexo/blob/master/source/404/index.md "404")

[about.html](https://github.com/luuman/Hexo/tree/master/source/about "about")

## 主题结构：

```
.
├── languages            #多语言
|   ├── default.yml      #默认语言
|   └── zh-CN.yml        #中文语言
├── layout               #布局，根目录下的*.ejs文件是对主页，分页，存档等的控制
|   ├── _partial         #局部的布局，此目录下的*.ejs是对头尾等局部的控制
|   └── _widget          #小挂件的布局，页面下方小挂件的控制
├── source               #源码
|   ├── css              #css源码 
|   |   ├── _base        #*.styl基础css
|   |   ├── _partial     #*.styl局部css
|   |   ├── fonts        #字体
|   |   ├── images       #图片
|   |   └── style.styl   #*.styl引入需要的css源码
|   ├── fancybox         #fancybox效果源码
|   └── js               #javascript源代码
├── _config.yml          #主题配置文件
└── README.md            #用GitHub的都知道
```

![iPhone6](https://raw.githubusercontent.com/luuman/luuman.github.io/master/resoures/iPhone6-mockup.jpg)


## 关于Hexo迁移

最近，Waterstrong提交了一版，这版本可以将hexo布置在GitHub其下的其他项目，比如Blog等。但是还是有些东西需要修改。

```

非常感谢Waterstrong


# URL #这项暂不配置，绑定域名后，欲创建sitemap.xml需要配置该项
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://luuman.github.io/Blog/
root: /Blog/
permalink: :year/:month/:day/:title/
permalink_defaults:

上传是需要出入密码

# Deployment 站点部署到github要配置，上一节中已经讲过
## Docs: http://zespia.tw/hexo/docs/deploy.html
deploy:
  type: git
  #repository: git@github.com:luuman/Blog.git
  repository: https://github.com/luuman/Blog.git
  branch: gh-pages
```
[Blog](http://luuman.github.com/Blog "Blog")
[Blog](https://github.com/luuman/Blog "Blog of Waterstrong")
