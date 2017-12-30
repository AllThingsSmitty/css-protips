<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" alt="light bulb icon">
</p>

# Consejos Profesionales para CSS[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Una colección de consejos para ayudarte a mejorar tus conocimientos profesionales de CSS.

> Para otras grandes listas echa un vistazo a [@sindresorhus](https://github.com/sindresorhus/)'s lista curada de [listas impresionantes](https://github.com/sindresorhus/awesome/).


## Tabla de contenido

* [Consejos Profesionales](#consejos-profesionales)
* [Soporte](#soporte)
* [Pautas para contribuir](../../CONTRIBUTING.md)


## Consejos Profesionales

1. [Utilizar un CSS Reset](#utilizar-un-css-reset)
2. [Heredar `box-sizing`](#heredar-box-sizing)
3. [Usar `:not()` para Aplicar / Cancelar la aplicación de bordes en la navegación](#usar-not-para-aplicar-cancelar-la-aplicacion-de-bordes-en-la-navegación)
4. [Añadir `line-height` al `body`](#añadir-line-height-al-body)
5. [Centrar cualquier cosa verticalmente](#centrar-cualquier-cosa-verticalmente)
6. [Listas separadas por comas](#listas-separadas-por-comas)
7. [Seleccionar elementos usando `nth-child` negativo](#seleccionar-elementos-usando-nth-child-negativo)
8. [Utilizar SVG para los íconos](#utilizar-svg-para-los-iconos)
9. [Utilizar la herramienta de selección "Búho lobotomizado"](#utilizar-la-herramienta-de-selección-buho-lobotomizado)
10. [Usar `max-height` para Sliders con CSS puro](#usar-max-height-para-sliders-con-css-puro)
11. [Celdas de tabla de igual ancho](#celdas-de-tabla-de-igual-ancho)
12. [Deshacerse de hacks para los márgenes en Flexbox](#deshacerse-de-hacks-para-los-margenes-en-flexbox)
13. [Utilizar atributos como selectores en enlaces vacíos](#utilizar-atributos-como-selectores-en-enlaces-vacios)
14. [Estilizar enlaces "por defecto"](#estilos-enlaces-por-defecto)
15. [Ritmo vertical consistente](#ritmo-vertical-consistente)
16. [Cajas con proporciones intrínsecas](#cajas-con-proporciones-intrinsecas)
17. [Estilizar enlaces rotos a imágenes](#estilizar-enlaces-rotos-a-imagenes)
18. [Usar `rem` para tamaños globales; Usar `em` para tamaños locales](#usar-rem-para-tamaños-globales-usar-em-para-tamaños-locales)
19. [Esconder videos con reproducción automática que no estén silenciados](#esconder-videos-con-reproducción-automática-que-no-estén-silenciados)
20. [Utilizar `:root` para una tipografía flexible](#utilizar-root-para-una-tipografía-flexible)
21. [Definir `font-size` en los elementos de formulario para una mejor experiencia móvil](#definir-font-size-en-los-elementos-de-formulario-para-una-mejor-experiencia-móvil)


### Utilizar un CSS Reset

Los CSS Resets ayudan a hacer cumplir la coherencia de estilo en los diferentes navegadores, como una hoja en blanco para los elementos de estilo. Puedes utilizar una biblioteca CSS Reset como [Normalize](http://necolas.github.io/normalize.css/), y otros, o puedes utilizar un enfoque más simplificado para el reset:

```css
* {
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

*, *::before, *::after {
  box-sizing: inherit;
}
```

Esto hace que sea más fácil cambiar `box-sizing` en plugins u otros componentes que aprovechan otros comportamientos.

<sup>[volver al índice de contenidos](#tabla-de-contenido)</sup>


### Usar `:not()` para Aplicar / Cancelar la aplicación de bordes en la navegación

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
Claro, se puede usar `li.nav + li` o incluso `.nav li:first-child ~ li`, pero con `:not()` la intención es muy clara y el selector CSS define los bordes de la forma en que un ser humano lo describiría.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

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


### Centrar cualquier cosa verticalmente

No, no es magia negra, realmente puedes centrar elementos verticalmente:

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

¿Quieres centrar algo más? Vertical, horizontal… cualquier cosa, en cualquier momento y en cualquier lugar? CSS-Tricks tiene [un bonito artículo](https://css-tricks.com/centering-css-complete-guide/) para hacer todo eso.

**Nota:** mira algunos [comportamientos erróneos](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) de Flexbox en IE11.

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


### Utilizar SVG para los iconos

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


### Estilizar enlaces "por defecto"

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
  font-family: Helvetica, Arial, sans-serif;
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


## Soporte

Las versiones actuales de Chrome, Firefox, Safari, Opera, Edge y IE11.
