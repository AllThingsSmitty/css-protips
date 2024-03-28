<p align="center">
  <img src="../../assets/img/bulb.svg" width="200" alt="light bulb icon">
</p>

# CSS 프로팁 [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

CSS스킬을 프로처럼 만들어주는 팁 모음

> 또 다른  꼭 확인해 볼 만한 [@sindresorhus](https://github.com/sindresorhus/)의 큐레이트 리스트  [awesome lists](https://github.com/sindresorhus/awesome/).

<div id="table-of-contents"></div>

## 목차

* [프로팁](#프로팁)
* [지원](#지원)
* [컨트리뷰션 가이드라인](../../CONTRIBUTING.md)


<div id="protips"></div>

## 프로팁

1. [CSS Reset을 사용](#use-a-css-reset)
1. [`box-sizing`을 컴포넌트마다 변경](#inherit-box-sizing)
1. [모든 프로퍼티를 리셋하는 대신에 `unset`를 쓴다](#use-unset-instead-of-resetting-all-properties)
1. [`:not()` 를 사용하여 보더를 삭제](#use-not-to-applyunapply-borders-on-navigation)
1. [글꼴이 로컬로 설치되어 있는지 확인](#check-if-font-is-installed-locally)
1. [`body`에 `line-height` 넣기](#add-line-height-to-body)
1. [폼 요소에`: focus`를 설정하기](#set-focus-for-form-elements)
1. [전부 수직 정렬 만들기](#vertically-center-anything)
1. [리스트를 콤마로 나누기](#comma-separated-lists)
1. [Negative `nth-child`를 사용하여 아이템 나누기](#select-items-using-negative-nth-child)
1. [SVG를 아이콘으로 사용하기](#use-svg-for-icons)
1. ["Lobotomized Owl" Selector 사용하기](#use-the-lobotomized-owl-selector)
1. [CSS로 구현된 슬라이더에 `max-height` 사용하기](#use-max-height-for-pure-css-sliders)
1. [테이블 셀의 너비 균등하게 하기](#equal-width-table-cells)
1. [Flexbox의 Margin Hack 제거](#get-rid-of-margin-hacks-with-flexbox)
1. [링크에 텍스트가 없을 때의 url 표시](#use-attribute-selectors-with-empty-links)
1. ["Default" 링크 스타일](#style-default-links)
1. [내재 비율의 박스](#intrinsic-ratio-boxes)
1. [깨진 링크의 이미지 스타일](#style-broken-images)
1. [글로벌 사이즈 지정에 `rem`; 로컬  사이즈 지정에 `em`](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [동영상 자동재생 감추기](#hide-autoplay-videos-that-arent-muted)
1. [Flexible Type의 `:root` 사용하기](#use-root-for-flexible-type)
1. [모바일 환경을 위한 `font-size` 요소 설정](#set-font-size-on-form-elements-for-a-better-mobile-experience)
1. [포인터 이벤트를 사용한 마우스 이벤트 제어](#use-pointer-events-to-control-mouse-events)
1. [간격으로 사용되는 줄 바꿈에서 `display: none` 을 설정하십시오.](#set-display-none-on-line-breaks-being-used-as-spacing)


<div id="use-a-css-reset"></div>

### CSS Reset을 사용

CSS reset은 스타일 요소들을 통해 백지 상태에서 다른 브라우저간의 스타일의 일관성을 강화하는데 도움을 줍니다. 또한 [Normalize](http://necolas.github.io/normalize.css/), _et al._, 와 같은 CSS 리셋 라이브러리를 통해 더 쉽게 reset 형태를 취할 수 있습니다.

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```


이제 요소는 마진과 패딩을 배제하고, `box-sizing`은 CSS 박스 모델을 통해 관리됩니다.

#### [데모](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Note:** 당신이 아래의 [`box-sizing`을 컴포넌트마다 변경](#inherit-box-sizing) 팁을 따를 경우 `box-sizing` 프로퍼티를 선택하지 않을 수 있습니다.

<sup>[목차로 돌아가기](#table-of-contents)</sup>



<div id="inherit-box-sizing"></div>

### `box-sizing`을 컴포넌트마다 변경

`html`에서 `box-sizing`을 계승하게 합니다:

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

이것은 다른 플러그인과 컴포넌트에서 `box-sizing`을 변경하는 것을 용이하게 합니다. 

#### [데모](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="use-unset-instead-of-resetting-all-properties"></div>

### 모든 프로퍼티를 리셋하는 대신에 `unset`를 쓴다

요소들을 리셋할 경우, 각각의 속성을 리셋할 필요가 없습니다.

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

요소의 속성 `all` 생략형을 통해 지정하고 `unset`을 통해 모든 요소를 초기값으로 설정할 수 있습니다.

```css
button {
  all: unset;
}
```

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="use-not-to-applyunapply-borders-on-navigation"></div>

### `:not()` 를 사용하여 보더를 삭제

Border를 넣거나...

```css
/* 보더 추가 */
.nav li {
  border-right: 1px solid #666;
}
```

...마지막 요소를 없애기 보다는...

```css
/* 보더 삭제 */
.nav li:last-child {
  border-right: none;
}
```

...`:not()`을 사용하여 코드를 간단히 지정할 수 있습니다.

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

CSS 선택자는 사람이 설명하는 방식 그대로 경계를 정의합니다.

#### [데모](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="check-if-font-is-installed-locally"></div>

### 글꼴이 로컬로 설치되어 있는지 확인

글꼴을 원격으로 가져 오기 전에 글꼴이 로컬에 설치되어 있는지 확인할 수 있으며 이는 좋은 성능 팁입니다.

```css
@font-face {
  font-family: "Dank Mono";
  src:
    /* 풀네임 */
    local("Dank Mono"),
    /* 포스트 스크립트명 */
    local("Dank-Mono"),
    /* 아니면 다운로드도 가능! */
    url("//...a.server/fonts/DankMono.woff");
}

code {
  font-family: "Dank Mono", system-ui-monospace;
}
```

이 팁과 [데모](https://codepen.io/argyleink/pen/VwYJpgR)를 공유 한 Adam Argyle의 모자 팁.

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="add-line-height-to-body"></div>

### `body`에 `line-height` 넣기

`body`요소에서`line-height`를 지정할 때 `p`,`h*`, _et al_ 등에 그 값이 계승되기 때문에 각각`line-height`을 지정할 필요가 없습니다.

```css
body {
  line-height: 1.5;
}
```

이 방법으로 텍스트 요소가 `body`의 속성을 쉽게 계승할 수 있습니다.

#### [데모](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="set-focus-for-form-elements"></div>

### 폼 요소에`: focus`를 설정하기

키보드 사용자는 포커스를 사용하여 키보드 이벤트의 위치를 결정합니다. 폼 요소에 집중할 수 있게 해주며, 브라우저의 기본 구현을 일관성있게 만듭니다.

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

#### [데모](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="vertically-center-anything"></div>

### 전부 Vertically-Center로 만들기

농담이 아니라, 진짜 전부 중앙으로 배치가 가능합니다.

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

무언가를 중앙으로 배치하고 싶으신가요? 가로로, 세로로 ...뭐든지, 어떤 때라도, 어디서든? CSS-Tricks의 [가이드](https://css-tricks.com/centering-css-complete-guide/)를 통해 그 모든 것을 해보세요!

#### [데모](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="comma-separated-lists"></div>

### 리스트를 콤마로 나누기

Make list items look like a real, comma-separated list:
리스트 아이템을 콤마를 통해 나눕니다.

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

`:not()` 을 사용할 때 리스트의 마지막 아이템에는 콤마를 사용하지 않도록 합니다.

**Note:** 이 팁의 경우 접근성이 떨어질 수 있습니다. 특히, 스크린 사용자에게는요. 또한 브라우저에서의 복사/붙여넣기는 CSS를 통해 생성한 콘텐츠에서는 사용 불가능하므로 주의해 주세요.

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="select-items-using-negative-nth-child"></div>
### Negative `nth-child`를 사용하여 아이템 나누기

Negative `nth-child`를 사용하여 n분의 1로 아이템을 나눌 수 있습니다.

```css
li {
  display: none;
}

/* 1에서 3까지의 선택하고 보여주기 */
li:nth-child(-n+3) {
  display: block;
}
```

[`:not()`](#use-not-to-applyunapply-borders-on-navigation), 를 사용해 봅시다.

```css
/* 처음 3개를 제외한 모든 아이템 보여주기 */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

#### [데모](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[목차로 돌아가기](#table-of-contents)</sup>



<div id="use-svg-for-icons"></div>

### SVG를 아이콘으로 사용하기

SVG를 아이콘으로 사용할 이유는 없지만:

```css
.logo {
  background: url("logo.svg");
}
```

SVG는 [IE9](http://caniuse.com/#search=svg) 이후부터 지원되고 있습니다.

**Note:** 버튼이 SVG로 만들어진 경우, 접근성을 높이기 위해 이 방법을 사용해 보세요.

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[목차로 돌아가기](#table-of-contents)</sup>


### "Lobotomized Owl" Selector 사용하기

이상한 이름이지만  (`*`)와  (`+`)와 함께 사용하면 강력한 CSS의 가능성을 제공합니다.

```css
* + * {
  margin-top: 1.5em;
}
```

이 예시에서는, 모든 요소가 `margin-top: 1.5em`를 따릅니다.

"lobotomized owl" selector에 대해 더 알고싶으시다면 *A List Apart* [Heydon Pickering's post](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls)의 이 문서를 읽어보세요.

#### [데모](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="use-max-height-for-pure-css-sliders"></div>

### CSS로 구현된 슬라이더에 `max-height` 사용하기

CSS에서 구현된 슬라이더는`max-height`을`overflow:hidden;`와 함께 사용하세요.

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

The element expands to the `max-height` value on hover and the slider displays as a result of the overflow
hover시 `max-height`를 요소를 확장 오버플로우의 결과로 슬라이더에 표시됩니다.

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="equal-width-table-cells"></div>

### 테이블 셀의 너비 균등하게 하기

테이블의 각 셀의 너비를 균등하려면`table-layout:fixed;`를 사용해 간단히 할 수 있습니다.

```css
.calendar {
  table-layout: fixed;
}
```

고통 없는 테이블 디스플레이를 가능하게 합니다

#### [데모](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="get-rid-of-margin-hacks-with-flexbox"></div>

### Flexbox의 Margin Hack 제거

column gutter을 사용할 때 flexbox의 `space-between` 요소를 사용하여 `nth-`, `first-`, `last-child`를 사용하지 않게 해줍니다.

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

column gutter는 이제 이벤트 공간에 표시됩니다.

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="use-attribute-selectors-with-empty-links"></div>

### 링크에 텍스트가 없을 때의 url 표시

링크의`href`속성에 링크의 텍스트 값이 없을 경우, 아래의 CSS를 사용하면 링크처의 URL을 표시합니다.

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

상당이 편리한 기능입니다.

#### [데모](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="style-default-links"></div>

### "Default" 링크 스타일

"default" 링크에 스타일 추가하기:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

이것은 보통 class속성이 없는 링크에`:not`을 사용하여 CMS로 삽입됩니다. 상속(cascade)문제 없이 차별화 할 수 있습니다.

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="intrinsic-ratio-boxes"></div>

### 내재 비율의 박스

당신이 top, bottom 패딩을 지정하는 것 만으로 내제된 비율의 박스를 생성합니다.

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

20%를 패딩으로 사용하면 높이를 너비의 20%와 동일하게 합니다.뷰 포트의 너비와 상관 없이, 자식의 div는 이 비율 (100% / 20% = 5:1)를 유지합니다.

#### [데모](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="style-broken-images"></div>

### 깨진 링크의 이미지 스타일

CSS를 통해 링크가 깨진 이미지를 사용자 친화적으로 만듭니다.

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

또는 다음 방법을 통해 사용자에게 깨진 링크에 대한 메세지를 전달하는 것도 가능합니다.

```css
img::before {
  content: "죄송하지만 이 이미지에 문제가 있습니다 :(";
  display: block;
  margin-bottom: 10px;
}

img::after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

이 스탕일링 패턴을 다음 링크에서 배울 수 있습니다.[Ire Aderinokun](https://github.com/ireade/)'s [original post](http://bitsofco.de/styling-broken-images/).

<sup>[목차로 돌아가기](#table-of-contents)</sup>



<div id="use-rem-for-global-sizing-use-em-for-local-sizing"></div>

### 글로벌 사이즈 지정에 `rem`; 로컬  사이즈 지정에 `em`

베이스 폰트 크기를 (`html { font-size: 100%; }`)를 통해 지정하고, 텍스트 요소를 `em`에서 지정합니다.

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

`rem`을 통해 모듈의 폰트 사이즈를 지정해 봅시다:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

이제 각 모듈별로 관리하면 관리가 쉽고 스탕일링이 간편해 집니다.

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="hide-autoplay-videos-that-arent-muted"></div>

### 동영상 자동재생 감추기

이것은 스타일 시트의 커스텀에서 유용한 트릭입니다. 유저가 페이지가 로드될 때 소리가 자동 재생될 때 겪는 부담을 줄여줍니다. 만약 소리를 끌 수 없다면, 차라리 동영상을 보여주지 마세요.

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

다시한 한 번[`:not()`](#use-not-to-applyunapply-borders-on-navigation)을 사용하는 것의 편리함을 보여줍니다.

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="use-root-for-flexible-type"></div>

### Flexible Type의 `:root` 사용하기

`:root`를 사용하여 반응형 레이아웃의 타입 폰트 사이즈를 뷰 포트마다 적용할 수 있게 합니다. 뷰 포트의 높이와 너비를 바탕으로 폰트 크기를 정의할 수 있습니다.

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

`:root`를 정의된 값을 바탕으로 `root em`을 사용할 수 있습니다.

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [데모](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id= "set-font-size-on-form-elements-for-a-better-mobile-experiences"></div>

### 모바일 환경을 위한 `font-size` 요소 설정

iOS Safari, _et al_ 과 같은 모바일 브라우저에서 `<select>`드롭다운을 탭 할 때 HTML 폼 요소가 줌 인 되는 것을 피하기 위해 `font-size` 의 선택자 룰을 추가한다.

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="use-pointer-events-to-control-mouse-events"></div>

### 포인터 이벤트를 사용한 마우스 이벤트 제어

[포인터 이벤트](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events)는 터치 시 마우스 동작을 특정할 수 있도록 도와줍니다. 버튼의 디폴트 포인터를 무효화 하려면 다음 방법을 따릅니다. 

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

아주 간단한 방법이죠?

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="set-display-none-on-line-breaks-being-used-as-spacing"></div>

### 간격으로 사용되는 줄 바꿈에서 `display: none` 을 설정하십시오.

[Harry Roberts가 지적한대로](https://twitter.com/csswizardry/status/1170835532584235008) CMS 사용자가 추가 줄 바꿈을 사용하여 간격을 두지 못하게 할 수 있습니다.

```css
br + br {
  display: none;
}
```

<sup>[목차로 돌아가기](#table-of-contents)</sup>


<div id="support"></div>

## 지원

최신 버전의 Chrome, Firefox, Safari, Edge에서 지원됩니다..

<sup>[목차로 돌아가기](#table-of-contents)</sup>


