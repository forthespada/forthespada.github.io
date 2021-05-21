---
title: 前端基础——CSS（二）

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
---

## css validate

对于CSS的校验可能不如HTML校验或者JavaScript校验那么重要，不过在正式发布之前用Lint工具校验一波你的CSS代码还是很有意义的。它会告诉你代码中潜在的错误，提示你一些不符合最佳实践的代码以及给你一些提升代码性能的建议。就像Minifers与Autoprefixers，也有很多可用的工具:

+ Online tools: W3 Validator, CSS Lint
+ Text editor plugins: Sublime Text, Atom
+ Libraries: stylelint (Node.js, PostCSS), css-validator (Node.js)

## table属性

### 属性介绍

|        属性        |            渲染            |
| :----------------: | :------------------------: |
|       table        |  使该元素按table样式渲染   |
|     table-row      |    使该元素按tr样式渲染    |
|     table-cell     |    使该元素按td样式渲染    |
|  table-row-group   |  使该元素按tbody样式渲染   |
| table-header-group |  使该元素按thead样式渲染   |
| table-footer-group |  使该元素按tfoot样式渲染   |
|   table-caption    | 使该元素按caption样式渲染  |
|    table-column    |   使该元素按col样式渲染    |
| table-column-group | 使该元素按colgroup样式渲染 |

> CSS2.1表格模型中的元素，可能不会全部包含在除HTML之外的文档语言中。这时，那些“丢失”的元素会被模拟出来，从而使得表格模型能够正常工作。所有的表格元素将会自动在自身周围生成所需的匿名table对象，使其符合table/inline-table、table-row、table-cell的三层嵌套关系。

上面这句话的意思是：我们可以在缺失` display：table ` 和` display：table-row` 的情况下，设定某个` div` 或其他**容器**为` display：table-cell`。

> 例如我们可以在如下书写：
>
> ```html
> <div class=”container”>
> <div class=”row”>
> <div class=”cell”>CELL A</div>
> <div class=”cell”>CELL B</div>
> <div class=”cell”>CELL C</div>
> </div>
> </div>
> ```
>
> 也可以如此书写：
>
> ```html
>  <div class=”row”>
>  <div class=”cell”>CELL A</div>
>  <div class=”cell”>CELL B</div>
>  <div class=”cell”>CELL C</div>
>  </div>
> ```
>
> 更可以如下书写：
>
> ```html
>  <div class=”cell”>CELL A</div>
>  <div class=”cell”>CELL B</div>
>  <div class=”cell”>CELL C</div>
> ```

很显然第三种代码写法可以省略很多的字符。

### table-cell

#### 元素两端对齐

	除了使用`float：left`和`float：right`之外，还可以使用以下办法：

> 该方法是创建了一个表格和两个tr、或者说两个td，令tr或td不显示外边框，在其内部创建两个容器，分别是这两个容器向左右移动，可参见一下链接：[点这里](/home/allen/文档/WEBS/css的应用/table元素的使用/table元素的使用.html)

```html
div.container+div.left>div.box^div.right+div.box
```

```css
.container {
    display: table;        /*important*/
    border: 1px solid #06c;
    padding: 15px 5px;
    max-width: 1000px;
    margin: 10px auto;
    min-width: 320px;
    width: 100%;
}
.box {
    width: 100px;
    height: 100px;
    border: 1px solid #ccc;
    text-align: center;
    display: inline-block;/*important*/
    font-size: 40px;
    line-height: 100px;
}
.right {
    text-align: right;
    display: table-cell
      }
.left{
   text-align:left;
   display:table-cell;
}
```

#### 自动平均划分每个小模块，使其一行显示

除了使用`float`之外，还可以使用`inline-block`

```html
div.container>ul>li{$}*5
```

```css
* {
    box-sizing: border-box;
}

.container {
    display: table;
    border: 1px solid #06c;
    padding: 15px 5px;
    max-width: 1000px;
    margin: 10px auto;
    min-width: 320px;
    width: 100%;
}
.container ul {
    display: table;
    width: 100%;
    padding: 0;
    border-right: 1px solid #ccc;
}

.container ul li {
    display: table-cell;
    border: 1px solid #ccc;
    text-align: center;
    height: 100px;
    border-right: none;
    line-height: 100px;
}
```

