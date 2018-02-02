CSS Protips

Een verzameling tips om uw CSS skills pro.

Inhoudsopgave

•	Protips
•	Ondersteuning
•	vertalingen
•	bijdrage richtsnoeren

Protips
1.	Gebruik een CSS Reset
2.	erven box-sizing
3.	gebruik :niet()/Unapply grenst aan Navigation
4.	Add line-height to body
5.	Vertically-Center iets
6.	kommagescheiden lijst
7.	Items selecteren met negatieve nth-kind
8.	gebruik SVG voor pictogrammen
9.	gebruiken de "Lobotomized Owl" Selector
10.	Gebruik max hoogte voor pure CSS Sliders
11.	Equal-Width Tabelcellen
12.	ontdoen van marge Hacks met Flexbox
13.	Gebruik Attribute Selectors met lege banden
14.	stijl "Default" Links
15.	consistente verticaal ritme
16.	intrinsieke verhouding dozen
17.	stijl gebroken beelden
18.	Gebruik rem voor wereldwijde omvang; Gebruik em voor lokale Sizing
19.	Verberg Autoplay filmpjes die niet gedempt
20.	gebruik :wortel voor een flexibele
21.	set font-size op formulier elementen voor een betere mobiele ervaring


Gebruik een CSS Reset
CSS resets gebruiksbeleid stijl consistentie tussen verschillende browsers met een schone lei voor styling elementen. U kunt een CSS reset bibliotheek zoals normaliseert, et al., of u kunt een eenvoudigere reset aanpak:

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}


Nu elementen worden ontdaan van marges en paddings en box-sizing helpt u bij het beheren van lay-outs met het CSS box model.
Opmerking: Als u de erven box-sizing tip hieronder ziet u soms niet de box-sizing eigendom in uw CSS gereset.

Erven box-sizing

laat box-sizing overgeërfd worden van html:

html {
  box-sizing: border-box;
}

*, *::before, *::after {
  box-sizing: inherit;
}


Dit maakt het gemakkelijker om box-sizing in plugins of andere onderdelen die hefboomwerking ander gedrag.




Gebruik :niet()/Unapply grenst aan navigatie in

plaats van over de grens...

/* add border */
.nav li {
  border-right: 1px solid #666;
}
...and then taking it off the last element...
/* remove border */
.nav li:last-child {
  border-right: none;
}

...De :niet() pseudo-klasse gelden alleen voor de elementen die u wilt:

.nav li:not(:last-child) {
  border-right: 1px solid #666;
}

Zeker, kunt u .nav li li of zelfs .nav li:first-child ~ li, maar met :niet() De intentie is zeer duidelijk en de CSS selector bepaalt de grenzen aan de manier waarop een mens zou beschrijven.

Voeg line-height op
je niet hoeft toe te voegen line-height op elk <p>, <h*> et al. afzonderlijk. In plaats daarvan, toevoegen aan berichttekst:

body {
  line-height: 1.5;
}

Deze manier tekstgedeelten kan overnemen van lichaam.




Niets Vertically-Center
Nee, het is niet zwart magic, kunt u echt centrum elementen verticaal:
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

Wilt centrum iets anders? Verticaal, horizontaal...alles, altijd en overal? CSS-Tricks heeft een mooie write-up op te doen.
Opmerking: Let bij sommige buggy gedrag met flexbox in IE11.

Kommagescheiden lijsten
maken lijstitems die eruit ziet als een echte, door komma's gescheiden lijst:
ul > li:not(:last-child)::after {
  content: ",";
}

Gebruik de :niet() pseudo-class dus geen komma wordt toegevoegd aan het laatste item.
Opmerking: Deze tip is misschien niet ideaal voor toegankelijkheid, specifiek screenreaders. En kopiëren/plakken vanuit de browser werkt niet met CSS gegenereerde content. Ga voorzichtig te werk.

Items selecteren met negatieve nth-kind
Gebruik negatieve nth-kind in CSS items te selecteren 1 tot n.
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
Of omdat u al hebt geleerd over het gebruik :niet(), probeer dan:
/* select all items except the first 3 and display them */
li:not(:nth-child(-n+3)) {
  display: none;
}

Nou dat was vrij eenvoudig.

Gebruik SVG voor pictogrammen
Er is geen enkele reden om geen gebruik te maken van SVG voor pictogrammen:
.logo {
  background: url("logo.svg");
}

