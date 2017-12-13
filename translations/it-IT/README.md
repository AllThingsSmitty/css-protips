<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" alt="light bulb icon">
</p>

# CSS suggerimenti per esperti [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Una collezione di dritte per aiutarti a migliorare le tue capacità con CSS.

> Per altre fantastiche liste di questo tipo guarda la [lista di fantastiche liste](https://github.com/sindresorhus/awesome/) curata da [@sindresorhus](https://github.com/sindresorhus/).


## Sommario

* [Suggerimenti per esperti](#suggerimenti-per-esperti)
* [Supporto](#supporto)
* [Linee guida per contribuire](../../CONTRIBUTING.md)


## Suggerimenti per esperti

1. [Utilizzare un reset CSS](#use-a-css-reset)
1. [Eredita il `box-sizing`](#inherit-box-sizing)
1. [Usa `:not()` per applicare/rimuovere i bordi su elementi di navigazione](#use-not-to-applyunapply-borders-on-navigation)
1. [Aggiungi `line-height` al `body`](#add-line-height-to-body)
1. [Centra verticalmente qualsiasi cosa](#vertically-center-anything)
1. [Liste separate da virgola](#comma-separated-lists)
1. [Seleziona un elemento usando gli `nth-child` negativi](#select-items-using-negative-nth-child)
1. [Usa SVG per le icone](#use-svg-for-icons)
1. [Usa il selettore detto "Lobotomized Owl"](#use-the-lobotomized-owl-selector)
1. [Usa `max-height` per slider fatti solo con CSS](#use-max-height-for-pure-css-sliders)
1. [Celle di tabella con larghezza uguale](#equal-width-table-cells)
1. [Sbarazzati degli hack sui margini grazie a Flexbox](#get-rid-of-margin-hacks-with-flexbox)
1. [Usa il selettore d'attributo con i link senza testo](#use-attribute-selectors-with-empty-links)
1. [Styling dei link di "Default"](#style-default-links)
1. [Mantieni un ritmo verticale coerente](#consistent-vertical-rhythm)
1. [Box con proporzioni intrinseche](#intrinsic-ratio-boxes)
1. [Styling delle immagini non scaricate](#style-broken-images)
1. [Usa `rem` per le grandezze globali; usa `em` per le dimensioni locali](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [Nascondi i video in riproduzione automatica che non sono silenziati](#hide-autoplay-videos-that-arent-muted)
1. [Usa `:root` per caratteri flessibili](#use-root-for-flexible-type)
1. [Imposta il `font-size` sugli elementi dei form per una migliore esperienza da mobile](#set-font-size-on-form-elements-for-a-better-mobile-experience)


<div id="use-a-css-reset"></div>

### Utilizzare un reset CSS

reset CSS aiutare a far rispettare lo stile coerenza tra diversi browser da zero per gli elementi stilistici. È possibile utilizzare libreria di reset CSS come [Normalize](http://necolas.github.io/normalize.css/), et al, oppure è possibile utilizzare un approccio più semplificato di ripristino.:

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Ora elementi saranno spogliati di margini e padding, e `box-sizing` consente di gestire i layout con il box model CSS.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Nota:** Se si segue la punta [Eredita il `box-sizing`](#inherit-box-sizing) in basso si potrebbe optare di non includere la proprietà box-sizing nel ripristino CSS.

<sup>[torna al sommario](#sommario)</sup>


<div id="inherit-box-sizing"></div>

### Eredita il `box-sizing`

Eredita il `box-sizing` dall'elemento `html`:

```css
html {
  box-sizing: border-box;
}

*, *::before, *::after {
  box-sizing: inherit;
}
```

In questo modo diventa più facile cambiare `box-sizing` in plugin o altri componenti che ne sfruttano un altro.

<sup>[torna al sommario](#sommario)</sup>


<div id="use-not-to-applyunapply-borders-on-navigation"></div>

### Usa `:not()` per applicare/rimuovere i bordi su elementi di navigazione

Invece di impostare il bordo...

```css
/* aggiunge il bordo */
.nav li {
  border-right: 1px solid #666;
}
```

...e poi rimuoverlo dall'ultimo elemento...

```css
/* rimuove il bordo */
.nav li:last-child {
  border-right: none;
}
```

...usa la pseudo classe `:not()` per applicarlo solo agli elementi che vuoi:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Certo, puoi usare `.nav li + li` o anche `.nav li:first-child ~ li`, ma con `:not()` l'intento è molto chiaro e il selettore CSS definisce il bordo nel modo in cui un essere umano lo descriverebbe.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[torna al sommario](#sommario)</sup>


<div id="add-line-height-to-body"></div>

### Aggiungi `line-height` al `body`

You don't need to add `line-height` to each `<p>`, `<h*>`, _et al_. separately. Instead, add it to `body`:

```css
body {
  line-height: 1.5;
}
```

In questo modo gli elementi di testo possono ereditare facilmente da `body`.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[torna al sommario](#sommario)</sup>


<div id="vertically-center-anything"></div>

### Centra verticalmente qualsiasi cosa

No, non è magia nera. Puoi veramente centrare gli elementi verticalmente:

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

Vuoi centrare qualcos'altro? In verticale, in orizzontale... qualsiasi cosa, in qualsiasi momento ovunque? Su CSS-Tricks trovi [un ottimo articolo](https://css-tricks.com/centering-css-complete-guide/) a riguardo.

**Nota bene:** si verificano dei [comportamenti anomali](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) con flexbox e IE11.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[torna al sommario](#sommario)</sup>


<div id="comma-separated-lists"></div>

### Liste separate da virgola

Visualizza gli elementi di una lista come fossero una vera lista con le virgole:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Usa la pseudo classe `:not()` in modo da non aggiungere la virgola all'ultimo elemento.

**Nota bene:** può non essere l'ideale per garantire l'accessibilità, nello specifico per gli screen reader. Inoltre il copia/incolla dal browser non funziona con il contenuto generato mediante CSS. Procedi con attenzione.

<sup>[torna al sommario](#sommario)</sup>


<div id="select-items-using-negative-nth-child"></div>

### Seleziona un elemento usando gli `nth-child` negativi

Usa gli `nth-child` negativi di CSS per selezionare gli elementi da 1 a n.

```css
li {
  display: none;
}

/* seleziona gli elementi da 1 a 3 e li mostra */
li:nth-child(-n+3) {
  display: block;
}
```

Oppure, dato che hai già imparato un po' di cose circa l'[uso di `:not()`](#use-not-to-applyunapply-borders-on-navigation), prova:

```css
/* selezionare tutti gli elementi tranne i primi 3 e visualizzarli */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Beh... era abbastanza facile.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[torna al sommario](#sommario)</sup>


<div id="use-svg-for-icons"></div>

### Usa SVG per le icone

Non c'è ragione per non usare SVG per le icone:

```css
.logo {
  background: url("logo.svg");
}
```

SVG scala molto bene a tutti i tipi di risoluzione ed è supportata in tutti i browser [fino a IE9](http://caniuse.com/#search=svg). Perciò butta i tuoi file .png, .jpg o .gif-jif-qualsiasicosa.

**Nota bene:** se usi bottoni con esclusivamente grafica SVG e le icone SVG non vengono caricate, questo ti aiuterà a preservare l'accessibilità:

```css
.no-svg .icon-only:after {
  content: attr(aria-label);
}
```

<sup>[torna al sommario](#sommario)</sup>


<div id="use-the-lobotomized-owl-selector"></div>

### Usa il selettore detto "Lobotomized Owl"

Sebbene il suo nome sia un po' strano, l'uso del selettore universale (`*`) insieme al selettore del fratello adiacente (`+`) può fornire una potenzialità CSS molto potente:

```css
* + * {
  margin-top: 1.5em;
}
```

In questo esempio, tutti gli elementi nel flusso del documento che seguono altri elementi riceveranno la proprietà `margin-top: 1.5em`.

Per saperne di più sul selettore detto "lobotomized owl", leggi [l'articolo di Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) su *A List Apart*.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[torna al sommario](#sommario)</sup>


<div id="use-max-height-for-pure-css-sliders"></div>

### Usa `max-height` per slider fatti solo con CSS

Realizza slider fatti solo con CSS usando `max-height` con overflow hidden:

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

L'elemento si espande al valore `max-height` all'hover e lo slider diventa visibile come risultato dell'overflow.

<sup>[torna al sommario](#sommario)</sup>


<div id="equal-width-table-cells"></div>

### Celle di tabella con larghezza uguale

Lavorare con le tabelle può dare il tormento, perciò prova a usare `table-layout: fixed` per avere celle di larghezza uguale:

```css
.calendar {
  table-layout: fixed;
}
```

Layout con le tabelle e senza tormento.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[torna al sommario](#sommario)</sup>


<div id="get-rid-of-margin-hacks-with-flexbox"></div>

### Sbarazzati degli hack sui margini grazie a Flexbox

Quando lavori con gli spazi tra colonne puoi sbarazzarti di `nth-`, `first-` e `last-child` usando la proprietà `space-between` di flexbox:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Ora le colonne avranno sempre una spaziatura uniforme.

<sup>[torna al sommario](#sommario)</sup>


<div id="use-attribute-selectors-with-empty-links"></div>

### Usa il selettore d'attributo con i link senza testo

Quando l'elemento `<a>` non ha testo al suo interno ma l'attributo `href` ha un link, lo mostra:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Decisamente comodo.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[torna al sommario](#sommario)</sup>


<div id="style-default-links"></div>

### Styling dei link di "Default"

Aggiunge uno stile per i link "default":

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Ora i link inseriti mediante un CMS, che solitamente non hanno un attributo `class`, saranno distinti senza intaccare tutti gli altri in cascata.

<sup>[torna al sommario](#sommario)</sup>


<div id="consistent-vertical-rhythm"></div>

### Mantieni un ritmo verticale coerente

Fai uso di un selettore universale (`*`) all'interno di un elemento per creare un ritmo verticale coerente:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

Un ritmo verticale coerente procura un'estetica visuale che favorisce la leggibilità del conenuto.

<sup>[torna al sommario](#sommario)</sup>


<div id="intrinsic-ratio-boxes"></div>

### Box con proporzioni intrinseche

Per creare un contenitore con proporzioni intrinseche tutto ciò che devi fare è applicare  a un div del `padding` superiore o inferiore:

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

Uare un `padding` del 20% rende l'altezza del contenitore pari al 20% della sua larghezza. Non importa quale sia la larghezza della finestra, il div figlio manterrà le proporzioni stabilite (100% / 20% = 5:1).

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[torna al sommario](#sommario)</sup>


<div id="style-broken-images"></div>

### Styling delle immagini non scaricate

Rendi le immagini non scaricate più piacevoli esteticamente con un po' di CSS:

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

Ora aggiungi le regole per gli pseudo elementi al fine di mostrare un messaggio e un riferimento URL dell'immagine non scaricata:

```css
img:before {
  content: "Siamo spiacenti, l'immagine non è stata scaricata. :(";
  display: block;
  margin-bottom: 10px;
}

img:after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

Ulteriori informazioni sullo styling secondo questo pattern nell'[articolo](http://bitsofco.de/styling-broken-images/) di [Ire Aderinokun](https://github.com/ireade/).

<sup>[torna al sommario](#sommario)</sup>


<div id="use-rem-for-global-sizing-use-em-for-local-sizing"></div>

### Usa `rem` per le grandezze globali; usa `em` per le dimensioni locali

Dopo avere impostato la dimensione di base del font sull'elemento root (`html { font-size: 100%; }`), imposta la dimensione del font per gli elementi testuali con `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Poi imposta il font-size per i moduli con `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

A questo punto ogni modulo diventa compartimentalizzato, più facile da modellare, più manutenibile e più flessibile.

<sup>[torna al sommario](#sommario)</sup>


<div id="hide-autoplay-videos-that-arent-muted"></div>

### Nascondi i video in riproduzione automatica che non sono silenziati

Questo è un fantastico trucchetto per un foglio di stile personalizzato per un utente. Evita di sovraccaricare un utente col suono di un video che parte in riproduzione automatica quando la pagina viene caricata. Se il suono non è disabilitato non mostrare il video:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Ancora una volta stiamo sfruttando la pseudo classe [`:not()`](#use-not-to-applyunapply-borders-on-navigation).

<sup>[torna al sommario](#sommario)</sup>


<div id="use-root-for-flexible-type"></div>

### Usa `:root` per caratteri flessibili

In un layout responsive la grandezza del carattere dovrebbe essere in grado di adattarsi a ogni risoluzione. Puoi calcolare la dimensione del font basandoti sull'altezza e sulla larghezza della finestra usando `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Adesso puoi usare l'unità basata su `root em` sul valore calcolato da `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[torna al sommario](#sommario)</sup>


<div id="set-font-size-on-form-elements-for-a-better-mobile-experience"></div>

### Imposta il `font-size` sugli elementi dei form per una migliore esperienza da mobile

Per evitare lo zoom sugli elementi dei form dai browser mobile (iOS Safari, _et al_.) quando si tocca una `<select>`, aggiungi `font-size` alle regole del selettore:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[torna al sommario](#sommario)</sup>


## Supporto

Le attuali versioni di Chrome, Firefox, Safari, Opera, Edge ed IE11.

<sup>[torna al sommario](#sommario)</sup>


## Traduzioni

* [Español](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/es-ES)
* [Français](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/fr-FR)
* [Italiano](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/it-IT)
* [日本語](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ja-JP)
* [Português do Brasil](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-BR)
* [Русский](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ru-RU)
* [简体中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-CN)

<sup>[torna al sommario](#sommario)</sup>