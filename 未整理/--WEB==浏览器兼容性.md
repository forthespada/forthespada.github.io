## div的垂直居中问题

vertical-align:middle; 将行距增加到和整个DIV一样高 line-height:200px; 然后插入文字，就垂直居中了。缺点是要控制内容不要换行 

## margin加倍的问题

设置为float的div在ie下设置的margin会加倍。这是一个ie6都存在的bug。解决方案是在这个div里面加上display:inline; 
例如：
```css
<#div id=”imfloat”> 
imFloat{float:left;
  		margin:5px;/*IE下理解为10px*/
  		display:inline;/*IE下再理解为5px*/}   
```

## ie产生的双倍距离

```css
.box{float:left;
  width:100px; 
  margin:0 0 0 100px; //这种情况之下IE会产生200px的距离 	   
  display:inline; //使浮动忽略}
```

这里细说一下block与inline两个元素：block元素的特点是,总是在新行上开始,高度,宽度,行高,边距都可以控制(块元素);Inline元素的特点是,和其他元素在同一行上,不可控制(内嵌元素);    

```css
box{ display:block; //可以为内嵌元素模拟为块元素 
     display:inline; //实现同一行排列的效果
     diplay:table;
```

## IE与宽度和高度的问题

IE 不认得min-这个定义，但实际上它把正常的width和height当作有min的情况来使。这样问题就大了，如果只用宽度和高度，正常的浏览器里这两个值就不会变，如果只用min-width和min-height的话，IE下面根本等于没有设置宽度和高度。 
比如要设置背景图片，这个宽度是比较重要的。要解决这个问题，可以这样：    
```css
box{ width: 80px; 
   height: 35px;}
html>body #box{ width: auto; 
  height: auto; 
  min-width: 80px; 
  min-height: 35px;}
```

## 页面的最小宽度

min -width是个非常方便的CSS命令，它可以指定元素最小也不能小于某个宽度，这样就能保证排版一直正确。但IE不认得这个，而它实际上把width当 做最小宽度来使。为了让这一命令在IE上也能用，可以把一个<div> 放到 <body> 标签下，然后为div指定一个类, 然后CSS这样设计：    
```css
container{ min-width: 600px;   width:expression(document.body.clientWidth < 600? "600px": "auto" );}
```
第一个min-width是正常的；但第2行的width使用了Javascript，这只有IE才认得，这也会让你的HTML文档不太正规。它实际上通过Javascript的判断来实现最小宽度。   

##  DIV浮动IE文本产生3象素的bug

左边对象浮动，右边采用外补丁的左边距来定位，右边对象内的文本会离左边有3px的间距.   
```css
box{ float:left; 
  width:800px;}
left{ float:left; 
  width:50%;}
right{ width:50%;}
*html #left{ margin-right:-3px; //这句是关键}    
<div id="box">   
<div id="left"></div>   
<div id="right"></div>   
</div>   
```

## IE兼容模式

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

以上代码可以告知浏览器，在安装有GCF的情况下，可以以CHROME的方式渲染IE浏览器，在未安装的情况下全安装的情况下，可以使用最新的IE方式渲染

## IE捉迷藏的问题    

当div应用复杂的时候每个栏中又有一些链接，DIV等这个时候容易发生捉迷藏的问题。有些内容显示不出来，当鼠标选择这个区域是发现内容确实在页面。

 解决办法：对#layout使用line-height属性 或者给#layout使用固定高和宽。页面结构尽量简单。   

## float的div闭合;清除浮动;自适应高度;    

① 例如：<#div id=”floatA” ><#div id=”floatB” ><#div id=” NOTfloatC” >这里的NOTfloatC并不希望继续平移，而是希望往下排。(其中floatA、floatB的属性已经设置为 float:left;)   
这段代码在IE中毫无问题，问题出在FF。原因是NOTfloatC并非float标签，必须将float标签 闭合。在 <#div class=”floatB”> <#div class=”NOTfloatC”>之间加上 < #div class=”clear”>这个div一定要注意位置，而且必须与两个具有float属性的div同级，之间不能存在嵌套关系，否则会 产生异常。 并且将clear这种样式定义为为如下即可： .clear{ clear:both;}    

②作为外部 wrapper 的 div 不要定死高度,为了让高度能自动适应，要在wrapper里面加上overflow:hidden; 当包含float的 box的时候，高度自动适应在IE下无效，这时候应该触发IE的layout私有属性(万恶的IE啊！)用zoom:1;可以做到，这样就达到了兼容。    
例如某一个wrapper如下定义：    
.colwrapper{ overflow:hidden; zoom:1; margin:5px auto;}    

③对于排版,我们用得最多的css描述可能就是float:left.有的时候我们需要在n栏的float div后面做一个统一的背景,譬如:   

```html
<div id=”page”>   
<div id=”left”></div>   
<div id=”center”></div>   
<div id=”right”></div>    
</div>   
```

比如我们要将page的背景设置成蓝色,以达到所有三栏的背景颜色是蓝色的目的,但是我们会发现随着left center right的向下拉长,而 page居然保存高度不变,问题来了,原因在于page不是float属性,而我们的page由于要居中,不能设置成float,所以我们应该这样解决    

```html
<div id=”page”>   
<div id=”bg” style=”float:left;width:100%”>   
<div id=”left”></div>   
<div id=”center”></div>   
<div id=”right”></div>   
</div>   
</div>   
```

再嵌入一个float left而宽度是100%的DIV解决之   

④万能float 闭合(非常重要!)    
关 于 clear float 的原理可参见 [How To Clear Floats Without Structural Markup],将以下 代码加入Global CSS 中,给需要闭合的div加上 class="clearfix" 即可,屡试不爽.    

```html
/* Clear Fix */    
.clearfix:after { content:"."; display:block; height:0; clear:both; visibility:hidden; }    
.clearfix { display:inline-block; }    
/* Hide from IE Mac */    
.clearfix {display:block;}    
/* End hide from IE Mac */    
/* end of clearfix */    
```

或者这样设置：.hackbox{ display:table; //将对象作为块元素级的表格显示}   

