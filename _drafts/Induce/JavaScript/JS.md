title: JavaScript修行
date: 2015-12-25 18:29:00
description:
categories:
- JavaScript
tags:
- JavaScript
toc: true
author:
comments:
original:
permalink:
---

　　**自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why
<!-- more -->
## 课程：
数据类型、表达式和运算符、语句、对象、数组、函数、this、闭包和作用域、OOP、正则与模式匹配。

JS是Ajax、JQuery、extjs等框架的基础。实现键盘、鼠标的响应，地图、网页游戏、WEB聊天等。

大家都知道，再啰嗦一遍，浏览器加载网页，加载到JS时，由于脚本比较多，而HTML代码还没有加载，这是页面会显示空白，脚本阻塞了HTML的加载，等到毫不容易加载完成了，有时候会发现这些网页元素没有样式，所以一个好的习惯是，CSS放在页头，JS放在页尾（先加载CSS，再加载HTML，再加载JS） 这样就能适时的将界面呈现给用户，减少页面空白的时间。

## 概述：

### 1、基础介绍：

一种广泛用于客户端Web开发的脚本语言。轻量级、解释型、面向对象的编程语言。
客户端JavaScript：脚本应包括在或由 HTML 文件中引用的代码，以通过浏览器解释。
>优点：更少的服务器交互、即时反馈给访问者、增加互动性、丰富的接口。

### 2、脚本语言：解释性语言 → 调用执行源码

往往不独立使用，要和HTML/jsp/php/asp/asp.net配合使用。
脚本语言有自己的变量、函数、控制语句（顺序、分支、循环）等。
解释语言与编译语言的区别：相比编译语言翻译成机器语言（字节码、二进制码）效率高。
>Java程序===.java → .class → jvm执行。JS脚本 → 浏览器（JS引擎解释）

### 3、引入方式：三种加载时间不同

```
1、头部：在<head>区域中，在页面被载入之前，脚本已经载入，准备好被调用。（放置：函数代码）
<script type="text/javascript"></script>

2、内部：在<body>区域中，在页面载入时，脚本被载入并立即执行。放置函数不会立即执行，只用调用时才执行，而且必须脚本成功加载完成之后，才能正确调用函数。
<script type="text/javascript"></script>

3、外部：在外部引用JavaScript，以.js为扩展名的文件中，在HTML页面中链接到这个脚本文件，不同的位置决定加载时机。
<script type="text/javascript" src="xxx.js"></script>

4、输出
JavaScript通常用来操作HTML，文档输出：
document.write("<p>this is my first JavaScript</p>");
```
### script元素

```
async：可选。立即下载脚本，但不应妨碍页面中的其他操作，比如下载其他资源或等待加载其他脚本。
只对外部脚本文件有效。

charset：可选。表示通过src 属性指定的代码的字符集。由于大多数浏览器会忽略它的值，因此这个属性很少有人用。

defer：可选。脚本可延迟到文档完全被解析和显示之后再执行。只对外部脚本文件有效。IE7 及更早版本对嵌入脚本也支持这个属性。

language：已废弃。原来用于表示编写代码使用的脚本语言（如JavaScript、JavaScript1.2或VBScript）。大多数浏览器会忽略这个属性，因此也没有必要再用了。

src：可选。表示包含要执行代码的外部文件。

type：可选。可以看成是language 的替代属性；表示编写代码使用的脚本语言的内容类型（也称为MIME 类型）。虽然text/javascript 和text/ecmascript 都已经不被推荐使用，但人们一直以来使用的都还是text/javascript。实际上，服务器在传送JavaScript 文件时使用的MIME 类型通常是application/x–javascript，但在type 中设置这个值却可能导致脚本被忽略。另外，在非IE浏览器中还可以使用以下值：application/javascript 和application/
```

## 二、语法结构

### 1、字符集

>JavaScript中的标识符：标识符是JavaScript中定义的符合，例如：变量名、函数名、数组名等。
标识符可以任意顺序的大小写字母、数字、下划线、美元组成，但是不能以数字开头，不能使用保留的关键词（ECMScript保留字）

