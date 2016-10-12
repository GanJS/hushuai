title: 面向对象的CSS样式
date: 2016-02-27 14:11:20
description: 
categories:
- HTML
tags:
- CSS
toc: true
author:
comments:
original:
permalink: 
---
　　** OOCSS:**面向对象的CSS样式，通过对CSS样式的合理规范，重复使用，达到代码的精简，便于换肤。
<!-- more -->



### 作用：

```
1. 加强代码复用以便方便维护
1. 减少CSS体积
1. 提升渲染效率
1. 组件库思想、栅格布局可共用、减少选择器、方便扩展
```
### 注意事项：

```
1. 不要直接定义子节点，应把共性声明放到父类

.mod .inner{} //

1. 结构和皮肤相分离
1. 容器和内容相分离
1. 抽象出可重用的元素，建好组件库，在组件库内寻找可用的元素组装页面
1. 往你想要扩展的对象本身添加Class，而不是他的父节点
1. 对象应保持独立性
1. 避免使用ID选择器，权重太高，无法重用
1. 避免位置相关的样式
1. 保证选择器相同的权重
1. 类名：简短、清晰、语义化、OOCSS的名字并不影响HTML语义化
```

### 拓展
[OOCSS](http://oocss.org "面向对象的CSS网站")

[Reset](htto://meyerweb.com/eric/tools/css/reset/ "")
>优点：样式初始化设置非常全面
缺点：设置了部分多余的设置，border

[Normalize](http://github.com/necolas/normalize.css "")
>优点：
缺点：有些默认的没有设置

[Neat.css](http://thx.github.io/cube/doc/neat/)
>优点：
1. 解决Bug，低级浏览器常见Bug
1. 统一效果，但不盲目追求重置为0
1. 向后兼容
1. 考虑响应式
1. 考虑移动设备

>缺点：