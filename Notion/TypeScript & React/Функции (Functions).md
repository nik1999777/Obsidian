  

Создадим стандартную функцию.

Когда мы работаем с TS мы должны понимать, что наша задача - это описание типов.

Типы есть почти у всех сущностей, с которыми мы работаем.

Не исключения и функции.

```TypeScript
// Function example
const createPassword = (name, age) => `${name}${age}`;

createPassword('Jack', 31);	// "Jack31"
```

Для начала мы можем описать - типы аргументов.

```TypeScript
// Arguments type
const createPassword = (name: string, age: number) => `${name}${age}`;
```

Предположим, что аргумент age - может быть как строкой, так и числом.

Добавим это условие.

Когда значение включает несколько типов - это называется **тип объединения**.

```TypeScript
// Multiple argument types
const createPassword = (name: string, age: number | string) => `${name}${age}`;

createPassword('Jack', 31);		// 'Jack31'
createPassword('Jack', '31');	// 'Jack31'
```

Как мы помним, что одной из фич у функций в синтаксисе ES6 - это **дефолтные** **аргументы**.

И в TS - они тоже никуда не пропали.

```TypeScript
// Default Arguments
const createPassword = (name: string = 'Max', age: number | string = 20) => `${name}${age}`;

createPassword();		// "Max20"
createPassword(null);	// Argument of type 'null' is not assignable to parameter of type 'string | undefined'
```

В TS есть такое понятие - как **опциональный аргумент**.

Предположим в нашей функции - мы не хотим указывать никаких дефолтных аргументов и попытаемся вызвать ее - передав только имя.

В этом случае мы получим ошибку о том - что в функцию мы не передали аргумент age.

Но как сделать так, чтобы аргумент age - был **опциональным**, то есть была описана логика того, как должен присваиваться age в случае его отсутствия.

Сделать это просто - достаточно после аргумента age поставить **вопросительный знак - ?**.

```TypeScript
// Function with two required arguments
const createPassword = (name: string, age: number): string => `${name}${age}`;

// Call function with one argument
createPassword('Jack');	// 'An argument for 'age' was not provided.'

// Function with optional argument 'age'
const createPassword = (name: string, age?: number) => `${name}${age}`;
```

Еще одна фича ES6 - это **остаточные** **параметры** или **Rest оператор**.

И как же описать подобный тип аргументов?

Все просто - ...skills - это массив строчных значений, а следовательно описание аргументов данной функции осуществляется с помощью уже рассмотренного типа **Array**, внутри которого указываем тип данных.

```TypeScript
// REST
const createSkills = (name, ...skills) => `${name}, my skils are ${skills.join()}`;

// REST type
const createSkills = (name: string, ...skills: Array<string>) => `${name}, my skils are ${skills.join()}`;

// Call function with REST arguments
createSkills('Jack', 'JS', 'ES6', 'React');	// "Jack, my skils are JS,ES6,React"
```

Как говорилось ранее - наша функция возвращает строку и мы спокойно можем это описать.

Ну вот и готово - все, что осталось сделать - это после круглых скобок описать тип возвращаемых функцией данных.

```TypeScript
// Returned type is string
const createPassword = (name: string, age: number | string): string => `${name}${age}`;

// Returned type is number
const sum = (first: number, second: number): number => first + second;

// Returned type is object
const createEmptyObject = (): object => ({});
```

Так же помним, что если функция не возвращает никаких данных - то мы используем **Void**.

Если функция возвращает ошибку или выполняется постоянно - то используем тип **Never**.

```TypeScript
// Void
const greetUser: void = () => {
    alert("Hello, nice to see you!");
};

// Never Type
// Function return Error
const msg = "hello";
const error = (msg: string): never => {
    throw new Error(msg);
};

// Function infinite loop
const infiniteLoop = (): never => {
    while (true) {
    }
};
```

И последнее, что мы разберем - это тип функций.

Предположи у нас возникает ситуация, когда мы создаем переменную и в последующем в эту переменную мы хотим присвоить функцию.

Благодаря стрелочным функция - такой кейс уже встретишь не часто.

Но если мы работаем с **Legacy** кодом - то с такой ситуацией вполне можем столкнуться.

В примере нам нужно описать переменную myFunc, в которую мы планируем присвоить функцию.

_**Legacy**_ code — тяжелая наследственность : ) Устаревший _**код**_, который более не поддерживается и не обновляется, но используется.

```TypeScript
// Function variable type
let myFunc;

function oldFunc(name: string):void {
    alert(`Hello ${name}, nice to see you!`);
};

myFunc = oldFunc;
```

Как ни странно, но для этой задачи используется синтаксис стрелочной функции.

Как мы видим после имени переменной мы ставим двоеточие и описываем функцию.

firstArg - это абстрактное название, которое нужно только для того, чтобы описать тип единственного аргумента функции.

После чего мы ставим знак стрелки и с помощью ключевого слова **void** - говорим, что функция ничего не возвращает.

Таким образом мы полностью описали функцию, которая будет присвоена в переменную myFunc.

```TypeScript
// Function type description
let myFunc: (firstArg: string) => void;

function oldFunc(name: string):void {
    alert(`Hello ${name}, nice to see you!`);
};

myFunc = oldFunc;
```