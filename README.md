# CSS Protips

A collection of tips to help take your CSS skills pro.


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


### Vertically/Horizontally Center Anything

```css
html, body {
  margin: 0;
  height: 100%;
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


### Select Items Using Negative `nth-child`

```css
li {
  display: none;
}
/* select items 1 through 3 and show them */
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

There's no reason not to use SVG for icons. SVG is supported in all browsers back to IE9. So start ditching your .png, .jpg, or .gif-jif-whatev files.


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