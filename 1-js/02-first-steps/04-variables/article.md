# Variablat

Në shumicën e rasteve, një aplikacion JavaScript ka nevojë të punojë me informacion. Ja dy shembuj:
1. Një dyqan online -- informacioni mund të përfshijë produktet që shiten dhe një shportë blerjesh.
2. Një aplikacion chati -- informacioni mund të përfshijë përdoruesit, mesazhet dhe shumë gjëra të tjera.


Variablat përdoren për të ruajtur këtë informacion.

## Nje variabel

Nje [variable](https://en.wikipedia.org/wiki/Variable_(computer_science)) eshte nje "named storage" per te dhenat. Ne mund të përdorim variablat për të ruajtur produkte, vizitorë dhe të dhëna të tjera.

Për të krijuar një variabël në JavaScript, përdorni fjalën kyçe `let`.

The statement below creates (in other words: *declares*) a variable with the name "message":
Deklarata më poshtë krijon (me fjalë te tjera: *deklaron*) një variabël me emrin "message":


```js
let message;
```

Tani, mund të vendosim disa të dhëna në të duke përdorur operatorin e caktimit `=`:

```js
let message;

*!*
message = 'Pershendetje'; // ruan stringun
*/!*
```

Stringu është tani ruajtur në hapësirën e memorjes që lidhet me variablën. Ne mund ta aksesojme atë duke përdorur emrin e variablës:


```js run
let message;
message = 'Pershendetje!';

*!*
alert(message); // tregon përmbajtjen e variablës
*/!*
```

Për të qenë të qartë, mund të kombinojmë deklarimin e variablës dhe caktimin në një rresht të vetëm:

```js run
let message = 'Pershendetje!'; // Definojme variablen dhe i japim nje vlere

alert(message); // Pershendetje!
```

Ne gjithashtu mund të deklarojmë disa variabla në një rresht:

```js no-beautify
let user = 'Xhoni', age = 25, message = 'Pershendetje';
```

Kjo mund të duket më e shkurtër, por nuk e rekomandojmë. Për hir të lexueshmërisë më të mirë, ju lutemi përdorni një rresht të vetëm për çdo variabël.

Varianta me shumë rreshta është pak më gjatë, por më e lehtë për tu lexuar:

```js
let user = 'Xhoni';
let age = 25;
let message = 'Pershendetje';
```

Disa persona gjithashtu përdorin stilin me shumë rreshta për të definuar disa variabla:

```js no-beautify
let user = 'Xhoni',
  age = 25,
  message = 'Pershendetje';
```

...Ose madje në stilin "comma-first":

```js no-beautify
let user = 'Xhoni'
  , age = 25
  , message = 'Pershendetje';
```

Teknikisht, të gjithë këto variante bëjnë të njëjtën gjë. Prandaj, është çështje e preferencës personale dhe estetikës se cili stil preferohet. 


````smart header="`var` instead of `let`"
Në skriptet më të vjetra, mund të hasni edhe fjalë kyçe të tjera: `var` në vend të `let`:

```js
*!*var*/!* message = 'Pershendetje';
```

Fjala kyçe `var` është  *pothuajse* e njëjtë me `let`. Ajo gjithashtu deklaron një variabël, por në një mënyrë pak të ndryshme, "old-school".

Ka dallime të hollësishme mes `let` dhe `var`, por ato nuk kanë rëndësi për ne ende. Do t'i trajtojmë ato në detaje në kapitullin <info:var>.
````

## Një analogji nga jeta reale

Mund të kuptojmë lehtësisht konceptin e një "variabli" nëse e imagjinojmë atë si një "kuti" për të dhënat, me një etiketë me emër unik mbi të.

Për shembull, variabla `message`  mund të paraqitet si një kuti me etiketën `"message"` dhe me vlerën "Përshëndetje!" në brendësi:

![](variable.svg)

Mund të vendosim çdo vlerë në këtë kuti.

Mund ta ndryshojmë atë aq herë sa të dëshirojmë:
```js run
let message;

message = 'Pershendetje!';

message = 'Bota!'; // vlera ndryshoj

alert(message);
```

Kur vlera ndryshohet, të dhënat e mëparshme largohen nga variabla:

![](variable-change.svg)

Mund të deklarojmë edhe dy variabla dhe të kopjojmë të dhënat nga njëra në tjetrën.

```js run
let hello = 'Pershendetje bota!';

let message;

*!*
// kopjo 'Pershendetje bota' nga hello ne message
message = hello;
*/!*

// tashme dy variabla mbajnë të njëjtën të dhënë.
alert(hello); // Pershendetje bota!
alert(message); // Pershendetje bota!
```

````warn header="Deklarimi i një variabli dy herë shkakton një gabim."
Një variabël duhet të deklarohet vetëm një herë.

Një deklarim i përsëritur i të njëjtit variabël është një gabim:

```js run
let message = "Ky";

// perseritja e  'let' na sjell nje gabim
let message = "Kjo"; // SyntaxError: 'message' has already been declared
```
Prandaj, duhet ta deklarojmë një variabël një herë dhe pastaj të referohemi në të pa përdorur `let` përsëri.
````

```smart header="Gjuhët funksionale"
Është interesante të theksohet se ekzistojnë gjuhë programimi [funksionale](https://en.wikipedia.org/wiki/Functional_programming), si [Scala](http://www.scala-lang.org/) ose [Erlang] (http://www.erlang.org/) që nuk e lejojne ndryshimin e vlerave të variablave.

Në këto gjuhë, kur një vlerë ruhet "në kuti", ajo qëndron aty përherë. Nëse duhet të ruajmë diçka tjetër, gjuha na detyron të krijojmë një kuti të re (të deklarojmë një variabël të re). Nuk mund të ri-përdorim të vjetrën.

Megjithëse mund të duket pak e çuditshme në shikim të parë, këto gjuhë janë mjaft të afta për projekte serioze. Për më tepër, ka fusha si llogaritjet paralele ku ky kufizim jep përfitime të caktuara. Studimi i një gjuhe të tillë (edhe nëse nuk planifikoni ta përdorni së shpejti) rekomandohet për të zgjeruar menyren e te menduarit.
```

## Emërtimi i variablave [#variable-naming]

Ekzistojnë dy kufizime për emrat e variablave në JavaScript:

1. Emri duhet të përmbajë vetëm shkronja, shifra ose simbolet `$` dhe `_`.
2. Karakteri i parë nuk duhet të jetë një shifër.

Shembuj të emrave të vlefshëm:

```js
let userName;
let test123;
```

Kur emri përmban shumë fjalë, zakonisht përdoret [camelCase](https://en.wikipedia.org/wiki/CamelCase). Kjo do të thotë: fjalët shkojnë njëra pas tjetrës, secila fjalë përveç se së pari fillon me një shkronjë të madhe: `myVeryLongName`.

Ajo që është interesante -- shenja e dollarit `'$'` dhe nënvizimi `'_'` mund të përdoren gjithashtu në emra. Janë simbole të rregullta, si shkronjat, pa ndonjë kuptim të veçantë.

Këta emra janë të vlefshëm:

```js run untrusted
let $ = 1; // deklaroi një variabël me emrin "$"
let _ = 2; // dhe tani një variabël me emrin "_"

alert($ + _); // 3
```

Shembuj të emrave të gabuar të variablave:

```js no-beautify
let 1a; // nuk mund të fillojë me një shifër

let my-name; // vizat '-' nuk lejohen në emër
```

```smart header="Ka rëndësi rasti"
Variablat e quajtur "apple" dhe "AppLE" janë dy variabla të ndryshëm.
```

````smart header="Shkronjat jo latine lejohen, por nuk rekomandohen"
Është e mundur të përdoret çdo gjuhë, duke përfshirë shkronjat cirilike apo edhe hieroglifet, si kjo:

```js
let имя = '...';
let 我 = '...';
```

Teknikisht, këtu nuk ka asnjë gabim. Emra të tillë lejohen, por ekziston një konventë ndërkombëtare për përdorimin e anglishtes në emrat e variablave. Edhe nëse po shkruajmë një skenar të vogël, ai mund të ketë një jetë të gjatë përpara. Njerëzit nga vende të tjera mund të kenë nevojë ta lexojnë atë për ca kohë.
````

````warn header="Emrat e rezervuar"
Ekziston një [listë e fjalëve të rezervuara](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords), të cilat nuk mund të përdoren si emra variablash sepse përdoren nga vetë Javascript.

Për shembull: `let`, `class`, `return`, dhe `function` janë të rezervuara.

Kodi më poshtë jep një gabim sintaksor:

```js run no-beautify
let let = 5; // nuk mund të emërojë një variabël "let", gabim!
let return = 5; // gjithashtu nuk mund ta emërtoj "return", gabim!
```
````

````warn header="Një detyrë pa `use strict`"

Normalisht, ne duhet të përcaktojmë një variabël përpara se ta përdorim atë. Por në kohët e vjetra, teknikisht ishte e mundur të krijohej një variabël me një caktim të thjeshtë të vlerës pa përdorur `let`. Kjo ende funksionon tani nëse nuk vendosim `use strict` në skriptet tona për të ruajtur përputhshmërinë me skriptet e vjetra.

```js run no-strict
// Shënim: nuk ka "use strict" në këtë shembull
num = 5; // variabli "num" krijohet nëse nuk ekziston

alert(num); // 5
```

Kjo është një praktikë e keqe dhe do të shkaktonte një gabim në strict mode:

```js
"use strict";

*!*
num = 5; // gabim: num nuk është përcaktuar
*/!*
```
````

## Konstantet

Per te deklaruar nje konstante (variabel e pandryshueshme), perdorim `const` në vend të `let`:

```js
const myBirthday = '18.04.1982';
```

Variablat e deklaruar duke përdorur 'const' quhen "konstante". Ata nuk mund të ricaktohen. Një përpjekje për ta bërë këtë do të shkaktonte një gabim:

```js run
const myBirthday = '18.04.1982';

myBirthday = '01.01.2001'; // gabim, nuk mund të ricaktohet konstantja!
```

Kur një programues është i sigurt se një variabël nuk do të ndryshojë kurrë, ai mund ta deklarojë atë me 'const' për të garantuar dhe komunikuar qartë këtë fakt për të gjithë.

### Konstantet e shkronjave të mëdha

Ekziston një praktikë e përhapur për të përdorur konstante si pseudonime për vlerat e vështira për t'u mbajtur mend që janë të njohura përpara ekzekutimit.

Konstante të tilla emërtohen duke përdorur shkronja të mëdha dhe nënvizime.

Për shembull, le të bëjmë konstante për ngjyrat në të ashtuquajturin format "web" (hexadecimal):

```js run
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...kur na duhet te zgjedhim nje ngjyre
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```

Përfitimet:

- `COLOR_ORANGE` është shumë më e lehtë për t'u mbajtur mend se `"#FF7F00"`.
- Është shumë më e lehtë të shkruash gabim `"#FF7F00"` sesa `COLOR_ORANGE`.
- Kur lexojme kodin, `COLOR_ORANGE` ka me shume kuptim se sa `#FF7F00`.

Kur duhet të përdorim kapitale për një konstante dhe kur duhet ta emërtojmë atë normalisht? Le ta bëjmë të qartë.

Të qenit "konstante" thjesht do të thotë që vlera e kesaj variable nuk ndryshon kurrë. Por ka konstante që njihen para ekzekutimit (si një vlerë heksadecimal për të kuqe) dhe ka konstante që *llogariten* në kohën e ekzekutimit, gjatë ekzekutimit, por nuk ndryshojnë pas caktimit të tyre fillestar.

Për shembull:
```js
const pageLoadTime = /* koha që i duhet një faqe interneti për t'u ngarkuar */;
```

Vlera e `pageLoadTime` nuk dihet para ngarkimit të faqes, kështu që emërtohet normalisht. Por është ende një konstante sepse nuk ndryshon pas caktimit.

Me fjalë të tjera, konstantet e emërtuara me kapital përdoren vetëm si pseudonime për vlerat "hard-coded".

## Emërtoni gjërat siç duhen

Duke folur për variablat, ka edhe një gjë jashtëzakonisht të rëndësishme.

Emri i variables duhet të ketë një kuptim të pastër, të qartë, duke përshkruar të dhënat që ruan.

Emërtimi i variablave është një nga aftësitë më të rëndësishme dhe komplekse në programim. Një vështrim i shpejtë në emrat e variablave mund të zbulojë se cili kod është shkruar nga një fillestar kundrejt një programuesi me përvojë.

Në një projekt real, pjesa më e madhe e kohës harxhohet duke modifikuar dhe zgjeruar një bazë kodi ekzistues në vend që të shkruani diçka krejtësisht të ndarë nga e para. Kur i kthehemi një kodi pasi kemi bërë diçka tjetër për një kohë, është shumë më e lehtë të gjejmë informacione të etiketuara mirë. Ose, me fjalë të tjera, kur variablat kanë emra të mirë.

Ju lutemi kaloni kohë duke menduar për emrin e duhur për një variabël përpara se ta deklaroni atë. Duke vepruar kështu do t'ju shpërblejë me vone.
Disa rregulla të mira për t'u ndjekur janë:

- Përdorni emra të lexueshëm nga njeriu si 'perdorues' ose 'shportaIme'.
- Qëndroni larg shkurtesave ose emrave të shkurtër si `a`, `b`, `c`, përveç nëse e dini vërtet se çfarë po bëni.
- Bëjini emrat maksimalisht përshkrues dhe konciz. Shembuj të emrave të këqij janë "data" dhe "value". Emra të tillë nuk thonë asgjë. Është në rregull t'i përdorësh ato vetëm nëse konteksti i kodit e bën jashtëzakonisht të qartë se cilat të dhëna ose vlerë i referohet variablit.
- Bini dakord për kushtet brenda ekipit tuaj dhe në mendjen tuaj. Nëse një vizitor i faqes quhet "user", atëherë duhet t'i emërtojmë variablat përkatës "currentUser" ose "newUser" në vend të "currentVisitor" ose "newManInTown".

Tingëllon e thjeshtë? Në të vërtetë është, por krijimi i emrave përshkrues dhe konciz të variablave në praktikë nuk është kështu. Shkoni për të.
```smart header="Ripërdorni ose krijoni?"

Dhe shënimi i fundit. Ka disa programues dembelë që, në vend që të deklarojnë variabla të reja, priren të ripërdorin ato ekzistuese.

Si rezultat, variablat e tyre janë si kuti në të cilat njerëzit hedhin gjëra të ndryshme pa ndryshuar etiketat e tyre. Çfarë ka brenda kutisë tani? Kush e di? Duhet të afrohemi dhe të kontrollojmë.

Programues të tillë kursejnë pak në deklarimin e variablave, por humbasin dhjetë herë më shumë në korrigjimin e gabimeve.

Një variabël shtesë është e mirë, jo e keqe.

Minifikuesit dhe shfletuesit modernë JavaScript optimizojnë mjaft mirë kodin, kështu që nuk do të krijojë probleme të performancës. Përdorimi i variablave të ndryshëm për vlera të ndryshme madje mund të ndihmojë motorin të optimizojë kodin tuaj.
```

## Përmbledhje

Ne mund të deklarojmë variabla për të ruajtur të dhënat duke përdorur fjalët kyçe "var", "let" ose "const".

- `let` -- menyra moderne e te deklaruarit nje variabel.
- `var` -- eshte menyra e vjeter e deklarimit te variables. Normalisht, ne nuk e përdorim fare, por do të mbulojmë ndryshimet delikate nga `let` ne kapitullin <info:var>, ne rast se do ju duhet.
- `const` -- eshte si `let`, por vlera e variables nuk ndryshon.

Variablat duhet të emërtohen në një mënyrë që të na lejojë të kuptojmë lehtësisht se çfarë ka brenda tyre.
