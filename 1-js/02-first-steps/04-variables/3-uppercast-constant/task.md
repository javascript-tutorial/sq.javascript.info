importance: 4

---

# Konstante me germa te medha?

Shqyrtoni kodin e mëposhtëm:

```js
const birthday = '18.04.1982';

const age = someCode(birthday);
```

Here we have a constant `birthday` date and the `age` is calculated from `birthday` with the help of some code (it is not provided for shortness, and because details don't matter here).
Këtu kemi konstantet `birthday` dhe `age` llogaritet nga `birthday` me ndihmën e një kodi (nuk është dhënë për shkurtim dhe sepse detajet nuk kanë rëndësi këtu).

A do të ishte e drejtë të përdoret shkronja e madhe për `birthday`? Për `age`? Apo edhe për të dyja?

```js
const BIRTHDAY = '18.04.1982'; // bëj shkronja të mëdha?

const AGE = someCode(BIRTHDAY); // bëj shkronja të mëdha?
```

