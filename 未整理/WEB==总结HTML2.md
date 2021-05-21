---
title: 前端基础——Html（二）

tags:
- Technology
- Website
- HTML
- Javascript
- CSS

categories:
- Technology
- Website
- HTML
---

## 字符编码

1. [HTML特殊字符编码对照表](http://www.jb51.net/onlineread/htmlchar.htm)

2. [字符编码详解](http://polaris.blog.51cto.com/1146394/377468/)

##  [I18N-国际化](http://www.ibm.com/developerworks/cn/web/1305_hezj_jqueryi18n/)

## 关于HTML5在浏览器中的兼容性问题

### 方式一：JavaScript

```javascript
<!--[if lt IE9]> 
<script> 
   (function() {
if (! 
 /*@cc_on!@*/
 0) return;
 var e = "abbr, article, aside, audio, canvas, datalist, details, dialog, eventsource, figure, footer, header, hgroup, mark, menu, meter, nav, output, progress, section, time, video".split(', ');
 var i= e.length;
 while (i--){
     document.createElement(e[i])
 } 
 })() 
</script>
<![endif]-->
```

如果是IE9以下的IE浏览器将创建HTML5标签， 这样非IE浏览器就会忽视这段代码，也就不会有无谓的http请求了。

### 方式二：html5shiv

```javascript
<!--[if lt IE9]> 
<script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
<![endif]-->
```

但是不管使用以上哪种方法,都要初始化新标签的CSS.因为HTML5在默认情况下表现为内联元素，对这些元素进行布局我们需要利用CSS手工把它们转为块状元素方便布局

```CSS
/*html5*/
article,aside,dialog,footer,header,section,footer,nav,figure,menu{display:block}
```

**但是如果ie6/7/8 禁用脚本的用户,那么就变成了无样式的"白板"网页,我们该怎么解决呢?**

我们可以参照facebook的做法，即引导用户进入带有noscript标识的 “/?_fb_noscript=1”页面，用 html4 标签替换 html5 标签，这要比为了保持兼容性而写大量 hack 的做法更轻便一些。

```javascript
<!--[if lte IE 8]> 
<noscript>
<style>.html5-wrappers{display:none!important;}</style>
 <div class="ie-noscript-warning">您的浏览器禁用了脚本，请<a href="">查看这里</a>来启用脚本!或者<a href="/?noscript=1">继续访问</a>.
 </div>
 </noscript>
<![endif]-->
```

这样可以引导用户开启脚本,或者直接跳转到HTML4标签设计的界面。

### 关于Modernizr

1. [Modernizr的介绍和使用](http://blog.chinaunix.net/uid-21633169-id-4286857.html)

2. [Modernizr——为HTML5和CSS3而生！](http://www.osmn00.com/translation/221.html)

