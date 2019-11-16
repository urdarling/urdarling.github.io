---
layout: post
title: "兄弟会学习笔记07--Js新手入门"
date: 2019-11-16 14:00:00 +0800
description: javascript如何使用. # Add post description (optional)
tag: [javascript, Ubuntu,]
---

##### 何为Js？

JavaScript 是一种轻量级的编程语言。

JavaScript 是可插入 HTML 页面的编程代码。

JavaScript 插入 HTML 页面后，可由所有的现代浏览器执行。

JavaScript 很容易学习。

JavaScript 是前端开发者使用的主要编程语言，随着前端技术的发展，这门语言的边界也得以不断扩展。

在学习js之前，先声明一下，Js的脚本语言是必须要放在 < script > 标签内的，且< script >标签可以放在 < head > 里也可以放在 < body > 里，一般情况下，除了想要先加载的文件外，我们把它放在< body >里。

##### 如何编写Js

- [ ] ***页面内写法***

 首先呢，当一个浏览器拿到一个网页的时候，比如拿到了一个HTML 的网页，它从上到下依次执行，当它遇上 < link > 标签（也就是网页中引用样式）的时候，它会一边执行< link >一边继续往下进行页面的渲染，二者并不冲突。

   但是，当它遇上 < script > 标签（也就是网页中引用脚本）的时候浏览器则会把渲染的权力交给js，因为js是单线程的，在执行js脚本的时候浏览器是不进行渲染的，直到js脚本文件执行完毕，才会将渲染的权力重新交给浏览器继续完成渲染。

   当一个网页脚本文件很大，且又放在了< head >里，则有可能在进入页面时加载慢，出现空白的现象（就是因为执行js的时候没有同时渲染页面样式导致的），放在后面就可以让页面先加载样式，后执行脚本就不会出现这种问题了。
测试代码如下:

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    // 这个位置也是可以放script标签的，但是建议现在body标签里面
    <title>js的学习及使用</title>
</head>
<body>
    <script>
        // 在页面上添加内容
        document.write("<h1>我是标题</h1>");
        document.write("<div>我是一个div</div>");
    </script>
</body>
</html>
```

  上面例子中的js语句会在页面加载时执行，项目中我们通常需要在某个事件发生的时候执行代码，比如当用户点击按钮时，如果我们把js的代码放到函数中，就可以在事件发生的时候调用该函数：

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="./styles.css">
    <title>js的学习及使用</title>
    <style>
        .btn {
            width: 200px;
            height: 50px;
            line-height: 50px;
            text-align: center;
            border-radius: 20px;
            background: pink;
            /* 鼠标变小手 */
            cursor: pointer;
            margin: 100px auto;
        }
        .text {
            width: 260px;
            margin: 100px auto;
        }
    </style>
</head>
<body>
    <h2 class="text">我是标题</h2>
    <!-- 2. 点击时调用该事件 -->
    <div class="btn" onclick="text()">点击改变标题</div>
    <script>
        // 1. 把改变后的内容封装在这个text()函数内
        function text() {
            document.querySelector(".text").innerHTML="我是被改过的标题哟~~"
        }
    </script>
</body>
</html>
```

- [ ] ***页面外写法***

也可以把脚本保存到外部文件中。外部文件通常包含被多个网页使用的代码。

外部 JavaScript 文件的文件扩展名是 .js。

如需使用外部文件，请在 <script> 标签的 "src" 属性中设置该 .js 文件：

```javascript
<!DOCTYPE html>
<html>
<body>
<script src="myScript.js"></script>
</body>
</html>
```

`注意：外部脚本不能包含 <script> 标签。`

##### 常用Js语法

弹窗

```javascript
alert('我是一个alert弹窗!');
confirm('我是confirm弹窗');
prompt('你吃饭了没?');
```

变量

```javascript
var 变量的名字; // 此时变量仅仅被创建，但是没有存储数据
var 变量的名字 = 变量的值; // 变量不仅仅被创建了，而且还被存储数据
var num = 10 + 2; // 创建了一个变量，变量名叫做num ,并且将数据10 存储到了变量num当中。
// num 相当于存储了10+2这个表达式的结果 
// console.log()里面如果输出的是一段话，那么这段话外面一定要使用引号 
// 如果console.log()里面输出的是一个表达式或者变量，那么就不需要引号。
console.log("尹志平真帅");
// console.log(尹志平真帅); // 此时本条语句会报错，程序会把`尹志平真帅`当做一个变量 
console.log(num);
var _name; // 正确的命名规范
var $age ; // 正确的命名规范
var 1ppp; // 错误的命名
```

第一个字符，可以是任意 Unicode 字母（包括英文字母和其他语言的字母），以及美元符号（$）和下划线（_）。

第二个字符及后面的字符，除了 Unicode 字母、美元符号和下划线，还可以用数字0-9。

`总结起来：就是开头字母可以是英文、字母、下划线、$等。但是不能以数字开头。`

##### 如何通过Js控制Html元素

通过document.getElementById()这个API来获取网页节点。

 

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>获取页面元素</title>
</head>
<body>
<div id="d1">
hello,world!
</div>
</body>
<script>
// 在当前网页文档中获取元素，通过元素的id值来获取元素
var oDiv = document.getElementById('d1');
console.log(oDiv);
</script>
</html>
```

可以通过element.innerHTML属性获取元素内的内容。

如果目标元素是input，我们需要获取的是input的内部的值,可以通过value属性来获取input当中的值。获取其他标签里面的内容，需要使用innerHTML.

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>获取页面元素</title>
</head>
<body>
<div id="d1">
hello,world!
</div>
<input type="text" id="name" value="张三">
</body>
<script>
// 在当前网页文档中获取元素，通过元素的id值来获取元素
var oDiv = document.getElementById('d1');
console.log(oDiv);
var content = oDiv.innerHTML;
console.log(content); 
// 获取一个input里面value的值
var oInput = document.getElementById('name');
console.log(oInput);
var oInput_value = oInput.value;
console.log(oInput_value);
</script>
</html>
```

##### 数据类型

js当中数据类型分为两类：原始数据类型和引用数据类型。

原始类型又称之为基础数据类型，而引用数据类型又称之为对象类型。

原始类型:

    Boolean
    Null
    Undefined
    Number
    String
    Symbol

引用数据类型:

    Object
    Array
    Function
    Date
    Math
    RegExp
二者在内存中存储的位置不同。具体来讲，原始数据类型存储在栈中。而引用数据类型实际存在内存的堆中
。而如果把某个引用数据类型的数据存储到了一个变量当中，本质上是把数据在堆中的位置存储在了变量中，而
变量存储在内存的栈中。

参看资料：

[小白日记](https://www.runoob.com/js/js-output.html)

[新手笔记](https://www.cnblogs.com/zhaohongcheng/p/10839412.html)

