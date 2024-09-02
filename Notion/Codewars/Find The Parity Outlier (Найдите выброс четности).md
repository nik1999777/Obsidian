Функцию `findOutlier()` - принимает массив, который полностью состоит из четных или нечетных чисел - за исключением одного числа N, который она и возвращает.

В данном решении:

- мы создаем 2 переменные `evens` и `odds`, в которых лежат 2 пустых массива
- далее создается цикл `for`, который будет перебирать каждый элемент массива integers
- в цикле будет условие `((integers[i] % 2) === 0)` - если каждый элемент массива `integers[i]` разделенный на `2` будет строго равне `0`:
    - то он добавится в конец пустого массива `evens` - `evens.push(integers[i])`
    - если нет, то добавится в конец пустого массива `odds` - `odds.push(integers[i])`
- далее в нашей функции идет другое условие `(odds.length > evens.length)` - если кол-во элементов в массиве `odds` больше чем кол-во элементов в массиве `evens`:
    - то будет возвращаться первый элемент массива `evens` - `return evens[0]`
    - если нет, то первый элемент массива `odds` - `return odds[0]`

```JavaScript
function findOutlier(integers) {
  const evens = [];
  const odds = [];

  for (let i = 0; i < integers.length; i++) {
    if ((integers[i] % 2) === 0) {
      evens.push(integers[i]);
    } else {
      odds.push(integers[i]);
    }
  }

  if (odds.length > evens.length) {
    return evens[0];
  } else {
    return odds[0];
  }
}

findOutlier([2, 4, 0, 100, 4, 11, 2602, 36]);
```

```JavaScript
/usr/local/bin/node /Users/nikitaelin/Desktop/test/script.js
11

Process finished with exit code 0
```