>JavaScript的标识符不能使用的ECMScript 3保留字：（尽量避免使用）
abstract、boolean、byte、char、class、const、debugger、double、enum、export、extends、final、float、goto、implements、import、int、interface、long、native、package、private、protected、public、short、static、super、synchronized、throws、transient、volatile。

>Javascript预定全局变量和函数：argument、Array、Boolean、Dote、decodeURI、decodeURIComponent、encodeURI、encodeURIComponent、Error、eval、EvalError、Function、Infinity、isFinite、isNaN、JSON、Math、NaN、Number、Object、parseFloat、parseInt、RangeError、ReferenceError、RegExp、String、SyntaxError、TypeError、underfined、URIError。

>JavaScript严格区分大小写。每条功能执行语句的最后用分号（；）结束。
区分大小写：javascrip语言区分大小写，关键词、变量、函数名、标示符都必须采用一致的大小写形式。HTML不区分大小写。

按照惯例，ECMAScript 标识符采用驼峰大小写格式，也就是第一个字母小写，剩下的每个单词的首字母大写，例如：doSomethingImportant
### 2、注释：
语法：单行：//注释内容、多行：/* 注释内容 */

### 3、JavaScript转义字符：

| 类型 | Typeof返回字符串 |
| -----|:---- |
|  \b  | 退格符
|  \f  | 换页符
|  \n  | 换行符
|  \r  | 回车符
|  \t  | 横向跳格 (Ctrl-I)
|  \'  | 单引号
|  \\  | 反斜杠
|  \"  | 双引号
|  \o  | NUL字符
|  \v  | 垂直制表符
|  \t  | 水平制表符

### 4、分号分隔：
javascript使用分号（;），将语句分隔。分行书写，分号可以省略，同行书写，之间分号不可省。

### 5、数据类型：

JavaScript是弱类型数据语言，定义无需关注类型。数据类型分为：原始类型Primitive type、对象类型Object type。
注释：通过typeof可以看到变量的具体类型。 //JS是动态语言；window.alert(“vi是”+typeof vi);
原始类型：

数值Number
字符串String
布尔型Boolean

对象类型：是一组数据和功能的集合，

数组Array
var colors = new Array();
var colors = [];
colors.push('one','first');//推入两项
colors.pop();// 取得最后一项
colors.shift();//取得第一项
colors.concat("yellow", ["black", "brown"]);
concat()方法可以基于当前数组中的所有项创建一个新数组。

位置方法
indexOf();方法可返回某个指定的字符串值在字符串中首次出现的位置。
lastIndexOf();方法可返回一个指定的字符串值最后出现的位置，在一个字符串中的指定位置从后向前搜索。


#### sort(compare)方法:
```
function compare(value1, value2) {
	if (value1 < value2) {
		return 1;
	} else if (value1 > value2) {
		return -1;
	} else {
		return 0;
	}
}
var values = [0, 1, 5, 10, 15];
values.sort(compare);
alert(values); // 15,10,5,1,0
```
#### splice()方法:
```
这个方法恐怕要算是最强大的数组方法了，它有很多种用法。
splice()的主要用途是向数组的中部插入项，但使用这种方法的方式则有如下3 种。

 删除：可以删除任意数量的项，只需指定2 个参数：要删除的第一项的位置和要删除的项数。
例如，splice(0,2)会删除数组中的前两项。

 插入：可以向指定位置插入任意数量的项，只需提供3 个参数：起始位置、0（要删除的项数）
和要插入的项。如果要插入多个项，可以再传入第四、第五，以至任意多个项。例如，
splice(2,0,"red","green")会从当前数组的位置2 开始插入字符串"red"和"green"。

 替换：可以向指定位置插入任意数量的项，且同时删除任意数量的项，只需指定3 个参数：起
始位置、要删除的项数和要插入的任意数量的项。插入的项数不必与删除的项数相等。例如，
splice (2,1,"red","green")会删除当前数组位置2 的项，然后再从位置2 开始插入字符串
"red"和"green"。
```

