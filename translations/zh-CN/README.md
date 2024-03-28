<p align="center">
  <img src="../../assets/img/bulb.svg" alt="light bulb icon">
</p>

# CSS 专业技巧 [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

一个帮你提升 CSS 技巧的收藏集。

> 对于其他收藏集合可以查看 [@sindresorhus](https://github.com/sindresorhus/) 创建的收藏集合 [Awesome Lists](https://github.com/sindresorhus/awesome/).


<div id="table-of-contents"></div>

## 目录

* [专业技巧](#专业技巧)
* [支持情况](#支持情况)
* [贡献准则](../../CONTRIBUTING.md)


## 专业技巧

1. [使用CSS复位](#使用css复位)
1. [继承 `box-sizing`](#继承-box-sizing)
1. [使用`unset`而不是重置所有属性](#使用unset而不是重置所有属性)
1. [使用 `:not()` 选择器来决定表单是否显示边框](#使用-not-选择器来决定表单是否显示边框)
1. [检查字体是否在本地安裝](#检查字体是否在本地安裝)
1. [为 body 元素添加行高](#为-body-元素添加行高)
1. [为表单元素设置`:focus`](#为表单元素设置focus)
1. [垂直居中任何元素](#垂直居中任何元素)
1. [逗号分隔的列表](#逗号分隔列表)
1. [使用负的 `nth-child` 来选择元素](#使用负的-nth-child-来选择元素)
1. [使用 SVG 图标](#使用-svg-图标)
1. [使用 “形似猫头鹰” 的选择器](#使用-形似猫头鹰-的选择器)
1. [使用 `max-height` 来建立纯 CSS 的滑块](#使用-max-height-来建立纯-css-的滑块)
1. [创造格子等宽的表格](#创造格子等宽的表格)
1. [利用 Flexbox 去除多余的外边距](#利用-flexbox-去除多余的外边距)
1. [利用属性选择器来选择空链接](#利用属性选择器来选择空链接)
1. [给 “默认” 链接定义样式](#给-默认-链接定义样式)
1. [内在比例盒](#固定比例盒子)
1. [为图裂定义样式](#为图裂定义样式)
1. [用 rem 来调整全局大小；用 em 来调整局部大小](#用-rem-来调整全局大小用-em-来调整局部大小)
1. [隐藏没有静音、自动播放的影片](#隐藏没有静音自动播放的影片)
1. [使用选择器 `:root` 来控制字体弹性](#使用选择器root来控制字体弹性)
1. [为更好的移动体验，为表单元素设置字体大小](#为更好的移动体验为表单元素设置字体大小)
1. [使用指针事件来控制鼠标事件](#使用指针事件来控制鼠标事件)
1. [在用作间距的换行符上设置`display-none`](#在用作间距的换行符上设置display-none)
1. [使用 `:empty` 隐藏空 HTML 元素](#使用-empty-隐藏空-html-元素)


### 使用CSS复位

CSS复位可以在不同的浏览器上保持一致的样式风格。您可以使用CSS reset 库[Normalize](http://necolas.github.io/normalize.css/)等，也可以使用一个更简化的复位方法：

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

现在元素的 margin 和 padding 已为0，`box-sizing`可以管理您的CSS盒模型布局。

#### [演示](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

注意：如果你遵循接下来[继承 `box-sizing`](#inherit-box-sizing)讲解的这个技巧, 你不需要在以上代码中添加 `box-sizing` 属性。

<sup>[回目录](#目录)</sup>


### 继承 `box-sizing`

从 `html` 元素继承 `box-sizing` ：

```css
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

如此在插件或其它组件里改变 `box-sizing` 变得简单。

#### [演示](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[回目录](#目录)</sup>


### 使用`unset`而不是重置所有属性

重置元素的属性时，不需要重置每个单独的属性：

```css
button {
  background: none;
  border: none;
  color: inherit;
  font: inherit;
  outline: none;
  padding: 0;
}
```

你可以用`all`简写來指定所有元素的属性。 将该值设置为`unset`会将元素的属性更改为其初始值：

```css
button {
  all: unset;
}
```

<sup>[回目录](#目录)</sup>


### 使用 `:not()` 选择器来决定表单是否显示边框

先为元素添加边框

```css
/* 添加边框 */
.nav li {
  border-right: 1px solid #666;
}
```

为最后一个元素去除边框

```css
/* 去掉边框 */
.nav li:last-child {
  border-right: none;
}
```

不过不要这么做，使用 `:not()` 伪类来达到同样的效果：

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

CSS选择器以人类描述它的方式定义边界。

#### [演示](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[回目录](#目录)</sup>


### 检查字体是否在本地安裝

您可以在远程获取字体之前检查是否在本地安装了字体，这也是一个很好的性能提示。

```css
@font-face {
  font-family: "Dank Mono";
  src:
    /* Full name */
    local("Dank Mono"),
    /* Postscript name */
    local("Dank-Mono"),
    /* Otherwise, download it! */
    url("//...a.server/fonts/DankMono.woff");
}

code {
  font-family: "Dank Mono", system-ui-monospace;
}
```

亚当·阿盖尔（Adam Argyle）的帽子技巧，分享了这个技巧和[例子](https://codepen.io/argyleink/pen/VwYJpgR)。

<sup>[回目录](#目录)</sup>


### 为 `body` 元素添加行高

不必为每一个 `<p>`，`<h*>` 元素逐一添加 `line-height`，直接添加到 `body` 元素：

```css
body {
  line-height: 1.5;
}
```

文本元素可以很容易地继承 `body` 的样式。

#### [演示](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[回目录](#目录)</sup>


### 为表单元素设置`:focus`

有视力的键盘用戶依靠焦点来确定键盘事件在页面中的位置。 使表单元素的焦点脱颖而出，然后与浏览器的默认实现保持一致：

```css
a:focus,
button:focus,
input:focus,
select:focus,
textarea:focus {
  box-shadow: none;
  outline: #000 dotted 2px;
  outline-offset: .05em;
}
```

#### [演示](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[回目录](#目录)</sup>


### 垂直居中任何元素

不！这绝不是黑魔法，真的可以垂直居中任何元素：

```css
html,
body {
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

...还有CSS Grid:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

这还不够？垂直方向，水平方向？任何元素，任何时间，任何地点？CSS-Tricks [有篇好文](https://css-tricks.com/centering-css-complete-guide/) 讲到了各种居中的技巧。

#### [演示](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[回目录](#目录)</sup>


### 逗号分隔列表

使列表的每项都由逗号分隔：

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

因最后一项不加逗号，可以使用 `:not()` 伪类。

**注意：** 这一技巧对于无障碍，特别是屏幕阅读器而言并不理想。而且复制粘贴并不会带走CSS生成的内容，需要注意。

<sup>[回目录](#目录)</sup>


### 使用负的 `nth-child` 来选择元素

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

或许你已经掌握了[如何使用 `:not()`](#use-not-to-applyunapply-borders-on-navigation)这个技巧，试下这个：

```css
/* 选择除前3个之外的所有项目，并显示它们 */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

如此简单！

#### [演示](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[回目录](#目录)</sup>


### 使用 SVG 图标

没有理由不使用 SVG 图标：

```css
.logo {
  background: url("logo.svg");
}
```

SVG 在所有分辨率下都可以良好缩放，并且支持所有 [IE9](https://caniuse.com/#search=svg) 以后的浏览器，丢掉你的 .png，.jpg，或 .gif-jif-whatev 文件吧。

**注意：** 针对仅有图标的按钮，如果 SVG 没有加载成功的话，以下样式对无障碍有所帮助：

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[回目录](#目录)</sup>


### 使用 “形似猫头鹰” 的选择器

这个名字可能比较陌生，不过通用选择器 (`*`) 和 相邻兄弟选择器 (`+`) 一起使用，效果非凡：

```css
* + * {
  margin-top: 1.5em;
}
```

在此示例中，文档流中的所有的相邻兄弟元素将都将设置 `margin-top: 1.5em` 的样式。

更多 “形似猫头鹰”  的选择器，可参考 *A List Apart* 上面 [Heydon Pickering 的文章](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls)

#### [演示](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[回目录](#目录)</sup>


### 使用 `max-height` 来建立纯 CSS 的滑块

`max-height` 与 overflow hidden 一起来建立纯 CSS 的滑块：

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

鼠标移入滑块元素时增大它的 `max-height` 值，便可以显示溢出部分。

<sup>[回目录](#目录)</sup>


### 创造格子等宽的表格

`table-layout: fixed` 可以让每个格子保持等宽：

```css
.calendar {
  table-layout: fixed;
}
```

无痛的 table 布局。

#### [演示](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[回目录](#目录)</sup>


### 利用 Flexbox 去除多余的外边距

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

列之间的间隙总是均匀相等。

<sup>[回目录](#目录)</sup>


### 利用属性选择器来选择空链接

当 `<a>` 元素没有文本内容，但有 `href` 属性的时候，显示它的 `href` 属性：

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

相当简便。

#### [演示](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[回目录](#目录)</sup>


### 给 “默认” 链接定义样式

给 “默认” 链接定义样式：

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

通过 CMS 系统插入的链接，通常没有 `class` 属性，以上样式可以甄别它们，而且不会影响其它样式。

<sup>[回目录](#目录)</sup>


### 固定比例盒子

要创建具有固定比例的一个盒子，所有你需要做的就是给 div 的顶部或底部设置一个 padding：

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

使用 20％ 的 padding-bottom 使得框等于其宽度的 20％ 的高度。与视口宽度无关，子元素的 div 将保持其宽高比（100％/ 20％= 5:1）。

#### [演示](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[回目录](#目录)</sup>


### 为图裂定义样式

只要一点CSS就可以美化破损的图片：

```css
img {  
  display: block;
  font-family: sans-serif;
  font-weight: 300;
  height: auto;
  line-height: 2;
  position: relative;
  text-align: center;
  width: 100%;
}
```

以添加伪元素的法则来显示用户信息和URL的引用：

```css
img::before {  
  content: "We're sorry, the image below is broken :(";
  display: block;
  margin-bottom: 10px;
}

img::after {  
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

了解更多关于这类样式的技巧 [Ire Aderinokun](https://github.com/ireade/) 的 [原帖](http://bitsofco.de/styling-broken-images/).

<sup>[回目录](#目录)</sup>


### 用 `rem` 来调整全局大小；用 `em` 来调整局部大小

在根元素设置基本字体大小后 (`html { font-size: 100%; }`), 使用 `em` 设置文本元素的字体大小:

```css
h2 { 
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

然后设置模块的字体大小为 `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

现在，每个模块变得独立，更容易、灵活的样式便于维护。

<sup>[回目录](#目录)</sup>


### 隐藏没有静音、自动播放的影片

这是一个自定义用户样式表的不错的技巧。避免在加载页面时自动播放。如果没有静音，则不显示视频：

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

再次，我们利用了 [`:not()`](#use-not-to-applyunapply-borders-on-navigation) 的优点。

<sup>[回目录](#目录)</sup>


### 使用选择器`:root`灵活控制字体大小

在响应式布局中，字体大小应需要根据不同的视口进行调整。你可以计算字体大小根据视口高度的字体大小和宽度，这时需要用到`:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

现在，您可以使用 `root em` 

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [演示](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[回目录](#目录)</sup>


### 为更好的移动体验，为表单元素设置字体大小

当触发`<select>`的下拉列表时，为了避免表单元素在移动浏览器（iOS Safari 和其它）上的缩放，加上`font-size`：

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[回目录](#目录)</sup>


### 使用指针事件来控制鼠标事件

[指针事件](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events)允许您指定鼠标如何与其触摸的元素进行交互。 要禁用按钮上的默认指针事件，例如：

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

就这么简单。

<sup>[回目录](#目录)</sup>


### 在用作间距的换行符上设置`display: none`

正如[Harry Roberts指出](https://twitter.com/csswizardry/status/1170835532584235008)，这有助于防止CMS用户使用额外的换行符

```css
br + br {
  display: none;
}
```

<sup>[回目录](#目录)</sup>

### 使用 `:empty` 隐藏空 HTML 元素

如果你有空的 HTML 元素，即内容尚未由 CMS 设置或动态注入（例如：`<p class="error-message"></p>`）并且它会在你的布局上创建不需要的空间，使用 `:empty` 伪类隐藏布局上的元素。

```css
:empty {
  display: none;
}
```

注意：请记住，带有空格的元素不会被视为空元素，例如 `<p class="error-message"> </p>`。

<sup>[回目录](#目录)</sup>


### 支持情况

这些技巧适用于最新版的 Chrome, Firefox, Safari, 以及 Edge。
