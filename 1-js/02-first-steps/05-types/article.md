# Llojet e te dhenave

Një vlerë në JavaScript është gjithmonë e një lloji të caktuar. Për shembull, një varg ose një numër.

Ekzistojnë tetë lloje bazë të të dhënave në JavaScript. Këtu do t'i trajtojmë ato në përgjithësi dhe në kapitujt e ardhshëm do të flasim për secilën prej tyre në detaje.

Ne mund të vendosim çdo lloj në një variabel. Për shembull, një variabel në një moment mund të jetë një string dhe më pas të ruajë një numër:

```js
// nuk ka error
let message = "hello";
message = 123456;
```

Gjuhët e programimit që lejojnë gjëra të tilla, si JavaScript, quhen "të shtypura në mënyrë dinamike", që do të thotë se ekzistojnë lloje të dhënash, por variablat nuk janë të lidhura me asnjë prej tyre.

## Numri

```js
let n = 123;
n = 12.345;
```

Lloji *number* përfaqëson si numrat e plotë(integer) ashtu edhe numrat me presje(flaoting numbers).

Ka shumë veprime për numrat, p.sh. shumëzimi `*`, pjesëtimi `/`, mbledhja `+`, zbritja `-`, e kështu me radhë.

Përveç numrave të rregullt, ekzistojnë të ashtuquajturat "vlera numerike speciale" të cilat gjithashtu i përkasin ketyre llojeve të të dhënave: `Infinity`, `-Infinity` dhe `NaN`.

