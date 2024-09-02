  

Мы можем создавать **статические** элементы класса, то есть те, которые видны в классе без создания экземпляра.

Достаточно добавить ключевое слово **static** и свойство становится **статическим**.

Каждый экземпляр получит доступ к этому значению - при использовании конструкции **User.secret**.

```TypeScript
// Example of call static property
User.secret

// Call static property in class method
class User {

    static secret = 12345; 

    constructor(public name: string, public age: number) {}

    getPass(): string {
        return `${this.name}${User.secret}`;
    }

}

const yauhen = new User('Yauhen', 30);

yauhen.getPass();	// "Yauhen12345"
```

Как мы уже говорил TS в чистом виде не воспринимается браузером - его нужно компилировать.

Если созданный класс со статическим методом мы скомпелируем - то он будет выглядеть так:

```TypeScript
"use strict";
class User {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    getPass() {
        return this.name + User.secret;
    }
}
User.secret = 12345;
```

Создадим класс User и на основании его создадим наследника, используя ключевое слово **extends**.

Далее пробуем создать экземпляры от 2-х наших классов.

И вот здесь мы сталкиваемся с проблемой - во втором случае вместо 2-х аргументов мы передаем 1 - и как результат получаем ошибку.

Но ведь в нашем классе наследники по **дефолту** уже определено свойство имени, поэтому ведь снаружи его передавать не нужно?

Причина этой проблемы - наследование от класса User, в конструкторе которого определено именно 2 параметра: name и age.

```TypeScript
class User {
 
    private nickName: string = 'webDev';
    static secret = 12345; 

    constructor(public name: string, public age: number) {}

    getPass(): string {
        return `${this.name}${User.secret}`;
    }

}
```

```TypeScript
// Inheritance example
class Yauhen extends User {

    name: string = 'Yauhen';

}

// Create instances based on 'User' and 'Yauhen' classes
const max = new User('Max', 20);
const yauhen = new Yauhen(31);	// Expected 2 arguments, but got 1
```

Решение простое - в классе Yauhen нам нужно создать свой конструктор.

В нем используется ключевое слово **super**, которое помогает вызвать родительский конструктор и уже в родительском конструкторе у нас происходит определение типов: name и age**.**

Поэтому в классе наследники - никакие типы мы не определяем.

Теперь создание экземпляров классов - полностью валидно.

```TypeScript
// Realization of constructor in the inherited class
class Yauhen extends User {

    name: string = 'Yauhen';

    constructor(age: number) {
        super(name, age);
    }

}

// No error
// Create instances based on 'User' and 'Yauhen' classes
const max = new User('Max', 20);
const yauhen = new Yauhen(31);
```

Помимо переопределения конструктора - мы также в классе наследники можем переопределять - методы.

Допустим в классе Yauhen будет своя реализация метода getPass().

```TypeScript
// Personal method in inherited class
class Yauhen extends User {

    name: string = 'Yauhen';

    constructor(age: number) {
        super(name, age);
    }

    getPass(): string {
        return `${this.age}${this.name}${User.secret}`;
    }

}

const yauhen = new Yauhen(31);

yauhen.getPass(); // "31Yauhen12345"
```

Теперь разберем понятие **абстрактных** **классов**.

В нативном JS - это просто обычный класс, который ничем не отличается от других классов.

Однако в TS - это отдельная сущность.

**Абстрактные** **классы** - это базовые классы от которых наследуются другие.

У него есть 2 основные особенности:

- **абстрактный** **класс** содержит детали реализации своих элементов (то есть свойств и методов)
- от данного типа класса - напрямую не создать экземпляр, **абстрактный** **класс** используется только для создания наследников.

  

Создается **абстрактный** **класс** с помощью ключевого слова - **abstract**.

**Абстрактный** **класс** - это некий интерфейс, который примерно описывает как должны выглядеть потомки.

```TypeScript
// Abstract class example
abstract class User {

    constructor(public name: string, public age: number) {}

    greet(): void {
        console.log(this.name);
    }


}

const max = new User('Max', 20);  // Cannot create an instance of an abstract class
```

**Абстрактный** **класс** - помогает лучше представить, как будут выглядеть его наследники и по сути он является обычной абстракцией, которая предназначена только для создания потомков.