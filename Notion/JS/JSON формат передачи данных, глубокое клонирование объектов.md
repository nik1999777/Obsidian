[https://medium.com/@stasonmars/%D0%BA%D0%BE%D0%BF%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BE%D0%B1%D1%8A%D0%B5%D0%BA%D1%82%D0%BE%D0%B2-%D0%B2-javascript-d25c261a7aff](https://medium.com/@stasonmars/%D0%BA%D0%BE%D0%BF%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BE%D0%B1%D1%8A%D0%B5%D0%BA%D1%82%D0%BE%D0%B2-%D0%B2-javascript-d25c261a7aff) - **клонирование объектов**

[https://ru.wikipedia.org/wiki/HTTP](https://ru.wikipedia.org/wiki/HTTP) - **HTTP**

[https://ru.wikipedia.org/wiki/JSON](https://ru.wikipedia.org/wiki/JSON) - **JSON**

  

**JavaScript Object Notation**

**JSON** — текстовый формат обмена данными, основанный на JavaScript

Основной причиной популярности такого формата является маленький вес файлов и простота чтения.

Все современные браузеры имеют встроенный **объект JSON** для работы с этими **данными** и в этом встроенном **объекте** есть, как **свойства**, так и **методы**.

**Методов** существует 2.

Первый **метод** - это **stringify()**, который превращает **объекты** JS в нужный нам формат. Запускам код на картинке ниже и получаем в консоле **объект**, но самое главное, что соблюдается важное правило в **JSON** - все наши сущности записаны в двойных кавычках.

```JavaScript
const persone = {
    name: 'Alex',
    tel: '+744444444'
};

console.log(JSON.stringify(persone));
```

```JavaScript
[Running] node "/Users/nikitaelin/Desktop/work/JS_React/react/my-app/src/tempCodeRunnerFile.js"
{"name":"Alex","tel":"+744444444"}

[Done] exited with code=0 in 0.128 seconds
```

А теперь обратная ситуация: нам с **сервера** приходит **JSON** и нам необходимо превратить его в обычный **объект** в нашем скрипте, и далее как-то использовать. И для этого существует **2 метод**, который называется **parse()**. Запускаем код и видим, что в результате всех действий мы получаем обратно обычный **объект**.

```JavaScript
const persone = {
    name: 'Alex',
    tel: '+744444444'
};

console.log(JSON.parse(JSON.stringify(persone)));
```

```JavaScript
[Running] node "/Users/nikitaelin/Desktop/work/JS_React/react/my-app/src/tempCodeRunnerFile.js"
{ name: 'Alex', tel: '+744444444' }

[Done] exited with code=0 in 0.114 seconds
```

С помощью JSON можно создавать **глубокие копии объектов**. Используя методы **stringify()** и **parse()** мы создаем **глубокий клон**, который совершенно не зависит от первоначального **объекта**.

```JavaScript
const persone = {
    name: 'Alex',
    tel: '+744444444',
    parents: {
        mom: 'Olga',
        dad: 'Mike'
    }
};

const clone = JSON.parse(JSON.stringify(persone));
clone.parents.mom = 'Ann';
console.log(persone);
console.log(clone);
```

```JavaScript
[Running] node "/Users/nikitaelin/Desktop/work/JS_React/react/my-app/src/tempCodeRunnerFile.js"
{
  name: 'Alex',
  tel: '+744444444',
  parents: { mom: 'Olga', dad: 'Mike' }
}
{
  name: 'Alex',
  tel: '+744444444',
  parents: { mom: 'Ann', dad: 'Mike' }
}

[Done] exited with code=0 in 0.056 seconds
```