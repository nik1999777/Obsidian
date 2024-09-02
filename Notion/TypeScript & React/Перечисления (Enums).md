  

Тип **Enum** - это такая сущность, которая помогает лучше структурировать однотипные элементы.

**Enum** представляет из себя некую смесь объекта и массива.

При обращении к значению **Enum** - возвращается его индекс. Это мы уже разобрали в предыдущем видео.

```TypeScript
// Simple example of enum type
enum Directions {
    Up,
    Down,
    Left,
    Right
}

Directions.Up;      // 0
Directions.Down;    // 1
Directions.Left;    // 2
Directions.Right;   // 3
```

Однако получить какие-то данные мы можем не только по значению, но и по ключу.

Такой подход называется - **Reverse enum**.

```TypeScript
// Reverse enum
enum Directions {
    Up,
    Down,
    Left,
    Right
}

Directions[0]	// "Up"
Directions[1]	// "Down"
Directions[2]	// "Left"
Directions[3]	// "Right"
```

Элементы в **Enum** - нумеруются.

По умолчанию эта нумерация начинается с 0 и идет по порядку.

Однако этот порядок мы можем изменять, задавая свой индекс.

```TypeScript
// Custom index for enum elements
enum Directions {
    Up = 2,
    Down = 4,
    Left = 6,
    Right = 8
}

Directions.Up;	// 2
Directions.Down;	// 4
Directions[6];	// Left
Directions[8];	// Right
```

Еще одна особенность - это более внятные имена для индексов.

То есть не просто какие-то порядковые имена - а действительно читаемые и интуитивно понятные значения.

```TypeScript
// Custom name for keys
enum links {
    youtube = 'https://youtube.com/',
    vk = 'https://vk.com/',
    facebook = 'https://facebook.com/'
}

// Using
links.vk        // "https://vk.com/"
links.youtube 	// "https://youtube.com/"
```

Довольно интересно посмотреть на результат компиляции.

Как мы можем видеть у нас создается анонимная самовызывающаяся функция, которая конструирует объект.

В нативном JS такого понятия как **Enum** - нет.

Поэтому из перечисляемых аргументов **Enum** - собирается объект, содержащий ключ и соответсвующее этому ключу значение.

```TypeScript
// Compiled code
"use strict";
var links;
(function (links) {
    links["youtube"] = "https://youtube.com/";
    links["vk"] = "https://vk.com/";
    links["facebook"] = "https://facebook.com/";
})(links || (links = {}));
```

Также если мы посмотрим на компилируемый код **Enum Directions**, в которой идет просто перечисление без задания имен - то мы может увидеть как реализован механизм удобного обращения по ключам и значениям.

Общий механизм создания тот же самый - только теперь вместо жесткого задания ключей объекта - у нас происходит конструирование объекта с перелинковкой на самого себя.

Это и есть тот механизм, который помогает обращаться к элементам набора и по значению и по индексу.

  

Также есть еще одна фича - это то как правильно создавать **Enum** тип и немного минимизировать выходной код:

Поскольку TS генерируется в JS - то ссылки к **Enum** всегда выполняются, как доступы к свойству и никогда не встраиваются.

Другими словами - просто написав **Enum** и описав его перечисляемые значения - мы всегда получим генерацию объекта через функцию, даже если этот объект в перспективе и не будет использоваться.

```TypeScript
// Compiled code
"use strict";
var Directions;
(function (Directions) {
    Directions[Directions["Up"] = 0] = "Up";
    Directions[Directions["Down"] = 1] = "Down";
    Directions[Directions["Left"] = 2] = "Left";
    Directions[Directions["Right"] = 3] = "Right";
})(Directions || (Directions = {}));
```

В большинстве своем такой подход является правильным, но если все таки стоят требования к минимизации и оптимизации ресурсов и мощностей - то можно воспользоваться константными перечислениями.

И если теперь посмотреть на сгенерируемый код - то он пуст.

У нас нет обращения к enum links, а соответсвенно создавать объект тоже не нужно.

```TypeScript
// const enum (without using)
const enum links {
    youtube = 'https://youtube.com/',
    vk = 'https://vk.com/',
    facebook = 'https://facebook.com/'
}

// Compiled code is empty
"use strict";
```

Но если мы попытаемся сделать обращение к какому-либо элементу **enum** (как в примере, создав массив arr и поместив туда элементы links.vk и links.facebook) - то только тогда в сгенерируемом коде мы получим значения.

И опять же обратите внимание - никакой генерации объекта нет.

В результирующем коде - мы просто получили соответсвующие ключам свойства.

```TypeScript
// const enum (with using)
const enum links {
    youtube = 'https://youtube.com/',
    vk = 'https://vk.com/',
    facebook = 'https://facebook.com/'
}

// Using of enum properties
const arr = [links.vk, links.facebook];

// Compiled code
"use strict";
const arr = ["https://vk.com/" /* vk */, "https://facebook.com/" /* facebook */];
```