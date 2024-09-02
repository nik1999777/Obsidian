  

**Декораторы** - это возможность TS по добавлению аннотаций и meta - программного синтаксиса для объявления классов и функций.

По сути **декоратор** - это обычная функция. Она может быть прикреплена к объявлению класса, методу, аксессору, свойству или параметру.

Декораторы оборачивают декорируемую сущность и модифицируют ее поведение.

  

Мы видим начальную реализацию **декоратора**.

Да, пока что она ничего не делает и ни к чему не применена.

```TypeScript
// Base structure of Decorator :)
const logClass = () => ();
```

Есть одно простое правило - в качестве единственного аргумента - функция классового декоратора должна принимать конструктор **декорируемой** **сущности**.

В данном коде мы можем видеть полную реализацию **декоратора** для класса:

То есть у нас есть **декоратор** logClass - он будет принимать конструктор класса и выводить его в консоль.

Для того чтобы применить **декоратор** - достаточно поставить знак собачки и написать имя **декоратора** - таким образом в консоле мы получим соответсвующий вывод конструктора.

Здесь важно запомнить, что если **декоратор** класса вернет значение - то он заменит объявление класса с помощью предоставленного конструктора - именно поэтому в нашем **декораторе** мы ничего не возвращаем.

Если говорить вообщем - то существует 4 основных типа **декоратора**:

- **класса**
- **свойства**
- **метода**
- **аксессора**

Имя соответсвует тому - какому конкретно месту применен **декоратор**.

И первый тип мы уже рассмотрели.

```TypeScript
// Class Decorator
const logClass = (constructor: Function) => {
    console.log(constructor);	// Result of call: class User {}
};

@logClass		// <--- Apply decorator for class
class User {

    constructor(public name: string, public age: number) {}

    public getPass(): string {
        return `${this.name}${this.age}`;
    }

}
```

Второй тип - это **декоратор** **свойства**.

Во-первых в класс User мы добавили свойство secret и его тип число - именно к этому свойству мы применяем декоратор logProperty.

А во-вторых декоратор logProperty принимает уже 2 аргумента:

- **target** - по сути это прототип класса, к которому применяется декоратор.
- **propertyKey** - это имя поля, к которому применяется декоратор (и тип этого поля - либо string, либо symbol - это логично, так как только эти значения могут использоваться для ключей объекта)

Декоратор logProperty - возвращает либо null, либо дескриптор свойства.

```TypeScript
// Property Decorator
const logProperty = (target: Object, propertyKey: string | symbol) => {
    console.log(propertyKey);	// Result of call: "secret"
};

class User {

    @logProperty		// <--- Apply decorator for property
    secret: number;

    constructor(public name: string, public age: number, secret: number) {
        this.secret = secret;
    }

    public getPass(): string {
        return `${this.name}${this.age}`;
    }

}
```

Третий тип **декоратора** - это **декоратор** **метода**.

Для начала мы применяем декоратор logMethod к публичному методу getPass().

Сам же декоратор принимает 3 аргумента:

- **target** - прототип класса
- **propertyKey** - имя метода
- и так как декоратор применяется к методу - то появляется дополнительный аргумент **descriptor**, у которого есть специальный тип **PropertyDescriptor**

Точно также как и **декоратор** **свойства** - данный **тип** **декоратора** может вернуть либо null, либо **дескриптор** **свойств**.

  

**Дескриптор свойства** – это обычный JavaScript-объект, описывающий атрибуты и значение свойства. **Дескрипторы свойств**, присутствующие в объектах, бывают двух основных типов: **дескрипторы** данных и **дескрипторы** доступа. **Дескриптор** данных - это свойство, имеющее значение, которое может быть (а может и не быть) записываемым.

```TypeScript
// Method Decorator
const logMethod = (
  target: Object,
  propertyKey: string | symbol,
  descriptor: PropertyDescriptor
) => {
    console.log(propertyKey);   // Result of call: "getPass"
};

class User {

    constructor(public name: string, public age: number) {}
    
    @logMethod			// <--- Apply decorator for method
    public getPass(): string {
        return `${this.name}${this.age}`;
    }

}
```

Последний тип - это **декоратор** **аксессора**, то есть декоратор для геттеров и сеттеров.

И здесь все по аналогии, как и с обычными методами - то есть применяем **декоратор** к set или get.

