<p align="center">
  <img src="../../assets/img/bulb.svg" width="200" alt="light bulb icon">
</p>

# Wskazówki CSS [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Zbiór porad, które pomogą Ci rozwinąć zawansowane umiejętności CSS.

> Sprawdż takze inne wspaniałe listy [@sindresorhus](https://github.com/sindresorhus/) z [zaufanych list](https://github.com/sindresorhus/awesome/).

## Powrót do spisu treści

* [Wskazówki](#Wskazowki)
* [Wsparcie](#Wsparcie)
* [Wskazówki dotyczące kontrybucji do tego projektu](../../CONTRIBUTING.md)


## Wskazówki

1. [Użyj resetowania CSS](#użyj-resetowania-css)
1. [Dziedziczenie `box-sizing`](#dziedziczenie-box-sizing)
1. [Użyj `unset` zamiast resetowania wszystkich ustawień](#użyj-unset-zamiast-resetowania-wszystkich-ustawień)
1. [Użyj `:not()` aby dodać/usunąć obramownie nawigacji](#użyj-not-aby-dodaćusunąć-obramownie-nawigacji)
1. [Sprawdź, czy czcionka jest zainstalowana lokalnie](#sprawdź,-czy-czcionka-jest-zainstalowana-lokalnie)
1. [Dodaj `line-height` do `body`](#dodaj-line-height-do-body)
1. [Ustaw `:focus` dla elementów formularza](#ustaw-:focus-dla-form-elements)
1. [Przesuń cokolwiek pionowo](#przesuwanie-w-pionie)
1. [Listy rozdziele przecinkami](#listy-podzielone-przecinkami)
1. [Wybierz elementy za pomocą negatywnego `nth-child`](#wybierz-przedmioty-za-pomocą-nth-child)
1. [Użyj SVG dla ikon ](#użyj-svg-dla-ikon)
1. [Użyj selektora "Lobotomized Owl"](#użyj-selektora-lobotomized-owl)
1. [Użyj `max-height` dla suwaków Pure CSS](#użyjmax-height-dla-suwaków-pure-csss)
1. [Komórki tabeli o równej-szerokości](#równoważne-komórki-tabeli)
1. [Pozbądź się marginesów za pomocą Flexbox](#pozbądź-się-marginesów-za-pomocą-flexbox)
1. [Użyj selektorów atrybutów z pustymi linkami](#użyj-selektorów-atrybutów-z-pustymi-linkami)
1. [Stylizuj domyślne linki](#stylizuj-domyślne-linki)
1. [Wewnętrzne proporcje bloków](#wewnętrzne-proporcje-bloków)
1. [Wystylizuj uszkodzone obrazy](#wystylizuj-uszkodzone-obrazy)
1. [Użyj `rem` dla ustawień globalnych rozmiarow i `em` do ustawień localnych](#użyj-rem-dla-ustawień-globalnych-rozmiarow-i-em-do-ustawień-localnych)
1. [Ukryj filmy z autoodtwarzaniem, które nie są wyciszone](#ukryj-filmy-z-autoodtwarzaniem-które-nie-są-wyciszone)
1. [Użyj `:root` dla elastycznych typów](#użyj-`:root`-dla-elastycznych-typów)
1. [Ustaw rozmiar czcionki w elementach formularza](#ustaw-rozmiar-czcionki-w-elementach-formularza)
1. [Użyj zdarzeń wskaźnika do sterowania zdarzeniami myszy](#użyj-zdarzeń-wskaźnika-do-sterowania-zdarzeniami-myszy)
1. [Ustaw `display: none` na Podziały linii używane jako odstępy](#ustaw-display-none-na-podziały-linii-używane-jako-odstępy)


### Użyj resetowania CSS

Reset ustawień CSS umośliwia wymuszenie spójność stylu w różnych przeglądarkach z czystym konturem dla elementów stylizacyjnych. Możesz wykorzystać jedną bibliotek resetującej ustawienia CSS np. [Normalize](http://necolas.github.io/normalize.css/) lub użyć  uproszczonego sposobu resetowania:

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Elementy zostaną pozbawione marginesów i dopełnienia, a `box-sizing` pozwala zarządzać układami za pomocą modelu pudełkowego CSS (CSS box model).

#### [Demonstracja](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Uwaga:** Jeżeli zdecydujesz sie na wykorzystanie powyżej opisanej wskazówki dotyczącej  [Dziedziczenia `box-sizing`](#inherit-box-sizing) możesz zrezygnować z dodania `box-sizing` w zresetowanych ustawieniach CSS.

<sup>[powrót do spisu treści](#powrót-do-spisu-treści )</sup>


### Dziedziczenie `box-sizing`

Niech `box-sizing` zostanie odziedziczony z `html`:

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

Ułatwia to łatwiejszą zmianę `box-sizing` w wtyczkach lub innych komponentach, które wpływaja na inne zachowania.

#### [Demonstracja](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[powrót do spisu treści](#powrót-do-spisu-treści)</sup>


### Użyj `unset` zamiast resetowania wszystkich ustawień

Podczas resetowania ustawień elementu nie jest konieczne resetowanie pojedyńczych ustawień:

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

Możesz sprecyzować wszystkie właściwości elementu, używając skrótu `all`. Używając `unset` możemy zresetować ustawienia elementu do wartości początkowych:

```css
button {
  all: unset;
}
```

<sup>[powrót do spisu treści](#powrót-do-spisu-treści)</sup>


### Użyj `:not()`, aby dodać/usunąć obramownie nawigacji

Zamiast dodać obramowanie...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

...a później usunąć ja z ostatniego elementu...

```css
/* usuń obramowanie */
.nav li:last-child {
  border-right: none;
}
```

...użyj `:not()` pseudo-klasy, aby dodać obramowanie do wybranych elementów:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Selektor CSS definiuje granicę w sposób opisany przez człowieka.

#### [Demonstracja](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[powrót do spisu treści](#powrót-do-spisu-treści)</sup>


### Sprawdź, czy czcionka jest zainstalowana lokalnie

Możesz sprawdzić, czy czcionka jest zainstalowana lokalnie, przed jej zdalnym pobraniem, co również jest dobrą wskazówką dotyczącą wydajności.

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

Czapka dla Adama Argyle'a za podzielenie się tym prototypem i [demonstracją](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[powrót do spisu treści](#powrót-do-spisu-treści)</sup>


### Dodaj `line-height` do `body`

Nie musisz dodawać  `wysokości linii` do każdego  `<p>`, `<h*>`, _et al_. osobno. Zamiast tego dodaj go do `body`:

```css
body {
  line-height: 1.5;
}
```

W ten sposób elementy tekstowe mogą łatwo odziedziczyć ustawienia z `body`.

#### [Demonstracja](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Ustaw `:focus` dla elementów formularza

Obserwowani użytkownicy klawiatury polegają na fokucie, aby określić, gdzie na stronie pojawiają się zdarzenia na klawiaturze. Skoncentruj się na elementach formy, które będą spójne, a następnie domyślna implementacja przeglądarki:

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

#### [Demonstracja](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>



### Przesuwanie w pionie

Nie, to nie jest czarna magia, naprawdę możesz wyśrodkować elementy w pionie:

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

a także używając CSS Grid:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

Chcesz coś przenieść? Pionowo, poziomo... zawsze i wszędzie? Na CSS-Tricks znajdziesz [ciekawy artykuł](https://css-tricks.com/centering-css-complete-guide/) z dobrymi instrukcje na ten temat. 

#### [Demonstracja](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Listy podzielone przecinkami

Elementy listy mogą wyglądać jak prawdziwa, oddzielona przecinkami lista:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Użyj `:not()` pseudo-klasy, aby przecinek nie zostal dodany do ostatniego elementu.

**Uwaga:** Ta wskazówka może nie być idealna dla ułatwień dostępu, w szczególności na ekranach czytników. Kopiowanie / wklejanie z przeglądarki nie działa z treścią generowaną przez CSS. Postępuj ostrożnie.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Wybierz przedmioty za pomocą `nth-child`

Wybierz przedmioty nieparzyste za pomocą negatywnego  `nth-child` w CSS, aby wybrać elementy od 1 do n.

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```

Lub, skoro już nauczyłeś się trochę o użyciu [`:not()`](#use-not-to-applyunapply-borders-on-navigation),wypróbuj:

```css
/* select all items except the first 3 and display them */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

To było całkiem łatwe.

#### [Demonstracja](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Użyj SVG dla ikon

Nie ma powodu, aby nie używać SVG jako ikon:

```css
.logo {
  background: url("logo.svg");
}
```

SVG skaluje się dobrze dla wszystkich typów rozdzielczości i jest obsługiwany we wszystkich przeglądarkach [wróć do IE9](http://caniuse.com/#search=svg). Więc porzuć swoje pliki .png, .jpg lub .gif-jif-whatev.

**Uwaga:** Jeśli masz przyciski tylko ikony SVG dla widzących użytkowników, a SVG nie załaduje się, pomoże to w utrzymaniu dostępności:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Użyj selektora "Lobotomized Owl" 

Być może "Lobotomized Owl" to dziwna nazwa dla selektora, ale użycie uniwersalnego (`*`) selektora z sąsiednim selektorem rodzeństwa  (`+`) może udostepnić potężne możliwości CSS:

```css
* + * {
  margin-top: 1.5em;
}
```

W tym przykładzie wszystkie elementy, które śledzą inne elementy, otrzymają `margin-top: 1.5em`.

Dowiedź sie wiecej na temat selektora "lobotomized owl" czytajac [artykul Heydon'a Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls)  *A List Apart*.

#### [Demonstracja](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Użyj`max-height` (atrybutu maksymalnej wysokości) dla suwaków Pure CSS

Zaimplementuj suwaki CSS używając `max-height`  z ukrytym przepełnieniem:

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

Element rozwija się do `max-height` po najechaniu kursorem, a suwak wyświetla się w wyniku przepełnienia.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Komórki tabeli o równej-szerokości

Tworzenie tabel może być uciążliwe. Spróbuj użyć `table-layout: fixed`, aby upewnić sie, że komórki mają jednakową szerokość:

```css
.calendar {
  table-layout: fixed;
}
```

Widzisz jakie to proste! :)

#### [Demonstracja](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Pozbądź się marginesów za pomocą Flexbox

Podczas pracy z rynnami kolumnowymi (column gutters) możesz pozbyć się  `nth-`, `first-`, i `last-child` za pomocą właściwości`space-between`:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Teraz rynny kolumnowe zawsze są rozmieszczone równomiernie.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Użyj selektorów atrybutów z pustymi linkami

Wyświetl linki, gdy element `<a>` nie ma wartości tekstowej, ale atrybut `href` posiada link:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

To całkiem wygodne.

#### [Demonstracja](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Stylizuj "domyślne" linki

Dodaj styl dla "domyślnych" linków:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Linki wstawiane za pośrednictwem CMS, które zwykle nie mają atrybutu class, będą wyróżnione bez  wpływu na kaskadę.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Wewnętrzne proporcje bloków

Aby utworzyć pola, które posiada wewnętrzne proporcje, wystarczy zastosować górny lub dolny margines do elementu div:

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

Użycie 20% wypełnienia (padding) sprawia, że wysokość bloku jest równa 20% jego szerokości. Bez względu na szerokość okna roboczego (viewport), element div zachowa swój współczynnik proporcji  (100% / 20% = 5:1).

#### [Demonstracja](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[powrót do spisu treści](#powrót-do-spisu-treści )</sup>


### Wystylizuj uszkodzone obrazy

Spraw, aby uszkodzone obrazy były bardziej estetyczne z użyciem odrobiny CSS:

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

Następnie dodaj reguły pseudoelementów, aby wyświetlić komunikat użytkownika i adres URL uszkodzonego obrazu:

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

Dowiedz się więcej o stylizacji używając tego wzoru w oryginalnym [originalny artykule](http://bitsofco.de/styling-broken-images/) [Ire Aderinokun](https://github.com/ireade/).

<sup>[powrót do spisu treści](#powrót-do-spisu-treści )</sup>


### Użyj `rem` dla ustawień globalnych rozmiarow i `em` do ustawień localnych
Po ustawieniu podstawowego rozmiaru czcionki w katalogu głównym (`html { font-size: 100%; }`), ustaw rozmiar czcionki dla elementów tekstowych na `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Następnie ustaw rozmiar czcionki dla modułów na rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```


Teraz każdy moduł jest podzielony na sekcje. Sprawia to żę stylizacja i utrzymanie kodu jest łątwiejsze.

<sup>[powrót do spisu treści](#powrót-do-spisu-treści )</sup>


### Ukryj filmy z autoodtwarzaniem, które nie są wyciszone

To świetna sztuczka dla niestandardowego arkusza stylów użytkownika. Unikaj przeciążania użytkownika dźwiękiem z filmu, który odtwarza się automatycznie po wczytaniu strony. Jeśli dźwięk nie jest wyciszony, nie pokazuj widea:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```


Po raz kolejny wykorzystujemy pseudo-klasę [`:not()`](#use-not-to-applyunapply-borders-on-navigation) 

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści</sup>


### Użyj `:root` dla elastycznych typów

Rozmiar czcionki typowej w elastyczny układzie (responsive layout) powinien być dostosowywany dla każdego ekranu. Możesz obliczyć rozmiar czcionki na podstawie wysokości i szerokości okna roboczego używając `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Następnie możesz użyć jednostki`root em` na podstawie wartości obliczonej przez `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Demonstracja](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[powrót do spisu treści](#powrót-do-spisu-treści )</sup>


### Ustaw rozmiar czcionki w elementach formularza

Aby uniknąć korzystania z przeglądarek komórkowych  (iOS Safari etc.) podczas powiększania elementów formularzy HTML, po dotknięciu menu rozwijanego `<select>` dnależy dodać `font-size` do reguły selektora:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Użyj zdarzeń wskaźnika do sterowania zdarzeniami myszy

[Pointer events](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) umożliwiają określenie sposobu interakcji myszy z elementem, na które kilka. Aby wyłączyć domyślne zdarzenie wskaźnika na przycisku, na przykład:

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

To takie proste.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Ustaw `display: none` na Podziały linii używane jako odstępy

Jak zauważył [Harry Roberts](https://twitter.com/csswizardry/status/1170835532584235008), może to pomóc zapobiec korzystaniu przez użytkowników CMS z dodatkowych podziałów linii dla odstępów:

```css
br + br {
  display: none;
}
```

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


## Wsparcie

Wersje aktualne Chrome, Firefox, Safari, e Edge.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>