<p align="center">
  <img src="../../assets/img/bulb.svg" alt="light bulb icon">
</p>

# Consejos Profesionales para CSS [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Una colección de consejos para ayudarte a mejorar tus conocimientos profesionales de CSS.

> Para ver otras listas geniales, echa un vistazo a la lista curada por [@sindresorhus](https://github.com/sindresorhus/) de [listas Awesome](https://github.com/sindresorhus/awesome/).


## Tabla de contenido

* [Consejos Profesionales](#consejos-profesionales)
* [Soporte](#soporte)
* [Pautas para contribuir](../../CONTRIBUTING.md)


## Consejos Profesionales

1. [Utilizar un CSS Reset](#utilizar-un-css-reset)
1. [Heredar `box-sizing`](#heredar-box-sizing)
1. [Utilice `unset` en lugar de restablecer todas las propiedades](#utilice-unset-en-lugar-de-restablecer-todas-las-propiedades)
1. [Usar `:not()` para Aplicar o Cancelar la aplicación de bordes en la navegación](#usar-not-para-aplicar-o-cancelar-la-aplicación-de-bordes-en-la-navegación)
1. [Compruebe si la fuente está instalada localmente](#compruebe-si-la-fuente-está-instalada-localmente)
1. [Añadir `line-height` al `body`](#añadir-line-height-al-body)
1. [Establecer `:focus` para elementos de formulario](#establecer-focus-para-elementos-de-formulario)
1. [Centrar cualquier cosa verticalmente](#centrar-cualquier-cosa-verticalmente)
1. [Listas separadas por comas](#listas-separadas-por-comas)
1. [Seleccionar elementos usando `nth-child` negativo](#seleccionar-elementos-usando-nth-child-negativo)
1. [Utilizar SVG para los íconos](#utilizar-svg-para-los-íconos)
1. [Utilizar la herramienta de selección "Búho lobotomizado"](#utilizar-la-herramienta-de-selección-búho-lobotomizado)
1. [Usar `max-height` para Sliders con CSS puro](#usar-max-height-para-sliders-con-css-puro)
1. [Celdas de tabla de igual ancho](#celdas-de-tabla-de-igual-ancho)
1. [Deshacerse de hacks para los márgenes en Flexbox](#deshacerse-de-hacks-para-los-márgenes-en-flexbox)
1. [Utilizar atributos como selectores en enlaces vacíos](#utilizar-atributos-como-selectores-en-enlaces-vacíos)
1. [Estilizar enlaces por defecto](#estilizar-enlaces-por-defecto)
1. [Ritmo vertical consistente](#ritmo-vertical-consistente)
1. [Cajas con proporciones intrínsecas](#cajas-con-proporciones-intrínsecas)
1. [Estilizar enlaces rotos a imágenes](#estilizar-enlaces-rotos-a-imágenes)
1. [Usar `rem` para tamaños globales; Usar `em` para tamaños locales](#usar-rem-para-tamaños-globales-usar-em-para-tamaños-locales)
1. [Esconder videos con reproducción automática que no estén silenciados](#esconder-videos-con-reproducción-automática-que-no-estén-silenciados)
1. [Utilizar `:root` para una tipografía flexible](#utilizar-root-para-una-tipografía-flexible)
1. [Definir `font-size` en los elementos de formulario para una mejor experiencia móvil](#definir-font-size-en-los-elementos-de-formulario-para-una-mejor-experiencia-móvil)
1. [Usar eventos de puntero para controlar eventos de mouse](#usar-eventos-de-puntero-para-controlar-eventos-de-mouse)
1. [Establezca `display: none` en Saltos de línea utilizados como espaciado](#establezca-display-none-en-saltos-de-línea-utilizados-como-espaciado)


### Utilizar un CSS Reset

Los CSS Resets ayudan a hacer cumplir la coherencia de estilo en los diferentes navegadores, como una hoja en blanco para los elementos de estilo. Puedes utilizar una biblioteca CSS Reset como [Normalize](http://necolas.github.io/normalize.css/), y otros, o puedes utilizar un enfoque más simplificado para el reset:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Ahora los elementos están despojados de márgenes y paddings, y `box-sizing` te permite administrar el diseño con el modelo de caja de CSS.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Nota:** Si sigues el consejo de más abajo [Heredar `box-sizing`](#inherit-box-sizing) puedes optar por no incluir la propiedad `box-sizing` en tu CSS reset.

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Heredar `box-sizing`

Heredar `box-sizing` de `html`:

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

Esto hace que sea más fácil cambiar `box-sizing` en plugins u otros componentes que aprovechan otros comportamientos.

#### [Demo](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Utilice `unset` en lugar de restablecer todas las propiedades

Al restablecer las propiedades de un elemento, no es necesario restablecer cada propiedad individual:

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

Puede especificar todas las propiedades de un elemento usando la declaraciones cortas `all`. Establecer el valor a `unset` cambia las propiedades de un elemento a sus valores iniciales:

```css
button {
  all: unset;
}
```

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Usar `:not()` para Aplicar o Cancelar la aplicación de bordes en la navegación

En lugar de poner en el borde...

```css
/* Agrega estilo al borde */
.nav li {
  border-right: 1px solid #666;
}
```

... para luego quitarlo del último elemento...

```css
/* quitar estilo al borde */
.nav li:last-child {
  border-right: none;
}
```

... utiliza la pseudo-clase `:not()` para sólo aplicar el estilo a los elementos que deseas:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}

```

El selector CSS define los bordes de la forma en que un ser humano lo describiría.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Compruebe si la fuente está instalada localmente

Puede verificar si una fuente está instalada localmente antes de buscarla de forma remota, lo que también es un buen consejo de rendimiento.

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

Felicitaciones a Adam Argyle por compartir este protip y [demo](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Añadir `line-height` al `body`

No es necesario añadir `line-height` a cada` <p> `,` <h *> `, _et al_. por separado. En su lugar, agregalo al `body`:

```css
body {
  line-height: 1.5;
}
```

De esta manera los elementos de texto pueden heredarlo fácilmente de `body`.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Establecer `:focus` para elementos de formulario

Los usuarios de teclado videntes confían en el enfoque para determinar dónde van los eventos del teclado en la página. Haga que el enfoque de los elementos de formulario se destaque y sea coherente con la implementación predeterminada de un navegador:

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

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Centrar cualquier cosa verticalmente

No, no es magia negra, realmente puedes centrar elementos verticalmente:

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

...y también con CSS Grid:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

¿Quieres centrar algo más? Vertical, horizontal… cualquier cosa, en cualquier momento y en cualquier lugar? CSS-Tricks tiene [un bonito artículo](https://css-tricks.com/centering-css-complete-guide/) para hacer todo eso.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Listas separadas por comas

Hacer que los elementos de la lista se vean de forma real, separados por comas:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Utilice la pseudo-clase `:not()` para agregar una coma al último elemento.

**Nota:** Este consejo puede no ser ideal para la accesibilidad, específicamente para lectores de pantalla. Y copiar / pegar desde el navegador no funciona con el contenido generado por CSS. Procede con precaución.

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Seleccionar elementos usando `nth-child` negativo

Utiliza  `nth-child` negativo en CSS para seleccionar los numerales de 1 a n.

```css
li {
  display: none;
}

/* seleccionar los elementos de 1 hasta 3 y muestralos */
li:nth-child(-n+3) {
  display: block;
}
```

O bien, como ya has aprendido un poco sobre [el uso de `:not()`](# uso no-a-applyunapply-fronteras-on-navegación), trata de:

```css
/* seleccionar todos los elementos excepto los 3 primeros y mostrarlos */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Bueno, éso ha sido bastante fácil.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Utilizar SVG para los íconos

No hay ninguna razón para no usar SVG para los íconos:

```css
.logo {
  background: url("logo.svg");
}
```

SVG funciona bien para todos los tipos de resoluciones y es compatible con todos los navegadores [hasta IE9](http://caniuse.com/#search=svg). Así que olvidate de tus archivos .png, .jpg o .gif-jif-loquesea.

**Nota:** Si tienes botones de íconos con SVG para usuarios no videntes y el SVG falla al cargar, esto te ayudará a mantener la accesibilidad:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}}
```

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Utilizar la herramienta de selección "Búho lobotomizado"

Puede que tenga un nombre extraño, pero utilizando el selector universal (`*`) con el selector de hermanos adyacentes (`+`) puedes proporcionar una potente capacidad de CSS:

```css
* + * {
  margin-top: 1.5em;
}
```

En este ejemplo, todos los elementos del flujo del documento que siguen otros elementos recibirán `margin-top: 1.5em`.

Para más información sobre el selector "búho lobotomizado", lee el [post de Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) en *A List Apart*.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Usar `max-height` para Sliders con CSS puro

Implementar un slider con CSS puro utilizando `max-height` con overflow hidden.

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

El elemento se expande hasta el valor de `max-height` en hover y el slider se muestra como resultado del desbordamiento (overflow).

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Celdas de tabla de igual ancho

Las tablas pueden ser dolorosas para trabajar, por lo que se trate de usar `table-layout: fixed` para mantener las celdas con el mismo ancho:

```css
.calendar {
  table-layout: fixed;
}
```

Diseño de tablas sin dolor.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Deshacerse de hacks para los márgenes en Flexbox

Cuando trabajas con el espaciado entre columnas puedes deshacerte de los hacks con `nth-`, `first-` y `last-child` mediante el uso de la propiedad `space-between` de Flexbox:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Ahora las columnas aparecen siempre espaciadas uniformemente.

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Utilizar atributos como selectores en enlaces vacíos

Mostrar vínculos cuando el elemento `<a>` no tiene un valor de texto, pero el atributo `href` tiene un enlace:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Eso es bastante conveniente.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Estilizar enlaces por defecto

Añadir un estilo a los enlaces "por defecto":

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Ahora los enlaces que se insertan a través de un CMS, que por lo general no tienen un atributo `class`, tendrán una distinción sin afectar de forma genérica la cascada.

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Ritmo vertical consistente

Utilice un selector universal (`*`) dentro de un elemento para crear un ritmo vertical consistente:

```ss
.intro> * {
  margin-bottom: 1.25rem;
}
```

Un ritmo vertical consistente proporciona una estética visual que hace que el contenido sea mucho más legible.

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Cajas con proporciones intrínsecas

Para crear un cuadro con una proporción intrínseca, todo lo que tiene que hacer es aplicar un padding superior o inferior a un div:

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

Usando un 20% de padding hace que la altura de la caja sea igual al 20% de su anchura. No importa el ancho de la ventana, el div hijo va a mantener su relación de aspecto (100% / 20% = 5: 1).

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Estilizar enlaces rotos a imágenes

Haz que las imágenes rotas sean estéticamente más agradables con un poco de CSS:

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

Ahora añade propiedades desde los pseudo-elementos para mostrar un mensaje al usuario y una referencia de dirección URL de la imagen rota:

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

Aprende más sobre el estilo de este patrón en [post original](http://bitsofco.de/styling-broken-images/) de [Iré Aderinokun](https://github.com/ireade/).

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Usar `rem` para tamaños globales; Usar `em` para tamaños locales

Después de definir el tamaño de la fuente base en la raíz (`html { font-size: 100%; }`), ajusta el tamaño de fuente para los elementos textuales con `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1 em;
}
```

A continuación, establezca el tamaño de fuente para los módulos con `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Ahora cada módulo se vuelve compartimentado y más fácil de estilizar, más fácil de mantener, y más flexible.

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Esconder videos con reproducción automática que no estén silenciados

Este es un gran truco para una hoja de estilo de usuario personalizada. Evita la sobrecarga de un usuario con el sonido de un vídeo que se reproduce automáticamente cuando se carga la página. Si el sonido no está silenciado, no se muestra el video:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Una vez más, estamos tomando ventaja de usar la pseudo-clase [`:not()`](#use-not-to-applyunapply-borders-on-navigation).

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Utilizar `:root` para una tipografía flexible

El tamaño de tipo de letra en un diseño que responde debe ser capaz de ajustar con cada ventana. Se puede calcular el tamaño de la fuente basada en la altura y la anchura de la ventana gráfica usando `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Ahora se puede utilizar la unidad de `root em` basado en el valor calculado por `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Definir `font-size` en los elementos de formulario para una mejor experiencia móvil

Para evitar que los navegadores móviles (iOS Safari, _et al_.) hagan zoom sobre los elementos de un formulario HTML cuando un `<select>` desplegable es pulsado, agrega `font-size` a la regla del selector:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Usar eventos de puntero para controlar eventos de mouse

[Eventos del puntero](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) le permiten especificar cómo el mouse interactúa con el elemento que está tocando. Para deshabilitar el evento de puntero predeterminado en un botón, por ejemplo:

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

Es así de simple.

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Establezca `display: none` en Saltos de línea utilizados como espaciado

Como señaló [Harry Roberts] (https://twitter.com/csswizardry/status/1170835532584235008), esto puede ayudar a evitar que los usuarios de CMS usen saltos de línea adicionales para el espaciado:

```css
br + br {
  display: none;
}
```

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


## Soporte

Las versiones actuales de Chrome, Firefox, Safari y Edge.
