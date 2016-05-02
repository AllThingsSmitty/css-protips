<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" alt="light bulb icon">
</p>

# CSS профессиональные советы [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Коллекция советов, которые помогут принять ваш CSS навыки профи.

> Для других больших списков проверить [@sindresorhus](https://github.com/sindresorhus/~~HEAD=dobj) в Куратор список [удивительных списков](https://github.com/sindresorhus/awesome/).


## Содержание

* [профессиональные советы](#protips)
* [Поддержка](#поддержка)
* [Вклад Руководство](../../CONTRIBUTING.md)


<div id="protips"></div>
## профессиональные советы

1. [Использование `:not()` Применить / Границы на Исключить навигации](#use-not-to-applyunapply-borders-on-navigation)
1. [Добавить `line-height` в `body`](#add-line-height-to-body)
1. [Вертикально-центр Все](#vertically-center-anything)
1. [списки разделенных запятыми](#comma-separated-lists)
1. [Выбор предметов с использованием отрицательных `пth-child`](#select-items-using-negative-nth-child)
1. [Использование SVG для значков](#use-svg-for-icons)
1. [Используйте "лоботомию Сова" Выбор](#use-the-lobotomized-owl-selector)
1. [Используйте `max-height` для чистого CSS Слидерс](#use-max-height-for-pure-css-sliders)
1. [Наследование `box sizing`](#inherit-box-sizing)
1. [одинаковой ширины ячейки таблицы](#equal-width-table-cells)
1. [Избавиться от маржинальных Hacks С Flexbox](#get-rid-of-margin-hacks-with-flexbox)
1. [Использование селекторов атрибутов с пустой ссылки](#use-attribute-selectors-with-empty-links)
1. [Стиль "по умолчанию" ссылки](#style-default-links)
1. [Последовательная Вертикальный ритм](#consistent-vertical-rhythm)
1. [Внутренние коробки Соотношение](#intrinsic-ratio-boxes)
1. [Стиль изображения разорванные](#style-broken-images)
1. [Используйте `rem` для глобального Калибровке; Используйте `em` для локального Калибровке](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [Скрыть автозапуск видео, которые не Приглушенный](#hide-autoplay-videos-that-arent-muted)
1. [Использование `:root` для гибкого типа](#use-root-for-flexible-type)


<div id="use-not-to-applyunapply-borders-on-navigation"></div>
### Использование `:not()` Применить / Границы на Исключить навигации

Вместо того, чтобы на границе...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

...А затем снимая его последний элемент...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

...Используйте `:not()` псевдо-класс, чтобы применить только к элементам, которые вы хотите:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Конечно, вы можете использовать `.nav li + li` или даже` .nav li:first-child ~ li`, но с `:not()` намерение очень ясно и селектор CSS определяет границу путь человека бы описать его.


<div id="add-line-height-to-body"></div>
### Добавить `line-height` в` body`

Вам не нужно, чтобы добавить `line-height` к каждому `<р>`, `<h*>`, _et Al_. в отдельности. Вместо этого добавьте его в `body`:

```css
body {
  line-height: 1;
}
```

Таким образом, текстовые элементы могут наследовать от `body` легко.


<div id="vertically-center-anything"></div>
### Вертикально-центр Все

Нет, это не черная магия, вы действительно можете сосредоточить элементы по вертикали:

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

Хотите, чтобы центр что-то еще? Вертикально, горизонтально...что-нибудь, в любое время и в любом месте? CSS-трюками [хороший рецензия](https://css-tricks.com/centering-css-complete-guide/) делать все это.

**Примечание:** Часы для некоторого [багги behavior](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) с flexbox в IE11.


<div id="comma-separated-lists"></div>
### списки разделенных запятыми

Сделать элементы списка выглядят как настоящий, разделенный запятыми список:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Используйте `:not()` псевдо-класса не так запятой добавляется к последнему пункту.

**Примечание:** Этот наконечник не может быть идеальным для доступности, в частности, экран читателей. И копировать / вставить из браузера не работает с CSS-контента. Действовать с осторожностью.


<div id="select-items-using-negative-nth-child"></div>
### Выбор элементов с использованием отрицательных `пth-child`

Используйте отрицательное `п-child` в CSS для выбора элементов с 1 по п.

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```

Или, так как вы уже узнали немного о [с помощью `:not()`](#use-not-to-applyunapply-borders-on-navigation), попробуйте:

```css
/* select items 1 through 3 and display them */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Хорошо, что было довольно легко.


<div id="use-svg-for-icons"></div>
### Использование SVG для значков

Там нет причин не использовать SVG для значков:

```css
.logo {
  background: url("logo.svg");
}
```

SVG хорошо масштабируется для всех типов разрешения и поддерживается во всех браузерах [вернуться к IE9](http://caniuse.com/#search=svg). Так угробить ваш .png, .jpg или .gif-Jif-whatev файлы.

**Примечание:** Если у вас есть SVG пиктограммами только кнопки для зрячих пользователей и SVG не удается загрузить, это поможет сохранить доступность:

```css
.no-svg .icon-only:after {
  content: attr(aria-label);
}
```


<div id="use-the-lobotomized-owl-selector"></div>
### Используйте "лоботомию Сова" Selector

Это может иметь странное название, но используя универсальный селектор (`*`) с соседним селекторном одноранговых (`+`) может обеспечить мощные возможности CSS:

``css
* + * {
  margin-top: 1.5em;
}
```

В этом примере все элементы в потоке документа, которые следуют другие элементы получат `margin-top: 1.5em`.

Более подробную информацию о селекторе "лоботомию сова", прочитать [сообщение Heydon Пикеринга](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) на *A List Apart*.


<div id="use-max-height-for-pure-css-sliders"></div>
### Используйте `max-height` для чистого CSS Слидерс

Реализация CSS только ползунки с помощью `max-height` с переливом скрытых:

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

Элемент расширяется до значение `max-height` на парении и ползунок отображает в результате переполнения.


<div id="inherit-box-sizing"></div>
### Наследование `box-sizing`

Пусть `box-sizing` быть унаследованы от` html`:

```css
html {
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}

```

Это делает его легче изменить `box-sizing` в плагинов или других компонентов, которые используют другое поведение.


<div id="equal-width-table-cells"></div>
### Равные Ширина ячейки таблицы

Таблицы могут быть боль, чтобы работать с таким попробуйте использовать `table-layout: fixed` держать клетки при одинаковой ширины:

```css
.calendar {
  table-layout: fixed;
}
```

Безболезненное макеты таблиц.


<div id="get-rid-of-margin-hacks-with-flexbox"></div>
### Избавиться от маржинальных Hacks С Flexbox

При работе с желобами колонок вы можете избавиться от `пth,` `first-` и `last-child` взломы с помощью `space-between` свойство flexbox в:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Теперь столбец желобов всегда появляются равномерно разнесены.


<div id="use-attribute-selectors-with-empty-links"></div>
### Использование селекторов атрибутов с пустыми Ссылки

Отображать ссылки, когда `<a>` элемент не имеет текстового значения, но `href` атрибут есть ссылка:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Это очень удобно.


<div id="style-default-links"></div>
### Стиль "по умолчанию" Ссылки

Добавьте стиль "по умолчанию" ссылки:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Теперь ссылки, вставленные через CMS, которая, как правило, не имеют `class` атрибут, будет иметь различие без обобщенно влияния на каскад.


<div id="consistent-vertical-rhythm"></div>
### Последовательная Вертикальный ритм

Используйте универсальный селектор (`*`) внутри элемента, чтобы создать последовательную вертикальный ритм:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

В соответствии вертикальный ритм обеспечивает визуальную эстетику, которая делает гораздо более удобным для чтения контента.


<div id="intrinsic-ratio-boxes"></div>
### Внутренние коробки Соотношение

Для того, чтобы создать блок с собственным отношением, все, что вам нужно сделать, это применить верхний или нижний отступ к DIV:

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

Использование 20% для заполнения делает высоту параллелепипеда равной 20% от его ширины. Независимо от того, ширина окна просмотра, ребенок DIV будет держать его соотношение сторон (100% / 20% = 5: 1).


<div id="style-broken-images"></div>
### Стиль разорванные Изображения

Сделайте сломанные изображения более эстетически приятны с немного CSS:

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

Теперь добавьте правила псевдо-элементы для отображения сообщения пользователя и URL-ссылки разбитого изображения:

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

Подробнее о моделировании для этой модели в [Ire Aderinokun](https://github.com/ireade/) в [исходное сообщение](http://bitsofco.de/styling-broken-images/).


<div id="use-rem-for-global-sizing-use-em-for-local-sizing"></div>
### Используйте `rem` для Global Калибровке; Используйте `em` для локального Калибровке

После установки базового размера шрифта в корневом каталоге (`html { font-size: 16px; }`), установите размер шрифта для текстовых элементов для `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Затем установите размер шрифта для модулей до `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Теперь каждый модуль становится разобщенным и проще в стиле, более легким в обслуживании и гибкость.


<div id="hide-autoplay-videos-that-arent-muted"></div>
### Скрыть автозапуск видео, которые не Приглушенный

Это отличный трюк для пользовательского пользователя таблицы стилей. Избегайте перегрузки пользователя со звуком из видео, которое воспроизводится автоматически при загрузке страницы. Если звук не приглушен, не показывают видео:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Еще раз, мы пользуясь помощью [`:not()`](#use-not-to-applyunapply-borders-on-navigation) псевдо-класс.


<div id="use-root-for-flexible-type"></div>
### Использование `: root` для гибкого типа

Размер тип шрифта в реагирующей макет должен иметь возможность регулировать с каждого видового экрана. Вы можете рассчитать размер шрифта, основанный на высоте видового экрана и ширины с помощью `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Теперь вы можете использовать `root em` блок на основе значения, рассчитанного с помощью `:root`:

```css
body {
  font: 1em/1.6rem sans-serif;
}
```




## Поддержка

Текущие версии Chrome, Firefox, Safari, Opera, Edge, и IE11.