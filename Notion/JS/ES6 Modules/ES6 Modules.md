Существует еще один синтаксис, как и **CommonJS** для сборки **модулей** - это **ES6 Modules**.

Это наши настройки - **webpack config**.

![[Untitled 145.png|Untitled 145.png]]

Давайте рассмотрим пример. Из **main.js** мы будем **экспортировать**, а в **script.js** **импортировать**.

Мы можем **экспортировать** **переменные** таким способом:

**export let one  = 1**

А также мы можем **экспортировать их** в другом формате(эта так называемый **именованный синтаксис**):

**let two = 2;**

**export {two};**

А также мы можем **экспортировать** **функции**:

**export function sayHi() {}**

Чтобы взять **экспортированные** файлы из **main.js** и **импортировать** в **script.js**, мы прописываем, указывая названия **переменных** и путь:

**import {one, two} from './main';**

И когда мы **импортировали** все сущности в **script.js**, мы уже можем их как-то использовать:

**console.log(`${one} and ${two}`);**

Далее прописываем **webpack npx**, запускам код в **bundle.js** и мы получаем результат **1 and 2**

main.js script.js

```JavaScript
export let one =1; 

let two = 2;

export {two};

export function sayHi() {
    console.log('Hello');
}
```

```JavaScript
import {one, two} from './main';

console.log(`${one} and ${two}`);
```

Когда мы что-то **импортируем** в наш проект, мы можем сразу же его переименовать в объявлении: **one as first** - то есть мы значение **one** переименовываем в **first** и далее уже используем **first**.

script.js

```JavaScript
import {one as first} from './main';

console.log(first);
```

Чтобы **импортировать** абсолютно все из **main.js** мы прописываем:  *** as data**

**data** это то, как мы все обзываем, а чтобы уже обратиться к **переменным** мы пишем **data** и название **свойства**: **data.one** и **data.two**, потому что **data** - это по факту **объект**, который включает в себя все, что было **экспортировано** из файла **main.js**

```JavaScript
import * as data from './main';

console.log(`${data.one} and ${data.two}`);
data.sayHi();
```

Кроме **именованного синтаксиса** в **модулях** есть также **экспорт** **по умолчанию**. Он может быть только один и выглядеть следующим образом.

В файле **main.js** мы прописываем: **export default function sayHi() {}**

А в **script.js** мы прописываем: **import sayHi from './main'** - преимущество таково способа в том, что **функция** берется не как **именованный экспорт**, а **экспортируется** напрямую.

```JavaScript
import {one, two} from './main';
import sayHi from './main';

console.log(`${one} and ${two}`);
sayHi();
```

```JavaScript
export let one = 1;

let two = 2;

export {two};

export default function sayHi() {
    console.log('Hello');
}
```

Далее правильно подключаем **модули** на страницу. Сначала мы прописываем **скрипт** с **main.js**, а потом уже **script.js**, потому из него идут **экспорты** и уже он используется дальше в **script.js**. Указываем **type="module"**

```HTML
<script type="module" src="./js/main.js"></script>
<script type="module" src="./js/script.js"></script>
```

```JavaScript
import {one, two} from './main.js';
import sayHI from './main.js';
```

![[Untitled 1 72.png|Untitled 1 72.png]]