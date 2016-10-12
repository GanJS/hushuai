title: Sublime插件
date: 2015-12-21 18:29:10
description: 来到GitHub这么长时间，才开始真真的了解GitHub，这个国外的代码托管平台，充满着大牛的身影。
categories:
- Tool
tags:
- Sublime
toc: true
author:
comments:
original:
permalink:
---
---
　　**自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why
<!-- more -->
## 安装有两个办法：
>1、直接把插件放到它的安装路径对应文件包packages里面去，不知道在哪的可以直接打开 preferences->Browse packages，放进去之后软件会自动检测。

>2、使用命令方式直接让软件自己下载安装。（使用package control组件）（前提：先安装下面那个package control插件)

>按下Ctrl+Shift+P调出命令面板，输入install， 调出 Install Package 选项并回车，然后在列表中选中要安装的插件。

>下载拷贝：然后把它放到package文件包中。没用过Github的朋友不知道在哪里下载。Download ZIP。然后把它解压，把文件夹放进package文件包，然后它就能检测到包啦！

>代码安装：Ctrl+shift+p、输入install、选择package install 过几秒会弹出另一个框。然后在输入框中输入你想要的插件关键字安装吧！大致就是这样，简单明了。下面介绍其他常用插件，安装方式同理！

>### 常用插件：
* [package control（包裹组件）]()
  * 通过快捷键 ctrl+` 或者 View > Show Console 菜单打开控制台，然后粘贴对应的版本代码进去，然后回车让它安装。

适用于 Sublime Text 3：

```
import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```
适用于 Sublime Text 2：

```
import urllib2,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
```
当然了，有些时候这样你安装不进去的，就只能自个去下载安装包放到package文件里边去了（就是上边我说的那个文件夹)如果在Preferences → Package Settings 中看到 Package Control 这一项，说明安装成功。


## 插件整理

>### 代码整理：

* [Tag（代码格式化）]()
  * 全选Ctrl+A，Ctrl+Alt+F
* [HTMLBeautify（）]()
  * 格式化HTML。
* [HTML/CSS/JS Prettify（代码格式化）]()
  * 能够格式化css html和js。
  * 注意：格式化的文件路径中不能有中文，不然会报找不到node的错误（windows下）。
* [YUI Compressor（压缩JS和CSS文件） ]()
* [PHPTidy（整理与排版PHP代码）]()
* [JsFormat（javascript格式化） ]()
  * 格式化js代码，这个插件很有用，我们有时在网上看到某些效果，想查看是怎么实现的，但是代码被压缩过，很难阅读，不用怕，用ST2打开，按下ctrl+alt+5（这是我设置的快捷键），即可让代码还原，莫非是武林中失传已久的“还我靓靓拳”。

>### 注释：

* [DocBlockr（代码自动注释生成） ]()
* [HtmlTidy（清理与排版你的HTML代码）]()
* [AutoPEP8（）]()
  * 格式化Python代码。
* [Alignment安装案例]()
* [Alignment（代码补齐）补齐就是补齐~就像这样]()

>### 代码简写：

* [SublimeCodeIntel（代码提示）]()
  * 自动提示我们，可能要输入HTML代码内容
* [snippets（自定制代码补齐机制）]()
  * 自定制代码补齐机制，
* [Emmet（Zen Coding 代码自动补齐） ]()
  * 通过简单的命令直接生成一大段代码！一个字又快又准，安装好插件后，使用Ctrl＋Alt＋Enter呼出ZenCoding。
我们可以用 div#content>ul>li*3>a* [href="javascript:void(0);"]{Links$} 这样短短的一句话，生成下面一段代码：
技巧：
前端必备，快速开发HTML/CSS

输入 div.wrapper>div.header+div.main+div.footer 按下Tab，立刻变成

或者按下ctrl+alt+enter，激发zencoding控制台，可看到整个动态的过程。


>### 高亮显示：

* [BracketHighlighter]()
  * BracketHighlighter高亮显示匹配的括号、引号和标签，BracketHighlighter这个插件能在左侧高亮显示匹配的括号、引号和标签，能匹配的* [] ,  ()   * ,  {} ,  "" ,  '' , <tag></tag>等甚至是自定义的标签，当看到密密麻麻的代码分不清标签之间包容嵌套的关系时，这款插件就能很好地帮你理清楚代码结构，快速定位括号，引号和标签内的范围。
* [TrailingSpacer（高亮显示多余的空格和Tab）]()

>### 颜色：

* [ColorPicker （调色盘） ]()
  * 在编辑CSS样式的时候，ColorPicker可以让sublime text 内置一个调色盘，调好颜色，点击OK就会在光标处生成十六进制颜色代码。

>### CSS：

* [CSScomb（CSS属性排序） ]()
* [CSS3_Syntax（css语法高亮）]()
  * 对css语法高亮的支持，view-syntax-css3选中css3就能使用css3高亮了。必须每条属性都加上分号，并且属性必须小写，不然不会高亮，有点鸡肋啊。
* [Prefixr（自动加-webkit前缀）]()
  * 写 CSS可自动添加 -webkit 等私有词缀，Ctrl+Alt+X触发。
* [Autoprefixer（自动加前缀）]()
  * 可以给css自动加前缀功能
* [Goto-CSS-Declaration（CSS文件跳转）]()
  * 跳转到css文件该class的声明处，方便修改查看，如图下所示，注意对应的css文件要同时打开才行。

>### 编码：

* [GBK Encoding Support（GBK中文编码）]()
  * 这个插件还是非常有用的，因为sublime 本身 不支持gbk编码，在utf8如此流行的今天，我们整站还是gbk编码，o(︶︿︶)o 唉，所以全靠这个插件了。
* [GBK to UTF8（编码转换）]()
  * 将文件编码从GBK转换成UTF8，菜单 – File里面找。


>### 文档管理：

* [Nettus+ fetch （管理一些开源框架）]()
  * 配置文件修改，Ctrl+Shift+P输入Fetch Manage，配置文档。通过输入fetch file，搜索框架名进行导入。
* [SideBarEnhancements（侧边栏增强） ]()
* [SyncedSideBar（侧边栏打开文件定位）]()
  * 支持当前文件在左侧面板中定位，不错。
* [Hex-to-HSL-Color Hex（颜色模式转HSL颜色模式）]()
* [advanceNewfile（面板随意添加文件）]()
  * 按Ctrl+Alt+N，下方输入A\B\test.css就好了，test.css这个文件出现在某个文件夹。
* [SublimeTmpl （自定义新建文件） ]()
  * 默认已经添加了html、css、js等常见类型的面板，按ctrl+alt+h/ctrl+alt+c/ctrl+alt+j可新建这 3钟类型的文件，快捷键在这里\Packages\SublimeTmpl\Default (Windows).sublime-keymap, 模板文件在这里\Packages\SublimeTmpl\templates，可修改。 比如下边简单的html文件
* [DocBlockr（代码建立文档）]()
  * DocBlockr 可以使你很方便地对代码建立文档。它会解析函数，变量，和参数，根据它们自动生成文档范式，你的工作就是去填充对应的说明。
* [GotoRecent（历史文档记录）]()
  * 打开最近的文件，系统有这个功能，但只能看最近8个，有点不爽，按ctrl+e，选择即可。

>### 语法识别：

* [jQuery（jQuery语法识别）]()
  * 支持jquery的只能语法提示，很赞。
* [JavaScriptNext - ES6 Syntax（ES6语法识别）]()
  * 提供ES6的语法支持。
* [WordPress（WordPress的函数）]()
  * 集成一些WordPress的函数，对于像我这种经常要写WP模版和插件的人特别有用
* [Vintage（Vim模拟）]()
  * 如果你习惯使用vim，那么可以安装这个插件，这个插件可以让sublime像vim一样。
* [LESS（LESS语法识别）]()
  * 这是一个非常棒的插件，可以让sublime支持less的语法高亮和语法提示，对于搞less的同学灰常重要，不过多解释。
* [SCSS（SCSS语法识别）]()
  * 支持scss的语法高亮，里面附带了好多CSS Snippet，无论现用或者改造成，都可节省不少时间。
* [Liquid（Liquid语法识别）]()
  * 提供Liquid语法支持，如果你也写博客的话不妨试试。
* [Smarty（Smarty语法识别）]()
  * 提供smarty语法的支持。Smarty插件默认的分隔符是{}，如果你使用的分隔符不同可以更改插件目录的Smarty.tmPreferences文件，找到其中的SMARTY_LDELIM和SMARTY_RDELIM，修改为你的分隔符即可。


>### 文件传输：

* [SFTP（编辑 FTP 或 SFTP 服务器上的文件）]()
* [Package Syncing]()
  * 最后推荐一个同步插件，这个插件可以在不同的机器同步配置信息和插件，非常方便，但鉴于国内的墙太高，我都是直接把插件给手动备份了，然后直接拖进去，或者直接去github上下载对应的包。


>### 其他：

* [Gits（集成 GitHub） ]()
* [Clipboard-history（粘贴板历史记录） ]()
  * 可以保存粘贴的历史，很赞的功能，再也不用担心历史丢失了。ctrl+alt+v可打开历史面板，上下选择即可，安装后会和默认的ctrl+shift+v（粘贴缩进）冲突，干掉这个快捷键。
* [lint（语法校验）：]()
* [SublimeLinter（代码错误提示） 总体架构]()
* [Jslint编程风格]()
  * Sub
* [Tradsim（中文繁字体和简体字转换） ]()
* [Terminal]()
  * 可以sublime中，打开命令行，非常方便哦。
* [AllAutocomplete]()
  * 自动完成插件，可在全部打开的文件中，自动完成。
* [HexViewer]()
  * 提供十六进制文件查看功能。
* [MultiEditUtils]()
  * 扩展多行编辑的功能。
* [IMESupport（输入框不更随着光标）]()
  * 

## 主题（Themes）
Sublime Text有大量第三方主题：

>1、Facebook Material Theme

>2、Soda