#### 图片垂直居中于元素

```html
div.container>div.img-box
```

```css
* {
    box-sizing: border-box;
}

.container{
    display: table;
    border: 1px solid #06c;
    padding: 15px 5px;
    max-width: 1000px;
    margin: 10px auto;
    min-width: 320px;
    width: 100%;
}
.img-box{
    height: 150px;
    width: 100px;
    border:1px solid red;
    display: table-cell;
    vertical-align: middle;
    text-align: center;
    background-color:#4679bd;
}
```

#### 两box实现等高对齐

```html
div.content>div.img-box>img^div.text-box>span{lorem100}
```

```css
* {
    box-sizing: border-box;
}
.content {
    display: table;
    border: 1px solid #06c;
    padding: 15px 5px;
    max-width: 1000px;
    margin: 10px auto;
    min-width: 320px;
    width: 100%;
}
.img-box{
    width: 100px;
    border:1px solid red;
    display: table-cell;
    vertical-align: middle;
    text-align: center;
    background-color:#4679bd;
}
.text-box{
    margin-left: 20px;
    border: 1px solid #ddd;
    padding: 10px;
}
```

#### 弹性、响应式布局

上面的demo中大家只要改变浏览器宽度就会发现他们其实都是会随高度变化自动变化高度的，其实上面内容我大部分没有设置绝对单位，即使设置了也只设置其中一个box另一个就让他去自适应父元素的剩余留下来的宽度，其实布局的时候设置宽度是一件很痛苦的事情，因为除了大量计算有时候可能在多浏览器下还算不准，可能你在chrome设好的宽度在ie下就坑爹了，要写hack才能解决。
	
移动端布局因为有display:box这等属性，所以table-cell相对就排不上什么大用场，不过在移动端你要用table-cell也不是不可以，根据自己对属性的理解去使用就可以了。

```html
div.content>duv.left-box>img^div.right-box>span{lorem100}
```

```css
* {
    box-sizing: border-box;
}
.content {
    display: table;
    border: 1px solid #06c;
    padding: 15px 5px;
    max-width: 1000px;
    margin: 10px auto;
    min-width: 320px;
    width: 100%;
}
.left-box {
    float:left;
    margin-right: 10px;
    padding-top:5px;
}

.right-box {
    display: table-cell;
    padding: 10px;
    border: 1px solid #ccc;
    margin-right: 10px;
    vertical-align: top;
}
```

## CSS Fallback

目前IE在国内的份额仍然非常高（可以看百度统计分析，或CNZZ），尤其是IE6这样远古的浏览器仍然占据市场份额的第一位。从IE8开始支持web标准，但是IE8只能支持到CSS2，IE9支持部分的CSS3，border-radius是不支持的。从市场份额考虑，一般不建议用圆角这样的属性，目前最适用的仍然是图片替代法。另外还有雅黑字体一般也不建议用，因为XP仍然占据大部分市场份额，XP上好像几乎都没有雅黑。

+ IE6并不支持CSS固定定位(POSITION:fixed;),

+ ie6，ie7 不支持负边距，采用负边距会导致异常显示

+ IE6/7浏览器并不支持 before after伪元素

+ ie6不支持!important

   如我们想在ie8,firefox,chrome等高端浏览器下设置字体为14个像素，ie6为12个像素，那么css就这样写

```css
text{font-size:14px!important;font-size:12px;}
```

   或者说高端浏览器中使用透明的png图片，而ie6本身不支持透明图片，只能使用gif,所以css中这样

```css
test{background:("a.png") no-repeat!important;background:url(ie6.gif) no-repeat}
```

+ ie6-ie9 不支持svg。。。。

+ ie6-ie9不支持 rgba。。。。。。

ie10是比较标准的东西，IE10支持最新的Web标准,包括对现在的行业标准HTML5、CSS3、SVG、ECMAScript5.1的支持

ie的的z-index很诡异，貌似不支持继承。要研究看看
http://www.cnblogs.com/Darren_code/archive/2012/03/05/z-index.html

mdia query 在ie8以及其之下 无法工作

http://kayosite.com/css3-rgba-color.html
http://www.dabaoku.com/jiaocheng/wangye/css/2012050113369.shtml

## css居中

推荐网址：http://blog.jobbole.com/46574/

