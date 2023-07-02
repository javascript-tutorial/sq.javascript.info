Arsyeja është se prompt kthen hyrjen e përdoruesit si një string.

Pra, variablat kanë respektivisht vlerat `"1"` dhe `"2"`.

```js run
let a = "1"; // prompt("Numeri i pare?", 1);
let b = "2"; // prompt("Numeri i dyte?", 2);

alert(a + b); // 12
```

What we should do is to convert strings to numbers before `+`. For example, using `Number()` or prepending them with `+`.
Ajo që duhet të bëjmë është të konvertojmë stringjet në numra përpara `+`. Për shembull, duke përdorur `Number()` ose duke i vendosur ato me `+`.

Për shembull, menjëherë përpara `prompt`:

```js run
let a = +prompt("First number?", 1);
let b = +prompt("Second number?", 2);

alert(a + b); // 3
```

Ose e vendosim ne alert `alert`:

```js run
let a = prompt("First number?", 1);
let b = prompt("Second number?", 2);

alert(+a + +b); // 3
```

Përdorimi i `+` unary dhe binar në kodin më të fundit. Duket qesharake, apo jo?
