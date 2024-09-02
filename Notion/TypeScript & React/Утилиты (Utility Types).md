  

TS предоставляет 16 утилит для упрощения базовых преобразований типов.

  

**Readonly**

С помощью этой утилиты - мы можем создать тип, все свойства которого будут предназначены только для чтения.

В примере при попытке переопределить свойство name - мы получаем ошибку.

```TypeScript
// Readonly<T>
interface User {
    name: string;
}

const user: Readonly<User> = {
    name: 'Yauhen',
};

user.name = 'Max';      // Error: cannot reassign a readonly property
```

**Required**

Данная утилита позволяет создать тип, все поля которого становятся обязательными.

В примере при создании первого объекта с интерфейсом Props - мы не получаем никаких ошибок, так как оба свойства - опциональные.

Но когда мы пытаемся создать 2 объект, используя утилиту - то получаем ошибку, так как уже в этом случае 2 свойство становится обязательным.

```TypeScript
// Required<T>
interface Props {
    a?: number;
    b?: string;
};

const obj: Props = { a: 5 };              // OK

const obj2: Required<Props> = { a: 5 };   // Error: property 'b' missing
```

**Record**

Утилита, которая создает тип с набором свойств Page - типа PageInfo.

В примере у нас есть набор типов - 'home' | 'about' | 'contact' и interface PageInfo.

Далее мы создаем const x, где с помощью утилиты **Record** - создаем набор соответствующего типа.

На выходе мы получаем объект, каждому свойству которого соответсвует объект связанного значения.

Также эту утилиту можно использовать для сопоставления свойств одного типа к другому.

```TypeScript
// Record<K, T>
interface PageInfo {
    title: string;
}

type Page = 'home' | 'about' | 'contact';

const x: Record<Page, PageInfo> = {
    about: { title: 'about' },
    contact: { title: 'contact' },
    home: { title: 'home' },
};
```

**Pick**

Эта утилита очень похожа на предыдущую, затем лишь исключением, что она создает тип, выбирая заданные нами свойства из интерфейса Todo - у нас это title и completed.

По факту мы конструируем объект - только из выбранных типов.

```TypeScript
// Pick<T, K>
interface Todo {
    title: string;
    description: string;
    completed: boolean;
}

type TodoPreview = Pick<Todo, 'title' | 'completed'>;

const todo: TodoPreview = {
    title: 'Clean room',
    completed: false,
};
```

**Omit**

Он позволяет удалять ненужные свойства у объекта.

```TypeScript
// Omit<T, K>
interface Todo {
    title: string;
    description: string;
    completed: boolean;
}

type TodoPreview = Omit<Todo, 'description'>;

const todo: TodoPreview = {
    title: 'Clean room',
    completed: false,
};
```

**Exclude**

Данная утилита создает тип, исключая из него все типы, которые передаются вторым аргументом.

В первом случае у нас есть 3 типа - "a" | "b" | "c" и тип "a" - мы исключаем.

Во-втором у нас остается только "c" - поскольку мы убираем "a" и "b".

И в-третьим у нас есть строка, число и функция - тип функции мы исключаем.

```TypeScript
// Exclude<T, U>
type T0 = Exclude<"a" | "b" | "c", "a">;                      // "b" | "c"
type T1 = Exclude<"a" | "b" | "c", "a" | "b">;                // "c"
type T2 = Exclude<string | number | (() => void), Function>;  // string | number
```

В противоположность **Exclude** есть утилита **Extract**.

Она наоборот конструирует тип - оставляя в нем только переданные свойства.

```TypeScript
// Extract<T, U>
type T0 = Extract<"a" | "b" | "c", "a" | "f">;                // "a"
type T1 = Extract<string | number | (() => void), Function>;  // () => void
```

И третья похожая утилита - это **NonNullable**.

Она выбрасывает из создаваемого типа - все несуществующие типы.

```TypeScript
// NonNullable<T>
type T0 = NonNullable<string | number | undefined>;   // string | number
type T1 = NonNullable<string[] | null | undefined>;   // string[]
```

**ReturnType**

Данная утилита создает тип, состоящий из возвращаемого функцией типа.

```TypeScript
// ReturnType<T>
declare function f1(): { a: number, b: string };

type T0 = ReturnType<() => string>;                                  // string
type T1 = ReturnType<(s: string) => void>;                           // void
type T2 = ReturnType<(<T>() => T)>;                                  // {}
type T3 = ReturnType<(<T extends X, X extends number[]>() => T)>;    // number[]
type T4 = ReturnType<typeof f1>;                                     // { a: number, b: string }
type T5 = ReturnType<any>;                                           // any
type T6 = ReturnType<never>;                                         // any
type T7 = ReturnType<string>;                                        // Error
type T8 = ReturnType<Function>;                                      // Error
```

И последняя утилита очень похожая на предыдущую - это **InstanceType**.

На этот раз мы создаем тип, состоящий из типа экземпляра и функции конструктора.

```TypeScript
// InstanceType<T>
class C {
    x = 0;
    y = 0;
}

type T0 = InstanceType<typeof C>;     // C
type T1 = InstanceType<any>;          // any
type T2 = InstanceType<never>;        // any
type T3 = InstanceType<string>;       // Error
type T4 = InstanceType<Function>;     // Error
```