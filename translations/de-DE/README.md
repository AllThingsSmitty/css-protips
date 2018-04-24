<p align="center">
<img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" width="200" alt="lampensymbol">
</p>

# CSS Pro Tips [![Super](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)


Eine Sammlung von Tipps, mit denen Your CSS-Kenntnisse verbessern können.

> Für andere tolle prüfen Hören Sie heraus [@sindresorhus](https://github.com/sindresorhus/)'s kuratiert Liste der Listen [Super](https://github.com/sindresorhus/awesome/).


## Inhaltsverzeichnis

* [Pro Tips](#Pro Tips)
* [Support](#Support)
* [Beitrag Leitlinien](../../CONTRIBUTING.md)


## Pro Tips

1. [Verwenden Sie einen CSS-Reset](#use-a-css-Reset)
1. [Erben' Box-sizing"](#Erben-box-Sizing)
1. [Benutzen': nicht bewerben () '/Entfernen Sie sterben Rahmen für sterben Navigation] (# verwenden-nicht-anwenden-anwenden-Grenzen-bei-Navigation)
1. [Füge 'line-height' zu 'Körper' hinzu] (#hinzufügen - Linie-Höhe-zu-Karosserie)
1. [Vertikal-Center Etwas] (#vertikal-Zentrum-etwas)
1. [Kommagetrennte Listen] (#comma-separated-Listen)
1. [Wählen Sie Elemente mit negativen "nth-child'] (#wählen - Einzelteile - Verwendung - negative - n-Kind)
1. [ SVG für Icons] (#verwenden - SVG-Icons)
1. [Verwenden Sie die "Lobotomisiert Eule "Selector] (#verwenden - Der-Lobotomisiert - Owl-Selector)
1. [Verwenden Sie die 'Max-height' für reine CSS-Regler] (#-max-height-für-rein-css-Schieberegler)
1. [Equal-Width Tabellenzellen] (#Höhe - Breite - Tabelle-Zellen)
1. [Loswerden Marge Hacks mit Flexbox] (#get-rid-of-margin-Hacks-mit-Flexbox)
1. [Verwenden Sie die Attribut Selektoren mit leeren Links] (#-Attribut-Selektoren-mit-leer-links)
1. [Style "Default"-Links] (#Style-default-links)
1. [Konsistente vertikale Rhythmus] (#konsequent - Vertikal - Rhythmus)
1. [Inneren Verhältnis Boxen] (#Intrinsic-Ratio-Boxen)
1. [Style gebrochen Bilder] (#Style - gebrochen - Bilder)
1. [Verwenden Sie 'rem' für globale Größe; verwenden Sie 'em' für Lokale Sizing] (#verwenden - Rem-für-global-sizing-verwenden-em-für-local-Sizing)
1. [Ausblenden Automatische Wiedergabe von Videos, die nicht stummgeschaltet sind.] (#verstecken - autoplay - Videos -, dass arent Stummgeschalteten)
1. [Verwendung": root' für Flexible Type] (#use-root-für-flexible-Typ)
1. [Set 'font-size' auf dem Formular Elemente für eine bessere mobile Erfahrung] (#set-font-size-auf-form-Elemente-für-ein-besser-mobile-Erfahrung)


### Verwenden eines CSS-Reset

CSS setzt Hilfe erzwingen Stil Konsistenz über verschiedene Browser mit einem sauberen Schiefer für Stilelemente. Sie können ein CSS-reset Bibliothek wie [Normalisieren] (Http://necolas.github.io/normalize.css/),_et al_, oder Sie können eine vereinfachte reset Ansatz verwenden:

```css
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Jetzt Elemente wird entfernt der Seitenränder und Textabstand und 'box-sizing" können Sie Layouts mit Css Box Model zu verwalten.

#### [Demo] (http://codepen.io/AllThingsSmitty/pen/kkrkLL)

** Hinweis: ** Wenn Sie die [Erben" folgen - grössensortierung"] (#Erben-box-Sizing) Tipp unten entscheiden Sie sich möglicherweise nicht die "box-sizing" Eigenschaft in Ihrem CSS-Reset.

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Erben' Box-sizing '

Lassen' Box-sizing" von "vererbt werden html':

'''css
html-
box-sizing: border-box;
}

*,*::*:: Nach {
box-sizing: erben;
}
'''

Das macht es leichter zu ändern' Box-sizing" in Plugins oder andere Komponenten, nutzen andere Verhalten.

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Verwenden': (Nicht) Anwenden/Unapply grenzt an Navigation

anstatt an der Grenze...

'''Css
/* Grenze */
. nav Li {
border-right:1px Solid #666;
}
'''

... und dann nehmen Sie das letzte Element...

'''Css
/* entfernen Sie Grenze */
. nav Li: Letztes - Kind {
border-right:none;
}
'''

... Die": (Nicht) 'Pseudo-Klasse nur für die Elemente, die Sie anwenden möchten:

'''css
. nav Li: (Nicht: Letztes - Kind) {
border-right:1px Solid #666;
}
'''

Sicher, können Sie mit der Option '. nav Li + li' oder sogar '. nav Li:first-child~li', aber mit ': (Nicht) "Die Absicht ist klar und die CSS-Selektor definiert die Grenze die Art und Weise, wie ein Mensch es beschreiben würde.

#### [Demo] (http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


###Add 'line-height', 'Körper', die

Sie nicht hinzufügen müssen, 'line-height', '<p>','<h*>', _et al_. getrennt. Stattdessen fügen Sie sie zu 'Körper':

'''css
Body {
line-height: 1.5;
}
''' auf

diese Weise textuelle Elemente erben können von 'Körper'.

#### [Demo] (http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Vertically-Center Alles,

nein, es ist keine schwarze Magie, Sie können wirklich Zentrum Elemente vertikal:

'''css
html, body {
Height: 100%;
margin: 0;
}

Body{
- webkit-Ausrichten-Reihen: Zentrum;
- ms-flex-align: center;
Ausrichten - Produkte: center;
Display: - webkit-Flex;
Anzeige: Flex;
}
'''

Wollen in die Mitte etwas anderes? Vertikal, Horizontal... alles, jederzeit, überall? CSS-Tricks hat [ein nettes Schreiben] (Https://css-tricks.com/centering-css-complete-guide/) auf all das tun.

** Hinweis: ** Achten Sie auf einige [buggy Verhalten] (Https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) mit der Flex-box in IE 11.

#### [Demo] (http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### kommagetrennte Listen

Liste Elemente wie ein echter, Komma-getrennte Liste Aussehen:

'''Css
Ul > li: (Nicht: Letztes - Kind):: Nach {
content:", ";
}
'''

verwenden, um die': (Nicht) 'Pseudo-Klasse so kein Komma auf das letzte Element hinzugefügt wird.

**Hinweis**: Dieser Tipp ist vielleicht nicht ideal für Zugänglichkeit, speziell Screen Reader. Und copy/paste aus dem Browser nicht mit CSS-generierten Inhalten. Mit Vorsicht vorgehen.

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### wählen Sie Elemente mit negativen "nth-child '

negative' nth-child" in CSS zu wählen Sie die Elemente 1 bis n.

'''Css
li {
display:none;
}

/* wählen Sie die Optionen 1 bis 3 und Anzeige*/
li: nth-child (-n+3) {
Display: Block;
}
'''

oder, da Sie bereits gelernt haben, ein wenig über [Verwendung': (Nicht)'] (#-nicht-zu-applyunapply-Grenzen-auf-navigation), versuchen Sie:

'''css
/* Alle Elemente außer den ersten 3 und angezeigt werden */
li: (Nicht: nth-child (-n+3)) {
display:none;
}
'''

Gut, die recht einfach war.

#### [Demo] (http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### SVG für Icons verwenden,

es gibt keinen Grund, nicht SVG für Symbole zu verwenden:

'''css
. Logo {
Background: url("logo.svg");
}
'''

SVG-Skalen sowie für alle Auflösung und ist in allen Browsern [zurück zu IE 9] (Http://caniuse.com/#search=svg). unterstützt. So graben Sie Ihre .png, .jpg oder .gif - jif-whatev Dateien.

**Hinweis**: Wenn Sie SVG-Symbol - nur Tasten für sehende Benutzer und der SVG nicht geladen wird, wird diese Hilfe Zugänglichkeit:

'''css
. Nein - svg. Symbol - nur: Nach {
Inhalt: Attr (aria-Label);
}
'''

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Die "Lobotomisiert Eule "Selector

es eine seltsame Namen haben kann, aber mit dem universellen Selektor ("*") mit den dazugehörigen gleichgeordneten Selektor ("+") kann ein leistungsfähiges CSS-Funktionen:

'''css
*+*{
margin-top: 1.5Em;
}
'''

In diesem Beispiel werden alle Elemente in der Strömung der Dokument, folgen die anderen Elemente erhalten bin 'margin-top:1.5em' bieten.

Für weitere Informationen über die "Lobotomisiert Eule "Selector, lesen [ Heydon Pickering's Post] (Http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) auf * eine Liste abgesehen*.

#### [Demo] (http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Verwenden Sie 'max-height' für reine CSS-Schieberegler

implementieren CSS-Slider mit 'max-height' mit Überlauf versteckt:

'''css
. Schieberegler {
max-height: 200px;
overflow-y:hidden;
width: 300px;
}

. Regler:hover {
max-height: 600px;
overflow-y: scroll;
}
'''

das Element auf die 'Max-height' Wert auf schweben und der Schieberegler zeigt als Ergebnis der Überlauf wird erweitert.

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Equal-Width Zellen der Tabelle

Tabellen ein Schmerz sein können, so versuchen Sie es mit 'table-layout: Fixed' Zellen bei gleicher Breite zu halten:

'''css
. Kalender {
table-layout:fixed;
}
'''

Schmerz- tabelle Layouts.

#### [Demo] (http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Loswerden Marge Hacks mit Flexbox

beim Arbeiten mit Spalte Dachrinnen erhalten Sie loszuwerden' n-te-', '-', und 'last-child" Hacks mit Hilfe der Flex-box Tempo - zwischen "Eigentum:

'''css
. Liste {
Display: Flex;
rechtfertigen - Inhalt: Raum - Zwischen;
}

. Liste. Person{
flex-Basis: 23%;
}
'''

Jetzt Spalte Dachrinnen erscheinen immer gleichmäßig verteilte.

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Verwenden Sie das Attribut Selektoren mit leeren Links

Anzeigen links Wenn die '<a>-Element hat kein Text wert aber das 'href' Attribut hat einen Link:

'''css-
a[href^="http"]: Leer:: Vor dem {
content: attr(href);
}
'''

Das ist ziemlich praktisch.

#### [Demo] (http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Style "Default" Links

ein Stil für "default" links hinzufügen:

'''css-
a[href]: Nicht ([Klasse]){
color:#008000;
text-decoration: underline;
}
'''

Jetzt links, die über ein CMS, das nicht normalerweise ein "class"-Attribut eingefügt sind, wird eine Unterscheidung ohne generisch, die die Kaskade.

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### konsistente vertikale Rhythmus

mit einem universellen Selektor ('*') innerhalb eines Elements eine konsistente vertikale Rhythmus zu erstellen:

''' css
. intro > * {
margin-bottom: 1,25 rem;
}
'''

konsistente vertikale Rhythmus bietet eine visuelle Ästhetik, die Macht Inhalt weit mehr lesbar.

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### intrinsische Verhältnis Boxen

eine Box mit einem inneren Verhältnis zu erstellen, müssen Sie nur die obere oder untere Polsterung um ein div gelten:

'''css-
Container {
height:0;
padding-bottom:20%;
position:relative;
}

. div-Container {
border: 2px gestrichelte #ddd;
Height: 100%;
Left: 0;
Position: absolute;
top: 0;
width: 100%;
}
'''

mit 20 % für die Polsterung macht die Höhe des Feldes in Höhe von 20 % der Breite. Egal, die Breite des Bildbereichs, dem Kind div wird das Seitenverhältnis (100% / 20% = 5:1) halten.

#### [Demo] (http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Stil gebrochen Bilder

machen kaputt Bilder mehr ästhetisch ansprechend mit ein wenig CSS:

'''css
img {
Display: Block;
font-family:Helvetica, Arial, sans-serif;
font-weight:300;
height: auto;
line-height: 2;
Position: relative;
text-align: center;
width: 100%;
}
'''

Jetzt pseudo-elemente Regeln hinzufügen eine Meldung für den Benutzer und URL-Referenz des gebrochenen Bild anzuzeigen:

'''css
img::Vor dem {
content: "Es tut uns Leid, das Bild unten gebrochen ist: (";
Display: Block;
margin-bottom: 10px;
}

img:: Nach {
content: "url: " attr (Src)")";
Display: Block;
font-size: 12px;
}
'''

erfahren Sie mehr über Styling für dieses Muster in [Ire (https://github.com/ireade/)'s Aderinokun] [Original post] (http://bitsofco.de/styling-broken-images/).

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Verwenden Sie m'für Globale Größe; verwenden Sie 'em' für Lokale Dimensionierung

nach Einstellung der Schriftgröße an der Wurzel ('html {font-size: 100%; }"), stellen Sie die Schriftgröße für textuelle Elemente zu 'em':

'''css
h2 {
font-size: 2em;
}

p {
font-size:1em;
}
''',

dann die font-size für Module zu 'rem':

''' css-
Artikel {
font-size: 1,25 rem;
}

beiseite. Modul {
font-size: 9 rem;
}
'''

jetzt jedes Modul wird abgeschottet und leichter Stil, wartungsfreundlicher und flexibel.

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### ausblenden Automatische Wiedergabe von Videos, die nicht

Dies ist ein toller Trick für ein benutzerdefiniertes Stylesheet stummgeschaltet sind. Vermeiden Sie die Überlastung einer Benutzer mit Klang aus einem Video, das Vollbildmodus wiedergegeben, wenn die Seite geladen wird. Wenn der Ton nicht stumm geschaltet ist, nicht das Video:

'''css
Video [Wiedergabe]: Nicht ([Stumm]) {
display:none;
}
'''

noch einmal, wir Vorteil der Verwendung der [': (Nicht)'] (#-nicht-zu-applyunapply-Grenzen-auf-navigation) pseudo-Klasse zeigen.

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


### Verwenden': root' für Flexible type

Der Typ Schriftgröße in einem reaktionsschnellen Layout sollte in der Lage sein, mit jedem Bildfenster einzustellen. Sie können die Schriftgröße auf dem Bildfenster, um Höhe und Breite Verwendung': root' berechnet werden:

'''css
: root {
font-size: Calc (1 vw + 1 vh +. 5 Vmin);
}
'''

können Sie die 'root em' auf den Wert von "Berechnet benutzen: root':

'''css
Body{
font:












css1 rem/1.6 sans-serif;}'''#### [Demo] (http://codepen.io/AllThingsSmitty/pen/XKgOkR)<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup> ### Stellen Sie 'font-size' auf dem Formular Elemente für eine bessere mobile Erfahrung mit mobilen Browsern (iOS-Safari,_et al_.) von Zoom auf HTML-Formular elemente Wenn ein '<select>' tippen, Hinzufügen "font-size" auf den Selektor Regel vermeiden: '''
input[type="text"],
Input[Type="Number"],
Select,
textarea {
font-size: 16px;
}
'''

: Tänzer:

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>


## Support

Aktuelle Versionen von Chrome, Firefox, Safari, Opera, Edge, Und IE 11.

<sup> [Zurück zum Inhaltsverzeichnis] (#Table-of-Contents)</sup>
