<p align="center">
  <img src="../../assets/img/bulb.svg" alt="light bulb icon">
</p>

# Conseils d’expert en CSS [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Une collection de conseils pour vous aider à mener vos compétences CSS au niveau pro.

> Pour d'autres listes géniales, consultez la liste organisée par [@sindresorhus](https://github.com/sindresorhus/) des [listes impressionnantes](https://github.com/sindresorhus/awesome/).


## Table des matières

* [Conseils d’expert](#conseils-dexpert)
* [Prise en charge par les navigateurs](#prise-en-charge-par-les-navigateurs)
* [Directives pour les contributions](../../CONTRIBUTING.md)


##  Conseils d’expert

1. [Utilisez un Reset CSS](#utilisez-un-reset-css)
1. [Hériter de `box-sizing`](#hériter-de-box-sizing)
1. [Utilisez `unset` au Lieu de Réinitialiser Toutes les Propriétés](#utilisez-unset-au-lieu-de-réinitialiser-toutes-les-propriétés)
1. [Utiliser `:not()` pour Appliquer / ne pas Appliquer des Bordures à la Barre de Navigation](#utiliser-not-pour-appliquer--ne-pas-appliquer-des-bordures-à-la-barre-de-navigation)
1. [Vérifiez si la police est installée localement](#vérifiez-si-la-police-est-installée-localement)
1. [Ajouter `line-height` à `body`](#ajouter-line-height-à-body)
1. [Définissez `: focus` pour les Éléments de Formulaire](#définissez-focus-pour-les-éléments-de-formulaire)
1. [Tout Centrer Verticalement](#tout-centrer-verticalement)
1. [Listes Séparées par des Virgules](#listes-séparées-par-des-virgules)
1. [Sélectionner des Éléments en Utilisant un `nth-child` Négatif](#sélectionner-des-éléments-en-utilisant-un-nth-child-négatif)
1. [Utiliser SVG pour les Icônes](#utiliser-svg-pour-les-icônes)
1. [Utilisez le Sélecteur "chouette lobotomisée"](#utilisez-le-sélecteur-chouette-lobotomisée)
1. [Utilisez `max-height` pour des Sliders en CSS Pur](#utilisez-max-height-pour-des-sliders-en-css-pur)
1. [Cellules de Tableau à Largeur Égale](#cellules-de-tableau-à-largeur-égale)
1. [Se Débarrasser des Hacks de Marge Avec Flexbox](#se-débarrasser-des-hacks-de-marge-avec-flexbox)
1. [Utiliser des Sélecteurs d'Attribut avec des Liens Vides](#utiliser-des-sélecteurs-dattribut-avec-des-liens-vides)
1. [Style "Par Défaut" des Liens](#style-par-défaut-des-liens)
1. [Ratio de Boîtes Intrinsèque](#ratio-de-boîtes-intrinsèque)
1. [Styliser des Images Cassées](#styliser-des-images-cassées)
1. [Utilisez `rem` pour le Dimensionnement Global; Utilisez `em` pour le Dimensionnement Local](#utilisez-rem-pour-le-dimensionnement-global-utilisez-em-pour-le-dimensionnement-local)
1. [Masquer les Vidéos Lancées Automatiquement qui ne sont pas Mises en Sourdine](#masquer-les-vidéos-lancées-automatiquement-qui-ne-sont-pas-mises-en-sourdine)
1. [Utilisez `:root` pour le Type Flexible](#utilisez-root-pour-le-type-flexible)
1. [Réglez `font-size` sur les Éléments de Formulaire pour une Meilleure Expérience Mobile](#réglez-font-size-sur-les-éléments-de-formulaire-pour-une-meilleure-expérience-mobile)
1. [Utiliser les Événements de Pointeur pour Contrôler les Événements de la Souris](#utiliser-les-événements-de-pointeur-pour-contrôler-les-événements-de-la-souris)
1. [Définit `display: none` sur les sauts de ligne utilisés comme espacement](#définit-display-none-sur-les-sauts-de-ligne-utilisés-comme-espacement)


### Utilisez un Reset CSS

La réinitialisation CSS aide à faire respecter une cohérence de style entre les différents navigateurs en faisant table rase pour les éléments de style. Vous pouvez utiliser la bibliothèque de réinitialisation CSS comme [Normalize](http://necolas.github.io/normalize.css/), et al, ou vous pouvez utiliser une approche de réinitialisation plus simplifiée :

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Maintenant, les éléments seront dépouillés des marges et de zones de remplissage, et `box-sizing` vous permet de gérer la mise en page avec le modèle de boîte CSS.

#### [Démo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Remarque:** Si vous suivez le conseil [Hériter `box-sizing`](#inherit-box-sizing) ci-dessous vous pouvez choisir de ne pas inclure la propriété box-sizing dans votre reset CSS.

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Hériter de `box-sizing`

Laisser `box-sizing` être héritée de `html`:

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

Cela rend plus facile le fait de changer `box-sizing` dans des plugins ou autres composants qui exploitent d'autres comportements.

#### [Démo](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utilisez `unset` au Lieu de Réinitialiser Toutes les Propriétés

Lors de la réinitialisation des propriétés d'un élément, il n'est pas nécessaire de réinitialiser chaque propriété individuelle :

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

Vous pouvez spécifier toutes les propriétés d'un élément en utilisant le raccourci `all`. Définir la valeur sur `unset` change les propriétés d'un élément à leurs valeurs initiales :

```css
button {
  all: unset;
}
```

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utiliser `:not()` pour Appliquer / ne pas Appliquer des Bordures à la Barre de Navigation

Au lieu de mettre à l'encadrement...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

... puis l'enlever du dernier élément...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

...Utiliser la pseudo-classe `:not()` pour appliquer uniquement aux éléments que vous voulez :

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Le sélecteur CSS définit la frontière comme un humain la décrirait.

#### [Démo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Vérifiez si la police est installée localement

Vous pouvez vérifier si une police est installée localement avant de la récupérer à distance, ce qui est également une bonne astuce de performance.

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

Pointe du chapeau à Adam Argyle pour avoir partagé ce protip et cette [démo](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Ajouter `line-height` à `body`

Vous n'avez pas besoin d'ajouter `line-height` à chaque `<p>`, `<h*>`, _et al_. séparément. Au lieu de cela, ajoutez-le à `body`:

```css
body {
  line-height: 1.5;
}
```

De cette façon, les éléments textuels peuvent hériter de `body` facilement.

#### [Démo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Définissez `:focus` pour les éléments de formulaire

Les personnes voyantes utilisant le clavier se fient au focus pour déterminer où vont les événements de clavier sur la page. Mettez en évidence les éléments de formulaire, de façon cohérente par rapport à la mise en œuvre par défaut du navigateur :

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

#### [Démo](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Tout Centrer Verticalement

Non, ce n'est pas de la magie noire, vous pouvez vraiment centrer des éléments verticalement. Vous pouvez le faire avec flexbox...

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

...et aussi avec CSS Grid :

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

Vous voulez centrer autre chose ? Verticalement, horizontalement... quoi que ce soit, à tout moment, en tout lieu ? CSS-Tricks a [un article sympa](https://css-tricks.com/centering-css-complete-guide/) sur comment faire tout cela.

#### [Démo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Listes Séparées par des Virgules

Faites que les liste d'éléments ressemblent de vraies listes, séparées par des virgules :

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Utilisez la pseudo-classe `:not()` et aucune virgule ne sera ajoutée au dernier élément.

**Remarque:** Il est possible que cette astuce ne soit pas idéale pour l'accessibilité, en particulier pour les lecteurs d'écran. Et copier / coller à partir du navigateur ne fonctionne pas avec le contenu généré par CSS. Procéder avec prudence.

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Sélectionner des Éléments en Utilisant un `nth-child` Négatif

Utilisez un `nth-child` négatif en CSS pour sélectionner des éléments de 1 à n.

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```

Ou, puisque vous avez déjà appris un peu [en utilisant `:not()`](#use-not-to-applyunapply-borders-on-navigation), essayez :

```css
/* select all items except the first 3 and display them */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

#### [Démo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utiliser SVG pour les Icônes

Il n'y a aucune raison de ne pas utiliser SVG pour les icônes :

```css
.logo {
  background: url("logo.svg");
}
```

Le SVG permet de bien mettre à l'échelle et ce pour tous types de résolution, de plus il est pris en charge dans tous les navigateurs depuis [retour au IE9](http://caniuse.com/#search=svg). Donc laissez tombé vos fichiers .png, .jpg ou .gif-JIF-etc.

**Remarque:** Si vous avez seulement des boutons sous forme d'icônes SVG pour les utilisateurs voyants et que le SVG ne parvient pas à charger, cela vous aidera à maintenir l'accessibilité :

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utilisez le Sélecteur "Chouette Lobotomisée"

Il a peut être un nom étrange, mais utiliser le sélecteur universel (`*`) avec le sélecteur de frère adjacent (`+`) peut fournir une capacité de CSS puissante :

```css
* + * {
  margin-top: 1.5em;
}
```

Dans cet exemple, tous les éléments dans le flux du document qui suivent d'autres éléments recevront `margin-top: 1.5em`.

Pour en savoir plus sur le sélecteur "chouette lobotomisée", lire [la publication de Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) sur *A List Apart*.

#### [Démo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utilisez `max-height` pour des Sliders en CSS Pur

Mettre en œuvre des sliders en CSS uniquement en utilisant `max-height` avec débordement caché :

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

L'élément s'étends jusqu'à la valeur `max-height` au survol et le slider s'affiche à la suite du débordement.

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Cellules de Tableau à Largeur Égale

Il peut être pénible de travailler avec des tableaux. Essayez d'utiliser `table-layout: fixed` pour maintenir les cellules à largeur égale :

```css
.calendar {
  table-layout: fixed;
}
```

Des tableaux sans douleurs.

#### [Démo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Se Débarrasser des Hacks de Marge Avec Flexbox

Lorsque vous travaillez sur les gouttières des colonnes, vous pouvez vous débarrasser de `nth`, `first-` et `last-child` en utilisant la propriété flexbox `space-between` :


```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Maintenant les gouttières de vos colonnes apparaissent toujours uniformément espacées.

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utiliser des Sélecteurs d'Attribut avec des Liens Vides

Affichez des liens lorsque l'élément `<a>` n'a pas de valeur de texte mais que l'attribut `href` a un lien :

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

C'est assez pratique.

#### [Démo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Style "Par Défaut" des Liens

Ajouter un style pour les liens " par défaut" :

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Maintenant, les liens qui sont insérés via un CMS, qui ne disposent généralement pas d'un attribut `class`, auront une distinction sans affecter de manière générique la cascade.

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Ratio de Boîtes Intrinsèque

Pour créer une boîte avec une proportion intrinsèque, tout ce que vous devez faire est d'appliquer une zone de remplissage en haut ou en bas de à un div :

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

En utilisant 20% pour le rembourrage, cela rend la hauteur de la boîte égale à 20% de sa largeur. Peu importe la largeur de la fenêtre d'affichage, la div enfant gardera son ratio d'aspect (100% / 20% = 5: 1).

#### [Démo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Styliser des Images Cassées

Faire des images cassées esthétiquement plus agréables avec un peu de CSS :

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

Maintenant, ajoutez les règles pseudo-éléments pour afficher un message d'utilisateur et une référence URL de l'image brisée :

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

En savoir plus sur la styliser de ce patron dans [Ire Aderinokun](https://github.com/ireade/)' [message original](http://bitsofco.de/styling-broken-images/).

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utilisez `rem` pour le Dimensionnement Global; Utilisez `em` pour le Dimensionnement Local

Après avoir défini la taille de la police de base à la racine (`html { font-size: 100%; }`), définir la taille de la police pour les éléments textuels à `em` :

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

Maintenant, chaque module devient compartimentée et plus faciles à styliser, plus maintenable, et flexible.

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Masquer les Vidéos Lancées Automatiquement qui ne sont pas Mises en Sourdine

Ceci est une super astuce pour une feuille de style personnalisée par l'utilisateur. Évitez de surcharger un utilisateur avec le son d'une vidéo lue Automatiquement lorsque la page est chargée. Si le son n'est pas coupé, ne pas montrer la vidéo :

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Encore une fois, nous trions parti de l'utilisation de la pseudo-classe [`:not()`](#use-not-to-applyunapply-borders-on-navigation).

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Utilisez `:root` pour le Type Flexible

La taille type de police dans une mise en page responsive devrait être en mesure de s'ajuster à chaque fenêtre d'affichage. Vous pouvez calculer la taille de la police basée sur la hauteur de la fenêtre et la largeur en utilisant `: root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

#### [Démo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

Maintenant, vous pouvez utiliser l'unitée de `root em` basée sur la valeur calculée par`: root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Réglez `font-size` sur les Éléments de Formulaire pour une Meilleure Expérience Mobile

Pour éviter aux navigateurs mobiles (iOS Safari, _et al_.) de zoomer sur des éléments de formulaire HTML quand un menu déroulant `<select>` est touché, ajoutez `font-size` à la règle de sélection :

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



### Utiliser les Événements de Pointeur pour Contrôler les Événements de la Souris

[Les événements de pointeur](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) vous permettent de spécifier comment la souris interagit avec l'élément qu'elle touche. Pour désactiver l'événement de pointeur par défaut sur un bouton, par exemple :

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

C'est aussi simple que cela.

<sup>[retour à la table des matières](#table-des-matières)</sup>


### Définit `display: none` sur les sauts de ligne utilisés comme espacement

Comme [Harry Roberts l'a souligné](https://twitter.com/csswizardry/status/1170835532584235008), cela peut aider à empêcher les utilisateurs du système de gestion de contenu d'utiliser des sauts de ligne supplémentaires pour l'espacement:

```css
br + br {
  display: none;
}
```

<sup>[retour à la table des matières](#table-des-matières)</sup>


## Prise en charge par les navigateurs

Les versions actuelles de Chrome, Firefox, Safari, et Edge.
