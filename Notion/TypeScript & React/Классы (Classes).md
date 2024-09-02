  

Первый способ описать класс с помощью TS - это непосредственно внутри класса задать все значения.

Внутри классов с помощью типов - мы описали все свойств.

А дальше внутри конструктора - мы добавили возможность принимать эти свойства при инициализации.

Теперь мы спокойно можем создать экземпляр на основании нашего класса.

```TypeScript
// Class types, including constructor
class User {
    
    name: string;
    age: number;
    nickName: string;

    constructor(name: string, age: number, nickName: string) {
        this.name = name;
        this.age = age;
        this.nickName = nickName;
    }

}

const yauhen = new User('Yauhen', 31, 'webDev');

yauhen;	// { name: "Yauhen", age: 31, nickName: "webDev" }
```

Поговорим о **приватных и публичных данных**.

Для определения доступности к свойствам и методам класса есть 4 ключевых слова (или как их правильно называют **4 модификатора доступа)**:

- **public** - это значение по умолчанию, свойства или метод получают данный тип автоматически. Данный модификатор говорит о том, что к соответствующему свойству или методу можно получить свободный доступ.
- **private** - элемент класса, помеченный данным модификатором не может быть доступен за пределами класса. Ни классы наследники, ни объекты созданные с помощью данного класса - не смогут использовать, помеченные этим модификатором.
- **protected** - доступ к элементам с данным модификатором могут получить только наследники. Экземпляры класса - доступа к свойствам и методам не имеют.
- **read-only** - элемент, помеченный им становится доступным только для чтения.

```TypeScript
// Class types modificators
class User {

    public name: string;
  	private nickName: string;
    protected age: number;
    readonly pass: number;

    constructor(name: string, age: number, nickName: string, pass: number) {
        this.name = name;
        this.age = age;
        this.nickName = nickName;
        this.pass = pass;
    }

}

const yauhen = new User('Yauhen', 31, 'webDev', 123);

yauhen.name;	    // "Yauhen"
yauhen.nickName;  // Prop 'nickName' is private and only accessible within class 'User'
yauhen.age;		    // Prop 'age' is protected and only accessible within class 'User' and its subclasses
yauhen.pass = 42; // Cannot assign to 'pass' because it is a read-only property
```

Точно также как и в функциях - в классах можно задавать **дефолтные значения** для элементов.

И в этом случае в конструкторе не нужно описывать никакое присвоение - создаваемый instance (экземпляр класса**)** автоматически получает указанные свойства.

```TypeScript
// Class default properties
class User {

    name: string;
    age: number = 20;
    nickName: string = 'webDev';

    constructor(name: string) {
        this.name = name;
    }

		getPass(): string {
        return `${this.nickName}${this.age}`;
    }

}

const user = new User('Yauhen');

user;   // { name: "Yauhen", age: 20, nickName: "webDev" }

user.getPass(); // "webDev20"
```

Немного поговорим о сокращении кода в классе.

До этого мы определяли свойство в классе и практически то же самое в конструкторе - получалась довольно громоздкая структура.

Поэтому мы можем воспользоваться сокращенной формой записи.

В данной записи - все типы определяются в конструкторе, причем автоматически выполняется присвоение.

Важным моментом является то - что для каждого свойства нужно обязательно указывать модификатор.

```TypeScript
// Minimization of Class properties
class User {

    constructor(
        public name: string,
        public age: number,
        public nickName: string,
        public pass: number
    ) {}

}
```

Теперь поговорим об **аксессорах**.

Речь идет о **геттерах** и **сеттерах** - это специальные методы класса, которые ведут себя как свойства - снаружи этого класса.

И они служат либо для чтения, либо для установки значений внутри него.

Чтобы изменить приватное свойство внутри класса TS предоставляет нам 2 возможности:

- с помощью метода setAge() - этот пример продемонстрирован для того, чтобы мы понимали, что изменять приватные свойства можно не только с помощью set, но и с помощью обычных методов
- во втором мы выполняем то же самое - разница кроется в типе вызова изменения, то есть в синтаксисе. В первом случае происходит - вызов метода, во втором - вызов свойства.

```TypeScript
// Get access to private property
class User {

    private age: number = 20;

    constructor(public name: string) {}

    setAge(age: number) {
        this.age = age;
    }

    set myAge(age: number) {
        this.age = age;
    }
}

const yauhen = new User('Yauhen');

yauhen.setAge(30);	// 30
yauhen.myAge = 31;	// 31
```

В JS нет классов в их классическом понимании - под капотом идут **прототипы**.

При разработки в **объектно-ориентированном** подходе - вполне возможно изменить что-то на верхнем уровне, что изменено быть не должно.

Поэтому напрямую свойства стараются не изменять , а использовать **геттеры** и **сеттеры** - это дает больший контроль над моментом взаимодействия со свойствами объекта.

В TS с помощью **модификаторов** устанавливается дополнительная защита этих свойств и методов - таким образом предотвращается попытка случайного изменения высокоуровневых компонентов и последующего крэша приложения из-за подобного косяка.