<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" width="200" alt="light bulb icon">
</p>

# CSS પ્રોપ્સ [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

તમારા CSS કુશળતાને ધ્યાનમાં રાખવામાં સહાય માટે ટિપ્સનો સંગ્રહ.

> અન્ય મહાન યાદીઓ માટે તપાસો [@sindresorhus](https://github.com/sindresorhus/)'s ની યાદી [અદ્ભુત યાદીઓ](https://github.com/sindresorhus/awesome/).


## વિષયસુચીકોષ્ટક
અરજી / અનપ્પેલી કરવા માટે
* [પ્રોપ્સ](#પ્રોપ્સ)
* [આધાર](#આધાર)
* [ભાષાંતરો](#ભાષાંતરો)
* [ફાળો માર્ગદર્શિકા](CONTRIBUTING.md)


## પ્રોપ્સ

1. [એક સીએસએસ રીસેટ વાપરો](#ઉપયોગ-a-CSS-રીસેટ)
1. [વારસો `box-sizing`](#વારસો-box-sizing)
1. [વાપરવ `:not()` અરજી / અનપ્પેલી કરવા માટે નેવિગેશન પર બોર્ડર્સ](#વાપરવ-નહીં-તરફ-અરજી / અનપ્પેલી કરવા મા-બોર્ડર્સ-ઑન-નેવિગેશન)
1. [ઉમેરો `line-height` તરફ `body`](#ઍડ-line-height-થી-body)
1. [વર્ટિકલ-કેન્દ્ર કંઈપણ](#ઊભી-કેન્દ્ર-કંઈપણ)
1. [કોમા-વિભાજિત સૂચિ](#અલ્પવિરામથી-વિભાજિત-સૂચિ)
1. [નકારાત્મક મદદથી વસ્તુઓ પસંદ કરો `nth-child`](#select-items-using-negative-nth-child)
1. [ચિહ્નો માટે SVG નો ઉપયોગ કરો](#ઉપયોગ- svg- માટે-ચિહ્નો)
1. [આ વાપરો "Lobotomized Owl" પસંદગીકાર](#ઉપયોગ-આ-lobotomized-owl-પસંદગીકાર)
1. [વાપરવ `max-height` શુદ્ધ માટે CSS સ્લાઇડર્સનો](#વાપરવ-max-height-માટે-શુદ્ધ-css-સ્લાઇડર્સનો)
1. [સમાન-પહોળાઈ કોષ્ટક કોષ](#સમાન-પહોળાઈ-ટેબલ-કોશિકાઓ)
1. [છુટકારો મેળવવા માર્જિન હેક્સ સાથે Flexbox](#છુટકારો-મેળવવા-માર્જિન-હેક્સ-સાથે-flexbox)
1. [વાપરવ એટ્રીબ્યુટ પસંદગીકારો સાથે ખાલી કડીઓ](#વાપરવ-એટ્રીબ્યુટ-પસંદગીકારો-સાથે-ખાલી-કડીઓ)
1. [પ્રકાર "Default" કડીઓ](#પ્રકાર-default-કડીઓ)
1. [સુસંગત વર્ટિકલ રિધમ](#સુસંગત-ઊભી-લય)
1. [આંતરિક ગુણોત્તર બૉક્સીસ](#આંતરિક-ગુણોત્તર-બોક્સ)
1. [પ્રકાર તૂટેલી છબીઓ](#પ્રકાર-તૂટેલી-છબીઓ)
1. [વાપરવ `rem` માટે વૈશ્વિક કદ બદલવાનું; વાપરવ `em` માટે સ્થાનિક કદ બદલવાનું](#વાપરવ-rem-માટે-વૈશ્વિક-બદલવાનું-વાપરવ-em-માટે-સ્થાનિક-બદલવાનું)
1. [છુપાવો ઑટોપ્લે વિડિઓઝ તે નથ ચૂપ](#છુપાવો-ઑટોપ્લે-વિડિઓઝ-તે-નથી-ચૂપ)
1. [વાપરવ `:root` માટે Flexible Type](#વાપરવ-root-માટે-flexible-type)
1. [સેટ `font-size` on ફોર્મ તત્વો માટે a બેટર મોબાઇલ અનુભવ](#સેટ-font-size-on-ફોર્મ-તત્વો-માટે-a-બેટર-મોબાઇલ-અનુભવ)


### વાપરવ a CSS રીસેટ 

સીએસએસ રીસેટ્સ સ્ટાઇલ ઘટકો માટે સ્વચ્છ સ્લેટ સાથે વિવિધ બ્રાઉઝર્સમાં સ્ટાઇલ સુસંગતતાને અમલમાં મૂકવા માટે મદદ કરે છે. તમે જેમ કે CSS રીસેટ લાઇબ્રેરીનો ઉપયોગ કરી શકો છો [Normalize](http://necolas.github.io/normalize.css/), _et al._, અથવા તમે વધુ સરળ રીસેટ અભિગમનો ઉપયોગ કરી શકો છો:

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

હવે તત્વો માર્જિન અને પેડિંગની છીનવી લેવામાં આવશે, અને `box-sizing` તમે સીએસએસ બોક્સ મોડેલ સાથે લેઆઉટ મેનેજ કરી શકો છો.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**નોટ:** જો તમે અનુસરશો તો [Inherit `box-sizing`](#inherit-box-sizing) નીચે ટીપ તમે નીચેની શામેલ ન કરવાનું પસંદ કરી શકો છો `box-sizing` મિલકત માં  તમારા CSS રીસેટ .

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછા](#કોષ્ટક-સામગ્રીઓ)</sup>


### વારસો `box-sizing`

પરવાનગી આપો `box-sizing` માંથી વારસામાં આવશે `html`:

```css
html {
  box-sizing: border-box;
}

*, *::before, *::after {
  box-sizing: inherit;
}
```

આનાથી ફેરફાર કરવાનું સરળ બને છે `box-sizing` પ્લગઇન્સ અથવા અન્ય ઘટકોમાં લીવરેજ કે અન્ય વર્તન.

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછા](#કોષ્ટક-સામગ્રીઓ)</sup>


### વાપરવ `:not()` અરજી / અનપ્પેલી કરવા માટે નેવિગેશન પર બોર્ડર્સ

તેના બદલે નો મૂકવા સરહદ પર...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

...અને પછી તે છેલ્લા તત્વ બોલ લેવા...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

...વાપરવ `:not()` pseudo-class ફક્ત તમે ઇચ્છો તે તત્વો પર જ લાગુ કરો:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

ખાતરી કરો, તમે ઉપયોગ કરી શકો `.nav li + li` અથવા તો `.nav li:first-child ~ li`, પરંતુ સાથે `:not()` ઉદ્દેશ ખૂબ જ સ્પષ્ટ છે અને CSS પસંદગીકાર સરહદને તે રીતે વ્યાખ્યાયિત કરે છે.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછા](#કોષ્ટક-સામગ્રીઓ)</sup>


### ઉમેર `line-height` તરફ `body`

તમારે ઉમેરવાની જરૂર નથી `line-height` to દરેક `<p>`, `<h*>`, _et al_. અલગ. તેની જગ્યાએ, તેને ઉમેરવા `body`:

```css
body {
  line-height: 1.5;
}
```

આ માર્ગ textual તત્વો શકવું બોલાવે થી `body` સરળતાથી.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછા](#કોષ્ટક-સામગ્રીઓ)</sup>


### ઊભું કેન્દ્ર કંઈપણ

ના, તે કાળા જાદુ નથી, તમે ખરેખર ઊભી તત્વોને કેન્દ્રિત કરી શકો છો:

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

કેન્દ્ર માંગો છો કંઈક બીજું? વર્ટિકલ, આડા...કંઈપણ, કોઈપણ સમયે, ગમે ત્યાં? CSS-Tricks has [a nice write-up](https://css-tricks.com/centering-css-complete-guide/) on કરવાનું બધા કે.

**નોટ:** જુઓ કેટલાક માટે [buggy behavior](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) સાથે flexbox માં IE11.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### કોમા-વિભાજિત સૂચિ

સૂચિ આઇટમ્સ વાસ્તવિક, અલ્પવિરામથી વિભાજીત સૂચિની જેમ દેખાય છે તે બનાવો:

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

વાપરવ આ `:not()` pseudo-class તેથી છેલ્લી વસ્તુમાં કોઈ અલ્પવિરામ ઉમેરવામાં આવી નથી.

**નોટ:** આ ટિપ સુલભતા માટે આદર્શ નથી, ખાસ કરીને સ્ક્રીન વાચકો. અને બ્રાઉઝરમાંથી કૉપિ / પેસ્ટ CSS- જનરેટેડ સામગ્રી સાથે કામ કરતું નથી. સાવધાની સાથે આગળ વધો.

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### નકારાત્મક મદદથી વસ્તુઓ પસંદ કરો `nth-child`

વાપરવ નકારાત્મક `nth-child` વસ્તુઓ પસંદ કરવા માટે CSS માં 1 દ્વારા n.

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```

અથવા, કારણ કે તમે પહેલેથી જ વિશે થોડું શીખ્યા છે [using `:not()`](#use-not-to-applyunapply-borders-on-navigation), પ્રયત્ન કરો:

```css
/* select all items except the first 3 and display them */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

વેલ તે ખૂબ સરળ હતું.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### વાપરવુ માટે SVG નો ઉપયોગ કરો

ચિહ્નો માટે એસવીજીનો ઉપયોગ ન કરવા માટે કોઈ કારણ નથી

```css
.logo {
  background: url("logo.svg");
}
```

The SVG scale is good for all resolution types and it is supported in all browsers [back to IE9](http://caniuse.com/#search=svg). તેથી છુટકારો મેળવવા .png, .jpg, or .gif-jif-whatev ફાઈલો.

**નોટ:** જો તમારી પાસે SVG આઇકોન-માત્ર બટનો છે અને જોવામાં આવેલાં વપરાશકર્તાઓ માટે SVG લોડ કરવામાં નિષ્ફળ જાય, તો તે એક્સેસીબિલીટી જાળવી રાખવામાં મદદ કરશે.:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### આ વાપરો "Lobotomized Owl" પસંદગીકાર

તેમાં વિચિત્ર નામ હોઈ શકે છે પરંતુ સાર્વત્રિક પસંદગીકારનો ઉપયોગ કરી શકો છો (`*`) અડીન બહેન સિલેક્ટર સાથે (`+`) શક્તિશાળી CSS ક્ષમતા પ્રદાન કરી શકે છે:

```css
* + * {
  margin-top: 1.5em;
}
```

આ ઉદાહરણમાં, અન્ય ઘટકોને અનુસરતા દસ્તાવેજના પ્રવાહમાંના બધા તત્વો પ્રાપ્ત થશે `margin-top: 1.5em`.

વધુ માટે "lobotomized owl" પસંદગીકાર, વાંચવું [Heydon Pickering's post](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) on *A List Apart*.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### વાપરવ `max-height` શુદ્ધ માટે CSS સ્લાઇડર્સન

ફક્ત ઉપયોગ કરીને CSS- ફક્ત સ્લાઇડર્સનો અમલ કરો `max-height` ઓવરફ્લો છુપાયેલ સાથે:

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

આ તત્વ વિસ્તરે છે `max-height` Value on hover and slider display as a result of overflow.

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### સમાન-પહોળાઈ કોષ્ટક કોષ

કોષ્ટકો સાથે કામ કરવા માટે પીડા હોઈ શકે છે જેથી આનો ઉપયોગ કરીને પ્રયાસ કરો `table-layout: fixed` કોષો સમાન પહોળાઈ પર રાખો:

```css
.calendar {
  table-layout: fixed;
}
```

પેઇન-મુક્ત કોષ્ટક લેઆઉટ.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### છુટકારો મેળવવા માર્જિન હેક્સ સાથે Flexbox

સ્તંભ ગટર સાથે કામ કરતી વખતે તમે છુટકારો મેળવી શકો છો `nth-`, `first-`, અને `last-child` હેક્સ દ્વારા ઉપયોગ કરીને flexbox's `space-between` મિલકત:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

હવે સ્તંભ ગટર હંમેશા સરખે ભાગે-અંતરે દેખાય છે.

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### વાપરવ એટ્રીબ્યુટ પસંદગીકારો સાથે ખાલી કડીઓ

લિંક્સ દર્શાવો જ્યારે `<a>` તત્વ કોઈ લખાણ કિંમત નથી પરંતુ `href` લક્ષણ એક લિંક છે:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

તે ખૂબ અનુકૂળ છે

#### [Demo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### પ્રકાર "Default" કડીઓ

માટે એક શૈલી ઉમેરો "default" લિંક્સ:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

હવે લિંક્સ કે જે CMS દ્વારા દાખલ કરવામાં આવે છે, જે સામાન્ય રીતે એક નથી `class` એટ્રિબ્યુટ, સામાન્ય રીતે કાસ્કેડને અસર કરતા વગર ભેદ રાખશે.

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### સુસંગત વર્ટિકલ રિધમ

સાર્વત્રિક પસંદગીકારનો ઉપયોગ કરો (`*`) એક તત્વ અંદર સતત ઊભા લય બનાવવા માટે:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

સતત વ્રેટકલ લય દૃશ્ય એકંદર પૂરી પાડે છે જે સામગ્રીને વધુ વાંચવા માટે બનાવે છે.

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### આંતરિક ગુણોત્તર બૉક્સીસ

સ્વભાવિક રેશિયો સાથે બૉક્સ બનાવવા માટે, તમારે ફક્ત ટોચ અથવા તળિયે ગાદીને DIV પર લાગુ કરવાની જરૂર છે:

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

પેડિંગ માટે 20% નો ઉપયોગ કરીને તેના પહોળાઈના 20% જેટલા બૉક્સની ઊંચાઇને બનાવે છે. કોઈ  વ્યૂપોર્ટની પહોળાઇ, બાળક ડિવ તેના પાસા રેશિયો રાખશે (100% / 20% = 5:1).

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### પ્રકાર તૂટેલી છબીઓ

તૂટેલી તસવીરો CSS ના થોડુંક સાથે વધુ સૌંદર્યલક્ષી-આનંદી બનાવો:

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

હવે ઉમેરો pseudo-elements તૂટેલી છબીના વપરાશકર્તા સંદેશ અને URL સંદર્ભને પ્રદર્શિત કરવાના નિયમો:

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

આ પેટર્ન માટે સ્ટાઇલ વિશે વધુ જાણો [Ire Aderinokun](https://github.com/ireade/)'s [original post](http://bitsofco.de/styling-broken-images/).

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### વાપરવ `rem` માટે વૈશ્વિક કદ બદલવાનું; વાપરવ `em` માટે સ્થાનિક કદ બદલવાનું

રુટ પર મૂળ ફોન્ટ માપ સુયોજિત કર્યા પછી (`html { font-size: 100%; }`), શાબ્દિક તત્વો માટે ફૉન્ટનું કદ સેટ કરો `em`:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

પછી મોડ્યુલો માટે ફૉન્ટ-કદ સેટ કરો to `rem`:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

હવે દરેક મોડ્યુલ શ્રેણીબદ્ધ અને સરળ, વધુ નિભાવવા યોગ્ય અને લવચીક બની જાય છે.

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### છુપાવો ઑટોપ્લે વિડિઓઝ તે નથ ચૂપ

આ વૈવિધ્યપૂર્ણ વપરાશકર્તા સ્ટાઇલશીટ માટે એક મહાન યુક્તિ છે. એક વપરાશકર્તા દ્વારા અવાજ સાથે ઓવરલોડિંગ કરવાનું ટાળો, જે જ્યારે પૃષ્ઠ લોડ થાય ત્યારે ઑટોપ્લે કરે છે. જો અવાજ મૌન નથી, તો વિડિઓ બતાવશો નહીં:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

ફરી એક વાર, અમે આનો ઉપયોગ કરીને લાભ લઈ રહ્યાં છીએ [`:not()`](#use-not-to-applyunapply-borders-on-navigation) pseudo-class.

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### વાપરવ `:root` માટે Flexible Type

એક પ્રતિસાદિત લેઆઉટમાં ટાઇપ ફૉન્ટનું કદ દરેક વ્યૂપોર્ટ સાથે વ્યવસ્થિત થવું જોઈએ. તમે ઉપયોગ કરીને વ્યૂપોર્ટની ઊંચાઈ અને પહોળાઈના આધારે ફોન્ટ કદની ગણતરી કરી શકો છો `:root`:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

હવે તમે આ ઉપયોગ શ `root em` દ્વારા ગણવામાં આવેલ કિંમત પર આધારિત એકમ `:root`:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


### સેટ `font-size` on ફોર્મ તત્વો માટે a બેટર મોબાઇલ અનુભવ

મોબાઇલ બ્રાઉઝર્સને ટાળવા માટે (iOS Safari, _et al_.) થી ઝુમિંગ HTML ફોર્મ એલિમેન્ટ્સ પર જ્યારે એક `<select>` ડ્રોપ ડાઉન ટેપ થયેલ છે, ઉમેરો `font-size` to the selector rule:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


## આધાર

વર્તમાન આવૃત્તિઓ of Chrome, Firefox, Safari, Opera, Edge, અને IE11.

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>


## ભાષાંતરો

* [Español](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/es-ES)
* [Français](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/fr-FR)
* [Italiano](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/it-IT)
* [日本語](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ja-JP)
* [Polskie](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pl-PL)
* [Português do Brasil](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-BR)
* [Русский](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ru-RU)
* [简体中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-CN)

<sup>[સામગ્રીઓના કોષ્ટકમાં પાછ](#કોષ્ટક-સામગ્રીઓ)</sup>
