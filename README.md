# CSS Protips

A collection of tips to help take your CSS skills pro.

1. [Use `:not()` to Apply/Unapply Borders on Navigation](#use-not-to-applyunapply-borders-on-navigation)
1. [Add Line-Height to `body`](#add-line-height-to-body)
1. [Vertically-Center Anything](#vertically-center-anything)
1. [Comma-Separated Lists](#comma-separated-lists)
1. [Select Items Using Negative `nth-child`](#select-items-using-negative-nth-child)
1. [Use SVG for Icons](#use-svg-for-icons)
1. [Text Display Optimization](#text-display-optimization)
1. [Use `max-height` for Pure CSS Sliders](#use-max-height-for-pure-css-sliders)
1. [Inherit `box-sizing`](#inherit-box-sizing)
1. [Equal Width Table Cells](#equal-width-table-cells)
1. [Get Rid of Margin Hacks With Flexbox](#get-rid-of-margin-hacks-with-flexbox)
1. [Use Attribute Selectors with Empty Links](#use-attribute-selectors-with-empty-links)
1. [Center a position absolute div within a position relative div](#center-a-position-absolute-div-within-a-position-relative-div)


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


### Add Line-Height to `body`

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

Well that was pretty easy.


### Use SVG for Icons

There's no reason not to use SVG for icons:

```css
.logo {
  background: url("logo.svg");
}
```

SVG scales well for all resolution types and is supported in all browsers back to IE9. So ditch your .png, .jpg, or .gif-jif-whatev files.


### Text Display Optimization

Sometimes fonts don't display optimally on all devices, so let the device browser help:

```css
html {
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  text-rendering: optimizeLegibility;
}
```

**Note:** [Please play with `optimizeLegibility` responsibly](https://bocoup.com/weblog/text-rendering/). Also, there's no `text-rendering` support for IE/Edge.


### Use `max-height` for Pure CSS Sliders

Implement CSS-only sliders using `max-height` with overflow hidden:

```css
.slider ul {
  max-height: 0;
  overlow: hidden;
}

.slider:hover ul {
  max-height: 1000px;
  transition: .3s ease; /* animate to max-height */
}
```


### Inherit `box-sizing`

Let `box-sizing` be inheritted from `html`:

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


### Center a position absolute div within a position relative div

For a div which is position absolute withing a relative div, give a width to the absolute div and give a margin left with a small calculation i.e. `negative( width of position absolute div / 2 )`. You will also need to give left as `50%` now that the absolute div is enclosed within a relative div.

[Demo here](http://codepen.io/ktkaushik/pen/epRMBG)

```css
.absolute-block {
  left: 50%; /* this is also important */
  width: 150px; /* you can set this width to any number but make sure that the margin-left is the negative( width / 2 ) */
  margin-left: -75px;
}

```


### Support

These protips work in current versions of Chrome, Firefox, Safari, and Edge, and in IE11.