- `Infinity` perfaqson ne matematike [Infinitin](https://en.wikipedia.org/wiki/Infinity) ∞. Është një vlerë e veçantë që është më e madhe se çdo numër.

    Mund ta marrim si rezultat i pjesëtimit me zero:

    ```js run
    alert( 1 / 0 ); // Infinit
    ```

    Ose thjesht referojuni drejtpërdrejt:

    ```js run
    alert( Infinity ); // Infinit
    ```
- `NaN` përfaqëson një gabim llogaritës. Është rezultat i një operacioni matematikor të pasaktë ose të papërcaktuar, për shembull:

    ```js run
    alert( "not a number" / 2 ); // NaN, një ndarje e tillë është e gabuar
    ```

    `NaN` esht ngjitese. Çdo operacion i mëtejshëm në `NaN` kthen `NaN`:

    ```js run
    alert( "not a number" / 2 + 5 ); // NaN
    ```

    Pra, nëse ka një `NaN` diku në një shprehje matematikore, ajo përhapet në të gjithë rezultatin.

```smart header="Veprimet matematikore janë të sigurta"
Bërja e matematikës është "e sigurt" në JavaScript. Ne mund të bëjmë gjithçka: pjesëtojmë me zero, trajtojmë vargjet jo numerike si numra, etj.

Skripti nuk do të ndalet kurrë me një gabim fatal ("die"). Në rastin më të keq, do të marrim `NaN` si rezultat.
```

Vlerat e veçanta numerike i përkasin formalisht llojit "numër". Sigurisht, ato nuk janë numra në kuptimin e zakonshëm të kësaj fjale.

Do të shohim më shumë si te punojme me numrat në kapitullin <info:number>.

## BigInt

Ne Javascript, lloji "number" nuk mund te perfaqesoje vlera me te medhaja se <code>(2<sup>53</sup>-1)</code> (qe eshte `9007199254740991`), ose me pak se <code>-(2<sup>53</sup>-1)</code> per negativet. Është një kufizim teknik i shkaktuar nga përfaqësimi i tyre i brendshëm.

Për shumicën e qëllimeve kjo është mjaft e mjaftueshme, por ndonjëherë na duhen numra vërtet të mëdhenj, p.sh. për kriptografi ose vula kohore me precizion mikrosekondë.

`BigInt` lloji i te dhenes është shtuar së fundi në gjuhë për të përfaqësuar numra të plotë me gjatësi arbitrare.

Një vlerë `BigInt` krijohet duke shtuar `n` në fund të një numri të plotë:

```js
// "n" në fund do të thotë se është një BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```

Duke qenë se numrat `BigInt` nevojiten rrallë, ne nuk i mbulojmë këtu, por u kushtuam atyre një kapitull të veçantë <info:bigint>. Lexojeni kur ju duhen numra kaq të mëdhenj.


```smart header="Problemet e përputhshmërisë"
Për momentin, `BigInt` suportohet në Firefox/Chrome/Edge/Safari, por jo në IE.
```

Ju mund te kontrolloni [*MDN* BigInt compatibility table](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt#Browser_compatibility) për të ditur se cilat versione të një shfletuesi suportohen.

## String

Një string në JavaScript duhet të rrethohet me thonjëza.

```js
let str = "Pershendetje";
let str2 = 'Thonjezat teke jane ne rregull';
let phrase = `mund të inkorporojë një tjetër ${str}`;
```

Në JavaScript, ekzistojnë 3 lloje thonjezash.

1. Thonjezat dyshe: `"Hello"`.
2. Thonjezat teke: `'Hello'`.
3. Backticks: <code>&#96;Hello&#96;</code>.

Thonjezat e dyshe dhe teke janë thonjëza "të thjeshta". Praktikisht nuk ka asnjë ndryshim midis tyre në JavaScript.

Backticks janë thonjeza me "funksionalitet të zgjeruar". Ato na lejojnë të vendosim variabla dhe shprehje në një string duke i mbështjellë në `${…}`, për shembull:

```js run
let name = "Xhoni";

// bashkojme nje variabel
alert( `Pershendetje, *!*${name}*/!*!` ); // Pershendetje, John!

// vendosim nje veprim
alert( `rezultati eshte *!*${1 + 2}*/!*` ); // rezultati eshte 3
```

Shprehja brenda `${…}` vlerësohet dhe rezultati bëhet pjesë e vargut. Mund të vendosim çdo gjë aty: një variabël si `name` ose një shprehje aritmetike si `1 + 2` ose diçka më komplekse.

Please note that this can only be done in backticks. Other quotes don't have this embedding functionality!
Ju lutemi vini re se kjo mund të bëhet vetëm me backticks. Thonjezat e tjera nuk e kanë këtë funksion të bashkimit!
```js run
alert( "rezultati eshte ${1 + 2}" ); // rezultati eshte ${1 + 2} (thonjazat dyshe nuk bejne asnje gje)
```

Ne do t'i trajtojmë stringjet më hollësisht në kapitullin <info:string>.

```smart header="Nuk ka lloj *character*."
Në disa gjuhë programimi, ekziston një lloj i veçantë "character" për një karakter të vetëm. Për shembull, në gjuhën C dhe në Java quhet "char".

Në JavaScript, nuk ka një lloj të tillë. Ekziston vetëm një lloj: `string`. Një string mund të përbëhet nga zero karaktere (të jetë bosh), një karakter ose shumë prej tyre.
```

## Boolean (llojet llogjike)

Lloji boolean ka vetëm dy vlera: `true` dhe `false`.

This type is commonly used to store yes/no values: `true` means "yes, correct", and `false` means "no, incorrect".
Ky lloj përdoret zakonisht për të ruajtur vlerat po/jo: `true` do të thotë "po, e saktë" dhe `false` do të thotë "jo, e pasaktë".

Për shembull:

```js
let nameFieldChecked = true; // po, fusha e emrit është e kontrolluar
let ageFieldChecked = false; // jo, fusha e moshës nuk është e kontrolluar
```

Vlerat Boolean vijnë gjithashtu si rezultat i krahasimeve:

```js run
let isGreater = 4 > 1;

alert( isGreater ); // true (rezultati i krahasimit është "po")
```
Ne do t'i mbulojmë më thellë booleanet në kapitullin <info:logical-operators>.

## Vlerat "null"

Vlera speciale `null` nuk i përket asnjë prej llojeve të përshkruara më sipër.

Ajo krijon një tip të veçantë të vetëm që përmban vetëm vlerën `null`:

```js
let age = null;
```

Në JavaScript, `null` nuk është një "referencë ndaj një objekti që nuk ekziston" ose një "tregues null" si në disa gjuhë të tjera.

Është thjesht një vlerë e veçantë që përfaqëson "asgjë", "bosh" ose "vlerë të panjohur".

Kodi i mësipërm thotë se `age` është e panjohur.

## Vlerat "undefined"

Vlera speciale `undefined` gjithashtu dallon nga te tjerat. Ajo krijon një tip të veçantë të vetëm, në të njëjtën mënyrë si `null`.

Kuptimi i `undefined` është "vlera nuk është caktuar".

Nëse një variabël është deklaruar, por nuk është caktuar, atëherë vlera e tij është `undefined`.

```js run
let age;

alert(age); // tregon "undefined"
```

Technically, it is possible to explicitly assign `undefined` to a variable:
Teknikisht, është e mundur të caktosh qartësisht vlerën `undefined` në një variabël.

```js run
let age = 100;

// ndryshojme vleren ne undefined
age = undefined;

alert(age); // "undefined"
```

...But we don't recommend doing that. Normally, one uses `null` to assign an "empty" or "unknown" value to a variable, while `undefined` is reserved as a default initial value for unassigned things.
Por ne nuk ju rekomandojmë ta bëni këtë. Normalisht, njehere përdor `null` për t'i caktuar një vlerë "bosh" ose "të panjohur" një variabli, ndërsa `undefined` rezervohet si një vlerë fillestare për gjërat e pacaktuara.

## Objektet dhe Simbolet

Lloji `object` është i veçantë.

Të gjitha llojet e tjera quhen "primitive" sepse vlerat e tyre mund të përmbajnë vetëm një gjë të vetme (qoftë një string, një numër ose çfarëdo qoftë). Në të kundërt, objektet përdoren për të ruajtur koleksione të dhënash dhe entitete më komplekse.

Duke qenë kaq të rëndësishme, objektet meritojnë një trajtim të veçantë. Do t'i trajtojmë më vonë në kapitullin <info:object>, pasi të mësojmë më shumë rreth primitivëve.

Lloji `simbol` përdoret për të krijuar identifikues unik për objekte. Ne duhet ta përmendim atë këtu për të pasurë një pasqyrë të plotë, por gjithashtu do të shtyjmë detajet deri sa të njohim objektet.

## Operatori typeof [#type-typeof]

Operatori `typeof` kthen tipin e argumentit. Është i dobishëm kur dëshirojmë të trajtojmë vlera të ndryshme sipas tipit ose kur dëshirojmë të bëjmë një kontroll të shpejtë.

Ai suporton dy forma të sintaksës:

1. Si nje operator: `typeof x`.
2. Si nje funksion: `typeof(x)`.

Me fjalë të tjera, funksionon me kllapa ose pa to. Rezultati është i njëjtë.

The call to `typeof x` returns a string with the type name:
Thirrja në `typeof x` kthen një string me emrin e tipit:

```js
typeof undefined // "undefined"

typeof 0 // "number"

typeof 10n // "bigint"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

*!*
typeof Math // "object"  (1)
*/!*

*!*
typeof null // "object"  (2)
*/!*

*!*
typeof alert // "function"  (3)
*/!*
```

Tre rreshtat e fundit mund të kenë nevojë për shpjegim shtesë:


1. `Math` është një objekt i integruar që ofron operacione matematikore. Do ta mësojmë në kapitullin <info:number>. Këtu, ai shërben vetëm si një shembull i një objekti.
2. Rezultati i `typeof null` është `object`. Ky është një gabim i njohur zyrtarisht në sjelljen e `typeof`, që vjen nga ditët e para të JavaScript dhe ruhet për kompaktibilitet. Definitivisht, `null` nuk është një `object`. Është një vlerë e veçantë me një lloj më vete.
3. Rezultati i `typeof alert` eshte `"function"`, sepse `alert` eshte nje funksion. Ne do të studiojmë funksionet në kapitujt e ardhshëm ku do të shohim gjithashtu se nuk ka asnjë lloj të veçantë "funksioni" në JavaScript. Funksionet i përkasin llojit të objektit. Por `typeof` i trajton ato ndryshe, duke i kthyer "funksionin"`. Kjo gjithashtu vjen nga ditët e para të JavaScript. Teknikisht, një sjellje e tillë nuk është e saktë, por mund të jetë e përshtatshme në praktikë.

## Permbledhje

Ekzistojnë 8 lloje bazë të të dhënave në JavaScript.

- `number` për numrat e çdo lloji: numër i plotë ose me presje, numrat e plotë janë të kufizuar nga <code>±(2<sup>53</sup>-1)</code>.
- `bigint` është për numra të plotë me gjatësi arbitrare.
- `string` per stringjet. Një string mund të ketë zero ose më shumë karaktere, nuk ka lloj të veçantë me një karakter.
- `boolean` per `true`/`false`.
- `null` per vlerat e panjohura -- një lloj i pavarur që ka një vlerë të vetme `null`.
- `undefined` per vlerat e të papërcaktuara -- një lloj i pavarur që ka një vlerë të vetme `undefined`.
- `object` për struktura më komplekse të të dhënave.
- `symbol` për identifikues unikë.

Operatori `typeof` na lejon të shohim se cili lloj është i ruajtur në një variabël.

- Dy lloje: `typeof x` ose `typeof(x)`.
- Kthen nje string me emrin e llojit, p.sh `"string"`.
- Per `null` kthen nje `"object"` -- eshte nje gabim i gjuhes se programimit, nuk eshte ne te vertete nje objekt.

Në kapitujt e ardhshëm, ne do të përqendrohemi në vlerat primitive dhe pasi të jemi njohur me to, do të kalojmë te objektet.
