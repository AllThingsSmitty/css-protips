<div align="center">
  <img src="./assets/img/bulb.svg" width="200" alt="light bulb icon">
</div>

# CSS Protips [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

A collection of tips to help take your CSS skills pro.

> For other great lists check out [@sindresorhus](https://github.com/sindresorhus/)'s curated list of [awesome lists](https://github.com/sindresorhus/awesome/).


## Table of Contents

* [Protips](#protips)
* [Support](#support)
* [Translations](#translations)
* [Contribution Guidelines](CONTRIBUTING.md)


## Protips

1. [Use a CSS Reset](#use-a-css-reset)
1. [Inherit `box-sizing`](#inherit-box-sizing)
1. [Use `unset` Instead of Resetting All Properties](#use-unset-instead-of-resetting-all-properties)
1. [Use `:not()` to Apply/Unapply Borders on Navigation](#use-not-to-applyunapply-borders-on-navigation)
1. [Check if Font Is Installed Locally](#check-if-font-is-installed-locally)
1. [Add `line-height` to `body`](#add-line-height-to-body)
1. [Set `:focus` for Form Elements](#set-focus-for-form-elements)
1. [Vertically-Center Anything](#vertically-center-anything)
1. [Use `aspect-ratio` Instead of Height/Width](#use-aspect-ratio-instead-of-heightwidth)
1. [Comma-Separated Lists](#comma-separated-lists)
1. [Select Items Using Negative `nth-child`](#select-items-using-negative-nth-child)
1. [Use SVG for Icons](#use-svg-for-icons)
1. [Use the "Lobotomized Owl" Selector](#use-the-lobotomized-owl-selector)
1. [Use `max-height` for Pure CSS Sliders](#use-max-height-for-pure-css-sliders)
1. [Equal-Width Table Cells](#equal-width-table-cells)
1. [Get Rid of Margin Hacks With Flexbox](#get-rid-of-margin-hacks-with-flexbox)
1. [Use Attribute Selectors with Empty Links](#use-attribute-selectors-with-empty-links)
1. [Control Specificity Better With `:is()`](#control-specificity-better-with-is)
1. [Style "Default" Links](#style-default-links)
1. [Intrinsic Ratio Boxes](#intrinsic-ratio-boxes)
1. [Style Broken Images](#style-broken-images)
1. [Use `rem` for Global Sizing; Use `em` for Local Sizing](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [Hide Autoplay Videos That Aren't Muted](#hide-autoplay-videos-that-arent-muted)
1. [Use `:root` for Flexible Type](#use-root-for-flexible-type)
1. [Set `font-size` on Form Elements for a Better Mobile Experience](#set-font-size-on-form-elements-for-a-better-mobile-experience)
1. [Use Pointer Events to Control Mouse Events](#use-pointer-events-to-control-mouse-events)
1. [Set `display: none` on Line Breaks Used as Spacing](#set-display-none-on-line-breaks-used-as-spacing)
1. [Use `:empty` to Hide Empty HTML Elements](#use-empty-to-hide-empty-html-elements)


### Use a CSS Reset

CSS resets help enforce style consistency across different browsers with a clean slate for styling elements. There are plenty of reset patterns to find, or you can use a more simplified reset approach:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Now elements will be stripped of margins and padding, and `box-sizing` lets you manage layouts with the CSS box model.

#### [Demo](https://codepen.io/AllThingsSmitty/pen/kkrkLL)

> [!TIP]
> If you follow the [Inherit `box-sizing`](#inherit-box-sizing) tip below you might opt to not include the `box-sizing` property in  your CSS reset.

<sup>[back to table of contents](#table-of-contents)</sup>


### Inherit `box-sizing`

Let `box-sizing` be inherited from `html`:

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

This makes it easier to change `box-sizing` in plugins or other components that leverage other behavior.

#### [Demo](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[back to table of contents](#table-of-contents)</sup>


### Use `unset` Instead of Resetting All Properties

When resetting an element's properties, it's not necessary to reset each individual property:

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

You can specify all of an element's properties using the `all` shorthand. Setting the value to `unset` changes an element's properties to their initial values:

```css
button {
  all: unset;
}
```

<sup>[back to table of contents](#table-of-contents)</sup>


### Use `:not()` to Apply/Unapply Borders on Navigation

Instead of putting on the border...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

...and then taking it off the last element...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

...use the `:not()` pseudo-class to only apply to the elements you want:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Here, the CSS selector is read as a human would describe it.

#### [Demo](https://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[back to table of contents](#table-of-contents)</sup>


### Check if Font Is Installed Locally

You can check if a font is installed locally before fetching it remotely, which is a good performance tip, too.

```css
@font-face {
  font-family: "Dank Mono";
  src:
    /* Full name */
    local("Dank Mono"),
    /* Postscript name */
    local("Dank Mono"),
    /* Otherwise, download it! */
    url("//...a.server/fonts/DankMono.woff");
}

code {
  font-family: "Dank Mono", system-ui-monospace;
}
```

H/T to Adam Argyle for sharing this protip and [demo](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[back to table of contents](#table-of-contents)</sup>


### Add `line-height` to `body`

You don't need to add `line-height` to each `<p>`, `<h*>`, _et al_. separately. Instead, add it to `body`:

```css
body {
  line-height: 1.5;
}
```

This way textual elements can inherit from `body` easily.

#### [Demo](https://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[back to table of contents](#table-of-contents)</sup>


### Set `:focus` for Form Elements

Sighted keyboard users rely on focus to determine where keyboard events go in the page. Make focus for form elements stand out and consistent than a browser's default implementation:

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

<sup>[back to table of contents](#table-of-contents)</sup>


### Vertically-Center Anything

No, it's not black magic, you really can center elements vertically. You can do this with flexbox...

```css
html,
body {
  height: 100%;
}

body {
  align-items: center;
  display: flex;
  justify-content: center;
}
```

...and also with CSS Grid:

```css
body {
  display: grid;
  height: 100vh;
  place-items: center;
}
```

> [!TIP]
> Want to center something else? Vertically, horizontally...anything, anytime, anywhere? CSS-Tricks has [a nice write-up](https://css-tricks.com/centering-css-complete-guide/) on doing all of that.

#### [Demo](https://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[back to table of contents](#table-of-contents)</sup>


### Use `aspect-ratio` Instead of Height/Width

The `aspect-ratio` property allows you to easily size elements and maintain consistent width-to-height ratio. This is incredibly useful in responsive web design to prevent layout shift. Use `object-fit` with it to prevent disrupting the layout if the height/width values of images changes.

```css
img {
  aspect-ratio: 16 / 9; /* width / height */
  object-fit: cover;
}
```

Learn more about the `aspect-ratio` property in this [web.dev post](https://web.dev/articles/aspect-ratio).

#### [Demo](https://codepen.io/AllThingsSmitty/pen/MWxwoNx/)

<sup>[back to table of contents](#table-of-contents)</sup>


### Comma-Separated Lists

Make list items look like a real, comma-separated list:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Use the `:not()` pseudo-class and no comma will be added to the last item.

> [!NOTE]
> This tip may not be ideal for accessibility, specifically screen readers. And copy/paste from the browser doesn't work with CSS-generated content. Proceed with caution.

<sup>[back to table of contents](#table-of-contents)</sup>


### Select Items Using Negative `nth-child`

Use negative `nth-child` in CSS to select items 1 through n.

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```

Or, since you've already learned a little about [using `:not()`](#use-not-to-applyunapply-borders-on-navigation), try:

```css
/* select all items except the first 3 and display them */
li:not(:nth-child(-n+3)) {
  display: block;
}
```

#### [Demo](https://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[back to table of contents](#table-of-contents)</sup>


### Use SVG for Icons

There's no reason not to use SVG for icons:

```css
.logo {
  background: url("logo.svg");
}
```

SVG scales well for all resolution types and is supported in all browsers [back to IE9](http://caniuse.com/#search=svg). Ditch your .png, .jpg, or .gif-jif-whatev files.

> [!NOTE]
> If you have SVG icon-only buttons for sighted users and the SVG fails to load, this will help maintain accessibility:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[back to table of contents](#table-of-contents)</sup>


### Use the "Lobotomized Owl" Selector

It may have a strange name but using the universal selector (`*`) with the adjacent sibling selector (`+`) can provide a powerful CSS capability:

```css
* + * {
  margin-top: 1.5em;
}
```

In this example, all elements in the flow of the document that follow other elements will receive `margin-top: 1.5em`.

> [!TIP]
> For more on the "lobotomized owl" selector, read [Heydon Pickering's post](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) on *A List Apart*.

#### [Demo](https://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[back to table of contents](#table-of-contents)</sup>


### Use `max-height` for Pure CSS Sliders

Implement CSS-only sliders using `max-height` with overflow hidden:

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

The element expands to the `max-height` value on hover and the slider displays as a result of the overflow.

<sup>[back to table of contents](#table-of-contents)</sup>


### Equal-Width Table Cells

Tables can be a pain to work with. Try using `table-layout: fixed` to keep cells at equal width:

```css
.calendar {
  table-layout: fixed;
}
```

Pain-free table layouts.

#### [Demo](https://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[back to table of contents](#table-of-contents)</sup>


### Get Rid of Margin Hacks With Flexbox

When working with column gutters you can get rid of `nth-`, `first-`, and `last-child` hacks by using flexbox's `space-between` property:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Now column gutters always appear evenly-spaced.

<sup>[back to table of contents](#table-of-contents)</sup>


### Use Attribute Selectors with Empty Links

Display links when the `<a>` element has no text value but the `href` attribute has a link:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

That's really convenient.

#### [Demo](https://codepen.io/AllThingsSmitty/pen/zBzXRx)

> [!NOTE]
> This tip may not be ideal for accessibility, specifically screen readers. And copy/paste from the browser doesn't work with CSS-generated content. Proceed with caution.

<sup>[back to table of contents](#table-of-contents)</sup>


### Control Specificity Better with `:is()`

The `:is()` pseudo-class is used to target multiple selectors at once, reducing redundancy and enhancing code readability. This is incredibly useful for writing large selectors in a more compact form.

```css
:is(section, article, aside, nav) :is(h1, h2, h3, h4, h5, h6) {
  color: green;
}
```

The above ruleset is equivalent to the following number selector rules...

```css
section h1, section h2, section h3, section h4, section h5, section h6,
article h1, article h2, article h3, article h4, article h5, article h6,
aside h1, aside h2, aside h3, aside h4, aside h5, aside h6,
nav h1, nav h2, nav h3, nav h4, nav h5, nav h6 {
  color: green;
}
```

#### [Demo](https://codepen.io/AllThingsSmitty/pen/rNRVxdx)

<sup>[back to table of contents](#table-of-contents)</sup>


### Style "Default" Links

Add a style for "default" links:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Now links that are inserted via a CMS, which don't usually have a `class` attribute, will have a distinction without generically affecting the cascade.

<sup>[back to table of contents](#table-of-contents)</sup>


### Intrinsic Ratio Boxes

To create a box with an intrinsic ratio, all you need to do is apply top or bottom padding to a div:

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

Using 20% for padding makes the height of the box equal to 20% of its width. No matter the width of the viewport, the child div will keep its aspect ratio (100% / 20% = 5:1).

#### [Demo](https://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[back to table of contents](#table-of-contents)</sup>


### Style Broken Images

Make broken images more aesthetically-pleasing with a little bit of CSS:

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

Now add pseudo-elements rules to display a user message and URL reference of the broken image:

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

> [!TIP]
> Learn more about styling for this pattern in [Ire Aderinokun's post](http://bitsofco.de/styling-broken-images/).

<sup>[back to table of contents](#table-of-contents)</sup>


### Use `rem` for Global Sizing; Use `em` for Local Sizing

After setting the base font size at the root (`html { font-size: 100%; }`), set the font size for textual elements to `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Then set the font-size for modules to `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Now each module becomes compartmentalized and easier to style, more maintainable, and flexible.

<sup>[back to table of contents](#table-of-contents)</sup>


### Hide Autoplay Videos That Aren't Muted

This is a great trick for a custom user stylesheet. Avoid overloading a user with sound from a video that autoplays when the page is loaded. If the sound isn't muted, don't show the video:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Once again, we're taking advantage of using the [`:not()`](#use-not-to-applyunapply-borders-on-navigation) pseudo-class.

<sup>[back to table of contents](#table-of-contents)</sup>


### Use `:root` for Flexible Type

The type font size in a responsive layout should be able to adjust with each viewport. You can calculate the font size based on the viewport height and width using `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Now you can utilize the `root em` unit based on the value calculated by `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Demo](https://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[back to table of contents](#table-of-contents)</sup>


### Set `font-size` on Form Elements for a Better Mobile Experience

To avoid mobile browsers (iOS Safari, _et al_.) from zooming in on HTML form elements when a `<select>` drop-down is tapped, add `font-size` to the selector rule:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

<sup>[back to table of contents](#table-of-contents)</sup>


### Use Pointer Events to Control Mouse Events

[Pointer events](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) allow you to specify how the mouse interacts with the element it's touching. To disable the default pointer event on a button, for instance:

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

It's that simple.

<sup>[back to table of contents](#table-of-contents)</sup>


### Set `display: none` on Line Breaks Used as Spacing

As [Harry Roberts pointed out](https://twitter.com/csswizardry/status/1170835532584235008), this can help prevent CMS users from using extra line breaks for spacing:

```css
br + br {
  display: none;
}
```

<sup>[back to table of contents](#table-of-contents)</sup>


### Use `:empty` to Hide Empty HTML Elements

If you have HTML elements that are empty, i.e., the content has yet to be set either by a CMS or dynamically injected (e.g., `<p class="error-message"></p>`) and it's creating unwanted space on your layout, use the `:empty` pseudo-class to hide the element on the layout. 

```css
:empty {
  display: none;
}
```

> [!NOTE]
> Keep in mind that elements with whitespace aren't considered empty, e.g., `<p class="error-message"> </p>`.

<sup>[back to table of contents](#table-of-contents)</sup>


## Support

Current versions of Chrome, Firefox, Safari, and Edge.

<sup>[back to table of contents](#table-of-contents)</sup>


## Translations

> [!NOTE]
> I've had less time available to maintain the growing list of translated tips; adding a new tip requires including it with over a dozen translations. For that reason, translated README files are likely to not include all the tips listed on the main README file.

* [简体中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-CN)
* [正體中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-TW)
* [Deutsch](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/de-DE)
* [Español](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/es-ES)
* [Français](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/fr-FR)
* [λληνικά](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/gr-GR)
* [ગુજરાતી](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/gu-IND)
* [Italiano](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/it-IT)
* [日本語](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ja-JP)
* [한국어](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ko-KR)
* [Polskie](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pl-PL)
* [Português do Brasil](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-BR)
* [Português do Europe](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-PT)
* [Русский](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ru-RU)
* [Tiếng Việt](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/vn-VN)

<sup>[back to table of contents](#table-of-contents)</sup>
