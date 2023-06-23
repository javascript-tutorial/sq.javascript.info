# Pershendetje bote!

Kjo pjesë e mesimit është për bazat JavaScript-it , vetë gjuhën e programimit.

Por ne kemi nevojë për një mjedis të funksionueshëm për të ekzekutuar skriptat tona dhe, pasi ky libër është në internet, shfletuesi është një zgjedhje e mirë. Ne do të perdorim komandat (sic eshte `alert`) në minimum, kështu që të mos humbasim kohë në to nëse planifikoni të përqendroheni në një mjedis tjetër (si Node.js). Ne do të fokusohemi te JavaScript-i në shfletues në [pjesen tjeter](/ui) të mesimit.

Kështu që së pari, le të shohim si bashkojmë një skript në një faqe interneti. Për mjediset server-side (si Node.js), mund të ekzekutoni skriptën me një komandë si `"node my.js"`.


## Etiketa "script"

Programet JavaScript mund të vendosen në çdo pjesë të një dokumenti HTML me ndihmën e etiketës `<script>`.

Për shembull:

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>Perpara script...</p>

*!*
  <script>
    alert( 'Pershendetje bote!!' );
  </script>
*/!*

  <p>...Pas script.</p>

</body>

</html>
```

```online
Mund të ekzekutoni shembullin duke klikuar në butonin "Luaj" në cepin e djathtë të sipërfaqes më lart.
```

Etiketa `<script>` përmban kod JavaScript i cili ekzekutohet automatikisht kur shfletuesi proceson etiketën.


## Markup modern

Etiketa `<script>` ka disa atribute që rrallë përdoren sot, por mund të gjenden ende në kodin e vjetër:

Atributi i `type`: <code>&lt;script <u>type</u>=...&gt;</code>

Standardi i vjetër i HTML, HTML4, kërkonte që një skript të kishte atributin `type`. Zakonisht, ishte `type="text/javascript"`. Kjo nuk kërkohet më në HTML. Atributi `type` ka ndryshuar plotësisht kuptimin e tij. Tani, ai mund të përdoret për modulet e JavaScript. Por ky është një temë e avancuar, dhe do të flasim më gjerësisht për modulet në një pjesë tjetër të mësimit.

Atributi i `language`: <code>&lt;script <u>language</u>=...&gt;</code>
: Ky atribut kishte për qëllim të tregonte gjuhën e skriptit. Megjithatë, ky atribut nuk ka më kuptim pasi JavaScript është gjuha kryesore. Nuk ka nevojë ta përdorni këtë atribut.

Komentet para dhe pas skripteve.
Në librat dhe udhëzime shumë të vjetra, mund të gjenden komente brenda etiketave `<script>`, si në këtë mënyrë:

    ```html no-beautify
    <script type="text/javascript"><!--
        ...
    //--></script>
    ```

    Ky truk nuk përdoret në JavaScriptin modern. Këto komente fshehin kodin JavaScript nga shfletuesit e vjetër që nuk dinin si të procesonin etiketën <script>. Pasi që shfletuesit në 15 vitet e fundit nuk kanë këtë problem, ky lloj komenti mund t'ju ndihmojë të identifikoni kodin shumë të vjetër.


## Skriptet e jashtëm

Nëse kemi shumë kod JavaScript, mund ta vendosim atë në një skedar të veçantë.

Skedarët e skripteve bashkohen me HTML-në duke përdorur atributin `src`:

```html
<script src="/path/to/script.js"></script>
```

Këtu, `/path/to/script.js` është një path absolute për skedarin nga rrënja e faqes. Mund të jepni gjithashtu një path relative nga faqja aktuale. Për shembull, `src="script.js"` do të thotë një skedar "script.js" në dosjen aktuale.


Ne gjithashtu mund të jepim një URL të plotë. Për shembull:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
```

Për të bashkangjitur disa skripte, përdorni shumë etiketa:

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

```smart
Si rregull, vetëm skriptet më të thjeshta vendosen në HTML. Skriptet më komplekse që kërkojnë më shumë kod zakonisht vendosen në skedarë të veçantë.

Përfitimi i një skedari të veçantë është se shfletuesi do ta shkarkojë atë dhe do ta ruajë në [cache](https://en.wikipedia.org/wiki/Web_cache).

Faqet e tjera që referencojnë të njëjtin skript do ta marrin atë nga cache në vend që ta shkarkojnë, kështu që skedari shkarkohet në fakt vetëm një herë.

Kjo redukton trafikun dhe bën faqet më të shpejta.
```

````warn header="Nese `src` eshte vendosur, permbajtja e skriptit injorohet."
Një etiketë e vetme `<script>` nuk mund të ketë njëkohësisht atributin `src` dhe kod brenda.

Kjo nuk do të funksionojë:

```html
<script *!*src*/!*="file.js">
  alert(1); // permbajtja do te injorohet, pasi src eshte vendosur
</script>
```

Duhet të zgjedhim ose një skedar të jashtëm `<script src="…">`, ose një skript normal `<script>` me kod.

Shembulli i mësipërm mund të ndahet në dy skripte për të funksionuar:

```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
````

## Përmbledhje

- Mund të përdorim etiketën `<script>` për të shtuar kod JavaScript në një faqe.
- Atributet `type` dhe `language` nuk janë të nevojshme.
- A script in an external file can be inserted with `<script src="path/to/script.js"></script>`.
- Një skript në një skedar të jashtëm mund të vendoset me anë të `<script src="path/to/script.js"></script>`.

Ka shumë më tepër për të mësuar në lidhje me skriptet e shfletuesit dhe ndërveprimin e tyre me faqen e internetit. Por le të mbajmë parasysh se kjo pjesë e udhëzuesit është e dedikuar gjuhës së programimit JavaScript, kështu që nuk duhet të shpërqendrohemi me implementimet specifike të shfletuesit. Ne do të përdorim shfletuesin si një mënyrë për të ekzekutuar JavaScript, e cila është shumë e përshtatshme për leximin në internet, por vetëm njërin nga shumë shfletues.
