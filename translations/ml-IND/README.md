<p align="center">
  <img src="./assets/img/bulb.svg" width="200" alt="light bulb icon">
</p>

# CSS പ്രോട്ടിപ്പുകൾ [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

നിങ്ങളുടെ CSS വൈദഗ്ധ്യം പ്രോൽസാഹിപ്പിക്കാൻ സഹായിക്കുന്ന നുറുങ്ങുകളുടെ ഒരു ശേഖരം.

> മറ്റ് മികച്ച ലിസ്റ്റുകൾക്കായി പരിശോധിക്കുക [@sindresorhus](https://github.com/sindresorhus/)'s ക്യൂറേറ്റ് ചെയ്ത പട്ടിക[awesome lists](https://github.com/sindresorhus/awesome/).


## ഉള്ളടക്ക പട്ടിക

* [പ്രോട്ടിപ്പുകൾ](#protips)
* [പിന്തുണ](#support)
* [വിവർത്തനങ്ങൾ](#translations)
* [സംഭാവന മാർഗ്ഗനിർദ്ദേശങ്ങൾ](CONTRIBUTING.md)


## പ്രോട്ടിപ്പുകൾ

1. [എങ്ങനെ ഒരു CSS റീസെറ്റ് ഉപയോഗിക്കുക](#use-a-css-reset)
1. [ഇൻഹെറിറ്റ `box-sizing`](#inherit-box-sizing)
1. [എല്ലാ പ്രോപ്പർട്ടികളും 'റീസെറ്റ്' പകരം `അൺസെറ്റ്` ഉപയോഗിക്കുക](#use-unset-instead-of-resetting-all-properties)
1. [`:not()` നാവിഗേഷനിൽ ബോർഡറുകൾ പ്രയോഗിക്കാൻ/അൺപ്ലേ ചെയ്യാൻ](#use-not-to-applyunapply-borders-on-navigation)
1. [ഫോണ്ട് ലോക്കലായി ഇൻസ്റ്റാൾ ചെയ്തിട്ടുണ്ടോയെന്ന് പരിശോധിക്കുക](#check-if-font-is-installed-locally)
1. [ആഡ് `line-height`  ട്ടോ `body`](#add-line-height-to-body)
1. [ `:focus` ഫോം ഘടകങ്ങൾക്കായി](#set-focus-for-form-elements)
1. [ലംബമായി - എന്തും കേന്ദ്രീകരിക്കുക](#vertically-center-anything)
1. [കോമയാൽ വേർതിരിച്ച ലിസ്റ്റുകൾ](#comma-separated-lists)
1. [നെഗറ്റീവ് nth-child ഉപയോഗിക്കുന്ന ഇനങ്ങൾ തിരഞ്ഞെടുക്കുക](#select-items-using-negative-nth-child)
1. [ഐക്കണുകൾക്കായി SVG ഉപയോഗിക്കുക](#use-svg-for-icons)
1. ["ലോബോടോമൈസ്ഡ് ഔൾ" സെലക്ടർ ഉപയോഗിക്കുക](#use-the-lobotomized-owl-selector)
1. [പ്യുവർ CSS സ്ലൈഡറുകൾക്കായി `max-height` ഉപയോഗിക്കുക](#use-max-height-for-pure-css-sliders)
1. [തുല്യ വീതിയുള്ള പട്ടിക സെല്ലുകൾ](#equal-width-table-cells)
1. [Flexbox ഉപയോഗിച്ച് മാർജിൻ ഹാക്കുകൾ ഒഴിവാക്കുക](#get-rid-of-margin-hacks-with-flexbox)
1. [ശൂന്യമായ ലിങ്കുകളുള്ള ആട്രിബ്യൂട്ട് സെലക്ടറുകൾ ഉപയോഗിക്കുക](#use-attribute-selectors-with-empty-links)
1. [ശൈലി "സ്ഥിര" ലിങ്കുകൾ](#style-default-links)
1. [ആന്തരിക അനുപാത ബോക്സുകൾ](#intrinsic-ratio-boxes)
1. [സ്റ്റൈൽ തകർന്ന ചിത്രങ്ങൾ](#style-broken-images)
1. [ഗ്ലോബൽ സൈസിംഗിനായി `rem` ഉപയോഗിക്കുക; പ്രാദേശിക വലുപ്പത്തിനായി `em` ഉപയോഗിക്കുക](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [മ്യൂട്ടുചെയ്യാത്ത ഓട്ടോപ്ലേ വീഡിയോകൾ മറയ്ക്കുക](#hide-autoplay-videos-that-arent-muted)
1. [ഫ്ലെക്സിബിൾ തരത്തിന് `:root` ഉപയോഗിക്കുക](#use-root-for-flexible-type)
1. [മികച്ച മൊബൈൽ അനുഭവത്തിനായി ഫോം എലമെന്റുകളിൽ `ഫോണ്ട്-സൈസ്` സജ്ജീകരിക്കുക](#set-font-size-on-form-elements-for-a-better-mobile-experience)
1. [മൗസ് ഇവന്റുകൾ നിയന്ത്രിക്കാൻ പോയിന്റർ ഇവന്റുകൾ ഉപയോഗിക്കുക](#use-pointer-events-to-control-mouse-events)
1. [സ്‌പെയ്‌സിംഗ് ആയി ഉപയോഗിക്കുന്ന ലൈൻ ബ്രേക്കുകളിൽ `ഡിസ്‌പ്ലേ: ഒന്നുമില്ല' എന്ന് സജ്ജീകരിക്കുക](#set-display-none-on-line-breaks-used-as-spacing)
1. [ശൂന്യമായ HTML ഘടകങ്ങൾ മറയ്ക്കാൻ `:empty` ഉപയോഗിക്കുക](#use-empty-to-hide-empty-html-elements)


### എങ്ങനെ ഒരു CSS റീസെറ്റ് ഉപയോഗിക്കുക

സ്റ്റൈലിംഗ് ഘടകങ്ങൾക്ക് ക്ലീൻ സ്ലേറ്റ് ഉപയോഗിച്ച് വ്യത്യസ്ത ബ്രൗസറുകളിലുടനീളം സ്റ്റൈൽ സ്ഥിരത നടപ്പിലാക്കാൻ CSS റീസെറ്റുകൾ സഹായിക്കുന്നു. നിങ്ങൾക്ക് ഒരു CSS റീസെറ്റ് ലൈബ്രറി ഉപയോഗിക്കാം [Normalize](http://necolas.github.io/normalize.css/), _et al._, അല്ലെങ്കിൽ നിങ്ങൾക്ക് കൂടുതൽ ലളിതമായ റീസെറ്റ് സമീപനം ഉപയോഗിക്കാം:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

ഇപ്പോൾ ഘടകങ്ങൾ മാർജിനുകളും പാഡിംഗും നീക്കം ചെയ്യും, കൂടാതെ `ബോക്സ്-സൈസിംഗ്` നിങ്ങളെ CSS ബോക്സ് മോഡൽ ഉപയോഗിച്ച് ലേഔട്ടുകൾ നിയന്ത്രിക്കാൻ അനുവദിക്കുന്നു.

#### [ഡെമോ](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക:** നിങ്ങൾ പിന്തുടരുകയാണെങ്കിൽ[Inherit `box-sizing`](#inherit-box-sizing) നിങ്ങളുടെ CSS റീസെറ്റിലെ പ്രോപ്പർട്ടി `box-sizing` ഉൾപ്പെടുത്താതിരിക്കാൻ നിങ്ങൾ തീരുമാനിച്ചേക്കാം .

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### ഇൻഹെറിറ്റ `box-sizing`

`box-sizing` എന്നത് `html`-ൽ നിന്ന് പാരമ്പര്യമായി ലഭിക്കട്ടെ:

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

ഇത് പ്ലഗിന്നുകളിലോ മറ്റ് സ്വഭാവത്തെ സ്വാധീനിക്കുന്ന മറ്റ് ഘടകങ്ങളിലോ `ബോക്സ്-സൈസിംഗ്` മാറ്റുന്നത് എളുപ്പമാക്കുന്നു.

#### [ഡെമോ](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### എല്ലാ പ്രോപ്പർട്ടികളും പുനഃസജ്ജമാക്കുന്നതിന് പകരം `അൺസെറ്റ്` ഉപയോഗിക്കുക

ഒരു മൂലകത്തിന്റെ പ്രോപ്പർട്ടികൾ പുനഃസജ്ജമാക്കുമ്പോൾ, ഓരോ വ്യക്തിഗത സ്വത്തും പുനഃസജ്ജമാക്കേണ്ട ആവശ്യമില്ല:

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

`എല്ലാം` ഷോർട്ട്‌ഹാൻഡ് ഉപയോഗിച്ച് നിങ്ങൾക്ക് ഒരു ഘടകത്തിന്റെ എല്ലാ ഗുണങ്ങളും വ്യക്തമാക്കാൻ കഴിയും. മൂല്യം `അൺസെറ്റ്` ആയി സജ്ജീകരിക്കുന്നത് മൂലകത്തിന്റെ ഗുണങ്ങളെ അവയുടെ പ്രാരംഭ മൂല്യങ്ങളിലേക്ക് മാറ്റുന്നു:

```css
button {
  all: unset;
}
```

**കുറിപ്പ്:** `എല്ലാം`, `അൺസെറ്റ്` എന്നീ ചുരുക്കെഴുത്ത് IE11-ൽ പിന്തുണയ്ക്കുന്നില്ല.

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### നാവിഗേഷനിൽ ബോർഡറുകൾ പ്രയോഗിക്കാൻ/അൺപ്ലേ ചെയ്യാൻ `:not()` ഉപയോഗിക്കുക

border ഇടുന്നതിനു പകരം...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

...എന്നിട്ട് അത് അവസാനത്തെ element നിന്ന് എടുക്കുക...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

...നിങ്ങൾ ആഗ്രഹിക്കുന്ന ഘടകങ്ങളിൽ മാത്രം പ്രയോഗിക്കുന്നതിന് `:not()` pseudo-ക്ലാസ് ഉപയോഗിക്കുക:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

ഇവിടെ, ഒരു മനുഷ്യൻ വിവരിക്കുന്നതുപോലെ CSS സെലക്ടർ വായിക്കുന്നു.

#### [ഡെമോ](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### ഫോണ്ട് ലോക്കലായി ഇൻസ്റ്റാൾ ചെയ്തിട്ടുണ്ടോയെന്ന് പരിശോധിക്കുക

ഒരു ഫോണ്ട് വിദൂരമായി ലഭ്യമാക്കുന്നതിന് മുമ്പ് അത് പ്രാദേശികമായി ഇൻസ്റ്റാൾ ചെയ്തിട്ടുണ്ടോ എന്ന് നിങ്ങൾക്ക് പരിശോധിക്കാം, ഇത് ഒരു നല്ല പ്രകടന ടിപ്പാണ്.

```css
@font-face {
  font-family: "Dank Mono";
  src:
    /* Full name */
    local("Dank Mono"),
    /* Postscript name */
    local("Dank-Mono"),
    /* Otherwise, download it! */
    url("//...a.server/fonts/DankMono.woff");
}

code {
  font-family: "Dank Mono", system-ui-monospace;
}
```

ഈ പ്രോത്സാഹനം പങ്കിട്ടതിന് ആദം ആർഗൈലിന് H/T[ഡെമോ](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


###`ബോഡി` എന്നതിലേക്ക് `ലൈൻ-ഹൈറ്റ്` ചേർക്കുക

ഓരോ `<p>`, `<h*>`, _et al_ എന്നിവയിലും നിങ്ങൾ `line-height` ചേർക്കേണ്ടതില്ല. പ്രത്യേകം. പകരം, ഇത് `body` എന്നതിലേക്ക് ചേർക്കുക:
```css
body {
  line-height: 1.5;
}
```

ഇതുവഴി വാചക ഘടകങ്ങൾക്ക് `ശരീരത്തിൽ` നിന്ന് എളുപ്പത്തിൽ അവകാശം നേടാനാകും.

#### [ഡെമോ](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


###ഫോം ഘടകങ്ങൾക്കായി `:focus` സജ്ജീകരിക്കുക

പേജിൽ കീബോർഡ് ഇവന്റുകൾ എവിടേക്കാണ് പോകുന്നതെന്ന് നിർണ്ണയിക്കാൻ കാഴ്ചയുള്ള കീബോർഡ് ഉപയോക്താക്കൾ ഫോക്കസിനെ ആശ്രയിക്കുന്നു. ബ്രൗസറിന്റെ ഡിഫോൾട്ട് നിർവ്വഹണത്തേക്കാൾ ഫോം ഘടകങ്ങൾ വേറിട്ടുനിൽക്കുന്നതും സ്ഥിരതയുള്ളതുമാക്കി മാറ്റുക:

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

#### [ഡെമോ](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### ലംബമായി - എന്തും കേന്ദ്രീകരിക്കുക

ഇല്ല, ഇത് ബ്ലാക്ക് മാജിക് അല്ല, നിങ്ങൾക്ക് ശരിക്കും ഘടകങ്ങൾ ലംബമായി കേന്ദ്രീകരിക്കാൻ കഴിയും. ഫ്ലെക്സ്ബോക്സ് ഉപയോഗിച്ച് നിങ്ങൾക്ക് ഇത് ചെയ്യാൻ കഴിയും...

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

...കൂടാതെ CSS ഗ്രിഡിനൊപ്പം:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```


മറ്റെന്തെങ്കിലും കേന്ദ്രീകരിക്കാൻ ആഗ്രഹിക്കുന്നുണ്ടോ? ലംബമായി, തിരശ്ചീനമായി...എന്തെങ്കിലും, എപ്പോൾ വേണമെങ്കിലും, എവിടെയും? CSS-Tricks ഉണ്ട് [ഒരു നല്ല എഴുത്ത്](https://css-tricks.com/centering-css-complete-guide/).

**ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക:** ചിലത് ശ്രദ്ധിക്കുക[ബഗ്ഗി പെരുമാറ്റം](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) IE11-ൽ ഫ്ലെക്സ്ബോക്സിനൊപ്പം.

#### [ഡെമോ](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### കോമയാൽ വേർതിരിച്ച ലിസ്റ്റുകൾ

ലിസ്റ്റ് ഇനങ്ങൾ ഒരു യഥാർത്ഥ, കോമയാൽ വേർതിരിച്ച ലിസ്റ്റ് പോലെയാക്കുക:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

`:not()` സ്യൂഡോ-ക്ലാസ് ഉപയോഗിക്കുക, അവസാന ഇനത്തിലേക്ക് കോമ ചേർക്കില്ല.

**ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക:** ഈ നുറുങ്ങ് പ്രവേശനക്ഷമതയ്ക്ക്, പ്രത്യേകിച്ച് സ്ക്രീൻ റീഡറുകൾക്ക് അനുയോജ്യമല്ലായിരിക്കാം. കൂടാതെ ബ്രൗസറിൽ നിന്ന് പകർത്തുക/ഒട്ടിക്കുക എന്നത് CSS സൃഷ്ടിച്ച ഉള്ളടക്കത്തിൽ പ്രവർത്തിക്കില്ല. ശ്രദ്ധയോടെ മുൻപൊട്ട് പോകുക.

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### നെഗറ്റീവ് `nth-child` ഉപയോഗിച്ച് ഇനങ്ങൾ തിരഞ്ഞെടുക്കുക

1 മുതൽ n വരെയുള്ള ഇനങ്ങൾ തിരഞ്ഞെടുക്കാൻ CSS-ൽ നെഗറ്റീവ് `nth-child` ഉപയോഗിക്കുക.

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```

അല്ലെങ്കിൽ, നിങ്ങൾ ഇതിനകം കുറച്ച് പഠിച്ചതിനാൽ[`:not()` ഉപയോഗിക്കുന്നു](#use-not-to-applyunapply-borders-on-navigation):

```css
/* select all items except the first 3 and display them */
li:not(:nth-child(-n+3)) {
  display: block;
}
```

#### [ഡെമോ](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


###ഐക്കണുകൾക്കായി SVG ഉപയോഗിക്കുക

ഐക്കണുകൾക്കായി SVG ഉപയോഗിക്കാതിരിക്കാൻ ഒരു കാരണവുമില്ല:

```css
.logo {
  background: url("logo.svg");
}
```

SVG എല്ലാ റെസല്യൂഷൻ തരങ്ങൾക്കും നന്നായി സ്കെയിൽ ചെയ്യുന്നു കൂടാതെ എല്ലാ ബ്രൗസറുകളിലും പിന്തുണയ്ക്കുന്നു [IE9 ലേക്ക്](http://caniuse.com/#search=svg). നിങ്ങളുടെ .png, .jpg, അല്ലെങ്കിൽ .gif-jif-whatev ഫയലുകൾ ഒഴിവാക്കുക.

**ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക:** കാഴ്ചയുള്ള ഉപയോക്താക്കൾക്കായി നിങ്ങൾക്ക് SVG ഐക്കൺ-മാത്രം ബട്ടണുകൾ ഉണ്ടെങ്കിൽ, SVG ലോഡുചെയ്യുന്നതിൽ പരാജയപ്പെടുകയാണെങ്കിൽ, ഇത് പ്രവേശനക്ഷമത നിലനിർത്താൻ സഹായിക്കും:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### "ലോബോടോമൈസ്ഡ് ഔൾ" സെലക്ടർ ഉപയോഗിക്കുക

ഇതിന് വിചിത്രമായ ഒരു പേരുണ്ടാകാം, എന്നാൽ സാർവത്രിക സെലക്ടർ (`*`) ഉപയോഗിച്ച് അടുത്തുള്ള സഹോദരൻ സെലക്ടർ (`+`) ഉപയോഗിച്ച് ശക്തമായ CSS കഴിവ് നൽകാം:
```css
* + * {
  margin-top: 1.5em;
}
```

ഈ ഉദാഹരണത്തിൽ, മറ്റ് ഘടകങ്ങളെ പിന്തുടരുന്ന പ്രമാണത്തിന്റെ ഒഴുക്കിലെ എല്ലാ ഘടകങ്ങളും സ്വീകരിക്കും `margin-top: 1.5em`.

"ലോബോടോമൈസ്ഡ് ഔൾ" സെലക്ടറെ കുറിച്ച് കൂടുതൽ അറിയാൻ, *എ ലിസ്റ്റ് അപാർട്ട്* എന്നതിൽ [ഹെയ്ഡൺ പിക്കറിംഗിന്റെ പോസ്റ്റ്](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) വായിക്കുക.
#### [ഡെമോ](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### പ്യുവർ CSS സ്ലൈഡറുകൾക്കായി `max-height` ഉപയോഗിക്കുക

ഓവർഫ്ലോ മറച്ചുകൊണ്ട് `max-height` ഉപയോഗിച്ച് CSS-മാത്രം സ്ലൈഡറുകൾ നടപ്പിലാക്കുക:

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

ഹോവറിലെ `max-height` മൂല്യത്തിലേക്ക് ഘടകം വികസിക്കുകയും ഓവർഫ്ലോയുടെ ഫലമായി സ്ലൈഡർ പ്രദർശിപ്പിക്കുകയും ചെയ്യുന്നു.
<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### തുല്യ വീതിയുള്ള പട്ടിക സെല്ലുകൾ

ടേബിളുകൾ പ്രവർത്തിക്കുന്നത് വേദനാജനകമാണ്. ഉപയോഗിക്കാൻ ശ്രമിക്കുക`table-layout: fixed` സെല്ലുകളെ തുല്യ വീതിയിൽ നിലനിർത്താൻ:

```css
.calendar {
  table-layout: fixed;
}
```

Pain-free ടേബിൾ ലേഔട്ടുകൾ.

#### [ഡെമോ](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### Flexbox ഉപയോഗിച്ച് മാർജിൻ ഹാക്കുകൾ ഒഴിവാക്കുക

കോളം ഗട്ടറുകളിൽ പ്രവർത്തിക്കുമ്പോൾ, ഫ്ലെക്‌സ്‌ബോക്‌സിന്റെ `സ്‌പേസ്-ബിറ്റ്‌വീൻ` പ്രോപ്പർട്ടി ഉപയോഗിച്ച് നിങ്ങൾക്ക് `nth-`, `fist-`, `last-child` ഹാക്കുകൾ ഒഴിവാക്കാം:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

ഇപ്പോൾ കോളം ഗട്ടറുകൾ എപ്പോഴും തുല്യ-അകലത്തിൽ ദൃശ്യമാകുന്നു.

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### ശൂന്യമായ ലിങ്കുകളുള്ള ആട്രിബ്യൂട്ട് സെലക്ടറുകൾ ഉപയോഗിക്കുക

`<a>` മൂലകത്തിന് വാചക മൂല്യം ഇല്ലെങ്കിലും `href` ആട്രിബ്യൂട്ടിന് ഒരു ലിങ്ക് ഉള്ളപ്പോൾ ലിങ്കുകൾ പ്രദർശിപ്പിക്കുക:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

അത് വളരെ സൗകര്യപ്രദമാണ്.

**ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക:** ഈ നുറുങ്ങ് പ്രവേശനക്ഷമതയ്ക്ക്, പ്രത്യേകിച്ച് സ്ക്രീൻ റീഡറുകൾക്ക് അനുയോജ്യമല്ലായിരിക്കാം. കൂടാതെ ബ്രൗസറിൽ നിന്ന് പകർത്തുക/ഒട്ടിക്കുക എന്നത് CSS സൃഷ്ടിച്ച ഉള്ളടക്കത്തിൽ പ്രവർത്തിക്കില്ല. ശ്രദ്ധയോടെ മുൻപൊട്ട് പോകുക.

#### [ഡെമോ](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### ശൈലി "default" ലിങ്കുകൾ

"ഡിഫോൾട്ട്" ലിങ്കുകൾക്കായി ഒരു ശൈലി ചേർക്കുക:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

സാധാരണയായി ഒരു `ക്ലാസ്` ആട്രിബ്യൂട്ട് ഇല്ലാത്ത, CMS വഴി ചേർത്തിരിക്കുന്ന ലിങ്കുകൾക്ക് കാസ്‌കേഡിനെ പൊതുവായി ബാധിക്കാതെ ഒരു വ്യത്യാസം ഉണ്ടായിരിക്കും.

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### ആന്തരിക അനുപാത ബോക്സുകൾ

അന്തർലീനമായ അനുപാതമുള്ള ഒരു ബോക്‌സ് സൃഷ്‌ടിക്കുന്നതിന്, നിങ്ങൾ ചെയ്യേണ്ടത് ഒരു ഡിവിയിലേക്ക് മുകളിലോ താഴെയോ പാഡിംഗ് പ്രയോഗിക്കുക: 

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

പാഡിംഗിനായി 20% ഉപയോഗിക്കുന്നത് ബോക്‌സിന്റെ ഉയരം അതിന്റെ വീതിയുടെ 20% ആക്കുന്നു. വ്യൂപോർട്ടിന്റെ വീതി പ്രശ്നമല്ല, ചൈൽഡ് ഡിവി അതിന്റെ വീക്ഷണാനുപാതം (100% / 20% = 5:1) നിലനിർത്തും.

#### [ഡെമോ](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### സ്റ്റൈൽ broken ചിത്രങ്ങൾ

കുറച്ച് CSS ഉപയോഗിച്ച് broken ചിത്രങ്ങൾ കൂടുതൽ സൗന്ദര്യാത്മകമാക്കുക:

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

ഇപ്പോൾ ഒരു ഉപയോക്തൃ സന്ദേശവും broken ചിത്രത്തിന്റെ URL റഫറൻസും പ്രദർശിപ്പിക്കുന്നതിന് കപട ഘടകങ്ങളുടെ നിയമങ്ങൾ ചേർക്കുക:

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

[Ire Aderinokun](https://github.com/ireade/) ന്റെ [യഥാർത്ഥ കുറിപ്പ്](http://bitsofco.de/styling-broken-images/) എന്നതിൽ ഈ പാറ്റേണിനായുള്ള സ്റ്റൈലിംഗിനെക്കുറിച്ച് കൂടുതലറിയുക.

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### ഗ്ലോബൽ സൈസിംഗിനായി `rem` ഉപയോഗിക്കുക; പ്രാദേശിക വലുപ്പത്തിനായി `em` ഉപയോഗിക്കുക

അടിസ്ഥാന ഫോണ്ട് വലുപ്പം റൂട്ടിൽ സജ്ജീകരിച്ച ശേഷം (`html { font-size: 100%; }`), വാചക ഘടകങ്ങളുടെ ഫോണ്ട് വലുപ്പം `em` ആയി സജ്ജമാക്കുക:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

തുടർന്ന് മൊഡ്യൂളുകൾക്കുള്ള ഫോണ്ട് വലുപ്പം `rem` ആയി സജ്ജമാക്കുക:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```
ഇപ്പോൾ ഓരോ മൊഡ്യൂളും കംപാർട്ട്മെന്റലൈസ് ചെയ്യുകയും സ്റ്റൈലിലേക്ക് എളുപ്പമുള്ളതും കൂടുതൽ പരിപാലിക്കാവുന്നതും വഴക്കമുള്ളതുമായി മാറുന്നു.

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### മ്യൂട്ടുചെയ്യാത്ത ഓട്ടോപ്ലേ വീഡിയോകൾ മറയ്ക്കുക

ഒരു ഇഷ്‌ടാനുസൃത ഉപയോക്തൃ സ്റ്റൈൽഷീറ്റിനുള്ള മികച്ച ട്രിക്ക് ആണിത്. പേജ് ലോഡ് ചെയ്യുമ്പോൾ സ്വയമേവ പ്ലേ ചെയ്യുന്ന ഒരു വീഡിയോയിൽ നിന്നുള്ള ശബ്ദം ഉപയോഗിച്ച് ഉപയോക്താവിനെ ഓവർലോഡ് ചെയ്യുന്നത് ഒഴിവാക്കുക. ശബ്ദം നിശബ്ദമാക്കിയിട്ടില്ലെങ്കിൽ, വീഡിയോ കാണിക്കരുത്:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

ഒരിക്കൽ കൂടി, [`:not()`](#use-not-to-applyunapply-borders-on-navigation) pseudo-class ഉപയോഗിക്കുന്നത് ഞങ്ങൾ പ്രയോജനപ്പെടുത്തുന്നു.

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### ഫ്ലെക്സിബിൾ തരത്തിന് `:root` ഉപയോഗിക്കുക

ഒരു റെസ്‌പോൺസീവ് ലേഔട്ടിലെ ടൈപ്പ് ഫോണ്ട് സൈസ് ഓരോ വ്യൂപോർട്ടിലും ക്രമീകരിക്കാൻ കഴിയണം. വ്യൂപോർട്ട് ഉയരവും വീതിയും അടിസ്ഥാനമാക്കി നിങ്ങൾക്ക് `:root` ഉപയോഗിച്ച് ഫോണ്ട് വലുപ്പം കണക്കാക്കാം:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

ഇപ്പോൾ നിങ്ങൾക്ക് `:root` കണക്കാക്കിയ മൂല്യത്തെ അടിസ്ഥാനമാക്കി `root em` യൂണിറ്റ് ഉപയോഗിക്കാം:
```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [ഡെമോ](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### മികച്ച മൊബൈൽ അനുഭവത്തിനായി ഫോം എലമെന്റുകളിൽ `ഫോണ്ട്-സൈസ്` സജ്ജീകരിക്കുക

`<select>` ഡ്രോപ്പ്-ഡൗൺ ടാപ്പുചെയ്യുമ്പോൾ HTML ഫോം ഘടകങ്ങളിൽ സൂം ഇൻ ചെയ്യുന്നതിൽ നിന്ന് മൊബൈൽ ബ്രൗസറുകൾ (iOS Safari, _et al_) ഒഴിവാക്കാൻ, സെലക്ടർ റൂളിലേക്ക് `font-size` ചേർക്കുക:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### മൗസ് ഇവന്റുകൾ നിയന്ത്രിക്കാൻ പോയിന്റർ ഇവന്റുകൾ ഉപയോഗിക്കുക

[പോയിന്റർ ഇവന്റുകൾ](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) മൗസ് സ്പർശിക്കുന്ന ഘടകവുമായി എങ്ങനെ ഇടപെടുന്നുവെന്ന് വ്യക്തമാക്കാൻ നിങ്ങളെ അനുവദിക്കുന്നു. ഒരു ബട്ടണിലെ ഡിഫോൾട്ട് പോയിന്റർ ഇവന്റ് പ്രവർത്തനരഹിതമാക്കുന്നതിന്, ഉദാഹരണത്തിന്:

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

അത് വളരെ ലളിതമാണ്.

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### സ്‌പെയ്‌സിംഗ് ആയി ഉപയോഗിക്കുന്ന ലൈൻ ബ്രേക്കുകളിൽ `ഡിസ്‌പ്ലേ: ഒന്നുമില്ല' എന്ന് സജ്ജീകരിക്കുക
[ഹാരി റോബർട്ട്സ് ചൂണ്ടിക്കാണിച്ചതുപോലെ](https://twitter.com/csswizardry/status/1170835532584235008), സ്‌പെയ്‌സിംഗിനായി അധിക ലൈൻ ബ്രേക്കുകൾ ഉപയോഗിക്കുന്നതിൽ നിന്ന് CMS ഉപയോക്താക്കളെ തടയാൻ ഇത് സഹായിക്കും:

```css
br + br {
  display: none;
}
```

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


### ശൂന്യമായ HTML ഘടകങ്ങൾ മറയ്ക്കാൻ `:empty` ഉപയോഗിക്കുക

നിങ്ങൾക്ക് ശൂന്യമായ HTML ഘടകങ്ങൾ ഉണ്ടെങ്കിൽ, അതായത്, ഉള്ളടക്കം ഇതുവരെ ഒരു CMS വഴി സജ്ജീകരിക്കുകയോ ചലനാത്മകമായി കുത്തിവയ്ക്കുകയോ ചെയ്തിട്ടില്ല (ഉദാ. `<p class="error-message"></p>`) അത് അനാവശ്യ ഇടം സൃഷ്ടിക്കുന്നു നിങ്ങളുടെ ലേഔട്ടിൽ, ലേഔട്ടിലെ മൂലകം മറയ്ക്കാൻ `:empty` കപട-ക്ലാസ് ഉപയോഗിക്കുക.

```css
:empty {
  display: none;
}
```

**ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക:** വൈറ്റ്‌സ്‌പെയ്‌സുള്ള ഘടകങ്ങൾ ശൂന്യമായി കണക്കാക്കുന്നില്ലെന്ന് ഓർമ്മിക്കുക, ഉദാ., `<p class="error-message"> </p>`.

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


## പിന്തുണ

Chrome, Firefox, Safari, Opera, Edge, IE11 എന്നിവയുടെ നിലവിലെ പതിപ്പുകൾ.

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>


## Translations

**ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക:** വിവർത്തനം ചെയ്‌ത നുറുങ്ങുകളുടെ വർദ്ധിച്ചുവരുന്ന പട്ടിക നിലനിർത്താൻ എനിക്ക് കുറച്ച് സമയമേ ലഭ്യമായിട്ടുള്ളൂ; ഒരു പുതിയ നുറുങ്ങ് ചേർക്കുന്നതിന് അത് ഒരു ഡസനിലധികം വിവർത്തനങ്ങളിൽ ഉൾപ്പെടുത്തേണ്ടതുണ്ട്. ഇക്കാരണത്താൽ, വിവർത്തനം ചെയ്ത README ഫയലുകളിൽ പ്രധാന README ഫയലിൽ ലിസ്റ്റ് ചെയ്തിരിക്കുന്ന എല്ലാ നുറുങ്ങുകളും ഉൾപ്പെട്ടേക്കില്ല.

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
* [മലയാളം](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ml-IND)
* [Polskie](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pl-PL)
* [Português do Brasil](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-BR)
* [Português do Europe](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-PT)
* [Русский](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ru-RU)
* [Tiếng Việt](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/vn-VN)

<sup>[ഉള്ളടക്ക പട്ടികയിലേക്ക് മടങ്ങുക](#table-of-contents)</sup>
