  

В нативном JS существует 6 основных типов данных:

```TypeScript
// Data types in JavaScript
- number
- string
- boolean
- null
- undefined
- object
- Symbol    // ES6
```

Однако в случае неправильной реализации функции или метода - тип переменной мог измениться.

И JS поскольку является языком с динамической типизацией - благополучно умалчивал этот факт.

В результате - в коде появлялись ошибки, которые ломали логику и которые становились действительно трудно отлавливаемыми.

```TypeScript
// Variable type changing
var num = 42;		// number
num = 'hello';		// string
num = false;		// boolean
```

Для того чтобы определить тип переменной в JS - применяется оператор **typeof**.

```TypeScript
// Defining types using operator typeof
typeof 42;          // "number"
typeof 'str';       // "string"
typeof true;        // "boolean"
typeof [];          // "object"
typeof {};          // "object"
typeof null;        // "object"
typeof undefined;   // "undefined"
typeof Symbol();    // "symbol"
```

С появлением **let** и **const** - часть проблем вроде бы отпала:

- Простое значение объявленное через const - стало невозможно изменить. Но этот условно говоря фикс - не работал с ссылочными типами.
- **let** же позволяла переопределять значение.

Но по факту картина никак не изменилась - переопределение типов в больших проектах - было сильной головной болью на проектах.

Поскольку не всегда было понятно какие конкретно данные принимали функции или методы, зачем эти данные трансформировались и т д.

А забытое переопределение типа - могло сожрать не один час времени любого разработчика.

Поэтому программисты на JS - всегда старались получить полный контроль над типами.

```TypeScript
// const
const num = 42;
num = 'hello';	// Uncaught TypeError: Assignment to constant variable

// let
let num = 42;
num = 'hello';	// No errors
```

С этими задачами - прекрасно начал справляться JS.

**TypeScript** - это строго типизированный язык.

Задав типизацию для всех элементов - еще на стадии написания кода - легко можно отследить, где конкретно произошла ошибка и тем самым моментально исправить ее.

  

Первый тип - **boolean**.

В данном коде, если мы захотим изменить тип переменной - то получим ошибку.

```TypeScript
// Boolean Type
let isCompleted: boolean = false;

isCompleted = 42;     // Type '42' is not assignable to type 'boolean'
isCompleted = '42';   // Type ’"42"' is not assignable to type 'boolean'

isCompleted = true;
```

Тип - **number**

```TypeScript
// Number Type
const decimal: number = 6;
const integer: number = 7.10;
const hex: number = 0xf00d;
const binary: number = 0b1010;
const octal: number = 0o744;
```

Тип - **string**

```TypeScript
// String Type for simple string
const name: string = 'Yauhen';

// String Type for template string
const sentence: string = `Hello, my name is ${ name }!`;
```

**Null** и **undefined**

Здесь уже всплывает первая разница между JS и TS.

В TS - тип **undefined** - **undefined**. В JS - тип **null** - это **object**.

```TypeScript
// Null & Undefined Types
// JavaScript:
typeof null;		// "object"
typeof undefined;	// "undefined"

// TypeScript types:
const u: undefined = undefined;
const n: null = null;
```

Тип - **void**

Тип **void** означает отсутствие вообще какого-либо типа. 

Как правило **void** тип используется в качестве возвращаемого типа функций, которые не возвращают значения. 

```TypeScript
// Void Type
// For function result:
const greetUser = (): void => {
    alert("Hello, nice to see you!");
};

// For 'greetUser'
// Error: Type '() => void' is not assignable to type 'void'
const greetUser: void = () => {
    alert("Hello, nice to see you!");
};
```