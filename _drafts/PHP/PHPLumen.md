title: PHP
date: 2016-01-19 14:11:20
description: 
categories:
- PHP
tags:
- PHP
toc: true
author:
comments:
original:
permalink: 
---
　　** ：**
<!-- more -->
Lumen - 为速度而生的 Laravel 框架


[接口文档：](http://doc.jingqubao.com/ "")
[Laravel中文网](http://www.golaravel.com/ "")
[Laravel 5.1 LTS 中文文档](http://laravel-china.org/docs/5.1 "")
[Laravel学院](http://laravelacademy.org/ "")
[Laravel速查表]( "https://cs.phphub.org/#db")
[]( "")
[]( "")



## 路由解析：
原理：/api/login =>
```
根路径：
D:\GitLab\php\jqb-api-user\bootstrap\app.php
$app->group(['namespace' => 'App\Http\Controllers'], function ($app) {
    require __DIR__.'/../app/Http/routes.php';
});
定义：api路由指向路径
$api->version('v1', [], function ($api) {
    require __DIR__.'/../app/Http/ApiRoutes.php';
});

添加API路由：
D:\GitLab\php\jqb-api-user\app\Http\ApiRoutes.php
路由：as路径名称，uses文件@方法名
$api->get('refresh_token', [
    'as'=>'refresh_token',
    'uses'=>'AuthController@refreshToken'
]);
/api/refresh_token
```
## 环境配置

```
lumen
root D:/GitLab/php/jqb-api-user/public;
root D:/GitLab/php/hpgds/public;
location / {
    try_files $uri $uri/ /index.php?$query_string;
}
```

```
http://www.jqb.com/index.php?app=w3g&mod=Weixin&act=ruanwen
tipuyou
root D:/GitLab/php/tipuyou;

location / {
    if ($request_uri ~* ~/api_v2) {
        rewrite ^(.*)/(.*?)/(.*?)/(.*?)$                         $1/index\.php?app=$2&mod=$3&act=$4 last;
    }
    set $flag "0";
    if ($request_uri ~* ^/testapi_v2) {
        set $flag "1";
    }
    if ($request_uri ~* ^/app) {
        set $flag "1";
    }
    if ($request_uri ~* ^/addons) {
        set $flag "1";
    }
    if ($request_uri ~* ^/data) {
        set $flag "1";
    }
    if ($flag = "0") {
        rewrite ^/(.*)/(.*)/(.*)/?$                      /index.php?app=$1&mod=$2&act=$3&$args last;
    }
    if (!-e $request_filename) {
        rewrite ^/code/([0-9]+)$ /index.php?app=api&mod=QrCode&act=check_code&id=$1 last;
        rewrite ^/code/([0-9]+)/(.*)$ /index.php?app=api&mod=QrCode&act=check_code&id=$1&from=$2 last;
    }
}
```
```
数据库配置
D:/hpgds/.env

123.57.136.104
remote
JQB2015test!!!
数据库docdb
```
安装composer依赖包（artisan生成秘钥）
D:/hpgds> php composer.phar install

更新秘钥
D:/hpgds> php artisan key:generate


##
git@123.57.136.104:jqb-api-user.git

lumen
laravel
bootstrap/app.php
app/Http/Controllers
ApiController

以前UserApi.class.php
OauthApi.class.php->AuthController.php






# lumen问题
## 1.\Validator::make
```
$validator = \Validator::make($this->request->all(), [
    'phone' => 'required|phone',
    'password' => 'required',
]);
```

# PHP

时间戳

time() 函数返回当前时间的 Unix 时间戳

date() 函数用于对日期或时间进行格式化
```
date("Y-m-d H:i:s", $shijian);

date("Y-m-d h:i:sa", $d);
2015-06-10 09:12:31am

<?php
// 假定今天是：March 10th, 2001, 5:16:18 pm
$today = date("F j, Y, g:i a");                 // March 10, 2001, 5:16 pm
$today = date("m.d.y");                         // 03.10.01
$today = date("j, n, Y");                       // 10, 3, 2001
$today = date("Ymd");                           // 20010310
$today = date('h-i-s, j-m-y, it is w Day z ');  // 05-16-17, 10-03-01, 1631 1618 6 Fripm01
$today = date('i	 is 	he jS day.');   // It is the 10th day.
$today = date("D M j G:i:s T Y");               // Sat Mar 10 15:16:08 MST 2001
$today = date('H:m:s m is mo h');     // 17:03:17 m is month
$today = date("H:i:s");                         // 17:16:17
?>
```
数据库的处理

$this->pageKeyList = array('id','title','scope','pic','brief','DOACTION');展示的内容
$this->pageTab[] = array('title' => '主题列表', 'tabHash' => 'list', 'url' => U('admin/Label/index'));tab导航




PHP获取当前文件路径,上层目录路径

取的現在檔案、目錄、上層目錄
於 test.php 內, 要做取得路徑、目錄等, 可見下述:
取得 路徑 + 檔名 (要取得 /var/www/project/test.php)
    * echo __FILE__;
取得 檔名 (要取得 test.php)
    * echo basename(__FILE__);
取得 不含附檔名的檔名 (要取得 test)
    * echo basename(__FILE__, '.php');
取得 到此目錄前的完整 PATH, 不含檔名 (要取得 /var/www/project)
    * echo dirname(__FILE__);
取得 到上層目錄前的完整 PATH (要取得 /var/www)
    * echo dirname(dirname(__FILE__));














## 基础

### 报警提示

| 名称 | 代码 |
| -----|:---- |
| 没有设置信息   |   FAILED_SET_INFO |
| 电话号码错误   |   WRONG_PHONE_NUMBER |
| 验证码错误   |   WRONG_QRCODE |
| 空信息或通过   |   EMPTY_UNAME_OR_PASS |
| 错误的帐户   |   WRONG_ACCOUNT |
| 没有修改过   |   FAILED_MODIFY_PASS |
| 没有注册   |   FAILED_REG |
| 没有注册或绑定电话   |   NOT_REG_OR_BIND_PHONE |
| 错误的信息或通过   |   WRONG_UNAME_OR_PASS |
| 平台的错误代码   |   WRONG_PLATFORM_CODE |
| 账户已存在  |   EXISTS_ACCOUNT |
| 用户名已存在   |   EXISTS_UNAME |
| 频繁请求验证码   |   FREQUENT_QRCODE_REQUEST |

class AuthErrorEnum extends ApiErrorEnum {
    const FAILED_SET_INFO = 122;
}
array('error'=>  AuthErrorEnum::FAILED_SET_INFO)

### 数据库

SSLECT
DB::delete("")

DB::


18:10:15

laravel
lumen

composer
18:13:11

composer.phar

composer.json同级目录
运行
php composer.phar install
18:39:26

https://www.processon.com/view/link/57ada741e4b06764c118a364

dhp

DB::select("")
DB::insert("")
DB::update("")
DB::delete("")

void DB::statement("")


DB::table('user')->where()->orWhere()->field()->groupBy()->skip()->take()->get()

whereBetween
whereNotBetween

whereIn
whereNotIn


model('user')->where()->field()->group()->limit()->findAll()



whereNot