# Operatori i bashkërenditjes së zero-vlerave (null/undefined) '??'

[recent browser="new"]

Këtu, në këtë artikull, do të themi se një shprehje është "e përcaktuar" kur ajo nuk është as `null` as `undefined`.

Operatori i bashkërenditjes së zero-vlerave shkruhet si dy pikëpyetje `??`.

Rezultati i `a ?? b` është:
- nëse `a` është i përcaktuar, atëherë `a`,
- nëse `a` nuk është i përcaktuar, atëherë `b`.

Me fjalë të tjera, `??` kthen argumentin e parë nëse ai nuk është `null/undefined`. Përndryshe, kthen të dytin.

Operatori i bashkërenditjes së zero-vlerave nuk është diçka krejtësisht e re. Është thjeshtë një sintaksë e bukur për të marrë vlerën e parë "të përcaktuar" nga dy vlerat.

Ne mund ta rishkruajmë `result = a ?? b` duke përdorur operatorët që tashmë i dimë, si më poshtë:

```js
result = (a !== null && a !== undefined) ? a : b;
```

Rasti i përdorimit më i zakonshëm për `??` është të ofrojë një vlerë të parazgjedhur për një variabël që mund të jetë e papërcaktuar.

Për shembull, këtu ne shfaqim `Anonymous` nëse `user` nuk është i përcaktuar:

```js
let user;

alert(user ?? "Anonymous"); // Anonymous
```

Sigurisht, nëse `user` do të kishte ndonjë vlerë përveç `null/undefined`, atëherë do ta shihnim atë në vend:

```js
let user = "John";

alert(user ?? "Anonymous"); // John
```

Ne gjithashtu mund të përdorim një varg të `??` për të zgjedhur vlerën e parë nga një listë që nuk është `null/undefined`.

Le të themi se kemi të dhënat e një përdoruesi në variablat `firstName`, `lastName` ose `nickName`. Të gjitha ato mund të jenë të papërcaktuara, nëse përdoruesi vendosi të mos shkruajë një vlerë.

Dëshirojmë të shfaqim emrin e përdoruesit duke përdorur një nga këto variabla, ose të shfaqim "Anonymous" nëse të gjitha ato janë të papërcaktuara.

Le të përdorim operatorin `??` për këtë:

```js
let firstName = null;
let lastName = null;
let nickName = "Supercoder";

// tregon vlerën e parë të përcaktuar:
*!*
alert(firstName ?? lastName ?? nickName ?? "Anonymous"); // Supercoder
*/!*
```

## Krahasimi me ||

Operatori OR `||` mund të përdoret në të njëjtën mënyrë si `??`, siç është përshkruar në [kapitullin e mëparshëm](info:logical-operators#or-finds-the-first-truthy-value).

Për shembull, në kodin e mësipërm mund të zëvendësojmë `??` me `||` dhe ende të marrim të njëjtin rezultat:

```js
let firstName = null;
let lastName = null;
let nickName = "Supercoder";

// tregon vlerën e parë të vërtetë:
*!*
alert(firstName || lastName || nickName || "Anonymous"); // Supercoder
*/!*
```

Operatori OR `||` ekziston tashmë në JavaScript për shumë vite. Para se `??` të shtohej në specifikimin e gjuhës, `||` ishte një mënyrë për të arritur të njëjtën gjë.

Por ka një rëndësi të madhe.

Operatori OR `||` kthen vlerën e parë të vërtetë, ndërsa `??` kthen vlerën e parë të përcaktuar.

Kjo do të thotë se kur përdorim `||`, vlerat false si `0`, `''`, `NaN` do të injorohen.

Për shembull:

```js
let height = 0;

alert(height || 100); // 100
alert(height ?? 100); // 0
```

Në këtë kod, `height || 100` kthen `100` sepse `height` është `0` (i cili është një vlerë false). Në anën tjetër, `height ?? 100` kthen `height` që është `0`, siç duhet të ishte.

## Prioriteti i `??`

Prioriteti i operatorit `??` është mjaft i ulët: `5` në [tabelën e MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence#Table). Pra, `??` vlerësohet para `=` dhe `?`, por pas shumicës së operacioneve të tjera, si `+`, `*`.

Pra, nëse dëshirojmë të zgjedhim një vlerë me `??` në një shprehje me operatorë të tjerë, konsideroni shtimin e kllapave:


Për shembull, në kodin më poshtë `alert` nuk do të ekzekutohet:

```js
let x = 1;
let y = 2;

*!*
// Gabim
if (x > y ?? x > 1 || y > 1) {
  alert('Nuk do të shfaqet');
}
*/!*
```

JavaScript e interpreton kodin `x > y ?? x > 1 || y > 1` si `x > (y ?? x) > 1 || y > 1`, kjo do të thotë se rezultati i `y ?? x` do të krahasohet me `1`. Por në fakt, duam të kontrollojmë rezultatin e `x > y` dhe `x > 1` ose `y > 1`.

Pra, duhet të përdorim kllapa:

```js
let x = 1;
let y = 2;

if ((x > y) ?? (x > 1) || (y > 1)) {
  alert('Nuk do të shfaqet');
}
```

Tani funksionon siç duhet.

## Përfundim

Operatori i bashkërenditjes së zero-vlerave `??` është një mënyrë e sigurt për të zgjedhur vlerën e parë "të përcaktuar" nga lista.

Ajo është një zëvendësim i mirë për `||` në rastet kur duam të mbështesim vlerat false `0`, `''`, `NaN`.

Sigurohuni që të mos përdorni `??` me `||` ose `&&` pa shtuar kllapa, sepse për shkak të prioritetit të ulët të operatorit `??`, mund të mos merrni rezultatin e pritur.