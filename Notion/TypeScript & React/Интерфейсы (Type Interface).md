3  

Основным принципом TS - является проверка типов, основанная на форме значений.

Такой подход иногда называется - структурным под типированием или утиной типизацией.

  

В TS - **интерфейсы** как раз и выполняют функцию именования типов.

Определяются они - с помощью ключевого слова **interface**.

Визуально - это тот же самый объект, однако в действительности - это над объектная сущность, которая помогает описать форму объекта (или то как он будет выглядеть в будущем).

Это немного похоже на абстрактный класс и на определение типа с помощью ключевого слова **Type**.

```TypeScript
// Simple interface example
interface User {
    name: string,
    age: number,
}
```

Мы можем написать примерно такие варианты описания формы объекта - использовать **interface** и **type**.

Однако между 2-мя этими подходами существует принципиальная разница:

- **Type** задает псевдоним для любой разновидности типа, включая примитивы. То есть - это механизм создания псевдонима для любого типа.
- **Interface** - представляет из себя именованный тип объекта и обеспечивает мощный способ определения сущностей.

Также **Interface** может наследоваться и расширяться другими интерфейсами.

Вообщем и целом способностей у **Interface** намного больше, чем у **Type**.

```TypeScript
// Interface & Type
interface User {
    name: string,
    age: number,
}

type User {
    name: string,
    age: number,
}
```

В **Interface** любое свойство не помеченное, как **опциональное** - по умолчанию является обязательным.

```TypeScript
// Interface optional property
interface User {
    name: string,
    age?: number,	// <--- Optional
}

// Creation with a required property
const yauhen: User = {
    name: 'Yauhen',
}

// Creation with missing a required property
/*
  Error:
  Property 'name' is missing in type '{ age: number; }' but required in type 'User'
*/
const max: User = {
    age: 20,
}
```

Следующая фича - это **блокировка** **изменений**.

Для того чтобы случайно не изменить свойство нашего объекта - можно воспользоваться **модификатором** **readonly**.

И в таком случае при попытки внести изменения - мы получим ошибку о том, что пытаемся изменить свойство, предназначенное только для чтения.

```TypeScript
// Interface 'readonly' modifier
interface User {
    readonly name: string,
    age: number,
}

const yauhen: User = {
    name: 'Yauhen',
    age: 31,
}

yauhen.age = 30;
yauhen.name = 'Max'; // Cannot assign to 'name' because it is a read-only property
```

Что делать, если нам необходимо расширение объекта?

Самый простой способ - это добавление **строкового** **индекса**.

Применяя такой подход - мы даем полную свободу при расширении объекта.

```TypeScript
// Interface extension
interface User {
    name: string,
    age: number,
    [propName: string]: any;
}

const yauhen: User = {
    name: 'Yauhen',
    age: 31,
    nickName: 'webDev',
    justTest: 'test',
}
```

Как говорилось ранее - **интерфейсы** помогают создавать описание различных сущностей в TS и классы не являются исключением.

В примере мы можем видеть 3 особенности:

- во-первых - **интерфейс** может содержать описание метода, который будет реализован внутри класса.
- во-вторых - если класс создается на основании определенного типа **интерфейса**, то делается это с помощью ключевого слова **implements**.
- в-третьих - в классе есть дополнительное свойство nickName, которое не определено в **интерфейсе**. Однако сам класса по прежнему валиден. И тут суть **интерфейса** в том, что мы должны реализовать минимальный набор необходимых параметров, остальные же параметры могут присутствовать абсолютно в любом кол-ве.

```TypeScript
// Class Interface
interface User {
    name: string,
    age: number,
    getPass(): string,
}

class Yauhen implements User {
    name: string = 'Yauhen';
    age: number = 31;
    nickName: string = 'webDev';

    getPass() {
        return `${this.name}${this.age}`;
    }
}
```

Еще одна особенность - это создание классов на основании нескольких **интерфейсов**.

Класс Yauhen - точно такой же как и в предыдущем примере, однако он создается от 2-х **интерфейсов** - User и Pass.

И в Pass мы просто вынесли - описание метода getPass().

```TypeScript
// Create Class based on multiple interfaces
interface User {
    name: string,
    age: number,
}

// Separate interface with one method
interface Pass {
    getPass(): string,
} 

class Yauhen implements User, Pass {
    name: string = 'Yauhen';
    age: number = 31;

    getPass() {
        return `${this.name}${this.age}`;
    }
}
```

И последняя особенность **интерфейса**, которую мы рассмотрим - это их расширение.

У нас есть наш базовый **интерфейс** - User и на основании его мы создаем новый - Admin.

И далее создаем класс Yauhen на основании расширенного **интерфейса** Admin.

```TypeScript
// Interface extends
interface User {
    name: string,
    age: number,
}

// Interface extends
interface Admin extends User {
    getPass(): string,
}

class Yauhen implements Admin {
    name: string = 'Yauhen';
    age: number = 31;

    getPass() {
        return `${this.name}${this.age}`;
    }
}
```