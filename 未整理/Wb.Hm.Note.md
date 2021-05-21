---
title: 前端基础——HTML（一）
date: 2018-6-10
tags:
- Technology
- Website
- HTML
- JavaScript
- CSS
categories: 
- Technology
- Website
- HTML
location: 青島市
description: HTML 筆記系列。
photo: 
 - "https://s2.ax1x.com/2019/05/16/Eb64Ff.png"
---

### 文字

```html
<b>字体加粗</b>
<i>斜体字体</i>
<u>下划线</u>
<s>删除线</s>

上标：X<sup>2</sup>
下标：Y<sub>3</sub>

//字体相关属性：
<font size="5" color="red" face="黑体">字体，添加属性值</font>  
<font size="3" color="#333333" face="黑体">size的值是1~7；color的表达方式：英语单词 RGB 十六进制</font>
```

### 标题 段落 换行 水平线

```html
//标题:
<h1 align="center">1号标题</h1>

//段落：<p></p>
<p>第一段</p>

//换行：<br />                 
<br />  //换行

//水平线:<hr />
<hr />
<hr size="10" width="800"/>
<hr size="10" width="800" noshade="noshade"/>  
<hr size="30%" width="80%" /> //随屏幕百分比变化
```

### 图片 超链接 锚点链接

```html
/* 相对路径和绝对路径
 绝对路径：协议+主机+路径+文档
 相对路径：./ 当前目录  ../ 父级目录   / 根目录   ../../父目录的父目录

URL：scheme://host.domain:port/path/filename
*/

//图像:<img src="" />

属性：
scr    //source 图像的URL地址
title  //鼠标悬停显示的图片描述
alt    //在浏览器无法载入图像时展示给读者提示的信息
width
height
broder //边框

//超链接：<a href=""></a>
<a href="http://www.baidu.com" target="_blank"></a>

href: 链接地址
target: 定义被链接的文档在何处显示  _blank(新标签打开)  
                                _self (当前标签打开) 
                                _parent
                                _top


//锚点链接:定义一个唯一的'id' 赋给href 实现跳转
<a href="#p1">点击前往第七段</a>
<p id="p1">第七段</p>
```

### HTML的实体

```html
在 HTML 中，某些字符是预留的：小于号（<）和 大于号（>），会误认为是标签。
因此，在 HTML 源代码中使用字符实体（character entities）来显示预留字符。
&nbsp;  //空格
&quto;  //引号
&yen;  //￥
&times; 
&divede;
```

### 列表: ol ul li

```html
分为：
   有序列表:<ol></ol> 
   无序列表:<ul></ul>

1）有序列表： 用于显示具有统一特征的有序数据

<ol type="i" start="3">
  <li>新闻1</li>
  <li>新闻2</li>
  <li>新闻3</li>
  <li>新闻4</li>
</ol>

属性   值              描述
type   1 数字(默认)    排序
       a 字母
       A 大写字母A
       i 小写罗马
       I 大写罗马
start  数字           起始数字


2）无序列表：用于显示同一特征的无限数据

<ul type="circle">
  <li>...</li>
  <li>...</li>
  <li>...</li>
</ul>

属性   值                  
type   disc 实心圆(默认)     
       circle  空心圆
       square 实心矩形
       none  无
```

### 表格: table

+ 用途：table元素的作用是显示表格化的数据！
+ table元素可以嵌套。

```html
//用途：table元素的作用是显示表格化的数据！

<table>  ---------表格
  <tr>   ---------行
    <th>内容</th>  ---------单元格(字体加粗)
    <td>内容</td>  ---------单元格
  </tr>
</table>


table属性               值           
width
height
bgcolor           背景颜色（英语颜色；RGB；十六进制）
background        背景图片
border
bordercolor
cellpadding       单元格与内容之间的间距
cellspacing       单元格与单元格的边距
align  

tr属性            值
align           (left|center|right)
bgcolor         (英文颜色|rgb（255，255，255）|十六进制)
valign          垂直对齐方式（top|middle|bottom）

th td属性         值
align           (left|center|right)
bgcolor         (英文颜色|rgb（255，255，255）|十六进制)
valign          垂直对齐方式（top|middle|bottom）
rowspan         行合并
clospan         列合并
```

### 表单: form

