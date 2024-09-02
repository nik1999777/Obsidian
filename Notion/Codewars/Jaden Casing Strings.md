В данном коде - мы создали метод, который является прототипом объекта - string.

Метод `toJadenCase()` - возвращает строку, в которой все слова начинаются с заглавной буквы.

В данном варианте решения:

- с помощью метода `split(" ")` - разбиваем строку на массив слов.
- далее с помощью метода `map()` - перебираем каждый элемент массива
- далее с помощью метода `charAt(0)` - возвращаем новую строку состоящую из 0-го индекса каждого элемента массива и делаем ее заглавную с помощью метода `toUpperCase()`
- и далее прибавляем оставшуюся часть слова (то есть без первой буквы) - с помощью метода `slice(1)`
- и в конце с помощью метода `join(" ")` - возвращаем строку путем объединения всех элементов массива

```JavaScript
String.prototype.toJadenCase = function () {
  return this.split(" ")
    .map(function (word) {
      return word.charAt(0).toUpperCase() + word.slice(1);
    })
    .join(" ");
};

const string = "jaden smith is the best man!";
string.toJadenCase()
```

В данном варианте решения:

- мы используем метод `replace()` - который заменяет одну строку на другую, если находит совпадения.
- в данном случае у нас первым аргументом является не строка, а регулярное выражение:
    - `^` - этот символ нужен для сопоставления c началом ввода
    - `\s` - этот символ нужен для сопоставления с одиночным пробельным символом
    - `[a-z]` - квадратные скобки могут содержать диапазоны символ, к примеру данная конструкция соответствует символу в диапазоне от `a`до `z`
    - `/g` - этот флаг означает глобальное сопоставление (то есть, когда мы пытаемся найти несколько вхождений)
- и далее внутри метода `replace()` - во втором аргументом мы callback функцию, которая используем метод `toUpperCase()`

```JavaScript
String.prototype.toJadenCase = function () {
  return this.replace(/(^|\s)[a-z]/g, function (x) {
    return x.toUpperCase();
  });
};

const string = "jaden smith is the best man!";
string.toJadenCase()
```

В данном варианте решение такое же как и во втором - за исключением того, что к первому индексу элемента массива обращаются через `item[0]`.

```JavaScript
String.prototype.toJadenCase = function () {
  return this.split(" ")
    .map((item) => item[0].toUpperCase() + item.slice(1))
    .join(" ");
};

const string = "jaden smith is the best man!";
string.toJadenCase()
```

```JavaScript
/usr/local/bin/node /Users/nikitaelin/Desktop/test/script.js
Jaden Smith Is The Best Man!

Process finished with exit code 0
```