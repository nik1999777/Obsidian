В данном коде функция `betterThanAverage()` - находит среднее значение среди элементов массива и возвращает `true` - если `yourPoints` > среднего значения.

В данном варианте решения:

- мы используем функцию `reduce()` - которая принимает 2 аргумента:
    - `previousValue` `(sum)` - значение, полученное в результате предыдущего вызова `callbackFn`. При первом вызове - `initialValue`если он указан, если нет - значение `array[0]`.
    - `currentValue (current)` - значение текущего элемента. При первом вызове значение `array[0]` - если `initialValue`было указано, если нет - значение `array[1]`.
- `initialValue` - указали `0`, так как при [] - current обращается к arr[1], а если бы не указали - то получили бы ошибку, так как такого индекса в [] не существует.

И далее делим на `classPoints.length` - чтобы узнать среднее значение среди элементов

```JavaScript
function betterThanAverage(classPoints, yourPoints) {
  return yourPoints > classPoints.reduce((a, b) => a + b, 0) / classPoints.length; 
}

betterThanAverage([2, 3, 1, 2, 7], 5)
```

В данном варианте решения:

- мы используем цикл `for` чтобы сложит все элементы в массиве
- и далее делим на `classPoints.length` - чтобы узнать среднее значение среди элементов

```JavaScript
function betterThanAverage(classPoints, yourPoints) {
  // Your code here
  let classAvg = 0;
  for (let i = 0; i < classPoints.length; i++){
    classAvg += classPoints[i]; 
  }
  classAvg = classAvg/classPoints.length; 
  return yourPoints > classAvg;
}

betterThanAverage([2, 3, 1, 2, 7], 5)
```

```JavaScript
/usr/local/bin/node /Users/nikitaelin/Desktop/test/script.js
true

Process finished with exit code 0
```