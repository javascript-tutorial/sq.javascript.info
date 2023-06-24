# Struktura e kodit

Gjëja e parë që do të studiojmë janë ndertimi i bllok-kodeve.

## Deklaratat

Deklaratat janë struktura sintaksore dhe komanda që kryejnë veprime.

Tashmë kemi parë një deklaratë, `alert('Pershendetje, bota!')`, e cila shfaq mesazhin "Përshëndetje, bota!".

Ne mund të kemi sa të dëshirojmë deklarata në kodin tonë. Deklaratat mund të ndahen me një pikëpresje.

Për shembull, këtu ndajmë "Përshëndetje Bota" në dy deklarata të ndara:

```js run no-beautify
alert('Përshëndetje'); alert('Bota');
```

Zakonisht, deklaratat shkruhen në rreshta të ndarë për të bërë kodin më të lexueshëm:

```js run no-beautify
alert('Hello');
alert('World');
```

## Pikëpresja [#semicolon]

Një pikëpresje mund të hiqet në shumicën e rasteve kur ekziston një ndarje e rreshtit.

Kjo gjithashtu do të funksionojë:

```js run no-beautify
alert('Hello')
alert('World')
```

Këtu, JavaScript-i e interpreton ndarjen e rreshtit si një pikëpresje "implisite". Kjo quhet [automatic semicolon insertion](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion).

**Në shumicën e rasteve, një ndarje e rreshtit implikon një pikëpresje. Por "në shumicën e rasteve" nuk do të thotë "në të gjitha rastet".!**

Ka raste kur një nje rresht i ri nuk do të thotë një pikëpresje. Për shembull:

```js run no-beautify
alert(3 +
1
+ 2);
```

Kodi jep rezultatin `6` sepse JavaScript nuk fut pikëpresje këtu. Është intuitivisht e qartë që nëse rreshti përfundon me shenjën plus `"+"`, atëherë është një "shprehje e paplotë", kështu që pikëpresja nuk kërkohet. Dhe në këtë rast, kjo vepron siç është parashikuar.

**Por ka situata kur JavaScript "dështon" të supozojë një pikëpresje aty ku është vërtet e nevojshme.**

Gabimet që ndodhin në këto raste janë të vështira për t'u gjetur dhe për t'u rregulluar.

````smart header="An example of an error"
Nëse jeni të interesuar të shihni një shembull konkret të një gabimi të tillë, kontrolloni këtë kod:

```js run
[1, 2].forEach(alert)
```

Nuk ka nevojë të merremi ende me kuptimin e thonjëzave `[]` dhe `forEach`. Do t'i studiojmë më vonë. Për tani, thjesht mbani mend rezultatin e kodit: shfaq 1, pastaj 2.

Now, let's add an `alert` before the code and *not* finish it with a semicolon:
Tani, shtojme një alert përpara kodit dhe mos e përfundo ate me një pikëpresje:



```js run no-beautify
alert("Ketu do te kete nje error")

[1, 2].forEach(alert)
```

Nëse ekzekutojmë kodin, do të shfaqet vetëm `alert` i parë dhe pastaj do të hasim një gabim!
Por gjithçka është e rregullt përsëri nëse shtojmë një pikëpresje pas `alert`:
```js run
alert("Gjithçka është e rregullt tani");

[1, 2].forEach(alert)  
```

Tani kemi mesazhin "Gjithçka është e rregullt tani" e ndjekur nga `1` dhe `2`.


Gabimi në variantin pa pikëpresje ndodh sepse JavaScript nuk konsideron automatikisht një pikëpresje para kllapave katrore `[...]`.

Prandaj, sepse pikëpresja nuk futet automatikisht, kodi në shembullin e parë trajtohet si një deklaratë e vetme. Kështu e sheh motori kodin:

```js run no-beautify
alert("Do të shfaqet një gabim")[1, 2].forEach(alert)
```

Por duhet të jenë dy deklarata të ndara, jo një. Një bashkim i tillë në këtë rast është gabim, prandaj shfaqet gabimi. Kjo mund të ndodhë edhe në situata të tjera.

````

We recommend putting semicolons between statements even if they are separated by newlines. This rule is widely adopted by the community. Let's note once again -- *it is possible* to leave out semicolons most of the time. But it's safer -- especially for a beginner -- to use them.
Ne rekomandojmë të vendosni pikëpresje midis deklaratave, edhe nëse ato janë të ndara me viza të reja. Ky rregull është i pranuar gjerësisht nga komuniteti. Le të theksojmë përsëri -- *është e mundur* të mos vendosni pikëpresje shpesh herë. Por është më e sigurt -- sidomos për një fillimtar -- të përdorni pikëpresjet.


## Komentet [#code-comments]

Dita dites, programet bëhen gjithnjë e më kompleks. Bëhet e nevojshme të shtoni komentet që përshkruajnë çfarë bën kodi dhe pse e bën atë.

Komentet mund të vendosen në çdo vend të skriptit. Ata nuk ndikojnë në ekzekutimin e tij, pasi motori thjesht i injoron ato.

**Komentet në një rresht fillon me dy karaktere `//`.**

Pjesa tjetër e rreshtit është koment. Ajo mund të zëj një rresht të tërë ose të ndjekë një deklaratë.

Si këtu:
```js run
// Kjo komentë zë një rresht të vetëm:
alert('Pershendetje');

alert('Bota'); // Ky koment vjen pas deklarates
```

**Komentet me shumë rreshta fillon me një / dhe një yll <code>/&#42;</code> dhe përfundon me një yll dhe një / <code>&#42;/</code>.**


Si këtu:

```js run
/* Nje shembull me dy mesazhe.
Ky eshte nje koment me shume rreshta.
*/
alert('Pershendetje');
alert('Bota');
```

Të dhënat e komenteve janë të injoruara, kështu që nëse vendosim kod brenda <code>/&#42; ... &#42;/</code>, ai nuk do të ekzekutohet.


Ka raste kur mund të jetë e dobishme të çaktivizojmë përkohësisht një pjesë të kodit:
```js run
/* Çaktivizimi i kodit duke e bërë atë koment
alert('Pershendetje');
*/
alert('Bota');
```

```smart header="Perdorni tastin!"
Në shumicën e editoreve, një rresht i kodit mund të vendoset si koment duke shtypur tastin `key:Ctrl+/` për një koment në një rresht, ndërsa diçka si `key:Ctrl+Shift+/` -- për komente me shumë rreshta (selektoni një pjesë të kodit dhe shtypni tastin). Për kompjuterat Mac, provoni `key:Cmd` në vend të `key:Ctrl` dhe `key:Option` në vend të `key:Shift`.
```

````warn header="Komentet e bashkuara nuk jane te suportuara!"
Mund të mos ketë `/*...*/` brenda një tjetri `/*...*/`.

Një kod i tillë do të shfaqi një gabim:

```js run no-beautify
/*
  /* koment i bashkuar ?!? */
*/
alert( 'Bota' );
```
````

Ju lutemi, mos hezitoni të komentoni kodin tuaj.

Komentet rrisin gjurmën e përgjithshme të kodit, por ky nuk është aspak problem. Ka shumë mjete që minimizojnë kodin përpara se të publikohen në një server prodhimi. Ata heqin komentet, në mënyrë që të mos shfaqen në skriptet e punës. Prandaj, komentet nuk kanë fare efekte negative në prodhim.

Më vonë në tutorial do të ketë një kapitull <info:code-quality> qe gjithashtu shpjegon se si të shkruani komente më të mira.
