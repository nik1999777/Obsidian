Функция `descendingOrder()` - сортирует числа в порядке убывания.

В данном решении:

- используется алгоритм - **Selection Sort**
- метод `join("")` - который возвращает строку путем объединения элементов массива
- унарный оператор `+` - который, если стоит перед строкой - превращает ее в числовой тип данных.

```JavaScript
function descendingOrder(n) {
  const splitString = n.toString().split("");

  for (let i = 0; i < splitString.length; i++) {
    let indexMin = i;

    for (let j = i + 1; j < splitString.length; j++) {
      if (splitString[j] > splitString[indexMin]) {
        indexMin = j;
      }
    }

    let tmp = splitString[i];
    splitString[i] = splitString[indexMin];
    splitString[indexMin] = tmp;
  }

  return +splitString.join("");
}

descendingOrder(122100033)
```

```JavaScript
/usr/local/bin/node /Users/nikitaelin/Desktop/test/script.js
332211000

Process finished with exit code 0
```