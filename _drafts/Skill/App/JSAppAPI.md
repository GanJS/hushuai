title: 公司app js接口V1
date: 2016-01-19 14:11:20
description: 
categories:
- App
tags:
- App
toc: true
author:
comments:
original:
permalink: 
---
　　** ：**
<!-- more -->

/* 
* @Author: luuman
* @Last Modified by:   luuman
* @Date:   2016-03-09 13:13:56
* @Last Modified time: 2016-04-07 14:29:18
* @Function: Interface arrangement
*/

// 统计接口
function sum(num){
    $.ajax({
        type: 'GET',
        url: 'http://v2.jingqubao.com/w3g/Statistic/record',
        data: {
            url: num,
            status:'1',
            type:'act_photo',
        },
        dataType: 'json',
        success: function(){
        },
        error: function(){
        },
    });
}

//在微信中隐藏
var ua = navigator.userAgent.toLowerCase();
if(ua.match(/MicroMessenger/i) == "micromessenger"){  
    $(".share").css("display","none");
}

//在微信中点击，传输数据
$(".Tour_page").click(function(){
    var oId = $(this).data('id');
    AppScenic(oId);
    AppUserPage(oId);
});

function share2(Tag){
    sum(Tag);
    var title="第二季媳妇代言景区火热报名中";
    var content="情人眼里出女神，我为媳妇抢代言";
    var iconUrl="http://v2.jingqubao.com/apps/w3g/_static/img/wife/shares_2.jpg.jpg";
    var targetUrl=oUrl; // 分享链接
    if(typeof(UserModel) == "undefined"){
    }else{
        UserModel.shareContentIconUrlTargetUrl(title,content,iconUrl,targetUrl);  //分享接口
    }
}

/**
 * App 分享接口
 * 接口 - (void)share:(NSString *)title content:(NSString *)content iconUrl:(NSString *)iconUrl targetUrl:(NSString *)targetUrl;//分享
 */
function AppShare(oUrl,oTitle,oDesc,oImgUrl){
    if(typeof(UserModel) == "undefined"){
    }else{
        UserModel.shareContentIconUrlTargetUrl(oTitle,oDesc,oImgUrl,oUrl);  //分享接口
    }
}

// <script type="text/javascript" src="http://res.wx.qq.com/open/js/jweixin-1.0.0.js"></script>

var ua = navigator.userAgent.toLowerCase();
if(ua.match(/MicroMessenger/i) == "micromessenger"){  
    $(".share").css("display","none");
}

// 分享信息提取
function oShare(){
    // 分享定制
    var oUrl = '';
    var oTitle = '';
    var oDesc = '';
    var oImgUrl = '';
    if(typeof(UserModel) !== "undefined"){
        UserModel.shareContentIconUrlTargetUrl(oTitle,oDesc,oImgUrl,oUrl);  //分享接口
    }else{
        WeiShare(oUrl,oTitle,oDesc,oImgUrl);
    }
}

/**
 * 微信分享定制接口
 */
function WeiShare(oUrl,oTitle,oDesc,oImgUrl){
    wx.config({
        debug: false,
        appId: 'wxdcb447934ddf8be6',
        timestamp: '<?php echo $timestamp ?>',
        nonceStr: '<?php echo $noncestr; ?>',
        signature: '<?php echo $sign ?>',
        jsApiList: [
            'checkJsApi',
            'onMenuShareTimeline',
            'onMenuShareAppMessage',
            'onMenuShareQQ',
            'onMenuShareWeibo']
    });
    wx.ready(function(){
        // 设置"发送给朋友圈"参数
        wx.onMenuShareTimeline({
          title: oTitle,          // 分享标题
          link: oUrl,             // 分享链接
          imgUrl: oImgUrl,        // 分享图标
          success: function(res) {}, // 用户确认分享后执行的回调函数
          cancel: function() {} // 用户取消分享后执行的回调函数
        });
        // 设置"发送给朋友"参数
        wx.onMenuShareAppMessage({
            title: oTitle,          // 分享标题
            desc: oDesc, // 分享描述
            link: oUrl,             // 分享链接
            imgUrl: oImgUrl,        // 分享图标
            success: function() {}, // 用户确认分享后执行的回调函数
            cancel: function() {} // 用户取消分享后执行的回调函数
        });
        // 设置"发送给QQ"参数
        wx.onMenuShareQQ({
            title: oTitle,          // 分享标题
            link: oUrl,             // 分享链接
            imgUrl: oImgUrl,        // 分享图标
            success: function() {}, // 用户确认分享后执行的回调函数
            cancel: function() {} // 用户取消分享后执行的回调函数
        });
    });
}

/**
 * 页面跳转下载页面
 */
function AppDown(){
    window.location.href="http://a.app.qq.com/o/simple.jsp?pkgname=com.jingqubao.tips";
}

/**
 * 发布旅图
 * 实例 ("#用美食，祭身材#")，可以为空
 */
function AppTravel(){
    if(typeof(UserModel) !== "undefined"){
        UserModel.publishTravelPhoto("");
    }else{}
}

/**
 * 发布旅图V2
 * 实例 ("2","#用美食，祭身材#")
 * 接口 - (void)publishTravelPhotoWithTopicId:(NSString *)topicId content:(NSString *)content;//发布旅图，参数为主题ID、内容
 */
function AppTravelNew(ID,Title){
    if(typeof(UserModel) !== "undefined"){
        UserModel.publishTravelPhotoWithTopicIdContent(ID,Title);
    }else{}
}

/**
 * 景区页面（景区ID）
 * 实例 ("21213")
 */
function AppScenic(id) {
    if(typeof(UserModel) !== "undefined"){
        UserModel.scenicInfo(id);
    }else{}
}

/**
 * 用户旅图详情页（旅图ID）(接口不稳定)
 * 实例 ("21213")
 * 接口 - (void)enterTravelPhotoInfo:(NSString *)feedId;//旅图详情页
 */
function AppUserPage(id) {
    if(typeof(UserModel) !== "undefined"){
       UserModel.enterTravelPhotoInfo(id);
    }else{}
}
/**
 * 用户旅图页（旅图）(接口不稳定)
 * 接口 - (void)enterTravelPhotoList;//旅图页
 */
function AppUserPage(id) {
    if(typeof(UserModel) !== "undefined"){
       UserModel.enterTravelPhotoList();
    }else{}
}


window.onload=function(){location.href="tipsTravel://";var n=window.navigator.userAgent,e="";e=/iphone/i.test(n)&&/micromessenger/i.test(n)?"http://a.app.qq.com/o/simple.jsp?pkgname=me.ele":"http://h.ele.me/dapp"+location.search,document.getElementById("go").setAttribute("href",e)};