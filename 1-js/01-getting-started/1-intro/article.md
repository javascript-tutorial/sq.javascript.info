# Një hyrje në JavaScript

Le të shohim se çfarë është kaq e veçantë për JavaScript, çfarë mund të arrijmë me të, dhe cilat teknologji të tjera luajnë mirë me të.

## Çfarë është JavaScript?

*JavaScript* u krijua fillimisht për t'i "bërë ueb faqet të gjalla".

Programet në këtë gjuhë janë quajtur *skripta*. Ato mund të shkruhen drejtpërdrejt në HTML të një ueb faqe dhe të ekzekutohen automatikisht kur faqja ngarkohet.

Skriptet sigurohen dhe ekzekutohen si tekst i thjeshtë. Ata nuk kanë nevojë për përgatitje ose përpilim të veçantë për t'u ekzekutuar.

Në këtë aspekt, JavaScript është shumë e ndryshme nga një gjuhë tjetër të quajtur [Java](https://en.wikipedia.org/wiki/Java_(programming_language)).

```smart header="Pse quhet <u>Java</u>Script?"
Kur u krijua JavaScript, ajo fillimisht kishte një emër tjetër: "LiveScript". Por Java ishte shumë e njohur në atë kohë, kështu që u vendos që pozicionimi i një gjuhe të re si një "vëlla më i ri" i Java do të ndihmonte.

Por ndërsa evoluoi, JavaScript u bë një gjuhë plotësisht e pavarur me specifikimet e veta të quajtura [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript), dhe tani nuk ka asnjë lidhje me Java.
```

Sot, JavaScript mund të ekzekutojë jo vetëm në shfletuesin, por edhe në server, ose në të vërtetë në çdo pajisje që ka një program të veçantë të quajtur [the JavaScript engine](https://en.wikipedia.org/wiki/JavaScript_engine).

Shfletuesi ka një motor të ngulitur që nganjëherë quhet "JavaScript virtual machine".

Motorë të ndryshëm kanë "emra të koduar" të ndryshëm. Për shembull:

- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- në Chrome dhe Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- në Firefox.
- ...Ekzistojnë emra të tjerë të koduar si "Chakra" për IE, "ChakraCore" për Microsoft Edge, "Nitro" dhe "SquirrelFish" për Safari, etj.

Termat e mësipërm janë të mira për tu mbajtur mend sepse ato përdoren në artikuj të zhvilluesve në internet. Ne gjithashtu do t'i përdorim ato. Për shembull, nëse "një tipar X mbështetet nga V8", atëherë ai ndoshta funksionon në Chrome dhe Opera.

```smart header="Si funksionojnë motorët?"

Motorët janë të komplikuar. Por bazat janë të lehta.

1. Motori (i ngulitur nëse është shfletues) lexon ("analizon") skenarin.
2. Pastaj shndërron ("përpilon") shkrimin në gjuhën e makinës.
3. Dhe pastaj kodi i makinës funksionon, shumë shpejt.

Motori aplikon optimizime në secilin hap të procesit. Ai madje shikon skenarin e përpiluar ndërsa ekzekutohet, analizon të dhënat që rrjedhin përmes tij dhe optimizon më tej kodin e makinës bazuar në ato njohuri.
```

## Çfarë mund të bëjë in-browser JavaScript?

JavaScriptja moderne është një gjuhë programimi "e sigurt". Ajo nuk ofron qasje të nivelit të ulët të kujtesës ose CPU, sepse ajo u krijua fillimisht për shfletuesit të cilat nuk kërkojnë atë.

Aftësitë e JavaScript varen shumë nga mjedisi ku po ekzekutohet. Për shembull, [Node.js](https://wikipedia.org/wiki/Node.js) mbështet funksione që lejojnë JavaScript të lexojë / shkruajë skedarë arbitrar, të kryejë kërkesa në rrjet, etj.

In-browser JavaScript mund të bëjë gjithçka që lidhet me manipulimin e ueb faqes, ndërveprimin me përdoruesin dhe ueb serverin.

Për shembull, in-browser JavaScript është në gjendje të:

- Të shton HTML të ri në faqe, ndryshoni përmbajtjen ekzistuese, modifikoni stilet.
- Të reagojë ndaj veprimeve të përdoruesit, të ekzekutohet në klikime të miut, lëvizje të treguesit, shtypje çelësash.
- Të dërgon kërkesa përmes rrjetit në serverë të largët, shkarkoni dhe ngarkoni skedarë (të ashtuquajturën [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) dhe [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) teknologjive).
- Për të marrë dhe vendosur cookies, bëj pyetje vizitorit, shfaq mesazhe.
- Për të kujtuar të dhënat në anën e klientit ("local storage").

## Çfarë nuk mund të bëjë in-browser JavaScript?

Aftësitë e JavaScriptit në shfletues janë të kufizuara për hir të sigurisë së përdoruesit. Qëllimi është të parandalojë një faqe të keqe në internet që të ketë informacion privat ose të dëmtojë të dhënat e përdoruesit.

Shembuj të kufizimeve të tilla përfshijnë:

- JavaScript në një faqe në internet mund të mos lexojë / shkruajë skedarë arbitrarë në hard disk, t'i kopjojë ato ose të ekzekutojë programe. Nuk ka qasje të drejtpërdrejtë në funksionet e sistemit operativ.

    Shfletuesit modernë e lejojnë atë të punojë me skedarë, por hyrja është e kufizuar dhe sigurohet vetëm nëse përdoruesi bën veprime të caktuara, si "hedhja" e një skedari në një dritare të shfletuesit ose zgjedhja e tij përmes një etikete "<input>".

    Ka mënyra për të bashkëvepruar me kamerën / mikrofonin dhe pajisjet e tjera, por ato kërkojnë leje të qartë të përdoruesit. Kështu që një faqe e aktivizuar në JavaScript mund të mos mundësojë fshehurazi një kamerë në internet, të vëzhgojë rrethinën dhe të dërgojë informacionin te [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Skeda / dritare të ndryshme zakonisht nuk dinë për njëri-tjetrin. Ndonjëherë ato e bëjnë, për shembull kur një dritare përdor JavaScript për të hapur tjetrën. Por edhe në këtë rast, JavaScript nga një faqe mund të mos ketë qasje në tjetrën nëse ato vijnë nga faqe të ndryshme (nga një domen, protokoll ose port i ndryshëm).

    Kjo quhet "Politika e Origjinës së Njëjtë". Për të punuar rreth kësaj, * të dy faqet * duhet të bien dakord për shkëmbimin e të dhënave dhe të përmbajnë një kod të veçantë JavaScript që e trajton atë. Ne do ta trajtojmë atë në tutorial.

    Ky kufizim është, përsëri, për sigurinë e përdoruesit. Një faqe nga `http://anysite.com` që një përdorues ka hapur nuk duhet të jetë në gjendje të përdorë një skedar tjetër të shfletuesit me URL-në` http://gmail.com` dhe të vjedhë informacionin prej andej.
- JavaScript mund të komunikojë lehtësisht përmes rrjetit me serverin nga ka ardhur faqja aktuale. Por aftësia e tij për të marrë të dhëna nga faqet / fushat e tjera është e gjymtuar. Megjithëse është e mundur, ajo kërkon marrëveshje të qartë (shprehur në headers HTTP) nga ana e largët. Edhe një herë, ky është një kufizim i sigurisë.

![](limitations.svg)

Kufij të tillë nuk ekzistojnë nëse JavaScript përdoret jashtë shfletuesit, për shembull në një server. Shfletuesit modernë lejojnë gjithashtu shtojca / shtesa të cilat mund të kërkojnë leje të zgjatura.

## Çfarë e bën JavaScript unike?

Ka të paktën * tre * gjëra të mrekullueshme në lidhje me JavaScript:

```compare
+ Integrimi i plotë me HTML / CSS.
+ Gjërat e thjeshta bëhen thjesht.
+ Mbështetje nga të gjithë shfletuesit kryesorë dhe mundësohet nga default.
```
JavaScript është e vetmja teknologji e shfletuesit që kombinon këto tre gjëra.

Kjo është ajo që e bën JavaScript unike. Kjo është arsyeja pse është mjeti më i përhapur për krijimin e ndërfaqeve të shfletuesit.

Thënë kjo, JavaScript lejon gjithashtu krijimin e serverave, aplikacioneve mobile, etj.

## Gjuhët "mbi" JavaScript

Sintaksa e JavaScript nuk i përshtatet nevojave të të gjithëve. Njerëz të ndryshëm duan tipare të ndryshme.

Kjo pritet, sepse projektet dhe kërkesat janë të ndryshme për të gjithë.

Kohët e fundit u shfaq një bollëk gjuhësh të reja, të cilat * transpilohen * (konvertohen) në JavaScript para se të ekzekutohen në shfletues.

Mjetet moderne e bëjnë transpilimin shumë të shpejtë dhe transparent, duke lejuar në fakt zhvilluesit të kodojnë në një gjuhë tjetër dhe ta konvertojnë automatikisht atë "nën kapuç".

Shembuj të gjuhëve të tilla:

- [CoffeeScript](http://coffeescript.org/) është një "sheqer sintaksor" për JavaScript. Ajo paraqet sintaksë më të shkurtër, duke na lejuar të shkruajmë kod më të qartë dhe më të saktë. Zakonisht, Ruby devs e pëlqejnë.
- [TypeScript](http://www.typescriptlang.org/) është përqendruar në shtimin e "shtypjes së saktë të të dhënave" për të thjeshtuar zhvillimin dhe mbështetjen e sistemeve komplekse. Është zhvilluar nga Microsoft.
- [Flow](http://flow.org/) gjithashtu shton shtypjen e të dhënave, por në një mënyrë tjetër. Zhvilluar nga Facebook.
- [Dart](https://www.dartlang.org/) është një gjuhë e pavarur që ka motorin e vet që funksionon në mjedise pa shfletues (si aplikacionet për celularë), por gjithashtu mund të transmetohet në JavaScript. Zhvilluar nga Google.
- [Brython](https://brython.info/) është një transportues Python në JavaScript që lejon të shkruash aplikacion në Python të pastër pa JavaScript.

Ka më shumë. Sigurisht, edhe nëse përdorim një nga gjuhët e transpiluara, duhet të dimë gjithashtu JavaScript për të kuptuar me të vërtetë se çfarë po bëjmë.

## Përmbledhje

- JavaScript u krijua fillimisht si gjuhë vetëm për shfletuesin, por tani përdoret gjithashtu në shumë mjedise të tjera.
- Sot, JavaScript ka një pozicion unik si gjuha e shfletuesit më e pranuar gjerësisht me integrimin e plotë me HTML / CSS.
- Ka shumë gjuhë që "transpilohen" në JavaScript dhe ofrojnë veçori të caktuara. Rekomandohet të hidhni një vështrim në to, të paktën shkurtimisht, pasi të zotëroni JavaScript.
