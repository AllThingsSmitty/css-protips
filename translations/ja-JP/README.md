<p align="center">
  <img src="../../assets/img/bulb.svg" alt="light bulb icon">
</p>

# CSSの便利な小技・テクニックのまとめ [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

CSSのプロのスキルになるようにアドバイスのリストを紹介します。

> 他のリストのため： [Awesome リスト](https://github.com/sindresorhus/awesome/)　の　[@sindresorhus](https://github.com/sindresorhus/)　をチェックSしてください。.


<div id="table-of-contents"></div>

## 目次

* [プロチップス](#protips)
* [サポート](#soutien)
* [参考](#references)
* [コントリビュート](../../CONTRIBUTING.md)


<div id="protips"></div>

##  プロチップス

1. [CSSのリセットを使用します](#use-a-css-reset)
1. [box-sizingをコンポーネントごとに変更](#inherit-box-sizing)
1. [すべてのプロパティをリセットする代わりに `unset`を使う](#use-unset-instead-of-resetting-all-properties)
1. [`:not()` を使用 / ボーダーを削除](#use-not-to-applyunapply-borders-on-navigation)
1. [フォントがローカルにインストールされているかどうかを確認します](#check-if-font-is-installed-locally)
1. [`body`に`line-height`を加える](#add-line-height-to-body)
1. [フォーム要素に `：focus`を設定する](#set-focus-for-form-elements)
1. [天地の中央に配置](#vertically-center-anything)
1. [リストをカンマ区切りにする](#comma-separated-lists)
1. [ネガティブな「:nth-child」を使用してアイテムを選択](#select-items-using-negative-nth-child)
1. [SVGのアイコン](#use-svg-for-icons)
1. [Owlを使用](#use-the-lobotomized-owl-selector)
1. [CSSで実装されたスライダーにはmax-heightを使う](#use-max-height-for-pure-css-sliders)
1. [テーブルのセルの幅を均等にする](#equal-width-table-cells)
1. [Flexboxのマージンハックを取り除く](#get-rid-of-margin-hacks-with-flexbox)
1. [リンクにテキストが無い時はURLを表示](#use-attribute-selectors-with-empty-links)
1. [デフォルトのリンクをスタイル](#style-default-links)
1. [内在比率のボックス](#intrinsic-ratio-boxes)
1. [リンク切れの画像要素をスタイル](#style-broken-images)
1. [グローバルのサイズ指定に「rem」、ローカルに「em」を使用](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [動画の自動再生を隠す](#hide-autoplay-videos-that-arent-muted)
1. [フレクシブルタイプの`:root`を使用](#use-root-for-flexible-type)
1. [スマホ向け、フォーム要素のフォントサイズの設定](#set-font-size-on-form-elements-for-a-better-mobile-experience)
1. [ポインターイベントを使用してマウスイベントを制御する](#use-pointer-events-to-control-mouse-events)
1. [間隔として使用される改行に「display：none」を設定します](#set-display-none-on-line-breaks-being-used-as-spacing)


<div id="use-a-css-reset"></div>

### CSSのリセットを使用します

CSSのリセットはスタイリング要素のための白紙の状態で異なるブラウザ間でスタイルの一貫性を強化するのに役立ちます。あなたは[Normalize](http://necolas.github.io/normalize.css/)、_et al._のようにCSSのリセットライブラリを使用するか、より簡略化リセットアプローチを使用することができます。

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

今の要素は、マージンやパディングを剥奪し、`box-sizing`は、CSSボックスモデルとレイアウトを管理することができますされます。

#### [デモ](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**注意：**あなたがあなたのCSSのリセットで[Inherit `box-sizing`](#inherit-box-sizing) プロパティが含まれていないことを選択する可能性があります下に`box-sizing`ヒントに従っている場合。


<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="inherit-box-sizing"></div>

### `box-sizing`をコンポーネントごとに変更

`box-sizing`はhtml要素で指定し、継承して利用すると、コンポーネントで変える時に簡単です。

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

これでプラグインかその他のコンポーネントに `box-sizing` を変更しやすくなります。

#### [デモ](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="use-unset-instead-of-resetting-all-properties"></div>

### すべてのプロパティをリセットする代わりに `unset`を使う

要素のプロパティをリセットするときは、個々のプロパティをリセットする必要はありません。

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

要素のプロパティのすべてを `all`省略形で指定することができます。 値を `unset`に設定すると、要素のプロパティが初期値に変更されます：

```css
button {
  all: unset;
}
```

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="use-not-to-applyunapply-borders-on-navigation"></div>

### `:not()`を使用して、リスト要素で実装したナビゲーションの最後のアイテムだけに区切り線を削除します。

ボーダーを書いて。。。

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

ラストチャイルドで非表示するより

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

`:not()`を使用するとシンプルなコードで指定できます。

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

CSSセレクターは、境界線を人間が表現する方法で定義します。

#### [デモ](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="check-if-font-is-installed-locally"></div>

### フォントがローカルにインストールされているかどうかを確認します

フォントをリモートでフェッチする前に、フォントがローカルにインストールされているかどうかを確認できます。これもパフォーマンスのヒントになります。

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

このプロチップと[デモ](https://codepen.io/argyleink/pen/VwYJpgR)を共有してくれたAdam Argyleへの帽子のヒント.

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="add-line-height-to-body"></div>

### `body` に`line-height`を加える

`body`要素で`line-height`を指定することで`p`, `h*`などにその値が継承されるため、それぞれに`line-height`を指定する必要がなくなります。

```css
body {
  line-height: 1.5;
}
```

#### [デモ](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="set-focus-for-form-elements"></div>

### フォーム要素に `：focus`を設定する

視認されたキーボードユーザーは、キーボードイベントがページ内のどこに移動するかを決定するためにフォーカスを当てています。 フォーム要素のフォーカスを目立たせ、ブラウザのデフォルトの実装と一貫性を持たせる：

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

#### [デモ](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="vertically-center-anything"></div>

### 天地の中央に配置

なんでも天地の中央に配置できます！！

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

...CSSグリッド:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

なんでも中央に揃いたいですか？ CSS-Tricks の[セントリングガイド](https://css-tricks.com/centering-css-complete-guide/) をチェックしてください。

#### [デモ](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="comma-separated-lists"></div>

### リストをカンマ区切りにする

リストの各アイテムをカンマ区切りにします。

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

`:not()` を使えば最後のエレメントにカンマ追加されないようにします。

**備考:** アクセシビリティによくないので気をつけてをお使いください。

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="select-items-using-negative-nth-child"></div>

### ネガティブな `:nth-child` を使用してアイテムを選択

`nth-child`にはネガティブな値も指定できます。

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```

また [`:not()`](#use-not-to-applyunapply-borders-on-navigation)　を使用してこちらをのコードを書いてみてください：

```css
/* select all items except the first 3 and display them */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

簡単でしょう〜！

#### [デモ](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="use-svg-for-icons"></div>

### SVGのアイコン

アイコンとしてSVGを使えない理由がないです！

```css
.logo {
  background: url("logo.svg");
}
```

SVGは [IE9](http://caniuse.com/#search=svg)以降のすべてのブラウザでサポートされています。

**備考:** ボタンがSVGだけで作られている場合、SVGがローディングされなかったらアクセシビリティのためこちらのコードを書いて見てください:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="use-the-lobotomized-owl-selector"></div>

### Owlを使用

変な名前ですが(`*`) と (`+`) を使用するとパワフルCSSセレクターになります！

```css
* + * {
  margin-top: 1.5em;
}
```

全てのページの要素にある要素が`margin-top: 1.5em`をもらいます。

Owlについて詳しくはこちら：*List Apart* の[ヘイドンピケリングの記事](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls)

#### [デモ](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="use-max-height-for-pure-css-sliders"></div>

### CSSで実装されたスライダーには`max-height`を使う

CSSで実装されたスライダーは、`max-height`を`overflow: hidden;`と一緒に使ってください。

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

ホバーの時`max-height`の要素を拡張オバーフローの結果でスライダーが表示されます。

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="equal-width-table-cells"></div>

### テーブルのセルの幅を均等にする

テーブルの各セルの幅を均等にするには、`table-layout: fixed;`を使うと簡単にできます。

```css
.calendar {
  table-layout: fixed;
}
```

簡単にテーブルレイアウトを作れます。

#### [デモ](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="get-rid-of-margin-hacks-with-flexbox"></div>

### Flexboxのマージンハックを取り除く

`flexbox`でカラムの溝をつくる時、`nth-`, `first-`, `last-child`などのハックで最後の溝を取り除くことができますが、それは`flexbox`の`space-between`プロパティを使うだけで解決します。


```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

columnのスペースが揃えている。

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="use-attribute-selectors-with-empty-links"></div>

### リンクにテキストが無い時はURLを表示

リンクの`href`属性にはURLがあり、リンクのテキストがない場合に、下記のCSSを使用すると、リンク先のURLを表示します。

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

便利ですよー！

#### [デモ](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="style-default-links"></div>

### `:not`を使ってデフォルトのリンクをスタイル

デフォルトのリンクのスタイルを追加：

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

CMSで挿入される通常class属性を持たないリンクに`:not`を使ってスタイルを定義します。

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="intrinsic-ratio-boxes"></div>

### 内在比率のボックス

ボックスを内在比率で作成するには、ボックスの上部か下部に`div`の詰め物を適用します。

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

paddingに20%を使っているのは、そのボックスの高さを幅の20%と等しくします。ビューポートの幅に関わらず、子のdiv要素のアスペクト比は「100%:20%(5:1)」を保持します。

#### [デモ](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="style-broken-images"></div>

### リンク切れの画像要素をスタイル

よりよいユーザエクスペリエンスを提供するために、リンク切れの画像要素にスタイルを定義します。もちろんリンク切れがないのがベストですが、絶対に存在しない訳ではありません。

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

疑似要素を使い、ユーザーの役に立つ情報を加えることもできます。

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

このようなスタイリングに興味があればこちらに参考してください：[イレ　アデリノクン](https://github.com/ireade/)' [リンク切れの画像についての記事](http://bitsofco.de/styling-broken-images/).

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="use-rem-for-global-sizing-use-em-for-local-sizing"></div>

### グローバルのサイズ指定に`rem`、ローカルに`em`を使用

ベースのフォントサイズを`html{font-size: 16px;}`にルート指定し、テキスト要素を`em`で指定します。

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

モジュールのフォントサイズは`rem`で指定します。

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

モジュールごとに分けるとスタイルするのが簡単で、メンテナンス性もアップします。

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="hide-autoplay-videos-that-arent-muted"></div>

### 動画の自動再生を隠す

これはカスタマイズされたユーザースタイルシートのための素晴らしいテクニックです。ページがロードされた時、動画が自動再生されて音がでてしまうユーザーの負担を軽減します。もし無音にできないなら、動画を使わないでください。

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

こちらも [`:not()`](#use-not-to-applyunapply-borders-on-navigation)を使用できます！

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="use-root-for-flexible-type"></div>

### フレクシブルタイプの`:root`を使用

レスポンシブ対応時に、フォントのサイズをビューポートごとに適応することができます。`:root`を使い、ビューポートの高さと幅に基づいてフォントのサイズを定義することができます。

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

#### [デモ](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

`:root`で定義した値に基づいて、それぞれのタグや要素に`em`を使って利用します。

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="set-font-size-on-form-elements-for-a-better-mobile-experience"></div>

### スマホ向け、フォーム要素のフォントサイズの設定

スマホでセレクト要素のドロップダウンをタップした時に、iOS Safariでフォーム要素にズームインするのを回避するために、フォントサイズを加えます。

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="use-pointer-events-to-control-mouse-events"></div>

### ポインターイベントを使用してマウスイベントを制御する

[Pointer events](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events)では、マウスがタッチしている要素とどのように対話するかを指定することができます。 ボタン上のデフォルトポインタイベントを無効にするには、次のようにします。

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

それは簡単です。

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="set-display-none-on-line-breaks-being-used-as-spacing"></div>

### 間隔として使用される改行に `display：none` を設定します

[ハリー・ロバーツが指摘したように](https://twitter.com/csswizardry/status/1170835532584235008)、これはCMSユーザーがスペースのために余分な改行を使用するのを防ぐのに役立ちます：

```css
br + br {
  display: none;
}
```

<sup>[目次へ戻る](#table-of-contents)</sup>


<div id="support"></div>

## サポート

現在のChrome, Firefox, Safari, のバージョンとEdge.
