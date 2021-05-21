---
title: CSS布局
tags:
- Technology
- Website
- HTML
- Javascript
- CSS

categories:
- Technology
- Website
- CSS
- Layout
---
## 1. Margin

使用`margin: 0 auto`时会使容器居中，但当浏览器窗口被缩小时，浏览器上出现滚动条，为了防止这种情况的发生可以为容器设置`max-width`属性，结果如下：

```css
#div{
  width：pixels;
  height：pixels;
  margin：0 auto;
  max-width: pixels;
}
```

> 所有的主流浏览器包括IE7都支持该属性。

+ table方法：width必须是百分比值。
```html+css
<div class="Table-Cell">
    <div class="Center-Block">
    <!-- CONTENT -->
    </div>
  </div>

.Table-Cell {
  display: table-cell;
  vertical-align: middle;
}
.Center-Block {
  width: 50%;
  margin: 0 auto;
}
```

## 2. 盒模型

当设置了元素的宽度，实际展现的元素却超出你的设置：这是因为元素的边框和内边距会撑开元素。要解决这种现象应当使用`box-sizing:border-box`属性，可以减少计算。结果如下：

```css
*{
-webkit-box-sizing: border-box;
   -moz-box-sizing: border-box;
        box-sizing: border-box;
}
```

>  `box-sizing` 是支持[IE8+](http://caniuse.com/#search=box-sizing)的。

## 3. 清除浮动

当图片的高度大于包含它的容器时，图片会溢出容器，要解决这种现象，可以使用：

```css
#div{
  overflow：auto;
  zoom：1; //可支持ie6
}
```

现在各大网站包括boostrap都会使用如下的代码：

​```css
.clearfix:before,
.clearfix:after
{
  display: table;
  content: " ";
}
.clearfix:after
{
  clear: both;
}
.clearfix{zoom:1;} //ie 6 7
```

至于before和after中的`display:table`;是为了防止**子元素垂直方向上的边距折叠，也就是通常说的子元素margin-top会被转移到父元素的问题**

## 4. 媒体查询

“响应式设计（Responsive Design” 是一种让网站针对不同的浏览器和设备“呈现”不同显示效果的策略，这样可以让网站在任何情况下显示的很棒！





# display:inline-block属性带来的空白间隙问题

这个现象产生的原因就是我们编码的习惯照成的，我们习惯在标签结束处敲一个回车，然而回车会产生回车符，相当于空白符。当多个空白符连续使用时，会合并成一个空白符。正是这个习惯照成了空白间隔。解决方法：

```css
.demo02{
  width:pixels;
  margin:0 auto;
  font-size:0;//消除水平方向间隔，会使文字消失
}
.demo02 li{
  display:inline-block; 
  *display:inline; 
  *zoom:1; // *只能被ie6、ie7支持;
  width:pixels; 
  height:pixels; 
  vertical-align:top; //消除垂直方向间隔
  font-size:pixels; //显示文字
}
```

# 关于子元素的margin-top属性会传给父元素的问题

**问题描述：**
一个父包含框包含一个子元素。给正常流的子元素一个垂直外边距margin-top就会使得父元素跟着往下走，而子元素和父元素的边距则没有发生变化。

**html结构：**
<div class="box1"><div class="box1_1"></div></div>
css样式：
.box1{height:400px;background:#efefef;}
.box1_1{height:100px;margin-top:50px;background:black;}

**解决办法：**
1.修改父元素的高度，增添padding-top样式（常用）；
2.为父元素添加overflow:hidden;样式即可（完美）；
5.为父元素或者子元素声明浮动（可用）；
3.为父元素添加border（可用）;
4.添加额外的元素放在子元素最前面，设置高度为1px，overflow:hidden(若为行内元素，需要声明为块元素)（啰嗦）;
6.为父元素或者子元素声明绝对定位（……）;

**原理：**
一个盒子如果没有上补白(padding-top)和上边框(border-top)，那么这个盒子的上边距会和其内部文档流中的第一个子元素的上边距重叠。
这个问题的避免方法很多，只要破坏它出现的条件就行。给**Outer Div** 加上 padding/border，或者给 **Outer Div / Inner Div** 设置float/position:absolute(CSS2.1规定浮动元素和绝对定位元素不参与Margin折叠)。 
在 IE 中如果这个盒子有 layout 那么这种现象就不会发生了：似乎拥有 layout 会阻止其孩子的边距伸出包含容器之外。此外当 hasLayout = true 时，不论包含容器还是孩子元素，都会有边距计算错误的问题出现。



# IE6,7,8支持HTML5/CSS3网站的三种途径

## 1. HTML5SHIV

```HTML
<!--[if lt IE 9]>
<script src="dist/html5shiv.js"></script>
<![endif]-->
```

## 2.SELECTIVIZR

```HTML
<!--[if lte IE 8]><script src="js/libs/selectivizr.js"></script><![endif]-->
```

## 3. <html>条件判断注释

```html
<!DOCTYPE html>
<!--[if lt IE 7 ]> <html class="ie6 lazy " lang="en"> <![endif]-->
<!--[if IE 7 ]>    <html class="ie7 lazy " lang="en"> <![endif]-->
<!--[if IE 8 ]>    <html class="ie8 lazy " lang="en"> <![endif]-->
<!--[if IE 9 ]>    <html class="ie9 lazy " lang="en"> <![endif]-->
<!--[if (gt IE 9)|!(IE)]><!--> <html lang="en"> <!--<![endif]-->
```







# KILL IE6

以下代码可以插入到</body> 以上的任何地方。

**English**
```html
<!--[if IE 6]> 
<script src="//letskillie6.googlecode.com/svn/trunk/2/default.js"></script>
<![endif]—> 
```
**简体中文**
```html
<!--[if IE 6]>
<script src="//letskillie6.googlecode.com/svn/trunk/2/zh_CN.js"></script>
<![endif]—> 
```
**繁體中文**
```html
<!--[if IE 6]> 
<script src="//letskillie6.googlecode.com/svn/trunk/2/zh_TW.js"></script><![endif]—> 
```
**日本語**
```html
<!--[if IE 6]>
 <script src="//letskillie6.googlecode.com/svn/trunk/2/ja.js"></script>
<![endif]—>
```
