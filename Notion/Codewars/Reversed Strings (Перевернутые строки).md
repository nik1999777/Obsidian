Функция `reverseString()` - переворачивает строку.

В даном варианте решения:

- с помощью метода `split("")` - разбиваем строку на массив символов
- далее с помощью метода `reverse()` - переворачиваем массив
- и в конце с помощью метода `join("")` - возвращаем строку путем объединения элементов массива

```JavaScript
function reverseString(str) {
  const splitString = str.split("");

  const reverseArray = splitString.reverse();

  const joinArray = reverseArray.join("");

  return joinArray;

	//return str.split("").reverse().join("")
}

reverseString("world");
```

В этом решении:

- создаем переменную `let newString = ""`
- далее с помощью цикла `for` - мы перебираем массив в обратном порядке.

```JavaScript
function reverseString(str) {
  let newString = "";

  for (let i = str.length - 1; i >= 0; i--) {
    newString += str[i];
  }

  return newString;
}

reverseString("world");
```

```JavaScript
/usr/local/bin/node /Users/nikitaelin/Desktop/test/script.js
dlrow

Process finished with exit code 0
```