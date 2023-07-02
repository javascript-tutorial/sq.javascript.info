# Operatoret bazike, matematike

Ne njohim shumë operatorë nga shkolla. Ato janë gjëra të tilla si mbledhja `+`, shumëzimi `*`, zbritja `-`, e kështu me radhë.

Në këtë kapitull, ne do të fillojmë me operatorë të thjeshtë, më pas do të përqendrohemi në aspekte specifike të JavaScript, të cilat nuk mbulohen nga aritmetika e shkollës.

## Termat: "unary", "binary", "operand"

Para se të vazhdojmë, le të kuptojmë disa terminologji të zakonshme.

- *Një operand* -- është ajo për të cilën aplikohen operatorët. Për shembull, në shumëzimin e `5 * 2` ka dy operandë: operandi i majtë është `5` dhe operandi i djathtë është `2`. Ndonjëherë, njerëzit i quajnë këto "argumente" në vend të "operandëve".
- Një operator është *unary* nëse ka një operand të vetëm. Për shembull, operatori i mohimit unar `-` ndryshon shenjën e një numri:

    ```js run
    let x = 1;

    *!*
    x = -x;
    */!*
    alert( x ); // -1, unary minus egzekutohet
    ```
- Nje operator eshte *binary* nese ka dy operande. I njejti minus funksionon edhe ne forme binare:

    ```js run no-beautify
    let x = 1, y = 3;
    alert( y - x ); // 2, binary minus zbret vlerat
    ```

    Formalisht, në shembujt e mësipërm kemi dy operatorë të ndryshëm që ndajnë të njëjtin simbol: operatori i mohimit, një operator unar që kthen shenjën kundër, dhe operatori i zbritjes, një operator binar që zbret një numër nga një tjetër.

## Veprimet matematikore

Operacionet e mëposhtme matematikore suportohen:

- Mbledhje `+`,
- Zbritje `-`,
- Shumezim `*`,
- Pjestim `/`,
- Mbetje `%`,
- Eksponentimi `**`.

Katër të parat janë të drejtpërdrejta, ndërsa `%` dhe `**` kanë nevojë për disa fjalë rreth tyre.

### Mbetja %

Operatori i mbetjes `%`, pavarësisht pamjes së tij, nuk lidhet me përqindjet.

