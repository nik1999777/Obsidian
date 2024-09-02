  

Все виды переменных в JS делятся на 2 основных типа:

- **локальные**
- **глобальные**

Тип зависит от того - в какой **области** **видимости** определены переменные.

  

Если мы условно создадим файл main.js и подключим его в проект. После чего просто скопируем все эти данные в этот файл - то каждая из этих const становится **глобальной**.

То есть она доступна из любого места приложения и фактически засоряет **глобальную** **область** **видимости**.

Создавать **глобальные** **переменные** - это плохо.

```TypeScript
// Just example of functionality
const SECRET: string = '123321';
const PI: number = 3.14;

const getPass = (name: string, age: number): string => `${name}${age}`;

const isEmpty = <T>(data: T): boolean => !data;
```

В JS для решения возникшей проблемы - использовались **анонимные** **самовызывающиеся** **функции**.

Таким образом к данным, находящимся внутри нее - нельзя было получить доступ снаружи.

После глобального обновления ECMAScript 2015 - в JS появились свои **модули**, которые инкапсулировали заложенную в них логику.

```TypeScript
// ES5 Module
(function () {
    
    const SECRET: string = '123321';
    const PI: number = 3.14;

    const getPass = (name: string, age: number): string => `${name}${age}`;

    const isEmpty = <T>(data: T): boolean => !data;

}());
```

TS предложил свое элегантное решение данной проблемы, а именно - **пространство** **имен**.

Как мы видим - это отдельная сущность похожая на объект, однако объявлена она через ключевое слово - **namespace**.

И такая запись инкапсулирует все добавленные в нее сущности, создавая свое пространство имен, к которому можно обратиться.

```TypeScript
// Define namespace
namespace Utils {

    const SECRET: string = '123321';
    const PI: number = 3.14;

    const getPass = (name: string, age: number): string => `${name}${age}`;

    const isEmpty = <T>(data: T): boolean => !data;

};
```

Но чтобы получить доступ к этим данным снаружи **namespace** - нам нужно их экспортировать.

```TypeScript
// Export data from Namespace
namespace Utils {

    export const SECRET: string = '123321';
    const PI: number = 3.14;

    export const getPass = (name: string, age: number): string => `${name}${age}`;

    export const isEmpty = <T>(data: T): boolean => !data;

};
```

А что если необходимо использовать один **namespace** на несколько файлов.

Предположим, что этот namespace находится в отдельном файле Utils.ts и нам нужно получить доступ к функции getPass() в файле Customers.ts

Как это сделать?

Для импортирования **namespace** из другого файла - существует свой синтаксис:

```TypeScript
/// <reference path="Utils.ts" />
```

```TypeScript
// File "Utils.ts"
// Export
namespace Utils {

    export const SECRET: string = '123321';

    export const getPass = (name: string, age: number): string => `${name}${age}`;

};
```

```TypeScript
// File "Customers.ts"
// Import
/// <reference path="Utils.ts" />			// <--- Import

// Calling "Utils" namespace method
const myPass = Utils.getPass('Yauhen', 31);	// "Yauhen31"
```

В больших проектах, где мы интегрируем React с TypeScript - рекомендуется использовать ES6 модули.

Для этого мы убираем обертку **namespace** - и экспортируем каждую const по отдельности.

```TypeScript
// Import/Export (ES6 Modules)

// File "Utils.ts"
export const SECRET: string = '123321';

export const getPass = (name: string, age: number): string => `${name}${age}`;

// File "Customers.ts"
import { getPass, SECRET } from "./Utils";

const myPass = getPass(SECRET, 31);	// "Yauhen31"
```

Но если вместо множественного импорта каждого метода - мы хотим экспортировать просто одну сущность - то в этом случае создание **класса** со **статическими** **свойствами** и методами вполне обоснованно.