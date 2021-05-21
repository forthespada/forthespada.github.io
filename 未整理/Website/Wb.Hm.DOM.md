---
title: 前端基础——HTML（一）
date: 2018-6-10
tags: 
 -  Technology
 -  Website
 -  HTML
 -  Javascript
 -  CSS
categories: 
 -  Technology
 -  Website
 -  HTML
location: 青島市
description: HTML 筆記系列之 HTML文档结构。
photo: 
 - "https://s2.ax1x.com/2019/05/16/Eb64Ff.png"
---

## HTML 5 的背景知識

HTML 是用来描述网页的一种语言。

- HTML 指的是超文本标记语言 (**H**yper **T**ext **M**arkup **L**anguage)
- HTML 不是一种编程语言，而是一种*标记语言* (markup language)
- 标记语言是一套*标记标签* (markup tag)
- 制定 HTML 規範的是 W3C （**W**orld **W**ide **W**eb **C**onsortium）

瀏覽器對 HTML 5 的支持情況

- 可以使用 Modernizr 之類的 JavaScript 庫檢查某些特性的可行性
- 可以使用 [When Can I Use?](http://caniuse.com)  檢查瀏覽器兌特性的支持情況和採用率等方面的詳細信息

## HTML 元素

### HTML 標籤

HTML 标记标签通常被称为 HTML 标签 (HTML tag)。

HTML 元素指的是从开始标签（start tag）到结束标签（end tag）的所有代码。

- HTML 元素以开始标签起始，以结束标签终止
- 元素的内容是开始标签与结束标签之间的内容
- 某些 HTML 元素具有空内容（empty content）
- 大多数 HTML 元素可以**嵌套**
- 虛元素（void element）是指那些不可以在其中放入任何內容的元素，例如 `&lt;hr&gt;` ，類似的標籤被稱爲自閉合標籤

```html
&lt;!-- 這裏的內容是註釋，下面將提供實例說明 HTML 元素。 --&gt;
這裏將出現一個加粗的字：&lt;b&gt;商無射&lt;/b&gt;。
&lt;!-- 這裏的 &lt;b&gt; 就是開始標籤。 --&gt;
&lt;!-- 這裏的 &lt;/b&gt; 就是結束標籤。 --&gt;
&lt;!-- 這裏的 商無射 就是元素的內容，也就是位於開始標籤和結束標籤之內的文字。 --&gt;
&lt;!-- 注意，標籤是不區分大小寫的。例如我書寫 &lt;div&gt; &lt;DIV&gt; &lt;DiV&gt; 對於瀏覽器來說都是一樣的，但是仍然建議使用小寫。 --&gt;
```

### HTML 元素的屬性

- 所有的元素都有屬性（attribute），屬性值間通過空格隔開，不論順序
- 属性总是以名称/值对的形式出现，比如：name="value"。
- 属性总是在 HTML 元素的**开始标签**中规定。
- 一個元素可以應用多個屬性
- 屬性包括全局屬性和專有屬性
- 有一部分屬性是布爾屬性，寫法可以是 `disabled` `disabled=""` `disabled="disabled"`
- 用戶可以自定屬性。但其屬性名應以 `-data-` 開頭。
- 属性值应该始终被包括在引号内。双引号是最常用的，不过使用单引号也没有问题。

```html
&lt;!-- 這裏的內容是註釋，下面將提供實例說明 HTML 元素的屬性。 --&gt;
<a href="htmllearning.html" class="link">HTML Learning</a>
&lt;!-- 這裏的 href 就是 <a> 元素的屬性，表示其鏈接地址。當然 class 也是。 --&gt;
&lt;!-- href 等號後用單引號引住的就是其屬性值。class 相同。 --&gt;

&lt;!-- 接下來的實例則介紹了布爾屬性。 --&gt;
<input disabled>
&lt;!-- 正如前面說的，disabled 可以寫作 disabled="" disabled="disabled"。無論是那種書寫方式，都會得到相同的效果。 --&gt;
```

### 注释

```html
//注释:&lt;!--注释--&gt;
&lt;a href="www.baidu.com"&gt;百度一下 你不知道&lt;/a&gt; &lt;!--注释写在这里--&gt;

//条件注释
&lt;!--[if IE 8]&gt;
    .... some HTML here ....
&lt;![endif]--&gt;元素(标签+属性+文本)
```

## HTML文档结构

### HTML文档基本结构

```html
DTD(Document Type Definition)  -------------- 文档定义类型
&lt;html&gt;  -------------- 文本描述网页
    &lt;head&gt; -------------- 文档头部标记：含脚本，样式表等等。
        &lt;meta&gt; -------------- 定义文档字符集、使用语言、作者等基本信息(元数据)
        &lt;base&gt; -------------- 定义页面上所有链接的默认地址或默认目标。
        &lt;link&gt; -------------- 定义文档与外部资源之间的关系。   
        &lt;style&gt; -------------- 定义文档的样式信息。
        &lt;title&gt;  -------------- 定义文档的标题
        &lt;script&gt; -------------- 定义客户端脚本。
    &lt;body&gt; -------------- 网页主体,是可见的页面内容
```
### DOCTYPE元素

#### 概述

本文系统的讲解DOCTYPE元素.同时查证了很多的资料.因为互联网上面的资料比较杂乱,所以经过收集整理我进行了重新定义.比如对于DOCTYPE元素的定义.主要分为基础知识和高级知识.基础知识讲解基本的DOCTYPE知识. 高级知识很多来自网络收集, 主要是实际应用的一些技巧.

#### 定义

DOCTYPE是文档类型(Document Type)的缩写, &lt;!DOCTYPE&gt; 元素用于声明一个页面的文档类型定义(Document Type Declaration, 即DTD).此元素声明位于文档中的最前面的位置，处于 &lt;html&gt; 标签之前。通过确认页面的DTD,可以同时确定页面使用哪种W3C规范(比如 HTML 或 XHTML 规范)。

#### W3C规范

W3C规范的正确翻译应该为W3C推荐(W3C Recommendations).很多设计师的眼里W3C就是标准.但是许多人都是一知半解.下面列于了目前W3C规范中的HTML规范和XHTML规范,稍后会讲解HTML和XHTML的关系:   

XHTML可以看成是最新的HTML规范, 是一项可从 HTML 4.01 平稳迁移的 XML 应用。W3C 把 HTML 4.01 重构为 XML 的第一个步骤，导致了 XHTML 1.0 的诞生。XHTML 1.0 依赖于 HTML 4.01 标签所提供的语义。  

#### 规范与DTD

页面文件通过&lt;DOCTYPE&gt;元素声明不同的DTD, 来告知浏览器当前页面符合哪种HTML或者XHTML规范.下面只列举HTML4.01和XHTML1.0两种规范相关的DTD:   

> HTML(XHTML同HTML）
>
> ```
> HTML 4.01 规定了三种文档类型：Strict、Transitional 以及 Frameset。
> ```

+ HTML Strict DTD

> 如果您需要干净的标记，免于表现层的混乱，请使用此类型。请与层叠样式表（CSS）配合使用：
>
> ```
> &lt;!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" " 
> 
> http://www.w3.org/TR/html4/strict.dtd"&gt;
> ```

+ HTML Transitional DTD

> Transitional DTD 可包含 W3C 所期望移入样式表的呈现属性和元素。如果您的读者使用了不支持层叠样式表（CSS）的浏览器以至于您不得不使用 HTML 的呈现特性时，请使用此类型：
>
> <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" " 
> http://www.w3.org/TR/html4/loose.dtd">

+ Frameset DTD

> Frameset DTD 应当被用于带有框架的文档。除 frameset 元素取代了 body 元素之外，Frameset DTD 等同于 Transitional DTD：
>
> <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" " 
> http://www.w3.org/TR/html4/frameset.dtd">
>
> PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" 
> "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"&gt;

#### HTML 文档类型

+ 声明必须是 HTML 文档的第一行，位于 &lt;html&gt; 标签之前。
+ 作用：指示浏览器关于页面使用哪个 HTML 版本进行编写的指令。

```html
//HTML 5
&lt;!DOCTYPE html&gt;

//HTML 4.01 Strict
该 DTD 包含所有 HTML 元素和属性，但不包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。
&lt;!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd"&gt;

//HTML 4.01 Transitional
该 DTD 包含所有 HTML 元素和属性，包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。
&lt;!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" 
"http://www.w3.org/TR/html4/loose.dtd"&gt;

//HTML 4.01 Frameset
该 DTD 等同于 HTML 4.01 Transitional，但允许框架集内容。
&lt;!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" 
"http://www.w3.org/TR/html4/frameset.dtd"&gt;

//XHTML 1.0
&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;
```

#### DOCTYPE 元素语法

**HTML 顶级元素 可用性 "注册//组织//类型 标签//定义 语言""URL"**

语法元素说明

+ 顶级元素：指定 DTD 中声明的顶级元素类型。这与声明的 SGML 文档类型相对应。 默认为HTML。

+ 可用性：指定正式公开标识符(FPI)是可公开访问的对象还是系统资源。取值可以为PUBLIC或者SYSTEM.PUBLIC 默认。表示可公开访问的对象。SYSTEM表示系统资源，如本地文件或 URL。

+ 注册：指定组织是否由国际标准化组织(ISO)注册。

	+为默认,表示组织名称已注册。

	-表示组织名称未注册。Internet 工程任务组(IETF)和万维网协会(W3C)并非注册的 ISO 组织。

+ 组织：指定表明负责由 !DOCTYPE 声明引用的 DTD 的创建和维护的团体或组织的名称，即 OwnderID。 IETF为IETF。W3C为W3C。

+ 类型：指定公开文本类，即所引用的对象类型。 默认为DTD。

+ 标签：指定公开文本描述，即对所引用的公开文本的唯一描述性名称。后面可附带版本号。默认为HTML。

+ 定义：指定文档类型定义。

+ Frameset 框架集文档。

	Strict 排除所有 W3C 专家希望逐步淘汰的代表性属性和元素，因为样式表已经很完善了。

	Transitional 包含除 frameSet 元素的全部内容。

+ 语言：指定公开文本语言，即用于创建所引用对象的自然语言编码系统。该语言定义已编写为 ISO 639 语言代码(大写两个字母)。 EN 默认。英语。

+ URL：指定所引用对象的位置。   

#### 检查工具

  如果要检查你的页面内容是否符合在DOCTYPE中声明的标准,可以使用W3C提供的验证工具:http://validator.w3.org/

#### DOCTYPE切换

现代浏览器包括不同的呈现模式，目的是既支持遵循W3C标准的网页，也支持为老式浏览器而设计的网页。其中， Standards （标准）模式（也就是严格呈现模式）用于呈现遵循最新标准的网页，而 Quirks （包容）模式（也就是松散呈现模式或者兼容模式）用于呈现为传统浏览器而设计的网页。另外，注意Mozilla/Netscape 6新增了一种 Almost Standards （近似标准）模式，用于支持为标准的某个老版本而设计的网页。

理论上，这应该是一个非常直观的切换。假如页面的&lt;!DOCTYPE&gt;元素指出了页面的遵循标准(比如XHTML1.0), 浏览器就会切换到Standards模式。假如没有指定doctype，或者指定HTML 3.2以及更老的版本，浏览器就切换到Quirks模式。这样一来，浏览器既能正确显示遵循标准的文档，又不至于完全舍弃老式的、与标准不符的网页。 但是会有下面几种情况:

+ 丢失的URL或者相对URL

	在完整的doctype声明中，要包括相应的文档类型定义（DTD）文件的URL。如果URL丢失，或者指定的是一个相对路径（而不是完全限定的Internet地址），大多数浏览器都会进入Quirks模式，不管doctype声明规定的是什么模式。

+ 形式错误的doctype

	浏览器对doctype声明的形式和格式非常敏感，如果不能识别一个形式错误的doctype，就会强制进入Quirks模式（建议将一个已知正确的doctype拷贝和粘贴到文档中，而不是亲自输入它）。之所以出现形式错误的doctype，一个常见的原因是在 doctype 的第一部分与URL之间缺少一个空格。将一个分两行的doctype折叠成单独一行，常常会丢失那个空格。

+ 过渡期的 doctype

	浏览器处理过渡期的doctype时，最容易出现不一致的问题。IE和Opera使用Standards模式；Netscape 6和旧版本的Safari使用Quirks模式；Netscape 7、Mozilla 1和新版本的Safari使用Netscape的Almost Standards模式，它是Standards模式的一个具有更好容错性的版本。

+ 未知的 doctype

  浏览器在处理不能识别的doctype时，也存在不一致的现象。IE和Opera会进入Standards模式；换言之，它假定不能识别的 doctype 是尚未在浏览器中集成的一个新标准。Netscape 6则相反，会在遇到不能识别的doctype时切换到Quirks模式。
   doctype切换也许是让浏览器进入正确呈现模式并正确显示网页的一种有效手段，前提是你注意到了各种浏览器的不一致，并能积极主动地避免各种问题。

### XHTML使用技巧

+ 紧跟在上面 DOCTYPE 声明之后的是一个 XHTML 名字空间（namespace）声明，放在增强的 &lt;html&gt; 元素中，写法为：

   &lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;

+ 由于 XHTML 1.0 页面就是合法的 XML 文档，而 XML 对于标签和属性都是区分大小写的，为了简单起见，XHTML 1.0 页面中所有的标签和属性都必须使用小写。

   一些免费的工具，例如 [HTML Tidy](http://tidy.sourceforge.net/)，可以帮助你把标签和属性自动转换为小写。

+ 通过在 &lt;head&gt; 元素中添加一个 &lt;meta&gt; 元素来声明页面中使用的语言。

   &lt;meta http-equiv="Content-Type" content="text/html; charset=gbk" /&gt;

+ 在 XHTML 中，所有的属性都必须要加上引号。

   一些免费的工具，例如  [HTML Tidy](http://tidy.sourceforge.net)，可以帮助你自动为所有的属性加上引号。

+ 在 XHTML 中，所有的属性都必须有值。

   不能像在 HTML 4.0 中那样写：

   ```html
   &lt;input type="checkbox" name="shirt" value="medium" checked&gt;
   
   而要写成：
   
   &lt;input type="checkbox" name="shirt" value="medium" checked="checked" /&gt;
   ```

+ 在 XHTML 中，所有的标签都必须关闭。

   关闭标签有两种方式，包含内容的标签使用结束标签关闭，空标签在后面加上空格和"/"。例如：

   ```html
   &lt;p&gt;This is acceptable HTML and it is also valid XHTML.&lt;/p&gt;
   ```

+ 不要在注释内容中使用"--" 。

   "--" 只能使用在 XHTML 注释的开头和结束，不能出现在注释的内容中。下面的写法都是不允许的：

   ```html
   &lt;!--Invalid -- and so is the classic "separator" below. --&gt;
   
   &lt;!------------------------------------&gt;
   ```

+ 把所有的特殊符号进行HTML编码。   

  W3C 的 XHTML/CSS/DOM 这 3 个规范构成了一个完整而严密的体系，我称这 3 个规范为 Web 世界中"三位一体神的化身"。这 3 个规范分别代表了 Web 页面的 structure（结构）、presentation（表现）和 behaviour（行为） 3 部分。将 Web 页面严格分为这 3 层，并且尽量使每一层的内容相互独立，有助于提高页面的可重用性和模块化程度，大幅降低页面制作、维护和修改的成本。为了达到上述分层的目标，编写的 XHTML 中应该只包含与 structure 相关的标记（元素和属性）。因此应该习惯于使用 Strict 类型的 DTD，尽快摒弃那些带有表现含意的标记（这些标记在 HTML 4.0 规范中被标识为 Deprecated 即"不提倡"，并且会在 XHTML 以后的版本中被完全舍弃）；尽快摒弃基于 table 做布局的老方法，采用完全的 CSS 布局。  

#### 推荐的 XHTML 相关书籍

> 《HTML 与 XHTML 权威指南》，Chuck Musciano & Bill Kennedy 著。

> 《XHTML教程》，Chelsea Valentine & Chris Minnick 著。

> 《网站重构》，Jeffrey Zeldman 著。

	*作者：张子秋*
	*出处：http://www.cnblogs.com/zhangziqiu/*
	*本文版权归作者和博客园共有，欢迎转载，但未经作者同意必须保留此段声明，且在文章页面明显位置给出原文连接，否则保留追究法律责任的权利。*

### [META属性](http://www.haorooms.com/post/liulanq_think_ie)

#### 前言

&lt;meta&gt; 元素可提供有关页面的元信息（meta-information），比如针对搜索引擎和更新频度的描述和关键词。
&lt;meta&gt; 标签位于文档的头部，不包含任何内容。&lt;meta&gt; 标签的属性定义了与文档相关联的名称/值对。

所有浏览器都支持 &lt;meta&gt; 标签。

#### 1.NAME属性

name属性主要用于描述网页，与之对应的属性值为content，content中的内容主要是便于搜索引擎机器人查找信息和分类信息用的。

meta标签的name属性语法格式是：

```html
&lt;meta name="参数"content="具体的参数值"&gt;。 
```

其中name属性主要有以下几种参数：　

##### **A、Keywords(关键字)**

说明：keywords用来告诉搜索引擎你网页的关键字是什么。

```html
&lt;meta name="keywords" content="meta总结,html meta,meta属性,meta跳转"&gt; 
```

##### **B、description(网站内容描述)**

说明：description用来告诉搜索引擎你的网站主要内容。

```html
&lt;meta name="description" content="haorooms博客,html的meta总结，meta是html语言head区的一个辅助性标签。"&gt; 
```

##### **C、robots(机器人向导)**

说明：robots用来告诉搜索机器人哪些页面需要索引，哪些页面不需要索引。

content的参数有all,none,index,noindex,follow,nofollow。默认是all。

```html
&lt;meta name="robots" content="none"&gt; 
```

**具体参数如下：**

　　all：文件将被检索，且页面上的链接可以被查询；
　　none：文件将不被检索，且页面上的链接不可以被查询；
　　index：文件将被检索；
　　follow：页面上的链接可以被查询；
　　noindex：文件将不被检索，但页面上的链接可以被查询；
　　nofollow：文件将被检索，页面上的链接不可以被查询。

##### **D、author(作者)**

说明：标注网页的作者

```html
&lt;meta name="author" content="root,root@xxxx.com"&gt; 
```

##### **E、generator**

```html
&lt;meta name="generator"content="信息参数"/&gt; 
```

meta标签的generator的信息参数，代表说明网站的采用的什么软件制作。

##### **F、COPYRIGHT**

```html
&lt;META NAME="COPYRIGHT"CONTENT="信息参数"&gt; 
```

meta标签的COPYRIGHT的信息参数，代表说明网站版权信息。

##### **G、revisit-after**

```html
&lt;META name="revisit-after"CONTENT="7days"&gt; 
```

revisit-after代表网站重访,7days代表7天，依此类推。

#### 2、http-equiv属性

http-equiv顾名思义，相当于http的文件头作用，它可以向浏览器传回一些有用的信息，以帮助正确和精确地显示网页内容，与之对应的属性值为content，content中的内容其实就是各个参数的变量值。

meta标签的http-equiv属性语法格式是：

```html
&lt;meta http-equiv="参数"content="参数变量值"&gt;； 
```

其中http-equiv属性主要有以下几种参数：

##### **A、Expires(期限)**

说明：可以用于设定网页的到期时间。一旦网页过期，必须到服务器上重新传输。

```html
&lt;meta http-equiv="expires"content="Fri,12Jan200118:18:18GMT"&gt; 
```

注意：必须使用GMT的时间格式。

##### **B、Pragma(cache模式)**

说明：禁止浏览器从本地计算机的缓存中访问页面内容。

```html
&lt;meta http-equiv="Pragma"content="no-cache"&gt; 
```

注意：这样设定，访问者将无法脱机浏览。

##### **C、Refresh(刷新)**

说明：自动刷新并指向新页面。

```html
&lt;meta http-equiv="Refresh"content="2;URL=http://www.haorooms.com"&gt; //(注意后面的引号，分别在秒数的前面和网址的后面) 
```

注意：其中的2是指停留2秒钟后自动刷新到URL网址。

##### **D、Set-Cookie(cookie设定)**

说明：如果网页过期，那么存盘的cookie将被删除。

```html
&lt;meta http-equiv="Set-Cookie"content="cookie value=xxx;expires=Friday,12-Jan-200118:18:18GMT；path=/"&gt; 
```

注意：必须使用GMT的时间格式。

##### **E、Window-target(显示窗口的设定)**

说明：强制页面在当前窗口以独立页面显示。

```html
&lt;meta http-equiv="Window-target"content="_top"&gt; 
```

注意：用来防止别人在框架里调用自己的页面。

##### **F、content-Type(显示字符集的设定)**

说明：设定页面使用的字符集。

```html
&lt;meta http-equiv="content-Type"content="text/html;charset=gb2312"&gt; 
```

**具体如下：**

meta标签的charset的信息参数如GB2312时，代表说明网站是采用的编码是简体中文；

meta标签的charset的信息参数如BIG5时，代表说明网站是采用的编码是繁体中文；

meta标签的charset的信息参数如iso-2022-jp时，代表说明网站是采用的编码是日文；

meta标签的charset的信息参数如ks_c_5601时，代表说明网站是采用的编码是韩文；

meta标签的charset的信息参数如ISO-8859-1时，代表说明网站是采用的编码是英文；

meta标签的charset的信息参数如UTF-8时，代表世界通用的语言编码；

##### **G、content-Language（显示语言的设定）**

```html
&lt;meta http-equiv="Content-Language"content="zh-cn"/&gt; 
```

##### **H、Cache-Control指定请求和响应遵循的缓存机制。**

Cache-Control指定请求和响应遵循的缓存机制。在请求消息或响应消息中设置Cache-Control并不会修改另一个消息处理过程中的缓存处理过程。请求时的缓存指令包括no-cache、no-store、max-age、max-stale、min-fresh、only-if-cached，响应消息中的指令包括public、private、no-cache、no-store、no-transform、must-revalidate、proxy-revalidate、max-age。各个消息中的指令含义如下

> Public指示响应可被任何缓存区缓存

> Private指示对于单个用户的整个或部分响应消息，不能被共享缓存处理。这允许服务器仅仅描述当用户的部分响应消息，此响应消息对于其他用户的请求无效

> no-cache指示请求或响应消息不能缓存

> no-store用于防止重要的信息被无意的发布。在请求消息中发送将使得请求和响应消息都不使用缓存。

> max-age指示客户机可以接收生存期不大于指定时间（以秒为单位）的响应

> min-fresh指示客户机可以接收响应时间小于当前时间加上指定时间的响应

> max-stale指示客户机可以接收超出超时期间的响应消息。如果指定max-stale消息的值，那么客户机可以接收超出超时期指定值之内的响应消息。

##### **J、http-equiv="imagetoolbar"**

```html
&lt;meta http-equiv="imagetoolbar"content="false"/&gt; 
```

指定是否显示图片工具栏，当为false代表不显示，当为true代表显示。

##### **K、Content-Script-Type**

```html
&lt;Meta http-equiv="Content-Script-Type"Content="text/javascript"&gt; 
```

W3C网页规范，指明页面中脚本的类型。

##### **L 页面跳转，只用于IE**

具体请看 [http://www.haorooms.com/post/liulanq_think_ie](http://www.haorooms.com/post/liulanq_think_ie)

#### 3.移动设备

```html
&lt;meta name="viewport" content="width=device-width, initial-scale=1.0,maximum-scale=1.0, user-scalable=no"/&gt;
&lt;!-- `width=device-width` 会导致 iPhone 5 添加到主屏后以 WebApp 全屏模式打开页面时出现黑边  --&gt;
```

+ WebApp全屏模式

```html
&lt;meta name="apple-mobile-web-app-capable" content="yes" /&gt;
&lt;!-- 启用 WebApp 全屏模式 --&gt;
```

+ 隐藏状态栏/设置状态栏颜色

```html
&lt;meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" /&gt;
```

+ 添加到主屏后的标题

```html
&lt;meta name="apple-mobile-web-app-title" content="标题"&gt;
```

+ 忽略数字自动识别为电话号码

```html
&lt;meta content="telephone=no" name="format-detection" /&gt;
```

+ 忽略识别邮箱

```html
&lt;meta content="email=no" name="format-detection" /&gt;
```

+ 申明编码

```html
&lt;meta charset='utf-8' /&gt;
```

+ 优先使用 IE 最新版本和 Chrome

```html
　　&lt;meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" /&gt;
　　&lt;!-- 关于X-UA-Compatible --&gt;
　　&lt;meta http-equiv="X-UA-Compatible" content="IE=6" &gt;&lt;!-- 使用IE6 --&gt;
　　&lt;meta http-equiv="X-UA-Compatible" content="IE=7" &gt;&lt;!-- 使用IE7 --&gt;
　　&lt;meta http-equiv="X-UA-Compatible" content="IE=8" &gt;&lt;!-- 使用IE8 --&gt;
```

+ 禁止浏览器从本地计算机的缓存中访问页面内容

```html
&lt;meta http-equiv="Pragma" content="no-cache"&gt;
```

+ 浏览器不会自动调整文件的大小,也就是说是固定大小,不会随着浏览器拉伸缩放。

```html
&lt;meta name="MobileOptimized" content="240"/&gt; 
```


