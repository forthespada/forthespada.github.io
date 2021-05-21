## 背景

为了解决初期html当中混乱的表现标记的问题，1995年，W3C（World Wild Web Consortiam，万维网联盟）开始发布css，至1996年推荐草案（Recommendation）已经成熟。

相较于初期只使用html标签和元素，具有以下特点：
+  易于维护
+  缩减文件大小
+  内容和样式的分离
+  易于使用（可将一个样式表应用到多个页面）

## 元素

### 替换元素和非替换元素

+ 替换元素（Replaced Element）是指盖元素所显示的内容并非是由文档内容直接显示，而是援引外部文件或者其他方式。例如：`input`，`img`等元素。
+ 非替换元素（Nonreplaced Element）是指内容有用户代理（一般为浏览器）在元素本身生成的框中显示。例如：`span`，`p`，`div`等元素。

### 块级元素和行内元素

+ 块级元素（Block-level Element）是指该元素自成一列，其前后都生成了“分隔符”，例如：`div`，`p`等元素。

+ 行内元素（Inline Element）是指元素在一个文本行内，不会自动生成“分隔符”，例如：`span`,`em`等元素。

 ==**注意！**==

  行内元素和块级元素有很多共同点，但是他两有一个较大的不同之处在于：在html和xhtml中，块级元素**不会继承**行内元素的属性，在css中对于显示角色如何嵌套则**不存在任何限制**。

### @import指令

​	Internet Explore不会忽略任何@import指令，无论他在何位置。

​	其他浏览器则会忽略在不正确位置上的该指令。

### 向后访问性

如果一个浏览器无法识别`<style></style>`,就是将其通通忽略，但是标记中的声明不一定会忽略，这样样式表的声明会出现在页面的会上面！为了解决这一问题需要将声明标记在注释之中。

```css
<style><!--
@import url(sheet.css);
h1{color:#efefef;}
--></style>
```

### 内联样式

```html
<p style="color:green;">This is a paragraph .</p>
```



## 基本语法

### 语法结构

所有的 CSS 的语法结构都是 `selector{property:value}`。

`property` 和 `value` 之间用 `:` 隔开，`property` 和 `property` 之间用 `;` 隔开。如果 `value` 是多个值的话则用 `“”` 包裹起来。如果同样的属性应用于多个选择器，`selector` 和 `selector` 之间用 `,` 隔开。一个简单的示例如下：

```css
p{
    line-height：1.5rem;
    margin-bottom: 1rem;
}

kbd,code,tt,samp,var{
    background: grey;
    color: white;
}
```

### css的注释 `/* */`

通常注释可以让自己或别人在以后修改代码是可以更加快速的理解代码的含义。注释是不会显示的。

```css
kbd,code,tt,samp,var{
    background: grey; /* 背景颜色为灰色 */
    color: white; /* 字体颜色为白色 */
}
```

1. css的继承

2. css的添加

   ```html
   <link rel="stylesheet" type="text/css" href="">
   ```

### 选择器

1. 通用选择器：通配符

2. 类型选择器

3. 类选择器

4. id选择器

5. 关系选择器

   + 子选择器：tr>tb (应用于tr后直接的tb元素)，嫡长袭位
   + 后代选择器： tr tb，（所有）子承父业
   + 相邻兄弟选择器：h1+p（必先拥有一个共同的父元素，只会选择最相近的兄弟）
   + 一般兄弟选择器：h1~p（条件同上，但他会选择所有的兄弟）

6. 特性选择器

   + 存在选择器：p[id]（带有某特性的某元素）
   + 相等选择器：p[id="name"] （带有某特性为某的某元素）
   + 空格选择器：p[class~="name"]（带有某特性为多个值，值与值之间用空格间隔，之中的某个值的某元素）
   + 连字号选择器：div[language|="en"]（带有language特性且以en开头并其后带有连字符的div元素）
   + 前缀选择器：p[class^="p"]（以p开头的class属性的p元素）
   + 后缀选择器：p[class$="p"]
   + 子字符选择器：p[class*="p"]（属性中带有p字符的p元素）
   + 第n子元素选择器：p:nth-child(n)
   + 倒数第n个元素选择器：p:nth-last-child(n)
   + 第一同类型选择器：p:first-of-type
   + 最后同类型选择器：p:last-of-type
   + 第n同类型选择器：p:nth-of-type(n)
   + 倒数第n同类型选择器：p:nth-last-of-type(n)
   + 最后子元素选择器：plast-child
   + 唯一子元素选择器：p:only-child
   + 唯一同类型选择器：p:only-type
   + 空元素选择器：p:empty
   + 目标选择器：p:target
   + 激活禁用选择器：input:enabled|input:disabled
   + 选定选择器：input:checked
   + 非选择器：p:not(".class")

