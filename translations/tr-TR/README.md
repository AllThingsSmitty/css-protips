<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" width="200" alt="light bulb icon">
</p>

# CSS Protips [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

CSS yeteneklerinizi üst seviyeye çıkaracak teknikler listesi

> Daha başka konularla ilgili muhteşem kaynaklar için [@sindresorhus](https://github.com/sindresorhus/)'un seçkisine göz atabilirsiniz. [awesome lists](https://github.com/sindresorhus/awesome/).

## İçerikler

* [İpuçları](#protips)
* [Destek](#support)
* [Çeviriler](#translations)
* [Katkıda Bulunma Rehberi](CONTRIBUTING.md)


## İpuçları

1. [CSS Reset kullanın](#use-a-css-reset)
1. [`box-sizing` özelliğini kalıtımla destekleyin](#inherit-box-sizing)
1. [Bir ögenin bütün özelliklerini sıfırlamak yerine `unset` belirtecini kullanın](#use-unset-instead-of-resetting-all-properties)
1. [`:not()` seçicisini kullanın](#use-not-to-applyunapply-borders-on-navigation)
1. [Kullandığınız fontların kullanıcı bilgisayarında yüklü olup olmadığını kontrol edin](#check-if-font-is-installed-locally)
1. [Body tag'ine bir `line-height` değeri atayın](#add-line-height-to-body)
1. [Form elementlerinin `:focus` durumu için bir stil tanımlayın](#set-focus-for-form-elements)
1. [Herhangi bir nesneyi dikey olarak ortalamanın yolu](#vertically-center-anything)
1. [Virgülle ayrılmış ögeler listesi](#comma-separated-lists)
1. [Aynı türdeki birden fazla elementi stillendirmek için negatif değerli `nth-child` seçicisini kullanın](#select-items-using-negative-nth-child)
1. [İkonlar için SVG grafikler kullanın](#use-svg-for-icons)
1. [ * + * seçicisini kullanın](#use-the-lobotomized-owl-selector)
1. [Daha etkili scroll için `max-height` özelliğini kullanın](#use-max-height-for-pure-css-sliders)
1. [Eşit Ölçülü Tablo Hücreleri](#equal-width-table-cells)
1. [Flexbox kullanarak, nesnelerin margin değerini belirlemenin zorluğundan kurtulun](#get-rid-of-margin-hacks-with-flexbox)
1. [Metin girilmemiş linkler](#use-attribute-selectors-with-empty-links)
1. [Standart linkleri stillendirin](#style-default-links)
1. [Intrinsic Ratio Boxes](#intrinsic-ratio-boxes) (translation in progres...)
1. [Kaynağına ulaşılamayan resimleri stillendirin](#style-broken-images)
1. [Global yazı boyutu için `rem` nesnelere özel yazı boyutu için `em` ölçülerini kullanın](#use-rem-for-global-sizing-use-em-for-local-sizing)
1. [Sesi açık halde otomatik olarak oynayan videoları gizleyin](#hide-autoplay-videos-that-arent-muted)
1. [Tasarımınıza göre ölçeklenen yazı boyutu için `:root` seçicisini kullanın](#use-root-for-flexible-type)
1. [Daha etkili bir mobil kullanım deneyimi için form elementlerinin `font-size` değerini belirleyin](#set-font-size-on-form-elements-for-a-better-mobile-experience)
1. [Mouse aksiyonlarını kontrol etmek için pointer-events özelliğini kullanın](#use-pointer-events-to-control-mouse-events)
1. [Boşluk vermek için kullanılan <br/> elementlerini gizleyin](#set-display-none-on-line-breaks-used-as-spacing)


### CSS Reset kullanın

CSS reset, tarayıcılar arasındaki stil farklarını ortadan kaldırmanıza yarar ve kullandığınız her elementin sahip olduğu standart stili her tarayıcı için eşitlemenizi sağlar.
Bu sayede tarayıcılar arası stil tutarlılığını sağlayabilirsiniz. CSS reset için [Normalize](http://necolas.github.io/normalize.css/) vb. bir kütüphane kullanabilir ya da basit olarak aşağıdaki css kod bloğunu projenize ekleyebilirsiniz.

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Artık bütün elementler margin ve padding değerlerden arındırılmış durumda.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Not:** Bir sonraki başlığa göz atarak `box-sizing` değerini CSS Reset ile birlikte nasıl kullanabileceğiniz hakkında önemli bir fikir edinebilirsiniz. [`box-sizing` özelliğini kalıtımla destekleyin](#inherit-box-sizing)

<sup>[Listeye dönün](#table-of-contents)</sup>


### `box-sizing` özelliğini kalıtımla destekleyin

`box-sizing` değerini `html` seçicisinden kalıtalım.

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

Bu kullanım şekli, farklı `box-sizing` değeri kullanmak istediğinizde sizlere daha fazla esneklik sağlar. Ayrıca projenizde kullandığınız ve farklı `box-sizing` değerine sahip olan eklentilerin sizin stillerinizden etkilenmemesini sağlar.

#### [Demo](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[Listeye dönün](#table-of-contents)</sup>


### Bir ögenin bütün özelliklerini sıfırlamak yerine `unset` belirtecini kullanın

Bir elementin özelliklerini sıfırlamak istediğinizde bunu yapmak için aşağıdaki gibi uzun bir yönteme ihtiyacınız yok.

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

Bunun yerine aşağıda gördüğünüz şekilde, kısaca bir elementin `all` özelliğini `unset` olarak ayarlayabilirsiniz. Bu yöntem, o elementin bütün özelliklerini standart değerine döndürür.

```css
button {
  all: unset;
}
```

**Not:** `all` özelliği ve `unset` değeri Interet Explorer'ın 11 sürümü ve öncesinde desteklenmemektedir.

<sup>[Listeye dönün](#table-of-contents)</sup>


### `:not()` seçicisini kullanın.

Birbiriyle benzerlik gösteren elementleri stillendirirken aşağıdaki klasik yöntemi kullanırız. Örneğin; yatay bir menü tasarladınız ve bu menünün ögelerini sağ bordürle ayırmak istediniz.
Önce menü ögelerinin stilini oluşturdunuz.

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

... ve aşağıdaki kod bloğundaki örnekle birlikte son elementin sağ bordürünü kaldırdınız.

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

...bunun yerine `:not()` seçicisini kullanarak bu ve benzeri işlemleri daha kısa bir yöntemle halledebilirsiniz.

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

Aşağıdaki demodan bağlantısında bu kullanıma ait olan bir örneğe göz atabilirsiniz.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[Listeye dönün](#table-of-contents)</sup>


### Kullandığınız fontların kullanıcı bilgisayarında yüklü olup olmadığını kontrol edin

Tasarımınızda kullandığınız fontun, kullanıcı bilgisayarında yüklü olup olmadığını kontrol edin. Aşağıdaki kod bloğu, bu kontrolü yapar ve kullanıcı bilgisayarında yüklü olan fontu kullanmanızı sağlar. Ayrıca bu bir performans arttırıcı bir tekniktir.

```css
@font-face {
  font-family: "Dank Mono";
  src:
    /* Full name */
    local("Dank Mono"),
    /* Postscript name */
    local("Dank Mono"),
    /* Otherwise, download it! */
    url("//...a.server/fonts/DankMono.woff");
}

code {
  font-family: "Dank Mono", system-ui-monospace;
}
```

Bu tekniğe dair bir örneğe yandaki bağlantıdan ulaşabilirsiniz. [demo](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[Listeye dönün](#table-of-contents)</sup>

### Body tag'ine bir `line-height` değeri atayın

Her bir element için `line-height` değeri belirtmenize gerek yok. Bunun yerine tasarımınızda kullandığınız genel bir `line-height` değerini `body` elementine ekleyebilirsiniz.

```css
body {
  line-height: 1.5;
}
```

Bu yolla metinsel elementlerin `line-height` değerini `body` özelliklerinden kalıtımla almasını sağlayabilirsiniz.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[Listeye dönün](#table-of-contents)</sup>


### Form elementlerinin `:focus` durumu için bir stil tanımlayın

Kullanıcıların klavye hareketlerini ayırt edebilmesi için form elementlerinin `focus` durumundaki stilleri önemlidir. Form elementlerinin `focus` durumlarını stillendirerek daha iyi bir kullanıcı deneyimi elde etmiş olursunuz. Ayrıca tarayıcılar arası farklılıkların dışında bir stile sahip olursunuz.

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

<sup>[Listeye dönün](#table-of-contents)</sup>


### Herhangi bir nesneyi dikey olarak ortalamanın yolu

Korkmayın! Bu kara bir büyü değil. HTML elementlerini *gerçekten* dikey olarak ortalayabilirsiniz. Örneğin bunu flexbox kullanarak yapabilirsiniz...

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

...bunu CSS Grid ile de yapabilirsiniz:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```

Herhangi birşeyi ortalamak mı istiyorsunuz? Dikey, yatay... herhangi bir yönde, herhangi bir zamanda, herhangi bir yerde? CSS-Tricks bütün bunlara cevap veren güzel bir yazıyı içeriyor. [a nice write-up](https://css-tricks.com/centering-css-complete-guide/)

**Not:** IE11'de bu konuyla ilgili bir bug var. Detaylı bilgi almak için [buggy behavior](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items)

#### [Demo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[Listeye dönün](#table-of-contents)</sup>


### Virgülle ayrılmış ögeler listesi

Liste ögelerini daha gerçekçi göstermek için virgülle ayrılma yöntemini kullanabilirsiniz.

```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Ayrıca dikkat ettiyseniz, son liste ögesinden sonra gelecek olan virgülü kaldırmak için CSS kodumuzda `:not()` seçicisini kullandık. Yukarıdaki örneklerden birinde bundan bahsetmiştik.

**Not:** Bu eknik erişilebilirlik açısından ideal olmayabilir.

#### [Demo](https://markheath.net/post/css-comma-separated-list)

<sup>[Listeye dönün](#table-of-contents)</sup>

### Aynı türdeki birden fazla elementi stillendirmek için negatif değerli `nth-child` seçicisini kullanın

Örneğin; 6 elemanlı bir listeniz olduğunu düşünelim. Bunlardan ilk üçünü gösterip, diğerlerini gizlemek için aşağıdaki kod bloğunu kullanabiliriz.
...önce bütün elementleri gizleyelim. 

```css
li {
  display: none;
}

...şimdi aşağıda ilk üç liste ögesini görünür hale getirelim.

/* ilk üç elementi seçer ve onların görüntülenmesini sağlar */
li:nth-child(-n+3) {
  display: block;
}
```

Ya da daha önceki örneklerde de incelediğimiz `:not()` seçicisini kullanarak tek seferde istediğimize ulaşabilirz. [`:not()` seçicisini kullanmak](#use-not-to-applyunapply-borders-on-navigation)

```css
/* ilk üç element dışındaki bütün elementleri seçer ve onların görüntülenmesini engeller */
li:not(:nth-child(-n+3)) {
  display: none;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[Listeye dönün](#table-of-contents)</sup>


### İkonlar için SVG kullanın

İkonlarınızı tasarımınıza eklerken SVG kullanmak için herhangi bir engeliniz yok.

```css
.logo {
  background: url("logo.svg");
}
```

SVG türündeki grafikler, problemsiz bir şekilde yeniden boyutlandırılabilir ve tüm çözünürlüklere uyum sağlayabilir. Tüm modern tarayıcılar tarafından da desteklenmektedir.

**Not:** 
**Note:** If you have SVG icon-only buttons for sighted users and the SVG fails to load, this will help maintain accessibility:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[Listeye dönün](#table-of-contents)</sup>


### * + * seçicisini kullanın. (Lobotomized Owl Selector)

Anlaşılması zor olabilir ancak en geniş kapsamlı CSS seçicisi (`*`) ile birlikte komşu element seçicisini (`+`) kullanmak CSS kodunuzun etkinliğini oldukça arttıracaktır.

```css
* + * {
  margin-top: 1.5em;
}
```

Bu örnekte, HTML dökümanınızda bir diğerini bütün elementler `margin-top: 1.5em` değerini alacaktır.

Bu örnek hakkında daha fazla bilgi alabilmek için [Heydon Pickering tarafından yazılan makaleyi] okuyabilirsiniz. (http://alistapart.com/article/axiomatic-css-and-lobotomized-owls)

#### [Demo](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[Listeye dönün](#table-of-contents)</sup>


### `max-height` özelliğini kullanarak akordeon efekti yapabilirsiniz

Sadece CSS özelliklerini kullanarak akordeon efekti yapabilirsininiz. Bu efekti slide-up / slide-down terimleri ile de anlatabiliriz.
Normalde jQuery vb. bir JavaScript kütüphanesi ile yapabileceğimiz bir animasyonu, sadece CSS özelliklerini kullanarak nasıl yapacağımıza bir göz atalım.

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

Yukarıdaki CSS class'ını yazdığımız elementin yüksekliği, hover durumunda kendisine atanmış olan `max-height` değerine genişleyecek ve bunun sonucunda görsel olarak slide-up / slide-down animasyonunu elde etmiş olacağız.

Bununla ilgili bir örnek için David Walsh'in yazısına göz atabilirsiniz.

#### [Demo](https://davidwalsh.name/css-slide)

<sup>[Listeye dönün](#table-of-contents)</sup>


### Eşit Ölçülü Tablo Hücreleri

CSS'te tablolarla çalışmak çok zor olabilir. Bu zorluğu `table-layout: fixed` ile aşabilirsiniz. Bu özellik, tablonuzdaki hücrelerin her satırda farklı bir boyut almasını engeller ve bütün tablo hücreleriniz birbirleriyle eşit boyutlara sahip olur. Aynı zamanda bu özellik atamasıyla birlikte tarayıcıların algoritmaları gereği tablo hücrelerinin genişliğinin hesaplanmasına gerek kalmayacağı için, tablolarınız daha hızlı render edilir ve kullanıcıya gösterilir.

```css
.calendar {
  table-layout: fixed;
}
```

Bu konudaki bir örnek için aşağıdaki bağlantıya tıklayabilirsiniz.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[Listeye dönün](#table-of-contents)</sup>


### Flexbox kullanarak, nesnelerin margin değerini belirlemenin zorluğundan kurtulun

When working with column gutters you can get rid of `nth-`, `first-`, and `last-child` hacks by using flexbox's `space-between` property:
Elementler arası boşluklara çalışırken `nth-`, `first-`, `last-child` vb. seçicilere boğulabilirsiniz. Ancak flexbox ile bunu aşmak çok kolay. Flexbox sahip olduğu spaces-between, space-around, space-evenly modları sizleri hiç margin değerleriyle uğraştırmadan nesneler arası eşit boşluklar ayarlamanıza yarar.

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Yukarıdaki örnekte .person sınıfının atandığı elementler içinde yer aldıkları container'a eşit boşluklarla dağıtılacakardır.

<sup>[Listeye dönün](#table-of-contents)</sup>


### Metin girilmemiş linkler Use Attribute Selectors with Empty Links

Hedef adresi atanmış ancak herhangi bir metinle belirtilmemiş linkleri stillendirin.
Örneğin elinizde `<a href="https://goole.com"></a>` şeklinde bir bağlantınızın var olduğunu düşünelim. Bu bağlantı HTML dökümanınızda yer alacaktır ancak kullanıcılarınız tarafından görüntülenemeyecektir. Aşağıdaki CSS kodu ile bu türdeki bütün linklerinizi tek seferde stillendirebilir ve görünür hale getirebilirsiniz.

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Çok kullanışlı bir yöntem değil mi ?

#### [Demo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[Listeye dönün](#table-of-contents)</sup>


### Standart linkleri stillendirin 

Standart halde bulunan linklerinizi stillendirin. 
Add a style for "default" links:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Bu linkler genelde CMS ile hazırlanmış içeriklerde bulunurlar ve herhangi bir class ataması, stil ataması yapamadığınız linklerdir. Yukarıdaki örnek sayesinde bu linkler tasarım bütünlüğünü bozmadan tasarımınızın birer parçası olacaklardır.

<sup>[Listeye dönün](#table-of-contents)</sup>


### Gerçel Oranlı Kutular

Gerçel ölçülü bir kutu oluşturmak için tek yapmanız gereken kapsayıcınıza üst ya da alt taraftan bir padding değeri atamanızdır.
To create a box with an intrinsic ratio, all you need to do is apply top or bottom padding to a div:

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

Yüzde 20'lik padding değeri, kutunuzun yüksekliğini, kendisine ait genişliğin yüzde 20'sine eşitleyecektir. Ekran çözünürlüğü, tuval boyutu ne olursa olsun kutu, 5'e 1 oranında ölçüye sahip olacaktır. Atayacağınız padding değerini değiştirerek farklı oranlara ulaşabilirsiniz.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[Listeye dönün](#table-of-contents)</sup>


### Kaynağına ulaşılamayan resimleri stillendirin

Kaynağına ulaşılmayan, görüntülenmeyen resimleri birkaç satır CSS ile estetik açıdan daha hoş bir hale getirebilirsiniz. Bu kullanıcılar için daha kabul edilebilir bir durumdur.

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

Şimdi pseudo seçicilerle kullanıcılarımıza bir mesaj gösterelim ve resmin bağlantısını bu mesaja iliştirelim.

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

[Ire Aderinokun]'dan bu konuyla ilgili daha fazla şey öğrenebilirsiniz. (https://github.com/ireade/)'s [orijinal kaynak](http://bitsofco.de/styling-broken-images/).

<sup>[Listeye dönün](#table-of-contents)</sup>


### Global yazı boyutu için `rem` nesnelere özel yazı boyutu için `em` ölçülerini kullanın

Yazı tipinizin taban boyutunu belirledikten sonra metinsel elementlerin yazı tipi boyutunu belirlemek için `em` birimini kullanın.

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Sonrasında HTML elementleri için yazı tipi boyutunuzu belirlemek için `rem` birimini kullanın.

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Artık tasarımınız, stillendirme açısından daha modüler, daha esnek ve daha sürdürülebilir hale geldi.

<sup>[Listeye dönün](#table-of-contents)</sup>


### Sesi açık halde otomatik olarak oynayan videoları gizleyin

Sayfanız yüklendiğinde otomatik oynayan videolarla kullanıcılarınızı boğmayın. Otomatik oynatılan videonun sesi açıksa, o videoyu gizleyin.

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Bir kez daha `:not()` seçicisini kullanarak elde ettiğimiz avantajlara göz atmak için (#use-not-to-applyunapply-borders-on-navigation)

<sup>[Listeye dönün](#table-of-contents)</sup>


### Tasarımınıza göre ölçeklenen yazı boyutu için `:root` seçicisini kullanın

Yazı tipi boyutunuz, duyarlı olmalıdır ve her ekran çözünürlüğüne göre uyumluluk gösterebilimelidir. Tasarımınızın görüntülendiği ekran boyutunun en-boy ölçüleriyle birlikte belirli bir formül çerçevesinde hesaplayarak yazı tipi boyutunuzu duyarlı hale getirebilirsiniz. Bu hesaplamayı `:root` seçicisinde yaparak duyarlı yazı tipi boyutunuzu tüm tasarımınıza yayabilirsiniz.

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Artık `:root` içerisinde belirlenen değere göre `root em - rem` birimini kullanabilirsiniz.

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[Listeye dönün](#table-of-contents)</sup>


### Daha etkili bir mobil kullanım deneyimi için form elementlerinin `font-size` değerini belirleyin

Mobil tarayıcılar, HTML form elementlerine odaklandığınızda, bu elementleri size yakınlaştırırlar. Bunu engellemek için form elementlerinizin `font-size` boş bırakmayın, tasarımınıza uygun bir font boyutu ayarlayın.

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[Listeye dönün](#table-of-contents)</sup>


### Mouse aksiyonlarını kontrol etmek için pointer-events özelliğini kullanın

[pointer-events özelliği](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) dokunmatik ekranlarda mouse aksiyonlarını yönetebilmenize yarar. Örneğin, disabled durumdaki bir butonun dokunmatik ekranlarda da disabled hale getirmek için aşağıdaki örneği kullanabilirsiniz.

```css
.button-disabled {
  opacity: .5;
  pointer-events: none;
}
```

Oldukça basit.

<sup>[Listeye dönün](#table-of-contents)</sup>


### Fazla satır boşluklarını gizleyin

[Harry Roberts'ın belirttiği gibi](https://twitter.com/csswizardry/status/1170835532584235008), bu ipucu CMS kullanıcıları için ekstra satır boşluklarından kurtularak daha düzgün bir metin görünümüne ulaşmasını sağlar.

```css
br + br {
  display: none;
}
```

<sup>[Listeye dönün](#table-of-contents)</sup>


## Tarayıcı Desteği

Bu ipuçları Chrome, Firefox, Safari, Opera, Edge, and IE11 tarayıcılarının güncel versiyonlarında çalışır durumdadır.

<sup>[Listeye dönün](#table-of-contents)</sup>


## Çevirilier

* [简体中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-CN)
* [正體中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-TW)
* [Deutsch](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/de-DE)
* [Español](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/es-ES)
* [Français](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/fr-FR)
* [λληνικά](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/gr-GR)
* [ગુજરાતી](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/gu-IND)
* [Italiano](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/it-IT)
* [日本語](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ja-JP)
* [한국어](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ko-KR)
* [Polskie](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pl-PL)
* [Português do Brasil](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-BR)
* [Português do Europe](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-PT)
* [Русский](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ru-RU)
* [Tiếng Việt](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/vn-VN)
* [Türkçe](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/tr-TR)

<sup>[Listeye dönün](#table-of-contents)</sup>
