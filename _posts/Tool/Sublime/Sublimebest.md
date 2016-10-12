title: Sublime Text历练
date: 2015-12-21 18:29:20
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
## 编辑器的选择（Editor Choices）
Sublime Text是一款跨平台代码编辑器（Code Editor），从最初的Sublime Text 1.0，到现在的Sublime Text 3.0，Sublime Text从一个不知名的编辑器演变到现在几乎是各平台首选的GUI编辑器。[官网地址](http://www.sublimetext.com/2)
从初学编程到现在，我用过的编辑器有EditPlus、UltraEdit、Notepad++、Vim、TextMate和Sublime Text，如果让我从中推荐，我会毫不犹豫的推荐Vim和Sublime Text，原因有下面几点：

>1. 跨平台：Vim和Sublime Text均为跨平台编辑器（在Linux、OS X和Windows下均可使用）。作为一个程序员，切换系统是常有的事情，为了减少重复学习，使用一个跨平台的编辑器是很有必要的。可扩展：Vim和Sublime Text都是可扩展的（Extensible），并包含大量实用插件，我们可以通过安装自己领域的插件来成倍提高工作效率。互补：Vim和Sublime Text分别是命令行环境（CLI）和图形界面环境（GUI）下的最佳选择，同时使用两者会大大提高工作效率。

>1. 优点：自动保存代码，代码高亮、语法提示、自动完成且反应快速。少用鼠标，多用键盘。
编辑器（Editor） vs 集成开发环境（Integrated Development Environment，下文简称IDE）

我经常看到一些程序员拿编辑器和IDE进行比较，诸如Vim比Eclipse强大或是Visual Studio太慢不如Notepad++好使之类的讨论比比皆是，个人认为这些讨论没有意义，因为编辑器和IDE根本是面向两种不同使用场景的工具：
编辑器面向无语义的纯文本，不涉及领域逻辑，因此速度快体积小，适合编写单独的配置文件和动态语言脚本（Shell、Python和Ruby等）。IDE面向有语义的代码，会涉及到大量领域逻辑，因此速度偏慢体积庞大，适合编写静态语言项目（Java、C++和C#等）。
我认为应当使用正确的工具去做有价值的事情，并把效率最大化，所以我会用Eclipse编写Java项目，用Vim编写Shell，用Sublime Text编写JavaScript/HTML/Python，用Visual Studio编写C#。
前言到此结束，下面进入正题。

## 界面
>1、概况：
>1. 从上到下：标题栏Title、菜单栏Menu、标签栏Tab、编辑区Editing Area、控制台Console、状态栏Status Bar。
>2. 从做到右：侧边栏（可关闭、文件、文件夹视图）、编辑区（代码编辑）、MiniMap（缩略图）。

>2. 菜单栏：
各种命令，各种设置。文件File：编辑Edit：选择Selection：查找Find：视图View：转到Goto：工具Tools：项目Project：首选项Preferences：个性化定制。帮助Help：

>3. 标签栏：
文件名的缩略图，文件编辑未保存，右上角有个小圆点，提示保存。如果未保存关了也不用害怕，自动保存。

>4. 状态栏：
ASCII编码、Line 6-Column 53（当前行列号）、Tab Size：4（Tab格式等信息）、HTML（当前语言）。

>5. 控制台：
使用Ctrl+`调出，它既是一个标准的Python REPL，也可以直接对Sublime Text进行配置。

>6. 编辑区：
这是我们主要的工作区域，ST2支持代码自动缩进，代码折叠功能。

>2、常见的功能：
1. 自动完成：
自动完成的快捷键是Tab，如果在html文件中，输入cl按下tab，即可自动补全为class=””；加上zencoding后，更是如虎添翼，后面再讲到
2. 多列编辑：
按住ctrl点击鼠标，会出现多个闪烁的光标，这时可同时修改多处，或者按住鼠标中键拖拽，
3. 代码注释功能：ctrl+/、ctrl+shift+/分别未行注释和块注释，再按一下就能去掉注释，ST2能够自动识别是html、css还是js文件，给出不同类型的注释。
4. 行操作：
ctrl+alt+↑、ctrl+alt+↓向上或者向下交换两行，ctrl+enter，光标后插入空行，ctrl+d选择相似，可以参考后面的快捷键列表。
5. 右键功能：
前3个，大家都知道，第4个，show unsaved changes，显示未保存的修改，红色减号表示删去的内容，绿色加号表示新增的内容
Open Containing Folder…，打开包含此文件的文件夹，这个很方便找到相关的文件
Copy File Path，复制文件路径，方便我们复制路径到浏览器中查看
Auto-Format Tags on Selection 格式化选中的文档，方便我们更清晰的查看代码结构，虽然ST2有自动缩进功能，但是当我们粘贴进一段没有格式化过的代码，就需要这个能了，这个功能要安装了Tag这个插件才会出现。
6. 人性化设计：
ST2虽然还是beta版中，但是有很多设计细节还是值得称赞的，比如点击一个标签或者括弧，会在起始处显示下划点线，方便看清代码结果，每一层嵌套代码间都有竖线，起到视觉辅助的作用。

## 设置
自定制，数据被保存在Preferences.sublime-settings，Default或User，user可以覆盖default。在配置文件，直接设置
配置文件在：preferences－setting user。
下面是一些可能有用但我很少用到的功能：
>宏（Macro）：Sublime Text支持录制宏，但我在实际工作中并未发现宏有多大用处。

>其它平台（Other Platforms）：本文只介绍了Windows平台上Sublime Text的使用，不过Linux和OS X上Sublime Text的使用方式和Windows差别不大，只是在快捷键上有所差异，请参考Windows/Linux快捷键和OS X快捷键。

>项目（Projects）：Sublime Text支持简单的项目管理，但我一般只用到文件夹。

>Vim模式（Vintage）：Sublime Text自带Vim模式。

>构建（Build）：通过配置，Sublime Text可以进行源码构建。

>调试（Debug）：通过安装插件，Sublime Text可以对代码进行调试。

## 快捷键
若稍有英文基础，则更建议打开Preferences->KeyBindings--Default，这里面是详细的快捷键配置。
快捷键设置，ST2的快捷键很多，改的时候注意不要覆盖了。
因为快捷键众多，所以有下面这种组合快捷键，先按下ctrl+k，松开k，再按下j就可以展开全部代码了。
 
 
快捷键列表（Shortcuts Cheatsheet）
我把本文出现的Sublime Text按其类型整理在这里，以便查阅。

```
>### 通用（General）
    ↑↓←→：上下左右移动光标，注意不是不是KJHL！
    Alt：调出菜单
### 整理（clear）
    Tab：缩进：自动完成
    Shift+Tab：去除缩进
    Ctrl+KT：折叠属性
    Ctrl+K0：展开所有
### 窗口（Window）
### 移动（Move）
    Ctrl+←/→：进行逐词移动
    Ctrl+Shift+←/→进行逐词选择
    Ctrl+↑/↓移动当前显示区域
    Ctrl+Shift+↑/↓移动当前行
    Ctrl+D：选择当前光标所在的词并高亮该词所有出现的位置，再次Ctrl+D选择该词出现的下一个位置，在多重选词的过程中，使用Ctrl+K进行跳过，使用Ctrl+U进行回退，使用Esc退出多重
### 编辑
    Ctrl+Shift+L：将当前选中区域打散
### 文件（File）
    Ctrl+N：在当前窗口创建一个新标签
    Ctrl+O：打开文件
    Ctrl+Shift+T：打开最近关闭的文件
    Ctrl+S：保存
    Ctrl+Shift+S：另存为
    Ctrl+Shift+N：创建新窗口
    Ctrl+Shift+W：关闭窗口
    Ctrl+W：关闭当前标签，当窗口内没有标签时会关闭该窗口
### 编辑（Edit）
    Ctrl+Z：撤销
    Ctrl+Y：恢复
### 取消选择（Undo Selection）
    Ctrl+U：智能撤销
    Ctrl+ Shift+U：智能重做
    Ctrl+ Shift+V：粘贴并缩进
    Ctrl+K，Ctrl+V：
### 行（Line）
    Ctrl +]：缩进
    Ctrl +[：反缩进
    Ctrl + Shift + Up：上移一行 
    Ctrl + Shift + Down：下移一行
    Ctrl + Shift + D：复制行(加倍)
    Ctrl + Shift + K：删除行
    Ctrl + J：连接行
### 文本（Text）
    Ctrl+Shift+Enter：在当前行上面增加一行并跳至该行
    Ctrl+Alt+Enter：替换所有关键字匹配
    Ctrl+Enter：在当前行下面新增一行然后跳至该行
    Ctrl+Delete：删除单词前部
    Ctrl+Backspace：删除单词后部
    Ctrl+K，Ctrl+K：从光标处删除至行尾
    Ctrl+K+Backspace：从光标处删除至行首
    Ctrl+T：前后调转
### 注释（Comment）
    Ctrl+/：注释（如已选择内容，同“Ctrl+Shift+/”效果）
    Ctrl+Shift：/：块注释(注释已选择内容)
    Ctrl+Alt+/：块注释，并Focus到首行，写注释说明用的
### 标签（Tag）
    Alt+.：闭合当前标签
    Ctrl+Shift+A：选择标签(可重复)
    Ctrl+Shift+W：选择区域被标签包含
### （Mark）
    Ctrl+K， Alt+Space：设置记号
    Ctrl+K，Alt+A：选择到记号
    Ctrl+K，Alt+W：删除到记号
    Ctrl+K，Alt+S：交换(移动)记号
    Ctrl+K，Alt+G：移除记号
    Ctrl+K，Alt+Y：Yank
    Ctrl+K，Alt+J：取消所有折叠
### 代码折叠（Code Folding）
    Ctrl+Shift+[：折叠代码
    Ctrl+Shift+]：展开代码
    （Convert Case）
    Ctrl+K，Ctrl+U：改为大写
    Ctrl+K，Ctrl+L：改为小写
### （Wrap）
    Alt+Q：
    Ctrl+Space：显示提示
    F9：按行排序
    Ctrl+F9：按行排序(区分大小写)
### 选择（Selection）
    Ctrl+ Shift+L：分割为多光标(选择多行时)
    Ctrl+ Alt +Up：向上一行添加光标
    Ctrl+ Alt +Down：向下一行添加光标
    Escape单光标
### 扩展（Expand）
    Ctrl+A：全选
    Ctrl+L：选择整行（按住-继续选择下行）
    Ctrl+D：选词：（按住-继续选择下个相同的字符串）
    Ctrl+Shift+Space：快速选择当前作用域（Scope）的内容
    Ctrl+Shift+M：快速选择括号间的内容{}
    Ctrl+Shift+J：快速选择同缩进的内容
    Ctrl+Shift+A：选择光标位置父标签对儿
### 查找（Find）
    Ctrl+F：进行标准查找
    F3：跳至当前关键字下一个位置
    Shift+F3：跳到当前关键字上一个位置
    Ctrl +I：
    Ctrl +H：进行标准替换
    Ctrl+Shift+H：替换当前关键字
    Ctrl +F3：快速查询
    Alt +F3：选中当前关键字出现的所有位置
    Ctrl+D：快速查询下一个(多光标)
    Ctrl+K，Ctrl+D：快速查询跳过下一个(多光标)
    Ctrl+E：字
    Ctrl+Shift+E：字
    Ctrl+Shift+F：多文件搜索&替换
### 视图（View）
    Ctrl+K，Ctrl+B：侧边栏开关Side Bar
    Ctrl+`：调出控制台
    F11：切换普通全屏
    Shift+F11：切换无干扰全屏
    Alt+Shift+2：进行左右分屏
    Alt+Shift+5：进行上下左右分屏
    Alt+Shift+8：进行上下分屏。
    分屏，使用Ctrl+数字键跳转到指定屏，使用Ctrl+Shift+数字键将当前屏移动到指定屏
### 组（Group）：
    Ctrl+K，Ctrl+Up：
    Ctrl+K，Ctrl+ Shift+ Up：
    Ctrl+K，Ctrl+Down：
### 焦点小组（Focus Group）：
    Ctrl+K，Ctrl+Right：
    Ctrl+K，Ctrl+ Left：
    Ctrl+1：组间切换焦点
    Ctrl+ Shift +1：移动文件到组
    Syntax语法和文件类型、indentation缩排、Line Endings行尾结束符号
    F6：拼写检查
    Ctrl + F6：下一个错误
    Ctrl+Shift+ F6：上一个错误
### 跳转（Goto）
    Ctrl+P：跳转到指定文件
    Ctrl+R：跳转到指定符号
    Ctrl+Shift+R：
    F12：
    Ctrl+G：跳转到指定行号
    Alt+-：跳转到底部
    Alt+Shift +-：
### 文件开关（Switch File）
    Ctrl+Pagedown：下一个文件
    Ctrl+Pageup：上一个文件
    Ctrl+Tab：下一个文件(stack)
    Ctrl+Shift + Tab：上一个文件(stack)
    Alt+O：
    Alt+1：最近打开文件
### 滚动（Scroll）
    Ctrl+K，Ctrl+C：滚动到光标处
    Ctrl+Up：向上滚动一行(定光标)
    Ctrl+Down：向下滚动一行(定光标)
### 书签（Boolmarks）
    Ctrl+F2：设置书签
    F2：下一个书签
    Shift+F2：上一个书签
    Ctrl+Shift+F2：清除书签
    Alt+F2：全选书签
    Ctrl+M：在起始括号和结尾括号间切换
### 工具（Tools）
    Ctrl+Shift+P：调出命令板（Command Palette）
    Ctrl +B：
    Ctrl+Shift+B：
    Ctrl +Break：
    F4：
    Shift+ F4：
    Ctrl +Q：
    Ctrl+Shift+Q：
### 项目（Project）
    Ctrl+Alt+P：切换项目
    #### 首选项（Preferences）
    Ctrl+ Keypad Plus：
    Ctrl+Shift+Keypad Plus：
    Help（帮助）
```

## 总结：
### 多行游标：
```
方法一：利用查找替换功能：Ctrl + H
方法二（推荐）：Ctrl+D选中另一个，如果有某些不想添加新行的模式则按ctrl+K，ctrl+D跳过这个进入下一个符合条件的模式行。
按Alt + F3快捷键，全选所有符合条件的单词。
如果要在每行都加入光标，可以先ctrl+A然后ctrl+shift+L即可。
如果在某个字符的多行后面加上光标，可以将光标放在这个字符后面，按住shift键，然后右键可以向下拖动产生多个光标。
```
### Goto anything：（模糊匹配）
```
Ctrl+P：跳转到指定文件，输入文件名后可以：
@ 符号跳转：输入@symbol跳转到symbol符号所在的位置
# 关键字跳转：输入#keyword跳转到keyword所在的位置
: 行号跳转：输入:12跳转到文件的第12行。
```
命令快捷执行：
```
Ctrl+Shift+P：输入set syntax JavaScript进行文件类型更改。
输入Minimap进行迷你地图切换。
```
快速添加新行
```
Ctrl + Enter可以在当前行下新建一行。 
Ctrl + Shift + Enter可以在当前行上面添加一行。
```



## 最后购买：
Sublime Text2或者3都没关系，3也只是作为2的beta版本，所以还是推荐3吧，支持新版嘛。2和3在使用方法功能上也有差异~
你可以去官网下载对应版本，但可能需要输入序列号什么的。访问[下载 2.x 版本](http://www.sublimetext.com/2)。或从[下载 3.x 版本](http://www.sublimetext.com/3)。

注册码（仅供个人非商业应用）：
```
----- BEGIN LICENSE ------
Alexander
Single User License
EA7E-814345
51F47F09 4EAB1285 7827EFF0 8B1207DC
A76A6EA3 E1A1CA7A DC1F2703 14,897,784
8EDC1C82 3F2A58B9 1C0C8B24 67686432
281245B3 6233DE5C ADC5C2F9 61FB8A04
171B63EF 86BA423F 6AC884FD 3273A7AA
5F50A6DB CE7859AE D62D2B37 AEEDD8C2
078A8A20 70EEA791 84F48C1E 8ABA7DEB
0B3907C0 C9A3523B 0091A045 6F67AED8
------ END LICENSE ------
```
```
----- BEGIN LICENSE -----
Andrew Weber
Single User License
EA7E-855605
813A03DD 5E4AD9E6 6C0EEB94 BC99798F
942194A6 02396E98 E62C9979 4BB979FE
91424C9D A45400BF F6747D88 2FB88078
90F5CC94 1CDC92DC 8457107A F151657B
1D22E383 A997F016 42397640 33F41CFC
E1D0AE85 A0BBD039 0E9C8D55 E1B89D5D
5CDB7036 E56DE1C0 EFCC0840 650CD3A6
B98FC99C 8FAC73EE D2B95564 DF450523
------ END LICENSE ------
```
搜索3114注册码
```
—– BEGIN LICENSE —–
Anthony Sansone
Single User License
EA7E-878563
28B9A648 42B99D8A F2E3E9E0 16DE076E
E218B3DC F3606379 C33C1526 E8B58964
B2CB3F63 BDF901BE D31424D2 082891B5
F7058694 55FA46D8 EFC11878 0868F093
B17CAFE7 63A78881 86B78E38 0F146238
BAE22DBB D4EC71A1 0EC2E701 C7F9C648
5CF29CA3 1CB14285 19A46991 E9A98676
14FD4777 2D8A0AB6 A444EE0D CA009B54
—— END LICENSE —
```
## 汉化：
可以网上找些中文包放进去就行了。
[Sublime Text 全程指南：](http://lucida.me/blog/sublime-text-complete-guide/ )


## 插件：
插件的选择：
主题：blackboard 
SideBarEnhancements（侧边栏增强，添加浏览器） 
Zen Coding  
advanceNewfile
SyncedSideBar
tag

JsFormat（javascript格式化） 
ColorPicker （调色盘） 
GBK to UTF8
GBK Encoding Support（GBK中文编码）
SublimeLinter（代码错误提示） 总体架构
snippets（自定制代码补齐机制）

## 快捷代码：
1. 跳到行首行尾的快捷键
```
    [
        //跳到行首行尾的快捷键
        { "keys": ["ctrl+k", "ctrl+h"], "command": "move_to", "args": {"to": "bol", "extend": false} },
        { "keys": ["ctrl+k", "ctrl+e"], "command": "move_to", "args": {"to": "eol", "extend": false} }
    ]
```
先按ctrl+k，然后按ctrl+h（home首字母）光标移动到行首；先按ctrl+k，然后按ctrl+e（end首字母）光标移动到行尾。

## 设置Setting

```
//Set Update false
"update_check": false,
```

## 延伸阅读（Further Reading）：
1、书籍（Books）
Mastering Sublime Text：我读过的唯一一本关于Sublime Text的书籍，书中介绍的插件很实用，但对编辑技巧介绍不全。
Instant Sublime Text Starter：另外一本关于Sublime Text的书，我没有读过。
2、链接（Links）
 [官方文档：](http://www.sublimetext.com/docs/3/)
 [官方论坛：](http://www.sublimetext.com/forum/)
Stack Overflow的Sublime Text频道：
 [sublimetext](http://stackoverflow.com/questions/tagged/sublimetext)
 [sublimetext2](http://stackoverflow.com/questions/tagged/sublimetext2)
 [sublimetext3](http://stackoverflow.com/questions/tagged/sublimetext3)
 [非官方文档：](http://sublime-text-unofficial-documentation.readthedocs.org/) 甚至比官方文档还要全面！
 [Package Control： ](https://sublime.wbond.net/)大量的Sublime Text插件和主题。
3、视频（Videos）
 [Getting Started with SublimeText：](https://www.youtube.com/watch?v=04gKiTiRlq8)
 [Sublime Text Pefect Workflow：](https://www.youtube.com/watch?v=bpEp0ePIOEM&list=PLuwqxbvf3olpLsnFvo06gbrkcEB5o7K0g)