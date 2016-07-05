<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" alt="light bulb icon">
</p>

# CSS Conseils Professionnels [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Une collection de conseils pour aider à prendre vos compétences CSS pro.

> Pour les autres grandes listes vérifier [@sindresorhus](https://github.com/sindresorhus/) de la liste curated des [listes impressionnantes](https://github.com/sindresorhus/awesome/).


<div id="table-of-contents"></div>
## Table des matières

* [Conseils Professionnels](#protips)
* [Soutien](#soutien)
* [Lignes directrices des contributions](../../CONTRIBUTING.md)


<div id="protips"></div>
##  Conseils Professionnels

1. [Utiliser `:not()` postuler / unapply Borders Navigation](#use-not-to-applyunapply-borders-on-navigation)
1. [Ajouter `line-height` à `body`](#add-line-height-to-body)
1. [Verticalement-Center Tout](#vertically-center-anything)
1. [Listes Comma-Separated Values](#comma-separated-lists)
1. [Sélectionner éléments à l'aide négative `nth-child`](#select-items-using-negative-nth-child)
1. [Utiliser SVG pour Icons](#use-svg-for-icons)
1. [Utilisez le sélecteur "lobotomisé Owl"](#use-the-lobotomized-owl-selector)
1. [Utilisez `max-height` pour Sliders CSS pur](#use-max-height-for-pure-css-sliders)
1. [Hériter `box-sizing`](#inherit-box-sizing)
1. [Cellules Equal Largeur de table](#equal-width-table-cells)
1. [Se débarrasser de la marge Hacks Avec Flexbox](#get-rid-of-margin-hacks-with-flexbox)
1. [Utilisation des attributs sélecteurs avec des liens vides](#use-attribute-selectors-with-empty-links)
1. [Style "par défaut" Liens](#style-default-links)
1. [Conformément Vertical Rhythm](#consistent-vertical-rhythm)
1. [Boîtes Ratio Intrinsic](#intrinsic-ratio-boxes)
1. [Style de Broken Images] (#style-broken-images)
1. [Utilisez `rem` for Global Dimensionnement; Utilisez `em` pour Local Sizing](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [Masquer les vidéos Autoplay qui ne sont pas Muted](#hide-autoplay-videos-that-arent-muted)
1. [Utiliser `:root` de type flexible](#use-root-for-flexible-type)
1. [Réglez `font-size` sur le formulaire éléments pour une expérience mobile mieux](#set-font-size-on-form-elements-for-a-better-mobile-experience)


<div id="use-not-to-applyunapply-borders-on-navigation"></div>
### Utiliser `:not()` postuler / unapply frontières sur la navigation

Au lieu de mettre à la frontière...

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

...Utiliser la `:not()` pseudo-classe à appliquer uniquement aux éléments que vous voulez:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Bien sûr, vous pouvez utiliser `.nav li + li` ou même `.nav li:first-child ~ li`, mais avec `:not()` l'intention est très claire et le sélecteur CSS définit la frontière comme un être humain serait le décrire.

[**Démo**](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="add-line-height-to-body"></div>
### Ajouter `line-height` à `body`

Vous ne devez pas ajouter `line-height` à chaque `<p>`, `<h*>`, _et al_. séparément. Au lieu de cela, ajoutez-le à `body`:

```css
body {
  line-height: 1.5;
}
```

De cette façon, les éléments textuels peuvent hériter de `body` facilement.

[**Démo**](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="vertically-center-anything"></div>
### Verticalement-Center Tout

Non, ce n'est pas de la magie noire, vous ne pouvez vraiment centrer des éléments verticalement:

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

Vous voulez centrer autre chose? Verticalement, horizontalement...quoi que ce soit, à tout moment, en tout lieu? CSS-Tricks a [une belle écriture-up](https://css-tricks.com/centering-css-complete-guide/) à faire tout cela.

**Remarque:** Surveillez certains [poussette behavior](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) avec flexBox dans IE11.

[**Démo**](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="comma-separated-lists"></div>
### Listes séparées par des virgules

Faire la liste des articles ressemblent à une vraie liste, séparées par des virgules:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Utilisez le `:not()` pseudo-classe donc pas une virgule est ajoutée au dernier point.

**Remarque:** Cette astuce peut ne pas être idéal pour l'accessibilité, l'écran spécifiquement lecteurs. Et copier / coller à partir du navigateur ne fonctionne pas avec le contenu généré par CSS. Procéder avec prudence.

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="select-items-using-negative-nth-child"></div>
### Sélectionnez éléments à l'aide négative `nth-child`

Utilisez négative `nth-child` en CSS pour sélectionner des éléments de 1 à n.

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```

Ou, puisque vous avez déjà appris un peu [en utilisant `:not()`](#use-not-to-applyunapply-borders-on-navigation), essayez:

```css
/* select items 1 through 3 and display them */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Eh bien, ce fut assez facile.

[**Démo**](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="use-svg-for-icons"></div>
### Utiliser SVG pour Icons

Il n'y a aucune raison de ne pas utiliser SVG pour les icônes:

```css
.logo {
  background: url("logo.svg");
}
```

SVG échelles bien pour tous les types de résolution et est pris en charge dans tous les navigateurs [retour au IE9](http://caniuse.com/#search=svg). Donc fossé vos fichiers .png, .jpg ou .gif-JIF-whatev.

**Remarque:** Si vous avez SVG icon-seulement des boutons pour les utilisateurs voyants et le SVG ne parvient pas à charger, cela vous aidera à maintenir l'accessibilité:

```css
.no-svg .icon-only:after {
  content: attr(aria-label);
}
```

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="use-the-lobotomized-owl-selector"></div>
### Utilisez le sélecteur "lobotomisé Owl"

Il peut avoir un nom étrange, mais en utilisant le sélecteur universel (`*`) avec le sélecteur de frère adjacent (`+`) peut fournir une capacité de CSS puissante:

```css
* + * {
  margin-top: 1.5em;
}
```

Dans cet exemple, tous les éléments dans le flux du document qui suivent d'autres éléments recevront `margin-top: 1.5em`.

Pour en savoir plus sur la "chouette lobotomisé" sélecteur, lire [le poste de Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) sur *A List Apart*.

[**Démo**](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="use-max-height-for-pure-css-sliders"></div>
### Utilisez `max-height` pour Sliders CSS pur

Mettre en œuvre des curseurs CSS uniquement en utilisant `max-height` avec trop-plein caché:

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

L'élément se dilate à la valeur `max-height` sur le vol stationnaire et le curseur se affiche à la suite du débordement.

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="inherit-box-sizing"></div>
### Hériter `box-sizing`

Soit `box-sizing` être héritée de `html`:

```css
html {
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}

```

Cela rend plus facile de changer `box-sizing` dans les plugins ou autres composants qui exploitent d'autres comportements.

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="equal-width-table-cells"></div>
### Cellules Equal Largeur de table

Les tableaux peuvent être une douleur à travailler avec donc essayer d'utiliser `table-layout: fixed` pour maintenir les cellules à largeur égale:

```css
.calendar {
  table-layout: fixed;
}
```

dispositions de table sans douleur.

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="get-rid-of-margin-hacks-with-flexbox"></div>
### Se débarrasser de la marge Hacks Avec Flexbox

Lorsque vous travaillez avec des gouttières de colonne, vous pouvez vous débarrasser de `nth`, `first-` et `last-child` en utilisant la propriété `space-between` flexBox:


```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Maintenant gouttières colonnes apparaissent toujours uniformément espacés.

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="use-attribute-selectors-with-empty-links"></div>
### Utilisation des attributs sélecteurs avec des liens vides

Liens d'affichage lorsque le `<a>` élément n'a pas de valeur de texte, mais l'attribut `href` a un lien:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

C'est assez pratique.

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="style-default-links"></div>
### Style "par défaut" Liens

Ajouter un style pour "défaut" liens:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Maintenant, les liens qui sont insérés via un CMS, qui ne disposent généralement pas un attribut `class`, auront une distinction sans affecter de manière générique la cascade.

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="consistent-vertical-rhythm"></div>
### Conformément Vertical Rhythm

Utilisez un sélecteur universel (de `*`) dans un élément pour créer un rythme vertical cohérente:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

Rythme vertical conformément offre une esthétique visuelle qui rend le contenu beaucoup plus lisible.

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="intrinsic-ratio-boxes"></div>
### Boîtes Ratio Intrinsic

Pour créer une boîte avec un rapport intrinsèque, tout ce que vous devez faire est d'appliquer en haut ou en bas de rembourrage à un div:

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

En utilisant 20% pour le rembourrage rend la hauteur de la caisse égale à 20% de sa largeur. Peu importe la largeur de la fenêtre, la div enfant gardera son ratio d'aspect (100% / 20% = 5: 1).

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="style-broken-images"></div>
### Style de Broken Images

Faire des images brouillées esthétiquement plus agréables avec un peu de CSS:

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

Maintenant, ajoutez les règles pseudo-éléments pour afficher un message d'utilisateur et référence URL de l'image brisée:

```css
img:before {  
  content: "We're sorry, the image below is broken :(";
  display: block;
  margin-bottom: 10px;
}

img:after {  
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

En savoir plus sur le style de ce modèle dans [Ire Aderinokun](https://github.com/ireade/)' [message original](http://bitsofco.de/styling-broken-images/).

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="use-rem-for-global-sizing-use-em-for-local-sizing"></div>
### Utilisez `rem` for Global Dimensionnement; Utilisez `em` pour Local Sizing

Après avoir défini la taille de la police de base à la racine (`html { font-size: 16px; }`), définir la taille de la police pour les éléments textuels à `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Définissez ensuite la taille de police pour les modules à `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Maintenant, chaque module devient compartimentée et plus faciles à coiffer, plus maintenable, et flexible.

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="hide-autoplay-videos-that-arent-muted"></div>
### Masquer les vidéos Autoplay qui ne sont pas Muted

Ceci est un grand tour pour une feuille de style utilisateur personnalisé. Évitez de surcharger un utilisateur avec le son d'une vidéo lorsque la page lectures automatiques est chargé. Si le son est pas coupé, ne pas montrer la vidéo:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Encore une fois, nous prenons avantage d'utiliser le [`:not()`](#use-not-to-applyunapply-borders-on-navigation) pseudo-classe.

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="use-root-for-flexible-type"></div>
### Utiliser `:root` de type flexible

La taille type de police dans une disposition sensible devrait être en mesure d'ajuster à chaque fenêtre. Vous pouvez calculer la taille de la police basée sur la hauteur de la fenêtre et la largeur en utilisant `: root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Maintenant, vous pouvez utiliser l'appareil de `root em` sur la base de la valeur calculée par`: root`:

```css
body {
  font: 1em/1.6 sans-serif;
}
```

<sup>[retour à la table des matières](#table-of-contents)</sup>


<div id="set-font-size-on-form-elements-for-a-better-mobile-experience"></div>
### Réglez `font-size` sur le formulaire éléments pour une expérience mobile mieux

Pour éviter les navigateurs mobiles (iOS Safari, _et al_.) De zoom sur des éléments de formulaire HTML quand un `<select>` déroulante est taraudé, ajoutez `font-size` à la règle de sélection:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[retour à la table des matières](#table-of-contents)</sup>


## Soutien

Les versions actuelles de Chrome, Firefox, Safari, Opera, Edge, et IE11.
