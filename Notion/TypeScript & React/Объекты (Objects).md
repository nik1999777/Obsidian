  

Самый простой способ с помощью которого можно определить тип объекта - это использовать тип **any**.

**any** - определяет любой тип.

Технически - это очень универсальный подход, но проблема в том, что такой способ не дает нам раскрыть потенциал TS.

```TypeScript
// Object type using any
let user: any = {
    name: 'Yauhen',
    age: 30,
};
```

Вспомним такой тип как **Array**.

```TypeScript
let list: Array<number> = [1, 2, 3];
```

С **объектами** ситуация обстоит точно также - поэтому по аналогии мы можем выполнить следующую типизацию:

```TypeScript
// Define object type
let user: { name: string, age: number, nickName: string } = {
    name: 'Yauhen',
    age: 30,
    nickName: 'webDev',
};
```

Представим, что у нас 2 одинаковых объекта - с одинаковыми полями и описанными типами.

И чтобы не повторяться и не нарушать принцип **DRY** - мы воспользуемся ключевым словом **type** с помощью которого мы создадим **пользовательский тип**.

И после чего этот тип - мы присвоим к каждому из объектов.

```TypeScript
// Using Type for objects structure
type Person = { name: string, age: number, nickName: string };

// Apply Person type for objects with the same structure
let user: Person = {
    name: 'Yauhen',
    age: 30,
    nickName: 'webDev',
};

let admin: Person = {
    name: 'Max',
    age: 20,
    nickName: 'Mad',
};
```

А что же делать, если структура объектов в целом похожая, но есть небольшие отличия?

Мы можем немного модифицировать уже существующий тип Person.

Мы оставили свойство nickName, добавили метод getPass - и каждый из типов пометили с помощью **вопросительного** **знака**, как **опциональный**.

```TypeScript
// Updating type with optional properties
type Person = {
    name: string,
    age: number,
    nickName?: string,
    getPass?: () => string,
};
```

Таким образом можно выделить плюс использования TS - гибкость при создании типов.