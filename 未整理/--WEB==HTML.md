# HTML

## 为web结构化文档

### 什么是html5

1. 标签和元素：开闭标签

2. 头部和主体元素

3. 特性描述元素（attribute)：名称和值；特殊的：布尔特性

4. 常见特性：核心特性，国际化特性，辅助访问特性

   1.核心特性：id的取值规则/class/title/style/

   2.国际化特性：dir/lang

5. 核心元素

   ` <doctype> <html> <head> <title> <link> <script> <body>`

6. 确保html5的向后兼容性——html5shiv/modernizr

7. 基本文本格式化

   `<hn>,<p>,<br>,<pre>`

> 关于实体引用： 空格的符号是：& nbsp; (no break space)；< 的符号是& lt; >的符号是& gt; 引号的实体是 & quot;

8. 块级元素与行内元素
   + 块级元素
   + 行内元素
9. 内容分组
   `<div> <header> <hgroup> <nav> <section> <article> <hr> <blockquote> <aside> <footer> <address>`

> 关于article和section的区别；关于aside的使用

10. 列表元素
+ 有序列表
+ 无序列表
+ 自定义列表

> 特性： start定义起始数字；
> ​             reversed是列表倒序；
> ​            type定义列表标记符号（1/a/A/i/I）；

### 文本微调

1. 语义元素
   `<span>  <em>（加粗） <strong>（倾斜） <b>  <i>  <small> <cite> <q> <dfn> <abbr> <time> <code> <figure> <figcaption> <var> <samp> <kbd> <sup> <sub> <mark>`

   > small元素用于打印条文细则，免责声明，警告，版权信息
   > 注意cite元素与cite特性的区别
   > time元素的datetime特性的取值可以是。。。。

2. 文本编辑

   `<del> <ins>`

   > 这两个元素可以包含datetime特性，以表明修改时间

3. 注释

## 链接与导航

### 基本链接

1. 链接到其他网址

2. 链接到email

   > <a href="mailto:info@exp.com?subject=subject&cc=name&body=content&bcc=name"

3. 链接到本地文件

   > 理解URL 统一资源定位符，包括协议，主机地址，文件路径组成
   > 理解根目录，子目录等概念，相对路径和绝对路径
   > base标签的用法 <base href="url">

4. a标签的其他特性

    accesskey：定义快捷健

   hreflang：定义链接语言

   rel：定义链接之间的关系

   tabindex：定义焦点顺序

   target：定义链接的打开方式

   title：定义链接的信息

   type：指定链接的mime类型

## 媒体

### 插入图片

1. 使用img标签，必要的特性有：

   src、alt。可选的特性有height、width 另外使用百分比值的时候，其代表的是包含元素的百分比，而非其本身的百分比。

2. 关于图片的格式：

   对于要保留大量的细节逼真图片可以使用JPEG格式；

   对于扁平色，没有太多细节的图片可以使用PNG格式；

   另外还可以创建一个缩小版本，即所谓的缩略图（thumbnails）；

   其他的格式还有svg\gif\bmp等等；

### 插入富媒体

1. 通过网站提供的分享链接来引用其他网站的视频或音频；

2. 使用\<audio>、\<video>元素来添加本地的富媒体；

   常见的特性：controls poster loop muted autoplay preload

   > 关于容器和编解码器

3. 使用\<param> \<object>添加flash视频；

```html
<object width="" height="">
  <param name=""allowScriptAccess" value="always"/> //可在不同的网站播放
  <param name="allowFullScreen" value="true"/>
  <param name="movie" value="flash/this-changes-everything.swf"/>//指定播放地址
  <param name=“loop” value="false"/>
    <emed src="flash/this-changes-everything.swf" loop="false" allowScriptAccess="sameDomain" allowFullScreen="true" width="" height=""/>
</object>
```

4. 通过SWFObject引入：

```html
<script src="swfobject.js"></script>
<script>swfobject.emedSWF("flash/this-changes-everything.swf","flash_movie","500","400","8.0.0")</script>//id="flash_movie" width="500" height="400" version:8.0.0
```