+ **作用：**用于收集用户输入


```html
表单元素: 指的是不同类型的 input 元素、复选框、单选按钮、提交按钮等等

<form action="action_page.php" method="POST" name="">
  表单元素...
</form>

属性
name      表单的名字
method    规定在提交表单时所用的方法：get/post
action    定义在提交表单时执行的动作

常用的表单元素:

<input type=""/>  根据不同的 type 属性，可以变化为多种形态。
<select></select>  定义下拉列表。
<textarea></textarea>  定义多行输入字段（文本域）。
<button></button> 定义可点击的按钮。

文本框：<input type="text"> 定义供文本输入的单行输入字段。
<input type="text" name="控件名字" value="值" maxlength="最大输入字符长度" size="控件宽度" readonly="readonly"（只读） />

密码框：<input type="password"> 定义密码字段。
<input type="password" name="控件名字" value="值" maxlength="最大输入字符长度" size="控件宽度" readonly="readonly"（只读） />

多选勾选控件：<input type="checkbox"> 定义复选框
<input type="checkbox" name="控件名字" value="值" checked="checked"(已选中) disabled = "disabled"(禁用控件) />

单选勾选控件：<input type="radio"> 定义单选按钮。
<input type="radio" name="控件名字" value="值" checked="checked"(已选中) disabled = "disabled"(禁用控件) />

提交表单按钮：<input type="submit"> 定义提交表单数据至表单处理程序的按钮。
<input type="submit" value="按钮字样" />

重置表单按钮：
<input type="reset" value="按钮字样" />

上传文件按钮：
<input type="file" name="文件名称">

隐藏域:
<input type="hidden" name="控件名字" value="值" />

按钮：<input type="button> 定义按钮。
<input type="button" onclick="alert('Hello World!')" value="Click Me!">

<!--
HTML5 增加了多个新的输入类型：（老式浏览器不支持的输入类型，会被视为输入类型 text）  

<input type="number" name="quantity" min="1" max="5">

<input type="color" name="favcolor">

<input type="range"> 用于应该包含一定范围内的值的输入字段。
<input type="range" name="points" min="0" max="10">

<input type="date"> 用于应该包含日期的输入字段。
<input type="date" name="bday" max="1979-12-31"><br>

<input type="month"> 允许用户选择月份和年份。
<input type="month" name="bdaymonth">

<input type="week"> 允许用户选择周和年。
 <input type="week" name="week_year">

<input type="time"> 允许用户选择时间（无时区）。
<input type="time" name="usr_time">

<input type="datetime"> 允许用户选择日期和时间（有时区）。
<input type="datetime" name="bdaytime">

<input type="datetime-local"> 允许用户选择日期和时间（无时区）。
<input type="datetime-local" name="bdaytime">

<input type="email" name="email">

<input type="search" name="googlesearch">

<input type="tel" name="usrtel">

<input type="url" name="homepage">
-->

多行文本控件：
<textarea name="控件名称" cols="设置长度" rows="设置宽度">
  文本内容
</textarea>

下拉框控件：
<select name="控件名字">
  <option value="值" selected="selected"(已选中)>选择内容</option>
  <option value="值" >选择内容</option>
  <option value="值" >选择内容</option>
</select>

下拉选项的分组：
<optgroup label="分组标签01">
  <option value="值" selected="selected"(已选中)>选择内容</option>
  <option value="值" >选择内容</option>
  <option value="值" >选择内容</option>
</optgroup>

按钮：
<button type="button" onclick="alert('Hello World!')">Click Me!</button>
```

实践：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 
<html xmlns="http://www.w3.org/1999/xhtml"> 
<head> 
   <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> 
   <title>用户注册例子</title> 
