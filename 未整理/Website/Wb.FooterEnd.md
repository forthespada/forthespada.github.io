---
title:  轉 footer固定在页面底部
categories: 
- Technology
- Website
- HTML
tags: 
- Technology
- Website
- HTML
- CSS
- Layout
- Footer
date: 2017-12-28
location:  四川大學
description:  将footer固定在页面底部的实现方法
photo:  
 -  "https://s2.ax1x.com/2019/05/16/Eb64Ff.png"
---

## footer高度固定+绝对定位

HTML结构：

```html
<body>
    <header>header</header>
    <main>main content</main>
    <footer>footer</footer>
</body>
```

CSS设置：

```css
html{height:100%;}
body{min-height:100%;margin:0;padding:0;position:relative;}

.header{background-color: #ffe4c4;}
.main{padding-bottom:100px;background-color: #bdb76b;}/* main的padding-bottom值要等于或大于footer的height值 */
.footer{position:absolute;bottom:0;width:100%;height:100px;background-color: #ffc0cb;}
```

首先，设置body的高度至少充满整个屏幕，并且body作为footer绝对定位的参考节点；
其次，设置main（footer前一个兄弟元素）的padding-bottom值大于等于footer的height值，以保证main的内容能够全部显示出来而不被footer遮盖；
最后，设置footer绝对定位，并`设置height为固定高度值`。

## footer高度固定+margin负值

HTML结构：

```html
<body>
    <div class="container">
        <header>header</header>
        <main>main content</main>
    </div>
    <footer>footer</footer>
</body>
```

CSS设置：

```css
html,body{height:100%;margin:0;padding:0;}

.container{min-height:100%;}
header{background-color: #ffe4c4;}
main{padding-bottom:100px;background-color: #bdb76b;}/* main的padding-bottom值要等于或大于footer的height值 */
footer{height:100px;margin-top:-100px;background-color: #ffc0cb;}/* margin-top（负值的）高度等于footer的height值 */
```

此方法把footer之前的元素放在一个容器里面，形成了container和footer并列的结构：
首先，设置.container的高度至少充满整个屏幕；
其次，设置main（.container最后一个子元素）的padding-bottom值大于等于footer的height值；
最后，设置footer的height值和`margin-top负值`。

这种方法没有使用绝对定位，但html结构的语义化不如方法一中的结构清晰。

也可以设置负值的margin-bottom在.container上面，此时html结构变化如下：

```html
<body>
    <div class="container">
        <header>header</header>
        <main>main content</main>
        <div class="empty"></div>
    </div>
    <footer>footer</footer>
</body>
```

CSS设置：

```css
html,body{height:100%;margin:0;padding:0;}
.container{min-height:100%;margin-bottom:-100px;}
.empty,footer{height:100px;}
```

使用一个空的div把footer容器推到页面最底部，同时给container设置一个负值的margin-bottom，这个margin-bottom与footer和.empty的高度相等。

虽然多了一个空的div，语义上也不怎么好，但是相比前面为main元素设置padding-bottom的方法有一个明显的好处：当网页内容不满一屏的时候，如果需要为main元素设置边框、背景色的时候，padding-bottom硬生生地撑出了一片空白，真真是有点丑，但是加个空的div之后，布局方式作用在.empty上，对main的css设置就不影响了，算是一个好处吧！

## footer高度任意+js

HTML结构：

```html
<body>
    <header>header</header>
    <main>main content</main>
    <footer>footer</footer>
</body>
```

CSS设置：

```css
html,body{margin:0;padding: 0;}
header{background-color: #ffe4c4;}
main{background-color: #bdb76b;}
footer{background-color: #ffc0cb;}

/* 动态为footer添加类fixed-bottom */
.fixed-bottom {position: fixed;bottom: 0;width:100%;}
```

js代码:

```javascript
$(function(){
    function footerPosition(){
        $("footer").removeClass("fixed-bottom");
        var contentHeight = document.body.scrollHeight,//网页正文全文高度
            winHeight = window.innerHeight;//可视窗口高度，不包括浏览器顶部工具栏
        if(!(contentHeight > winHeight)){
            //当网页正文高度小于可视窗口高度时，为footer添加类fixed-bottom
            $("footer").addClass("fixed-bottom");
        }
    }
    footerPosition();
    $(window).resize(footerPosition);
});
```

