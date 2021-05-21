---
title:  如何只用CSS做到完全居中
photo: 
 - "https://s2.ax1x.com/2019/05/16/Eb65Y8.png"
date: 2019-05-17 20:19:57
tags:
- Technology
- Website
- HTML
- CSS
- Margin
- Layout
- Center
categories:
- Technology
- Website
- CSS
location: 四川大學
description:  如何只用CSS做到完全居中
---
我们都知道 `margin:0 auto;` 的样式能让元素水平居中，而 `margin: auto;` 却不能做到垂直居中……直到现在。但是，请注意！想让元素绝对居中，只需要声明元素高度，并且附加以下样式，就可以做到：

```CSS
.Absolute-Center {  
    margin: auto;  
    position: absolute;  
    top: 0; 
    left: 0; 
    bottom: 0; 
    right: 0;
}
```

我并不是第一个发现这种方法的人（不过我还是敢把它叫做“完全居中”），它有可能是种非常普遍的技巧。但大多数介绍垂直居中的文章中并没有提到过这种方法。如果不是浏览[这篇文章](http://designshack.net/articles/css/how-to-center-anything-with-css)的评论，我甚至根本就不会发现这个办法。

上面那篇文章的评论栏中，Simon提供了一个[jsFiddle](http://jsfiddle.net/mBBJM/1/)的链接，其他的方法相比之下就相形见绌了。（Priit也在评论栏中提到了同样的方法）。深入研究了一番之后，我又用某些关键词找到了记载这种方法的三个网站：[站点一](http://www.vanseodesign.com/css/vertical-centering/)、[站点二](http://www.student.oulu.fi/~laurirai/www/css/middle/)、[站点三](http://blog.themeforest.net/tutorials/vertical-centering-with-css/)。

以前从未用过这种方法的我想试试，看看这种”完全居中”的方法到底有多么神奇。 好处：

+ 跨浏览器，兼容性好（无需hack，可兼顾IE8~IE10）
+ 无特殊标记，样式更精简
+ 自适应布局，可以使用百分比和最大最小高宽等样式
+ 居中时不考虑元素的padding值（也不需要使用box-sizing样式）
+ 布局块可以自由调节大小
+ img的图像也可以使用

同时注意：

+ 必须声明元素高度
+ 推荐设置overflow:auto;样式避免元素溢出，显示不正常的问题
+ 这种方法在Windows Phone上不起作用

浏览器支持：Chrome、Firefox、Safari、Mobile Safari、IE8-10。 “完全居中”经测试可以完美地应用在最新版本的Chrome、Firefox、Safari、Mobile Safari中，甚至也可以运行在IE8~IE10上

## 对照表

“完全居中”并不是本篇文章中唯一的选项。要做到垂直居中，还存在着其他方法，各有各的长处。采取什么样的方法，取决于你所支持的浏览器，以及现有标签的结构。下面这张对照表能够帮你选出最符合你需要的方法。

| 所用样式     | 支持的浏览器         | 是否 响应式 | 内容溢出后的样式 | resize:both        | 高度可变 | 主要缺陷                                    |
| ------------ | -------------------- | ----------- | ---------------- | ------------------ | -------- | ------------------------------------------- |
| Absolute     | 现代浏览器&IE8+      | 是          | 会导致容器溢出   | 是                 | 是*      | ‘可变高度’的特性不能跨浏览器                |
| 负margin值   | 所有                 | 否          | 带滚动条         | 大小改变后不再居中 | 否       | 不具有响应式特性，margin值必须经过手工计算  |
| Transform    | 现代浏览器&IE9+      | 是          | 会导致容器溢出   | 是                 | 是       | 妨碍渲染                                    |
| Table-Cell   | 现代浏览器&IE8+      | 是          | 撑开容器         | 否                 | 是       | 会加上多余的标记                            |
| Inline-Block | 现代浏览器&IE8+&IE7* | 是          | 撑开容器         | 否                 | 是       | 需要使用容器包裹和hack式的样式              |
| Flexbox      | 现代浏览器&IE10+     | 是          | 会导致容器溢出   | 是                 | 是       | 需要使用容器包裹和厂商前缀（vendor prefix） |

## 说明

在研究了规范和文档后，我总结出了“完全居中”的工作原理：

1. 在普通文档流里，margin: auto; 的意思是设置元素的margin-top和margin-bottom为0。

[W3.org](http://www.w3.org/TR/CSS2/visudet.html#normal-block):?If ‘margin-top’, or ‘margin-bottom’ are ‘auto’, their used value is 0.

\2. 设置了position: absolute; 的元素会变成块元素，并脱离普通文档流。而文档的其余部分照常渲染，元素像是不在原来的位置一样。 [Developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/CSS/position#Absolute_positioning):?…an element that is positioned absolutely is taken out of the flow and thus takes up no space

\3. 设置了top: 0; left: 0; bottom: 0; right: 0; 样式的块元素会让浏览器为它包裹一层新的盒子，因此这个元素会填满它相对父元素的内部空间，这个相对父元素可以是是body标签，或者是一个设置了position: relative; 样式的容器。 [Developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/CSS/position#Notes):?For absolutely positioned elements, the top, right, bottom, and left properties specify offsets from the edge of the element’s containing block (what the element is positioned relative to).

\4. 给元素设置了宽高以后，浏览器会阻止元素填满所有的空间，根据margin: auto; 的要求，重新计算，并包裹一层新的盒子。 [Developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/CSS/position#Notes):?The margin of the [absolutely positioned] element is then positioned inside these offsets.

\5. 既然块元素是绝对定位的，又脱离了普通文档流，因此浏览器在包裹盒子之前会给margin-top和margin-bottom设置一个相等的值。 [W3.org](http://www.w3.org/TR/CSS2/visudet.html#abs-non-replaced-height):?If none of the three [top, bottom, height] are ‘auto’: If both ‘margin-top’ and ‘margin-bottom’ are ‘auto’, solve the equation under the extra constraint that the two margins get equal values.?AKA: center the block vertically

使用“完全居中”，有意遵照了标准margin: auto; 样式渲染的规定，所以应当在与标准兼容的各种浏览器中起作用。

## 对齐

### 容器内对齐

使用“完全居中”，就可以在一个设置了position: relative的容器中做到完全居中元素了！ [（居中例子，请前往英文原文查看）](http://codepen.io/shshaw/full/gEiDt)

```CSS
.Center-Container {  
    position: relative;
} 
.Absolute-Center {  
    width: 50%;  
    height: 50%;  
    overflow: auto;  
    margin: auto;  
    position: absolute;  
    top: 0; 
    left: 0; 
    bottom: 0; 
    right: 0;
}
```

![img](http://ww2.sinaimg.cn/large/7cc829d3gw1e8dtm5q14rj20gu0b4jrr.jpg)

接下来的示例会假设已经包含了以下样式，并且以逐步添加样式的方式提供不同的特性。

### 在可视区域内居中

想要使内容区在可视区域内居中么？设置position: fixed样式，并设置一个较高的z-index值，就可以做到。

```CSS
.Absolute-Center.is-Fixed {  position: fixed;  z-index: 999;}
```

![img](http://ww2.sinaimg.cn/large/7cc829d3gw1e8dtm67yllj20ad082dg4.jpg)

**移动版Safari****的说明**：如果外面没有一层设置position: relative的容器，内容区会以整个文档的高度的中心点为基准居中，而不是以可视区域的高度中心点为基准居中。

### 偏移值

如果需要添加固定的标题，或者其他带偏移样式的元素，可以直接把类似top: 70px; 的样式写进内容区域的样式中。一旦声明了margin: auto; 的样式，内容块的`top ``left ``bottom ``right`的属性值也会同时计算进去。

如果想让内容块在贴近侧边的过程中保持水平居中，可以使用right: 0; left: auto; 让内容贴在右侧，或者使用left: 0; right: auto; 使内容贴在左侧。

```CSS
.Absolute-Center.is-Fixed {  position: fixed;  z-index: 999;}
```

![img](http://ww1.sinaimg.cn/large/7cc829d3gw1e8dtm8nu2ej20gw0b50t1.jpg)

### 带响应式

使用absolute的最大好处就是可以完美地使用带百分比的宽高样式！就算是min-width/max-width或者min-height/max-height也能够有如预期般的表现。

再进一步加上padding样式的话，absolute式的完全居中也丝毫不会破坏！

```CSS
.Absolute-Center.is-Responsive {  width: 60%;   height: 60%;  min-width: 200px;  max-width: 400px;  padding: 40px;}
```

![img](http://ww4.sinaimg.cn/large/7cc829d3gw1e8dtmbxviuj20gw0b6jrw.jpg)

### 带溢出内容

内容区高度大于可视区域或者一个position: relative的容器，其内容可能会溢出容器，或被容器截断。只要内容区域没有超出容器（没有给内容容器预留padding的话，可以设置max-height: 100%;的样式），那么容器内就会产生滚动条。

```CSS
.Absolute-Center.is-Overflow {  overflow: auto;}
```

![img](http://ww4.sinaimg.cn/large/7cc829d3gw1e8dtmcpu5uj20gw0b63zg.jpg)

### 大小可调整

使用其他样式，或者使用JavaScript调整内容区的大小，也是不用手动重新计算的！如果设置了resize的样式，甚至可以让用户自行调节内容区域的大小。 “完全居中”法，无论内容区怎么改变大小，都会保持居中。

设置了min-/max- 开头的属性可以限制区块的大小而不用担心撑开容器。

```CSS
8.Absolute-Center.is-Resizable {  min-width: 20%;  max-width: 80%;  min-height: 20%;  max-height: 80%;  resize: both;  overflow: auto;}
```

![img](http://ww4.sinaimg.cn/large/7cc829d3gw1e8dtmdawehj20gw0b4aai.jpg)

如果不设置resize: both的样式，可以设置transition样式平滑地在大小间切换。一定要记得设置overflow: auto样式，因为改变大小后的容器高宽很有可能会小于内容的高宽。 “完全居中”法是唯一一种能支持使用resize: both样式的方法。

使用注意：

+ 需要设置max-width/max-height给内容区域留足够的空间，不然就有可能使容器溢出。
+ resize属性不支持移动版浏览器和IE8-10，如果用户体验很重要的话，请确保用户可以有其他替代方法来改变大小。
+ 同时使用resize样式和transition会使用户在开始改变大小时产生等于transition效果时间等长的延时。

### 图像

图像也同样有效！提供相应的class，并指定样式 height: auto; ，就得到了一张随着容器改变大小的响应式图片。

![img](http://ww3.sinaimg.cn/large/7cc829d3gw1e8dtmekxnpj20gv0b5t8x.jpg)

请注意，height: auto; 样式虽然对图片有效，如果没有用到了后面介绍的‘可变高技巧’，则会导致普通内容区域伸长以适应容器长度。

浏览器很有可能是根据渲染结果填充了图像高度值，所以在测试过的浏览器中，margin: auto; 样式就像是声明了固定的高度值一般正常工作。

<img src="http://placekitten.com/g/500/200" alt="" />

```CSS
.Absolute-Center.is-Image {  height: auto;} .Absolute-Center.is-Image img {   width: 100%;  height: auto;} 
```

### 可变高度

“完全居中”法的确需要声明容器高度，但是高度受max-height样式的影响，也可以是百分比。这非常适合响应式的方案，只需要设置好带溢出内容就行。

![img](http://ww3.sinaimg.cn/large/7cc829d3gw1e8du1cpkopj20gt0b4jro.jpg)

另一种替代方案是设置display: table样式居中，，不管内容的长度。这种方法会在一些浏览器中产生问题（主要是IE和Firefox）。我在ELL Creative的朋友Kalley写了一个基于Modernizr 的测试，可以用来检查浏览器是否支持这种居中方案。现在这种方法可以做到渐进增强。

注意要点： 这种方法会破坏浏览器兼容性，如果Modernizr测试不能满足你的需求，你可能需要考虑其他的实现方案。

+ 与大小可调整技术是不兼容的
+ **Firefox/IE8**中使用display: table，内容区在垂直方向靠上，水平方向仍然居中。
+ **IE9/10**中使用display: table，内容区会跑到左上角。
+ **移动版****Safari**中内容区是水平对齐的，但是如果使用了百分比的宽度，水平方向上会稍稍偏离中心。

```CSS
\* Modernizr Test for Variable Height Content \*/*Modernizr.testStyles('#modernizr { display: table; height: 50px; width: 50px; margin: auto; position: absolute; top: 0; left: 0; bottom: 0; right: 0; }', function(elem, rule) {  Modernizr.addTest('absolutecentercontent', Math.round(window.innerHeight / 2 - 25) === elem.offsetTop);});
.absolutecentercontent .Absolute-Center.is-Variable {  display: table;  height: auto;} 
```

## 其他方法

“完全居中”法是解决居中问题的好方法，同时也有许多可以满足不同需求的其他方法。最常见的，推荐的方法有负margin值、transform法、table-cell法、inline-block法、以及现在出现的Flexbox法，这些方法其他文章都有深入介绍，所以这里只会稍稍提及。

### 负margin值

这或许是最常用的方法。如果知道了各个元素的大小，设置等于宽高一半大小的负margin值（如果没有使用box-sizing: border-box样式，还需要加上padding值），再配合top: 50%; left: 50%;样式就会使块元素居中。

![img](http://ww4.sinaimg.cn/large/7cc829d3gw1e8du1d8ll3j20gv0b3glt.jpg)

需要注意的是，这是按照预想情况也能在工作在IE6-7下的唯一方法。

```CSS
.is-Negative {        width: 300px;        height: 200px;        padding: 20px;        position: absolute;        top: 50%; left: 50%;        margin-left: -170px; */\* (width + padding)/2 \*/*        margin-top: -120px; */\* (height + padding)/2 \*/*}
```

好处：

+ 浏览器兼容性非常好，甚至支持IE6-7
+ 需要的编码量很少

同时注意：

+ 这是个非响应式的方法，不能使用百分比的大小，也不能设置min-/max-的最大值最小值。
+ 内容可能会超出容器
+ 需要为padding预留空间，或者需要使用box-sizing: border-box样式。

### transform法

和“完全居中”法的好处一样，简单有效，同时支持可变高度。为内容指定带有厂商前缀的transform: translate(-50%,-50%)和top: 50%; left: 50%;样式就可以让内容块居中。

```CSS
.is-Transformed {   width: 50%;  margin: auto;  position: absolute;  top: 50%; left: 50%;  -webkit-transform: translate(-50%,-50%);      -ms-transform: translate(-50%,-50%);          transform: translate(-50%,-50%);}
```

![img](http://ww2.sinaimg.cn/large/7cc829d3gw1e8du1dt1xfj20gw0b5aae.jpg)

好处：

+ 内容高度可变
+ 代码量小

同时注意：

+ 不支持IE8
+ 需要写厂商前缀
+ 会和其他transform样式有冲突
+ 某些情况下的边缘和字体渲染会有问题

### table-cell法

这种可能是最好的方法，因为高度可以随内容改变，浏览器支持也不差。主要缺陷是会产生额外的标签，每一个需要居中的元素需要三个额外的HTML标签。

![img](http://ww2.sinaimg.cn/large/7cc829d3gw1e8du1eg5cgj20gw0b53yx.jpg)

```css
.Center-Container.is-Table { display: table; }.is-Table .Table-Cell {  display: table-cell;  vertical-align: middle;}.is-Table .Center-Block {  width: 50%;  margin: 0 auto;}
```

好处：

+ 内容高度可变
+ 内容溢出则能自动撑开父元素高度
+ 浏览器兼容性好

同时注意：

+ 需要额外的HTML标签

### 

### inline-block法

迫切需要的方法：inline-block法居中。基本方法是使用 `display: inline-block`, `vertical-align: middle`样式和伪元素让内容块在容器中居中。我的实现用到了几个在其他地方见不到的新技巧解决了一些问题。

内容区声明的宽度不能大于容器的100% 减去0.25em的宽度。就像一段带有长文本的区域。不然，内容区域会被推到顶端，这就是使用:after伪类的原因。使用:before伪类则会让元素有100%的大小！

![img](http://ww2.sinaimg.cn/large/7cc829d3gw1e8du1f7o33j20gv0b5glz.jpg)

如果内容块需要尽可能大地占用水平空间，可以为大容器加上max-width: 99%;样式，或者考虑浏览器和容器宽度的情况下使用max-width: calc(100% – 0.25em) 样式。

这种方法和table-cell的大多数好处相同，不过最初我放弃了这个方法，因为它更像是hack。不管这一点的话，浏览器支持很不错，而且也被证实是很流行的方法。

**HTML:**















XHTML



| 12345 | **<div** class="Center-Container is-Inline"**>**  **<div** class="Center-Block"**>**    *<!-- CONTENT -->*  **</div>****</div>** |
| ----- | ------------------------------------------------------------ |
|       |                                                              |



**CSS:**

















CSS



| 123456789101112131415161718192021 | .Center-Container.is-Inline {   text-align: center;  overflow: auto;} .Center-Container.is-Inline:after,.is-Inline .Center-Block {  display: inline-block;  vertical-align: middle;} .Center-Container.is-Inline:after {  content: '';  height: 100%;  margin-left: -0.25em; */\* To offset spacing. May vary by font \*/*} .is-Inline .Center-Block {  max-width: 99%; */\* Prevents issues with long content causes the content block to be pushed to the top \*/*  */\* max-width: calc(100% - 0.25em) /\* Only for IE9+ \*/* } |
| --------------------------------- | ------------------------------------------------------------ |
|                                   |                                                              |

好处：

+ 内容高度可变
+ 内容溢出则能自动撑开父元素高度
+ 浏览器兼容性好，甚至可以调整支持IE7

同时注意：

+ 需要额外容器
+ 依赖于margin-left: -0.25em的样式，做到水平居中，需要为不同的字体大小作调整
+ 内容区声明的宽度不能大于容器的100% 减去0.25em的宽度

 

### Flexbox法

CSS未来发展的方向就是采用Flexbox这种设计，解决像垂直居中这种共同的问题。请注意，Flexbox有不止一种办法居中，他也可以用来分栏，并解决奇奇怪怪的布局问题。

![img](http://ww2.sinaimg.cn/large/7cc829d3gw1e8du699aqwj20gu0b3weo.jpg)

```html
<div class="Center-Container is-Table">  <div class="Table-Cell">    <div class="Center-Block">    <!-- CONTENT -->    </div>  </div></div>
```

```css
.Center-Container.is-Flexbox {  display: -webkit-box;  display: -moz-box;  display: -ms-flexbox;  display: -webkit-flex;  display: flex;  -webkit-box-align: center;     -moz-box-align: center;     -ms-flex-align: center;  -webkit-align-items: center;          align-items: center;  -webkit-box-pack: center;     -moz-box-pack: center;     -ms-flex-pack: center;  -webkit-justify-content: center;          justify-content: center;}
```

好处：

+ 内容可以是任意高宽，溢出也能表现良好
+ 可以用于各种高级布局技巧

同时注意： 不支持IE8-9

+ 需要在body上写样式，或者需要额外容器
+ 需要各种厂商前缀兼容现代浏览器
+ 可能有潜在的性能问题

## 最后的建议

各项技术都有各自的好处，采取什么样的方法，取决于你所支持的浏览器，以及现有标签的结构。请使用上面提供对照表帮你选出最符合你需要的方法。

“完全居中”法简单方便，迅速及时。以前使用负Margin值的地方，都可以使用Absolute居中。无需繁琐的数学计算，无需额外标签，而且可以随时改变大小。

如果网站需要可变高度的内容，而且同时照顾到浏览器兼容性的话，可以尝试table-cell和inline-block技术，如果想尝试新鲜事物的话，可以使用Flexbox，并享受这种高级技术带来的好处。