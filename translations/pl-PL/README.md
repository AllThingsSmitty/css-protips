<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" width="200" alt="light bulb icon">
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
1. [Użyj `:not()`, aby dodać/usunąć obramownie nawigacji](#użyj-not-aby-dodać/usunąć-obramowanie-nawigacji)
1. [Dodaj `line-height` do `body`](#dodaj-wysokość-linii-do-treści)
1. [Ustaw `:focus` dla elementów formularza](#ustaw-focus-dla-form-elements)
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
1. [Spójny pionowy rytm](#spójny-pionowy-rytm)
1. [Wewnętrzne proporcje bloków](#indywidualne-pola-wyników)
1. [Wystylizuj uszkodzone Obrazy](#wystylizuj-uszkodzone-obrazy)
1. [Użyj `rem` dla ustawień globalnych rozmiarow i `em` do ustawień localnych](#użyj-rem-dla-global-sizing-użyj-em-dla-local-sizing)
1. [Ukryj filmy z autoodtwarzaniem, które nie są wyciszone](#ukryj-filmy-z-autoodtwarzaniem-które-nie-są-wyciszone)
1. [Użyj `:root` dla elastycznych typów](#użyj-root-tryp-elastyczny)
1. [Ustaw `font-size` w elementach formularza, aby uzyskać lepsze doświadczenia na urządzeniach komórkowych](#ustaw-font-size-w-elementach-formularza-aby-uzyskać-lepsze-wrażenia-z-urządzenia-mobilnego)
1. [Użyj zdarzeń wskaźnika do sterowania zdarzeniami myszy](#użyj-zdarzeń-wskaźnika-do-sterowania-zdarzeniami-myszy)


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

**Uwaga:** skrót `all` nie jest obsługiwany w IE11 i jest obecnie rozważany pod kątem obsługi w Edge. `unset` nie jest obsługiwany w IE11.

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

Oczywiście możesz także użyć `.nav li + li`, ale z `:not()` intencja jest bardzo jasna, a selektor CSS definiuje obramowanie w sposób czytelny dla człowieka.

#### [Demonstracja](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[powrót do spisu treści](#powrót-do-spisu-treści)</sup>


### Dodaj `wysokość linii` do `body`

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

**Uwaga:** Uważaj na pewne [nieprawidłowe zachowanie](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) z Flexbox w IE11.

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

Może mieć dziwną nazwę, ale użycie uniwersalnego (`*`) z sąsiednim selektorem rodzeństwa  (`+`) może zapewnić potężne możliwości CSS:

```css
* + * {
  margin-top: 1.5em;
}
```

W tym przykładzie wszystkie elementy w przepływie dokumentu, które śledzą inne elementy, otrzymają  `margin-top: 1.5em`.

Aby uzyskać więcej informacji na temat selektora  "lobotomized owl", przeczytaj [wpis Heydon'a Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) na *A List Apart*.

#### [Próbny](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Użyj`max-height` dla suwaków Pure CSSs

Zaimplementuj suwaki CSS `max-height` Wysokości z ukrytym przepełnieniem:

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

Element rozwija się do  `max-height` po najechaniu kursorem, a suwak wyświetla się w wyniku przepełnienia.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Równoważne komórki tabeli

Tabele mogą być uciążliwe, więc spróbuj `table-layout: fixed` aby utrzymać komórki na jednakowej szerokości:

```css
.calendar {
  table-layout: fixed;
}
```

Bezbolesne układy stołów.

#### [Próbny](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Pozbądź się marginesów za pomocą Flexbox

Podczas pracy z rynnami kolumnowymi możesz pozbyć się  `nth-`, `first-`, i `last-child` za pomocą właściwości spacji między fleksami `space-between`:

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

Wyświetl linki, gdy element  `<a>` nie ma wartości tekstowej, ale atrybut  `href` ma link:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```
a
To całkiem wygodne.

#### [Próbny](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Stylizuj "Domyślne" Linki

Dodaj styl dla "domyślnych" linków:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Teraz linki wstawiane za pośrednictwem CMS, które zwykle nie mają atrybutu class, będą miały rozróżnienie bez generalnie wpływającego na kaskadę.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Spójny pionowy rytm

Użyj uniwersalnego selektora (`*`) wewnątrz elementu, aby stworzyć spójny pionowy rytm:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

Consistent vertical rhythm provides a visual aesthetic that makes content far more readable.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Indywidualne pola wyników

Aby utworzyć pole o wewnętrznym współczynniku, wystarczy zastosować górny lub dolny margines do elementu div:

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

Użycie 20% do wypełnienia sprawia, że wysokość pudełka jest równa 20% jego szerokości. Bez względu na szerokość rzutni, element div zachowa swój współczynnik proporcji  (100% / 20% = 5:1).

#### [Próbny](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści</sup>


### Wystylizuj Uszkodzone Obrazy

Spraw, aby uszkodzone obrazy były bardziej estetyczne z odrobiną CSS:

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

Teraz dodaj reguły pseudoelementów, aby wyświetlić komunikat użytkownika i adres URL uszkodzonego obrazu:

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

Dowiedz się więcej o stylizacji tego wzoru w oryginalnym poście Ire Aderinokun. [Ire Aderinokun](https://github.com/ireade/)'s [originalny post](http://bitsofco.de/styling-broken-images/).

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści</sup>


### Użyj rem dla Global Sizing; Użyj em dla Local Sizing

Po ustawieniu podstawowego rozmiaru czcionki w katalogu głównym (`html { font-size: 100%; }`), ustaw rozmiar czcionki dla elementów tekstowych na `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Następnie ustaw rozmiar czcionki dla modułów na  `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```


Teraz każdy moduł jest podzielony na sekcje i łatwiejszy do ułożenia, łatwiejszy w utrzymaniu i bardziej elastyczny.
.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści</sup>


### Ukryj filmy z autoodtwarzaniem, które nie są wyciszone

To świetna sztuczka dla niestandardowego arkusza stylów użytkownika. Unikaj przeciążania użytkownika dźwiękiem z filmu, który odtwarza się automatycznie po wczytaniu strony. Jeśli dźwięk nie jest wyciszony, nie pokazuj wideo:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```


Po raz kolejny wykorzystujemy pseudo-klasę [`:not()`](#use-not-to-applyunapply-borders-on-navigation) 

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści</sup>


### Użyj `:root` Tryp Elastyczny

Rozmiar czcionki typowej w responsywnym układzie powinien być dostosowywany dla każdej rzutni. Możesz obliczyć rozmiar czcionki na podstawie wysokości i szerokości widoku, używając `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Now you can utilize the `root em` unit based on the value calculated by `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Próbny](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


### Ustaw `font-size` w elementach formularza, aby uzyskać lepsze wrażenia z urządzenia mobilnego

Aby uniknąć korzystania z przeglądarek komurkowych  (iOS Safari, _et al_.) podczas powiększania elementów formularzy HTML po dotknięciu menu rozwijanego  `<select>` dnależy dodać  `font-size` do reguły selektora:

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

[Pointer events](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) umożliwiają określenie sposobu interakcji myszy z elementem, który dotyka. Aby wyłączyć domyślne zdarzenie wskaźnika na przycisku, na przykład:

```css
.button-disabled {
  opacity: .5;
  pointer-events: none;
}
```

To takie proste.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>


## Wsparcie

Wersje aktualne Chrome, Firefox, Safari, Opera, Edge, and IE11.

<sup>[Powrót do spisu treści](#Powrót-do-spisu-treści)</sup>