  

**Generic** - это просто обозначение типов в общем виде.

**Generic** позволяет создавать компоненты, способные работать с различными типами, а не только с каким-то одним, строго определяя его.

Другими словами - мы сами будем задавать определенные типы и контролировать весь процесс.

  

Создадим простую функцию getter, которая будет принимать любой тип данных и возвращать его.

Ключевое слово **any** - служит своеобразным обобщением, поскольку позволяет использовать аргумент абсолютно любого типа.

Однако особенностью TS - является полный контроль над всеми типами данных.

А в примере - мы все пускаем на самотек.

```TypeScript
// Example of using 'any'
const getter = (data: any): any => data;

getter(10);         // 10
getter('test');     // "test"
```

И вот к какой ошибке это может привести.

При использовании length в случае с числом - мы получаем undefined, так как у числа такого свойства проста нет.

Таким образом - мы написали валидную по синтаксису TS функцию, однако потеряли контроль над типами и сломали приложение.

```TypeScript
// Issue we have
const getter = (data: any): any => data;

getter(10).length;        // undefined
getter('test').length;    // 4
```

Чтобы такая ситуация не произошла - в идеале мы должны захватить тип аргумента, чтобы в последующим его можно было бы использовать для описания возвращаемого типа из функции.

То есть, если в функцию прилетает строка - мы возвращаем строку. Если число - то число.

И как раз для решения данной проблемы - используют **Generic type**.

  

В данном коде мы написали 2 варианта использования функции, используя **Generic** **type**:

- в синтаксисе ES6
- ES5

Вообще это может быть произвольная буква, но распространенной практикой считается указание буквы **T - Type**.

```TypeScript
// Using of generic type
const getter = <T>(data: T): T => data;

function getter<T>(data: T): T {
    return data;
}
```

Обратим внимание, что теперь произошло.

Как только мы добавили **Generic** **type** - еще на этапе написания кода, мы получили ошибку о том, что у числа нет метода length.

```TypeScript
// Defining issue immediately
const getter = <T>(data: T): T => data;

getter(10).length;        // Property 'length' does not exist on type '10'
getter('test').length;    // 4
```

Под капотом эти преобразования выглядят следующем образом.

**Generic** **type** динамически манипулирует, получаемыми типами и подставляет их вместо себя.

```TypeScript
// Generic behavior explanation
// For a number
const getter = (data: number): number => data;
getter(10).length;        // Property 'length' does not exist on type '10'

// For a string
const getter = (data: string): string => data;
getter('test').length;    // 4
```

Как мы уже поняли - компилятор сам автоматически определяет какой тип данных он должен вернуть, однако это совершенно не значит, что мы не можем контролировать этот процесс самостоятельно.

Для примера - мы совершенно свободно можем указать тип данных, который будет получать функция.

Делается это в момент ее вызова - в скобках указывается тип, получаемых ею данных.

```TypeScript
// Function arguments type
const getter = <T>(data: T): T => data;

// Define type in function calling
getter<number>(10).length;		  // Property 'length' does not exist on type '10'
getter<string>('test').length;	// 4
```

Если мы посмотрим на данный код - то можем убедится, что **Generic type** мы уже рассматривали.

Здесь мы определяли тип list - как массив.

И в синтаксисе - мы описываем массив через ключевое слово **Array** и после чего в скобках описываем из какого типа данных этот массив будет состоять.

```TypeScript
// Array generic type
let list: Array<number> = [1, 2, 3];
```

Если мы хотим, чтобы наш класс имел большую гибкость и принимал данные разных типов, свободно ими манипулируя - то для этого наш обычный класс нужно переписать в **Generic** **класс**.

После имени класса - мы указываем **Generic** **type**.

Также наши публичные классы name и age - меняют свои типы на тип **T**.

Далее мы создаем 2 user-ов и вызываем у них метод getPass().

И как мы видим все отработало корректно - теперь наш класс может принимать не только строки, но и числа.

Можно заметить, что в обоих вариантах мы передаем данные одинаковых типов - в первом это строки, во втором это числа.

```TypeScript
// Generic class
class User<T> {

    constructor(public name: T, public age: T) {}

    public getPass(): string {
        return `${this.name}${this.age}`;
    }

}

const yauhen = new User('Yauhen', '31');
const max = new User(123, 321);

yauhen.getPass();     // "Yauhen31"
max.getPass();        // "123321"
```

Но что если нам нужно передать строку и число?

Для этого через запятую - мы просто указываем еще один **Generic** **type**.

И в этом случае подразумевается, что принимаемые аргументы - могут быть как разных типов, так и одного.

```TypeScript
// Multiple generic types
class User<T, K> {

    constructor(public name: T, public age: K) {}

    public getPass(): string {
        return `${this.name}${this.age}`;
    }

}

const yauhen = new User('Yauhen', '31');	// string, string
const max = new User(123, 321);				// number, number
const leo = new User('Leo', 22);			// string, number

yauhen.getPass();     // "Yauhen31"
max.getPass();        // "123321"
leo.getPass();        // "Leo22"
```

А что если в наш метод getSecret() должны приходить только числа?

Для этого нам нужно поставить ограничения на **Generic** **type** - K и сказать, что он должен быть только числом.

Делается это с помощью ключевого слова **extends** - после которого мы указываем тип.

При таком случаи при создании экземпляра max и передаче ему значения неверного типа - мы получаем ошибку.

```TypeScript
// Specify generic type 'K' with key-word 'extends'
class User<T, K extends number> {

    constructor(public name: T, public age: K) {}

    public getPass(): string {
        return `${this.name}${this.age}`;
    }

    public getSecret(): number {
        return this.age**2;
    }
}

const yauhen = new User('Yauhen', 31);
const leo = new User(123, 321);

/*
  Error:
  Argument of type '"20"' is not assignable to parameter of type 'number'
*/
const max = new User('Max', '20');
```