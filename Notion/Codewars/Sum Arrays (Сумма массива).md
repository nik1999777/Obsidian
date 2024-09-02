Функция `sum` - возвращает сумму всех чисел массива. Если `[]` и не число - то возвращает `0`.

В данном варианте решения:

- мы используем одно условие вне цикла `numbers.length === 0` - `[]`
- внутри цикла используем условие `typeof numbers[i] !== "number"`
- и внутри цикла суммируем все элементы массива - `sum += numbers[i]`

```JavaScript
function sum(numbers) {
  let sum = 0;

  if (numbers.length === 0) {
    return 0;
  }

  for (let i = 0; i < numbers.length; i++) {
    if (typeof numbers[i] !== "number") {
      return 0;
    }

    sum += numbers[i];
  }

  return sum;
}

sum([1, 5.2, 4, 0, -1]);
```

В данном варианте решения:

- мы используем функцию `reduce()` - которая принимает 2 аргумента:
    - `previousValue` `(sum)` - значение, полученное в результате предыдущего вызова `callbackFn`. При первом вызове - `initialValue`если он указан, если нет - значение `array[0]`.
    - `currentValue (current)` - значение текущего элемента. При первом вызове значение `array[0]` - если `initialValue`было указано, если нет - значение `array[1]`.
- `initialValue` - указали `0`, так как при [] - current обращается к arr[1], а если бы не указали - то получили бы ошибку, так как такого индекса в [] не существует.

```JavaScript
function sum(numbers) {
  return numbers.reduce((sum, current) => sum + current, 0);
}

sum([1, 5.2, 4, 0, -1])
```

```JavaScript
/usr/local/bin/node /Users/nikitaelin/Desktop/test/script.js
9.2

Process finished with exit code 0
```