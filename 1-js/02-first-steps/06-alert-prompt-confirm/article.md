# Ndërveprimet: alert, prompt, confirm
Duke qenë se do të përdorim shfletuesin si mjedisin tonë demonstrues, le të shohim disa funksione për të bashkëvepruar me përdoruesin: `alert`, `prompt` dhe `confirm`.

## alert

Këtë e kemi parë tashmë. Shfaq një mesazh dhe pret që përdoruesi të shtypë "OK".

Per shembull:

```js run
alert("Pershendetje");
```

Dritarja e vogël me mesazh quhet *dritare modale*. Fjala "modale" nënkupton se vizitori nuk mund të nderveproj me pjesën tjetër të faqes, të shtypë butona të tjera etj., derisa të merret me dritaren. Në këtë rast -- derisa të shtypin "OK".

## prompt

Funksioni `prompt` pranon dy argumenta:

```js no-beautify
result = prompt(title, [default]);
```

Shfaq një dritare modale me një mesazh tekstual, një fushë inputi për vizitorin dhe butonat OK/Cancel.

`title`
: Teksti për të treguar vizitorin.

`default`
: Një parametër i dytë opsional, vlera fillestare për fushën e inputit.

```smart header="Kllapat katrore ne sintakse `[...]`"
Kllapat katrore përreth `default` në sintaksën e mësipërme tregojnë se parametri është opsional, nuk kërkohet me domodoshmeri.
```

Vizitori mund të shkruajë diçka në fushën e inputit dhe të shtypë OK. Pastaj e marrim atë tekst në 'result'. Ose ata mund të anulojnë hyrjen duke shtypur Cancel ose duke shtypur tastin 'tastin:Esc', atehere marrim `null` si `result`.

Thirrja tek `prompt` kthen tekstin nga fusha e input ose `null` nëse hyrja është anuluar.

Per shembull:

```js run
let age = prompt('Sa vjec jeni ju?', 100);

alert(`Ju jeni ${age} vjec!`); // Ju jeni 100 vjec!
```

````warn header="Ne IE: gjithmone perdorni `default`"
Parametri i dytë është opsional, por nëse nuk e japim, Internet Explorer do të fusë tekstin `"undefined"` në prompt.

Ekzekutoni këtë kod në Internet Explorer për të parë:

```js run
let test = prompt("Test");
```

Pra, që kërkesat të duken mirë në IE, ne rekomandojmë që gjithmonë të jepni argumentin e dytë:

```js run
let test = prompt("Test", ''); // <-- per IE
```
````

## confirm

Sintaksa:

```js
result = confirm(question);
```

Funksioni `confirm` tregon një dritare modale me një `pyetje` dhe dy butona: OK dhe Cancel.

Rezultati është `true` nëse shtypet OK dhe `false` ndryshe.

Per shembull:

```js run
let isBoss = confirm("A jeni ju bosi?");

alert( isBoss ); // true nese OK eshte shtypur
```

## Permbledhje

Ne mbuluam 3 funksione specifike të shfletuesit për të bashkëvepruar me vizitorët:

`alert`
: shfaq nje mesazh.

`prompt`
: tregon një mesazh që i kërkon përdoruesit të fusë tekst. Ai kthen tekstin ose, nëse klikohet butoni Cancel ose `key:Esc`, `null`.

`confirm`
: shfaq nje mesazh dhe pret qe perdoruesi te shtypi "OK" ose "Cancel". Kthen vleren `true` per OK dhe `false` per Cancel/`key:Esc`.

Të gjitha këto metoda janë modale: ato ndalojnë ekzekutimin e skriptit dhe nuk e lejojnë vizitorin të ndërveprojë me pjesën tjetër të faqes derisa dritarja të hiqet.

Ekzistojnë dy kufizime të përbashkëta nga të gjitha metodat e mësipërme:

1. Vendndodhja e saktë e dritares modale përcaktohet nga shfletuesi. Zakonisht është në qendër.
2. Pamja e saktë e dritares varet gjithashtu nga shfletuesi. Nuk mund ta modifikojmë.

Ky është çmimi i thjeshtësisë. Ka mënyra të tjera për të treguar dritare më të bukura dhe ndërveprim më të pasur me vizitorin, por nëse "këmbanat dhe bilbilat" nuk kanë shumë rëndësi, këto metoda funksionojnë mirë.
