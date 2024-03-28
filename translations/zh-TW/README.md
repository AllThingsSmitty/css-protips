<p align="center">
  <img src="../../assets/img/bulb.svg" alt="light bulb icon">
</p>

# CSS 專家密技 [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

這裡收集了一系列 CSS 專家密技，幫助你提升 CSS 技能點數。

> 更多專家密技可以查看 [@sindresorhus](https://github.com/sindresorhus/) 的 [Awesome Lists](https://github.com/sindresorhus/awesome/)

> 正體中文由 [Will 保哥](http://blog.miniasp.com/) 翻譯，歡迎造訪 [Will 保哥的技術交流中心](https://www.facebook.com/will.fans)


<div id="table-of-contents"></div>

## 目錄

* [專家密技](#專家密技)
* [瀏覽器支援度](#瀏覽器支援度)
* [貢獻準則](../../CONTRIBUTING.md)

## 專家密技

1. [使用 CSS Reset](#使用-css-reset)
1. [繼承 `box-sizing`](#繼承-box-sizing)
1. [使用 `unset` 而不是重置所有屬性](#使用-unset-而不是重置所有屬性)
1. [使用 `:not()` 選擇器來決定表單是否顯示邊框](#使用-not-選擇器來決定表單是否顯示邊框)
1. [检查字体是否在本地安装](#检查字体是否在本地安装)
1. [將 `line-height` 加入到 `body` 元素](#將-line-height-加入到-body-元素)
1. [為表單元素設定`focus`](#為表單元素設定focus)
1. [將所有元素設定垂直居中](#將所有元素設定垂直居中)
1. [逗號分隔列表](#逗號分隔列表)
1. [使用負數的 `nth-child` 來選擇元素](#使用負數的-nth-child-來選擇元素)
1. [使用 SVG 圖示](#使用-svg-圖示)
1. [使用 "貓頭鷹" 的選擇器](#使用-貓頭鷹-選擇器)
1. [使用 `max-height` 來建立純 CSS 的捲動軸](#使用-max-height-來建立純-css-的捲動軸)
1. [讓表格中每個儲存格維持等寬](#讓表格中每個儲存格維持等寬)
1. [利用 Flexbox 去除多餘的 Margin 技巧](#利用-flexbox-去除多餘的-margin-技巧)
1. [利用屬性選擇器填滿空白連結的文字內容](#利用屬性選擇器填滿空白連結的文字內容)
1. [幫沒有類別的連結設定一個預設樣式](#幫沒有類別的連結設定一個預設樣式)
1. [等比例的方塊](#等比例的方塊)
1. [為破圖定義樣式](#為破圖定義樣式)
1. [用 `rem` 來調整全域大小；用 `em` 來調整區域大小](#用-rem-來調整全域大小用-em-來調整區域大小)
1. [隱藏沒有靜音並設定自動播放的影片](#隱藏沒有靜音並設定自動播放的影片)
1. [使用 `:root` 選擇器來設定彈性的字體大小](#使用-root-選擇器來設定彈性的字體大小)
1. [為了更好的行動體驗來設定表單元素的 `font-size`](#為了更好的行動體驗來設定表單元素的-font-size)
1. [使用指標事件來控制滑鼠事件](#使用指標事件來控制滑鼠事件)
1. [在用作間距的換行符上設置`display: none`](#在用作間距的換行符上設置display-none)


### 使用 CSS Reset

CSS Reset 可以幫你在不同的瀏覽器上維持一致的樣式風格。你可以使用像 [Normalize](http://necolas.github.io/normalize.css/) 這類的 CSS Reset 套件，或使用更簡潔的 CSS Reset 方法：

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

現在元素的 margin 和 padding 已重設，且 `box-sizing` 可以讓你透過 CSS Box Model 管理版面配置。

#### [示範](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

注意：如果你接著套用 [繼承 `box-sizing`](#繼承-box-sizing) 這個技巧, 你或許不需要在你的 CSS Reset 中加入 `box-sizing` 屬性。

<sup>[回到目錄](#table-of-contents)</sup>

### 繼承 `box-sizing`

讓 `box-sizing` 屬性自動從 `html` 元素繼承下來 ：

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

如此一來，你就很容易的在其他外掛或元件裡改變 `box-sizing` 的值。

#### [示範](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[回到目錄](#table-of-contents)</sup>

### 使用 `unset` 而不是重置所有屬性

當重置元素的屬性時，並不需要重置元素中每個屬性：

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

你可以用 `all` 來代表元素中所有的樣式屬性。 將該值設定為 `unset` 意味著將元素中所有樣式屬性回復到預設值：

```css
button {
  all: unset;
}
```

<sup>[回到目錄](#table-of-contents)</sup>

### 使用 `:not()` 選擇器來決定表單是否顯示邊框

假設你用以下樣式先替元素新增邊框

```css
/* 新增邊框 */
.nav li {
  border-right: 1px solid #666;
}
```

然後在最後一個元素去除邊框

```css
/* 去掉邊框 */
.nav li:last-child {
  border-right: none;
}
```

不過你可以改用 `:not()` 偽類別 (pseudo-class) 來做到完全相同的效果：

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

CSS選擇器以人類描述它的方式定義邊界。

#### [示範](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[回到目錄](#table-of-contents)</sup>


### 检查字体是否在本地安装

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

亚当·阿盖尔（Adam Argyle）的帽子技巧，分享了这个技巧和[例子](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[回到目錄](#table-of-contents)</sup>


### 將 `line-height` 加入到 `body` 元素

你不必為分別為每一個 `<p>`、`<h*>` 元素加入 `line-height` 樣式，相反的，你應該直接新增到 `body` 元素：

```css
body {
  line-height: 1.5;
}
```

所有的文字元素預設就會繼承 `body` 的樣式。

#### [示範](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[回到目錄](#table-of-contents)</sup>


### 為表單元素設定`focus`

視力正常的鍵盤使用者依靠焦點來確認鍵盤事件在頁面中的位置。使表單元素的焦點脫穎而出，然後與瀏覽器的預設實作保持一致：

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

#### [Demo](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[回到目錄](#table-of-contents)</sup>


### 將所有元素設定垂直居中

不！這絕不是黑魔法，這真的可以將所有元素設定垂直居中：

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

...還有 CSS Grid:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

還想居中排版其他的東西？垂直居中、水平居中、... 任何事、任何時間、任何地點？CSS-Tricks [有篇不錯的文章](https://css-tricks.com/centering-css-complete-guide/) 提到了各種居中排版的技巧。

#### [示範](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[回到目錄](#table-of-contents)</sup>

### 逗號分隔列表

使列表的每項都由逗號分隔：

```css
ul > li:not(:last-child)::after {
  content: ',';
}
```

列表中最後一項不用加逗號，所以可以使用 `:not()` 偽類別 (pseudo-class) 。

**注意：**這一技巧對於無障礙網頁，特別是螢幕閱讀器而言，並不理想。而且預設要複製貼網頁內容時，並不會包含 CSS 動態產生的內容，這點必須特別注意。

<sup>[回到目錄](#table-of-contents)</sup>

### 使用負數的 `nth-child` 來選擇元素

使用負數的 `nth-child` 可以選擇 1 至 n 個元素。

```css
li {
  display: none;
}

/* 選擇第 1 至第 3 個元素並顯示出來 */
li:nth-child(-n+3) {
  display: block;
}
```

或者，你已經知道 [使用 `:not()` 選擇器來決定表單是否顯示邊框](#使用-not-選擇器來決定表單是否顯示邊框) 這個技巧，你可以試試：

```css
/* 選擇除了前 3 個之外的所有項目，並顯示出來 */
li:not(:nth-child(-n + 3)) {
  display: none;
}
```

就是這麼簡單！

#### [示範](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[回到目錄](#table-of-contents)</sup>

### 使用 SVG 圖示

沒有理由不使用 SVG 圖示：

```css
.logo {
  background: url('logo.svg');
}
```

SVG 在所有解析度下都可以良好縮放，並且支援 IE9 之後的所有瀏覽器，丟棄你的 .png, .jpg, 或 .gif 檔案！

**注意：** 如果你有一個只用 SVG 圖示的按鈕，只給看的見的人來點選。當 SVG 無法載入的時候，以下樣式可以幫助你維持網頁的可及性(Accessibility)：

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[回到目錄](#table-of-contents)</sup>

### 使用 "貓頭鷹" 選擇器

這個名字 "Lobotomized Owl" (貓頭鷹) 大家可能比較陌生，不過如果你將 通用選擇器 (`*`) 和 相鄰兄弟選擇器 (`+`) 一起使用的話，將可帶來極大效益：

```css
* + * {
  margin-top: 1.5em;
}
```

在此範例中，在檔案中所有的元素，只要緊接著其他元素，就會套用一個 `margin-top: 1.5em` 樣式。

更多 "貓頭鷹" (Lobotomized Owl) 選擇器，可參考 *A List Apart* 上面關於 [Heydon Pickering 的文章](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls)

#### [示範](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[回到目錄](#table-of-contents)</sup>

### 使用 `max-height` 來建立純 CSS 的捲動軸

你可以透過 `max-height` 與 `overflow-y: hidden` 來實作出 CSS-only 的捲動軸：

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

當滑鼠移到 `.slider` 的元素時，元素的內容如果過多，最大高度只會擴展到 `max-height` 的值，而且會自動顯示捲動軸。

<sup>[回到目錄](#table-of-contents)</sup>

### 讓表格中每個儲存格維持等寬

表格中要維持每一格都等寬是一件痛苦的事，所以你應該嘗試用 `table-layout: fixed` 來讓所有儲存格維持等寬：

```css
.calendar {
  table-layout: fixed;
}
```

這才是無痛的 Table 版面配置。

#### [示範](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[回到目錄](#table-of-contents)</sup>

### 利用 Flexbox 去除多餘的 Margin 技巧

排版的時候，為了設計出每一欄的間隙 (gutters)，一般都會用到像是 `nth-`、`first-` 和 `last-child` 的技巧，來去除頭尾多餘的間隙，不如使用 Flexbox 的 `space-between` 屬性：

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

現在，每一欄之間的間隙將會平均分佈。

<sup>[回到目錄](#table-of-contents)</sup>

### 利用屬性選擇器填滿空白連結的文字內容

當 `<a>` 元素沒有文字內容，但有 `href` 屬性的時候，可以這樣做：

```css
a[href^='http']:empty::before {
  content: attr(href);
}
```

這真的非常方便。

#### [示範](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[回到目錄](#table-of-contents)</sup>

### 幫沒有類別的連結設定一個預設樣式

幫沒有套用 class 的超連結設定一個預設樣式：

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

使用者透過後台 CMS 系統插入的超連結通常沒有 `class` 屬性，以上樣式可以針對這些超連結進行設定，且不會影響其它樣式定義。

<sup>[回到目錄](#table-of-contents)</sup>

### 等比例的方塊

要建立一個固定比例的方塊 (Box)，你需要的就是將 `padding-top` 或 `padding-bottom` 設定到 div 元素：

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

在 `padding-bottom` 設定 `20％` 意味著各個 div 方塊的高度等同於 20% 的寬度。無論 Viewport 現在的寬度多少，子元素的 div 將維持其寬高比（100％ / 20％ = 5:1）。

#### [示範](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[回到目錄](#table-of-contents)</sup>

### 為破圖定義樣式

只要一點 CSS 就可以美化所有破圖：

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

接著新增一個 偽元素規則 (pseudo-elements rules) 來顯示使用者訊息，以及這張破圖的 URL 參考：

```css
img::before {
  content: "We're sorry, the image below is broken :(";
  display: block;
  margin-bottom: 10px;
}

img::after {
  content: '(url: ' attr(src) ')';
  display: block;
  font-size: 12px;
}
```

想學習更多這類樣式技巧，可以參考 [Ire Aderinokun](https://github.com/ireade/) 的 [原始文章](http://bitsofco.de/styling-broken-images/)。

<sup>[回到目錄](#table-of-contents)</sup>

### 用 `rem` 來調整全域大小；用 `em` 來調整區域大小

在根元素設定基礎字體大小後 (`html { font-size: 100%; }`), 使用 `em` 設定文字元素的字體大小：

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

然後設定模組的字體大小為 `rem`：

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: 0.9rem;
}
```

現在，每個模組變得獨立，更容易、靈活的樣式便於維護。

<sup>[回到目錄](#table-of-contents)</sup>

### 隱藏沒有靜音並設定自動播放的影片

當你在一個可以自訂樣式的後台環境設定網站樣式時，這是一個不錯的小技巧。畢竟自動撥放影片是蠻惱人的，這個技巧可以幫助你避免影片在沒有靜音的情況下自動撥放。

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

你看，我們再次利用了 [`:not()`](#使用-not-選擇器來決定表單是否顯示邊框) 偽類別 (pseudo-class) 的優勢。

<sup>[回到目錄](#table-of-contents)</sup>

### 使用 `:root` 選擇器來設定彈性的字體大小

在響應式版面(responsive layout)中，字體大小通常需要根據不同的 Viewport (畫面大小) 進行調整。你可以根據 `:root` 所定義的 Viewport 高度與寬度來調整字體大小：

```css
:root {
  font-size: calc(1vw + 1vh + 0.5vmin);
}
```

現在你便能使用依 `:root` 字級為基準的 `rem` 單位了。

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [示範](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[回到目錄](#table-of-contents)</sup>

### 為了更好的行動體驗來設定表單元素的 `font-size`

為了避免使用者在行動瀏覽器 (iOS Safari, 等等）點擊 `<select>` 的下拉選單時在 HTML 表單元素進行縮放，你可以加上`font-size` 到這些選取器樣式規則：

```css
input[type='text'],
input[type='number'],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[回到目錄](#table-of-contents)</sup>


### 使用指標事件來控制滑鼠事件

[指標事件](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events)允許您指定滑鼠如何與其觸控的元素進行互動。 要停用按鈕上的預設指標事件，例如：

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

就這麼簡單。

<sup>[回目錄](#目錄)</sup>


### 在用作間距的換行符上設置`display: none`

正如[Harry Roberts指出](https://twitter.com/csswizardry/status/1170835532584235008)，這有助於防止CMS用戶使用額外的換行符

```css
br + br {
  display: none;
}
```

<sup>[回目錄](#目錄)</sup>


## 瀏覽器支援度

以上技巧支援 Chrome, Firefox, Safari, 最新版本與 Edge 瀏覽器。
