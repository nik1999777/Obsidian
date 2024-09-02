В данном коде функция `sumTwoSmallestNumbers` - возвращает нам сумму 2-х целых положительных чисел.

В данном решении:

- мы использовали алгоритм - `selection sort`
- и далее сложили первый и второй элемент уже отсотированного массива

```JavaScript
function sumTwoSmallestNumbers(numbers) {
  for (let i = 0; i < numbers.length; i++) {
    let indexMin = i;
    for (let j = i + 1; j < numbers.length; j++) {
      if (numbers[j] < numbers[indexMin]) {
        indexMin = j;
      }
    }

    if (indexMin !== i) {
      [numbers[i], numbers[indexMin]] = [numbers[indexMin], numbers[i]];
    }
  }

  return numbers[0] + numbers[1];
}

sumTwoSmallestNumbers([3, 87, 45, 12, 7]);
```

В данном решении:

- мы отсортировали массив с помощью метода `sort()`
- `a` и `b` - элементы сравнения

```JavaScript
function sumTwoSmallestNumbers(numbers) {
  numbers = numbers.sort((a, b) => a - b);
  return numbers[0] + numbers[1];
}
```

```JavaScript
/usr/local/bin/node /Users/nikitaelin/Desktop/test/script.js
10

Process finished with exit code 0
```