函数Function
对象Object
特殊原始类型：

空null（var a=null；）
未定义undefine

数据类型判断：window.alert(tt);，报错 var aa; 弹出undefine

## 数据类型初探：

>1、数值number：
整型常量：10、8、16进制，
实型常量：12.23 5E7=5*107，
特殊数值：NaN不是数、Infinity无穷大、IsNaN不是数字、isFinite有穷大等，进行是否判断。

>2、布尔型Boolean：true真、false假。JS中非“0”的值，都是true，|0、’’、false、null、undefine、NaN等值。

>3、字符串String：使用双引号、单引号，”a”、’a’、’’，特殊字符：”a\”sk”

>5、运算符
按功能分类：
A=10，B=20

### 算数运算符：

运算符 | 描述 | 例子
-----|------|----
+	 | 两个运算数相加               |	A + B = 30
-	 | 第一个运算数减去第二个运算数               |	A - B = -10
*	 | 运算数相乘               |	A * B = 200
/	 | 分子除以分母               |	B / A = 2
%	 | 模数运算符，整除后的余数               |	B % A = 0
++	 | 增量运算符，整数值逐次加1               |	A++ = 11
--	 | 减量运算符，整数值逐次减1               |	--A=10，A=9

注意 : + 运算符不仅可以用于数字相加，还可以用于把文本值或字符串变量加起来（连接起来）。例如，"a" + 10 = “a10”。

### 比较运算符：

运算符 | 描述 | 例子
-----|------|----
==	 | 检查两个运算数的值是否相等，如果是，则结果为true	    | A == B 为false
!=	 | 检查两个运算数的值是否相等，如果不相等，则结果为true	    | A != B 为true
>	 | 检查左边运算数是否大于右边运算数，如果是，则结果为true	    | A > B 为false
	 | 检查左边运算数是否小于右边运算数，如果是，则结果为true	    | A
>=	 | 检查左边运算数是否大于或者等于右边运算数，如果是，则结果为true	    | A >= B 为false
	 | 检查左边运算数是否小于或者等于运算数，如果是，则结果为true	    | A

### 逻辑运算符：

运算符 | 描述 | 例子
-----|------|----
&&	 | 称为逻辑与运算符。如果两个运算数都非零，则结果为true。  |	A && B 为true
\\	 | 称为逻辑或运算符。如果两个运算数中任何一个非零，则结果为true。  |	A '\' B 为 true
!	 | 称为逻辑非运算符。用于改变运算数的逻辑状态。如果逻辑状态为true，则通过逻辑非运算符可以使逻辑状态变为false  |	!(A && B) 为false

### 位运算符：

运算符 | 描述 | 例子
-----|------|----
&	 | 称为按位与运算符。它对整型参数的每一个二进制位进行布尔与操作。	 | A & B = 2 .
\	 | 称为按位或运算符。它对整型参数的每一个二进制位进行布尔或操作。	 | A | B = 3.
^	 | 称为按位异或运算符。它对整型参数的每一个二进制位进行布尔异或操作。异或运算是指第一个参数或者第二个参数为true，并且不包括两个参数都为true的情况，则结果为true。|	(A ^ B) = 1.
~	 | 称为按位非运算符。它是一个单运算符，对运算数的所有二进制位进行取反操作。 | 	~B = -4 .
	 | 称为按位左移运算符。它把第一个运算数的所有二进制位向左移动第二个运算数指定的位数，而新的二进制位补0。将一个数向左移动一个二进制位相当于将该数乘以2，向左移动两个二进制位相当于将该数乘以4，以此类推。|	A
>>	 | 称为按位右移运算符。它把第一个运算数的所有二进制位向右移动第二个运算数指定的位数。为了保持运算结果的符号不变，左边二进制位补0或1取决于原参数的符号位。如果第一个运算数是正的，运算结果最高位补0；如果第一个运算数是负的，运算结果最高位补1。将一个数向右移动一位相当于将该数乘以2，向右移动两位相当于将该数乘以4，以此类推。|	A >> 1 = 1.
>>>	 | 称为0补最高位无符号右移运算符。这个运算符与>>运算符相像，除了位移后左边总是补0.	 | A >>> = 1.

