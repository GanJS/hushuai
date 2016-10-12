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

php初学

代码格式：
<?php
//内容
?>

php注释：
// 单行注释
/*  */

输出函数：
echo()
print()
printf()
sprintf()

变量赋值：
传值赋值、引用赋值

作用域：
默认为局部变量，未申明及可用。PHP作用域是块分割的。
局部变量、全局变量
局部变量是声明在某一函数体内的变量，该变量的作用范围仅限于其所在的函数体的内部。如果在该函数体的外部引用这个变量，则系统将会认为引用的是另外一个变量。
未定义及可以使用=>局部变量。

全局变量：声明为全局变量，
global $a;
声明与执行分开；

静态变量：临时变量，函数结束后自动清除。
static $a;

可变变量：变量名称可以变化的命名方式。
$a;$a = b;
$$a; => $b;

PHP 预定义变量

| 变量 | 作用 |
| -----|:---- |
| $GLOBALS[]  | 储存当前脚本中的所有全局变量，其KEY 为变量名，VALUE 为变量值   |
| $_SERVER[]  | 当前WEB 服务器变量数组   |
| $_GET[]     | 存储以GET 方法提交表单中的数据   |
| $_POST[]    | 存储以POST 方法提交表单中的数据   |
| $_COOKIE[]  | 取得或设置用户浏览器Cookies 中存储的变量数组   |
| $_FILES[]   | 存储上传文件提交到当前脚本的数据   |
| $_ENV[]     | 存储当前WEB 环境变量   |
| $_REQUEST[] | 储提交表单中所有请求数组，其中包括$_GET、$_POST、$_COOKIE 和$_SESSION 中的所有内容   |
| $_SESSION[] | 存储当前脚本的会话变量数组   |

$a;global $a;var_dump($GLOBALS['a']);

## 四、变量的数据类型
标量类型（四种）：整型（int，integer）浮点型（float，double，real）布尔型（bool，boolean）字符串（string）
复合类型（两种）：数组（array）对象（object）特殊类型（两种）：资源（resource）空值（NULL）

### 1、整型（integer）
默认输出十进制

### 2、浮点型（float）

### 3、布尔型（boolean）
当布尔值为“true”时，输出为1，当布尔值为“false”时，输出为空。

### 4、字符串（string）
使用单引号（'）定义、使用双引号（"）定义和使用定界符（<<<）,使用“转译字符”转译

### 5、数组（array）
$network = array("how","are","you");
$network = array(1=>"how",2=>are,'three'=>"you");
echo $network[2];
echo $network[three];

### 6、对象（object）

```
class 类名 {
	类里包含的内容;
}

<?php
class Book {
function getBookName($book_name){
return $book_name;
}
}
$book1 = new Book(); //实例化一个Book类的对象book1
echo $book1->getBookName("PHP")."<br>";
$book2 = new Book(); //实例化一个Book类的对象book2
echo $book2->getBookName("JSP");
?>
```

### 7、资源（resource）
资源是PHP 提供的一种特殊数据类型，该数据类型用于表示一个PHP 的外部资源，比如一个数据库的访问操作，或者一个网络流的处理等。

### 8、空值（NULL）
NULL 是PHP 4 开始引入的一个特殊的数据类型，这种数据类型只有一个值NULL
unset($c); //使用unset()函数处理后，$c的值为NULL
unset($network[0]);

## 五、变量类型的转换

### 1、自动类型转换
如果所有运算数都是数字，则将选取占用字节最长的一种运算数的数据类型作为基准数据类型；如果运算数为字符串，则将该字符串转型为数字然后再进行求值运算。字符串转换为数字的规定为如果字符串以数字开头，则只取数字部分而去除数字后面部分，根据数字部分构成决定转型为整型数据还是浮点型数据；如果字符串以字母开头，则直接将字符串转换为0。
字符串拼接则使用“.”
$a = 5/2; => 2.5
$b = 2 + "3.14"; => 5.14
$c = "abc"+ 1; => 1
$d = "abc".1; => abc1

### 2、强制类型转换

转换格式 | 转换结果 | 实现方式
-----|------|----
(int),(integer)          | 将其他数据类型 , 强制转换为整型      |$a = "3"; $b = (int)$a;    //也可写为$b = (integer)$a;
(bool),(boolean)         | 将其他数据类型 , 强制转换为布尔型    |$a = "3"; $b = (bool)$a;   //也可写为$b = (boolean)$a;
(float),(double),(real)  | 将其他数据类型 , 强制转换为浮点型    |$a = "3"; $b = (float)$a;  $c = (double)$a;  $d = (real)$a;
(string)                 | 将其他数据类型 , 强制转换为字符串    |$a = 3;   $b = (string)$a;
(array)                  | 将其他数据类型 , 强制转换为数组      |$a = "3"; $b = (array)$a;
(object)                 | 将其他数据类型 , 强制转换为对象      |$a = "3"; $b = (object)$a;