Rezultati i  `a % b` eshte ne [remainder](https://en.wikipedia.org/wiki/Remainder) nga pjesëtimi i plotë i `a` me `b`.

Pershembull:

```js run
alert( 5 % 2 ); // 1, mbetja e  5 pjesetuar me 2
alert( 8 % 3 ); // 2, mbetja e  8 pjesetuar me 3
```

### Eksponentimi (operatori i fuqise) **

Operatori i fuqisë `a ** b` shumëzon `a` me veteveten `b` herë.

For instance:

```js run
alert( 2 ** 2 ); // 4  (2 shumezohet me me veteveten 2 here)
alert( 2 ** 3 ); // 8  (2 * 2 * 2, 3 here)
alert( 2 ** 4 ); // 16 (2 * 2 * 2 * 2, 4 here)
```

Matematikisht, fuqia përcaktohet edhe për numrat jo të plotë. Për shembull, një rrënjë katrore është një eksponentim me `1/2`:

```js run
alert( 4 ** (1/2) ); // 2 (fuqia e 1/2 është e njëjtë me rrënjën katrore)
alert( 8 ** (1/3) ); // 2 (fuqia e 1/3 është e njëjtë me rrënjën kubike)
```


## Lidhja e stringjeve me binar +

Le të shofim veçoritë e operatorëve JavaScript që janë përtej aritmetikës shkollore.

Zakonisht, operatori plus `+` mbledh numrat.

But, if the binary `+` is applied to strings, it merges (concatenates) them:
Por, nëse opratori binar `+` zbatohet te stringjet, ai i bashkon (perfshin) ato:

```js
let s = "my" + "string";
alert(s); // mystring
```

Vini re se nëse ndonjë nga operandët është një string, atëherë edhe tjetri konvertohet në një string.

Per shembull:

```js run
alert( '1' + 2 ); // "12"
alert( 2 + '1' ); // "21"
```

Shihni, nuk ka rëndësi nëse operandi i parë është një string apo i dyti.

Këtu është një shembull më kompleks:

```js run
alert(2 + 2 + '1' ); // "41" dhe jo "221"
```

Këtu, operatorët punojnë njëri pas tjetrit. `+` e parë përmbledh dy numra, kështu që kthen `4`, më pas `+` tjetër i shton stringun `1`, pra është si `4 + '1' = 41`.

Binari `+` është i vetmi operator që mbështet stringjet në një mënyrë të tillë. Operatorët e tjerë aritmetikë punojnë vetëm me numra dhe gjithmonë i konvertojnë operandët e tyre në numra.

Këtu është demonstrimi për zbritjen dhe pjesëtimin:

```js run
alert( 6 - '2' ); // 4, konverton '2' ne nje numer
alert( '6' / '2' ); // 3, konverton te dy operandet ne numra
```

## Konvertimi numerik, unary +

Plusi `+` egziston ne dy forma: forma binare që përdorëm më sipër dhe forma unare.

Operatori unary plus ose, me fjalë të tjera, operatori plus + i aplikuar në një vlerë të vetme, nuk bën asgjë tek numrat. Por nëse operandi nuk është një numër, unary plus e konverton atë në një numër.

Per shembull:

```js run
// Nuk ka asnje efekt tek numri
let x = 1;
alert( +x ); // 1

let y = -2;
alert( +y ); // -2

*!*
// Konverton jo numrat
alert( +true ); // 1
alert( +"" );   // 0
*/!*
```

Faktikisht, ai bën të njëjtën gjë si `Number(...)`, por është më i shkurtër.

Nevoja për të konvertuar stringjet në numra lind shpesh. Për shembull, nëse po marrim vlera nga fushat e formularit HTML, ato zakonisht janë stringje. Çfarë bëjmë nëse duam t'i shumojmë ato?

Operatori binar plus do t'i shtonte ato si stringje:

```js run
let apples = "2";
let oranges = "3";

alert( apples + oranges ); // "23", the binary plus concatenates strings
```

Nëse duam t'i trajtojmë ato si numra, duhet t'i konvertojmë dhe pastaj t'i mbledhim:

```js run
let apples = "2";
let oranges = "3";

*!*
// të dy vlerat konvertohen në numra para operatorit binar plus
alert( +apples + +oranges ); // 5
*/!*

// varianti me i gjate
// alert( Number(apples) + Number(oranges) ); // 5
```

Nga pikëpamja e një matematicienti, sasia e shumë pluseve mund të duket e çuditshme. Por nga pikëpamja e një programuesi, nuk ka asgjë të veçantë: plusi unary aplikohen në fillim, ato konvertojnë stringjet në numra, dhe pastaj operatori binar plus i shton ato së bashku.


Pse aplikohen unary pluset në vlera para atyre binarëve? Si do të shohim, kjo ndodh për shkak të *perparesise*.

## Përparësia e operatorëve

Nëse një shprehje ka më shumë se një operator, rendi i ekzekutimit përcaktohet nga *përparësia* e tyre, ose, me fjalë të tjera, renditja e prioritetit të paracaktuar të operatorëve.

Nga shkolla, të gjithë e dimë se shumëzimi në shprehjen `1 + 2 * 2` duhet të llogaritet para mbledhjes. Kjo është pikërisht ajo e përparësisë. Thuhet se shumëzimi ka *përparësi* më të lartë se mbledhja.

Kllapat anashkalojnë çdo përparësi, kështu që nëse nuk jemi të kënaqur me renditjen e paracaktuar, mund t'i përdorim ato për ta ndryshuar atë. Për shembull, shkruani `(1 + 2) * 2`.

Ka shumë operatorë në JavaScript. Çdo operator ka një numër përkatës precedent. Ai me numrin më të madh ekzekutohet i pari. Nëse përparësia është e njëjtë, rendi i ekzekutimit është nga e majta në të djathtë.

Këtu është një ekstrakt nga [tabela e përparësisë](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence) (nuk keni nevojë ta mbani mend këtë, por vini re se unary operatorët janë më të lartë se ata binarë):

| Përparësia | Emri | Shenja |
|------------|------|------|
| ... | ... | ... |
| 17 | unary plus | `+` |
| 17 | unary negation | `-` |
| 16 | fuqia | `**` |
| 15 | shumezimi | `*` |
| 15 | pjesetimi | `/` |
| 13 | mbledhja | `+` |
| 13 | zbritja | `-` |
| ... | ... | ... |
| 3 | caktimi | `=` |
| ... | ... | ... |

Siç mund ta shohim, "unary plus" ka një përparësi prej `17` që është më e lartë se `13` e "mbledhjes" (plus binar). Kjo është arsyeja pse, në shprehjen `"+apples + +oranges"`, pluset unare funksionojnë para shtimit.

## Caktimi

Le të vërejmë se një caktues `=` është gjithashtu një operator. Është renditur në tabelën e përparësisë me prioritet shumë të ulët `3`.

That's why, when we assign a variable, like `x = 2 * 2 + 1`, the calculations are done first and then the `=` is evaluated, storing the result in `x`.
Kjo është arsyeja pse, kur i caktojmë një variabël, siç është `x = 2 * 2 + 1`, llogaritjet bëhen së pari dhe pastaj `=` caktohet, duke ruajtur rezultatin në `x`.
```js
let x = 2 * 2 + 1;

alert( x ); // 5
```

### Caktimi = rikthen nje vlere

Fakti që `=` është një operator, dhe jo një strukturë "magjike" e gjuhës, ka një implikim interesant.

Shumica e operatorëve në JavaScript kthejnë një vlerë. Kjo është e qartë për operatorët  `+` dhe `-`, por është gjithashtu e vërtetë edhe për operatorin `=`.

Thirrja `x = value` shkruan `value` në `x` *dhe pastaj e kthen atë*.

Këtu është një demonstrim që përdor një detyrë si pjesë e një shprehjeje më komplekse:

```js run
let a = 1;
let b = 2;

*!*
let c = 3 - (a = b + 1);
*/!*

alert( a ); // 3
alert( c ); // 0
```

Në shembullin e mësipërm, rezultati i shprehjes `(a = b + 1)` është vlera që i është caktuar `a` (që është `3`). Më pas përdoret për vlerësime të mëtejshme.

Kodi qesharak, apo jo? Ne duhet të kuptojmë se si funksionon, sepse ndonjëherë e shohim atë në bibliotekat JavaScript.

Edhe pse, ju lutemi mos e shkruani kodin ashtu. Truket e tilla definitivisht nuk e bëjnë kodin më të qartë apo të lexueshëm.

### Detyrat zinxhirore

Një veçori tjetër interesante është aftësia për të lidhur detyrat:

```js run
let a, b, c;

*!*
a = b = c = 2 + 2;
*/!*

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
```

Detyrat me zinxhir vlerësohen nga e djathta në të majtë. Së pari, shprehja më e djathtë `2 + 2` vlerësohet dhe më pas u caktohet variablave në të majtë: "c", "b" dhe "a". Në fund, të gjitha variablat ndajnë një vlerë të vetme.

Edhe një herë, për qëllime të lexueshmërisë, është më mirë të ndash një kod të tillë në disa rreshta:

```js
c = 2 + 2;
b = c;
a = c;
```
Kjo është më e lehtë për t'u lexuar, veçanërisht kur skanoni kodin me sy të shpejtë.

## Modifiko-në vend

Shpesh na duhet të aplikojmë një operator në një variabël dhe të ruajmë rezultatin e ri në të njëjtën variabel.

Per shembull :

```js
let n = 2;
n = n + 5;
n = n * 2;
```

Ky kod mund të shkurtohet duke përdorur operatorët `+=` dhe `*=`:

```js run
let n = 2;
n += 5; // tashme n = 7 (same as n = n + 5)
n *= 2; // tashme n = 14 (same as n = n * 2)

alert( n ); // 14
```

Operatorët e shkurtër "modify-and-assign" ekzistojnë për të gjithë operatorët aritmetikë dhe bit: `/=`, `-=`, etj.

Operatorë të tillë kanë të njëjtën përparësi si një caktim normal, kështu që ata ekzekutohen pas kalkulimeve te tjera:

```js run
let n = 2;

n *= 3 + 5;

alert( n ); // 16  (Pjesa e djathtë shikohet ne fillim, njësoj si n *= 8)
```

## Inkrement/Dekrement

<!-- Nuk mund të përdoret -- në titull, sepse analizuesi i integruar e kthen atë në një 'vijë të gjatë' – -->

Rritja ose zvogëlimi i një numri me 1 është ndër veprimet numerike më të zakonshme.

Pra, ka operatorë të veçantë për të:

- **Increment** `++` rrit vleren e variables me 1:

    ```js run no-beautify
    let counter = 2;
    counter++;        // funksionon njësoj si counter = counter + 1, por është më i shkurtër
    alert( counter ); // 3
    ```
- **Decrement** `--` zvogelon vleren e variables me 1:

    ```js run no-beautify
    let counter = 2;
    counter--;        //  funksionon njësoj si counter = counter - 1, por është më i shkurtër
    alert( counter ); // 1
    ```

```warn
Inkrementimi/Dekrementimi mund të aplikohet vetëm për variablat. Përpjekja për ta përdorur atë në një vlerë si "5++" do të japë një gabim.
```

Operatoret `++` dhe `--` mund të vendoset ose para ose pas një variable.

- Kur operatori shkon pas variablit, ai është në "Formen e post-prefiksit": `counter++`.
- "Forma e prefiksit" është kur operatori shkon përpara variables: `++counter`.

Të dyja këto pohime bëjnë të njëjtën gjë: rrisin `counter` me `1`.

A ka ndonjë ndryshim? Po, por ne mund ta shohim atë vetëm nëse përdorim vlerën e kthyer të `++/--`.

Le të sqarojmë. Siç e dimë, të gjithë operatorët kthejnë një vlerë. Rritja/ulja nuk bën përjashtim. Forma e prefiksit kthen vlerën e re, ndërsa forma e postprefiksit kthen vlerën e vjetër (para rritjes/zvogëlimit).

Për të parë ndryshimin, ja një shembull:

```js run
let counter = 1;
let a = ++counter; // (*)

alert(a); // *!*2*/!*
```

Në rreshtin `(*)`, *prefiksi* nga `++counter` rrit me 1 `counter` dhe kthen vlerën e re, `2`. Pra, `alert` tregon "2".

Tani, le të përdorim formën postfiks:

```js run
let counter = 1;
let a = counter++; // (*) ndryshuam ++counter ne counter++

alert(a); // *!*1*/!*
```

Në rreshtin `(*)`, forma *postfix* `counter++` rrit gjithashtu `counter` por kthen vlerën *e vjetër* (para rritjes). Pra, `alert` tregon `1`.

Për të përmbledhur:

- Nëse rezultati i inkrementimit/dekrementimit nuk përdoret, nuk ka ndryshim në cilën formë të përdoret:

    ```js run
    let counter = 0;
    counter++;
    ++counter;
    alert( counter ); // 2, rreshtat me siper bejne te njejten gje
    ```
- Nëse duam të rrisim një vlerë *dhe* të përdorim menjëherë rezultatin e operatorit, na duhet forma e prefiksit:

    ```js run
    let counter = 0;
    alert( ++counter ); // 1
    ```
- Nëse duam të rrisim një vlerë, por përdorim vlerën e saj të mëparshme, na duhet formulari postfiks:

    ```js run
    let counter = 0;
    alert( counter++ ); // 0
    ```

````smart header="Inkrementim/dekrementim ndërmjet operatorëve të tjerë"
Operatorët `++/--` mund të përdoren gjithashtu brenda shprehjeve. Përparësia e tyre është më e lartë se shumica e operacioneve të tjera aritmetike.

Per shembull:

```js run
let counter = 1;
alert( 2 * ++counter ); // 4
```

Krahesoheni me:

```js run
let counter = 1;
alert( 2 * counter++ ); // 2, sepse counter++ rikthen vleren e vjeter
```

Megjithëse teknikisht në rregull, një shënim i tillë zakonisht e bën kodin më pak të lexueshëm. Një linjë bën shumë gjëra -- jo mirë.

Gjatë leximit të kodit, një skanim i shpejtë "vertikal" i syve mund të humbasë lehtësisht diçka si "counter++" dhe nuk do të jetë e qartë se variabli është rritur.

Ne këshillojmë një stil të "një linjë -- një veprim":

```js run
let counter = 1;
alert( 2 * counter );
counter++;
```
````

## Operatorët bitwise

Operatorët bitwise i trajtojnë argumentet si numra të plotë 32-bit dhe punojnë në nivelin e paraqitjes së tyre binar.

Këta operatorë nuk janë specifikë për JavaScript. Ato mbështeten në shumicën e gjuhëve programuese.

Lista e operatorëve:

- AND ( `&` )
- OR ( `|` )
- XOR ( `^` )
- NOT ( `~` )
- LEFT SHIFT ( `<<` )
- RIGHT SHIFT ( `>>` )
- ZERO-FILL RIGHT SHIFT ( `>>>` )


Këta operatorë përdoren shumë rrallë, kur duhet të merremi me numra në nivelin më të ulët (bitwise). Këta operatorë nuk do të na duhen së shpejti, pasi zhvillimi i uebit ka pak përdorim të tyre, por në disa fusha të veçanta, si kriptografia, ato janë të dobishme. Mund të lexoni kapitullin [Bitwise Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Bitwise) mbi MDN kur lind nevoja.

## Presja

Operatori i presjes `,` është një nga operatorët më të rrallë dhe më të pazakontë. Ndonjëherë, përdoret për të shkruar kodin më të shkurtër, kështu që ne duhet ta dimë atë në mënyrë që të kuptojmë se çfarë po ndodh.

Operatori i presjes na lejon të vlerësojmë disa shprehje, duke i ndarë ato me presje `,`. Secila prej tyre vlerësohet por kthehet vetëm rezultati i të fundit.

Per shembull:

```js run
*!*
let a = (1 + 2, 3 + 4);
*/!*

alert( a ); // 7 (rezultati i 3 + 4)
```

Këtu, shprehja e parë `1 + 2` vlerësohet dhe rezultati i saj hidhet tutje. Më pas, `3 + 4` vlerësohet dhe kthehet si rezultat.

```smart header="Presja ka një përparësi shumë të ulët"
Ju lutemi vini re se operatori i presjes ka përparësi shumë të ulët, më të ulët se `=`, kështu që kllapat janë të rëndësishme në shembullin e mësipërm.

Pa to: `a = 1 + 2, 3 + 4` vlerëson fillimisht `+`, duke përmbledhur numrat në `a = 3, 7`, më pas operatori i caktimit `=` cakton `a = 3`, dhe pjesa tjetër është injoruar. Është si `(a = 1 + 2), 3 + 4`.
```

Pse na duhet një operator që hedh gjithçka përveç shprehjes së fundit?

Ndonjëherë, njerëzit e përdorin atë në konstruksione më komplekse për të vendosur disa veprime në një linjë.

Per shembull:

```js
// tre veprime në një linjë
for (*!*a = 1, b = 3, c = a * b*/!*; a < 10; a++) {
 ...
}
```

Truket e tilla përdoren në shumë framework te JavaScript. Prandaj po i përmendim. Por zakonisht ato nuk përmirësojnë lexueshmërinë e kodit, kështu që ne duhet të mendojmë mirë përpara se t'i përdorim ato.