SVG weegschaal goed voor alle soorten resolutie en wordt ondersteund door alle browsers terug naar IE9. Zo sloot het .png-, .jpg- of .gif-jif-whatev bestanden.
Opmerking: Als u SVG icon-alleen knoppen voor slechtzienden gebruikers en de SVG niet wordt geladen, dit zal bijdragen tot het behoud van toegankelijkheid:
.no-svg .icon-only::after {
  content: attr(aria-label);
}

Gebruik de "Lobotomized Owl" Selector
misschien een vreemde naam maar met behulp van de universele selector (*) met het aangrenzende broertje selector ( ) een krachtige CSS-functionaliteit:
* + * {
  margin-top: 1.5em;
}
In dit voorbeeld worden alle elementen in de flow van het document die volgen andere elementen ontvangt margin-top: 1.5em.
Voor meer informatie over de "lobotomized owl" selector, lees Heydon Pickering's post op een lijst.

Gebruik max hoogte voor pure CSS Sliders
werktuig CSS-only sliders met max hoogte met overloop verborgen:
.slider {
  max-height: 200px;
  overflow-y: hidden;
  width: 300px;
}

.slider:hover {
  max-height: 600px;
  overflow-y: scroll;
}
Het element vormt de max-hoogtewaarde op hangen en de schuifbalk geeft als gevolg van de overloop.
Equal-Width Tabelcellen
tabellen kan een pijn te werken met dus probeer met behulp van het tabel-layout: vast om cellen op gelijke breedte:
.calendar {
  table-layout: fixed;
}

Pijn-vrij table layouts.:
Ontdoen van marge Hacks met Flexbox
bij het werken met kolom dakgoten kunt ontdoen van ne-, eerste- en laatste kind hacks via flexbox's space-tussen eigendom:
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
Nu kolom dakgoten verschijnen altijd gelijkmatig verdeelde.

Gebruik attribuut Selectors met lege Links
links tonen wanneer de <a>-element heeft geen tekst, maar het href attribuut heeft een link:
a[href^="http"]:empty::before {
  content: attr(href);
}
Dat is best handig.
Stijl "Default" Links
Voeg een stijl voor "default" links:
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
Nu links die ingevoegd via een CMS, dat meestal niet een klassekenmerk, zal een onderscheid zonder boodschap die de cascade.
Consistente verticaal ritme
Gebruik een universele selector (*) binnen een element om een consistent verticaal ritme:
.intro > * {
  margin-bottom: 1.25rem;
}
Consistente verticaal ritme geeft een visuele esthetiek die content wordt veel beter leesbaar zijn.

Intrinsieke verhouding dozen
een vak te maken met een intrinsieke verhouding, alles wat je hoeft te doen is van toepassing Top of Bottom padding aan een div:
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
Met 20% voor vulling maakt de hoogte van het vak gelijk aan 20% van de breedte. Ongeacht de breedte van het weergavevenster kind div houdt zijn beeldverhouding (100%/20% = 5:1).

Stijl gebroken beelden
gebroken beelden meer esthetisch aangenaam met een beetje CSS:
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
Voeg nu pseudo-elementen regels om een gebruiker bericht en URL referentie van het gebroken beeld:
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

Gebruik rem voor wereldwijde omvang; Gebruik em voor lokale Sizing
na het instellen van de basis de lettergrootte op de hoofdpartitie (html { font-size: 100%; }); stel de lettergrootte voor tekstgedeelten em:
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
Then set the font-size for modules to rem:
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
Now each module becomes compartmentalized and easier to style, more maintainable, and flexible.
Verberg Autoplay filmpjes die niet gedempt
is dit een geweldige truc voor een aangepaste user stylesheet. Voorkom overbelasting van een gebruiker met het geluid van een video die screenmodus afgespeeld wanneer de pagina geladen is. Als het geluid niet gedempt, don't show video:
video[autoplay]:not([muted]) {
  display: none;
}
Nogmaals, we profiteren van de :niet() pseudo-class.

Gebruik :wortel voor flexibele Type
het type font size in een responsieve lay-out moet kunnen aanpassen met elk deelvenster. U berekent de tekengrootte op basis van het deelvenster hoogte en breedte met :wortel:
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
Nu kunt u gebruik maken van de wortel em eenheid gebaseerd op de waarde berekend door :wortel:
body {
  font: 1rem/1.6 sans-serif;
}

Set font-size op formulier elementen voor een betere mobiele ervaring
te vermijden mobiele browsers (iOS Safari, et al.) vanaf het inzoomen op een HTML formulier elementen als een <select> vervolgkeuzelijst wordt aangetikt, font-size op de selectieschakelaar regel:
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}




