<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" alt="light bulb icon">
</p>

# CSS Protips [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Uma coleção de dicas para elevar suas habilidades de CSS.

> Dê uma olhada em mais algumas [listas fantásticas](https://github.com/sindresorhus/awesome/) mantidas por [@sindresorhus](https://github.com/sindresorhus/).


## Índice

* [Protips](#protips)
* [Suporte](#suporte)
* [Contribuições](../../CONTRIBUTING.md)


## Protips

1. [Use `:not()` para Aplicar/Remover Bordas](#use-not-para-aplicarremover-bordas)
1. [Defina o `line-height` no `body`](#defina-o-line-height-no-body)
1. [Alinhe Elementos Verticalmente](#alinhe-elementos-verticalmente)
1. [Listas Separadas por Vírgula](#listas-separadas-por-vírgula)
1. [Selecione Itens Usando `nth-child` Negativo](#selecione-itens-usando-nth-child-negativo)
1. [Ícones SVG](#Ícones-svg)
1. [Use o Seletor "Lobotomized Owl"](#use-o-seletor-lobotomized-owl)
1. [Sliders em CSS com `max-height`](#sliders-em-css-com-max-height)
1. [Herde o `box-sizing`](#herde-o-box-sizing)
1. [Tabelas com Células de Tamanho Igual](#tabelas-com-células-de-tamanho-igual)
1. [Esqueça as "Margin Hacks", use Flexbox](#esqueça-as-margin-hacks-use-flexbox)
1. [Use Seletores de Atributo em Links Vazios](#use-seletores-de-atributo-em-links-vazios)
1. [Estilize Links "Default"](#estilize-links-default)
1. [Espaçamento Vertical Consistente](#espaçamento-vertical-consistente)
1. [Div com Proporção de Tela Fixa](#div-com-proporção-de-tela-fixa)
1. [Estilize Imagens Quebradas](#estilize-imagens-quebradas)
1. [Use `rem` para Definir Tamanhos Globais; Use `em` para Definir Tamanhos Locais](#use-rem-para-definir-tamanhos-globais-use-em-para-definir-tamanhos-locais)
1. [Esconda Vídeos em Autoplay Que Não Estejam no Mudo](#esconda-vídeos-em-autoplay-que-não-estejam-no-mudo)
1. [Use `:root` para uma Typografia Flexível](#use-root-para-uma-typografia-flexível)
1. [Defina `font-size` em Elementos de Formulário para uma Melhor Experiência Mobile](#set-font-size-on-form-elements-for-a-better-mobile-experience)


### Use `:not()` para Aplicar/Remover Bordas

Ao invés de colocar a borda…

```css
/* adiciona a borda */
.nav li {
  border-right: 1px solid #666;
}
```

…para então remover no último elemento…

```css
/* remove a borda */
.nav li:last-child {
  border-right: none;
}
```

…utilize a _pseudo-class_ `:not()` para aplicar a borda apenas nos elementos corretos:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Claro, você poderia usar `.nav li + li` ou ainda `.nav li:first-child ~ li`, mas usando `:not()` a intenção fica mais clara e o seletor CSS passa a definir a borda de uma maneira que nós humanos entenPasseatas mais claramente.

[**Passeata**](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[voltar ao índice](#table-of-contents)</sup>


### Defina o `line-height` no `body`

Você não precisa adicionar o `line-height` para cada `<p>`, `<h*>`, _et al_. separadamente. Apenas adicione ao `body`:

```css
body {
  line-height: 1.5;
}
```

Dessa maneira elementos de texto vão herdar o `line-height` do `body`.

[**Passeata**](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[voltar ao índice](#table-of-contents)</sup>


### Alinhe Elementos Verticalmente

Que bruxaria é essa? Não é bruxaria! Você realmente pode centralizar elementos verticalmente:

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

Isso não resolveu seu problema? O site CSS-Tricks tem [um guia completo](https://css-tricks.com/centering-css-complete-guide/) de como centralizar elementos com CSS.

**Aviso:** Fique atento com os [bugs](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) quando utilizar flexbox no IE11.

[**Passeata**](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[voltar ao índice](#table-of-contents)</sup>


### Listas Separadas por Vírgula

Transforme listas normais em listas separadas por vírgula:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Utilize a _pseudo-class_ `:not()` para evitar que a vírgula seja adicionada depois do último item.

**Aviso:** Se considerarmos acessibilidade essa dica pode não ser ideal, especialmente para usuários de leitores de tela. Além disso, copiar e/ou colar não funcionam em conteúdo criado com CSS. Proceda com cautela.

<sup>[voltar ao índice](#table-of-contents)</sup>


### Selecione Itens Usando `nth-child` Negativo

Utilize `nth-child` negativo no CSS para selecionar itens de 1 a n.

```css
li {
  display: none;
}

/* mostrar itens de 1 a 3 */
li:nth-child(-n+3) {
  display: block;
}
```

Já que você aprendeu um pouquinho sobre como usar a _pseudo-class_ [using `:not()`](#use-not-to-applyunapply-borders-on-navigation), você pode tentar:

```css
/* mostrar itens de 1 a 3 */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Mais fácil que isso só dois disso.

[**Passeata**](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[voltar ao índice](#table-of-contents)</sup>


### Ícones SVG

Não tem porque você não usar ícones em SVG:

```css
.logo {
  background: url("logo.svg");
}
```

A vantagem do SVG é que o ícone fica bom em qualquer resolução, além de ter suporte amplo em todos os browsers [desde o IE9](http://caniuse.com/#search=svg). Agora você pode se desfazer dos seus arquivos .png, .jpg, ou ainda .gif-jif-qissomano.

**Aviso:** Se você tem botões feitos apenas com ícones SVG, a dica a seguir o ajudará a manter a acessibilidade:

```css
.no-svg .icon-only:after {
  content: attr(aria-label);
}
```

<sup>[voltar ao índice](#table-of-contents)</sup>


### Use o Seletor "Lobotomized Owl"

O nome é super estranho (coruja lobotomizada), mas o uso do seletor universal (`*`) com o seletor adjacente (`+`) pode ser muito útil:

```css
* + * {
  margin-top: 1.5em;
}
```

Nesse exemplo, todos os elementos acompanhados de outros elementos recebem `margin-top: 1.5em`.

Para mais exemplos utilizando o seletor "lobotomized owl", leia [o artigo escrito por Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) no site *A List Apart*.

[**Passeata**](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[voltar ao índice](#table-of-contents)</sup>


### Sliders em CSS com `max-height`

Crie _sliders_ usando apenas CSS com `max-height` e `overflow-y: hidden`:

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

O elemento se expandirá ao valor definido no `max-height` no _hover_ e você terá um _slider_ devido ao uso do overflow.

<sup>[voltar ao índice](#table-of-contents)</sup>


### Herde o `box-sizing`

Faça que o `box-sizing` seja herdado do `html`:

```css
html {
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}
```

Assim fica fácil de alterar o `box-sizing` em plugins ou outros componentes que tenham um comportamento diferente.

<sup>[voltar ao índice](#table-of-contents)</sup>


### Tabelas com Células de Tamanho Igual

Não tem nada mais chato do que trabalhar com tabelas, mas você pode usar `table-layout: fixed` para manter as células do mesmo tamanho:

```css
.calendar {
  table-layout: fixed;
}
```

Tabelas sem dor de cabeça.

<sup>[voltar ao índice](#table-of-contents)</sup>


### Esqueça as "Margin Hacks", use Flexbox

Quando definir o espaçamento entre as colunas, você pode deixar os seletores `nth-`, `first-`, e `last-child` de lado e usar a propriedade `space-between` do flexbox:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Assim as colunas ficam espaçadas uniformemente.

<sup>[voltar ao índice](#table-of-contents)</sup>


### Use Seletores de Atributo em Links Vazios

Mostre links para `<a>` tags vazias que possuem o atributo `href`:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Mão na roda.

<sup>[voltar ao índice](#table-of-contents)</sup>


### Estilize Links "Default"

Defina estilos para links "default":

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Dessa forma, links que são inseridos por CMS – que normalmente não possuem o atributo `class` – vão ser estilizados sem comprometer outros links.

<sup>[voltar ao índice](#table-of-contents)</sup>


### Espaçamento Vertical Consistente

Use o seletor universal dentro de um elemento para criar um espaçamento vertical consistente:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

Com um espaçamento vertical consistente o seu conteúdo fica visualmente mais agradável de ler.

<sup>[voltar ao índice](#table-of-contents)</sup>


### Div com Proporção de Tela Fixa

Para criar uma div com proporção de tela fixa, tudo que você precisa fazer é adicionar `padding` (`top` ou `bottom`) a div pai:

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

Se você usar 20% no `padding` a altura da div vai ser igual a 20% de sua largura. Independente da largura do _viewport_, a div filho vai sempre manter a proporção de tela (100% / 20% = 5:1).

<sup>[voltar ao índice](#table-of-contents)</sup>


### Estilize Imagens Quebradas

Faça com que imagens quebradas fiquem esteticamente mais agradáveis com um pouquinho de CSS:

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

Agora adicione regras com _pseudo-elements_ para mostrar uma mensagem e a URL da imagem quebrada:

```css
img:before {
  content: "Desculpe, a imagem abaixo não pode ser carregada :(";
  display: block;
  margin-bottom: 10px;
}

img:after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

Leia mais sobre como estilizar imagens quebradas no [artigo original](http://bitsofco.de/styling-broken-images/) por [Ire Aderinokun](https://github.com/ireade/).

<sup>[voltar ao índice](#table-of-contents)</sup>


### Use `rem` para Definir Tamanhos Globais; Use `em` para Definir Tamanhos Locais

Depois de definir o tamanho de fonte base na raíz (`html { font-size: 16px; }`), defina o tamanho de fonte para elementos de texto utilizando `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Então defina o tamanho da fonte de módulos utilizando `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Assim fica mais fácil de estilizar e manter cada módulo, além de ser flexível.

<sup>[voltar ao índice](#table-of-contents)</sup>


### Esconda Vídeos em Autoplay Que Não Estejam no Mudo

Ótima dica para uma _stylesheet_ personalizada. Evite sobrecarregar o usuário com som de vídeos em autoplay. Se o som não estiver no mudo, esconda o vídeo:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

E aqui mais uma entre as muitas vantagens de usar a _pseudo-class_ [`:not()`](#use-not-to-applyunapply-borders-on-navigation).

<sup>[voltar ao índice](#table-of-contents)</sup>


### Use `:root` para uma Typografia Flexível

O tamanho de fonte de um site _responsive_ deveria ser ajustável de acordo com cada _viewport_. Você pode calcular o tamanho da fonte baseado na largura e na altura do _viewport_ usando `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Assim você pode utilizar a unidade de medida `root em` baseada no valor calculado por `:root`:

```css
body {
  font: 1em/1.6 sans-serif;
}
```

<sup>[voltar ao índice](#table-of-contents)</sup>


<div id="set-font-size-on-form-elements-for-a-better-mobile-experience"></div>
### Defina `font-size` em Elementos de Formulário para uma Melhor Experiência Mobile

Para evitar zoom indesejado em elementos de formulários de navegadores mobile (iOS Safari, _et al_) quando um `<select>` é selecionado, adicione `font-size` no seletor:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[voltar ao índice](#table-of-contents)</sup>


## Suporte

Versões atuais do Chrome, Firefox, Safari, Opera, Edge, e IE11.
