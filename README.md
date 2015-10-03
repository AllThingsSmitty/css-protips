# CSS Protips

A collection of tips to help take your CSS skills pro.

1. [Use `:not()` to Apply/Unapply Borders on Navigation](#use-not-to-applyunapply-borders-on-navigation)
1. [Add Line-Height to `body`](#add-line-height-to-body)
1. [Vertically Center Anything](#vertically-center-anything)
1. [Select Items Using Negative `nth-child`](#select-items-using-negative-nth-child)
1. [Use SVG for Icons](#use-svg-for-icons)
1. [Inherit `box-sizing`](#inherit-box-sizing)
1. [Get Rid of Margin Hacks With Flexbox](#get-rid-of-margin-hacks-with-flexbox)


### Use `:not()` to Apply/Unapply Borders on Navigation

```css
/* instead of putting on the border... */
.nav li {
  border-right: 1px solid #666;
}

/* ...and then taking it off... */
.nav li:last-child {
  border-right: 0;
}

/* ...use :not() to only apply to the elements you want */
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

It's clean, readable, and easy to understand without the need for hack-y code.


### Add Line-Height to `body`

```css
body {
  line-height: 1;
}
```

You don't need to add `line-height` to each `<p>`, `<h*>`, _et al_. separately. This way textual elements can inherit from `body` easily.


### Vertically Center Anything

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

No, it's not dark magic, you really can center elements vertically. Look how simple this is.

**Note:** Watch for some [buggy behavior](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) with flexbox in IE11.


### Select Items Using Negative `nth-child`

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```

Use negative `nth-child` in CSS to select items 1 through n. Well that was pretty easy.


### Use SVG for Icons

```css
.logo {
  background: url("logo.svg");
}
```

There's no reason not to use SVG for icons. SVG is supported in all browsers back to IE9. So ditch your .png, .jpg, or .gif-jif-whatev files.


### Inherit `box-sizing`

```css
html {
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}

```

Letting `box-sizing` be inheritted from `html` makes it easier to change `box-sizing` in plugins or other components that leverage other behavior.


### Get Rid of Margin Hacks With Flexbox

```css
.list-of-people {
  display: flex;
  justify-content: space-between;
}

.list-of-people .person {
  flex-basis: 23%;
}
```

When working with column gutters you can get rid of `nth-`, `first-`, and `last-child` hacks by using flexbox's `space-between` property.


### Support

These protips work in current versions of Chrome, Firefox, Safari, and Edge, and in IE11.