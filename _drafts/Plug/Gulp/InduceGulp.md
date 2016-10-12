title: Gulp前端构建工具
date: 2016-04-02 14:11:20
description: 
categories:
- Plug
tags:
- Gulp
toc: true
author:
comments:
original:
permalink: 
---

　　**Gulp前端自动化：**Gulp的高度集成化开发环境，释放了前端开发中大量时间，如css压缩、js压缩、错误检查、合并js、压缩图片、压缩html、模块构造等，只要你能想到的基本都可以通过Gulp插件去实现。

<!-- more -->

## 前端自动化的目的

在一个项目过程中，重复而枯燥的工作太多了……绳命就这样浪费了。
我们需要一个自动化的工作流程，让我们更专注于coding，而不是coding外的繁琐工作。于是Gulp应运而生。可以想像，如果在node环境下，一行命令搞定一个场景，So Cool…

gulp是基于Nodejs的自动任务运行器， 她能自动化地完成 javascript/coffee/sass/less/html/image/css 等文件的的测试、检查、合并、压缩、格式化、浏览器自动刷新、部署文件生成，并监听文件在改动后重复指定的这些步骤。在实现上，她借鉴了<b>Unix操作系统的管道（pipe）</b>思想，前一级的输出，直接变成后一级的输入，使得在操作上非常简单。通过本文，我们将学习如何使用Gulp来改变开发流程，从而使开发更加快速高效。
gulp 和 grunt 非常类似，但相比于 grunt 的频繁 IO 操作，gulp 的流操作，能更快地更便捷地完成构建工作。
本示例以gulp-less为例（将less编译成css的gulp插件）展示gulp的常规用法，只要我们学会使用一个gulp插件后，其他插件就差看看其帮助文档了。让我们一起来学习gulp吧！ ^_^

### 功能：

>1. 版本控制
2. 检查JS
3. 图片合并
4. 压缩CSS
5. 压缩JS
6. 编译SASS

### 目前最知名的构建工具： Gulp、Grunt、NPM + Webpack；

```Text
grunt是前端工程化的先驱

gulp更自然基于流的方式连接任务

Webpack最年轻，擅长用于依赖管理，配置稍较复杂

推荐使用Gulp，Gulp基于nodejs中stream，效率更好语法更自然,不需要编写复杂的配置文件
```

## 安装前准备：

在学习前，先谈谈大致使用gulp的步骤，给读者以初步的认识。首先当然是安装nodejs，通过nodejs的npm全局安装和项目安装gulp，其次在项目里安装所需要的gulp插件，然后新建gulp的配置文件gulpfile.js并写好配置信息（定义gulp任务），最后通过命令提示符运行gulp任务即可。
安装nodejs -> 全局安装gulp -> 项目安装gulp以及gulp插件 -> 配置gulpfile.js -> 运行任务

### node
为了确保依赖环境正确，我们先执行几个简单的命令检查。

```
luuman@luuman-PC MINGW64 ~
$ node -v

v5.3.0

Node是一个基于Chrome JavaScript V8引擎建立的一个解释器
检测Node是否已经安装，如果正确安装的话你会看到所安装的Node的版本号
```
### npm
接下来看看npm，它是 node 的包管理工具，可以利用它安装 gulp 所需的包

```
luuman@luuman-PC MINGW64 ~
$ npm -v

3.3.12

这同样能得到npm的版本号，装 Node 时已经自动安装了npm
```

### npm Node依赖包

1. 说明：npm（node package manager）nodejs的包管理器，用于node插件管理（包括安装、卸载、管理依赖等）；
2. 使用npm安装插件：命令提示符执行```npm install <name> [-g] [--save-dev]；```
    1、<name>：node插件名称。例：```npm install gulp-less --save-dev```
    2、-g：全局安装。将会安装在C:\Users\Administrator\AppData\Roaming\npm，并且写入系统环境变量；  非全局安装：将会安装在当前定位目录；  全局安装可以通过命令行在任何地方调用它，本地安装将安装在定位目录的node_modules文件夹下，通过require()调用；
    3、--save：将保存配置信息至package.json（package.json是nodejs项目配置文件）；
    4、-dev：保存至package.json的devDependencies节点，不指定-dev将保存至dependencies节点；一般保存在dependencies的像这些express/ejs/body-parser等等。
    5、为什么要保存至package.json？因为node插件包相对来说非常庞大，所以不加入版本管理，将配置信息写入package.json并将其加入版本管理，其他开发者对应下载即可（命令提示符执行npm install，则会根据package.json下载所有需要的包，npm install --production只下载dependencies节点的包）。