5. 跨浏览器兼容

```html
<video width="" height="" controls>
  <source src="***.mp4" type="video/mp4"/>
  <source src="***.webm" type="video/webm"/>
  <source src="***.ogv" type="video/ogg"/>
  <object width="" height="" type="application/x-shockwave-flash" data="***.swf">
    <param name="movie" value="***.swf"/>
  </object>
</video>
```

```html
<audio width="" height="" controls>
  <source src="***.mp3" type="audio/mp3"/>
  <source src="***.ogv" type="video/ogg"/>
  <object width="" height="" data="flash/dewplayer.swf?mp3=***.mp3" id="">
    <param name="wmode" value="transparent"/>
    <param name="movie" value="flash/dewplayer.swf?mp3=***.mp3" 
  </object>
</audio>
```

## 表格

### 常用元素

1. table  caption thead th tr td tbody tfoot

2. colspan特性：合并列

   rowspan特性：合并行

   header特性：指定表头对应的单元，指定表格中某个单元格所对应的表头

     例如：header="a-row b-col" 指明了该单元格所在的表头是a-row行，b-col列。

   ==scope特性==  

3. colgroup进行分组

```html
   <colgroup span="2" class=" maincolumn"/>
   <colgroup span="4" class="subcolumn"/>
```

4. col在列间共享样式

```html
   <colgroup span="4" class=" maincolumn"/>
     <col span="1" class="main"/>
     <col span="3" class="sub"/>
   </colgroup>
```

## 表单



```html
<form action="处理表单的网址" method="get/post(两者择一)" id="" name="" enctype="text/plain" accept-charset="utf-8" novalidate="true" target="_blank" autocomplete ></form>
```

> enctype 可取的值有：application/x-ww-form-urlencoded、multipart/form-data、text/plain

```html
<input type="text">
<input type="password">
<input type="submit">
<input type="reset">
<input type="url">
<input type="tel">
<input type="search">
<input type="email">
<input type="color">
<input type="date">
<input type="month">
<input type="week"> 
<input type="time">
<input type="datetime-local">
```

常见的特性：

 name maxlength value preholder size disabled readonly form autocomplete autofocus list pattern required dirname multiple tabindex accesskey

```html
<textarea cols="" rows="" wrap="soft"></textarea>//wrap="hard"

<input type="number" min="1" max="5">
<input type="range" min="0" max="10">
<input type="button" onclick="" value="">
<input type="image" src="" alt="" name="" height="" width="" >
```

> 填充剂preholder.js可以弥补某些不支持preholder的浏览器

```html
<button type="submit">submit</button>
<button type="reset">reset</button>
<button type="button"><img src="" alt=""></button>
```

> tabindex标签遍历顺序 值为0时不参与遍历

```html
<input type="checkbox" name="设为同一个值" value="" checked/>
<input type="checkbox" name="也可是不同的值" value="不同的值"/>
<input type="checkbox" name="" value=""/>

<input type="radio" name="设为同一个值" value="" checked/>
<input type="radio" name="" value="不同的值"/>
<input type="radio" name="" value=""/>
```

> accesskey 可以设置快捷键

```html
<select name="" multiple>
  <option value="" selected></option>
  <option value="" ></option>
  <option value="" ></option>
</select>

<select name="" multiple>
  <optgroup label="">
    <option value="" selected></option>
    <option value="" ></option>
  </optgroup>
  <optgroup label="">
    <option value="" ></option>
  </optgroup>
</select>
```

```html
<form action="" method="post" id="" name="" enctype="multipart/form-data" >
  <input type="file" name="" accept="mime类型"
</form>
```

```html
<progress value="" max="">
<meter max="" min="" value="已使用" high="高范围低值" low="低范围高值" optimum="最佳值">
<input type="text">
  <datalist id="">
    <option value="">
    <option value="">
    <option value="">
  </datalist>
```

```html
<label for="aform">username:</label><input type="text" id="aform" name="txtusername">
```

```html
<form>
  <fieldset>
    <legend>form caption</legend>
    ………
  </fieldset>
</form>
```