var_dump()
void var_dump ( mixed expression [, mixed expression [, ...]] )
var_dump()方法是判断一个变量的类型与长度,并输出变量的数值,如果变量有值输的是变量的值并回返数据类型.
[var_dump()函数](http://www.php100.com/html/php/hanshu/2013/0905/4344.html "")

[php 操作数组 （合并，拆分，追加，查找，删除等）](http://justcoding.iteye.com/blog/1181962/ "")

sort() - 以升序对数组排序
rsort() - 以降序对数组排序
asort() - 根据值，以升序对关联数组进行排序
ksort() - 根据键，以升序对关联数组进行排序
arsort() - 根据值，以降序对关联数组进行排序
krsort() - 根据键，以降序对关联数组进行排序
usort

array_merge_recursive
array_merge
array_combine
array_slice
array_splice
array_intersect
array_intersect_assoc
array_diff
array_diff_assoc

key
current
each

in_array
array_key_exists
array_search
array_keys
array_values
array_unshift
array_push
array_pop
array_shift

## php取整的几种方式

```
floor()(舍去小数部分，只取整数)
	echo floor(9.999); // 9
ceil()(进一取整，只要有小数部分，直接加一)
	echo ceil(4.1);    // 5
round()(四舍五入取整)
	echo round(3.4);         // 3
	echo round(3.5);         // 4
	echo round(3.6);         // 4
	echo round(3.6, 0);      // 4
	echo round(1.95583, 2);  // 1.96
	echo round(1241757, -3); // 1242000
	echo round(5.045, 2);    // 5.05
	echo round(5.055, 2);    // 5.06
```

## ThinkPHP 数据查询

连贯操作 | 作用 | 支持的参数类型
-----|------|----
where	    | 用于查询或者更新条件的定义             | 字符串、数组和对象
table	    | 用于定义要操作的数据表名称             | 字符串和数组
alias	    | 用于给当前数据表定义别名               | 字符串
data	    | 用于新增或者更新数据之前的数据对象赋值 | 数组和对象
field	    | 用于定义要查询的字段（支持字段排除）   | 字符串和数组
order	    | 用于对结果排序                         | 字符串和数组
limit	    | 用于限制查询结果数量                   | 字符串和数字
page	    | 用于查询分页（内部会转换成limit）      | 字符串和数字
group	    | 用于对查询的group支持                  | 字符串
having	    | 用于对查询的having支持                 | 字符串
join*	    | 用于对查询的join支持                   | 字符串和数组
union*   	| 用于对查询的union支持                  | 字符串、数组和对象
distinct	| 用于查询的distinct支持                 | 布尔值
lock	    | 用于数据库的锁机制                     | 布尔值
cache	    | 用于查询缓存                           | 支持多个参数
relation	| 用于关联查询（需要关联模型支持）       | 字符串

limit('1,2')设置起始位置，数量。


### where用于查询或者更新条件的定义
where('city="成都"')
where(array('city'=>'成都'))
where('status=1 and id=1')

where(array('id'=>array('in',$labelids)))

'eq' => string '=' (length=1)
'neq' => string '!=' (length=2)
'gt' => string '>' (length=1)
'egt' => string '>=' (length=2)
'lt' => string '<' (length=1)
'elt' => string '<=' (length=2)
'notlike' => string 'NOT LIKE' (length=8)
'like' => string 'LIKE' (length=4)


### field
field('name,sex,wechat,weibo,city,tel_num,ctime')
field(array('city','name','sex','wechat','weibo','tel_num','ctime'))
field(array('city','name','sex','wechat','weibo','tel_num','ctime'))


### order(asc/desc)
用法：order($order)

order('name asc')
order('name desc')

[6.12 连贯操作](http://doc.thinkphp.cn/manual/continuous_operation.html "")

$listData = model('TravelExp')->field('name,sex,wechat,weibo,city,tel_num,ctime')->findPage($this->pageSize);

### model
('表名')，调用数据库表名

### findPage(20);


# 问题：

```
$a = '1地点' + 1.23;
echo a;
$b = (object)$a;
var_dump($b);

object(stdClass)[25]
public 'scalar' => float 2.23
```


### $cars[]
给数组进行赋值，执行默认添加新的数据
$cars=array("Volvo","BMW","SAAB");
$cars[] = 1;
var_dump($cars);

### 关于存储数字的长度
通过memory_get_usage，获取php消耗的内存




// var_dump(model('Comment')->getLastSql());exit;
// model('Comment')->select





query("SELECT audio_category_id,title FROM ts_audio_category ");
