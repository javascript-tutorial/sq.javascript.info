
```js no-beautify
"" + 1 + 0 = "10" // (1)
"" - 1 + 0 = -1 // (2)
true + false = 1
6 / "3" = 2
"2" * "3" = 6
4 + 5 + "px" = "9px"
"$" + 4 + 5 = "$45"
"4" - 2 = 2
"4px" - 2 = NaN
7 / 0 = Infinity
"  -9  " + 5 = "  -9  5" // (3)
"  -9  " - 5 = -14 // (4)
null + 1 = 1 // (5)
undefined + 1 = NaN // (6)
" \t \n" - 2 = -2 // (7)
```

1. Shtimi me një string `"" + 1` konverton `1` në një string: `"" + 1 = "1"`, dhe më pas kemi `"1" + 0`, zbatohet i njëjti rregull.
2. Zbritja `-` (si shumica e operacioneve matematikore) funksionon vetëm me numra, ajo konverton një string bosh `""` në `0`.
3. Shtimi me stringu i shton stringut numrin `5`.
4. Zbritja gjithmonë shndërrohet në numra, kështu që e bën `" -9 "` një numër `-9` (duke shpërfillur hapësirat rreth tij).
5. 'null' bëhet '0' pas konvertimit numerik.
6. `undefined` behet `NaN` pas konvertimit numerik.
7. Karakteret e hapësirës, shkurtohen nga fillimi dhe mbarimi i vargut kur një varg konvertohet në një numër. Këtu i gjithë vargu përbëhet nga karaktere me hapsire, të tilla si `\t`, `\n` dhe një hapësirë "e rregullt" midis tyre. Pra, në mënyrë të ngjashme me një varg bosh, ai bëhet `0`.
