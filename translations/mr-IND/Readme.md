<p align="center">
  <img src="../../assets/img/bulb.svg" width="200" alt="light bulb icon">
</p>

# CSS प्रोटिप्स [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

तुमची CSS कौशल्ये प्रो मध्ये मदत करण्यासाठी टिपांचा संग्रह.

> इतर उत्कृष्ट सूचींसाठी [@sindresorhus](https://github.com/sindresorhus/) ची क्युरेट केलेली [अद्भुत सूची](https://github.com/sindresorhus/awesome/) पहा.

## सामग्री सारणी

* [प्रोटिप्स](#प्रोटिप्स)
* [सपोर्ट](#सपोर्ट)
* [भाषांतरे](#भाषांतरे)


## प्रोटिप्स

1. [CSS रीसेट वापरा](#css-रीसेट-वापरा)
2. [वारस `box-sizing`](#वारस-box-sizing)
3. [सर्व गुणधर्म रीसेट करण्याऐवजी `unset` वापरा](#सर्व-गुणधर्म-रीसेट-करण्याऐवजी-unset-वापरा)
4. [नेव्हिगेशनवर सीमा लागू/अनलागू करण्यासाठी `:not()` वापरा](#नेव्हिगेशनवर-सीमा-लागू-अनलागू-करण्यासाठी-not-वापरा)
5. [फॉन्ट स्थानिक पातळीवर स्थापित केला आहे का ते तपासा](#फॉन्ट-स्थानिक-पातळीवर-स्थापित-केला-आहे-का-ते-तपासा)
6. [`body` मध्ये `line-height` जोडा](#body-मध्ये-line-height-जोडा)
7. [फॉर्म घटकांसाठी `:focus` सेट करा](#फॉर्म-घटकांसाठी-focus-सेट-करा)
8. [उभ्या-मध्यभागी काहीही](#उभ्या-मध्यभागी-काहीही)
9.  [स्वल्पविरामाने विभक्त केलेल्या याद्या](#स्वल्पविरामाने-विभक्त-केलेल्या-याद्या)
10. [नकारात्मक `nth-child` वापरून आयटम निवडा](#नकारात्मक-nth-child-वापरून-आयटम-निवडा)
11. [चिन्हांसाठी SVG वापरा](#चिन्हांसाठी-svg-वापरा)
12. [Lobotomized Owl सिलेक्टर वापरा](#lobotomized-owl-सिलेक्टर-वापरा)
13. [शुद्ध CSS स्लाइडरसाठी `max-height` वापरा](#शुद्ध-css-स्लाइडरसाठी-max-height-वापरा)
14. [समान-रुंदीचे टेबल सेल](#समान-रुंदीचे-टेबल-सेल)
15. [फ्लेक्सबॉक्ससह मार्जिन हॅकपासून मुक्त व्हा](#फ्लेक्सबॉक्ससह-मार्जिन-हॅकपासून-मुक्त-व्हा)
16. [रिक्त लिंकसह विशेषता निवडक वापरा](#रिक्त-लिंकसह-विशेषता-निवडक-वापरा)
17. [शैली "Default" दुवे](#शैली-default-दुवे)
18. [आंतरिक गुणोत्तर बॉक्सेस](#आंतरिक-गुणोत्तर-बॉक्सेस)
19. [शैली तुटलेली प्रतिमा](#शैली-तुटलेली-प्रतिमा)
20. [ग्लोबल साइझिंगसाठी `rem` वापरा; स्थानिक आकारमानासाठी `em` वापरा](#ग्लोबल-साइझिंगसाठी-rem-वापरा-स्थानिक-आकारमानासाठी-em-वापरा)
21. [निःशब्द न केलेले ऑटोप्ले व्हिडिओ लपवा](#निःशब्द-न-केलेले-ऑटोप्ले-व्हिडिओ-लपवा)
22. [लवचिक प्रकारासाठी `:root` वापरा](#लवचिक-प्रकारासाठी-root-वापरा)
23. [उत्तम मोबाइल अनुभवासाठी फॉर्म घटकांवर `font-size` सेट करा](#उत्तम-मोबाइल-अनुभवासाठी-फॉर्म-घटकांवर-font-size-सेट-करा)
24. [माउस इव्हेंट नियंत्रित करण्यासाठी पॉइंटर इव्हेंट वापरा](#माउस-इव्हेंट-नियंत्रित-करण्यासाठी-पॉइंटर-इव्हेंट-वापरा)
25. [अंतर म्हणून वापरल्या जाणार्‍या लाइन ब्रेकवर `display: none` सेट करा](#अंतर-म्हणून-वापरल्या-जाणार्‍या-लाइन-ब्रेकवर-display-none-सेट-करा)
26. [रिक्त HTML घटक लपवण्यासाठी `:empty` वापरा](#रिक्त-html-घटक-लपवण्यासाठी-empty-वापरा)


### CSS रीसेट वापरा

CSS रीसेट विविध ब्राउझरमध्ये शैलीतील घटकांसाठी स्वच्छ स्लेटसह शैली सुसंगतता लागू करण्यात मदत करतात. तुम्ही CSS रीसेट लायब्ररी वापरू शकता जसे की [Normalize](http://necolas.github.io/normalize.css/), _et al._, किंवा तुम्ही अधिक सरलीकृत रीसेट पद्धत वापरू शकता:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

आता घटक मार्जिन आणि पॅडिंगमधून काढून टाकले जातील आणि `box-sizing` तुम्हाला CSS बॉक्स मॉडेलसह लेआउट व्यवस्थापित करू देते.

#### [डेमो](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**नोंद:** तुम्ही खालील [Inherit `box-sizing`](#वारस-box-sizing) टिप फॉलो केल्यास तुम्ही तुमच्या CSS रीसेटमध्ये `बॉक्स-साइजिंग` गुणधर्म समाविष्ट न करण्याचे निवडू शकता.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### वारस `box-sizing`

`box-sizing` ला `html` वरून वारसा मिळू द्या:

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

हे प्लगइन्समध्ये किंवा इतर वर्तनाचा लाभ घेणाऱ्या इतर घटकांमध्ये `box-sizing` बदलणे सोपे करते.

#### [डेमो](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### सर्व गुणधर्म रीसेट करण्याऐवजी `unset` वापरा

घटकाचे गुणधर्म रीसेट करताना, प्रत्येक वैयक्तिक गुणधर्म रीसेट करणे आवश्यक नाही:

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

तुम्ही `all` शॉर्टहँड वापरून घटकाचे सर्व गुणधर्म निर्दिष्ट करू शकता. मूल्य `unset` वर सेट केल्याने घटकाचे गुणधर्म त्यांच्या प्रारंभिक मूल्यांमध्ये बदलतात:

```css
button {
  all: unset;
}
```

**नोंद:** IE11 मध्ये `all` आणि `unset` शॉर्टहँड समर्थित नाही.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### नेव्हिगेशनवर सीमा लागू/अनलागू करण्यासाठी `:not()` वापरा


सीमेवर टाकण्याऐवजी...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

...आणि नंतर शेवटचा घटक काढून टाकणे...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```

... फक्त तुम्हाला हव्या असलेल्या घटकांवर लागू करण्यासाठी `:not()` स्यूडो-क्लास वापरा:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

येथे, CSS सिलेक्टर हे वाचले जाते जसे एक मनुष्य त्याचे वर्णन करेल.

#### [डेमो](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### फॉन्ट स्थानिक पातळीवर स्थापित केला आहे का ते तपासा

एखादा फॉन्ट दूरस्थपणे आणण्यापूर्वी तो स्थानिक पातळीवर स्थापित केला आहे का ते तुम्ही तपासू शकता, ही एक चांगली कामगिरी टिप आहे.

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

हा प्रोटिप आणि [डेमो](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### `body` मध्ये `line-height` जोडा

तुम्हाला प्रत्येक `<p>`, `<h*>`, _et al_ मध्ये `line-height` जोडण्याची आवश्यकता नाही. स्वतंत्रपणे त्याऐवजी, ते `body`मध्ये जोडा:

```css
body {
  line-height: 1.5;
}
```

अशा प्रकारे मजकूर घटक `body` मधून सहज मिळू शकतात.

#### [डेमो](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### फॉर्म घटकांसाठी `:focus` सेट करा

पृष्ठावर कीबोर्ड इव्हेंट कुठे जातात हे निर्धारित करण्यासाठी दृष्टीक्षेप असलेले कीबोर्ड वापरकर्ते फोकसवर अवलंबून असतात. ब्राउझरच्या डीफॉल्ट अंमलबजावणीपेक्षा फॉर्म घटकांवर लक्ष केंद्रित करा आणि सुसंगत करा:

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

#### [डेमो](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### उभ्या-मध्यभागी काहीही

नाही, ही काळी जादू नाही, तुम्ही खरोखर घटकांना अनुलंब मध्यभागी ठेवू शकता. तुम्ही हे flexbox सह करू शकता...

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

...आणि CSS ग्रिडसह:

```css
body {
  display: grid;
  height: 100vh;
  margin: 0;
  place-items: center center;
}
```



दुसरे काहीतरी केंद्र करू इच्छिता? अनुलंब, आडवे...काहीही, कधीही, कुठेही? हे सर्व करण्यासाठी CSS-ट्रिक्समध्ये [छान लेखन](https://css-tricks.com/centering-css-complete-guide/) आहे.

**नोंद:** IE11 मध्ये फ्लेक्सबॉक्ससह काही [बग्गी वर्तन](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) पहा .

#### [डेमो](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### स्वल्पविरामाने विभक्त केलेल्या याद्या

सूची आयटम वास्तविक, स्वल्पविरामाने विभक्त केलेल्या सूचीसारखे बनवा:
```css
ul > li:not(:last-child)::after {
  content: ",";
}
```


`:not()` स्यूडो-क्लास वापरा आणि शेवटच्या आयटममध्ये स्वल्पविराम जोडला जाणार नाही.

**नोंद:** ही टीप प्रवेशयोग्यतेसाठी, विशेषत: स्क्रीन वाचकांसाठी आदर्श असू शकत नाही. आणि ब्राउझरमधून कॉपी/पेस्ट करणे CSS-व्युत्पन्न सामग्रीसह कार्य करत नाही. सावधानपूर्वक पुढे जा.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### नकारात्मक `nth-child` वापरून आयटम निवडा

1 ते n आयटम निवडण्यासाठी CSS मध्ये नकारात्मक `nth-child` वापरा.

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```

किंवा, तुम्ही आधीच [`:not()` वापरणे](#use-not-to-applyunapply-borders-on-navigation) बद्दल थोडेसे शिकले असल्याने, प्रयत्न करा:

```css
/* select all items except the first 3 and display them */
li:not(:nth-child(-n+3)) {
  display: block;
}
```

#### [डेमो](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### चिन्हांसाठी SVG वापरा


चिन्हांसाठी SVG न वापरण्याचे कोणतेही कारण नाही:

```css
.logo {
  background: url("logo.svg");
}
```

SVG सर्व रिझोल्यूशन प्रकारांसाठी चांगले स्केल करते आणि सर्व ब्राउझरमध्ये समर्थित आहे [IE9 वर परत](http://caniuse.com/#search=svg). तुमच्या .png, .jpg, किंवा .gif-jif-whatev फायली काढून टाका.

**नोंद:** तुमच्याकडे दिसलेल्या वापरकर्त्यांसाठी SVG आयकॉन-ओन्ली बटणे असल्यास आणि SVG लोड करण्यात अयशस्वी झाल्यास, हे प्रवेशयोग्यता राखण्यात मदत करेल:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### Lobotomized Owl सिलेक्टर वापरा

त्याचे नाव विचित्र असू शकते परंतु सार्वत्रिक सिलेक्टर (`*`) समीपच्या सिबलिंग सिलेक्टरसह (`+`) वापरल्याने एक शक्तिशाली CSS क्षमता प्रदान केली जाऊ शकते:

```css
* + * {
  margin-top: 1.5em;
}
```


या उदाहरणात, दस्तऐवजाच्या प्रवाहातील सर्व घटक जे इतर घटकांचे अनुसरण करतात त्यांना `margin-top: 1.5em` प्राप्त होईल.

"लोबोटोमाइज्ड उल्लू" निवडकर्त्याबद्दल अधिक माहितीसाठी, *ए लिस्ट अपार्ट* वर [हेडॉन पिकरिंगची पोस्ट](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) वाचा.

#### [डेमो](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### शुद्ध CSS स्लाइडरसाठी `max-height` वापरा

ओव्हरफ्लो लपवून `max-height` वापरून फक्त-सीएसएस स्लाइडर लागू करा:

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

घटक होव्हरवर `max-height` मूल्यापर्यंत विस्तृत होतो आणि ओव्हरफ्लोच्या परिणामी स्लाइडर प्रदर्शित होतो.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### समान-रुंदीचे टेबल सेल

टेबल काम करण्यासाठी एक वेदना असू शकते. सेल समान रुंदीवर ठेवण्यासाठी `table-layout: fixed` वापरून पहा:

```css
.calendar {
  table-layout: fixed;
}
```

वेदना-मुक्त टेबल लेआउट.
#### [डेमो](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### फ्लेक्सबॉक्ससह मार्जिन हॅकपासून मुक्त व्हा

कॉलम गटरसह काम करताना फ्लेक्सबॉक्सच्या `space-between` गुणधर्माचा वापर करून तुम्ही `nth-`, `first-` आणि `Last-child` हॅकपासून मुक्त होऊ शकता:

```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

आता स्तंभ गटर नेहमी समान अंतरावर दिसतात.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### रिक्त लिंकसह विशेषता निवडक वापरा

जेव्हा `<a>` घटकामध्ये मजकूर मूल्य नसते परंतु `href` विशेषतामध्ये लिंक असते तेव्हा दुवे प्रदर्शित करा:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

ते खूपच सोयीचे आहे.

**नोंद:** 
ही टीप प्रवेशयोग्यतेसाठी, विशेषत: स्क्रीन वाचकांसाठी आदर्श असू शकत नाही. आणि ब्राउझरमधून कॉपी/पेस्ट करणे CSS-व्युत्पन्न सामग्रीसह कार्य करत नाही. सावधानपूर्वक पुढे जा.

#### [डेमो](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### शैली "Default" दुवे

"default" दुव्यांसाठी एक शैली जोडा:
```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

आता CMS द्वारे समाविष्ट केलेल्या लिंक्स, ज्यात सामान्यतः `class` विशेषता नसते, त्यांना सामान्यपणे कॅस्केड प्रभावित न करता एक वेगळेपण असेल.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### आंतरिक गुणोत्तर बॉक्सेस


अंतर्गत गुणोत्तरासह बॉक्स तयार करण्यासाठी, तुम्हाला फक्त div वर शीर्ष किंवा खालचे पॅडिंग लागू करावे लागेल:

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

पॅडिंगसाठी 20% वापरल्याने बॉक्सची उंची त्याच्या रुंदीच्या 20% इतकी होते. व्ह्यूपोर्टची रुंदी काहीही असो, चाइल्ड डिव्ह त्याचे गुणोत्तर (100% / 20% = 5:1) ठेवेल.

#### [डेमो](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### शैली तुटलेली प्रतिमा

तुटलेल्या प्रतिमा थोड्या CSS सह सौंदर्यदृष्ट्या-आनंददायक बनवा:

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


आता वापरकर्ता संदेश आणि तुटलेल्या प्रतिमेचा URL संदर्भ प्रदर्शित करण्यासाठी स्यूडो-एलिमेंट नियम जोडा:

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

[Ire Aderinokun](https://github.com/ireade/) च्या [मूळ पोस्ट](http://bitsofco.de/styling-broken-images/) मध्ये या पॅटर्नच्या शैलीबद्दल अधिक जाणून घ्या.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### ग्लोबल साइझिंगसाठी `rem` वापरा; स्थानिक आकारमानासाठी `em` वापरा

मूळ फॉन्ट आकार (`html { font-size: 100%; }`) वर सेट केल्यानंतर, मजकूर घटकांसाठी फॉन्ट आकार `em` वर सेट करा:

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

नंतर मॉड्यूलसाठी फॉन्ट-आकार `rem` वर सेट करा:

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

आता प्रत्येक मॉड्युल कंपार्टमेंटलाइज्ड आणि स्टाइलसाठी सोपे, अधिक देखरेख करण्यायोग्य आणि लवचिक बनले आहे.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### निःशब्द न केलेले ऑटोप्ले व्हिडिओ लपवा

सानुकूल वापरकर्ता स्टाइलशीटसाठी ही एक उत्तम युक्ती आहे. पृष्‍ठ लोड केल्‍यावर आपोआप प्ले होणार्‍या व्‍हिडिओमध्‍ये आवाजासह वापरकर्ता ओव्हरलोड करणे टाळा. जर आवाज म्यूट केला नसेल, तर व्हिडिओ दाखवू नका:

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

पुन्हा एकदा, आम्ही वापरण्याचा फायदा घेत आहोत [`:not()`](#use-not-to-applyunapply-borders-on-navigation) pseudo-class.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### लवचिक प्रकारासाठी `:root` वापरा

प्रतिसादात्मक लेआउटमधील प्रकार फॉन्ट आकार प्रत्येक व्ह्यूपोर्टसह समायोजित करण्यास सक्षम असावा. तुम्ही `:root` वापरून व्ह्यूपोर्ट उंची आणि रुंदीच्या आधारावर फॉन्ट आकार मोजू शकता:

```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

आता तुम्ही `:root` द्वारे मोजलेल्या मूल्यावर आधारित `root em` युनिट वापरू शकता:

```css
body {
  font: 1rem/1.6 sans-serif;
}
```

#### [डेमो](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### उत्तम मोबाइल अनुभवासाठी फॉर्म घटकांवर `font-size` सेट करा

जेव्हा `<select>` ड्रॉप-डाउन टॅप केले जाते तेव्हा मोबाइल ब्राउझर (iOS Safari, _et al_) HTML फॉर्म घटकांवर झूम इन करण्यापासून टाळण्यासाठी, निवडक नियमात `font-size` जोडा:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### माउस इव्हेंट नियंत्रित करण्यासाठी पॉइंटर इव्हेंट वापरा

[Pointer events](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) तुम्हाला माऊस स्पर्श करत असलेल्या घटकाशी कसा संवाद साधतो हे निर्दिष्ट करू देते. बटणावर डीफॉल्ट पॉइंटर इव्हेंट अक्षम करण्यासाठी, उदाहरणार्थ:

```css
button:disabled {
  opacity: .5;
  pointer-events: none;
}
```

हे इतके सोपे आहे.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>

 
#### अंतर म्हणून वापरल्या जाणार्‍या लाइन ब्रेकवर `display:none` सेट करा

[हॅरी रॉबर्ट्सने निदर्शनास आणल्याप्रमाणे](https://twitter.com/csswizardry/status/1170835532584235008), हे CMS वापरकर्त्यांना अंतरासाठी अतिरिक्त लाइन ब्रेक वापरण्यापासून प्रतिबंधित करण्यात मदत करू शकते:

```css
br + br {
  display: none;
}
```

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


### रिक्त HTML घटक लपवण्यासाठी `:empty` वापरा

तुमच्याकडे HTML घटक रिकामे असल्यास, उदा., सामग्री एकतर CMS द्वारे सेट करणे बाकी आहे किंवा डायनॅमिकली इंजेक्ट केलेले (उदा. `<p class="error-message"></p>`) आणि त्यामुळे अवांछित जागा तयार होत आहे. तुमच्या लेआउटवर, लेआउटवरील घटक लपवण्यासाठी `:empty` स्यूडो-क्लास वापरा.

```css
:empty {
  display: none;
}
```

**नोंद:** लक्षात ठेवा की व्हाइटस्पेस असलेले घटक रिक्त मानले जात नाहीत, e.g., `<p class="error-message"> </p>`.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


## सपोर्ट

Chrome, Firefox, Safari, Opera, Edge आणि IE11 च्या वर्तमान आवृत्त्या.

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>


## भाषांतरे

**नोंद:** अनुवादित टिपांची वाढती यादी राखण्यासाठी माझ्याकडे कमी वेळ उपलब्ध आहे; नवीन टिप जोडण्यासाठी डझनहून अधिक भाषांतरांसह ते समाविष्ट करणे आवश्यक आहे. त्या कारणास्तव, अनुवादित README फाइल्समध्ये मुख्य README फाइलवर सूचीबद्ध केलेल्या सर्व टिपा समाविष्ट नसतील.

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

<sup>[सामग्री सारणीकडे परत](#सामग्री-सारणी)</sup>
