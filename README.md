<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" alt="light bulb icon">
</p>

# CSS Protips [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

A collection of tips to help take your CSS skills pro.

> For other great lists check out [@sindresorhus](https://github.com/sindresorhus/)'s curated list of [awesome lists](https://github.com/sindresorhus/awesome/).


## Table of Contents

* [Protips](#protips)
* [Support](#support)
* [Contribution Guidelines](CONTRIBUTING.md)


## Protips

1. [Use `:not()` to Apply/Unapply Borders on Navigation](#use-not-to-applyunapply-borders-on-navigation)
1. [Add `line-height` to `body`](#add-line-height-to-body)
1. [Vertically-Center Anything](#vertically-center-anything)
1. [Comma-Separated Lists](#comma-separated-lists)
1. [Select Items Using Negative `nth-child`](#select-items-using-negative-nth-child)
1. [Use SVG for Icons](#use-svg-for-icons)
1. [Use the "Lobotomized Owl" Selector](#use-the-lobotomized-owl-selector)
1. [Use `max-height` for Pure CSS Sliders](#use-max-height-for-pure-css-sliders)
1. [Inherit `box-sizing`](#inherit-box-sizing)
1. [Equal Width Table Cells](#equal-width-table-cells)
1. [Get Rid of Margin Hacks With Flexbox](#get-rid-of-margin-hacks-with-flexbox)
1. [Use Attribute Selectors with Empty Links](#use-attribute-selectors-with-empty-links)
1. [Style "Default" Links](#style-default-links)
1. [Consistent Vertical Rhythm](#consistent-vertical-rhythm)
1. [Intrinsic Ratio Boxes](#intrinsic-ratio-boxes)
1. [Easily Fit an Image Inside Its Container](#easily-fit-an-image-inside-its-container)

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

Sure, you can use `.nav li + li` or even `.nav li:first-child ~ li`, but with `:not()` the intent is very clear and the CSS selector defines the border the way a human would describe it.


### Add `line-height` to `body`

You don't need to add `line-height` to each `<p>`, `<h*>`, _et al_. separately. Instead, add it to `body`:

```css
body {
  line-height: 1;
}
```

This way textual elements can inherit from `body` easily.


### Vertically-Center Anything

No, it's not black magic, you really can center elements vertically:

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

Want to center something else? Vertically, horizontally...anything, anytime, anywhere? CSS-Tricks has [a nice write-up](https://css-tricks.com/centering-css-complete-guide/) on doing all of that.

**Note:** Watch for some [buggy behavior](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) with flexbox in IE11.


### Comma-Separated Lists

Make list items look like a real, comma-separated list:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Use the `:not()` pseudo-class so no comma is added to the last item.

**Note:** This tip may not be ideal for accessibility, specifically screen readers. And copy/paste from the browser doesn't work with CSS-generated content. Proceed with caution.


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
/* select items 1 through 3 and display them */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Well that was pretty easy.


### Use SVG for Icons

There's no reason not to use SVG for icons:

```css
.logo {
  background: url("logo.svg");
}
```

SVG scales well for all resolution types and is supported in all browsers [back to IE9](http://caniuse.com/#search=svg). So ditch your .png, .jpg, or .gif-jif-whatev files.

**Note:** If you have SVG icon-only buttons for sighted users and the SVG fails to load, this will help maintain accessibility:

```css
.no-svg .icon-only:after {
  content: attr(aria-label);
}
```


### Use the "Lobotomized Owl" Selector

It may have a strange name but using the universal selector (`*`) with the adjacent sibling selector (`+`) can provide a powerful CSS capability:

```css
* + * {
  margin-top: 1.5em;
}
```

In this example, all elements in the flow of the document that follow other elements will receive `margin-top: 1.5em`.

For more on the "lobotomized owl" selector, read [Heydon Pickering's post](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) on *A List Apart*.


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


### Inherit `box-sizing`

Let `box-sizing` be inherited from `html`:

```css
html {
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}

```

This makes it easier to change `box-sizing` in plugins or other components that leverage other behavior.


### Equal Width Table Cells

Tables can be a pain to work with so try using `table-layout: fixed` to keep cells at equal width:

```css
.calendar {
  table-layout: fixed;
}
```

Pain-free table layouts.


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


### Use Attribute Selectors with Empty Links

Display links when the `<a>` element has no text value but the `href` attribute has a link:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

That's pretty convenient.


### Style "Default" Links

Add a style for "default" links:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Now links that are inserted via a CMS, which don't usually have a `class` attribute, will have a distinction without generically affecting the cascade.


### Consistent Vertical Rhythm

Use a universal selector (`*`) within an element to create a consistent vertical rhythm:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

Consistent vertical rhythm provides a visual aesthetic that makes content far more readable.


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


### Easily Fit an Image Inside Its Container

You can easily specify how an image (or video) is fitted inside its container by assigning the `object-fit` property to the element itself:

```css
.img {
  object-fit: cover;
}
```
and the even reposition it thanks to the `object-position` property!

Supported values are :
* `cover` fills image into the parent element so it's fully covered and contains aspect-ratio.
* `contain` fills image into the parent element so the object is fully shown.
* `fill` fills image into the parent element so it's fully covered and shrinks image, not respecting aspect-ratio.

Beware of [browser compatibility](http://caniuse.com/#search=object-position), this one is tricky: only Firefox and Chrome have native support!

## Support

Current versions of Chrome, Firefox, Safari, Opera, Edge, and IE11.
