Функция `findShort()` - возвращает длину кратчайшего слова.

В данном решении:

- мы используем функцию `Math.min()` - которая возвращает наименьшее из чисел, заданных в качестве входных параметров
- далее метод `apply()` - который вызывает указанную функцию с заданным `this`значением и `arguments`предоставляется в виде массива `apply(thisArg, argsArray)`
- далее мы используем метод `split(" ")` - чтобы разбить строку на массив слов
- и используем метод `map()` - которым перебираем все элементы массив и применяем на каждом из них свойство `length`
- и по результату возвращаем длину кратчайшего слова

```JavaScript
function findShort(s) {
  return Math.min.apply(
    null,
    s.split(" ").map((w) => w.length)
  );
}

findShort("An object containing all of")
```

В данном решении:

- почти все то же самое, что и в прошлом - за исключением того, что используется spread оператор `…` - который позволяет расширить массив, где ожидается ноль или более аргументов.

```JavaScript
function findShort(s) {
  return Math.min(...s.split(" ").map((s) => s.length));
}

findShort("An object containing all of")
```

В данном решении:

- используем алгоритм - **Selection Sort**

```JavaScript
function findShort(s) {
  const arr = s.split(" ");
  let smallest = arr[0];
  for (let i = 0; i < arr.length; i++) {
    if (arr[i].length < smallest.length) {
      smallest = arr[i];
    }
  }
  return smallest.length;
}

findShort("An object containing all of")
```

В данном решени:

- мы сначала использовали метод `split(" ")` - для того, чтобы разбить строку на массив слов
- далее используем метод `sort()` , который сортирует массив - здесь мы вычитаем из `b` (второй элемент для сравнения) - `a` (первый элемент для сравнения), применив свойство `length`. И по итогу он возвращает нам отсортированный массив - `[ 'containing', 'object', 'all', 'An', 'of' ]`.
- и в заключении - используем метод массива`pop()`, который удаляет последний элемент и возвращает его значение и свойство - `length`

```JavaScript
const findShort = (s) =>
  s
    .split(" ")
    .sort((a, b) => b.length - a.length)
    .pop().length;

findShort("An object containing all of")
```

```JavaScript
/usr/local/bin/node /Users/nikitaelin/Desktop/test/script.js
2

Process finished with exit code 0
```