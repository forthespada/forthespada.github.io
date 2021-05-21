---
title: 圣杯布局
tags:
- Technology
- Website
- HTML
- Javascript
- CSS
- Layout
categories:
- Technology
- Website
- CSS
date: 2017-10-30
location: 四川大學
description: 在網頁中使用聖杯佈局（上[左中右]下）。
photo: 
 - "https://s2.ax1x.com/2019/05/16/Eb6Owq.png"
---
## 圣杯布局

代码如下

```html
<div id="header">#header</div>
<div id="container">
  <div id="center" class="column">#center</div>
  <div id="left" class="column">#left</div>
  <div id="right" class="column">#right</div>
</div>
<div id="footer">#footer</div>
```

```css
body {
  min-width: 550px;      /* 2x LC width + RC width */
}
#container {
  padding-left: 200px;   /* LC width */
  padding-right: 150px;  /* RC width */
}
#container .column {
  height: 200px;
  position: relative;
  float: left;
}
#center {
  background-color: #e9e9e9;
  width: 100%;
}
#left {
  background-color: red;
  width: 200px;          /* LC width */
  right: 200px;          /* LC width */
  margin-left: -100%;
}
#right {
  background-color: blue;
  width: 150px;          /* RC width */
  margin-right: -150px;  /* RC width */
}
#footer {
  clear: both;
}
#header, 
#footer {
  background-color: #c9c9c9;
}
/*** IE6 Fix ***/
* html #left {
  left: 150px;           /* RC width */
}
```

