<div align="center">
  <img src="../../assets/img/bulb.svg" width="200" alt="light bulb icon">
</div>

# CSS Protips [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Uma coleção de dicas para aumentar suas habilidades no CSS.

> Dê uma olhada em mais algumas [listas fantásticas](https://github.com/sindresorhus/awesome/) mantidas por [@sindresorhus](https://github.com/sindresorhus/).


## Índice

* [Protips](#protips)
* [Suporte](#suporte)
* [Guia de Contribuições](../../CONTRIBUTING.md)


## Protips

1. [Use um Reset CSS](#use-um-reset-css)
1. [Herde o `box-sizing`](#herde-o-box-sizing)
1. [Use `unset` em vez de redefinir todas as propriedades](#use-unset-em-vez-de-redefinir-todas-as-propriedades)
1. [Use `:not()` para Aplicar/Remover Bordas](#use-not-para-aplicarremover-bordas)
1. [Verifique se a fonte está instalada localmente](#verifique-se-a-fonte-está-instalada-localmente)
1. [Defina o `line-height` no `body`](#defina-o-line-height-no-body)
1. [Definir `:focus` para elementos de formulário](#definir-focus-para-elementos-de-formulário)
1. [Alinhe Elementos Verticalmente](#alinhe-elementos-verticalmente)
1. [Use `aspect-ratio` ao invés de Height/Width](#use-aspect-ratio-ao-invés-de-heightwidth)
1. [Listas Separadas por Vírgula](#listas-separadas-por-vírgula)
1. [Selecione Itens Usando `nth-child` Negativo](#selecione-itens-usando-nth-child-negativo)
1. [Ícones SVG](#Ícones-svg)
1. [Use o Seletor "Lobotomized Owl"](#use-o-seletor-lobotomized-owl)
1. [Sliders em CSS com `max-height`](#sliders-em-css-com-max-height)
1. [Tabelas com Células de Tamanho Igual](#tabelas-com-células-de-tamanho-igual)
1. [Esqueça as "Margin Hacks", use Flexbox](#esqueça-as-margin-hacks-use-flexbox)
1. [Use Seletores de Atributo em Links Vazios](#use-seletores-de-atributo-em-links-vazios)
1. [Controle Melhor a Especificidade Com `:is()`](#controle-melhor-a-especificidade-com-is)
1. [Estilize Links "Default"](#estilize-links-default)
1. [Div com Proporção de Tela Fixa](#div-com-proporção-de-tela-fixa)
1. [Estilize Imagens Quebradas](#estilize-imagens-quebradas)
1. [Use `rem` para Definir Tamanhos Globais; Use `em` para Definir Tamanhos Locais](#use-rem-para-definir-tamanhos-globais-use-em-para-definir-tamanhos-locais)
1. [Esconda Vídeos em Autoplay Que Não Estejam no Mudo](#esconda-vídeos-em-autoplay-que-não-estejam-no-mudo)
1. [Use `:root` para uma Tipografia Flexível](#use-root-para-uma-tipografia-flexível)
1. [Defina `font-size` em Elementos de Formulário para uma Melhor Experiência Mobile](#defina-font-size-em-elementos-de-formulário-para-uma-melhor-experiência-mobile)
1. [Use eventos de ponteiro para controlar eventos do mouse](#use-eventos-de-ponteiro-para-controlar-eventos-do-mouse)
1. [Definir `display: none` em quebras de linha usadas como espaçamento](#definir-display-none-em-quebras-de-linha-usadas-como-espaçamento)
1. [Use `:empty` para Esconder Eelementos HTML Vazios](#use-empty-para-esconder-elementos-html-vazios)

### Use um Reset CSS

Resetar o CSS vai te ajudar a manter a consistência de estilo em diferentes navegadores com um ponto de partida limpo para elementos de estilo. Você pode usar a biblioteca de reset CSS como [Normalize](http://necolas.github.io/normalize.css/), ou se preferir, usar uma abordagem mais simplificada.:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Agora os elementos estarão sem margens, preenchimento e `box-sizing`. Te permitindo gerenciar o layout com o seu CSS.

#### [Exemplo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Nota:** Se você seguir a dica [Herde o box-sizing](#herde-o-box-sizing) abaixo você pode optar por não incluir a propriedade `box-sizing` em sua redefinição de CSS.

<sup>[voltar ao índice](#Índice)</sup>


### Herde o `box-sizing`

Faça com que o `box-sizing` seja herdado do `html`:

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

Assim fica fácil de alterar o `box-sizing` em plugins ou outros componentes que tenham um comportamento diferente.

#### [Exemplo](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[voltar ao índice](#Índice)</sup>


### Use `unset` em vez de redefinir todas as propriedades

Ao redefinir as propriedades de um elemento, não é necessário redefinir cada propriedade individual:

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

Você pode especificar todas as propriedades de um elemento usando a abreviação `all`. Definir o valor como `unset` altera as propriedades de um elemento para seus valores iniciais:

```css
button {
  all: unset;
}
```

<sup>[voltar ao índice](#Índice)</sup>


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

…utilize a _pseudo-classe_ `:not()` para aplicar a borda apenas nos elementos corretos:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

O seletor CSS define a borda da maneira que um humano a descreveria.

#### [Exemplo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[voltar ao índice](#Índice)</sup>


### Verifique se a fonte está instalada localmente

Você pode verificar se uma fonte está instalada localmente antes de buscá-la remotamente, o que também é uma boa dica de desempenho.

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

Dica de chapéu para Adam Argyle por compartilhar este protip e [exemplo](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[voltar ao índice](#Índice)</sup>


### Defina o `line-height` no `body`

Você não precisa adicionar o `line-height` para cada `<p>`, `<h*>`, _et al_. separadamente. Apenas adicione ao `body`:

```css
body {
  line-height: 1.5;
}
```

Dessa maneira elementos de texto vão herdar o `line-height` do `body`.

#### [Exemplo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[voltar ao índice](#Índice)</sup>


### Definir `:focus` para elementos de formulário

Os usuários de teclado com visão dependem do foco para determinar onde os eventos de teclado vão na página. Faça com que os elementos do formulário se foquem e sejam consistentes com a implementação padrão do navegador:

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

#### [Exemplo](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[voltar ao índice](#Índice)</sup>


### Alinhe Elementos Verticalmente

Que bruxaria é essa? Não é bruxaria! Você realmente pode centralizar elementos verticalmente:

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

...e também com CSS Grid:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

Isso não resolveu seu problema? O site CSS-Tricks tem [um guia completo](https://css-tricks.com/centering-css-complete-guide/) de como centralizar elementos com CSS.

#### [Exemplo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[voltar ao índice](#Índice)</sup>

### Use `aspect-ratio` ao Invés de Height/Width

A propriedade `aspect-ratio` permite que você dimensione elementos facilmente e mantem a proporção largura-altura (width-to-height) consistênte. Isso é incrivelmente útil em web design responsivo para prevenir alterações no layout. Use `object-fit` com isso para prevenir quebras no layout se os valores de altura/largura das images mudar.

```css
img {
  aspect-ratio: 16 / 9; /* width / height */
  object-fit: cover;
}
```

Aprenda mais sobre a propriedade `aspect-ratio` neste [web.dev post](https://web.dev/articles/aspect-ratio).

#### [Demo](https://codepen.io/AllThingsSmitty/pen/MWxwoNx/)

> [!NOTA]
> `aspect-ratio` e `object-fit` não são suportados em IE11.

<sup>[voltar ao índice](#Índice)</sup>

### Listas Separadas por Vírgula

Transforme listas normais em listas separadas por vírgula:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Utilize a _pseudo-classe_ `:not()` para evitar que a vírgula seja adicionada depois do último item.

**Aviso:** Se considerarmos acessibilidade essa dica pode não ser ideal, especialmente para usuários de leitores de tela. Além disso, copiar e/ou colar não funcionam em conteúdo criado com CSS. Proceda com cautela.

<sup>[voltar ao índice](#Índice)</sup>


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

Já que você aprendeu um pouquinho sobre como usar a _pseudo-classe_ [using `:not()`](#use-not-to-applyunapply-borders-on-navigation), você pode tentar:

```css
/* selecione todos os itens, exceto os primeiros 3 e exiba-os */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

Mais fácil que isso só dois disso.

#### [Exemplo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[voltar ao índice](#Índice)</sup>


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
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[voltar ao índice](#Índice)</sup>


### Use o Seletor "Lobotomized Owl"

O nome é super estranho (coruja lobotomizada), mas o uso do seletor universal (`*`) com o seletor adjacente (`+`) pode ser muito útil:

```css
* + * {
  margin-top: 1.5em;
}
```

Nesse exemplo, todos os elementos acompanhados de outros elementos recebem `margin-top: 1.5em`.

Para mais exemplos utilizando o seletor "lobotomized owl", leia [o artigo escrito por Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) no site *A List Apart*.

#### [Exemplo](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[voltar ao índice](#Índice)</sup>


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

<sup>[voltar ao índice](#Índice)</sup>


### Tabelas com Células de Tamanho Igual

Não tem nada mais chato do que trabalhar com tabelas, mas você pode usar `table-layout: fixed` para manter as células do mesmo tamanho:

```css
.calendar {
  table-layout: fixed;
}
```

Tabelas sem dor de cabeça.

#### [Exemplo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[voltar ao índice](#Índice)</sup>


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

<sup>[voltar ao índice](#Índice)</sup>


### Use Seletores de Atributo em Links Vazios

Mostre links para tags `<a>` vazias que possuem o atributo `href`:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Mão na roda.

#### [Exemplo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[voltar ao índice](#Índice)</sup>

### Controle Melhor a Especificidade Com `:is()`

A pseudoclasse `:is()` é usada para marca vários seletores de uma só vez, reduzindo a redundância e melhorando a legibilidade do código. Isso é extremamente útil para escrever seletores grandes de uma forma mais compacta.

```css
:is(section, article, aside, nav) :is(h1, h2, h3, h4, h5, h6) {
  color: green;
}
```

O conjunto de regras acima é equivalente às seguintes regras do seletor de números...

```css
section h1, section h2, section h3, section h4, section h5, section h6,
article h1, article h2, article h3, article h4, article h5, article h6,
aside h1, aside h2, aside h3, aside h4, aside h5, aside h6,
nav h1, nav h2, nav h3, nav h4, nav h5, nav h6 {
  color: green;
}
```

#### [Demo](https://codepen.io/AllThingsSmitty/pen/rNRVxdx)

> [!NOTA]
> A pseudoclasse `:is()` não é suportada em IE11.

<sup>[voltar ao índice](#Índice)</sup>

### Estilize Links "Default"

Defina estilos para links "default":

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Dessa forma, links que são inseridos por CMS – que normalmente não possuem o atributo `class` – vão ser estilizados sem comprometer outros links.

<sup>[voltar ao índice](#Índice)</sup>


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

#### [Exemplo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[voltar ao índice](#Índice)</sup>


### Estilize Imagens Quebradas

Faça com que imagens quebradas fiquem esteticamente mais agradáveis com um pouquinho de CSS:

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

Agora adicione regras com _pseudo-elementos_ para mostrar uma mensagem e a URL da imagem quebrada:

```css
img::before {
  content: "Desculpe, a imagem abaixo não pode ser carregada :(";
  display: block;
  margin-bottom: 10px;
}

img::after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

Leia mais sobre como estilizar imagens quebradas no [artigo original](http://bitsofco.de/styling-broken-images/) por [Ire Aderinokun](https://github.com/ireade/).

<sup>[voltar ao índice](#Índice)</sup>


### Use `rem` para Definir Tamanhos Globais; Use `em` para Definir Tamanhos Locais

Depois de definir o tamanho de fonte base na raíz (`html { font-size: 100%; }`), defina o tamanho de fonte para elementos de texto utilizando `em`:

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

<sup>[voltar ao índice](#Índice)</sup>


### Esconda Vídeos em Autoplay Que Não Estejam no Mudo

Ótima dica para uma _stylesheet_ personalizada. Evite sobrecarregar o usuário com som de vídeos em autoplay. Se o som não estiver no mudo, esconda o vídeo:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

E aqui mais uma entre as muitas vantagens de usar a _pseudo-classe_ [`:not()`](#use-not-to-applyunapply-borders-on-navigation).

<sup>[voltar ao índice](#Índice)</sup>


### Use `:root` para uma Tipografia Flexível

O tamanho de fonte de um site _responsivo_ deveria ser ajustável de acordo com cada _viewport_. Você pode calcular o tamanho da fonte baseado na largura e na altura do _viewport_ usando `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Assim você pode utilizar a unidade de medida `root em` baseada no valor calculado por `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Exemplo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[voltar ao índice](#Índice)</sup>


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

<sup>[voltar ao índice](#Índice)</sup>


### Use eventos de ponteiro para controlar eventos do mouse

[Eventos de ponteiro](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) permitem que você especifique como o mouse interage com o elemento que está tocando. Para desativar o evento de ponteiro padrão em um botão, por exemplo:

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

É simples assim.

<sup>[voltar ao índice](#Índice)</sup>

### Definir `display: none` em quebras de linha usadas como espaçamento

Como [Harry Roberts apontou](https://twitter.com/csswizardry/status/1170835532584235008), isso pode ajudar a impedir que os usuários do CMS usem quebras de linha extras para espaçamento:

```css
br + br {
  display: none;
}
```

<sup>[voltar ao índice](#Índice)</sup>

### Use `:empty` para Esconder Elementos HTML Vazios

Se você tem elementos HTML vazios, ou seja, o conteúdo ainda tem que ser definido ou pela CMS ou injetado dinamicamente (e.g., `<p class="error-message"></p>`) e está criando espaços indesejáveis no seu layout, use a pseudoclasse `:empty` para esconder os elementos no layout.

```css
:empty {
  display: none;
}
```

> [!NOTA]
> Lembre-se que os elementos com espaços em branco não são considerados vazios, e.g., `<p class="error-message"> </p>`.

<sup>[voltar ao índice](#Índice)</sup>

## Suporte

Versões atuais do Chrome, Firefox, Safari, e Edge.

<sup>[voltar ao índice](#Índice)</sup>