<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" alt="light bulb icon">
</p>

# CSS 专业的技巧 [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

提示的集合，以帮助把你的CSS技巧亲。

> 对于其他大名单退房 [@sindresorhus](https://github.com/sindresorhus/)的策展的名单 [真棒名单](https://github.com/sindresorhus/awesome/).


<div id="table-of-contents"></div>
## 目录

* [专业的技巧](#protips)
* [支持情况](#support)
* [贡献准则](../../CONTRIBUTING.md)


<div id="protips"></div>
## 专业的技巧

1. [使用 `:not()` 选择器决定导航菜单是否显示边框](#use-not-to-applyunapply-borders-on-navigation)
1. [给 `body` 元素加行高](#add-line-height-to-body)
1. [垂直居中任何元素](#vertically-center-anything)
1. [逗号分隔的列表](#comma-separated-lists)
1. [使用负的 `nth-child` 选择元素](#select-items-using-negative-nth-child)
1. [使用 SVG 图标](#use-svg-for-icons)
1. [使用 "形似猫头鹰" 的选择器](#use-the-lobotomized-owl-selector)
1. [使用 `max-height` 实现纯 CSS 滑块](#use-max-height-for-pure-css-sliders)
1. [继承 `box-sizing`](#inherit-box-sizing)
1. [格子等宽的表格](#equal-width-table-cells)
1. [利用 Flexbox 去除多余的 Margin](#get-rid-of-margin-hacks-with-flexbox)
1. [利用属性选择器选择空链接](#use-attribute-selectors-with-empty-links)
1. [给"默认"链接定义样式](#style-default-links)
1. [垂直节奏一致性](#consistent-vertical-rhythm)
1. [内在比例盒](#intrinsic-ratio-boxes)
1. [风格破碎的形象](#style-broken-images)
1. [使用 `rem` 全球上浆; 使用 `em` 本地浆纱](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [隱藏自動播放的影片，沒有靜音](#hide-autoplay-videos-that-arent-muted)
1. [使用`:root`柔性型](#use-root-for-flexible-type)


<div id="use-not-to-applyunapply-borders-on-navigation"></div>
### 使用 `:not()` 选择器决定导航菜单是否显示边框

与其加上边框...

```css
/* 添加边框 */
.nav li {
  border-right: 1px solid #666;
}
```

...然后去掉最后一个元素的边框...

```css
/* 去掉边框 */
.nav li:last-child {
  border-right: none;
}
```

...不如使用 `:not()` 伪类实现同样的效果：

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

当然，也可以使用 `.nav li + li` 或者 `.nav li:first-child ~ li` 实现，但是 `:not()` 选择器的实现更清晰明了，一目了然。

<sup>[回目录](#table-of-contents)</sup>


<div id="add-line-height-to-body"></div>
### 给 `body` 元素加行高

不必给每一个 `<p>`，`<h*>`，_等元素_逐一添加 `line-height`，给 `body` 元素添加就好了：

```css
body {
  line-height: 1;
}
```

文本元素可以很自然地继承 `body` 的样式。

<sup>[回目录](#table-of-contents)</sup>


<div id="vertically-center-anything"></div>
### 垂直居中任何元素

这不是黑魔法，就是可以垂直居中任何元素：

```css
html, body {
  height: 100%;
  margin: 0;
}

body {
  -webkit-align-items: center;  
  -ms-flex-align: center;  
  align-items: center;
  display: -webkit-flex;
  display: flex;
}
```

这还不够？垂直方向，水平方向...任何元素，任何时间，任何地方？CSS-Tricks [有篇好文](https://css-tricks.com/centering-css-complete-guide/) 讲到了各种居中的实现。

**注意：** IE11 对 flexbox 的支持[有点 bug](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items)。

<sup>[回目录](#table-of-contents)</sup>


<div id="comma-separated-lists"></div>
### 逗号分隔的列表

列表的每项都由逗号分隔：

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

使用了 `:not()` 伪类，因此最后一项没加逗号。

**注意：**这一实现对于无障碍，屏幕阅读器而言并不理想，需要注意。

<sup>[回目录](#table-of-contents)</sup>


<div id="select-items-using-negative-nth-child"></div>
### 使用负的 `nth-child` 选择元素

使用负的 `nth-child` 可以选择 1 至 n 个元素。


```css
li {
  display: none;
}

/* 选择第 1 至第 3 个元素并显示出来 */
li:nth-child(-n+3) {
  display: block;
}
```

或许你已经掌握了[如何使用 `:not()`](#use-not-to-applyunapply-borders-on-navigation)，试下这个：

```css
/* 选择第 1 至第 3 个元素并显示出来 */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

就是这么简单。

<sup>[回目录](#table-of-contents)</sup>


<div id="use-svg-for-icons"></div>
### 使用 SVG 图标

没有理由不使用 SVG 图标：

```css
.logo {
  background: url("logo.svg");
}
```

SVG 在所有分辨率下都可以良好缩放，IE9+ 及其它所有浏览器都支持，丢掉你的 .png, .jpg, 或 .gif-jif-whatev 文件吧。

**注意：** 针对仅有图标的按钮，如果 SVG 没有加载成功的话，以下样式对无障碍性有所帮助：

```css
.no-svg .icon-only:after {
  content: attr(aria-label);
}
```

<sup>[回目录](#table-of-contents)</sup>


<div id="use-the-lobotomized-owl-selector"></div>
### 使用 "形似猫头鹰" 的选择器

这个名字可能比较陌生，不过全局选择器 (`*`) 和 相邻兄弟选择器 (`+`) 一起使用，效果非凡：

```css
* + * {
  margin-top: 1.5em;
}
```

此例中，文档流里紧跟在其它元素后面的所有元素具有 `margin-top: 1.5em` 的样式。

更多 "形似猫头鹰" 的选择器，可参考 *A List Apart* 上面 [Heydon Pickering 的文章](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls)

<sup>[回目录](#table-of-contents)</sup>


<div id="use-max-height-for-pure-css-sliders"></div>
### 使用 `max-height` 实现纯 CSS 滑块

`max-height` 与 overflow hidden 一起实现纯 CSS 的滑块：

```css
.slider {
  max-height: 200px;
  overflow-y: hidden;
  width: 300px;
}

.slider:hover {
  max-height: 600px;
  overflow-y: scroll;
}
```

移入滑块元素时增大它的 `max-height` 的值，便可以显示溢出部分。

<sup>[回目录](#table-of-contents)</sup>


<div id="inherit-box-sizing"></div>
### 继承 `box-sizing`

从 `html` 元素继承 `box-sizing` 就好：

```css
html {
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}
```

如此在插件或其它组件里改变 `box-sizing` 变得简单。

<sup>[回目录](#table-of-contents)</sup>


<div id="equal-width-table-cells"></div>
### 格子等宽的表格

`table-layout: fixed` 可以让每个格子保持等宽：

```css
.calendar {
  table-layout: fixed;
}
```

无痛的 table 布局。

<sup>[回目录](#table-of-contents)</sup>


<div id="get-rid-of-margin-hacks-with-flexbox"></div>
### 利用 Flexbox 去除多余的 Margin

与其使用 `nth-`， `first-`， 和 `last-child` 去除列之间多余的间隙，不如使用 flexbox 的 `space-between` 属性：

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

列之间的间隙相等，并且首尾没有多余的间隙。

<sup>[回目录](#table-of-contents)</sup>


<div id="use-attribute-selectors-with-empty-links"></div>
### 利用属性选择器选择空链接

当 `<a>` 元素没有文本内容，但是有 `href` 属性的时候，可以显示它的 `href` 链接：

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

相当简便。

<sup>[回目录](#table-of-contents)</sup>


<div id="style-default-links"></div>
### 给"默认"链接定义样式

给"默认"链接定义样式：

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

通过 CMS 系统插入的链接，通常没有 `class` 属性，以上样式可以甄别它们，而且不会影响其它样式。

<sup>[回目录](#table-of-contents)</sup>


<div id="consistent-vertical-rhythm"></div>
### 垂直节奏一致性

通用选择器 (`*`) 跟元素一起使用，可以保持一致的垂直节奏：

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

一致的垂直节奏可以提供视觉美感，增强内容的可读性。

<sup>[回目录](#table-of-contents)</sup>


<div id="intrinsic-ratio-boxes"></div>
### 内在比例盒

要创建具有内在比一个盒子，所有你需要做的就是应用顶部或底部填充，以一个div：

```css
.container {
  height: 0;
  padding-bottom: 20%;
  position: relative;
}

.container div {
  border: 2px dashed #ddd;	
  height: 100%;
  left: 0;
  position: absolute;
  top: 0;
  width: 100%;
}
```

使用20％的填充使得框等于其宽度的20％的高度。不管视口的宽度，孩子的div将保持其宽高比（100％/ 20％= 5:1）。

<sup>[回目录](#table-of-contents)</sup>


<div id="style-broken-images"></div>
### 风格破碎的形象

让破碎的形象与CSS一点点更美观的：

```css
img {  
  display: block;
  font-family: Helvetica, Arial, sans-serif;
  font-weight: 300;
  height: auto;
  line-height: 2;
  position: relative;
  text-align: center;
  width: 100%;
}
```

现在添加伪元素的规则来显示用户信息和虚线图像的URL引用：

```css
img:before {  
  content: "We're sorry, the image below is broken :(";
  display: block;
  margin-bottom: 10px;
}

img:after {  
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

了解更多关于造型此模式中 [Ire Aderinokun](https://github.com/ireade/)的 [原帖](http://bitsofco.de/styling-broken-images/).

<sup>[回目录](#table-of-contents)</sup>


<div id="use-rem-for-global-sizing-use-em-for-local-sizing"></div>
### 使用 `rem` 全球上浆; 使用 `em` 本地浆纱

在根設置基本字體大小後 (`html { font-size: 16px; }`), 設置為文本元素的字體大小 `em`:

```css
h2 { 
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

然後設置字體大小的模塊 `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

現在，每個模塊變得條塊分割，更容易的風格，更易於維護和靈活。

<sup>[回目录](#table-of-contents)</sup>


<div id="hide-autoplay-videos-that-arent-muted"></div>
### 隱藏自動播放的影片，沒有靜音

這是一個自定義的用戶樣式表一個偉大的把戲。避免在加載頁面時自動播放視頻超載有聲的用戶。如果沒有靜音，不顯示視頻：

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

再次，我們趁著使用的 [`:not()`](#use-not-to-applyunapply-borders-on-navigation) 偽類。

<sup>[回目录](#table-of-contents)</sup>


<div id="use-root-for-flexible-type"></div>
### 使用`:root`柔性型

在响应式布局的类型字体大小应能与每个视口进行调整。你可以计算的基础上视口高度的字体大小和宽度，使用`:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

现在，您可以利用基于'计算的值`root em`单位：root`:

```css
body {
  font: 1em/1.6rem sans-serif;
}
```

<sup>[回目录](#table-of-contents)</sup>


### 支持情况

这些技巧适用于最新版的 Chrome, Firefox, Safari, Opera, Edge, 以及 IE11。
