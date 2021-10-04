 <p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" width="200" alt="light bulb icon">
</p>

# CSS Protips [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

আপনার CSS দক্ষতা প্রো নিতে সাহায্য করার জন্য টিপসের একটি সংগ্রহ।

> অন্যান্য দুর্দান্ত তালিকার জন্য দেখুন [@sindresorhus](https://github.com/sindresorhus/)'s এর কিউরেটেড তালিকা [awesome lists](https://github.com/sindresorhus/awesome/).


## Table of Contents

* [প্রোটিপস](#protips)
* [সমর্থন](#support)
* [অনুবাদ](#translations)
* [অবদান নির্দেশিকা](CONTRIBUTING.md)


## Protips

1. [একটি CSS রিসেট ব্যবহার করুন](#use-a-css-reset)
1. [Inherit `box-sizing`](#inherit-box-sizing)
1. [Use `unset` Instead of Resetting All Properties](#use-unset-instead-of-resetting-all-properties)
1. [Use `:not()` to Apply/Unapply Borders on Navigation](#use-not-to-applyunapply-borders-on-navigation)
1. [Check If Font Is Installed Locally](#check-if-font-is-installed-locally)
1. [Add `line-height` to `body`](#add-line-height-to-body)
1. [Set `:focus` for Form Elements](#set-focus-for-form-elements)
1. [Vertically-Center Anything](#vertically-center-anything)
1. [Comma-Separated Lists](#comma-separated-lists)
1. [নেতিবাচক ব্যবহার করে আইটেম নির্বাচন করুন `nth-child`](#select-items-using-negative-nth-child)
1. [ব্যবহার করুন SVG for Icons](#use-svg-for-icons)
1. [ব্যবহার করুন "Lobotomized Owl" Selector](#use-the-lobotomized-owl-selector)
1. [ব্যবহার করুন `max-height` for Pure CSS Sliders](#use-max-height-for-pure-css-sliders)
1. [সমান-প্রস্থ সারণী ঘর](#equal-width-table-cells)
1. [মার্জিন হ্যাকস থেকে মুক্তি পান With Flexbox](#get-rid-of-margin-hacks-with-flexbox)
1. [ব্যবহার করুন Attribute Selectors with Empty Links](#use-attribute-selectors-with-empty-links)
1. [Style "Default" Links](#style-default-links)
1. [Intrinsic Ratio Boxes](#intrinsic-ratio-boxes)
1. [Style Broken Images](#style-broken-images)
1. [ব্যবহার করুন `rem` for Global Sizing; Use `em` for Local Sizing](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [Hide Autoplay Videos That Aren't Muted](#hide-autoplay-videos-that-arent-muted)
1. [ব্যবহার করুন `:root` for Flexible Type](#use-root-for-flexible-type)
1. [Set `font-size` on Form Elements for a Better Mobile Experience](#set-font-size-on-form-elements-for-a-better-mobile-experience)
1. [ব্যবহার করুন Pointer Events to Control Mouse Events](#use-pointer-events-to-control-mouse-events)
1. [Set `display: none` on Line Breaks Used as Spacing](#set-display-none-on-line-breaks-used-as-spacing)


### Use a CSS Reset

CSS রিসেটগুলি স্টাইলিং উপাদানগুলির জন্য একটি পরিষ্কার স্লেট সহ বিভিন্ন ব্রাউজার জুড়ে শৈলীর সামঞ্জস্য প্রয়োগ করতে সহায়তা করে। আপনি একটি CSS রিসেট লাইব্রেরি ব্যবহার করতে পারেন [Normalize](http://necolas.github.io/normalize.css/), _et al._, অথবা আপনি আরো সরলীকৃত রিসেট পদ্ধতি ব্যবহার করতে পারেন:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

এখন উপাদানগুলি মার্জিন এবং প্যাডিং থেকে ছিনিয়ে নেওয়া হবে, এবং `box-sizing` আপনাকে CSS বক্স মডেলের সাথে লেআউট পরিচালনা করতে দেয়।

#### [Demo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Note:** আপনি যদি অনুসরণ করেন [Inherit `box-sizing`](#inherit-box-sizing) নীচের টিপ আপনি অন্তর্ভুক্ত করতে নাও বেছে নিতে পারেন `box-sizing` আপনার CSS রিসেটে সম্পত্তি.

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Inherit `box-sizing`

অনুমান করুন `box-sizing` থেকে উত্তরাধিকার সূত্রে প্রাপ্ত `html`:

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

এটি প্লাগইন বা অন্যান্য উপাদানগুলিতে `box-sizing` পরিবর্তন করা সহজ করে তোলে যা অন্যান্য আচরণকে উপকৃত করে।


#### [Demo](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Use `unset` Instead of Resetting All Properties

একটি উপাদানের বৈশিষ্ট্য পুনরায় সেট করার সময়, প্রতিটি পৃথক সম্পত্তি পুনরায় সেট করার প্রয়োজন হয় না:

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

আপনি `all` শর্টহ্যান্ড ব্যবহার করে একটি উপাদানের সমস্ত বৈশিষ্ট্য উল্লেখ করতে পারেন। মানকে `unset` এ সেট করা একটি উপাদানের বৈশিষ্ট্যগুলিকে তাদের প্রাথমিক মানগুলিতে পরিবর্তন করে:


```css
button {
  all: unset;
}
```

**Note:** the `all` and `unset` IE11 এ শর্টহ্যান্ড সমর্থিত নয়|

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Use `:not()` to Apply/Unapply Borders on Navigation

সীমান্তে লাগানোর পরিবর্তে...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

...এবং তারপর শেষ উপাদান থেকে এটি গ্রহণ...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

... `:not()` ছদ্ম-শ্রেণী ব্যবহার করুন শুধুমাত্র আপনার প্রয়োজনীয় উপাদানগুলিতে প্রয়োগ করতে:


```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

এখানে, সিএসএস সিলেক্টরকে একজন মানুষ হিসেবে পড়লে এটি বর্ণনা করবে।

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Check If Font Is Installed Locally

দূরবর্তীভাবে আনার আগে আপনি একটি ফন্ট স্থানীয়ভাবে ইনস্টল করা আছে কিনা তা পরীক্ষা করতে পারেন, যা একটি ভাল পারফরম্যান্স টিপ।

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

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Add `line-height` to `body`

You don't need to add `line-height` to each `<p>`, `<h*>`, _et al_. separately. Instead, add it to `body`:

```css
body {
  line-height: 1.5;
}
```

This way textual elements can inherit from `body` easily.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Set `:focus` for Form Elements

দৃষ্টিনন্দন কীবোর্ড ব্যবহারকারীরা পাতায় কীবোর্ড ইভেন্টগুলি কোথায় যায় তা নির্ধারণ করতে ফোকাসের উপর নির্ভর করে। ব্রাউজারের ডিফল্ট বাস্তবায়নের জন্য ফর্ম উপাদানগুলিকে আলাদা এবং সামঞ্জস্যপূর্ণ করার জন্য ফোকাস করুন:

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

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Vertically-Center Anything

না, এটি কালো জাদু নয়, আপনি সত্যিই উল্লম্বভাবে উপাদানগুলিকে কেন্দ্র করতে পারেন। আপনি ফ্লেক্সবক্স দিয়ে এটি করতে পারেন ...

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

...এবং সিএসএস গ্রিডের সাথেও:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```


Want to center something else? Vertically, horizontally...anything, anytime, anywhere? CSS-Tricks has [a nice write-up](https://css-tricks.com/centering-css-complete-guide/) on doing all of that.

**Note:** Watch for some [buggy behavior](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) with flexbox in IE11.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Comma-Separated Lists

Make list items look like a real, comma-separated list:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Use the `:not()` pseudo-class and no comma will be added to the last item.

**Note:** This tip may not be ideal for accessibility, specifically screen readers. And copy/paste from the browser doesn't work with CSS-generated content. Proceed with caution.

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


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

অথবা, যেহেতু আপনি ইতিমধ্যে কিছুটা শিখেছেন [using `:not()`](#use-not-to-applyunapply-borders-on-navigation), try:

```css
/* select all items except the first 3 and display them */
li:not(:nth-child(-n+3)) {
  display: block;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Use SVG for Icons

আইকনগুলির জন্য SVG ব্যবহার না করার কোন কারণ নেই:

```css
.logo {
  background: url("logo.svg");
}
```

SGV সমস্ত রেজোলিউশনের প্রকারের জন্য ভাল এবং সমস্ত ব্রাউজারে সমর্থিত [back to IE9](http://caniuse.com/#search=svg). আপনার .png, .jpg, অথবা .gif-jif-whatev ফাইলগুলি খনন করুন।

**Note:** যদি আপনার দৃষ্টিশক্তি ব্যবহারকারীদের জন্য শুধুমাত্র SVG আইকন বোতাম থাকে এবং SVG লোড করতে ব্যর্থ হয়, তাহলে এটি অ্যাক্সেসিবিলিটি বজায় রাখতে সাহায্য করবে:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Use the "Lobotomized Owl" Selector

এর একটি অদ্ভুত নাম থাকতে পারে কিন্তু সংলগ্ন ভাইবোন নির্বাচক (`+`) সহ সর্বজনীন নির্বাচক (`*`) ব্যবহার করে একটি শক্তিশালী CSS ক্ষমতা প্রদান করতে পারে:

```css
* + * {
  margin-top: 1.5em;
}
```

এই উদাহরণে, নথির প্রবাহের সমস্ত উপাদান যা অন্যান্য উপাদানগুলি অনুসরণ করে তা গ্রহণ করবে `margin-top: 1.5em`.

For more on the "lobotomized owl" selector, read [Heydon Pickering's post](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) on *A List Apart*.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Use `max-height` for Pure CSS Sliders

শুধুমাত্র CSS ব্যবহার করে স্লাইডার প্রয়োগ করুন `max-height` ওভারফ্লো লুকানো সঙ্গে:

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

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Equal-Width Table Cells

Tables can be a pain to work with. Try using `table-layout: fixed` to keep cells at equal width:

```css
.calendar {
  table-layout: fixed;
}
```

Pain-free table layouts.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


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

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Use Attribute Selectors with Empty Links

Display links when the `<a>` element has no text value but the `href` attribute has a link:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

That's pretty convenient.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Style "Default" Links

Add a style for "default" links:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Now links that are inserted via a CMS, which don't usually have a `class` attribute, will have a distinction without generically affecting the cascade.

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


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

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


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

Learn more about styling for this pattern in [Ire Aderinokun](https://github.com/ireade/)'s [original post](http://bitsofco.de/styling-broken-images/).

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


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

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Hide Autoplay Videos That Aren't Muted

এটি একটি কাস্টম ব্যবহারকারী স্টাইলশীটের জন্য একটি দুর্দান্ত কৌশল। এমন একটি ভিডিও থেকে ব্যবহারকারীকে ওভারলোড করা থেকে বিরত থাকুন যা পৃষ্ঠা লোড হওয়ার সময় অটোপ্লে হয়। যদি শব্দ নিutedশব্দ না হয়, ভিডিওটি দেখাবেন না:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Once again, we're taking advantage of using the [`:not()`](#use-not-to-applyunapply-borders-on-navigation) pseudo-class.

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Use `:root` for Flexible Type

একটি প্রতিক্রিয়াশীল লেআউটে টাইপ ফন্ট সাইজ প্রতিটি ভিউপোর্টের সাথে সামঞ্জস্য করতে সক্ষম হওয়া উচিত। আপনি ভিউপোর্ট উচ্চতা এবং প্রস্থ ব্যবহার করে ফন্টের আকার গণনা করতে পারেন `:root`:

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

#### [Demo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


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

:dancer:

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Use Pointer Events to Control Mouse Events

[Pointer events](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) মাউস যে উপাদানটি স্পর্শ করছে তার সাথে কীভাবে যোগাযোগ করে তা নির্দিষ্ট করার অনুমতি দেয়। উদাহরণস্বরূপ, একটি বোতামে ডিফল্ট পয়েন্টার ইভেন্ট অক্ষম করতে:

```css
.button-disabled {
  opacity: .5;
  pointer-events: none;
}
```

It's that simple.

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


### Set `display: none` on Line Breaks Used as Spacing

As [Harry Roberts pointed out](https://twitter.com/csswizardry/status/1170835532584235008), this can help prevent CMS users from using extra line breaks for spacing:

```css
br + br {
  display: none;
}
```

<sup>[back to table of contents](#table-of-contents)</sup>


## Support

Current versions of Chrome, Firefox, Safari, Opera, Edge, and IE11.

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>


## Translations

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

<sup>[বিষয়বস্তুর টেবিলে ফিরে যান](#table-of-contents)</sup>
