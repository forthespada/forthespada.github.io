---
title: Pre标签
date: 2018-8-12
tags:
- Technology
- Website
- HTML
- Pre
- Prism
categories:
- Technology
- Website
- HTML
location: 青島市
description: HTML 筆記系列之 Pre 標籤。
photo: 
 - "https://s2.ax1x.com/2019/05/16/Eb64Ff.png"
---

## Pre标签

+ 代码主题：prism.js

### 控制 Pre 內文本的換行

可以使用 `white-space` 屬性。該屬性有以下幾個可能的取值：

| 值       | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| normal   | 默认。空白会被浏览器忽略。                                   |
| pre      | 空白会被浏览器保留。其行为方式类似 HTML 中的 `&lt;pre&gt;` 标签。 |
| nowrap   | 文本不会换行，文本会在在同一行上继续，直到遇到 `&lt;br&gt;` 标签为止。 |
| pre-wrap | 保留空白符序列，但是正常地进行换行。可以自動折行。           |
| pre-line | 合并空白符序列，但是保留换行符。                             |
| inherit  | 规定应该从父元素继承 white-space 属性的值。                  |

### 控制 Pre 內的代碼縮進

使用 `tab-size` 屬性。目前只有chrome支持該屬性值。語法和屬性值如下：

```css
tab-size: *number*|*length*|initial|inherit;
```

| 值       | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| *number* | 默认值是 8。规定每个制表符（tab）字符要显示的空格字符的数量。 |
| *length* | 规定制表符（tab）字符的长度。几乎所有的主流浏览器都不支持该属性值。 |
| initial  | 设置该属性为它的默认值。请参阅 [*initial*](https://www.w3cschool.cn/cssref/css-initial.html)。 |
| inherit  | 从父元素继承该属性。请参阅 [*inherit*](https://www.w3cschool.cn/cssref/css-inherit.html)。 |

<div class="note warning">目前只有 Chrome 支持 tab-size 属性。
Firefox 支持另一个可替代该属性的属性，即 -moz-tab-size 属性。
Opera 支持另一个可替代该属性的属性，即 -o-tab-size 属性。
目前没有浏览器支持该值作为长度单位。</div>