3. 使用npm卸载插件：```npm uninstall <name> [-g] [--save-dev]```  PS：不要直接删除本地插件包
    1、删除全部插件：```npm uninstall gulp-less gulp-uglify gulp-concat``` ……???太麻烦
    2、借助rimraf：```npm install rimraf -g``` 用法：rimraf node_modules
4. 使用npm更新插件：```npm update <name> [-g] [--save-dev]```
    更新全部插件：```npm update [--save-dev]```
5. 查看npm帮助：```npm help```
6. 当前目录已安装插件：```npm list```

PS：npm安装插件过程：从http://registry.npmjs.org下载对应的插件包（该网站服务器位于国外，所以经常下载缓慢或出现异常），解决办法往下看↓↓↓↓↓↓。

### 选装cnpm
因为npm安装插件是从国外服务器下载，受网络影响大，可能出现异常，如果npm的服务器在中国就好了，所以我们乐于分享的淘宝团队干了这事。
来自官网：“这是一个完整 npmjs.org 镜像，你可以用此代替官方版本(只读)，同步频率目前为 10分钟 一次以保证尽量与官方服务同步。”；

[官方网址：](http://npm.taobao.org "")
安装：命令提示符执行```npm install cnpm -g --registry=https://registry.npm.taobao.org```
注意：安装完后最好查看其版本号cnpm -v或关闭命令提示符重新打开，安装完直接使用有可能会出现错误；
注：cnpm跟npm用法完全一致，只是在执行命令时将npm改为cnpm（以下操作将以cnpm代替npm）。
```
luuman@luuman-PC MINGW64 /l/自动化
$ npm install cnpm -g --registry=https://registry.npm.taobao.org
npm WARN deprecated has-color@0.1.7: Renamed to supports-color. If you're usingchalk, upgrade to the latest version. https://github.com/chalk/supports-color
C:\Users\luuman\AppData\Roaming\npm\cnpm -> C:\Users\luuman\AppData\Roaming\npm\node_modules\cnpm\bin\cnpm
C:\Users\luuman\AppData\Roaming\npm\cnpm-sync -> C:\Users\luuman\AppData\Roaming\npm\node_modules\cnpm\bin\cnpm-sync
C:\Users\luuman\AppData\Roaming\npm\cnpm-user -> C:\Users\luuman\AppData\Roaming\npm\node_modules\cnpm\bin\cnpm-user
C:\Users\luuman\AppData\Roaming\npm\cnpm-check -> C:\Users\luuman\AppData\Roaming\npm\node_modules\cnpm\bin\cnpm-check
C:\Users\luuman\AppData\Roaming\npm\cnpm-web -> C:\Users\luuman\AppData\Roaming\npm\node_modules\cnpm\bin\cnpm-web
C:\Users\luuman\AppData\Roaming\npm\cnpm-doc -> C:\Users\luuman\AppData\Roaming\npm\node_modules\cnpm\bin\cnpm-doc
C:\Users\luuman\AppData\Roaming\npm\cnpm-search -> C:\Users\luuman\AppData\Roaming\npm\node_modules\cnpm\bin\cnpm-search
C:\Users\luuman\AppData\Roaming\npm
├── abbrev@1.0.9
├── aproba@1.0.4
├─┬ cnpm@4.3.1
│ ├── auto-correct@1.0.0
│ ├── bagpipe@0.3.5
```
### 全局安装gulp
说明：全局安装gulp目的是为了通过她执行gulp任务；
安装：命令提示符执行```cnpm install gulp -g```
查看是否正确安装：命令提示符执行gulp -v，出现版本号即为正确安装。
```
luuman@luuman-PC MINGW64 /l/自动化
$ cnpm -v
4.3.1
```

### 开始全局安装Gulp

```
luuman@luuman-PC MINGW64 ~
$ cnpm install -g gulp

npm WARN deprecated graceful-fs@3.0.8: graceful-fs version 3 and before will fail on newer node releases. Please update to graceful-fs@^4.0.0 as soon as possible.
npm WARN deprecated lodash@1.0.2: lodash@<3.0.0 is no longer maintained. Upgrade to lodash@^4.0.0.
npm WARN deprecated graceful-fs@1.2.3: graceful-fs version 3 and before will fail on newer node releases. Please update to graceful-fs@^4.0.0 as soon as possible.
C:\Users\luuman\AppData\Roaming\npm\gulp -> C:\Users\luuman\AppData\Roaming\npm\node_modules\gulp\bin\gulp.js
C:\Users\luuman\AppData\Roaming\npm
└─┬ gulp@3.9.1
  └─┬ gulp-util@3.0.7
    ├─┬ dateformat@1.0.12
    │ └─┬ meow@3.7.0
    │   └─┬ normalize-package-data@2.3.5
    │     └─┬ validate-npm-package-license@3.0.1
    │       └─┬ spdx-correct@1.0.2
    │         └── spdx-license-ids@1.2.1
    └─┬ fancy-log@1.2.0
      └── time-stamp@1.0.1
```

```
luuman@luuman-PC MINGW64 /l/Github
$ gulp -v

[18:39:18] CLI version 3.9.1

得到gulp的版本号，确认安装成功
```

## 创建工程

### 演示项目目录结构

```
└─┬ src — 源文件:
	├──images
	├──scripts
	├──styles
├──build — 编译后文件输出到的生产文件夹:
├──images
├──scripts
├──styles


TestProject     (项目名称)
|–.git               通过git进行版本控制,项目自动生成这个文件
|–node_modules       组件包目录
|–dist               发布环境（编译自动生成的）
    |–css                 样式文件(style.css style.min.css)
    |–images              图片文件(压缩图片\合并后的图片)
    |–js                  js文件(main.js main.min.js)
    |–index.html          静态页面文件(压缩html)

|–src                开发环境
    |–sass                sass文件
    |–images              图片文件
    |–js                  js文件
    |–index.html          静态文件
|–gulpfile.js        gulp配置文件
|–package.json       依赖模块json文件,在项目目录下npm install会安装项目所有的依赖模块，简化项目的安装程序
```

### 创建package.json

我们先使用npm init来创建类似Nuget package的package.config一样的文件，这样我们就知道项目依赖哪些插件，而且我们不需要把插件提交到代码库，其它程序员只需要使用 npm install 就可以安装所有配置的插件

```
$ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg> --save` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
name: (test) test                  //名称
version: (1.0.0) 1.0.0             //版本
description: test description      //描述
entry point: (index.js)            //
test command:                      //测试代码
git repository:                    //Git版本库
keywords:                          //关键词
author: luuman                     //作者
license: (ISC)                     //协议
About to write to F:\Gulp\test\package.json:

{
  "name": "test",
  "version": "1.0.0",
  "description": "test description",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "luuman",
  "license": "ISC"
}

Is this ok? (yes)

```

### 安装插件，加到项目依赖package.json中

npm install gulp --save-dev //将具体的gulp功能插件局部安装项目下

```
$ npm install gulp --save-dev

npm WARN deprecated graceful-fs@3.0.8: graceful-fs version 3 and before will fail on newer node releases. Please update to graceful-fs@^4.0.0 as soon as possible.
npm WARN deprecated lodash@1.0.2: lodash@<3.0.0 is no longer maintained. Upgrade to lodash@^4.0.0.
npm WARN deprecated graceful-fs@1.2.3: graceful-fs version 3 and before will fail on newer node releases. Please update to graceful-fs@^4.0.0 as soon as possible.
F:\Gulp\new
└─┬ gulp@3.9.1
```

npm install gulp-sass --save-dev //将具体的gulp功能插件局部安装项目下

```
$ npm install gulp-sass --save-dev
```

### 安装gulp功能插件依赖包

npm install gulp-jshint gulp-sass gulp-concat gulp-uglify gulp-rename --save-dev
gulp功能模块的文件会放在项目所在的目录的./node_modules 下,并在package.json中添加插件名称。


### 引入插件包

```
npm install

当package.json中已经有提示插件依赖包，node.js将会直接下载所有依赖插件包。
```

### 简单的功能：

| 插件 | 功能 |
|  ---- | ---- |
| gulp-imagemin:   | 压缩图片
| gulp-ruby-sass:  | 支持sass，安装此版本需要安装ruby
| gulp-minify-css: | 压缩css
| gulp-jshint:     | 检查js
| gulp-uglify:     | 压缩js
| gulp-concat:     | 合并文件
| gulp-rename:     | 重命名文件
| gulp-htmlmin:    | 压缩html
| gulp-clean:      | 清空文件夹
| gulp-livereload: | 服务器控制客户端同步刷新（需配合chrome插件LiveReload及tiny-lr）

#### gulp-jshint

```
luuman@luuman-PC MINGW64 /f/Gulp/new
$ npm install gulp-jshint --save-dev

F:\Gulp\new
├─┬ gulp@3.9.1
├─┬ gulp-jshint@2.0.0

npm WARN EPEERINVALID gulp-jshint@2.0.0 requires a peer of jshint@2.x but none was installed.
```

### 补充：的前端开发软件环境

```text
Node.Js、NPM、Ruby、Java        基础环境
Sublime + 插件                  用于编写前端代码
Chrome、Firefox + Firebug       浏览器
Internet Explorer               进行兼容测试和预览页面UI、动画效果和交互功能
Node.js+Gulp                    进行前端自动化构建、JS语法验证、CSS压缩，图片压缩等；
Koala                           实时编译Less、Sass、Compass、CoffeeScript;
Github                          存储自己的代码库 、git或SVN用于版本控制和团队Code Review
Tomcat、DedeAMPZ、MAMP          进行简单运行环境演示
Photoshop CC 切图 + Sprites     合并小图标
XMind                           画出清晰的工作或业务逻辑思维图
```

```
新建gulpfile.js 配置文件放在项目根目录下

演示项目目录结构
testProject     (项目名称)
|–.git            通过git进行版本控制,项目自动生成这个文件
|–node_modules    组件包目录
|–dist            **发布环境**（编译自动生成的）
    |–css         样式文件(style.css style.min.css)
    |–images  图片文件(压缩图片\合并后的图片)
    |–js      js文件(main.js main.min.js)
    |–index.html  静态页面文件(压缩html)
|–src             **开发环境**
    |–sass                sass文件
    |–images              图片文件
    |–js                  js文件
    |–index.html      静态文件
|–gulpfile.js             gulp配置文件
|–package.json            依赖模块json文件,在项目目录下npm install会安装项目所有的依赖模块，简化项目的安装程序
```

```
现在，项目文件夹都建好，组件也安装完毕了，我们需要编写gulpfile.js文件以指定gulp需要为我们完成什么任务。

gulpfile.js内容如下：

// 引入gulp
var gulp = require('gulp');

// 引入组件
var jshint = require('gulp-jshint');//检查js
var sass   = require('gulp-sass');  //编译Sass
var concat = require('gulp-concat');//合并
var uglify = require('gulp-uglify');//uglify 组件（用于压缩 JS）
var rename = require('gulp-rename');//重命名

// 检查js脚本的任务
gulp.task('lint', function() {
    gulp.src('./js/*.js') //可配置你需要检查脚本的具体名字。
        .pipe(jshint())
        .pipe(jshint.reporter('default'));
});

// 编译Sass
gulp.task('sass', function() {
    gulp.src('./scss/*.scss')
        .pipe(sass())
        .pipe(gulp.dest('./css'));//dest()写入文件
});

// 合并，压缩js文件
// 找到 js/ 目录下的所有 js 文件，压缩，重命名，最后将处理完成的js存放在 dist/js/ 目录下
gulp.task('scripts', function() {
    gulp.src('./js/*.js')
        .pipe(concat('all.js'))
        .pipe(gulp.dest('./dist'))
        .pipe(rename('all.min.js'))
        .pipe(uglify())
        .pipe(gulp.dest('./dist'));

        console.log('gulp task is done');//自定义提醒信息
});
```

.... // 其他任务类似

// 定义默认任务,执行gulp会自动执行的任务
gulp.task('default', function(){
    gulp.run('lint', 'sass', 'scripts');

    // 监听js文件变化，当文件发生变化后会自动执行任务
    gulp.watch('./js/*.js', function(){
        gulp.run('lint','scripts');
    });
});

```
现在，回到命令行窗口，可以直接运行gulp任务了。

gulp

这将执行定义的default任务，就和以下的命令式同一个意思

gulp default

当然，我们可以运行在gulpfile.js中定义的任意任务，比如，现在单独运行sass任务：

gulp sass
```

### 编译会显示Finished,如果你的JS有什么不好的地方它会提醒，避免一些不必要的错误，十分贴心

```
常见提醒：
1.禁止在同一行声明多个变量。
2.请使用 ===/!==来比较true/false或者数值
3.使用对象字面量替代new Array这种形式
4.不要使用全局函数。
5.Switch语句必须带有default分支
6.函数不应该有时候有返回值，有时候没有返回值。
7.For循环必须使用大括号
8.If语句必须使用大括号
9.for-in循环中的变量 应该使用var关键字明确限定作用域，从而避免作用域污染。
```
### gulp的插件数量很多，后面还可以根据自己的需要进行添加任务

```
常用的gulp插件参考
gulp-imagemin:      压缩图片
gulp-ruby-sass:     支持sass，安装此版本需要安装ruby
gulp-minify-css:    压缩css
gulp-jshint:        检查js
gulp-uglify:        压缩js
gulp-concat:        合并文件
gulp-rename:        重命名文件
gulp-htmlmin:       压缩html
gulp-clean:         清空文件夹
gulp-livereload:    服务器控制客户端同步刷新（需配合chrome插件LiveReload及tiny-lr）
```

### gulp-livereload

npm install gulp gulp-livereload --save-dev
```
var gulp = require('gulp'),
    livereload = require('gulp-livereload');

gulp.task('watch', function () {    // 这里的watch，是自定义的，写成live或者别的也行
    var server = livereload();
    
    // app/**/*.*的意思是 app文件夹下的 任何文件夹 的 任何文件
    gulp.watch('app/**/*.*', function (file) {
        server.changed(file.path);
    });
});
```

命令行下运行
```
gulp watch
```
## 前端自动化的目的
[Gulp新手入门教程](http://www.w3ctrain.com/2015/12/22/gulp-for-beginners/ "")
[基于Gulp的前端自动化工程搭建](http://mrzhang123.github.io/2016/09/07/gulpUse/ "")
Gulp 自动化你的前端
http://www.sheyilin.cn/2016/02/gulp_introduce/
[gulp官方网址：](http://gulpjs.com "")
[gulp插件地址：](http://gulpjs.com/plugins "")
[gulp 官方API：](https://github.com/gulpjs/gulp/blob/master/docs/API.md "")
[gulp 中文API：](http://www.ydcss.com/archives/424 "")
[Gruntjs](http://gruntjs.com "The JavaScript Task Runner")
[Grunt安装及配合组件构建前端开发一体化](http://www.dbpoo.com/getting-started-with-grunt/ "")
[grunt前端打包——css篇](http://www.php100.com/html/it/qianduan/2015/0115/8377.html: "")

[SourceTree](http: "")
[SourceTree](http: "")
[UED团队前端自动化构建环境的搭建](http://markyun.github.io/2015/The-front-end-code-build-automated-build-environment/ "")
[前端构建大法 Gulp 系列 (四)：gulp实战](http://www.cnblogs.com/cnblogsfans/p/5104450.html "")


自动刷新
建议使用browser-sync
[[gulp入门]gulp-connect浏览器自动刷新](http://www.cnblogs.com/anywing/p/5311061.html "")
[Gulp.js-livereload 不用F5了，实时自动刷新页面来开发](http://cnodejs.org/topic/53427d16dc556e3b3901861e "")

```
var gulp = require('gulp'),
    livereload = require('gulp-livereload');

// 这里的f5，是自定义的，写成live或者别的也行
gulp.task('f5',function(){
    var server = livereload();
    // app/**/*.*的意思是 app文件夹下的 任何文件夹 的 任何文件
    gulp.watch('app/**/*.*',function(file){
        server.changed(file.path);
    });
})
```
[Gulp构建前端自动化工作流之：入门介绍及LiveReload的使用](http://www.tuicool.com/articles/qyiaInI "")
```
var livereload = require('gulp-livereload'), 
  webserver = require('gulp-webserver'); 

gulp.task('webserver', function() {
  gulp.src( './' ) // 服务器目录（./代表根目录）
  .pipe(webserver({ // 运行gulp-webserver
    livereload: true, // 启用LiveReload
    open: true // 服务器启动时自动打开网页
  }));
});

gulp.task('watch',function(){
  gulp.watch( '*.html', ['html']) // 监听根目录下所有.html文件
});

gulp.task('default',['webserver','watch']);

var gulp = require('gulp'),
// 网页自动刷新（服务器控制客户端同步刷新）
    livereload = require('gulp-livereload'),
// 本地服务器
    webserver = require('gulp-webserver')

// 注册任务
gulp.task('webserver',function(){
    gulp.src('./')
    .pipe(webserver({
        livereload: true,
        open: true,
    }))
})
// 监听f5任务
gulp.task('f5',function(){
    gulp.watch('*.html',['html'])
})

// web任务
gulp.task('web',['webserver','f5'])
```



### 报错：

```
$ gulp build
fs.js:856
  return binding.readdir(pathModule._makeLong(path));
                 ^
Error: ENOENT: no such file or directory, scandir 'L:\自动化\new\node_modules\.3.8.0@node-sass\vendor'
    at Error (native)
    at Object.fs.readdirSync (fs.js:856:18)
    at Object.getInstalledBinaries (L:\自动化\new\node_modules\.3.8.0@node-sass\lib\extensions.js:119:13)
    at foundBinariesList (L:\自动化\new\node_modules\.3.8.0@node-sass\lib\errors.js:20:15)
    at foundBinaries (L:\自动化\new\node_modules\.3.8.0@node-sass\lib\errors.js:15:5)
    at Object.module.exports.missingBinary (L:\自动化\new\node_modules\.3.8.0@node-sass\lib\errors.js:45:5)
    at Object.<anonymous> (L:\自动化\new\node_modules\.3.8.0@node-sass\lib\index.js:15:28)
    at Module._compile (module.js:398:26)
    at Object.Module._extensions..js (module.js:405:10)
    at Module.load (module.js:344:32)


解决方案是执行以下方法：
luuman@luuman-PC MINGW64 /l/自动化/new
$ cnpm rebuild node-sass

> node-sass@3.8.0 install L:\自动化\new\node_modules\gulp-sass\node_modules\node-sass
> node scripts/install.js

Binary downloaded and installed at L:\自动化\new\node_modules\.3.8.0@node-sass\vendor\win32-x64-47\binding.node

> node-sass@3.8.0 postinstall L:\自动化\new\node_modules\gulp-sass\node_modules\node-sass
> node scripts/build.js

"L:\自动化\new\node_modules\.3.8.0@node-sass\vendor\win32-x64-47\binding.node" exists.testing binary.Binary is fine; exiting.
node-sass@3.8.0 L:\自动化\new\node_modules\gulp-sass\node_modules\node-sass
```



## 使用 gulp 构建一个项目

### 安装前准备
安装完成Gulp之后我就要频繁的使用它，进行代码自动化处理。由于服务来自外国，可以被墙了。[淘宝 NPM 镜像](npm.taobao.org "这是一个完整 npmjs.org 镜像，你可以用此代替官方版本(只读)，同步频率目前为 10分钟 一次以保证尽量与官方服务同步。")

### 新建文件package.json

```
luuman@luuman-PC MINGW64 /l/自动化/Gulp
$ npm init //创建package.json

name: (Gulp) test                  //名称
version: (1.0.0) 1.0.0             //版本
description: test description      //描述
entry point: (index.js)            //
test command:                      //测试代码
git repository:                    //Git版本库
keywords:                          //关键词
author: luuman                     //作者
license: (ISC)                     //协议
About to write to L:\自动化\Gulp\package.json:
```
最终会在当前目录中创建 package.json 文件并生成类似如下代码：
```
{
  "name": "gulp-demo",
  "version": "1.0.0",
  "description": "gulp-demo",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git@github.com:luuman/Game.git"
  },
  "keywords": [
    "H5"
  ],
  "author": "luuman li",
  "license": "MIT",
  "bugs": {
    "url": "https://github.com/luuman/Game/issues"
  },
  "homepage": "http://luuman.github.io/Game/",
}
```
### 安装gulp依赖包
```
npm install gulp --save-dev
```
此时打开 package.json 会发现多了如下代码
```
"devDependencies": {
    "gulp": "^3.8.11" //声明此项目的开发依赖 gulp
}
```

### 安装gulp功能插件依赖包

#### 未配置文档
```
npm install gulp-uglify gulp-watch-path stream-combiner2 gulp-sourcemaps gulp-minify-css gulp-autoprefixer gulp-less gulp-ruby-sass gulp-imagemin gulp-util --save-dev
```
```
此时，package.json 将会更新
"devDependencies": {
    "colors": "^1.0.3",
    "gulp": "^3.8.11",
}
```
#### 已配置文档
当你将这份 gulpfile.js 配置分享给你的朋友时，就不需要将 node_modules/ 发送给他，他只需在命令行输入
```
npm install
```

### 设计目录结构

我们将文件分为2类，一类是源码，一类是编译压缩后的版本。文件夹分别为 src 和 dist。(注意区分 dist 和 ·dest 的区别)
```
TestProject     (项目名称)

