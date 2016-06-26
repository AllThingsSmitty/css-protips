<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" alt="light bulb icon">
</p>

# CSS Consejos Profesionales [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Una colección de consejos para ayudar a llevar su pro habilidades CSS.

> Para otros grandes listas echa un vistazo a [@sindresorhus](https://github.com/sindresorhus/)'s lista curada de [listas impresionantes](https://github.com/sindresorhus/awesome/).


<div id="table-of-contents"></div>
## Tabla de contenido

* [Consejos Profesionales](#protips)
* [Apoyo](#apoyo)
* [Pautas de contribución](../../CONTRIBUTING.md)


<div id="protips"></div>
## Consejos Profesionales

1. [Use `:not()` para Aplicar / Cancelar la aplicación de las bordes para la Navegación](#use-not-to-applyunapply-borders-on-navigation)
1. [Añadir `line-height` a `body`](#add-line-height-to-body)
1. [Cualquier cosa verticalmente-Centro](#vertically-center-anything)
1. [Listas separadas por comas](#comma-separated-links)
1. [Seleccionar elementos Usando negativo `nth-child`](#select-items-using-negative-nth-child)
1. [Utilizar SVG para iconos](#use-svg-for-icons)
1. [Utilice la herramienta de selección "lobotomizó búho"](#use-the-lobotomized-owl-selector)
1. [Use `max-height` característica de Sliders puro CSS](#use-max-height-for-pure-css-sliders)
1. [Heredar `box-sizing`](#inherit-box-sizing)
1. [Celdas de la tabla de igual ancho](#equal-width-table-cells)
1. [Deshacerse del margen Hacks Con Flexbox](#get-rid-of-margin-hacks-with-flexbox)
1. [Selectores de atributo con el uso Enlaces vacíos](#use-attribute-selectors-with-empty-links)
1. [Enlaces de estilo "por defecto"](#style-default-links)
1. [Consistente ritmo vertical](#consistent-vertical-rhythm)
1. [Cajas Relación intrínsecas](#intrinsic-ratio-boxes)
1. [Imágenes rotas Estilo](#style-broken-images)
1. [Use `rem` para Global Dimensionamiento; Use `em` para el dimensionamiento local](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [Esconder Reproducción automática los vídeos que no estén anulados](#hide-autoplay-videos-that-arent-muted)
1. [Utilizar `:root` para el tipo flexible](#use-root-for-flexible-type)
1. [Ajuste `font-size` en el Formulario Elementos para una mejor experiencia móvil](#set-font-size-on-form-elements-for-a-better-mobile-experience)


<div id="use-not-to-applyunapply-borders-on-navigation"></div>
### Use `:not()` para Aplicar / Cancelar los bordes de la navegación

En lugar de poner en el borde...

```css
/* Agregar el borde */
.nav li {
  border-right: 1px solid #666;
}
```

...Y luego quitarlo del último elemento...

```css
/* quitar el borde */
.nav li:last-child {
  border-right: none;
}
```

...Utiliza la pseudo-clase `:not()` que sólo se aplican a los elementos que desea:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}

```
Claro, se puede usar `li.nav + li` o incluso `li.nav: li` primer hijo ~, pero con `:not()` la intención es muy clara y el selector CSS define los bordes de la forma en que un ser humano lo describiría.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="add-line-height-to-body"></div>
### Añadir `line-height` a el `body`  

No es necesario añadir `line-height` a cada` <p> `,` <h *> `, _et al_. por separado. En su lugar, agregalo a el `body`:

```css
body {
  line-height: 1.5;
}
```

De esta manera los elementos textuales pueden heredar de `body` fácilmente.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="vertically-center-anything"></div>
### Centrar cualquier verticalmente

No, no es magia negra, realmente puedes centrar verticalmente elementos:

```css
html, body {
  height: 100%;
  margin: 0;
}

body {
  -webkit-align-items: center;
  -ms-Flex-align: center;
  alinear-elementos: center;
  display: -webkit-flex;
  display: flexionar;
}
```

¿Quieres centrar algo más? Vertical, horizontal...cualquier cosa, en cualquier momento y en cualquier lugar? CSS-Tricks tiene [un bonito reportaje](https://css-tricks.com/centering-css-complete-guide/) para hacer todo eso.

**Nota:** ve por algunos [comportamientos erroneos](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) con Flexbox en IE11.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="comma-separated-links"></div>
### Listas separadas por comas

Hacer que los elementos de la lista se vean de forma real, separados por comas:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Utilice la pseudo-clase `:not()` para agregar una coma al último elemento.

**Nota:** Esta punta puede no ser ideal para la accesibilidad, la pantalla específicamente lectores. Y copiar / pegar desde el navegador no funciona con el contenido generado por CSS. Proceda con precaución.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="select-items-using-negative-nth-child"></div>
### Seleccionar elementos Usando negativo `nth-child`

Utilice negativo `nth-child` en CSS para seleccionar los numerales 1 a n.

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```

O bien, como ya se ha aprendido un poco sobre [el uso de `:not()`](# uso no-a-applyunapply-fronteras-on-navegación), trate de:

```css
/* select items 1 through 3 and display them */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Así que era bastante fácil.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="use-svg-for-icons"></div>
### Utilizar SVG para iconos

No hay ninguna razón para no usar SVG para los iconos:

```css
.logo {
  background: url("logo.svg");
}
```

SVG funciona bien para todos los tipos de resolución y es compatible con todos los navegadores [volver a IE9](http://caniuse.com/#search=svg). Así que olvide sus archivos .png, .jpg o .gif-jif-whatev.

**Nota:** Si usted tiene SVG icono de sólo botones para los usuarios con visión y el SVG no se puede cargar, esto ayudará a mantener la accesibilidad:

```css
.no-svg .icon-only:after {
  content: attr(aria-label);
}}
```

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="use-the-lobotomized-owl-selector"></div>
### Utilice la herramienta de selección "lobotomizó búho"

Se puede tener un nombre extraño, pero con el mando universales (`*`) con el selector de hermanos adyacentes (`+`) puede proporcionar una potente capacidad de CSS:

```css
* + * {
  margin-top: 1.5em;
}
```

En este ejemplo, todos los elementos del flujo del documento que siguen otros elementos recibirán `margin-top: 1.5em`.

Para más información sobre el selector "buho lobotomized", lee [post de Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) en *A List Apart*.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="use-max-height-for-pure-css-sliders"></div>
### Use `max-height` característica de Sliders puro CSS

Implementar controles deslizantes CSS sólo para el uso de `max-height` característica con rebosadero oculto:

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

El elemento se expande para el valor `max-height` característica en vuelo estacionario y la corredera se muestra como resultado de la abundancia.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="inherit-box-sizing"></div>
### Heredar `box-sizing`

Let `box-sizing` ser heredada de `html`:

```css
html {
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}
```

Esto hace que sea más fácil cambiar `box-sizing` en plugins u otros componentes que aprovechan otros comportamientos.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="equal-width-table-cells"></div>
### Celdas de la tabla de igual ancho

Las tablas pueden ser un dolor de trabajar con lo que trate de usar `table-layout: fixed` para mantener las células en el mismo ancho:

```css
.calendar {
  table-layout: fixed;
}
```

Disposiciones de la tabla sin dolor.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="get-rid-of-margin-hacks-with-flexbox"></div>
### Deshacerse del margen Hacks Con Flexbox

Cuando se trabaja con las canaletas de columna que puede deshacerse de `nth-`, `first-` y `last-child` mediante el uso de la propiedad `space-between` de Flexbox:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Ahora canaletas de columna siempre aparecen uniformemente espaciadas.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="use-attribute-selectors-with-empty-links"></div>
### Selectores de atributo con el uso Enlaces vacíos

Mostrar vínculos cuando el elemento `<a>` no tiene un valor de texto, pero el atributo `href` tiene un enlace:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Eso es bastante conveniente.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="style-default-links"></div>
### Enlaces de estilo "por defecto"

Añadir un estilo de enlaces "por defecto":

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Ahora enlaces que se insertan a través de un CMS, que por lo general no tienen un atributo `class`, tendrán una distinción sin afectar de forma genérica la cascada.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="consistent-vertical-rhythm"></div>
### Consistente ritmo vertical

Utilice un selector universales (`*`) dentro de un elemento para crear un ritmo vertical consistente:

```ss
.intro> * {
  margin-bottom: 1.25rem;
}
```

Ritmo vertical consistente proporciona una estética visual que hace que el contenido mucho más legible.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="intrinsic-ratio-boxes"></div>
### Cajas Relación intrínsecas

Para crear un cuadro con una relación intrínseca, todo lo que tiene que hacer es aplicar el acolchado superior o inferior a un div:

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

El uso de 20% para el relleno hace que la altura de la caja igual a 20% de su anchura. No importa el ancho de la ventana, el div niño va a mantener su relación de aspecto (100% / 20% = 5: 1).

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="style-broken-images"></div>
### Imágenes rotas Estilo

Hacer imágenes rotas más estéticamente agradable con un poco de CSS:

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

Ahora añadir reglas pseudo-elementos para mostrar un mensaje de usuario y una referencia de dirección URL de la imagen rota:

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

Aprender más sobre el estilo de este patrón en [Iré Aderinokun](https://github.com/ireade/)'s [post original](http://bitsofco.de/styling-broken-images/).

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="use-rem-for-global-sizing-use-em-for-local-sizing"></div>
### Use `rem` para Global Dimensionamiento; Use `em` para el dimensionamiento local

Después de ajustar el tamaño de la fuente base en la raíz (`html {font-size: 16px;}`), ajustar el tamaño de fuente para los elementos textuales de `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1 em;
}
```

A continuación, establezca el tamaño de fuente para los módulos a `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Ahora cada módulo se divide en compartimientos y más fácil de peinar, más fácil de mantener, y flexible.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="hide-autoplay-videos-that-arent-muted"></div>
### Esconder Reproducción automática los vídeos que no estén anulados

Este es un gran truco para una hoja de estilo de usuario personalizada. Evitar la sobrecarga de un usuario con el sonido de un vídeo que se reproduce automáticamente cuando se carga la página. Si el sonido no está silenciado, no muestran el video:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Una vez más, nos estamos tomando ventaja de usar el [`:not()`](#use-not-to-applyunapply-borders-on-navigation) pseudo-clase.

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="use-root-for-flexible-type"></div>
### Utilizar `:root` para el tipo flexible

El tamaño de tipo de letra en un diseño que responde debe ser capaz de ajustar con cada ventana. Se puede calcular el tamaño de la fuente basada en la altura y la anchura de la ventana gráfica usando `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Ahora se puede utilizar la unidad de `root em` basado en el valor calculado por `:root`:

```css
body {
  font: 1em/1.6 sans-serif;
}
```

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


<div id="set-font-size-on-form-elements-for-a-better-mobile-experience"></div>
### Ajuste `font-size` en el Formulario Elementos para una mejor experiencia móvil

Para evitar los navegadores móviles (iOS Safari, _et al_.) De hacer zoom sobre los elementos de formulario HTML cuando un `<select>` desplegable se toca, agrega `font-size` a la regla de selección:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[volver al índice de contenidos](#table-of-contents)</sup>


## Soporte

Las versiones actuales de Chrome, Firefox, Safari, Opera, Edge y IE11.