### 内联元素的居中

1.水平居中

+ text-align：center；

  > 只能对*行内元素*(display为inline或inline-block等)进行水平居中。但要说明的是在*IE6、7浏览器*中，它是能对任何元素进行水平居中的。


+ display：flex/justify-content/center；（三选一，灵活运用）

2.垂直居中

+    单行文本：height=line-height；
+    多行文本： 
            1.使用TABLE元素，之后设置为vertical-align：middle；
            2.设置display：table-cell，在设置vertical-align：middle

     > 但是，这种方法只能在*IE8+、谷歌、火狐*等浏览器上使用，*IE6、IE7*都无效。即便父级overflow：hidden,随着文本的增加，溢出的文本依旧不会隐藏，适用于少文字或者静态文字。

### 块级元素的居中

1.水平居中

+ margin： pixel auto；（pixel可以为0）（定宽块状元素）
+ 绝对定位进行居中的原理是通过把这个绝对定位元素的left或top的属性设为50%，~~~这个时候元素并不是居中的，而是比居中的位置向右或向左偏了这个元素宽度或高度的一半的距离，~~~所以需要使用一个负的margin-left或margin-top的值来把它拉回到居中的位置，这个负的margin值就取元素宽度或高度的一半。[代码实例](http://images.cnitblog.com/blog/130623/201310/28171708-266c44999e164e9f9e1e3efeeb736a87.png)(已知宽度和高度)
+ 绝对定位2--[推荐](#abosolute-position)


2.垂直居中

+ 例一：

  ```css
  .box{
  position:absolute;/*或fixed*/
  top:50%;
  left:50%;
  margin-top:-100px;
  margin-left:-200px;}
  ```

+ 例二：

  ```css
  .box{
      position: absolute;或fixed
      top:0;
      right:0;
      bottom:0;
      left:0;
      margin: auto;}
  ```

+ display：table-cell之后设定vertical-align：middle

+ 例四：

  ```css
  .box{
      position: absolute;
      top:50%;
      left:50%;
      transform: translate(-50%,-50%);
      -webkit-transform:translate(-50%,-50%);
      -moz-transform:translate(-50%,-50%);
      -ms-transform:translate(-50%,-50%);}
  ```

+ 例五：

  ```html
  <div class='box'>
  	<div class='content'>垂直居中</div>
  </div>
  ```

  ```css
  .box{
    position:fixed;
    display:block;
    background:rgba(0,0,0,.5);}
  .box:before{
    content:'';
    display:inline-block;
    vertical-align:middle;
    height:100%;}
  .box:after{
    content:'';
    display:inline-block;
    vertical-align:middle;
    height:100%;}
  .box .content{
    width:60px;
    height:60px;
    line-height:60px;
    color:red;} 
  ```
  6.Flex布局;
  ```css
  .box{
    display: -webkit-box;
    display: -webkit-flex;
    display: -moz-box;
    display: -moz-flex;
    display: -ms-flexbox;
    display: flex;
    水平居中
    -webkit-box-align: center;
    -moz-box-align: center;
    -ms-flex-pack:center;
    -webkit-justify-content: center;
    -moz-justify-content: center;
    justify-content: center;
     垂直居中
    -webkit-box-pack: center;
    -moz-box-pack: center;
    -ms-flex-align:center;
    -webkit-align-items: center;
    -moz-align-items: center;
    align-items: center;}
  ```

***

<span id="abosolute-position">绝对定位2--推荐</span>

此法同样只适用于那些我们已经知道它们的宽度或高度的元素，并且它只支持IE9+,谷歌，火狐等符合w3c标准的现代浏览器。 “完全居中”法是唯一一种能支持使用resize: both样式的方法。

下面用一段代码来了解这种方法：[Code resource](http://images.cnitblog.com/blog/130623/201310/28171710-5b31367eba804b19b0a5170f94ba75bc.png)

这里如果不定义元素的宽和高的话，那么他的宽就会由left,right的值来决定，高会由top,bottom的值来决定，所以必须要设置元素的高和宽。同时如果改变left，right , top , bottom的值还能让元素向某个方向偏移，大家可以自己去尝试。 

1.优点

+ 跨浏览器，兼容性好（无需hack，可兼顾IE8~IE10）
+ 无特殊标记，样式更精简
+ 自适应布局，可以使用百分比和最大最小高宽等样式
+ 居中时不考虑元素的padding值（也不需要使用box-sizing样式）
+ 布局块可以自由调节大小
+ img的图像也可以使用

2.注意

+ 必须声明元素高度
+ 推荐设置overflow:auto;样式避免元素溢出，显示不正常的问题
+ 这种方法在Windows Phone上不起作用

***

Float+position:relative

此方法也是关于浮动元素水平居中的解决方法，并且我们不需要知道需要居中的元素的宽度。缺点是需要一个多余的元素来包裹要居中的元素。
	
浮动居中的原理是：把浮动元素相对定位到父元素宽度50%的地方，但这个时候元素还不是居中的，而是比居中的那个位置多出了自身一半的宽度，这时就需要他里面的子元素再用一个相对定位，把那多出的自身一半的宽度拉回来，而因为相对定位正是相对于自身来定位的，所以自身一半的宽度只要把left 或 right 设为50%就可以得到了，因而不用知道自身的实际宽度是多少。
	
看下代码：[Code resource](http://images.cnitblog.com/blog/130623/201310/28171711-a28d15febf2a4adaabb5e0861ffe650e.png)

***

Font-size

如果父元素高度是已知的，要把它里面的子元素进行水平垂直居中，则可以使用这种方法，且子元素的宽度或高度都不必知道。该方法只对IE6和IE7有效。
	
该方法的要点是给父元素设一个合适的font-size的值，这个值的取值为该父元素的高度除以1.14得到的值，并且子元素必须 是一个inline或inline-block元素，需要加上vertical-align:middle属性。

[	Code resource](http://images.cnitblog.com/blog/130623/201310/28171713-3f7f8bf7e29442a68b55426c130a6e18.png)

上面的例子中因为要居中的元素是一个块状元素，所以我们还需要把他变成行内元素，如果要居中的元素是图片等行内元素，则可以省略此步。另外，如果 vertical-align:middle 是写在父元素中而不是子元素中，这样也是可以的，只不过计算font-size时使用的  1.14 这个 数值要变成大约 1.5 这个值。
	
在方法5中说过在IE8+、火狐谷歌等现在浏览器中可以用*display:table-cell*来进行居中，而这里的*font-size*的方法则适用于IE6和IE7，所以*把这两种方法结合起来就能兼容所有浏览器了*：

[	Code resource](http://images.cnitblog.com/blog/130623/201310/28171714-dc6838c0b518438cbc81dbeccb8c86e6.png)

***

Display:flex

还不会使用这种方法，似乎是比较新的。

***

Calc

同上，不会使用。

***

垂直居中行内元素

```html
	</html>
	<meta charset="UTF-8">
	<title>Document</title>
		<style>
    #wrapper{
        width: 800px;
        height: 800px;
        background: gray;
        text-align: center;
    }
 
    #wrapper img{
        vertical-align: middle;
    }
         
    #wrapper #block{
        background: blue;
        height: 100%;
        width: 0;
 
    }
	</style>
	</head>
	<body>
		<div id="wrapper">
 		 <img src="http://img0.bdstatic.com/img/image/2016ss1.jpg" alt="">
		<img  id="block">
		</div>
	</body>
	</html>
```

这里的多了一个空的<img>标签，为什么要这样的，首先，要搞清楚vertical-align这个属性的特点，它是相对兄弟级行高（line-height）来定位，并且他仅对行内元素有效，所以，在要定位的元素后面加多一个行内元素img来撑开父级的行高，以此来居中。然后必须强调一点，记得把后面img的src=""这个空属性去掉，不然会留下一个空白框。也可以用其他行内元素,效果是一样的,在这里不可以用line-height:100%这样来设置行高.

| 所用样式    | 支持的浏览器     | 是否 响应式 | 内容溢出后的样式 | resize:both        | 高度可变 | 主要缺陷                                    |
| ----------- | ---------------- | ----------- | ---------------- | ------------------ | -------- | ------------------------------------------- |
| Absolute    | 现代浏览器&IE8+  | 是          | 会导致容器溢出   | 是                 | 是       | ‘可变高度’的特性不能跨浏览器                |
| Transform   | 现代浏览器&IE9+  | 是          | 会导致容器溢出   | 是                 | 是       | 妨碍渲染                                    |
| Table-Cell  | 现代浏览器&IE8+  | 是          | 撑开容器         | 否                 | 是       | 会加上多余的标记                            |
| nline-Block | 现代浏览器&IE7+  | 是          | 撑开容器         | 否                 | 是       | 需要使用容器包裹和hack式的样式              |
| Flexbox     | 现代浏览器&IE10+ | 是          | 会导致容器溢出   | 是                 | 是       | 需要使用容器包裹和厂商前缀（vendor prefix） |
| 负margin值  | 所有             | 否          | 带滚动条         | 大小改变后不再居中 | 否       | 不具有响应式特性，margin值必须经过手工计算  |



## 清除浮动Clearfix

 <span id="clearfix">链至css</span>

1.使用带clear属性的空元素

在浮动元素后使用一个空元素如`<div class="clear"></div>`
，并在CSS中赋予`.clear{clear:both;}`属性即可清理浮动。亦可使用`<br class="clear" />或<hr class="clear" />`来进行清理。

+ 优点：简单，代码少，浏览器兼容性好。
+ 缺点：需要添加大量无语义的html元素，代码不够优雅，后期不容易维护。

2.使用CSS的overflow属性

给浮动元素的容器添加`overflow:hidden;`或`overflow:auto;`可以清除浮动，另外在 IE6 中还需要触发`hasLayout`，例如为父元素设置容器宽高或设置`zoom:1`。在添加`overflow`属性后，浮动元素又回到了容器层，把容器高度撑起，达到了清理浮动的效果。

3.给浮动的元素的容器添加浮动

给浮动元素的容器也添加上浮动属性即可清除内部浮动，但是这样会使其整体浮动，影响布局，不推荐使用。

4.使用邻接元素处理

什么都不做，给浮动元素后面的元素添加clear属性。
```html+css
.news {
  background-color: gray;
  border: solid 1px black;
  }
.news img {
  float: left;
  }
.news p {
  float: right;
  }
.content{
  clear: both;
  }
<div class="news">
<img src="news-pic.jpg" />
<p>some text</p>
<div class="content">***</div>
</div>
```
注意这里的div.content有内容。

5.使用CSS的:after伪元素

结合 :after 伪元素（注意这不是伪类，而是伪元素，代表一个元素之后最近的元素）和 IEhack ，可以完美兼容当前主流的各大浏览器，这里的 IEhack 指的是触发 hasLayout。
给浮动元素的容器添加一个clearfix的class，然后给这个class添加一个:after伪元素实现元素末尾添加一个看不见的块元素（Block element）清理浮动。
```html+css
.news {
  background-color: gray;
  border: solid 1px black;
  }
.news img {
  float: left;
  }
.news p {
  float: right;
  }
.clearfix: after{
  content: "020";
  display: block;
  height: 0;
  clear: both;
  visibility: hidden;  
  }
.clearfix {
  /* 触发 hasLayout */
  zoom: 1;
  }
<div class="news clearfix">
<img src="news-pic.jpg" />
<p>some text</p>
</div>
```
通过CSS伪元素在容器的内部元素最后添加了一个看不见的空格”020”或点”.”，并且赋予clear属性来清除浮动。需要注意的是为了IE6和IE7浏览器，要给clearfix这个class添加一条`zoom:1`;触发haslayout。

总结

通过上面的例子，我们不难发现清除浮动的方法可以分成两类：

一是利用 clear 属性，包括在浮动元素末尾添加一个带有 clear: both 属性的空 div 来闭合元素，其实利用 :after 伪元素的方法也是在元素末尾添加一个内容为一个点并带有 clear: both 属性的元素实现的。

二是触发浮动元素父元素的 BFC (Block Formatting Contexts, 块级格式化上下文)，使到该父元素可以包含浮动元素，关于这一点。

在网页主要布局时使用:after伪元素方法并作为主要清理浮动方式；在小模块如ul里使用`overflow:hidden`;（留意可能产生的隐藏溢出元素问题）；如果本身就是浮动元素则可自动清除内部浮动，无需格外处理；正文中使用邻接元素清理之前的浮动。

最后可以使用相对完美的:after伪元素方法清理浮动，文档结构更加清晰。