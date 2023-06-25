# Menyra moderne, "use strict"

Për një kohë të gjatë, JavaScript zhvillohej pa probleme të përputhshmërisë. Vlera shtesë u shtuan në gjuhë ndërsa funksionaliteti i vjetër nuk ndryshoi.

Kjo kishte përfitimin e mosprishjes së kodit ekzistues. Por disavantazhi ishte se çdo gabim ose vendim i paregullt i krijuar i JavaScript-it mbetej aty përgjithmonë.

Kjo ishte ceshtja deri në vitin 2009 kur u paraqit ECMAScript 5 (ES5). Ai shtoi vlera të reja në gjuhë dhe ndryshoi disa prej atyre ekzistuese. Për të ruajtur funksionalitetin e kodit të vjetër, shumica e këtyre ndryshimeve janë të çaktivizuara si parazgjedhje. Ju duhet të aktivizoni ato në mënyrë të qartë me anë të një udhëzimi të veçantë: `"use strict"`.

## "use strict"

Udhëzimi duket si një string: `"use strict"` ose `'use strict'`. Ai gjendet në fillim të një skripti, gjithë skripti funksionon në mënyrën "moderne".

Për shembull:

```js
"use strict";

// ky kod punon në mënyrën moderne.
...
```

Së shpejti do të mësojmë për funksionet (një mënyrë për të grupuar komandat), kështu që të shënojmë paraprakisht se `"use strict"` mund të vendoset në fillim të një funksioni. Duke bërë këtë, aktivizohet mënyra e strict në atë funksion vetëm. Por zakonisht njerëzit e përdorin për gjithë skriptin.

````warn header="Për të garantuar që \"use strict\" eshte ne fillim"
Ju lutem sigurohuni që `"use strict"` është në fillim të skripteve tuaja, në të kundërtën, script mode nuk do të aktivizohet.

Strict mode nuk eshte e aktivizuar ketu:

```js no-strict
alert("disa kode");
// "use strict" do te injorohet--ai duhet te jete ne fillim

"use strict";

// strict node nuk eshte aktivizuar
```

Vetëm komentet mund të shfaqen mbi `"use strict"`..
````

```warn header="Nuk ka menyre per te kanceluar `use strict`"
Nuk ka nje direktive te tille si `"no use strict"` Kjo rikthen motorin në sjelljen e vjetër.

Pasi hyjmë në strict mode, nuk kemi mundësi të kthehemi mbrapa.
```

## Console i shfletuesit

Kur përdorni një [developer console](info:devtools) për të ekzekutuar kod, vini re se kjo nuk përdor `use strict` si parazgjedhje.

Ndonjëherë, kur `use strict` bën një ndryshim, mund të merrni rezultate të pasakta.

Pra, Si te perdorim `use strict` ne console?

First, you can try to press `key:Shift+Enter` to input multiple lines, and put `use strict` on top, like this:
Së pari, mund të provoni të shtypni `key:Shift+Enter` për të vendosur disa rreshta të kodit dhe të vendosni `use strict` në fillim, si në këtë shembull:


```js
'use strict'; <Shift+Enter per nje rresht te ri>
//  ...kodi juaj
<Enter to run>
```

Kjo veprimtari funksionon në shumicën e shfletuesve, në veçanti Firefox dhe Chrome.
Nëse kjo nuk funksionon, për shembull në shfletues të vjetër, ka një mënyrë tjeter, por e sigurtë për të perdorur `use strict`. Vendosni kodin brenda kësaj forme:

```js
(function() {
  'use strict';

  // ...kodi juaj ketu...
})()
```

##  Duhet te perdorim "use strict"?

Pyetja mund të tingëllojë e thjeshtë, por nuk është gjithmonë kështu.

Një rekomandim është të filloni skriptet me `"use strict"`... Por, e dini çfarë është interesante?

JavaScript-i modern suporton "klasat" dhe "modulet" - struktura të avancuara të gjuhës (sigurisht që do t'i mësojmë më vonë), që aktivizojnë "use strict" automatikisht. Prandaj, nuk kemi nevojë të shtojmë direktiven `"use strict"`, nëse i përdorim ato.

**Kështu, për tani `"use strict";` është një mysafir i mirë në fillim të skripteve tuaja. Më vonë, kur kodi juaj është i gjithi në klase dhe module, mund ta lini pa e përdorur.**

Deri tani, kemi mësuar për `use strict` në përgjithësi.

Në kapitujt e ardhshëm, siç mësojmë për karakteristikat e gjuhës, do të shohim dallimet midis strict mode dhe mënyrës së vjetër. Fatmirësisht, ato nuk janë shumë dhe në të vërtetë përmirësojnë punen tonë.

Të gjitha shembujt në këtë mesim supozojnë që strict mode është e aktivizuar, përveç rasteve kur është shënuar ndryshe (rrallë).
