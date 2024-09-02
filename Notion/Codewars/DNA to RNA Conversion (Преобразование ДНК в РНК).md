  

В данном коде мы создали функцию `DNAtoRNA` - которая переводит заданную строку ДНК в РНК, то есть все `T` заменяет на `U` .

В данном варианте решения:

- мы используем метод `replace()`
- и регулярное выражение `reg`

```JavaScript
function DNAtoRNA(dna) {
  return dna.replace(/T/g, "U");
}

DNAtoRNA("TTTT")
```

В данном варианте решения:

- мы используем метод `split()`
- и цикл `for`
- и метод `join()`

```JavaScript
function DNAtoRNA(dna) {
  const arr = dna.split("");

  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === "T") {
      arr[i] = "U";
    }
  }

  return arr;
}

DNAtoRNA("TTTT")
```

В данном варианте решения:

- мы используем метод `split()`
- и метод `join()`

```JavaScript
function DNAtoRNA(dna) {
  return dna.split("T").join("U");
}

DNAtoRNA("TTTT")
```

```JavaScript
/usr/local/bin/node /Users/nikitaelin/Desktop/test/script.js
UUUU

Process finished with exit code 0
```