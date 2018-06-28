<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" alt="light bulb icon">
</p>

# CSS Conseils Professionnels [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Une collection de conseils pour aider à prendre vos compétences CSS pro.

> Pour les autres grandes listes vérifier [@sindresorhus](https://github.com/sindresorhus/) de la liste curated des [listes impressionnantes](https://github.com/sindresorhus/awesome/).


## Table des matières

* [Conseils Professionnels](#conseils-professionnels)
* [Soutien](#soutien)
* [Lignes directrices des contributions](../../CONTRIBUTING.md)


##  Conseils Professionnels

1. [Utilisez un Reset CSS](#utilisez-un-reset-css)
1. [Hériter `box-sizing`](#hériter-box-sizing)
1. [Utilisez `unset` au lieu de Réinitialiser Toutes les Propriétés](#utilisez-unset-au-lieu-de-réinitialiser-toutes-les-propriétés)
1. [Utiliser `:not()` postuler / unapply Borders Navigation](#utiliser-not-postuler--unapply-frontières-sur-la-navigation)
1. [Ajouter `line-height` à `body`](#ajouter-line-height-à-body)
1. [Verticalement-Center Tout](#verticalement-center-tout)
1. [Listes Comma-Separated Values](#listes-séparées-par-des-virgules)
1. [Sélectionner éléments à l'aide négative `nth-child`](#sélectionnez-éléments-à-laide-négative-nth-child)
1. [Utiliser SVG pour Icons](#utiliser-svg-pour-icons)
1. [Utilisez le sélecteur "lobotomisé Owl"](#utilisez-le-sélecteur-lobotomisé-owl)
1. [Utilisez `max-height` pour Sliders CSS pur](#utilisez-max-height-pour-sliders-css-pur)
1. [Cellules Equal Largeur de table](#cellules-equal-largeur-de-table)
1. [Se débarrasser de la marge Hacks Avec Flexbox](#se-débarrasser-de-la-marge-hacks-avec-flexbox)
1. [Utilisation des attributs sélecteurs avec des liens vides](#utilisation-des-attributs-sélecteurs-avec-des-liens-vides)
1. [Style "par défaut" Liens](#style-par-défaut-liens)
1. [Conformément Vertical Rhythm](#conformément-vertical-rhythm)
1. [Boîtes Ratio Intrinsic](#boîtes-ratio-intrinsic)
1. [Style de Broken Images](#style-de-broken-images)
1. [Utilisez `rem` for Global Dimensionnement; Utilisez `em` pour Local Sizing](#utilisez-rem-for-global-dimensionnement-utilisez-em-pour-local-sizing)
1. [Masquer les vidéos Autoplay qui ne sont pas Muted](#masquer-les-vidéos-autoplay-qui-ne-sont-pas-muted)
1. [Utiliser `:root` de type flexible](#utiliser-root-de-type-flexible)
1. [Réglez `font-size` sur le formulaire éléments pour une expérience mobile mieux](#réglez-font-size-sur-le-formulaire-éléments-pour-une-expérience-mobile-mieux)
1. [Utiliser les événements de pointeur pour contrôler les événements de la souris](#utiliser-les-événements-de-pointeur-pour-contrôler-les-événements-de-lasouris)


### Utilisez un Reset CSS

Réinitialise CSS aider à faire respecter la cohérence de style entre les différents navigateurs avec une ardoise propre pour les éléments de style. Vous pouvez utiliser la bibliothèque de réinitialisation CSS comme [Normalize](http://necolas.github.io/normalize.css/), et al, ou vous pouvez utiliser une approche de réinitialisation plus simplifiée:

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Maintenant, les éléments seront dépouillés des marges et le rembourrage, et `box-sizing` vous permet de gérer les présentations avec le modèle de boîte CSS.

#### [Démo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Remarque:** Si vous suivez la pointe [Hériter `box-sizing`](#inherit-box-sizing) ci-dessous vous pouvez choisir de ne pas inclure la propriété box-sizing dans votre reset CSS.

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Hériter `box-sizing`

Soit `box-sizing` être héritée de `html`:

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

Cela rend plus facile de changer `box-sizing` dans les plugins ou autres composants qui exploitent d'autres comportements.

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utilisez `unset` au lieu de Réinitialiser Toutes les Propriétés

Lors de la réinitialisation des propriétés d'un élément, il n'est pas nécessaire de réinitialiser chaque propriété individuelle:

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

Vous pouvez spécifier toutes les propriétés d'un élément en utilisant le raccourci `all`. Définir la valeur sur `unset` change les propriétés d'un élément à leurs valeurs initiales:

```css
button {
  all: unset;
}
```

**Remarque:** le raccourci `all` n'est pas supporté dans IE11 et est actuellement à l'étude pour le support dans Edge. `unset` n'est pas supporté dans IE11.

<sup>[retour à la table des matières](#table-des-matières)</sup>


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

Bien sûr, vous pouvez utiliser `.nav li + li`, mais avec `:not()` l'intention est très claire et le sélecteur CSS définit la frontière comme un être humain serait le décrire.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Ajouter `line-height` à `body`

Vous ne devez pas ajouter `line-height` à chaque `<p>`, `<h*>`, _et al_. séparément. Au lieu de cela, ajoutez-le à `body`:

```css
body {
  line-height: 1.5;
}
```

De cette façon, les éléments textuels peuvent hériter de `body` facilement.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Verticalement-Center Tout

Non, ce n'est pas de la magie noire, vous ne pouvez vraiment centrer des éléments verticalement:

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

Vous voulez centrer autre chose? Verticalement, horizontalement...quoi que ce soit, à tout moment, en tout lieu? CSS-Tricks a [une belle écriture-up](https://css-tricks.com/centering-css-complete-guide/) à faire tout cela.

**Remarque:** Surveillez certains [poussette behavior](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) avec flexBox dans IE11.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Listes séparées par des virgules

Faire la liste des articles ressemblent à une vraie liste, séparées par des virgules:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Utilisez le `:not()` pseudo-classe donc pas une virgule est ajoutée au dernier point.

**Remarque:** Cette astuce peut ne pas être idéal pour l'accessibilité, l'écran spécifiquement lecteurs. Et copier / coller à partir du navigateur ne fonctionne pas avec le contenu généré par CSS. Procéder avec prudence.

<sup>[retour à la table des matières](#table-des-matières)</sup>


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
/* select all items except the first 3 and display them */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Eh bien, ce fut assez facile.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[retour à la table des matières](#table-des-matières)</sup>


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
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utilisez le sélecteur "lobotomisé Owl"

Il peut avoir un nom étrange, mais en utilisant le sélecteur universel (`*`) avec le sélecteur de frère adjacent (`+`) peut fournir une capacité de CSS puissante:

```css
* + * {
  margin-top: 1.5em;
}
```

Dans cet exemple, tous les éléments dans le flux du document qui suivent d'autres éléments recevront `margin-top: 1.5em`.

Pour en savoir plus sur la "chouette lobotomisé" sélecteur, lire [le poste de Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) sur *A List Apart*.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[retour à la table des matières](#table-des-matières)</sup>


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

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Cellules Equal Largeur de table

Les tableaux peuvent être une douleur à travailler avec donc essayer d'utiliser `table-layout: fixed` pour maintenir les cellules à largeur égale:

```css
.calendar {
  table-layout: fixed;
}
```

dispositions de table sans douleur.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[retour à la table des matières](#table-des-matières)</sup>


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

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utilisation des attributs sélecteurs avec des liens vides

Liens d'affichage lorsque le `<a>` élément n'a pas de valeur de texte, mais l'attribut `href` a un lien:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

C'est assez pratique.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Style "par défaut" Liens

Ajouter un style pour "défaut" liens:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Maintenant, les liens qui sont insérés via un CMS, qui ne disposent généralement pas un attribut `class`, auront une distinction sans affecter de manière générique la cascade.

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Conformément Vertical Rhythm

Utilisez un sélecteur universel (de `*`) dans un élément pour créer un rythme vertical cohérente:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

Rythme vertical conformément offre une esthétique visuelle qui rend le contenu beaucoup plus lisible.

<sup>[retour à la table des matières](#table-des-matières)</sup>


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

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[retour à la table des matières](#table-des-matières)</sup>


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

En savoir plus sur le style de ce modèle dans [Ire Aderinokun](https://github.com/ireade/)' [message original](http://bitsofco.de/styling-broken-images/).

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utilisez `rem` for Global Dimensionnement; Utilisez `em` pour Local Sizing

Après avoir défini la taille de la police de base à la racine (`html { font-size: 100%; }`), définir la taille de la police pour les éléments textuels à `em`:

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

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Masquer les vidéos Autoplay qui ne sont pas Muted

Ceci est un grand tour pour une feuille de style utilisateur personnalisé. Évitez de surcharger un utilisateur avec le son d'une vidéo lorsque la page lectures automatiques est chargé. Si le son est pas coupé, ne pas montrer la vidéo:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Encore une fois, nous prenons avantage d'utiliser le [`:not()`](#use-not-to-applyunapply-borders-on-navigation) pseudo-classe.

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utiliser `:root` de type flexible

La taille type de police dans une disposition sensible devrait être en mesure d'ajuster à chaque fenêtre. Vous pouvez calculer la taille de la police basée sur la hauteur de la fenêtre et la largeur en utilisant `: root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

Maintenant, vous pouvez utiliser l'appareil de `root em` sur la base de la valeur calculée par`: root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

<sup>[retour à la table des matières](#table-des-matières)</sup>


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

<sup>[retour à la table des matières](#table-des-matières)</sup>



### Utiliser les événements de pointeur pour contrôler les événements de la souris

[Événements de pointeur](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) vous permet de spécifier comment la souris interagit avec l'élément qu'elle touche. Pour désactiver l'événement de pointeur par défaut sur un bouton, par exemple:

```css
.button-disabled {
  opacity: .5;
  pointer-events: none;
}
```

C'est si simple.

<sup>[retour à la table des matières](#table-des-matières)</sup>


## Soutien

Les versions actuelles de Chrome, Firefox, Safari, Opera, Edge, et IE11.