### 赋值运算符：

运算符 | 描述 | 例子
-----|------|----
=	 | 简单赋值运算符，将右边运算数的值赋给左边运算数 |	C = A + B 将A+B的值赋给C
+=	 | 加等赋值运算符，将右边运算符与左边运算符相加并将运算结果赋给左边运算数 |	C += A 相当于 C = C + A
-=	 | 减等赋值运算符，将左边运算数减去右边运算数并将运算结果赋给左边运算数 |	C -= A 相当于C = C - A
*=	 | 乘等赋值运算符，将右边运算数乘以左边运算数并将运算结果赋给左边运算数 |	C *= A 相当于C = C * A
/=	 | 除等赋值运算符，将左边运算数除以右边运算数并将运算结果赋值给左边运算数 |	C /= A 相当于 C = C / A
%=	 | 模等赋值运算符，用两个运算数做取模运算并将运算结果赋值给左边运算数 |	C %= A 相当于 C = C % A

注意：同样的逻辑可以应用到位运算符，因此就有<<= , >>= , >>>= , &= , |= 以及 ^= 。
### 特殊运算符：delete obj.x

### 条件运算符：首先判断一个表达式是真或假，然后根据判断结果执行两个给定指令中的一个。（？：）如果条件为真 ? X值 : Y值。

### 逗号运算符：表达式结果取最后一个。var val=(1,2,3); →//val=3

### delete obj.x运算符：delete删除，删除后结果为undefined。

### in运算符：判断对象中是否含有。window.x=1; →‘x’ in window;→//true。

### new运算符：

### this运算符：全局的this指向window。this; →//window。var obj{func:function(){return this;}};obj.func();→//obj

### void运算符：

instanceof 判断的是对象的类型。
### typeof 运算符：判断数据类型，返回值为字符串。window.alert(“vi是”+typeof vi);


| 类型 | Typeof返回字符串 |
| -----|:---- |
| 数值   | "number" |
| 字符串 | "string" |
| 布尔   | "boolean" |
| 对象   | "object" |
| 函数   | "function" |
| 未定义 | "undefined" |
| 空     | "object" |

### 优先级：递减

| 类型 | Typeof返回字符串 |
| -----|:---- |
| 数组       | []
| 括号       | ( )
| 増減       | ++ --
| 负号       | -
| 取反       | ~
| NOT        | !
| 乘除余     | * / %
| 加减       | + -)
| 连接字符串 | +
| 位移       | << >> <<<
| 比较       | < <= >= >
| 比较       | == != === !==
| AND        | &
| XOR        | ^
| OR         | |
| 且         | &&
| 或         | ||
| 条件       | ? :
| 赋值       | =
| 扩展赋值   | +=等
| 逗号       | ,

按数量来分类：一元（+num）、二元（a+b）、三元运算符（C?a:b）

6、变量var
var a=b=1；定义的变量b为全局变量，var a=1,b=1；
语句：
	块block：（没有块级作用域）var定义变量


## 三大流程控制

顺序控制：对编程而言，不控制其流程就是顺序执行。

### if
#### 单分支
```
if(条件表达式){
case 常量1:
语句;
}
```

#### 双分支
```
if(条件表达式){
	语句;
}
else{
	语句;
}
```


#### 多分支
```
if(条件表达式1){
	语句;
}
else if(条件表达式2){
	语句;
}
else if(条件表达式3){
	语句;
}
```

### switch
#### 分支控制：
```
switch(表达式){
	case 常量1:
	语句;
	break;
	case 常量2:
	语句;
	break;
	defaule:
	语句;
	break;
}
```

```
强调：一且找到一个满足条件，进行执行后，直接结束整个。
案例：

var sex=window.prompt(“请输入性别”);
window.alert('');
document.write('');
document.writeIn(‘结果是’);
```

