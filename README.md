# CSS Protips

A collection of tips to help take your CSS skills pro.

![Ty and Al from Caddyshack](img/ty-al.png)

### Use `:not()` to Apply/Unapply Borders on Navigation

```css
/* instead of putting on the border... */
.nav-tab {
  border-right: 1px solid #424242;
}

/* ...and then taking it off... */
.nav-tab:last-child {
  border-right: 0;
}

/* ...use :not() to only apply to the elements you want */
.nav-tab:not(:last-child) {
  border-right: 1px solid #424242;
}
```

It's clean, readable, and easy to understand without the need for hack-y code.


### Vertically Center

```css
html, body {
  margin: 0;
  height: 100%;
}

body {
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-align-items: center;  
  -ms-flex-align: center;  
  align-items: center;
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


### Use SVG...for Everything!

```css
.logo {
  background: url("logo.svg");
}
```

There's no reason not to use SVG for icons. SVG been supported in all browsers since IE9, so start ditching your .png, .jpg, and .gif-jif-whatev files. Icon fonts, too, but that's a different protip.


### Get Rid of Margin Hacks With Flexbox

```css
.list-of-people {
  display: flex;
  justify-content: space-between;
  .person {
    flex-basis: 23%;
  }
}

```

You can get rid of `nth-`, `first-`, and `last-child` hacks when work with column gutters by using the `space-between` property in flexbox. Another flexbox win!


### Support

These protips work in current versions of Chrome, Firefox, Safari, and Edge, and in IE11.

![Carl from Caddyshack](img/carl.png)
Carl became the Cinderalla story by using CSS protips.