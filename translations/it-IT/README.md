<p align="center">
  <img src="../../assets/img/bulb.svg" alt="light bulb icon">
</p>

# CSS suggerimenti per esperti [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Una collezione di dritte per aiutarti a migliorare le tue capacità con CSS.

> Per altre fantastiche liste di questo tipo guarda la [lista di fantastiche liste](https://github.com/sindresorhus/awesome/) curata da [@sindresorhus](https://github.com/sindresorhus/).


## Sommario

* [Suggerimenti per esperti](#suggerimenti-per-esperti)
* [Supporto](#supporto)
* [Linee guida per contribuire](../../CONTRIBUTING.md)


## Suggerimenti per esperti

1. [Utilizzare un reset CSS](#utilizzare-un-reset-css)
1. [Eredita il `box-sizing`](#eredita-il-box-sizing)
1. [Usa `unset` invece di Reimposta tutte le proprietà](#usa-unset-invece-di-reimposta-tutte-le-proprietà)
1. [Usa `:not()` per applicare/rimuovere-i-bordi-su-elementi-di-navigazione](#usa-not-per-applicarerimuovere-i-bordi-su-elementi-di-navigazione)
1. [Controlla se il font è installato localmente](#controlla-se-il-font-è-installato-localmente)
1. [Aggiungi `line-height` al `body`](#aggiungi-line-height-al-body)
1. [Imposta `:focus` per gli elementi del modulo](#imposta-focus-per-gli-elementi-del-modulo)
1. [Centra verticalmente qualsiasi cosa](#centra-verticalmente-qualsiasi-cosa)
1. [Liste separate da virgola](#liste-separate-da-virgola)
1. [Seleziona un elemento usando gli `nth-child` negativi](#seleziona-un-elemento-usando-gli-nth-child-negativi)
1. [Usa SVG per le icone](#usa-svg-per-le-icone)
1. [Usa il selettore detto "Lobotomized Owl"](#usa-il-selettore-detto-"lobotomized-owl")
1. [Usa `max-height` per slider fatti solo con CSS](#usa-max-height-per-slider-fatti-solo-con-css)
1. [Celle di tabella con larghezza uguale](#celle-di-tabella-con-larghezza-uguale)
1. [Sbarazzati degli hack sui margini grazie a Flexbox](#sbarazzati-degli-hack-sui-margini-grazie-a-flexbox)
1. [Usa il selettore d'attributo con i link senza testo](#usa-il-selettore-d'attributo-con-i-link-senza-testo)
1. [Styling dei link di "Default"](#styling-dei-link-di-"default")
1. [Box con proporzioni intrinseche](#box-con-proporzioni-intrinseche)
1. [Styling delle immagini non scaricate](#styling-delle-immagini-non-scaricate)
1. [Usa `rem` per le grandezze globali; usa `em` per le dimensioni locali](#usa-rem-per-le-grandezze-globali;-usa-em-per-le-dimensioni-locali)
1. [Nascondi i video in riproduzione automatica che non sono silenziati](#nascondi-i-video-in-riproduzione-automatica-che-non-sono-silenziati)
1. [Usa `:root` per caratteri flessibili](#usa-:root-per-caratteri-flessibili)
1. [Imposta il `font-size` sugli elementi dei form per una migliore esperienza da mobile](#imposta-il-font-size-sugli-elementi-dei-form-per-una-migliore-esperienza-da-mobile)
1. [Utilizzare gli eventi puntatore per controllare gli eventi del mouse](#utilizzare-gli-eventi-puntatore-per-controllare-gli-eventi-del-mouse)
1. [Imposta `display: none` su Line Breaks usati come Spaziatura](#imposta-display:-none-su-line-breaks-usati-come-spaziatura)


### Utilizzare un reset CSS

reset CSS aiutare a far rispettare lo stile coerenza tra diversi browser da zero per gli elementi stilistici. È possibile utilizzare libreria di reset CSS come [Normalize](http://necolas.github.io/normalize.css/), et al, oppure è possibile utilizzare un approccio più semplificato di ripristino.:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Ora elementi saranno spogliati di margini e padding, e `box-sizing` consente di gestire i layout con il box model CSS.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Nota:** Se si segue la punta [Eredita il `box-sizing`](#inherit-box-sizing) in basso si potrebbe optare di non includere la proprietà box-sizing nel ripristino CSS.

<sup>[torna al sommario](#sommario)</sup>


### Eredita il `box-sizing`

Eredita il `box-sizing` dall'elemento `html`:

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

In questo modo diventa più facile cambiare `box-sizing` in plugin o altri componenti che ne sfruttano un altro.

#### [Dimostrazione](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[torna al sommario](#sommario)</sup>


### Usa `unset` invece di Reimposta tutte le proprietà

Quando si ripristinano le proprietà di un elemento, non è necessario reimpostare ogni singola proprietà:

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

Puoi specificare tutte le proprietà di un elemento usando la stenografia `all`. L'impostazione del valore su `unset` modifica le proprietà di un elemento ai valori iniziali:

```css
button {
  all: unset;
}
```

<sup>[torna al sommario](#sommario)</sup>


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

Il selettore CSS definisce il confine nel modo in cui un essere umano lo descrive.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[torna al sommario](#sommario)</sup>


### Controlla se il font è installato localmente

Puoi verificare se un font è installato localmente prima di recuperarlo da remoto, il che è anche un buon suggerimento per le prestazioni.

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

Punta del cappello ad Adam Argyle per aver condiviso questo prototipo e questa [dimostrazione](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[torna al sommario](#sommario)</sup>


### Aggiungi `line-height` al `body`

Non è necessario aggiungere `line-height` a ogni `<p> `,`<h *>`, _et al_. separatamente. Invece, aggiungilo a `body`:


```css
body {
  line-height: 1.5;
}
```

In questo modo gli elementi di testo possono ereditare facilmente da `body`.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[torna al sommario](#sommario)</sup>


### Imposta `:focus` per gli elementi del modulo

Gli utenti con tastiera a vista si affidano alla messa a fuoco per determinare dove vanno gli eventi della tastiera nella pagina. Fai attenzione agli elementi del modulo che si distinguono e coerenti rispetto all'implementazione predefinita del browser:

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

#### [Dimostrazione](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[torna al sommario](#sommario)</sup>


### Centra verticalmente qualsiasi cosa

No, non è magia nera. Puoi veramente centrare gli elementi verticalmente:

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

...e anche con CSS Grid:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

Vuoi centrare qualcos'altro? In verticale, in orizzontale... qualsiasi cosa, in qualsiasi momento ovunque? Su CSS-Tricks trovi [un ottimo articolo](https://css-tricks.com/centering-css-complete-guide/) a riguardo.

#### [Dimostrazione](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[torna al sommario](#sommario)</sup>


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
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[torna al sommario](#sommario)</sup>


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


### Styling delle immagini non scaricate

Rendi le immagini non scaricate più piacevoli esteticamente con un po' di CSS:

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

Ora aggiungi le regole per gli pseudo elementi al fine di mostrare un messaggio e un riferimento URL dell'immagine non scaricata:

```css
img::before {
  content: "Siamo spiacenti, l'immagine non è stata scaricata. :(";
  display: block;
  margin-bottom: 10px;
}

img::after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

Ulteriori informazioni sullo styling secondo questo pattern nell'[articolo](http://bitsofco.de/styling-broken-images/) di [Ire Aderinokun](https://github.com/ireade/).

<sup>[torna al sommario](#sommario)</sup>


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


### Nascondi i video in riproduzione automatica che non sono silenziati

Questo è un fantastico trucchetto per un foglio di stile personalizzato per un utente. Evita di sovraccaricare un utente col suono di un video che parte in riproduzione automatica quando la pagina viene caricata. Se il suono non è disabilitato non mostrare il video:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Ancora una volta stiamo sfruttando la pseudo classe [`:not()`](#use-not-to-applyunapply-borders-on-navigation).

<sup>[torna al sommario](#sommario)</sup>


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


### Utilizzare gli eventi puntatore per controllare gli eventi del mouse

[Eventi puntatore](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) consentono di specificare come il mouse interagisce con l'elemento che sta toccando. Per disabilitare l'evento puntatore predefinito su un pulsante, ad esempio:

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

È così semplice.

<sup>[torna al sommario](#sommario)</sup>


### Imposta `display: none` su Line Breaks usati come Spaziatura

Come [Harry Roberts ha sottolineato](https://twitter.com/csswizardry/status/1170835532584235008), questo può aiutare a impedire agli utenti CMS di utilizzare interruzioni di riga aggiuntive per la spaziatura:

```css
br + br {
  display: none;
}
```

<sup>[torna al sommario](#sommario)</sup>


## Supporto

Le attuali versioni di Chrome, Firefox, Safari, ed Edge.