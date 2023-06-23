# Console e zhvilluesit

Kodi është i prirur të ketë gabime. Ka shumë gjasa që ju të bëni gabime... Oh, çfare po flas unë? Ju absolutisht do të bëni gabime, të paktën nëse jeni një njeri, jo një [robot](https://en.wikipedia.org/wiki/Bender_(Futurama)).

Por në shfletues, përdoruesit nuk shohin gabimet në mënyrë të paracaktuar. Prandaj, nëse diçka shkon keq në skript, nuk do të shohim se çfarë po shkon keq dhe nuk mund ta rregullojmë atë.

Për të parë gabimet dhe për të marrë shumë informacione të tjera të dobishme rreth skripteve, "mjetet e zhvilluesit" janë të integruara në shfletues.

Shumica e zhvilluesve preferojnë Chrome ose Firefox për zhvillim, sepse ato shfletues kanë mjetet e zhvilluesit më të mira. Shfletuesit e tjerë gjithashtu ofrojnë mjetet e zhvilluesit, ndonjëherë me karakteristika speciale, por zakonisht po përpiqen të ndjekin Chrome ose Firefox. Prandaj shumica e zhvilluesve kanë një shfletues "të preferuar" dhe bëjnë ndërrimin në të tjerët nëse një problem është i veçantë për shfletuesin.

Mjetet e zhvilluesit janë të fuqishme; ato kanë shumë karakteristika. Fillimisht, do të mësojmë si t'i hapim ato, të shohim gabimet dhe të ekzekutojmë komanda JavaScript.

## Google Chrome

Hapim faqen [bug.html](bug.html).

Ka një gabim në kodin JavaScript në të. Ai është i fshehur nga sytë e një vizitori të rregullt, kështu që le të hapim mjetet e zhvilluesit për ta parë atë.

Shtypim `key:F12` ose, nese perdorni Mac, atëhere `key:Cmd+Opt+J`.

Mjetet e zhvilluesit do të hapen në skedën "Console" si parazgjedhje.

Do te duket dicka e tillë:

![chrome](chrome.png)

Pamja e saktë e mjetit te zhvilluesit varet nga versioni juaj i Chrome. Ajo ndryshon nga koha në kohë, por duhet të jetë e ngjashme.

- Këtu mund të shohim mesazhin e gabimit me ngjyrë të kuqe. Në këtë rast, skripti përmban një komandë të panjohur "lalala".
- Në të djathtë, ka një lidhje që mund të klikohet për burimin `bug.html:12` me numrin e linjës ku ka ndodhur gabimi.

Poshtë mesazhit të gabimit, ka një simbol blu >. Ai nenkupton një "linjë komande" ku mund të shkruajmë komandat JavaScript. Shtypni `key:Enter` për t'i ekzekutuar ato.

Tani mund të shohim gabimet, dhe kjo mjafton per fillim. Do të kthehemi në mjetet e zhvilluesit më vonë dhe do të trajtojmë më thellë debuggimin në kapitullin <info:debugging-chrome>.

```smart header="Multi-line input"
Zakonisht, kur vendosim një rresht kod në konsolë dhe pastaj shtypim `key:Enter`, ai ekzekutohet.

Për të vendosur më shumë rreshta, shtypni `key:Shift+Enter`. Kështu mund të vendosni fragmente të gjata të kodit JavaScript.
```

## Firefox, Edge, dhe te tjere.

Shumica e shfletuesve të tjerë përdorin `key:F12` për të hapur mjetet e zhvilluesit.

Pamjet e tyre janë shumë të ngjashme. Nëse dini si të përdorni njërin nga këto mjetet (mund të filloni me Chrome), mund të kaloni lehtësisht në një tjetër.

## Safari

Safari (shfletuesi i Mac, i cili nuk mbështetet në Windows/Linux) është paksa i veçantë këtu. Ne duhet të aktivizojmë "Menunë e Zhvilluesit" së pari.

Hapni Preferencat dhe shkoni te paneli "Advanced". Në fund të tij ka një kutizë zgjedhjeje:

![safari](safari.png)

Tani `key:Cmd+Opt+C` mund të ndërrojë konsolën. Gjithashtu, vini re se ka shfaqur një element menu i ri në krye me emrin "Develop". Ai ka shumë komanda dhe opsione.

## Përmbledhje

- Mjetet e zhvilluesit na lejojnë të shohim gabimet, të ekzekutojmë komanda, të eksplorojmë variablat dhe shumë të tjera.
- Ato mund te aksesohen me `key:F12` per shumicen e shfletuesve ne Windows. Chrome per Mac shtypim `key:Cmd+Opt+J`, Safari: `key:Cmd+Opt+C` (duhet ta aktivizioni si fillim).

Tani kemi gati mjedisin. Në seksionin e ardhshëm, do të merremi me JavaScript-in.