title: 微信SDK
date: 2015-12-25 18:29:00
description: 
categories:
- WeChat
tags:
- WeChatSDK
toc: true
author:
comments:
original:
permalink: 
---

　　**自用笔记：**
<!-- more -->

# H5地理位置定位

## 微信

### 要求：
使用公众号的支持，

#### 1. 获取用户地理位置(用于公众号的开发)

```
<xml>
<ToUserName><![CDATA[toUser]]></ToUserName>
<FromUserName><![CDATA[fromUser]]></FromUserName>
<CreateTime>123456789</CreateTime>
<MsgType><![CDATA[event]]></MsgType>
<Event><![CDATA[LOCATION]]></Event>
<Latitude>23.137466</Latitude>
<Longitude>113.352425</Longitude>
<Precision>119.385040</Precision>
</xml>
```
[获取用户地理位置](https://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1421140841&token=&lang=zh_CN "")

#### 2. 网页服务——地理位置——获取地理位置接口——微信JS-SDK说明文档

1.微信网页授权

2.微信JS-SDK说明文档
>步骤一：绑定域名
步骤二：引入JS文件
步骤三：通过config接口注入权限验证配置
步骤四：通过ready接口处理成功验证
步骤五：通过error接口处理失败验证


>HTML

```
<script type="text/javascript" src="http://res.wx.qq.com/open/js/jweixin-1.0.0.js"></script>

wx.config({
    debug: false,
    appId: 'wxdcb447934ddf8be6',
    timestamp: '<?php echo $timestamp ?>',
    nonceStr: '<?php echo $noncestr; ?>',
    signature: '<?php echo $sign ?>',
    jsApiList: [
        'getLocation',
    ]
});

wx.ready(function(){
	获取地理位置接口
	wx.getLocation({
	    type: 'wgs84', // 默认为wgs84的gps坐标，如果要返回直接给openLocation用的火星坐标，可传入'gcj02'
	    success: function (res) {
	        var latitude = res.latitude; // 纬度，浮点数，范围为90 ~ -90
	        var longitude = res.longitude; // 经度，浮点数，范围为180 ~ -180。
	        var speed = res.speed; // 速度，以米/每秒计
	        var accuracy = res.accuracy; // 位置精度
	    }
	    cancel: function (res) {
			alert('用户拒绝授权获取地理位置');
	    }
	});
})

```

| 名称        | 纬度   |  经度  |
| --------   | -----:  | :----:  |
| 电脑：    | 39.90403      | 116.407526      |
| 手机：    | 39.91266      | 116.43056       |
| 最大：    | 39.91369063   | 116.43096443    |
| 最小：    | 39.9116919    | 116.42883721    |
| 谷歌地图：| 39.9167063694 | 116.4377022448  |
| 百度地图：| 39.9225900000 | 116.4442280000  |
| 腾讯高德：| 39.9166952685 | 116.4376908955  |
| 图吧地图：| 39.9161414685 | 116.4267441555  |
| 谷歌地球：| 39.9153114685 | 116.4314741555  |

网络经纬的来自网络，感觉定位还可以。偏移大概在100m内。
靠近：北京市朝阳区雅宝路121号
参考：北京市朝阳区朝外街道雅宝里社区

[微信JS-SDK说明文档 地理位置](https://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1421141115&token=&lang=zh_CN "")

[测试地理位置](http://203.195.235.76/jssdk/#menu-location "")