### 循环控制：

#### for循环

```
for(循环初值；循环条件；步长){
	语句；//循环体
}

for(var i=0; i<10; i++){
	document.writeIn(“!<br/>”);
}
```
#### for in循环

```
for(变量 in 对象){
	语句；
}

var x;
var mybooks=new Array();
mybooks[0]= '亮剑';
for(x in mybooks){
	console.log(mybooks[x]+ '<br />');
}
```

#### while循环

```
While(条件表达式){
	语句；//循环体
}

var i=0;
while(i<10){
	document.writeIn(“hello!<br/>”);
	i++;
}
```

#### do while循环

```
do{
	语句；//循环体
} While(条件表达式);

var i=0;
do{
	document.writeIn(“hello!<br/>”);
	i++;
} while(i<10);
```





八、函数
定义：为完成某一功能的程序指令（语句）的集合。


function函数名(参数列表){
语句；//函数（方法）
return 返回值；
}	function add(x1,x2){
var dx =x1+x2；//函数（方法）
return Math.sqrt(dx*dx)；
}

注意：1参数名不要带var，2返回值return，3输入值时，一定要进行强制转换。
输出内容：document.write(); 输出文本使用引号包裹。
输出引号内容：<script type=”text/javascropt”> document.write(“I Love JavaScript!”);</script>
输出变量内容：<script type=”text/javascropt”> var mystr=”hello world!”; document.write(mystr);</script>
输出多项内容：<script type=”text/javascropt”> var mystr=”hello”; document.write(mystr+” I Love JavaScript”);</script>
输出标签可用：<script type=”text/javascropt”> var mystr=”hello”; document.write(mystr+”<br>”); document.write(” JavaScript”);</script>
JS输出空格：查看WIKI中“JS如何输出空格”
警告：alert(字符串或变量);


## 扩展：

### 隐式转换：
#### 类型转换

```
var a = 'The answer is' + 42; => "The answer is 42"
var a = 42 + 'is the answer'; => "42 is the answer"

string - 0 转换为数字
num + '' 转换为字符串

var a = '32' + 1; => "321"
var a = '32' - 1; => 31

var a = 32 + ''; => "32"
var a = 32 - ''; => 32
```

### 比较运算符
如果两边的类型不同，则会进行类型转换在进行比较。
如果比较有数字，则会转换为数字

#### a == b 相等运算符（相等）

```
'1.23' == 1.23; => true
string == number; string => number

0 == false; => true
'0' == false; => true
boolean == ?; boolean => number(0/1)

new String('12') == 12; => true
object == number|string;  尝试对象转换基本类型

null == undefined; => true
NaN == NaN; => false
new Object() == new Object; => false
[1,2] == [1,2]; => false

如果对象与数字、字符串比较，则会将对象转换为原始值进行比较。toString();valueOf();
首先尝试使用valueOf();（函数用于返回指定对象的原始值），除了日期类，只使用toString()（返回该对象的字符串表示）;。
[2] == 2; => true

var a = [1,2];
console.log(a.toString());
console.log(a.valueOf());
console.log(a.valueOf().toString());
```

是否改变原有类型
```
var a = '2';
if(a == 2){console.log(typeof a);}
if(2 == a){console.log(typeof a);}
```

#### a === b 严格相等运算符（恒等）

```
比较两边，类型不同，直接返回false。类型相同，比较值。

null === null; => true
undefined === undefined; => true
NaN === NaN; => false
x !== x;（可以判断是否为NaN）

对象进行比较
如果两个引用值指向同一个对象、数组、函数，则它们是相等的。
new Object() === new Object; => false
[1,2] === [1,2]; => false
```

改变了原来的值
```
var x = 1;
var obj = {
	valueOf: function(){
		x = 2;
		return 0;
	}
}
console.log(obj == 0, x);

=> true, 2
```
[比较运算符](http://jsfiddle.net/26Lf0a0L/ "")


### 类型检测：

typeof

instanceof
Object.prototype.toString
constructor
duck type