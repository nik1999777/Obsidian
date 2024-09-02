Функция `countSheeps()` - функция, которая подсчитывает кол-во овец (true).

В данном решении:

- мы создаем переменную - `let count`
- далее с помощью метода перебора массива `forEach()` при `element === true` - увеличиваем `count` на `count + 1`
- и по итогу возвращаем кол-во овец (true) - `return count`

```JavaScript
function countSheeps(arrayOfSheep) {
  let count = 0;
  arrayOfSheep.forEach((element, index) => {
    if (element === true) {
      count += 1;
    }
  });

  return count;
}

countSheeps([true, false, true, false])
```

В данном решении:

- используем метод массива `filter()` - который возвращает массив, отфильтрованный данным условием - `item === true`
- и далее используем свойство `length` - для подсчета элементов массива

```JavaScript
function countSheeps(arrayOfSheep) {
  return arrayOfSheep.filter((item) => item === true).length;
}

countSheeps([true, false, true, false])
```

```JavaScript
/usr/local/bin/node /Users/nikitaelin/Desktop/test/script.js
2

Process finished with exit code 0
```