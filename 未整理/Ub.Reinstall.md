---
title: Ubuntu系统重装
date: 2018-10-02 14:52:48
tags:
- linux
- ubuntu
- install
- software
- technology
categories:
- technology
- systems
location: 青島大學
description: 介紹了如何使用u盤安裝ubuntu等系統，同時也備忘了一部分自己常用的軟件和系統美化。
---
## 系统的安装

使用u盘安装：
<div class="note default no-icon">

软碟通>>>写入硬盘镜像>>>usb-hdd+

详细的安装过程可参见[笨小孩](http://blog.csdn.net/coderjyf/article/details/51241919)

</div>

参考的系统分区方案：

+ Root分区：15G
+ Boot分区：250M
+ SWAP分区：2G
+ Home分区：the Rest

## 系统美化

可以从[gnome-look.org](  https://www.gnome-look.org/)寻找更多适合自己的主题。

### 安装主题

将下载的主题包解压置于桌面，之后使用命令行将主题文件夹MOVE到 `/use/share/themes ` 文件夹之下。

过程如下（以文件夹在桌面为例，且文件夹名为 `themepacks` ）：

```bash
 ls   //在桌面启动终端并输入ls
 move -r /home/allen/桌面/themepacks /usr/share/themes/
```

之后在 `gnome-tweak` 中找到自己刚刚安装的主题就好。


### 主题推荐

+ gtk+主题：[apple](https://www.gnome-look.org/p/1013481/)
+ 图标：[paper](https://www.gnome-look.org/p/1099618/#myCarousel)
+ shell主题：[flat](https://www.gnome-look.org/p/1012908/#about-panel)
+ 字体：google noto

### 插件和其他

+ 最大化按钮：
 <div class="note info no-icon">

 `dconf` 内搜索 `button-layout` 项目，将其值修改为：`close,minimize,maximize,spacer:menu` 即可。(可以修改三个按钮的位置全部显示且使之位于标题栏左端，可按需要调试）</div>

+ gnome shell extensions

 <div class="note info no-icon">

 更新于2019-8-25：
 先在浏览器扩展插件商店内安装 `gnome shell intergration`。
 之后在本地安装连接器： `sudo apt install chrome-gnome-shell`
 之后打开 `gnome shell extension` 商店即可在线安装插件。 </div>

 <div class="note info no-icon">
 
 可以通过 `mozilla firefox` 在线安装（似乎只有火狐浏览器支持，我用 `chrome` 和 `chomium` 都没有反应，可能是我不小心关闭了什么选项）</div>

## 软件安装

###  Chrome

<div class="note info">

更新于2019-08-22：

现在已经可以通过 Google-Chrome 官网下载 `deb` 安装包。

</div>

```bash
 sudo wget https://repo.fdzh.org/chrome/google-chrome.list -P /etc/apt/sources.list.d/
 wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install google-chrome-stable
```

###  [~~Bleachbits~~](http://www.bleachbit.org/download)（清理垃圾）

<div class="note info">

已替换为 `stacer`。</div>

安装如下：
```bash
sudo add-apt-repository ppa:oguzhaninan/stacer -y
sudo apt-get update
sudo apt-get install stacer -y 
```

### Coffeine（观看视频时不自动黑屏）

<div class="note info">

现在已经可以通过软件商店或者 新立德 安装。</div>

```bash
sudo add-apt-repository ppa:caffeine-developers/ppa
sudo apt-get update
sudo apt-get install caffeine
```

### Variety（壁纸自动换）

<div class="note info">

现在已经可以通过软件商店或者 新立德 安装。</div>

```bash
sudo add-apt-repository ppa:peterlevi/ppa
sudo apt-get update
sudo apt-get install variety
```

### Fcitx（小企鹅中文输入法）

<div class="note info">via synaptic</div>

### kazam（截屏，录像软件）

```bash
sudo add-apt-repository ppa:kazam-team/stable-series
sudo apt-get update
sudo apt-get install kazam
```

### typora（用来写Markdown）

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
sudo add-apt-repository 'deb https://typora.io ./linux/'
sudo apt-get update
sudo apt-get install typora
```

### node.js

<div class="note info">

现在已经可以通过软件商店或者 新立德 安装。</div>

### ibus-rime

```bash
sudo apt-get install ibus-rime
```
关于该软件的配置可参照[安装地址](https://github.com/rime/home/wiki/RimeWithIBus)，[配置方法](https://github.com/rime/home/wiki/UserGuide)，
也可参照[致第一次安装 RIME 的你之修订版](http://tieba.baidu.com/p/3288634121),虽然是windows平台上的但依然可以借鉴。

### [~~Intellj idea~~](http://www.jetbrains.com/idea/#chooseYourEdition)（用来制作网页，书写javascript等）

###  [~~Neatease~~](http://music.163.com/#/download)（网易云音乐）

### [~~Lantern~~](https://github.com/getlantern/forum/issues/833#issue-167517328)（#番#羽#土#啬）

### [~~gitkraken~~](https://www.gitkraken.com/download)(git的视窗软件）

<div class="note info">

现在已经可以通过软件商店或者 新立德 安装。</div>

### [~~brackets~~](https://github.com/adobe/brackets/releases)（Adobe的软件，网页编辑器）

<div class="note info">

现在已经可以通过软件商店或者 新立德 安装。</div>

### [~~vmvare player~~](http://www.vmware.com/products/player/playerpro-evaluation.html)（虚拟机）

### [~~f.lux~~](https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/flux/+packages)（自动调色温的软件，保护视力）

<div class="note info">

现在已经可以通过软件商店或者 新立德 安装。</div>

### ~~Synaptic~~(新立德软件管理器）

```bash
sudo apt-get install synaptic
```

###   ~~Docky~~

<div class="note info">

现在已经可以通过软件商店或者 新立德 安装。</div>

```bash
sudo add-apt-repository ppa:docky-core/stable
sudo apt-get update
sudo apt-get install docky
```

###  ~~Shotwell~~（相册软件)

<div class="note info">via gnome-software-store</div>

## NumLock

在終端中執行以下命令.

```bash
sudo apt-get install numlockx
sudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
在最后添加：
greeter-setup-script=/usr/bin/numlockx on
```

重啟或註銷後,就會發現小鍵盤燈已啟用.

## 亮度調節工具

```bash
sudo apt-get -f install
sudo add-apt-repository ppa:indicator-brightness/ppa
sudo apt-get update && sudo apt-get install indicator-brightness
```

## 刪除不用的舊内核

### 自动移除Ubuntu 16.04旧版内核

1. 使用如下命令可以自动移除 Ubuntu 16.04 系统不再需要的旧版内核和软件包：

```bash
sudo apt autoremove --purge
```

2. 在终端中执行如下命令启用无人值守升级：

```bash
sudo dpkg-reconfigure unattended-upgrades
```

3. 使用 `vi` 或 `nano` 将  `/etc/apt/apt.conf.d/50unattended-upgrades` 配置文件中的` Unattended-Upgrade::Remove-Unused-Dependencies false`; 改为 `ture` 即可。

### 半自动移除Ubuntu 16.04旧版内核

如果你从 `Kernel PPA` 安装过最新内核或安装过自己手动编译的内核，那 `purge-old-kernels` 脚本便是清除这些老旧版本内核的最佳办法。

1. 先使用如下命令安装  `byobu` 包：

```bash
sudo apt install byobu
```

2. 再定期执行如下命令即可：

```bash
sudo purge-old-kernels
```

### 手动移除Ubuntu 16.04旧版内核

如果你的 `/boot` 分区已满，无法再使用 `apt` 来升级、安装和移除软件包及相关依赖，此时便可以使用 `dpkg` 命令以全手动的方式来进行操作：

1. 查看当前 `Kernel` 版本：

```bash
uname -r
```

2. 列出不包括当前内核版本的其它所有内核版本：

```bash
dpkg -l | tail -n +6| grep -E 'linux-image-[0-9]+'| grep -Fv $(uname -r)
```

输出的内容中可能会包括内核映像的如下三种状态：

+ rc：表示已经被移除
+ ii：表示符合移除条件（可移除）
+ iU：已进入 apt 安装队列，但还未被安装（不可移除）。

3. 例如要移除状态为 `ii` 的旧版 `linux-image-4.4.0-21-generic` 内核，可以使用如下命令：

```bash
sudo dpkg --purge linux-image-4.4.0-21-generic
```
## 系統使用貼士

###  Ubuntu桌面上创建文件夹快捷方式

```bash
ln -s /home/allen/下载 /home/allen/桌面
```

### 复制文件

```bash
cp -r 文件夹 文件夹
```

### 删除文件

```bash
rm -rf 文件夹
```

### 移动文件

```bash
mv -r 文件夹 文件夹
```

### 安装bundle文件

```bash
ls【回车】
sudo【空格】chmod【空格】+x【空格 】XXXXX.bundle【回车】
sudo【空格】./XXXXX.bundle【回车】
```

### 使ibus输入法横向显示

打开dconf editor，搜索ibus，找到panel列，修改其中的lookup-table-orientation为0，即可使之横向显示，修改为1可使之纵向显示。

## 双系统下正确删除Linux系统的方法

`XP`  或`win7+Linux`  双系统时，要删除 `Linux`  系统，一定不能直接格式化 `Linux`  所在分区。否则会进入<mark>`grub rescue`</mark>。

1、从网上下载工具`MbrFix`；
2、将工具`MbrFix.exe`解压到C盘根目录下；
3、打开`cmd`命令，即“开始——运行——输入`cmd`命令——回车”；
4、在C盘根目录下输入命令`MbrFix /drive 0 fixmbr`，它会提示`You are about to Fix MBR,are you sure ?` 输入`Y`，回车即可。
5、重启电脑后会发现，就可以删除`Linux`所在分区了。

如果不慎不正确删除了 `Linux` 分区，如果有U盘的话，可以下载安装 `WinPE` ，使用其中的分区助手重建 `MBR`。不同的 `WinPE` 可能方法稍有区别：

老毛桃：[链接](http://www.laomaotao.org/softhelp/syjc/1193.html)。

其他的可以仿照此方法。