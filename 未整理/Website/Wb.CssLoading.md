---
title: 根据浏览器加载CSS
tags:
- Technology
- Website
- HTML
- CSS
- Explorer
categories:
- Technology
- Website
- HTML
date: 2017-09-28 
location: 四川大學
description: 根据不同的浏览器加载不同的CSS文件
photo: 
 - "https://s2.ax1x.com/2019/05/16/Eb6fTP.png"
---


##  解释

`！：非` ，
`gt：greater than` ，
`lt：less than` ，
`gte：greater than or equal` ，
`lte:less than or equal` 

## 代码示例

```html
&lt;!--[if IE]&gt; &lt;link rel="stylesheet" type="text/css" hrf=""&gt; &lt;![endif]--&gt;    //对所有的ie都起作用
&lt;!--[if !IE]&gt; &lt;link ……&gt; &lt;!--&lt;![endif]--&gt;  //非ie浏览器
&lt;!--[if IE7]&gt; &lt;link ……&gt; &lt;!--[enfif]--&gt;    //ie7浏览器
     if IE7 还可以替换为
            if IE6        //ie6浏览器
            if IE5        //ie5浏览器
            if IE5.5000   //ie5.5浏览器
只对ie6及其一下版本影响：
&lt;!--[if lt IE7]&gt; &lt;link ...&gt; &lt;![endif]--&gt;
&lt;!--[if lte IE6]&gt; &lt;link ...&gt; &lt;![endif]--&gt;
只对IE7及以下的版本起作用：
&lt;!--[if lt IE 8]&gt;  &lt;link ...&gt; &lt;![endif]--&gt;
&lt;!--[if lte IE 7]&gt;  &lt;link ...&gt; &lt;![endif]--&gt;
只对IE8及以下的版本起作用：
&lt;!--[if lt IE 9]&gt;  &lt;link ...&gt; &lt;![endif]--&gt;
&lt;!--[if lte IE 8]&gt;  &lt;link ...&gt; &lt;![endif]--&gt;
只对IE6及以上的版本起作用：
&lt;!--[if gt IE 5.5]&gt;  &lt;link ...&gt; &lt;![endif]--&gt;
&lt;!--[if gte IE 6]&gt;  &lt;link ....&gt; &lt;![endif]--&gt;
只对IE7及以上的版本起作用：
&lt;!--[if gt IE 6]&gt;  &lt;link ...&gt; &lt;![endif]--&gt;
&lt;!--[if gte IE 7]&gt;  &lt;link ...&gt; &lt;![endif]--&gt;
只对IE8及以上的版本起作用：
&lt;!--[if gt IE 7]&gt;  &lt;link ...&gt; &lt;![endif]--&gt;
&lt;!--[if gte IE 8]&gt;  &lt;link ...&gt; &lt;![endif]--&gt;
```



