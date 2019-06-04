---
title: 'Web编程基础知识'
date: 2017-04-27
permalink: /posts/2017-04-27-WebProgramming/
tags:
  - 知识积累
  - web
  - html
  - CSS
  - JavaScript
  - php
mathjax: true
---

!['Web-Programming'](../images/WebProgramming-Web-Programming.jpg)

前段时间零零碎碎看了Web编程相关内容，今天就整理了一下
Web编程，前端主要是html+CSS+JavaScript，后端使用最多的是PHP+MySQL
此次教程主要是关于html、CSS、JavaScript和PHP的一些语法和使用细则
<!-- more -->

# 1  Html: HyperText Markup Language，超文本标记语言，网络内容载体

(1) Html是网页内容载体、CSS（层叠样式表）样式是表现、JavaScript是用来实现网页的特效效果
(2) Html语言不分大小写，但建议使用小写
(3) 常用标签：
```html
    <html>根标签</html>；
    <head>头部标签</head>；
    <h1>标题</h1>，h1-h6；
    <p>段落标签</p>；
    <img src=’1.jpg’>插入图片；
    <span>特殊样式</span>；
    <q>引用</q>，<blockquote>长文本引用</blockquote>
    <br />或者<br>回车，&nbsp;空格，<hr />或者<hr>横线；
    <address></address>地址；
    <code></code>代码，<pre>多行代码；
    <ul><li></li><li></li>…</ul>无序列表，<ol><li></li><li></li>…</ol>有序列表；
    <table><tbody><tr><th><td>表格；
    <a herf =’’title=’’target=’’>链接；
    <text area cols=’’rows=’’>文本域
    <select>下拉
    `<!--注释文字-->`
```
(4) html样式 
```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
    {content}
    </body>
    </html>   
```
# 2  CSS: Cascading Style Sheets，层叠样式表，网页样式表现

(1) CSS样式包含内联式、嵌入式、外部式，优先次序依次
(2) 选择器包含：选择器、类选择器、id选择器、后代选择器、子选择器、伪选择器、分担选择符
(3) 权值大小决定样式，标签1，类10，id100，!important 最高权值
(4) 字体属性：`font-size`、`font-family`、`font-weight(bold/italic)`…
(5) 元素包含块、内联、内联-块，display（inline、block、inline-block）
(6) CSS布局：流动模型、浮动模型、层模型
# 3  JavaScript，脚本语言，用来实现网页的动态效果

(1) 调用样式：
```html
<script type = "text/javascript"></script>
<script src="script.js"></script>
```
(2) JavaScript作为脚本语言可以放在html任何位置，浏览器按先后顺序进行解释，一般置于head和body之间
(3) 单行注释`//……`和多行注释`/*……*/`
(4) `var a`：定义变量名（字母/_/$开头）
(5) JS区分大小写
(6) `if(){} else{}`
(7) 确认对话框：`var message = confirm("……")`
(8) 提问对话框：`var myname = prompt("……")` 
(9) 打开新窗口：`window.open([url],[name],[param])`，
    [name]: `_blank`(新窗口) /`_self`(当前窗口)/`_top`(框架网页上部)
    [param]: `top|left|right|width|height: 50px`/`menubar|toolbar|scrollbars|status: yes|no`
(10) 关闭窗口：`window.close()`
(11) `alert()`: 警告
(12) `document.writ()`：输出文本
(13) `document.getElementByid('')`：通过ID获取元素
(14) `NaN`(Not a Number)，与任何数都不相等，判断用`isNaN(NaN)`, `Infinity`(无穷大)
(15) 或/且/非: && / || / !
(16) 等号用`===`(不会转换数据类型)，不用`==`
(17) 浮点比较用差值：`Math.abs(1/3 -(1-2/3))<0.000001`
(18) 空值：JavaScript(`null`)/swift(`nil`)/Java(`null`)/Python(`None`)
(19) 数组：`var arr = [1,2,3,null,true]/new Array(1,2,3,null,true)` 
(20) 对象：`var person = {name:'bob',age:20,···}`
(21) JavaScript是动态语言，`var a=123;a='ABC';`不会报错, Java里就会报错
(22) 变量未声明即为全局变量，`'use strict'`变量强制需要声明才能使用
(23) `\`用于转义，反引号`hello`表示多行字符串
(24) 操作字符串：`var s='hello'`, `s.length`, `s[0]`(超出不会报错，返回`undefined`), `toIpperCase`, `toLowerCase`, `substring(0,2`) 
(25) 操作数组：`arr.length`,`arr.slice()`,`arr.push()`,`arr.pop()`,`arr.unshift()`,`arr.shift()`,`arr.soft()`,`arr.reverse()`,`arr.splice()`,`concat()`: 连接数组，`arr.join('-')`: 替换逗号，变为字符串
(26) `for (var key in …)`, `while`, `do...while`, `for...of`
(27) RegEXP: `\d`: 匹配一个数字,`\w`: 匹配一个字母或数字,`.`: 匹配任何字符,`*`: 匹配至少一个字符,`?`: 匹配0个或1个任意字符,`{n}`：n个字符
(28) JSON: JavaScript Object Notation, JS 对象标记, 轻量级的数据交换格式，`var json = '{"a": "Hello", "b": "World"}'`(对比xml)
(29) 面向对象：`var Student{}`, `var xiaoming = {}`, `xiaoming._proto_ = student`
# 4 PHP（外文名：PHP: Hypertext Preprocessor，中文名：“超文本预处理器”）

(1) 创建动态交互性站点强有力的服务器端脚本语言（后端语言）
(2) 引用格式：
```php
<?php
echo "我的第一段PHP脚本"
?>
```
(3) WordPress、Facebook、Twitter核心都是PHP
(4) 功能包括：生成动态页面、创建/打开/读取/写入/删除/关闭服务器文件、接受表单、发送并取回cookie。数据库、限制访问、数据加密
(5) PHP可运行于各种平台，多种服务器（Apache、IIS）、多数据源、免费、易于学习
(6) 注释用`//`、`#`、`/*...*/`
(7) 函数、类、关键词对大小写不敏感，变量对大小写敏感（以$开头，常量不加$）
(8) 变量无需定义类型，三种作用域（local、global、static）
(9) `echo`(无返回值)和`print`(返回值1)，用于输出
(10) `str()`字符串长度
(11) `strpos('hello world', 'world')`，匹配返回（true和flase）
(12) 等号用`===`(不会转换数据类型)，不用`==`
(13) document.getElementByid('')：通过ID获取元素
(14) NaN(Not a Number)，与任何数都不相等，判断用isNaN(NaN), Infinity(无穷大)
(15) 与：&&/and，或：or/||，非：！，异或：Xor 