|– .git             通过git进行版本控制,项目自动生成这个文件
|– node_modules     组件包目录
|– dist             **发布环境**（编译自动生成的）
    |– css/         样式文件(style.css style.min.css)
    |– images/      图片文件(压缩图片\合并后的图片)
    |– js/          js文件(main.js main.min.js)
    |– index.html   静态页面文件(压缩html)
|– src              **开发环境**
    |– sass/                *.scss *.sass 文件夹
    |– less/                less文件夹
    |– images/              图片文件夹
    |– fonts/               字体文件夹
    |– js/                  js文件夹
    |– index.html           静态文件
|– gulpfile.js              gulp配置文件
|– package.json             依赖模块json文件,在项目目录下npm install会安装项目所有的依赖模块，简化项目的安装程序
```

### gulp-util
```
var gulp = require('gulp')
var gutil = require('gulp-util')

gulp.task('default', function () {
    gutil.log('message')
    gutil.log(gutil.colors.red('error'))
    gutil.log(gutil.colors.green('message:') + "some")
})
```



### Browser Sync自动刷新

Browser Sync 帮助我们搭建简单的本地服务器并能实时刷新浏览器，它还能 同时刷新多个设备。

不只是自动刷新
BrowserSync并不只是一个自动刷新工具，它还有许多其他功能。默认配置下，BrowserSync会在多个浏览器中同步滚动条位置，表单行为和点击事件。而且可以在不同设备上进行实时浏览文件效果，在局域网里面。

```
[11:33:17] Finished 'dev' after 6.07 μs
[BS] Access URLs:
 -------------------------------------
       Local: http://localhost:3000
    External: http://192.168.1.63:3000
 -------------------------------------
          UI: http://localhost:3001
 UI External: http://192.168.1.63:3001
 -------------------------------------
[BS] Serving files from: dist/
[BS] Watching files...
```

### 快速拷贝部署文件

在已经有成熟的gulp构建文件，新建文件夹，将文件gulpfile.js、package.json、src文件夹。
>cnpm install gulp引入gulp
>gulp install安装插件
>gulp执行