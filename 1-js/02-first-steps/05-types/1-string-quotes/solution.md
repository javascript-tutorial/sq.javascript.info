
Backticks vendosin shprehjen brenda `${...}` stringut.

```js run
let name = "Ilya";

// shprehja është një numër 1
alert( `hello ${1}` ); // hello 1

// shprehja eshte nje string "name"
alert( `hello ${"name"}` ); // hello name

// shprehja eshte nje variabel, e bashkojme ate
alert( `hello ${name}` ); // hello Ilya
```
