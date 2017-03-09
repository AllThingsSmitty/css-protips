<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" alt="light bulb icon">
</p>

# Советы профессионалов CSS [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Коллекция советов, которые помогут вам стать лучше в CSS.

> Вы найдете больше [классных списков](https://github.com/sindresorhus/awesome/) под кураторством [@sindresorhus](https://github.com/sindresorhus/).


<div id="table-of-contents"></div>
## Содержание

* [Профессиональные советы](#protips)
* [Поддержка](#Поддержка)
* [Помощь проекту](../../CONTRIBUTING.md)


<div id="protips"></div>
## Профессиональные советы

1. [Используйте CSS Reset](#use-a-css-reset)
1. [Наследуйте `box-sizing`](#inherit-box-sizing)
1. [Используйте `:not()` для добавления / удаления границ в меню навигации](#use-not-to-applyunapply-borders-on-navigation)
1. [Добавьте `line-height` в `body`](#add-line-height-to-body)
1. [Выровнять все по вертикали](#vertically-center-anything)
1. [Списки, разделенные запятыми](#comma-separated-lists)
1. [Выбирайте элементы с использованием отрицательных значений в `nth-child`](#select-items-using-negative-nth-child)
1. [Используйте SVG для значков](#use-svg-for-icons)
1. [Используйте селектор "Лоботомированная сова"](#use-the-lobotomized-owl-selector)
1. [Используйте `max-height` для ползунков на чистом CSS](#use-max-height-for-pure-css-sliders)
1. [Ячейки таблицы равной ширины](#equal-width-table-cells)
1. [Используйте Flexbox вместо margin](#get-rid-of-margin-hacks-with-flexbox)
1. [Используйте селектор атрибутов для пустых ссылок](#use-attribute-selectors-with-empty-links)
1. [Стиль "по умолчанию" для ссылок](#style-default-links)
1. [Постоянный вертикальный ритм](#consistent-vertical-rhythm)
1. [Блок с собственным отношением сторон](#intrinsic-ratio-boxes)
1. [Задайте стили для поломанныx изображений](#style-broken-images)
1. [Используйте `rem` для глобальных размеров; Используйте `em` для локальных размеров](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [Отключите автовоспроизведение видео с включенным звуком](#hide-autoplay-videos-that-arent-muted)
1. [Используйте `:root` для шрифтов](#use-root-for-flexible-type)
1. [Установите `font-size` для элементов формы, чтобы оптимизировать просмотр на мобильных устройствах](#set-font-size-on-form-elements-for-a-better-mobile-experience)


<div id="use-a-css-reset"></div>
### Используйте CSS Reset

Сброс CSS помогает обеспечить согласованность стилей между различными браузерами и с чистого листа начать оформление элементов. Вы можете использовать CSS библиотеки сброса такие как [Normalize](http://necolas.github.io/normalize.css/) и др., или вы можете использовать более простой способ сброса:

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Теперь для всех элементов свойства margin и padding будут равны нулю, а `box-sizing: border-box` позволяет указывать размеры всему блоку, а не его содержимому.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Примечание:** Если вы будете следовать совету [Наследуйте box-sizing](#inherit-box-sizing), то вы можете не включать свойство `box-sizing` в ваш CSS Reset.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="inherit-box-sizing"></div>
### Наследуйте `box-sizing`

Пусть `box-sizing` будет унаследован от `html`:

```css
html {
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}
```

Так значительно проще изменять `box-sizing` в плагинах или других компонентах, которые задают иное поведение.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="use-not-to-applyunapply-borders-on-navigation"></div>
### Используйте `:not()` для добавления / удаления границ в меню навигации

Вместо того, чтобы добавлять границу...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

...а затем убирать её с последнего элемента...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

...используйте псевдокласс `:not()`, чтобы добавить только к нужным элементам:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Конечно, вы можете использовать `.nav li + li` или даже `.nav li:first-child ~ li`, но с `:not()` намерение понятнее, а селектор CSS определяет границу на человеческом языке.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="add-line-height-to-body"></div>
### Добавьте `line-height` в `body`

Вам вовсе не требуется добавлять свойство `line-height` к каждому `<р>`, `<h*>`, _и т.д._. по отдельности. Вместо этого добавьте его в `body`:

```css
body {
  line-height: 1.5;
}
```

Таким образом текстовые элементы легко могут наследовать свойство от `body`.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="vertically-center-anything"></div>
### Выровнять все по вертикали

Нет, это не черная магия, вы действительно можете расположить элементы по центру по вертикали:

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

Хотите разместить по центру что-то еще? Вертикально, горизонтально...что угодно, в любое время и в любом месте? У нас есть [хорошая статья](https://css-tricks.com/centering-css-complete-guide/) которая научит всему этому.

**Примечание:** Будьте осторожны с некоторыми [багами](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) flexbox в IE11.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="comma-separated-lists"></div>
### Списки, разделенные запятыми

Сделайте список похожим на настоящий, разделенный запятыми список:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Используйте псевдокласс `:not()` чтобы не добавлять запятую к последнему пункту.

**Примечание:** Этот совет не всегда даёт лучший результат, например, могут возникнуть проблемы у экранного диктора. Да и копирование / вставка из браузера не всегда работают со сгенерированным CSS контентом. Следует быть осторожным.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="select-items-using-negative-nth-child"></div>
### Выбирайте элементы с использованием отрицательных значений в `nth-child`

Используйте отрицательные значения в `nth-child` в CSS для выбора элементов с 1 по n.

```css
li {
  display: none;
}

/* выбирает и отображает элементы с 1 по 3 */
li:nth-child(-n+3) {
  display: block;
}
```

Или, так как вы уже немного познакомились [с `:not()`](#use-not-to-applyunapply-borders-on-navigation), попробуйте:

```css
/* выбирает и отображает элементы с 1 по 3 */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Что же, это было довольно легко.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="use-svg-for-icons"></div>
### Используйте SVG для значков

Нет ни одной причины, чтобы не использовать SVG для значков:

```css
.logo {
  background: url("logo.svg");
}
```

SVG хорошо масштабируется для всех разрешений и поддерживается во всех браузерах [включая IE9 и выше](http://caniuse.com/#search=svg). Так выбросите же ваши .png, .jpg или .gif-jif-что-угодно файлы.

**Примечание:** Если у вас есть кнопки, содержащие только SVG пиктограммы, и SVG не удается загрузить, то это поможет сохранить доступность кнопки:

```css
.no-svg .icon-only:after {
  content: attr(aria-label);
}
```

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="use-the-lobotomized-owl-selector"></div>
### Используйте селектор "Лоботомированная сова"

Название, безусловно, странное, но используя универсальный селектор (`*`) с соседним селектором (`+`), мы получаем мощное правило CSS:

```css
* + * {
  margin-top: 1.5em;
}
```

В этом примере все элементы в потоке документа, которые следуют другие элементы получат `margin-top: 1.5em`.

Более подробную информацию о селекторе "Лоботомированная сова", можно найти в [статье Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) на *A List Apart*.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="use-max-height-for-pure-css-sliders"></div>
### Используйте `max-height` для ползунков на чистом CSS

Реализация ползунков на чистом CSS с помощью `max-height` и `overflow hidden`:

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

При наведении элемент расширяется до значения `max-height`, а всё что не влезло, можно прокрутить.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="equal-width-table-cells"></div>
### Ячейки таблицы равной ширины

Иногда работа с таблицами приносит боль, в таких случаях попробуйте задать `table-layout: fixed` чтобы ячейки были одинаковой ширины:

```css
.calendar {
  table-layout: fixed;
}
```

Даешь макеты таблиц без боли!

#### [Демо](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="get-rid-of-margin-hacks-with-flexbox"></div>
### Используйте Flexbox вместо margin

При работе с пробелами между колонок вы можете избавиться от псевдоклассов `nth,` `first-` и `last-child` воспользовавшись свойством flexbox `space-between`:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Теперь пробелы между колонками будут одного размера.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="use-attribute-selectors-with-empty-links"></div>
### Используйте селектор атрибутов для пустых ссылок

Отображайте ссылки, когда элемент `<a>` пустой, но есть ссылка в атрибуте `href`:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Это очень удобно.

#### [Демо](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="style-default-links"></div>
### Стиль "по умолчанию" для ссылок

Добавьте для ссылок стиль "по умолчанию":

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Теперь ссылки, вставленные через CMS, которые, как правило, не имеют атрибута `class`, будут иметь отличительный признак без влияния на каскад.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="consistent-vertical-rhythm"></div>
### Постоянный вертикальный ритм

Используйте универсальный селектор (`*`) внутри элемента, чтобы создать постоянный вертикальный ритм:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

Постоянный вертикальный ритм добавляет визуальную эстетику, благодаря которой читать текст гораздо проще.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="intrinsic-ratio-boxes"></div>
### Блок с собственным отношением сторон

Чтобы создать блок с собственным отношением сторон, все, что вам нужно сделать, это добавить верхний или нижний padding к DIV:

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

Использование padding 20% делает высоту параллелепипеда равной 20% от его ширины. Независимо от ширины окна, дочерний DIV будет сохранять соотношение сторон (100% / 20% = 5:1).

#### [Демо](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="style-broken-images"></div>
### Задайте стили для поломанныx изображений

Сделайте поломанные изображения эстетически приятнее с CSS:

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

Теперь добавьте правила псевдо-элементов для отображения сообщения пользователю и URL-ссылки поломаного изображения:

```css
img:before {
  content: "Упс, изображение ниже поломалось :(";
  display: block;
  margin-bottom: 10px;
}

img:after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

Подробнее об этой модели в [исходной статье](http://bitsofco.de/styling-broken-images/) [Ire Aderinokun](https://github.com/ireade/).

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="use-rem-for-global-sizing-use-em-for-local-sizing"></div>
### Используйте `rem` для глобальных размеров; Используйте `em` для локальных размеров

После установки базового размера шрифта всего проекта (`html { font-size: 100%; }`), установите размер шрифта для текстовых элементов через `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Затем установите размер шрифта для модулей через `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Теперь каждый модуль становится разобщенным и проще в настройке, более легким в обслуживании и гибче.

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="hide-autoplay-videos-that-arent-muted"></div>
### Отключите автовоспроизведение видео с включенным звуком

Это отличный трюк для пользовательских стилей. Избегайте раздражения пользователя звуком из видео, которое воспроизводится автоматически при загрузке страницы. Если звук не приглушен, то не показывайте видео:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

И снова мы воспользовались помощью псевдокласса [`:not()`](#use-not-to-applyunapply-borders-on-navigation).

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="use-root-for-flexible-type"></div>
### Используйте `:root` для шрифтов

Размер шрифта должен подстраиваться под каждый возможный размер экрана. Вы можете рассчитывать размер шрифта, основываясь на высоте и ширине экрана с помощью `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Теперь вы можете использовать единицу `root em` на основе значения, рассчитанного с помощью `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Демо](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


<div id="set-font-size-on-form-elements-for-a-better-mobile-experience"></div>
### Установите `font-size` для элементов формы, чтобы оптимизировать просмотр на мобильных устройствах

Чтобы избежать масштабирования мобильными браузерами (iOS Safari, _и др_.) элементов HTML формы, когда раскрывающийся список `<select>` нажат, добавьте  `font-size` правило селектору:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[вернуться к оглавлению](#table-of-contents)</sup>


## Поддержка

Текущие версии Chrome, Firefox, Safari, Opera, Edge, и IE11.