7. 伪类：

   + :focus
   + :active

8. 伪元素

   + ::before
   + ::after

   > 伪元素所创建的内容默认为行内元素，除非指定。
   >
   > 需要搭配content:"" 使用

### 盒子模型

```css
border
  border是一个联合属性，它包括border-style,border-color,border-width
  border-style的取值包括none，dotted，solid，dashed，double，groove，ridge，inset，outset，hiden
margin
padding
height
width
max-width
max-height
min-width
min-height
line-height
overflow:hidden,visible,scroll,auto,inherit
box-sizing:border-box,
```

### 文本

```css
   font：一个联合的属性
   font-family:最好使用多种同一类型的字型，作为备用显示
   font-size:可以使用的单位包括 px pt pc mm cm em % rem  in vw vh / xx-small x-small small medium large x-large xx-large / smaller larger /  
   font-weight:还可以出的值有bolder lighter ，以及100~900之内的整数
   font-style:
   font-variant:small-caps
   color：
   text-align：另外还有justify start end
   vertical-align：另外还有baseline(缺省) sub super text-top text-bottom/长度值 百分比值
   text-decoration：underline overline  line-through none
   text-indent：
   text-transform：capitalize uppercase lowercase none
   text-shadow：
   letter-spacing：
   word-spacing：
   white-spacing：pre nowrap normal
   direction：
```

   > 1.区分字型和字体：字体是字型某个具体成员
   >
   > 2.区分serif，sans-serif，monospace，cursive，fantasy字体使用场景

```css
   文本伪类：first-letter/first-line
```

### 链接

```css
伪类：
link
visited
hover
active
```

### 背景

```css
background：这是一个联合属性
background-color
background-image
background-repeat
background-position
background-attachment
```

> background-position的取值可以是left right center topbottom 以及x y（x轴和y轴的绝对长度）以及x% y%，另left center就等同于0 50%； center center（可简写为center ，第二个center值为默认值）=50% 50%
>
> background-attachment可取的值为fixed 和 scroll

### 列表

```css
list-style是一个联合属性：
  list-style-type
  list-style-image
  list-style-position：inside|outside
  marker-offset
```

> list-style-type: disc square circle  /  decimal decimal-leading-zero  /  lower-alpha|lower-latin upper-alpha|upper-latin  (roman greek .ect)  /  hiragana katakana

### 表格

```css
border-collapse：collapse|separate
border-spacing
caption-side：top|right|top|bottom
empty-cells：show|hide
table-layout:auto|fixed;
```

> 对于溢出的内容应当使用overflow属性

### 轮廓

```css
outline是一个联合属性：
  outline-style
  outline-width
  outline-color
```

### 其他属性

```css
cursor：auto|default|pointer|crosshair|move|text|wait|help|progress|<url>|e-resize(另外还可以是：ne|nw|n|se|sw|s|w)
display:inline|block|inline-block|table...
visible
```

### 额外规则

```css
@import
!important
```







#### content属性的使用

1. content的属性值：
   字符串
   url
   计属性数器
   open-quote/close-quote
   no-open-quote/no-close-quote

   

2.计数器其他属性

```html
<body>
<h1>lorem optium</h1>
<h2>lorem</h2>
<h2>lorem</h2>
<h2>lorem</h2>
<h1>lorem optium</h1>
<h2>lorem</h2>
<h2>lorem</h2>
<h2>lorem</h2>
</body>
```

```css
body{
  counter-reset:chapter;
  counter-reset:section;
}
h1:before{
  content:"chapter" counter(chapter)":";
}
h2:before{
  content:counter(chapter)"."counter(section)"";
}
h1{
  counter-increament:chapter;
  counter-reset:setion;//使用counter-reset在你需要开始计数的地方重置计数器
}
h2{
  counter-increament:section;//通过counter-increment指定计数器何时自增
}
```

## css布局

### position属性

```css
position:static|relative|absolute|fixed
top
left
bottom
right
z-index
```

### float属性

### clear属性



## css3

### 高级颜色可选方案

1.hsl

2.rgba

3.hsla

4.opacity（透明度设定）

### 圆角和阴影

```css
border-radius
box-shadow
```

### 多列布局模块

```css
column-count
column-gap
column-width
```

### 媒体查询

```css
@media screen and (max-width:){}
```

### 自定义字体

```css
@font-face {
  font-family: 'PT Serif';
  font-style: normal;
  font-weight: normal;
  src: local('PT Serif'), local('PTSerif-Regular'), url(./PT_Serif-Web-Regular.ttf);
}
```

### 变形（2D和3D）

### 动画和过渡

