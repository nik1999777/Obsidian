![[Untitled 103.png|Untitled 103.png]]

Специфический тип данных **null**, эта когда чего то просто не существует.

И **undefined** это когда что то существует, но значения у него никакого нет. (Например у вас стоит холодильник, но он абсолютно пустой)

**BigInt** - это такой тип данных, который отображает большие числа.

Является ли **массив** отдельным типом данных, на самом деле нет, **массив** это частный случай **объекта,** а не какой то отдельный тип данных.

**Массив** является комплексным типом данных и могут включать абсолютно любые типы данных.

**Объект** записывается в формате **ключ и значение**. **Ключ** это **свойство** **объекта**, а дальше значение этого **свойства**.

А если посмотреть на **массив**, то у нас есть только значение, мы описываем как то какие то элементы, которые идут по порядку, ключа нет. **Массивы** нужны, чтобы наши элементы располагались строго по порядку.

В программировании нумерация начинается с нуля!

  

[https://medium.com/@hydrock/bigint-%D0%BD%D0%BE%D0%B2%D1%8B%D0%B9-%D1%82%D0%B8%D0%BF-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85-%D0%B2-js-dd5c29446570](https://medium.com/%40hydrock/bigint-%D0%BD%D0%BE%D0%B2%D1%8B%D0%B9-%D1%82%D0%B8%D0%BF-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85-%D0%B2-js-dd5c29446570) - статья про **BigInt**

[https://learn.javascript.ru/symbol](https://learn.javascript.ru/symbol)  -  про **Symbol**

```JavaScript
"use strict";

let number = 4.6;

console.log(-4/0);
console.log('string' * 9);

const persone = '5';

const bool = false;

/* console.log(something); */

let und;
console.log(und);

const obj = {
    name: "John",
    age: 25,
    isMarried: false
};

console.log(obj.name);
/* console.log(obj["name"]); */

let arr = ['plum.png', 'orange.jpq', 6, 'apple.bmp', {}, []];
console.log(arr[1]);
```

![[Untitled 1 43.png|Untitled 1 43.png]]