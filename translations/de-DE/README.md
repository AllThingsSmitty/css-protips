<p align="center">
  <img src="../../assets/img/bulb.svg" width="200" alt="light bulb icon">
</p>

# CSS Profi-Tipps [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Eine Sammlung an Tipps, um deine CSS-Fähigkeiten zu professionalisieren.

> Für andere großartige Listen schaue dir [@sindresorhus](https://github.com/sindresorhus/)s kuratierte Liste von ["awesome" Listen](https://github.com/sindresorhus/awesome/) an.


## Inhaltsverzeichnis

* [Profi-Tipps](#profi-tipps)
* [Unterstützung](#unterstützung)
* [Mitarbeitsrichtlinien](../../CONTRIBUTING.md)


## Profi-Tipps

1. [Benutze ein CSS-Reset](#benutze-ein-css-reset)
1. [Übernehme `box-sizing`](#Übernehme-box-sizing)
1. [Benutze `unset`, anstatt alle Eigenschaften zurückzusetzen](#benutze-unset-anstatt-alle-eigenschaften-zurückzusetzen)
1. [Benutze `:not()` um Rahmen an die Navigation zu setzen oder zu entfernen](#benutze-not-um-rahmen-an-die-navigation-zu-setzen-oder-zu-entfernen)
1. [Kontroller, om skrifttypen er installeret lokalt](#Kontroller-om-skrifttypen-er-installeret-lokalt)
1. [Ergänze `line-height` an `body`](#ergänze-line-height-an-body)
1. [Setze `:focus` für Form-Elemente](#setze-focus-für-form-elemente)
1. [Zentriere alles vertikal](#zentriere-alles-vertikal)
1. [Kommaseparierte Liste](#kommaseparierte-liste)
1. [Selektiere Items mit einem negativen `nth-child`](#selektiere-items-mit-einem-negativen-nth-child)
1. [Benutze SVG für Symbole](#benutze-svg-für-symbole)
1. [Benutze den "lobotomisierte Eule"-Selektor](#benutze-den-lobotomisierte-eule-selektor)
1. [Benutze `max-height` für reine CSS-Galerien](#benutze-max-height-für-reine-css-galerien)
1. [Setze Tabellenzellen auf die gleiche Weite](#setze-tabellenzellen-auf-die-gleiche-weite)
1. [Benutze Flexbox, um von Margin-Hacks wegzukommen](#benutze-flexbox-um-von-margin-hacks-wegzukommen)
1. [Benutze den Attribut-Selektor mit leeren Verlinkungen](#benutze-den-attribut-selektor-mit-leeren-verlinkungen)
1. [Gestalte "Standard"-Verlinkungen](#gestalte-standard-verlinkungen)
1. [Boxen mit zugehörigem Größenverhältnis](#boxen-mit-zugehörigem-größenverhältnis)
1. [Gestalte defekte Bilder](#gestalte-defekte-bilder)
1. [Benutze `rem` für globales Ändern der Größe; Benutze `em` für lokale Größenveränderungen](#benutze-rem-für-globales-Ändern-der-größe-benutze-em-für-lokale-größenveränderungen)
1. [Verstecke automatisch abspielende Videos, die nicht auf stumm gesetzt sind](#verstecke-automatisch-abspielende-videos-die-nicht-auf-stumm-gesetzt-sind)
1. [Benutze `:root` für flexible Schrift](#benutze-root-für-flexible-schrift)
1. [Setze `font-size` auf Formular-Elemente für eine bessere mobile Erfahrung](#setze-font-size-auf-formular-elemente-für-eine-bessere-mobile-erfahrung)
1. [Benutze `Pointer`-Events um Mausereignisse zu kontrollieren](#benutze-pointer-events-um-mausereignisse-zu-kontrollieren)
1. [Stellen Sie bei Zeilenumbrüchen, die als Abstand verwendet werden, `display: none` ein](#stellen-sie-bei-zeilenumbrüchen,-die-als-abstand-verwendet-werden-display-none-ein)


### Benutze ein CSS-Reset

CSS Resets helfen dabei eine Gestaltungskonsistenz zwischen verschiedenen Browsern herzustellen, indem sie für einen sauberen Zustand zwischen den einzelnen Elementen sorgen. Du kannst eine CSS Resetsammlung wie [Normalize](http://necolas.github.io/normalize.css/), usw. benutzen, oder einen etwas einfacheren Ansatz wählen:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Nun werden Elemente von ihren Margins und Paddings befreit und `box-sizing` lässt dich das CSS Box-Modell handhaben.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Hinweis:** Wenn du den [Inherit `box-sizing`](#inherit-box-sizing)-Tipp im unten folgenden Punkt befolgst, kannst du dich dafür entscheiden keine `box-sizing`-Eigenschaft in dein CSS Reset aufzunehmen.

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Übernehme `box-sizing`

Übernehme `box-sizing` von `html`:

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

Dies macht es einfacher das `box-sizing` über Plugins oder andere Komponenten zu verändern.

#### [Demo](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Benutze `unset`, anstatt alle Eigenschaften zurückzusetzen

Wenn du die Eigenschaften eines Elements zurücksetzt, ist es nicht notwendig jede einzelne Eigenschaft individuell zurückzusetzen:

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

Du kannst alle Eigenschaften eines Elements spezifizieren, indem du das `all`-Kürzel verwendest. Der Wert `unset` setzt die Eigenschaften eines Elements auf den initialen Wert zurück:

```css
button {
  all: unset;
}
```

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Benutze `:not()` um Rahmen an die Navigation zu setzen oder zu entfernen

Anstatt den Rahmen zu ergänzen&hellip;

```css
/* füge den Rahmen hinzu */
.nav li {
  border-right: 1px solid #666;
}
```

&hellip;um ihn dann beim letzten Element wieder zu entfernen&hellip;

```css
/* entferne den Rahmen */
.nav li:last-child {
  border-right: none;
}
```

&hellip;benutze die `:not()`-Pseudoklasse um nur die Elemente zu gestalten, die du willst:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Sicher, du kannst `.nav li + li` verwenden, aber mit `:not()` ist die Absicht sehr klar und der CSS Selektor definiert den Rahmen auf die Weise wie ihn auch ein Mensch beschreiben würde.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Check If Font Is Installed Locally](#check-if-font-is-installed-locally)

### Kontroller, om skrifttypen er installeret lokalt

Du kan kontrollere, om en skrifttype er installeret lokalt, før du henter den eksternt, hvilket også er et godt ydelsestip.

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

Hat tip til Adam Argyle for at dele denne protip og [demoen](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Ergänze `line-height` an `body`

Du brauchst kein `line-height` an jedes `<p>`, `<h*>`, usw separat zu schreiben. Ergänze es stattdessen an `body`:

```css
body {
  line-height: 1.5;
}
```

Auf diese Weise können Textelemente dies einfach von `body` übernehmen.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Setze `:focus` für Form-Elemente

Sehende Tastaturbenutzer_innen sind auf die Fokussierung angewiesen, um unterscheiden zu können wohin Tastaturevents auf der Seite gehen. Gestalte den Fokus für Formular-Elemente klar ersichtlich und konsistenter als die voreingestellte Browserimplementation:

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

#### [Demo](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Zentriere alles vertikal

Nein, das ist keine Hexerei &ndash; du kannst wirklich alle Elemente vertikal zentrieren. 
Das machst du mit Flexbox&hellip;

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

&hellip;und ebenso mit CSS Grid:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

Möchtest du etwas anderes zentrieren? Vertikal, horizontal&hellip; alles, jederzeit, überall? CSS-Tricks hat [eine schöne Ausarbeitung](https://css-tricks.com/centering-css-complete-guide/) über all dies.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Kommaseparierte Liste

Lasse Listenpunkte wie eine echte kommaseparierte Liste aussehen:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Benutze die `:not()`-Pseudoklasse, um nach dem letzten Listenpunkt kein Komma anzuzeigen.

**Hinweis:** Dieser Tipp mag hinsichtlich der Zugänglichkeit für Bildschirmvorleseprogramme nicht ideal sein. Auch Kopieren/Einfügen von browsergeneriertem Inhalt funktioniert nicht. Handle deswegen mit Vorsicht.

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Selektiere Items mit einem negativen `nth-child`

Benutze ein negatives `nth-child` im CSS um Items von 1 bis n auszuwählen.

```css
li {
  display: none;
}

/* wähle die Listenpunkte 1 bis 3 und zeige sie an */
li:nth-child(-n+3) {
  display: block;
}
```

Anderweitig, da du nun ein bisschen über die [Benutzung von `:not()`](#benutze-not-um-rahmen-an-die-navigation-zu-setzen-oder-zu-entfernen) gelernt hast, versuche folgendes:

```css
/* wähle alle Listenpunkte außer die ersten 3 und zeige sie an */
li:not(:nth-child(-n+3)) {
  display: block;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Benutze SVG für Symbole

Es gibt keinen Grund SVG für Symbole nicht zu verwenden:

```css
.logo {
  background: url("logo.svg");
}
```

SVG skaliert für alle verschiedenen Auflösungen sehr gut und wird von allen Browsern [zurück bis zu IE9](http://caniuse.com/#search=svg) unterstützt. Gebe deinen .png, .jpg, or .gif-jif-wasauchimmer-Dateien den Laufpass.

**Hinweis:** Wenn du nur SVG-Symbole in Button-Schaltflächen für sehende Benutzer_innen verwendest und das SVG nicht geladen wird, kannst du die Zugänglichkeit wie folgt erhalten:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Benutze den "lobotomisierte Eule"-Selektor

Er hat zwar einen seltsamen Namen aber der Universal-Selektor (`*`) mit dem angrenzenden Geschwister-Selektor (`+`) kann starke CSS-Möglichkeiten darbieten:

```css
* + * {
  margin-top: 1.5em;
}
```

In diesem Beispiel bekommen alle Elemente im Fluss des Dokuments, die anderen Elementen folgen, `margin-top: 1.5em`.

Für mehr bezüglich des "lobotomisierte Eule"-Selektors lese [Heydon Pickerings Eintrag](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) auf *A List Apart*.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Benutze `max-height` für reine CSS-Galerien

Implementiere reine CSS Galerien über `max-height` in Verbindung mit `overflow: hidden`:

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

Das Element dehnt sich beim Überfahren zum Wert von `max-height` aus und die Galerie wird als das Ergebnis des Overflows dargestellt.

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Setze Tabellenzellen auf die gleiche Weite

Tabellen können ein ganz schönes Problem sein. Versuche `table-layout: fixed`, um die Tabellenzellen auf die gleiche Größe zu setzen:

```css
.calendar {
  table-layout: fixed;
}
```

Schmerzfreie Tabellen-Layouts.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Benutze Flexbox, um von Margin-Hacks wegzukommen

Wenn du mit Spaltenabständen arbeitest, kannst du dich von `nth-`, `first-` und `last-child`-Hacks verabschieden, indem du die Flexbox-Eigenschaft `space-between` verwendest:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Nun erscheinen Spaltenabstände immer gleichmäßig.

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Benutze den Attribut-Selektor mit leeren Verlinkungen

Zeige Verlinkungen an, wenn das `<a>`-Element keinen Textwert beinhaltet, das `href`-Attribut jedoch eine Verlinkung hat:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Das ist äußerst praktisch.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Gestalte "Standard"-Verlinkungen

Ergänze eine Darstellung für die von Browsern voreingestellte Verlinkung:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Nun werden Verlinkungen, die über ein CMS eingesetzt wurden &ndash; welche überlicherweise kein `class`-Attribut haben &ndash; unterscheidbar sein, ohne die Kaskade im Allgemeinen zu beeinflussen.

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Boxen mit zugehörigem Größenverhältnis

Um eine Box mit zugehörigem Größenverhältnis zu erstellen, brauchst du nur eine Padding-top/-bottom-Eigenschaft zu bezeichnen:

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

Das Anwenden eines Wertes von 20% auf die Padding-Eigenschaft erzeugt eine Box mit der gleichen Höhe in Bezug auf 20% ihrer Breite. Ungeachtet der Weite des Ansichtsfensters, wird das Kind-Div sein Seitenverhältnis beibehalten (100% / 20% = 5:1).

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Gestalte defekte Bilder

Erzeuge mit einem kleinen bisschen CSS ästhetisch ansprechendere defekte Bilder:

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

Nun ergänze Regeln für Pseudo-Elemente, die eine Nachricht für die Benutzer_innen darstellen, sowie eine URL-Referenz des defekten Bildes:

```css
img::before {
  content: "Entschuldige bitte, das Bild ist leider defekt :(";
  display: block;
  margin-bottom: 10px;
}

img::after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

Lerne mehr über das Gestalten dieses Modells in [Ire Aderinokun](https://github.com/ireade/)s [ursprünglichen Beitrag](http://bitsofco.de/styling-broken-images/).

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Benutze `rem` für globales Ändern der Größe; Benutze `em` für lokale Größenveränderungen

Nachdem du die grundlegende Schriftgröße (`html { font-size: 100%; }`) festgelegt hast, setze die Schriftgrößen für Textelemente auf `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Dann setze die Schriftgröße für Module auf `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Nun sollte jedes Modul gegliedert, einfacher zu gestalten, wartbarer und flexibler sein.

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Verstecke automatisch abspielende Videos, die nicht auf stumm gesetzt sind

Das ist ein großartiger Trick für ein speziell angefertigtes Stylesheet. Vermeide es die Benutzer_innen mit den Geräuschen eines automatisch startenden Videos zu überfordern. Zeige das Video nicht, wenn die Töne nicht auf stumm geschaltet sind:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Erneut nutzen wir die [`:not()`](#benutze-not-um-rahmen-an-die-navigation-zu-setzen-oder-zu-entfernen)-Pseudoklasse zu unserem Vorteil.

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Benutze `:root` für flexible Schrift

Die Größe der Schriftart innerhalb eines _responsive_ Layouts sollte mit jedem Ansichtsfenster veränderbar sein. Du kannst die Schriftgröße basierend auf der Höhe und Weite des Fensters berechnen, indem du `:root` verwendest: 

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Nun kannst du die `root em`-Einheit verwenden, die auf den errechneten Werten von `:root` basiert:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Setze `font-size` auf Formular-Elemente für eine bessere mobile Erfahrung

Um mobile Browser (iOS Safari, usw.) am Hereinzoomen in das HTML-Formular zu hindern sobald ein `<select>`-Dropdown betätigt wird, ergänze `font-size` zu der Regel des Selektors:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Benutze `Pointer`-Events um Mausereignisse zu kontrollieren

[Pointer-Events](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) erlauben es dir zu spezifizieren wie die Maus mit dem Element interagiert sobald sie es berührt. Um beispielsweise das standardgemäß eingestellte Pointer-Event &ndash; beispielsweise bei einer Button-Schaltfläche &ndash; abzuschalten:

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

So einfach ist das.

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


### Stellen Sie bei Zeilenumbrüchen, die als Abstand verwendet werden, `display: none` ein

Wie [Harry Roberts hervorhob](https://twitter.com/csswizardry/status/1170835532584235008), kann dies dazu beitragen, dass CMS-Benutzer keine zusätzlichen Zeilenumbrüche als Abstand verwenden:

```css
br + br {
  display: none;
}
```

<sup>[zurück zum Inhaltsverzeichnis](#inhaltsverzeichnis)</sup>


## Unterstützung

Aktuelle Versionen von Chrome, Firefox, Safari, und Edge.