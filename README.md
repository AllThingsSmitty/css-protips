<div align="center">
  <img src=".github/assets/banner.png" style="width: 100%" alt="CSS Protips banner">
</div>

# CSS Protips [![Awesome](https://awesome.re/badge-flat.svg)](https://awesome.re)

A collection of tips to help take your CSS skills pro.

> [!TIP]
> For other great lists check out [@sindresorhus](https://github.com/sindresorhus/)'s curated list of [awesome lists](https://github.com/sindresorhus/awesome/).

## Contents

- [Protips](#protips)
- [Support](#support)
- [Translations](#translations)
- [Contribution Guidelines](CONTRIBUTING.md)

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
1. [Use `margin-inline` instead of `margin`](#use-margin-inline-instead-of-margin)

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
> If you follow the [Inherit `box-sizing`](#inherit-box-sizing) tip below you might opt to not include the `box-sizing` property in your CSS reset.

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

### Check if Font Is Installed Locally

You can check if a font is installed locally before fetching it remotely, which is a good performance tip, too.

```css
@font-face {
  font-family: "Dank Mono";
  src:
    /* Full name */
    local("Dank Mono"),
    /* Postscript name */ local("Dank Mono"),
    /* Otherwise, download it! */ url("//...a.server/fonts/DankMono.woff");
}

code {
  font-family: "Dank Mono", system-ui-monospace;
}
```

H/T to Adam Argyle for sharing this protip and [demo](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[Back to top](#contents)</sup>

### Add `line-height` to `body`

You don't need to add `line-height` to each `<p>`, `<h*>`, _et al_. separately. Instead, add it to `body`:

```css
body {
  line-height: 1.5;
}
```

This way textual elements can inherit from `body` easily.

#### [Demo](https://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[Back to top](#contents)</sup>

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
  outline-offset: 0.05em;
}
```

#### [Demo](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

### Select Items Using Negative `nth-child`

Use negative `nth-child` in CSS to select items 1 through n.

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n + 3) {
  display: block;
}
```

Or, since you've already learned a little about [using `:not()`](#use-not-to-applyunapply-borders-on-navigation), try:

```css
/* select all items except the first 3 and display them */
li:not(:nth-child(-n + 3)) {
  display: block;
}
```

#### [Demo](https://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

### Use the "Lobotomized Owl" Selector

It may have a strange name but using the universal selector (`*`) with the adjacent sibling selector (`+`) can provide a powerful CSS capability:

```css
* + * {
  margin-top: 1.5em;
}
```

In this example, all elements in the flow of the document that follow other elements will receive `margin-top: 1.5em`.

> [!TIP]
> For more on the "lobotomized owl" selector, read [Heydon Pickering's post](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) on _A List Apart_.

#### [Demo](https://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

### Equal-Width Table Cells

Tables can be a pain to work with. Try using `table-layout: fixed` to keep cells at equal width:

```css
.calendar {
  table-layout: fixed;
}
```

Pain-free table layouts.

#### [Demo](https://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

### Control Specificity Better with `:is()`

The `:is()` pseudo-class is used to target multiple selectors at once, reducing redundancy and enhancing code readability. This is incredibly useful for writing large selectors in a more compact form.

```css
:is(section, article, aside, nav) :is(h1, h2, h3, h4, h5, h6) {
  color: green;
}
```

The above ruleset is equivalent to the following number selector rules...

```css
section h1,
section h2,
section h3,
section h4,
section h5,
section h6,
article h1,
article h2,
article h3,
article h4,
article h5,
article h6,
aside h1,
aside h2,
aside h3,
aside h4,
aside h5,
aside h6,
nav h1,
nav h2,
nav h3,
nav h4,
nav h5,
nav h6 {
  color: green;
}
```

#### [Demo](https://codepen.io/AllThingsSmitty/pen/rNRVxdx)

<sup>[Back to top](#contents)</sup>

### Style "Default" Links

Add a style for "default" links:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Now links that are inserted via a CMS, which don't usually have a `class` attribute, will have a distinction without generically affecting the cascade.

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

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
  font-size: 0.9rem;
}
```

Now each module becomes compartmentalized and easier to style, more maintainable, and flexible.

<sup>[Back to top](#contents)</sup>

### Hide Autoplay Videos That Aren't Muted

This is a great trick for a custom user stylesheet. Avoid overloading a user with sound from a video that autoplays when the page is loaded. If the sound isn't muted, don't show the video:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Once again, we're taking advantage of using the [`:not()`](#use-not-to-applyunapply-borders-on-navigation) pseudo-class.

<sup>[Back to top](#contents)</sup>

### Use `:root` for Flexible Type

The type font size in a responsive layout should be able to adjust with each viewport. You can calculate the font size based on the viewport height and width using `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + 0.5vmin);
}
```

Now you can utilize the `root em` unit based on the value calculated by `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Demo](https://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[Back to top](#contents)</sup>

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

<sup>[Back to top](#contents)</sup>

### Use Pointer Events to Control Mouse Events

[Pointer events](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) allow you to specify how the mouse interacts with the element it's touching. To disable the default pointer event on a button, for instance:

```css
button:disabled {
  opacity: 0.5;
  pointer-events: none;
}
```

It's that simple.

<sup>[Back to top](#contents)</sup>

### Set `display: none` on Line Breaks Used as Spacing

As [Harry Roberts pointed out](https://twitter.com/csswizardry/status/1170835532584235008), this can help prevent CMS users from using extra line breaks for spacing:

```css
br + br {
  display: none;
}
```

<sup>[Back to top](#contents)</sup>

### Use `:empty` to Hide Empty HTML Elements

If you have HTML elements that are empty, i.e., the content has yet to be set either by a CMS or dynamically injected (e.g., `<p class="error-message"></p>`) and it's creating unwanted space on your layout, use the `:empty` pseudo-class to hide the element on the layout.

```css
:empty {
  display: none;
}
```

> [!NOTE]
> Keep in mind that elements with whitespace aren't considered empty, e.g., `<p class="error-message"> </p>`.

<sup>[Back to top](#contents)</sup>

## Support

Current versions of Chrome, Firefox, Safari, and Edge.

<sup>[Back to top](#contents)</sup>

### Use `margin-inline` instead of `margin`

`margin-inline` defines the inline start and end margins of an element. So instead of using `margin-left` and `margin-right` we can use the inline property to define both.

```css
.div {
  margin-inline: auto;
}
```

The same can be done for `margin-block` with defines the block start and end margins, i.e., `margin-top` and `margin-bottom`.

```css
.div {
  margin-block: auto;
}
```

#### [Demo](https://codepen.io/AllThingsSmitty/pen/PwoOQGB)

<sup>[Back to top](#contents)</sup>

## Translations

> [!NOTE]
> I've had less time available to maintain the growing list of translated tips; adding a new tip requires including it with over a dozen translations. For that reason, translated README files are likely to not include all the tips listed on the main README file.

- [简体中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-CN)
- [正體中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-TW)
- [Deutsch](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/de-DE)
- [Español](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/es-ES)
- [Français](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/fr-FR)
- [λληνικά](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/gr-GR)
- [ગુજરાતી](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/gu-IND)
- [Italiano](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/it-IT)
- [日本語](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ja-JP)
- [한국어](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ko-KR)
- [Polskie](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pl-PL)
- [Português do Brasil](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-BR)
- [Português do Europe](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-PT)
- [Русский](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ru-RU)
- [Tiếng Việt](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/vn-VN)

<sup>[Back to top](#contents)</sup>


## 🌐 Web Resources & Interactive Index
- [EAT DONUTS](https://frskillcrafts.pages.dev/eat-donuts.html)
- [STUDENT AND TEACHER](https://studyquests.pages.dev/student-and-teacher.html)
- [BUBBLE POP FAIRYLAND](https://studyquests.github.io/bubble-pop-fairyland.html)
- [CATEGORY 1 PLAYER139](https://studyplaying.github.io/category-1-player139.html)
- [POLICE CAR LINE DRIVING](https://learnquesters.pages.dev/police-car-line-driving.html)
- [CATEGORY FPS 2](https://studyquesthub.web.app/category-fps-2.html)
- [CATEGORY COLOR197](https://studyquesthub.web.app/category-color197.html)
- [ANTISTRESS SIMULATOR OF SEQUINS DIY](https://studyquests.github.io/antistress-simulator-of-sequins-diy.html)
- [ITALIAN BRAINROT DRAG MERGE PUZZLE](https://studyquests.github.io/italian-brainrot-drag-merge-puzzle.html)
- [SKYHILL ESCAPE FROM THE SKYSCRAPER](https://studyquests.github.io/skyhill-escape-from-the-skyscraper.html)
- [FUN OBBY EXTREME](https://studyquests.github.io/fun-obby-extreme.html)
- [HEADLEG DASH PARKOUR](https://studyquests.pages.dev/headleg-dash-parkour.html)
- [INDEX34](https://studyplaying.github.io/index34.html)
- [CATEGORY ARENA255](https://studyquesthub.web.app/category-arena255.html)
- [CITYQUEST](https://studyquesthub.web.app/cityquest.html)
- [PASSENGER SORT](https://studyquests.pages.dev/passenger-sort.html)
- [ZOMBIE OUTBREAK SURVIVE](https://studyquesthub.web.app/zombie-outbreak-survive.html)
- [LAST UFO DEFENSE](https://studyquests.pages.dev/last-ufo-defense.html)
- [TRAIN DRIFT](https://studyquesthub.web.app/train-drift.html)
- [DALGONA MASTER](https://studyquests.pages.dev/dalgona-master.html)
- [LOVE CATS ROPE](https://studyquests.github.io/love-cats-rope.html)
- [CATEGORY BATTLE524](https://studyquesthub.web.app/category-battle524.html)
- [CATEGORY PUZZLE 4](https://studyquests.pages.dev/category-puzzle-4.html)
- [SKYSCRAPER TO THE SKY](https://studyquesthub.web.app/skyscraper-to-the-sky.html)
- [MONSTER MERGE LEGENDS ALIVE](https://studyquests.pages.dev/monster-merge-legends-alive.html)
- [BADLAND](https://studyquests.github.io/badland.html)
- [HIDE ME](https://studyquesthub.web.app/hide-me.html)
- [CHICKEN BANANA QUEST](https://studyquests.github.io/chicken-banana-quest.html)
- [BUBBLE SHOOTER FREE 3](https://themindplaying.web.app/bubble-shooter-free-3.html)
- [DOWNTOWN PARKOUR DRIVE](https://studyquests.pages.dev/downtown-parkour-drive.html)
- [CATEGORY CRAFTING45](https://themindplay.github.io/category-crafting45.html)
- [CATEGORY MATCH 3 2](https://studyquests.pages.dev/category-match-3-2.html)
- [CATEGORY MERGE GAMES](https://themindplay.github.io/category-merge-games.html)
- [ARCHERS RANDOM](https://themindplays.pages.dev/archers-random.html)
- [CATEGORY CAN T STOP PLAYING212](https://themindplay.github.io/category-can-t-stop-playing212.html)
- [BUS DRIVER SIMULATOR 3D](https://studyquests.github.io/bus-driver-simulator-3d.html)
- [IMPOSTOR AMONG SPACE](https://studyquests.github.io/impostor-among-space.html)
- [SKINFLUENCER BEAUTY ROUTINE](https://iskillquest.pages.dev/skinfluencer-beauty-routine.html)
- [FPS TOY REALISM](https://iskillquest.pages.dev/fps-toy-realism.html)
- [JIGSAW M](https://iskillquest.pages.dev/jigsaw-m.html)
- [AMONG SQUID CHALLENGE ONLINE](https://iskillquest.pages.dev/among-squid-challenge-online.html)
- [CUBEREALM IO](https://studyquesthub.web.app/cuberealm-io.html)
- [CATEGORY MONSTER207](https://themindplay.github.io/category-monster207.html)
- [REAL CAR PARKING SIMULATOR](https://iskillquest.pages.dev/real-car-parking-simulator.html)
- [FLOOF MY PET HOUSE](https://studyquests.github.io/floof-my-pet-house.html)
- [MERGEDUELIO](https://studyquests.github.io/mergeduelio.html)
- [CATEGORY BIKE](https://studyquesthub.web.app/category-bike.html)
- [INDEX14](https://themindplaying.web.app/index14.html)
- [MERGE SHOOTER](https://iskillquest.pages.dev/merge-shooter.html)
- [SQUID GAME MEMORY CARD MATCH](https://studyquests.github.io/squid-game-memory-card-match.html)
- [PURRFECT SCOOPS](https://iskillquest.pages.dev/purrfect-scoops.html)
- [PYRAMID SOLITAIRE ANCIENT EGYPT](https://themindplay.pages.dev/pyramid-solitaire-ancient-egypt.html)
- [SWIPETOWN](https://studyquests.pages.dev/swipetown.html)
- [SLIDE BLOCK PUZZLE](https://themindplaying.web.app/slide-block-puzzle.html)
- [SPIDER SOLITAIRE 2 SUITS](https://studyquesthub.web.app/spider-solitaire-2-suits.html)
- [GUESS THE DRAWING](https://themindplays.pages.dev/guess-the-drawing.html)
- [SHEEP SHEEP DUCK](https://iskillquest.pages.dev/sheep-sheep-duck.html)
- [CATEGORY ARENA255](https://studyplaying.github.io/category-arena255.html)
- [CATEGORY FPS GAMES](https://themindplay.pages.dev/category-fps-games.html)
- [LOVIE CHICS COACHELLA FESTIVAL](https://studyquesthub.web.app/lovie-chics-coachella-festival.html)
- [THIEF STICK PUZZLE MAN ESCAPE](https://themindplays.pages.dev/thief-stick-puzzle-man-escape.html)
- [SPACEBAR CLICKER](https://themindplays.pages.dev/spacebar-clicker.html)
- [SKY MAZE CHALLENGE](https://themindplay.pages.dev/sky-maze-challenge.html)
- [WILD TANKS](https://studyquests.github.io/wild-tanks.html)
- [GROSS OUT RUN](https://studyquests.pages.dev/gross-out-run.html)
- [FOOD TRUCK CHEF COOKING](https://studyquests.github.io/food-truck-chef-cooking.html)
- [SMART DOTS RELOADED](https://studyquests.github.io/smart-dots-reloaded.html)
- [CATEGORY CONTROLLER 2](https://themindplay.github.io/category-controller-2.html)
- [LADDER MASTER COLOR RUN](https://studyquests.github.io/ladder-master-color-run.html)
- [CATEGORY SOCCER 2](https://themindplay.pages.dev/category-soccer-2.html)
- [BARRY PRISON HIDE AND SEEK](https://studyquests.github.io/barry-prison-hide-and-seek.html)
- [CATEGORY FOOD95](https://themindplay.github.io/category-food95.html)
- [OFFICE KNIGHT 3D CASTLE DEFENSE](https://themindplay.pages.dev/office-knight-3d-castle-defense.html)
- [WORD SCRAMBLE FAMILY TALES](https://themindplays.pages.dev/word-scramble-family-tales.html)
- [HAPPY FRUIT LINK](https://iskillquest.pages.dev/happy-fruit-link.html)
- [CATEGORY ALIEN34](https://themindplaying.web.app/category-alien34.html)
- [SLINKY COLOR SORT](https://studyquests.github.io/slinky-color-sort.html)
- [IDOL LIVESTREAM DOLL DRESS UP](https://quizverses-9d2f2.web.app/idol-livestream-doll-dress-up.html)
- [ZOMBIE DEFENSE WAR](https://themindplay.pages.dev/zombie-defense-war.html)
- [HEADLEG DASH PARKOUR](https://themindplay.pages.dev/headleg-dash-parkour.html)
- [CIRCLE RUN ENDLESS](https://themindplays.pages.dev/circle-run-endless.html)
- [CATEGORY MOUSE1 697](https://themindplay.github.io/category-mouse1-697.html)
- [CUBES 2048IO](https://themindplaying.web.app/cubes-2048io.html)
- [PICK BRAINROT 3D BATTLE](https://quizverses.pages.dev/pick-brainrot-3d-battle.html)
- [SUGAR HEROES](https://studyquests.pages.dev/sugar-heroes.html)
- [CATEGORY CASUAL 11](https://themindplays.pages.dev/category-casual-11.html)
- [STICKMAN ZOMBIE VS STICKMAN HERO](https://iskillquest.pages.dev/stickman-zombie-vs-stickman-hero.html)
- [SWORD LIFE](https://studyquests.pages.dev/sword-life.html)
- [CATEGORY IDLE](https://themindplay.github.io/category-idle.html)
- [MOTO TRIALS RUSH](https://iskillquest.pages.dev/moto-trials-rush.html)
- [CATEGORY POOL 2](https://quizverses.pages.dev/category-pool-2.html)
- [AGENT HUNT SPY SHOOTER GAME](https://themindplay.pages.dev/agent-hunt-spy-shooter-game.html)
- [CATEGORY DRESS UP](https://studyquests.pages.dev/category-dress-up.html)
- [DTA 2 MANIAC](https://studyquests.pages.dev/dta-2-maniac.html)
- [CATEGORY SHOOTER](https://themindplay.pages.dev/category-shooter.html)
- [POXEL IO](https://studyquests.github.io/poxel-io.html)
- [LOOPER](https://themindplays.pages.dev/looper.html)
- [MECHA DUEL](https://quizverses-9d2f2.web.app/mecha-duel.html)
- [ANIMERGE](https://themindplay.pages.dev/animerge.html)
- [TOWER WARS ARENA](https://quizverses-9d2f2.web.app/tower-wars-arena.html)
- [CHICKEN SHOOTER IO](https://studyquests.github.io/chicken-shooter-io.html)
- [CATEGORY SOLDIER](https://quizverses.pages.dev/category-soldier.html)
- [GOOD TO DRIVE](https://quizverses-9d2f2.web.app/good-to-drive.html)
- [CARDS KLONDIKE SOLITAIRE](https://themindplaying.web.app/cards-klondike-solitaire.html)
- [TAP GALLERY](https://themindplay.pages.dev/tap-gallery.html)
- [HELICOPTER BATTLE STEVE 2 PLAYER](https://quizverses-9d2f2.web.app/helicopter-battle-steve-2-player.html)
- [JUICY MATCH](https://studyquests.github.io/juicy-match.html)
- [MERMAIDS SPOT THE DIFFERENCES](https://studyquests.pages.dev/mermaids-spot-the-differences.html)
- [THE SORT AGENCY](https://themindplays.pages.dev/the-sort-agency.html)
- [SOLITAIRE STORY TRIPEAKS 6](https://skillplay.github.io/solitaire-story-tripeaks-6.html)
- [UNSCREW WOOD PUZZLE](https://quizverses-9d2f2.web.app/unscrew-wood-puzzle.html)
- [CATEGORY BUBBLE SHOOTER](https://studyquesthub.web.app/category-bubble-shooter.html)
- [ITALIAN BRAINROT CLICKER](https://quizverses-9d2f2.web.app/italian-brainrot-clicker.html)
- [CATEGORY CAT55](https://skillplay.github.io/category-cat55.html)
- [CATEGORY IDLE CLICKER GAME](https://quizverses.pages.dev/category-idle-clicker-game.html)
- [AMERICAN BLOCK SNIPER ONLINE](https://studyquests.github.io/american-block-sniper-online.html)
- [PENTAWORD](https://studyquesthub.web.app/pentaword.html)
- [CATEGORY SURVIVAL366](https://studyquests.pages.dev/category-survival366.html)
- [CHRISTMAS CANDY ESCAPE 3D](https://studyquests.github.io/christmas-candy-escape-3d.html)
- [MARBLE RUN ULTIMATE RACE](https://themindplays.pages.dev/marble-run-ultimate-race.html)
- [CATEGORY CRAFTING45](https://themindplaying.web.app/category-crafting45.html)
- [PUZZLE BLOCKS](https://themindplay.pages.dev/puzzle-blocks.html)
- [CATEGORY CONTROLLER 2](https://skillplay.github.io/category-controller-2.html)
- [TRICKY CASTLE](https://iskillquest.pages.dev/tricky-castle.html)
- [INCREDIBLE KIDS DENTIST](https://themindplays.pages.dev/incredible-kids-dentist.html)
- [CATEGORY SNAKE40](https://quizverses.pages.dev/category-snake40.html)
- [INDEX9](https://studyquests.github.io/index9.html)
- [CUT THE ROPE 2](https://themindplay.pages.dev/cut-the-rope-2.html)
- [IDLE BATHROOM EMPIRE TYCOON](https://themindplays.pages.dev/idle-bathroom-empire-tycoon.html)
- [GRAND MAHJONG](https://themindplaying.web.app/grand-mahjong.html)
