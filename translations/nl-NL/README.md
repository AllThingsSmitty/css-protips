# CSS protips Awesome

Een collectie van tips om jouw CSS vaardigheden naar pro level.

> Voor meer awesome lijsten check [@sindresorhus](https://github.com/sindresorhus/)'s  [samengestelde lijst van awesome lijsten](https://github.com/sindresorhus/awesome/)

## inhoudsopgaven

* [Protips](#protips)
* [Ondersteuning](#ondersteuning)
* [Vertalingen](#vertalingen)
* [Contributie richtlijnen](CONTRIBUTING.md)
 
## Protips

1. [Gebruik een CSS reset](#gebruik-een-css-reset)
1. [Overerven van `box-sizing`](#overerven-van-box-sizing)
1. [Gebruik `unset` in plaats van alle attributen te resetten](#gebruik-unset-in-plaats-van-alle-attributen-te-resetten)
1. [Gebruik `:not()` voor het toevoegen/weghalen van randen op navigatie](#gebruik-not-voor-het-toevoegenweghalen-van-randen-op-navigatie)
1. [Voeg `line-height` toe aan `body`](#voeg-line-height-toe-aan-body)
1. [Centreer alles verticaal](#centreer-alles-verticaal)
1. [Comma gescheiden lijsten](#comma-gescheiden-lijsten)
1. [Selecteer items met negatieef `nth-child`](#selecteer-items-met-negatieef-nth-child)
1. [Gebruik SVG voor iconen](#gebruik-svg-voor-iconen)
1. [Gebruik de "Lobotomized Owl" Selector](#gebruik-de-lobotomized-owl-selector)
1. [Gebruik `max-height` voor pure css sliders](#gebruik-max-height-voor-pure-css-sliders)
1. [Tabel cellen met dezelfde breedte](#tabel-cellen-met-dezelfde-breedte)
1. [Geen marge hacks meer met Flexbox](#geen-marge-hacks-meer-met-flexbox)
1. [Gebruik attribuut selectoren met lege links](#gebruik-attribuut-selectoren-met-lege-links)
1. [Stijl "standaard" links](#stijl-standaard-links)
1. [Consistent verticaal ritme](#consistent-verticaal-ritme)
1. [Intrinsieke ratio boxes](#intrinsieke-ratio-boxes)
1. [Stijl gebroken afbeeldingen](#stijl-gebroken-afbeeldingen)
1. [Gebruik `rem` voor globale vergroting, gebruik `em` voor lokale vergroting](#gebruik-rem-voor-globale-vergroting-gebruik-em-voor-lokale-vergroting)
1. [Verberg automatisch afspelende video's die niet gemute zijn](#verberg-automatisch-afspelende-videos-die-niet-gemute-zijn)
1. [Gebruik `:root` voor flexibele type](#gebruik-root-voor-flexibele-type)
1. [Zet `font-size` op form elementen voor een betere mobiele ervaring](#zet-font-size-op-form-elementen-voor-een-betere-mobiele-ervaring)
1. [Gebruik pointer events om control te nemen over muis events](#gebruik-pointer-events-om-control-te-nemen-over-muis-events)


### Gebruik een CSS reset

CSS resets helpt met forceren van een consistente stijl in verschillende browsers door een schone lei stijl toe te passen op elementen. Je kan gebruik maken van een CSS reset module zoals Normalize of van een meer simpele aanpak:

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Element worden nu ontnomen van marges, vulling en `box-sizing` maakt layouts beheren mogelijk via het CSS box model.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Attentie**: Als je de hieronder genoemde Overerven van `box-sizing` tip volgt dan kan je kiezen het `box-sizing` attribuut niet in de CSS reset te zetten.

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Overerven van `box-sizing`

Erf `box-sizing` over van `html`:

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

Dit maakt het makkelijker om de `box-sizing` te veranderen in plugins of andere componenten die gebruik maken van ander gedrag.

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Gebruik `unset` in plaats van alle attributen te resetten

Het is niet nodig elk individueel attribuut handmatig te resetten op een element:


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

Het is mogelijk alle attributen van een element te specificeren met het `all` attribuut. Zet de waarde naar `unset` om de attributen van een elementen terug te zetten naar de initiële waarde.

```css
button {
  all: unset;
}
```

**Attentie:** het `all` attribuut wordt niet ondersteund in IE11 en wordt overwogen te ondersteunen in Edge.

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Gebruik `:not()` voor het toevoegen/weghalen van randen op navigatie

In plaats van een rand toe te voegen...

```css
/* Voeg rand toe */
.nav li {
  border-right: 1px solid #666;
}
```

... om vervolgens de rand van het laatste element af te halen...

```css
/* Verwijder rand */
.nav li:last-child {
  border-right: none;
}
```

...gebruik de `:not()` psuedo klasse om de stijl op de gewenste elementen toe te passen:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Het is natuurlijk mogelijk om `.nav li + li` te gebruiken, maar met `:not()` is de intentie duidelijk en de CSS selector definieert de rand zoals een mens het zou beschrijven.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Voeg `line-height` toe aan `body`

Je hoeft geen `line-height` los toe te voegen aan elk `<p>`, `<h*>`, et al. Voeg het toe aan de `body`:


```css
body {
  line-height: 1.5;
}
```

Deze manier maakt het makkelijker voor tekst elementen om over te erven van `body`.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Centreer alles verticaal

Nee, het is geen zwarte magie. Het is mogelijk om echt elk element verticaal te centreren door gebruik te maken van flexbox...

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

...en met CSS Grid:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

Wil je een ander element centreren? Verticaal, horizontaal, elke directie op elk moment? CSS-tricks heeft een goed artikel om dat voor elkaar te krijgen.

**Attentie:** Kijk uit voor vreemd gedrag met flexbox in IE11

#### [Demo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Comma gescheiden lijsten

Transformeer lijst items naar een comma gescheiden lijst:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Gebruik de `:not()` psuedo klasse om geen comma aan het laatste item toe te voegen.

**Attentie:** Deze tip kan niet ideaal zijn voor toegankelijkheid. Screen readers in het specifiek. Ook werken kopieer/plak operataties vanuit de browsers niet op CSS gengenereerde inhoud. Voeg met beleid toe.

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Selecteer items met negatieef `nth-child`

Gebruik negatief `nth-child` in CSS om items te selecteren van 1 tot n.

```css
li {
  display: none;
}

/* selecteer items 1 t/m 3 and laat ze zien */
li:nth-child(-n+3) {
  display: block;
}
```

De `:not()` psuedo klasse kan ook gebruikt worden:

```css
/* selecteer alle items behavle de eerste drie en laat ze zien */
li:not(:nth-child(-n+3)) {
  display: block;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Gebruik SVG voor iconen

Er is geen reden om SVG niet te gebruiken voor iconen:


```css
.logo {
  background: url("logo.svg");
}
```

SVG schaalt goed op elke resolutie en wordt ondersteund in alle browsers.

**Attentie:** Als je gebruik maakt van knoppen met alleen een SVG als icoon voor slechtziende gebruikers. Wanneer de SVG faalt om in te laden helpt dit om te toegankelijkheid te waarborgen:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Gebruik de "Lobotomized Owl" Selector

Het heeft misschien een vreemde naam maar het gebruik van de universele selector (`*`) met het aangenzend element selector (`+`) kan zorgen voor een krachtige CSS functionaliteit:

```css
* + * {
  margin-top: 1.5em;
}
```

In dit voorbeeld ontvangen alle elementen in de flow van het document die gevolgd worden door een ander element de `margin-top: 1.5em`.

Voor meer informatie over de "lobotomized owl" selector, lees [Heydon Pickering's post](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) op *A List Apart*.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Gebruik `max-height` voor pure css sliders

Implementeer sliders die alleen gebruik maken van CSS met `max-height` en geen overflow:

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

Het element vergroot naar de waarden van `max-height` op hover en de slider wordt weergeven als resultaat van de overflow.

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Tabel cellen met dezelfde breedte

Het kan verveldend zijn om met tabellen te werken. Probeer `table-layout: fixed` te gebruiken om de breedte van de cellen te bewaren.

```css
.calendar {
  table-layout: fixed;
}
```

Pijnloze tabel layouts.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Geen marge hacks meer met Flexbox

Wanneer er gewerkt wordt met Kolommengoten kan je `nth-`, `first-` en `last-child` hacks vervangen met flexbox's `space-between` attribuut.

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Kolommengoten verschijnen nu altijd op gelijke afstand van elkaar.

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>


### Gebruik attribuut selectoren met lege links

Geef links weer wanneer het `<a>` element geen tekst bevat maar het `href` attribuut wel ingevuld is:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Stijl "standaard" links

Voeg een stijl toe aan "standaard" links:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Links die via een CMS toegevoegd worden die meestal geen `class` attribuut hebben, worden nu ondersheiden zonder de cascade aan te passen.

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Consistent verticaal ritme

Gebruik een universele selector (`*`) in een element om een consistent verticaal ritme te maken:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

Een consistent verticaal ritme zorgt voor een visueel aesthetisch effect waardoor de inhoud meer leesbaar word.

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Intrinsieke ratio boxes

Om een box te maken met een intrinsieke ratio hoe je alleen meer een top of bodem opvulling toe te voegen:


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

Het gebruik van 20% van de opvulling maakt de hoogte van de box gelijk aan 20% van de breedte. Ongeacht de breedte van de viewport, het onderliggende div behoudt zijn aspect ratio  (100% / 20% = 5:1).

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Stijl gebroken afbeeldingen

Maak gebroken afbeeldingen meer aesthetisch aangenaam met een beetje CSS:

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

Voeg psuedo elementen regels toe om een bericht met de URL aan de gebruiker te weergeven.

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

Lees meer over dit patroon op [Ire Aderinokun](https://github.com/ireade/)'s [original post](http://bitsofco.de/styling-broken-images/).

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Gebruik `rem` voor globale vergroting, gebruik `em` voor lokale vergroting

Na het instellen van de basis lettergroote op de root (`html { font-size: 100%; }`), zet de lettergroote voor tekstuele element op `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Zet de lettergroote voor modules op `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Nu wordt elke module gecompartimenteerd en gemakkelijker te stijlen, beter te onderhouden en flexibeler.

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Verberg automatisch afspelende video's die niet gemute zijn

Dit is een geweldige truuc voor een gebruiker instelbaar stylesheet. Vermijdt het iriteren van een gebruiker met geluid van een video die automatisch afgespeeld wordt wanneer de pagina is geladen. Als het geluid niet op stil is gezet, laat de video niet zien:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

We maken nogmaals gebruik van de  [`:not()`](#use-not-to-applyunapply-borders-on-navigation) psuedo klasse.

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Gebruik `:root` voor flexibele type

De lettergroote in een responsive layout moet zichzelf aanpassen voor elk viewport. De lettergroote kan berekent worden op basis van de viewport hoogte en breedte door `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Het is nu mogelijk om gebruik te maken van de `root em` unit gebaseerd op de berekende waarde van `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```
 
#### [Demo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Zet `font-size` op form elementen voor een betere mobiele ervaring

Om te voorkomen dat mobiele browsers (IOS Safari, _et al_.) inzoomen op HTML form elementen wanneer een `<select>` drop-down is getapped. Voeg `font-size` toe aan de selector regel:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

### Gebruik pointer events om control te nemen over muis events

[Pointer events](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) allow you to specifiy how the mouse interacts with the element it's touching. To disable the default pointer event on a button, for instance:

```css
.button-disabled {
  opacity: .5;
  pointer-events: none;
}
```

Het is zo simpel

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

## Ondersteuning
Huidige versies van Chrome, Firefox, Safari, Opera, Edge en IE11.

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>

## Vertalingen

* [简体中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-CN)
* [正體中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-TW)
* [Deutsche](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/de-DE)
* [Español](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/es-ES)
* [Français](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/fr-FR)
* [ગુજરાતી](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/gu-IND)
* [Italiano](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/it-IT)
* [日本語](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ja-JP)
* [한국어](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ko-KR)
* [Polskie](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pl-PL)
* [Português do Brasil](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-BR)
* [Português do Europe](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-PT)
* [Русский](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ru-RU)
* [Nederlands](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/nl-NL)

<sup>[Terug naar inhoudsopgaven](#inhoudsopgaven)</sup>