Декоратор logSet принимает те же самые 3 аргумента и также возвращает - либо null, либо descriptor.

```TypeScript
// get/set Decorator
const logSet = (
  target: Object,
  propertyKey: string | symbol,
  descriptor: PropertyDescriptor
) => {
    console.log(propertyKey);	// Result of call: "myAge"
};

class User {

    constructor(public name: string, public age: number) {}
    
    @logSet		// <--- Apply decorator for set
    set myAge(age: number) {
        this.age = age;
    }

}
```

Теперь разберем такое понятие, как **фабрика** **декораторов**.

**Фабрика** **декораторов** - это функция, которая возвращает выражение и которая будет вызвана декоратором во время исполнения программы.

В общем виде она выглядит следующим образом:

Вместо того, чтобы просто написать **декоратор** - мы создаем дополнительную обертку над ним из функций.

Сама функция (конкретно в нашем случае) - может принимать некое значение с типом **any** - и это значение она может применить внутри **декоратора**.

А вот уже сама **функция** **фабрика** - должна возвращать **декоратор**.

```TypeScript
// Factory Decorator
function factory(value: any) {        // Factory
    return function (target: any) {   // Decorator
        console.log(target);          // Decorator logic
    }
}
```

Для примера используем класс User, к свойству которого применяем **фабричный** **декоратор** enumerable.

Он в свою очередь принимает булевое значение (в нашем случае - это false) и передает его в **декоратор**.

При вызове этого **декоратора** - будет изменено свойство enumerable **дескриптора** **свойства**.

```TypeScript
// Applying Factory Decorator
const enumerable = (value: boolean) => {
    return (
      target: any,
      propertyKey: string | symbol,
      descriptor: PropertyDescriptor
    ) => {
        descriptor.enumerable = value;
    };
}

class User {

    constructor(public name: string, public age: number) {}

    @enumerable(false)			// <--- Call decorator factory with argument
    public getPass(): string {
        return `${this.name}${this.age}`;
    }

}
```

До этого момента мы всегда применяли только один **декоратор**.

В TS разрешается применять по несколько **декораторов** - и эта называется **композиция** **декораторов**.

В данном коде мы можем видеть синтаксис использования нескольких **декораторов** - они либо будут писаться в одну линию, либо каждый на своей.

Существуют следующие шаги при вычислении нескольких **декораторов** на одном объявлении:

1. Сначала выражения для каждого декоратора вычисляются - сверху вниз.
2. Затем результаты вызываются как функции - снизу вверх.

```TypeScript
// Decorator composition syntax
// Apply decorators (one line)
@f @g x

// Apply decorators (multiple lines)
@f
@g
x
```

Рассмотрим небольшой пример.

У нас есть 2 **декоратора**, которые создаются с помощью **фабрик** **декораторов** - first и second.

И обратим внимания, что внутри **фабрики** и внутри **декоратора** - стоит console.log().

Внутри **фабрики** - мы трекаем обращение к ней.

Внутри **декоратора** соответсвенно - его вызов.

```TypeScript
// Example of two factory decorators
const first = () => {
    console.log('first() completing');
    return (target: any, propertyKey: string | symbol, descriptor: PropertyDescriptor) => {
        console.log('first() called');
    };
}

const second = () => {
    console.log('second() completing');
    return (target: any, propertyKey: string | symbol, descriptor: PropertyDescriptor) => {
        console.log('second() called');
    };
}
```

После чего мы применяем 2 наших **декоратора** к классу.

И если заглянуть в консоль - мы увидим примерно следующий результат:

1. Сначала у нас происходит вызов 1 **фабрики**
2. Затем вызов 2 **фабрики**
3. После чего мы вызываем сначала 2 **декоратор**
4. А затем 1 **декоратор**

То есть выражения для **декораторов** вызываются и вычисляется последовательно сверху вниз, а результаты затем - вызывают **декораторы** снизу вверх.

Вот что из себя представляет механизм работы - **композиции** **декоратора**.

```TypeScript
// Apply and call two factory decorators
class User {

    constructor(public name: string, public age: number) {}
    
    @first()
    @second()
    public getPass(): string {
        return `${this.name}${this.age}`;
    }

}

// Call results:
"first() completing"      // Factory 1
"second() completing"     // Factory 2
"second() called"         // Decorator 2
"first() called"          // Decorator 1
```