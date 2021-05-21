---
title: 如何优雅的选择字体
language: zh-tw
date: 2019-05-09 21:24:56
updated:
tags:
- Design
- Font
- Typeset
- Website
- Technology
categories:
- Technology
- Website
- Design
location: 四川大學
top:
comments:
description: 本文轉自 koreyhan 的博文。介紹了在不同平臺上的中文字體使用解決方案。
visible:
photo: 
 - "https://s2.ax1x.com/2019/05/16/Eb6Wwt.png"
---

原文地址如下：  [如何优雅的选择字体(font-family)](https://segmentfault.com/a/1190000006110417)

大家都知道，在不同操作系统、不同游览器里面默认显示的字体是不一样的，并且相同字体在不同操作系统里面渲染的效果也不尽相同，那么如何设置字体显示效果会比较好呢？下面我们逐步的分析一下：

## 各平台的默认字体情况

### Windows

+ **宋体（SimSun）**：Win下大部分游览器的默认字体，`宋体`在小字号下（如12px、14px）的显示效果还可以接受，但是字号一大就非常糟糕了，所以使用的时候要注意。
+ **微软雅黑（"Microsoft Yahei"）**：从 Vista 开始，微软提供了这款新的字体，一款无衬线的黑体类字体，并且拥有 *Regular*、*Bold* 两种粗细的字重，显著提高了字体的显示效果。现在这款字体已经成为Windows游览器中最值得使用的中文字体。从Win8开始，`微软雅黑`又加入了 *Light* 这款更细的字重，对于喜欢细字体的设计、开发人员又多了一个新的选择。
+ **Arial**：Win平台上默认的无衬线西文字体（为什么要说英文字体后面会解释），有多种变体，显示效果一般。
+ **Tahoma**：十分常见的无衬线字体，被采用为Windows 2000、Windows XP、Windows Server 2003及Sega游戏主机Dreamcast等系统的预设字型，显示效果比`Arial`要好。
+ **Verdana**：无衬线字体，优点在于它在小字上仍结构清晰端整、阅读辨识容易。
+ **其他**：Windows 下默认字体列表：[微软官网](https://www.microsoft.com/typography/fonts/product.aspx?pid=161)、[维基百科](https://en.wikipedia.org/wiki/List_of_typefaces_included_with_Microsoft_Windows)、[Office字体](https://support.office.com/zh-cn/article/%E4%B8%8D%E5%90%8C%E7%89%88%E6%9C%AC%E7%9A%84-Office-%E6%8F%90%E4%BE%9B%E7%9A%84%E5%AD%97%E4%BD%93-db1101fc-5cc0-4300-91cd-de7c79d907cd?CorrelationId=e2918255-27c6-4f99-b24c-6789900e8cb2&ui=zh-CN&rs=zh-CN&ad=CN&ocmsassetID=HA010282644)
+ **结论：微软雅黑为Win平台上最值得选择的中文字体，但非游览器默认，需要设置；西文字体的选择以Arial、Tahoma等无衬线字体为主。**

### Mac OS

+ **华文黑体（STHeiti）、华文细黑（STXihei）**：属于同一字体家族系列，OS X 10.6 之前的简体中文系统界面默认字体，也是目前Chrome游览器下的默认字体，有 *Regular* 和 *Bold* 两个字重，显示效果可以接受，`华文细黑`也曾是我最喜欢的字体之一。
+ **黑体-简（Heiti SC）**：从 10.6 开始，`黑体-简`代替`华文黑体`用作简体中文系统界面默认字体，苹果生态最常用的字体之一，包括iPhone、iPad等设备用的也是这款字体，显示效果不错，但是喇叭口设计遭人诟病。
+ **冬青黑体（ Hiragino Sans GB ）**：听说又叫`苹果丽黑`，日文字体`Hiragino KakuGothic`的简体中文版，简体中文有 *常规体* 和 *粗体* 两种，`冬青黑体`是一款清新的专业印刷字体，小字号时足够清晰，拥有很多人的追捧。
+ **Times New Roman**：Mac平台Safari下默认的字体，是最常见且广为人知的西文衬线字体之一，众多网页浏览器和文字处理软件都是用它作为默认字体。
+ **Helvetica、Helvetica Neue**：一种被广泛使用的传奇般的西文字体（这货还有专门的记录片呢），在微软使用山寨货的`Arial`时，乔布斯却花费重金获得了`Helvetica`苹果系统上的使用权，因此该字体也一直伴随着苹果用户，是苹果生态中最常用的西文字体。`Helvetica Neue`为`Helvetica`的改善版本，且增加了更多不同粗细与宽度的字形，共拥有51种字体版本，极大的满足了日常的使用。
+ **苹方（PingFang SC）**：在Mac OS X EL Capitan上，苹果为中国用户打造了一款全新中文字体--`苹方`，去掉了为人诟病的喇叭口，整体造型看上去更加简洁，字族共六枚字体：*极细体、纤细体、细体、常规体、中黑体、中粗体*。
+ **San Francisco**：同样是Mac OS X EL Capitan上最新发布的西文字体，感觉和`Helvetica`看上去差别不大，目前已经应用在Mac OS 10.11+、iOS 9.0+、watch OS等最新系统上。
+ **其他**：Mac下默认字体列表：[苹果官网](https://support.apple.com/zh-cn/HT202408)、[维基百科](https://en.wikipedia.org/wiki/List_of_typefaces_included_with_OS_X)
+ **结论：目前苹方和San Francisco为苹果推出的最新字体，显示效果也最为优雅，但只有最新系统才能支持，而黑体-简和Helvetica可以获得更多系统版本支持，显示效果也相差无几，可以接受。**

### Android系统

+ **Droid Sans、Droid Sans Fallback**：`Droid Sans`为安卓系统中默认的西文字体，是一款人文主义无衬线字体，而`Droid Sans Fallback`则是包含汉字、日文假名、韩文的文字扩展支持。
+ **结论：Droid Sans为默认的字体，并结合了中英文，无需单独设置。**

### iOS系统

+ **iOS系统的字体和Mac OS系统的字体相同，保证了Mac上的字体效果，iOS设备就没有太大问题。**

### Linux

+ **文泉驿点阵宋体**：类似`宋体`的衬线字体，一般不推荐使用。
+ **文泉驿微米黑**：几乎是 Linux 社区现有的最佳简体中文字体。

## 选择字体需要注意的问题

### 字体的中英文写法

我们在操作系统中常常看到`宋体`、`微软雅黑`这样的字体名称，但实际上这只是字体的显示名称，而不是字体文件的名称，一般字体文件都是用英文命名的，如`SimSun`、`Microsoft Yahei`。在大多数情况下直接使用显示名称也能正确的显示，但是有一些用户的特殊设置会导致中文声明无效。
**因此，保守的做法是使用字体的字体名称（英文）或者两者兼写。**如下示例：

```
font-family: STXihei, "Microsoft YaHei";
font-family: STXihei, "华文细黑", "Microsoft YaHei", "微软雅黑";
```

### 声明英文字体

绝大部分中文字体里都包含英文字母和数字，不进行英文字体声明是没有问题的，但是大多数中文字体中的英文和数字的部分都不是特别漂亮，所以建议也对英文字体进行声明。
**由于英文字体中大多不包含中文，我们可以先进行英文字体的声明，这样不会影响到中文字体的选择，因此优先使用最优秀的英文字体，中文字体声明则紧随其次。**如下示例：

```
font-family: Arial, "Microsoft YaHei";
```

### 照顾不同的操作系统

+ 英文、数字部分：在默认的操作系统中，Mac和Win都会带有`Arial`, `Verdana`, `Tahoma`等几个预装字体，从显示效果来看，`Tahoma`要比`Arial`更加清晰一些，因此字体设置`Tahoma`最好放到前面，当找不到`Tahoma`时再使用`Arial`；而在Mac中，还拥有一款更加漂亮的`Helvetica`字体，所以为了照顾Mac用户有更好的体验，应该更优先设置`Helvetica`字体；Android系统下默认的无衬线字体就可以接受，因此无需单独设置。**最后，英文、数字字体的最佳写法如下：**

```
font-family: Helvetica, Tahoma, Arial;
```

+ 中文部分：在Win下，`微软雅黑`为大部分人最常使用的中文字体，由于很多人安装Office的缘故，Mac电脑中也会出现微软雅黑字体，因此把显示效果不错的`微软雅黑`加入到字体列表是个不错的选择；同样，为了保证Mac中更为优雅字体`苹方（PingFang SC）`、`黑体-简（Heiti SC）`、`冬青黑体（ Hiragino Sans GB ）`的优先显示，需要把这些字体放到中文字体列表的最前面；同时为了照顾到Linux操作系统的体验，还需要添加`文泉驿微米黑`字体。**最后，中文字体部分最佳写法如下：**

```
font-family: "PingFang SC", "Hiragino Sans GB", "Heiti SC", "Microsoft YaHei", "WenQuanYi Micro Hei";
```

**中英文整合写法：**

```
font-family: Helvetica, Tahoma, Arial, "Heiti SC", "Microsoft YaHei", "WenQuanYi Micro Hei";
font-family: Helvetica, Tahoma, Arial, "PingFang SC", "Hiragino Sans GB", "Heiti SC", "Microsoft YaHei", "WenQuanYi Micro Hei";
```

### 注意向下兼容

如果还需要考虑旧版本操作系统用户的话，不得不加上一些旧版操作系统存在的字体：Mac中的`华文黑体`、`冬青黑体`，Win中的`黑体`等。**同样按照显示效果排列在列表后面，写法如下：**

```
font-family: Helvetica, Tahoma, Arial, "PingFang SC", "Hiragino Sans GB", "Heiti SC", STXihei, "Microsoft YaHei", SimHei, "WenQuanYi Micro Hei";
```

加入了` STXihei（华文细黑）`和` SimHei（黑体）`。

### 补充字体族名称

字体族大体上分为两类：`sans-serif（无衬线体）`和`serif（衬线体）`，当所有的字体都找不到时，我们可以使用字体族名称作为操作系统最后选择字体的方向。一般非衬线字体在显示器中的显示效果会比较好，**因此我们需要在最后添加 sans-serif，写法如下：**。

```
font-family: Helvetica, Tahoma, Arial, "PingFang SC", "Hiragino Sans GB", "Heiti SC", "MicrosoftYaHei", "WenQuanYi Micro Hei", sans-serif;
```

## 大公司的常见写法

（2016.07查看）

### 小米

```
font: 14px/1.5 "Helvetica Neue",Helvetica,Arial,"Microsoft Yahei","Hiragino Sans GB","HeitiSC","WenQuanYi Micro Hei",sans-serif;
```

小米公司优先使用`Helvetica Neue`这款字体以保证最新版本Mac用户的最佳体验，选择了`Arial`作为Win下默认英文字体及Mac的替代英文字体；中文字体方面首选了`微软雅黑`，然后选择了`冬青黑体`及`黑体-简`作为Mac上的替代方案；最后使用`文泉驿微米黑`兼顾了Linux系统。

### 淘宝

鉴于淘宝网改版频率较频繁，这里截图保存了一下，[点此查看](http://oamfqhi9c.bkt.clouddn.com/blog_201607_taobao.jpg)。

```
font: 12px/1.5 tahoma,arial,'Hiragino Sans GB','\5b8b\4f53',sans-serif;
```

其实从图中明显看出淘宝网的导航及内容有着大量的衬线字体，鉴于淘宝网站大部分字号比较小，显示效果也还可以接受。代码中可以看出淘宝使用了`Tahoma`、`Arial`作为首选英文字体，中文字体首选了`冬青黑体`，由于Win下没有预装该款字体，所以显示出了后面的宋体（`5b8b4f53`为汉字`宋体`用 unicode 表示的写法，不用`SimSun`是因为 Firefox 的某些版本和 Opera 不支持 `SimSun`的写法）

### 简书

```
font-family: "lucida grande", "lucida sans unicode", lucida, helvetica, "Hiragino Sans GB", "MicrosoftYaHei", "WenQuanYi Micro Hei", sans-serif;
```

自认为简书的阅读体验很棒，我们看看简书所用的字体，简书优先选择了`lucida`家族的系列字体作为英文字体，该系列字体在Mac和Win上都是预装的，并且有着不俗的表现；中文字体方面将`冬青黑体`作为最优先使用的字体，同样考虑了Linux系统。

*各大公司的字体设置大同小异，这里不再一一举例查看，有兴趣的可以自己多多查看。*

## 其他的一些注意点

### 字体何时需要添加引号

当字体具体某个取值中若有一种样式名称包含空格，则需要用双引号或单引号表示，如：

```
font-family: "Microsoft YaHei", "Arial Narrow", sans-serif;
```

如果书写中文字体名称为了保证兼容性也会添加引号，如：

```
font-family: "黑体-简", "微软雅黑", "文泉驿微米黑";
```

### 引用外部字体

大多数的中文字体由于版权原因不能随意使用，这里推荐一个免版权而且漂亮的中文字体`思源黑体`，该字体为Adobe与Google推出的一款开源字体， 有七种字体粗细*（ExtraLight、Light、Normal、Regular、Medium、Bold 和 Heavy）*，完全支持日文、韩文、繁体中文和简体中文，字形优美，依稀记得小米公司好像有使用过。
鉴于中文字体的体积比较大（一般字库全一点的中文字体动辄几Mb），所以较少人会使用外部字体，如果真的需要引入，也可以考虑通过工具根据页面文字的使用多少单独生成中文字体，以减小文件大小。

## 推荐写法

由于每个人的审美不一样，钟爱的字体也会有所有不同，这里给出我个人的常用写法：

```
font-family: "Helvetica Neue", Helvetica, Arial, "PingFang SC", "Hiragino Sans GB", "Heiti SC", "Microsoft YaHei", "WenQuanYi Micro Hei", sans-serif;
```

另外推荐两个github上的关于中文字体和排版的项目：

+ [Fonts.css -- 跨平台中文字体解决方案](https://github.com/zenozeng/fonts.css)
+ [typo.css -- 中文网页重设与排版：一致化浏览器排版效果](https://github.com/sofish/typo.css)

## 参考资料

+ [如何保证网页的字体在各平台都尽量显示为最高质量的黑体？](https://www.zhihu.com/question/19911793)
+ [Web 中文字体应用指南](http://ruby-china.org/topics/14005)
+ ["5b8b4f53"的意思](http://www.keleyi.com/a/bjac/avaf0haa.htm)