</head> 
<body> 
    <form name="" method="" action="">
        <table align="center" width="500" cellspacing="0" cellpadding="10" border="1" bgcolor="cyan">
            <tr>
                <th colspan="2">用户注册</th>
            </tr>
            <tr>
                <th>用户名:</th>
                <td>
                    <input type="text" name="inputyourname" value="" maxlength="20" \>
                </td>
            </tr>
            <tr>
                <th>密 码:</th>
                <td>
                    <input type="text" name="inputyourpsw" value="" maxlength="20" \>
                </td>
            </tr>
            <tr>
                <th>性 别:</th>
                <td>
                    男<input type="radio" name="sex" value="" \>
                    女<input type="radio" name="sex" value="" \>
                    保密<input type="radio" name="sex" value="" checked="checked"\>
                </td>
            </tr>
            <tr>
                <th>爱 好:</th>
                <td>
                    <input type="checkbox" name="love" value="" checked="checked" \>唱歌
                    <input type="checkbox" name="love" value=""  \>跳舞
                    <input type="checkbox" name="love" value=""  \>绘画
                    <input type="checkbox" name="love" value=""  \>书法
                    <input type="checkbox" name="love" value=""  \>篮球
                    <br \>
                    <input type="checkbox" name="love" value=""  \>足球
                    <input type="checkbox" name="love" value=""  \>乒乓球
                    <input type="checkbox" name="love" value=""  \>游泳
                    <input type="checkbox" name="love" value=""  \>溜冰
                </td>
            </tr>
            <tr>
                <th>家 乡:</th>
                <td>
                    <select name="">
                        <optgroup label="第一选区">
                            <option value="" selected="selected">选项11</option>
                            <option value="">选项12</option>
                            <option value="">选项13</option>
                        </optgroup>
                        <optgroup label="第二选区">
                            <option value="">选项21</option>
                            <option value="">选项22</option>
                            <option value="">选项23</option>
                        </optgroup>
                        <optgroup label="第三选区">
                            <option value="">选项31</option>
                            <option value="">选项32</option>
                            <option value="">选项33</option>
                        </optgroup>
                    </select>
                </td>
            </tr>
            <tr>
                <th>自我介绍:</th>
                <td>
                    <textarea cols="50" rows="10" >
                        请输入自我介绍:
                    </textarea>
                </td>
            </tr>
            <tr>
                <td colspan="2" align="center">
                    <button>我要注册</button>
                </td>
            </tr>
        </table>
    </form>

</body> 
</html>
```

### 框架: frameset

```html
//通过使用框架，你可以在同一个浏览器窗口中显示不止一个页面。

1. 框架结构标签：<frameset></frameset>
作用：定义如何将窗口分割
属性名  值
rows  横向分割（固定值px|百分比|*）有三种写法:（200，300，500）（20%，30%,*）（20%,*,*）
cols  纵向分割（固定值px|百分比|*）
border 边框宽度（px）
frameborder 是否显示边框（0|1） 0-不显示 1-显示

2.框架标签：<frame />
作用：定义了放置在每个框架中的HTML文档。
属性
scr    URL链接
name   窗口名称
scrolling    滚动条，默认显示（no）
noresize     边框是否可以被拖动（noresize）

//e.g.:设置一个两列的框架集: 第一列占据浏览器窗口的 25%。第二列占据浏览器窗口的 75%。HTML 文档 "frame_a.htm" 被置于第一个列中，而 HTML 文档 "frame_b.htm" 被置于第二个列中
<frameset cols="25%,75%">
   <frame src="frame_a.htm">
   <frame src="frame_b.htm">
</frameset>

3.内联框架：<iframe src=""></iframe>
作用：用于在网页内显示网页
<iframe src="demo_iframe.html" width="200" height="200" frameborder="0"></iframe>

4. noframes标签: <noframes></noframes>
用于为不支持框架集的浏览器显示文本

e.g.
<noframes>对比起，您的浏览器不支持框架集类型</noframes>
```

### 样式和脚本

```html
//样式标签：<style></style>  
//脚本标签：<script></script>
```

### 块: div span

HTML 元素被定义为块级元素或内联元素。

+ 块级元素：以新行来显示。
+ 内联元素：不会以新行来显示。

```html
//div和span标签

<div> 元素是块级元素，常用于组合其他 HTML 元素的容器，进行文档布局。---
<span> 元素是内联元素，常用作文本的容器。


块级元素：
<body></body>
<div></div>  //常用的布局元素
<h1></h1>...<h6></h6>
<ol></ol>
<ul></ul>
<li></li>
<p></p>
<table></table>
<tr></tr>
<td></td>


内联元素：
<a href=""></a>
<i></i>
<u></u>
<b></b>
<span></span>  //文本标签
<font></font>
```

這裡表示本文已結束。。。
