# Konvertimet e tipit

Pjesen më të madhe të kohës, operatorët dhe funksionet automatikisht konvertojnë vlerat e dhëna në tipin e duhur.

Për shembull, `alert` automatikisht konverton çdo vlerë në një string për ta shfaqur. Operacionet matematikore konvertojnë vlerat në numra.

Ka raste kur duhet të konvertojmë qartësisht një vlerë në tipin qe presim.

```smart header="Nuk po flasim ende per objektet"
Në këtë kapitull, nuk do të trajtojmë objekte. Për momentin, do të flasim vetëm për primitivet.

Më vonë, pasi të mësojmë për objektet, në kapitullin <info:object-toprimitive> do të shohim si objektet vendosen në vend.
```

## Konvertimi në string

Konvertimi në string ndodh kur kemi nevojë për formën e string-ut të një vlerë.

Per shembull, `alert(value)` e bën për të treguar vlerën.

Ne gjithashtu mund te therasim `String(value)` funksionin per te konvertuar vleren ne string:

```js run
let value = true;
alert(typeof value); // boolean

*!*
value = String(value); // tani vlera eshte nje string "true"
alert(typeof value); // string
*/!*
```

Konvertimi i vargut është kryesisht i dukshëm. Nje `false` behet `"false"`, `null` behet `"null"`, etj.

## Konvertimi ne numra

Konvertimi numerik ndodh automatikisht në funksionet dhe shprehjet matematikore.

Për shembull, kur ndarja `/` zbatohet për jo-numrat:

```js run
alert( "6" / "2" ); // 3, stringjet jane konvertuar ne numra
```

Ne mund të përdorim funksionin `Number(value)` per te konvertuar nje `value` ne nje numer:

```js run
let str = "123";
alert(typeof str); // string

let num = Number(str); // behet nje numer 123

alert(typeof num); // number
```

Konvertimi i qartë zakonisht kërkohet kur lexojmë një vlerë nga një burim i bazuar në string si një formë teksti, por presim që të futet një numër.

Nëse stringu nuk është një numër i vlefshëm, rezultati i një konvertimi të tillë është `NaN`. Për shembull:

```js run
let age = Number("nje string ne vend te nje numri");

alert(age); // NaN, konvertimi deshtoj
```

Rregullat e konvertimit numerik:

| Vlera |  Behet... |
|-------|-------------|
|`undefined`|`NaN`|
|`null`|`0`|
|<code>true&nbsp;ose&nbsp;false</code> | `1` dhe `0` |
| `string` | Hapësirat e bardha nga fillimi dhe fundi hiqen. Nëse stringu është bosh, rezultati është `0`. Përndryshe, numri "lexohet" nga stringu. Nje gabim jep `NaN`. |

Shembull:

```js run
alert( Number("   123   ") ); // 123
alert( Number("123z") );      // NaN (ndodh nje gabim gjate leximit te numrit "z")
alert( Number(true) );        // 1
alert( Number(false) );       // 0
```

Ju lutemi vini re se `null` dhe `undefined` sillen ndryshe këtu: `null` bëhet zero ndërsa `undefined` bëhet `NaN`.

Shumica e operatorëve matematikorë kryejnë gjithashtu një konvertim të tillë, këtë do ta shohim në kapitullin vijues.

## Konvertimi Boolean

Konvertimi Boolean është më i thjeshti.

Ndodh në operacionet logjike (më vonë do të njihemi me testet e kushteve dhe gjëra të ngjashme), por mund të kryhet gjithashtu qartësisht me një thirrje te `Boolean(value)`.

Rregulli i konvertimit:

- Vlerat që janë intuitivisht "bosh", si `0`, një string bosh, `null`, `undefined`, dhe `NaN`, bëhen `false`.
- Vlerat e tjera behen `true`.

Pershembull:

```js run
alert( Boolean(1) ); // true
alert( Boolean(0) ); // false

alert( Boolean("hello") ); // true
alert( Boolean("") ); // false
```

````warn header="Ju lutem vini ri: Nje string me zero `\"0\"` eshte `true`"
Disa gjuhe programimi (si PHP) e trajtojne `"0"` si `false`. Por ne Javascript, nje string qe nuk eshte bosh quhet `true`.

```js run
alert( Boolean("0") ); // true
alert( Boolean(" ") ); // hapesirat, gjithashtu true (cdo string qe nuk eshte bosh quhet true)
```
````

## Permbledhje

The three most widely used type conversions are to string, to number, and to boolean.
Tre konvertimet më të përdorura janë në string, në numër dhe në boolean.

**`Konvertimi ne String`** -- Ndodh kur shfaqim diçka. Mund të realizohet me anë të `String(value)`. Konvertimi në string zakonisht është i qartë për vlerat primitive.

**`Konvertimi numerik`** -- Ndodh ne operacionet matematikore. Mund të realizohet me anë të  `Number(value)`.

Konvertimi ndjek rregullat:

| Vlera |  Do te behet... |
|-------|-------------|
|`undefined`|`NaN`|
|`null`|`0`|
|<code>true&nbsp;/&nbsp;false</code> | `1 / 0` |
| `string` | Stringu lexohet "sic eshte", hapesirat ne fillim dhe ne fund injorohen. Nje string bosh behet `0`. Nje error do te japi `NaN`. |

**`Konvertimi ne Boolean`** -- Ndodh ne operatoret llogjike. Mund të realizohet me anë të `Boolean(value)`.

Ndiqni rregullat:

| Vlera |  Do te behet... |
|-------|-------------|
|`0`, `null`, `undefined`, `NaN`, `""` |`false`|
|cdo vlere tjeter| `true` |

Pjesa më e madhe e këtyre rregullave janë të lehta për t'u kuptuar dhe për t'u mbajtur mend. Një përjashtim i vëmendshëm ku njerëzit zakonisht bëjnë gabime janë:

- `undefined` është `NaN` si numër, jo `0`.
- `"0"` dhe stringjet që përmbajnë vetëm hapësirë si "   " janë të vërteta si boolean.

Objektet nuk trajtohen këtu. Do t'i kthehemi atyre më vonë në kapitullin <info:object-toprimitive>, që është i kushtuar ekskluzivisht objekteve, pasi të mësojmë më shumë për JavaScript-in.