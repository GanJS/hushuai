title: 电脑优化相关
date: 2015-12-26 14:11:20
description: 
categories:
- Skill
tags:
- window 7
toc: true
author:
comments:
original:
permalink: 
---
　　** 自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why
<!-- more -->
## windows系统装机必备软件
把这个清单写下来，每次重装系统都可以按图索骥

### 基本
	win7 64 sp3 操作系统
	搜狗输入法
	Microsoft Office 2010
	qq
	微信
	360压缩
	Abobe Reader
	Abobe Flash Player
	ADSafe
	迅雷看看
	photoshop cc 2015
	360网盘
	百度云网盘
	有道词典

### 前端开发
	firefox+firebug 浏览器
	chrome + Proxy SwitchySharp 浏览器
	sublime text（代码编辑器）
	Fiddler2 

### 驱动
	LenovoDM（联想驱动）
	魔方（优化美化）
	驱动精灵万能网卡版
### 工具
	8UFTP
	foxmail
	KeePass 密码管理工具
	gow 命令行增强
	everything 文件名搜索
	SecureCRT ssh登录管理工具
	MarkdownPad 写文档专用编辑器
	.net framework 4.0 系统包
### 工具
	XSkyWalker（外网浏览器）
	WVS网站扫描工具


## 笔记本美化

### 安装前准备
>1、应用软件：魔方
2、素材：
登陆界面背景、系统壁纸、系统主题、开机动画、开机关机铃声

#### 开机关机铃
	* 海贼王DEAR FRIEND
	海贼王OST回忆
	海贼王进行曲
	海贼王圣诞歌
	* 海贼王我当定了

#### 开机动画
	S.H.I.E.L.D
	activity（系统自带）

#### 如何设置 Windows 7 的休息提醒？
	直接使用cmd命令shutdown -s -t 7200，两个小时候右下方会提示将要关机，如果你还想继续玩，可以取消！

## USB ICON

### 一、安装前准备
>U盘、电脑、ICON.ico（U盘图标）、autorun.inf（ICON）、desktop.inf（Bg）、background.jpg（背景图片）、1.bat（显示文件）、2.bat（隐藏文件）

>将文件存放在，U盘的根目录下即可，双击“2.bat”隐藏文件。

#### autorun.inf
	[autorun]
	ICON=ICON.ico

#### desktop.inf
	[ExtShellFolderViews]
	[{BE098140-A513-11D0-A3A4-00C04FD706EC}]
	InfoTip=hello
	IconArea_Image=background.jpg

#### 1.bat
	@echo off
	attrib ../desktop.ini +r +a +s +h
	attrib ../background.jpg +r +a +s +h
	attrib ../autorun.inf +r +a +s +h
	attrib ../ICON.ico +r +a +s +h

#### 2.bat
	@echo off
	attrib ../desktop.ini -r -a -s -h
	attrib ../background.jpg -r -a -s -h
	attrib ../autorun.inf -r -a -s -h
	attrib ../ICON.ico -r -a -s -h


## win7开机动画DIY
自己在做的时候没要找到一个完善的教程所以在此写一个，所有经验都来自互联网，我只是系统的整理一下。BY：zby

1、首先制作FLASH，注意开机动画格式为【200像素X200像素】共【105】帧且前【60】帧为一次性播放后【45】帧为重复播放

注：下面是我自己做的flash，保存的GIF动画

 

![win7开机动画制作](http://upload-images.jianshu.io/upload_images/1064727-b0b6adb60e10a154.jpg)

 

2、flash制作完成后，影片导出时选择PNG序列格式，就得到了105张图片了。

注:记得选择【完整文档大小】

 

![win7开机动画制作](http://upload-images.jianshu.io/upload_images/1064727-904770c5382c1605.jpg)

![win7开机动画制作](http://upload-images.jianshu.io/upload_images/1064727-a6ffefaa9a05e8e4.jpg)

![win7开机动画制作](http://upload-images.jianshu.io/upload_images/1064727-fb3eab668452d471.jpg)

 

3、之后将105张图片在PS中合并，由于PS一次仅支持100张所以要分开合并。第一段5张，第二段100张。

注：合并时请耐心等待，两次合并的初始文档大小分别为（1）宽【200像素X1000像素】(2)【200像素X20000像素】

 

![win7开机动画制作](http://upload-images.jianshu.io/upload_images/1064727-24ccd860a112681d.jpg)

![win7开机动画制作](http://upload-images.jianshu.io/upload_images/1064727-e747f9adc02c4cba.jpg)

![win7开机动画制作](http://upload-images.jianshu.io/upload_images/1064727-0fbcf67c6e325caf.jpg)

 

4、将得到的两段图片拼合，并保存为BMP格式即可

注：最终文档大小为【200像素X21000像素】

 

![win7开机动画制作](http://upload-images.jianshu.io/upload_images/1064727-b3dd9d8fe7cf5c75.jpg)

![win7开机动画制作](http://upload-images.jianshu.io/upload_images/1064727-6c009865418c1a14.jpg)

 

5、最后使用软媒魔方中的美化大师，将得到的BMP更改为新的开机动画即可

 

![win7开机动画制作](http://upload-images.jianshu.io/upload_images/1064727-89cc7e1b14395e7b.jpg)

 

END

 

注意事项

ps自动合并间距输入0.001即可得到0。

 

如果想换回去，记得备份。

 

如果想要将视频设置为开机动画可参考此处http://tieba.baidu.com/p/3139701776

 

以上软件为CC 2014版，PS3已经有合并功能

nkx2G��Ҟyg�



## PS CC 2015安装
1. 安装前准备，下载：Photoshop_16_LS20_win64、Adobe破解补丁等。
安装PS，点击Setup进行安装。安装时需要账号，选择使用512@，Qq
1. 如链接失效 请自行搜索下载
Adobe Photoshop CC 2014安装包及破解补丁64位下载 http://pan.baidu.com/s/1eQtNLRk
Adobe Photoshop CC 2014安装包及破解补丁32位下载 http://pan.baidu.com/s/1dGW5w
1、下载以上对应系统的安装包及破解补丁（教程以64位为例） 解压压缩文件得一个文件夹 右键“以管理员方式运行”里面的“Set-up”
 
2、可能出现以下情况  不用管 点击“忽略”接下来点击“试用”
  
3、接下来先不急着操作下一步  打开360流量防火墙找到“PDapp.exe”这个程序  右键“禁止访问网络”（其他安全软件也有类似功能，实在不行拔网线，简单粗暴）
 
4、接下来就可以点击“登录”了  什么？没有网！ 第三步的目的达到  “以后再说”
  
5、接下来就是人人都会的了 “接受”即可  然后选择你要的安装路径 “安装”
  
6
安装时间几分钟左右  值得注意的是安装完毕后先不要打开 点击“关闭”
 
7、复制破解补丁“amtlib.dll”粘贴至PS CC 2014安装目录下  选择“替换”
  
8、打开软件 还有个协议  点击“接受”即可    请尽情使用吧
 
1. 插件：安装cutterman
C:\Users\UUhike\AppData\Roaming\Adobe\CEP\extensions插件安装的文件地址。