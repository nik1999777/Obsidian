- **Single responsibility principle (Принцип единой ответсвенности)**
    
    Это принцип проектирования программного обеспечения, который утверждает, что каждый класс или модуль должен иметь только одну причину для изменения. Согласно этому принципу, класс должен иметь только одну основную ответственность и не должен нести ответственность за более чем одну функцию или аспект системы.
    
    ```JavaScript
    class User {
      constructor(name, email) {
        this.name = name;
        this.email = email;
      }
      
      updateProfile(data) {
        // обновление профиля пользователя
      }
      
      sendMessage(to, message) {
        // отправка сообщения пользователю
      }
      
      getProfile() {
        // получение профиля пользователя
      }
    }
    ```
    
    Чтобы следовать принципу единой ответственности, мы можем разделить этот класс на два класса: `**UserProfile**` и `**UserMessenger**`.
    
    ```JavaScript
    class UserProfile {
      constructor(name, email) {
        this.name = name;
        this.email = email;
      }
      
      updateProfile(data) {
        // обновление профиля пользователя
      }
      
      getProfile() {
        // получение профиля пользователя
      }
    }
    
    class UserMessenger {
      constructor() {}
      
      sendMessage(to, message) {
        // отправка сообщения пользователю
      }
    }
    ```
    
- **Open-closed principle (Принцип закрытости и открытости)**
    
    Это принцип проектирования программного обеспечения, который утверждает, что классы и модули должны быть открыты для расширения, но закрыты для изменения. Согласно этому принципу, код должен быть написан таким образом, чтобы изменение его поведения можно было осуществить путем добавления нового кода, а не изменения существующего.
    
    ```JavaScript
    // Базовый класс Shape, от которого будут наследоваться другие фигуры
    class Shape {
      area() {
        throw new Error("Area method must be implemented in derived classes.");
      }
    }
    
    // Классы различных фигур, расширяющие базовый класс Shape
    class Circle extends Shape {
      constructor(radius) {
        super();
        this.radius = radius;
      }
    
      area() {
        return Math.PI * this.radius ** 2;
      }
    }
    
    class Rectangle extends Shape {
      constructor(width, height) {
        super();
        this.width = width;
        this.height = height;
      }
    
      area() {
        return this.width * this.height;
      }
    }
    
    // Функция, которая вычисляет суммарную площадь массива фигур
    function calculateTotalArea(shapes) {
      let totalArea = 0;
    
      for (const shape of shapes) {
        totalArea += shape.area();
      }
    
      return totalArea;
    }
    
    const circle = new Circle(5);
    const rectangle = new Rectangle(4, 6);
    const shapes = [circle, rectangle];
    
    console.log("Total area:", calculateTotalArea(shapes));
    ```
    
    В этом примере мы создали базовый класс `**Shape**` и два производных класса `**Circle**` и `**Rectangle**`. Каждый из производных классов определяет свою реализацию метода `**area()**`. Функция `**calculateTotalArea**` работает с массивом объектов, являющихся экземплярами классов, производных от `**Shape**`, и вычисляет суммарную площадь всех фигур.
    
- **Liskov Substitution Principle (Принцип подстановки Барбары Лисков)**
    
    LSP гласит, что объекты базового класса должны быть заменяемыми на объекты производных классов без изменения их корректности. Это означает, что при использовании наследования, объекты производного класса должны сохранять поведение и свойства, определенные в базовом классе.
    
    ```JavaScript
    class Bird {
      fly() {
        console.log("I can fly!");
      }
    }
    
    class NonFlyingBird extends Bird {
      fly() {
        console.log("I can't fly!");
      }
    }
    
    class Penguin extends NonFlyingBird {}
    
    function letBirdsFly(birds) {
      for (const bird of birds) {
        bird.fly();
      }
    }
    
    const bird1 = new Bird();
    const bird2 = new Penguin();
    
    letBirdsFly([bird1, bird2]);
    ```
    
    Теперь, вместо того чтобы нарушать LSP, мы создали новый класс `**NonFlyingBird**`, который является производным от класса `**Bird**` и переопределяет метод `**fly()**` таким образом, чтобы выводить информацию о том, что птица не может летать. Затем класс `**Penguin**` наследуется от класса `**NonFlyingBird**` и сохраняет поведение, определенное в нем. Теперь объекты класса `**Penguin**` могут быть безопасно заменены на объекты класса `**Bird**` без нарушения корректности программы, и принцип LSP соблюдается.
    
- **Interface segregation principle (Принцип разделение интерфейса)**
    
    ISP гласит, что клиенты не должны зависеть от интерфейсов, которые они не используют. Вместо того чтобы создавать один большой интерфейс с множеством методов, лучше разделить его на несколько более мелких интерфейсов, которые более конкретно отвечают за определенные функции.
    
    ```TypeScript
    // Интерфейсы
    interface CanFly {
      fly(): void;
    }
    
    interface CanSwim {
      swim(): void;
    }
    
    // Классы
    class Bird implements CanFly {
      fly() {
        console.log("I can fly!");
      }
    }
    
    class Fish implements CanSwim {
      swim() {
        console.log("I can swim!");
      }
    }
    
    class Duck implements CanFly, CanSwim {
      fly() {
        console.log("I can fly!");
      }
    
      swim() {
        console.log("I can swim!");
      }
    }
    
    // Использование классов
    const bird: Bird = new Bird();
    bird.fly();
    
    const fish: Fish = new Fish();
    fish.swim();
    
    const duck: Duck = new Duck();
    duck.fly();
    duck.swim();
    ```
    
    В этом примере мы определили два интерфейса CanFly и CanSwim, которые могут быть использованы классами для добавления определенного набора функций. Затем мы создали классы Bird, Fish и Duck, каждый из которых реализует один или несколько интерфейсов для определения своего поведения. Таким образом, каждый класс зависит только от интерфейсов, которые он реализует и использует, и не от ненужных методов.
    
- **Dependency inversion principle (Принцип инверсии зависимости)**
    
    DIP состоит из двух ключевых идей:
    
    1. Высокоуровневые модули не должны зависеть от низкоуровневых модулей. Оба должны зависеть от абстракций.
    2. Абстракции не должны зависеть от деталей. Детали должны зависеть от абстракций.
    
    Цель DIP — минимизировать зависимости между модулями и уменьшить связность в системе, делая ее более гибкой, модульной и легко изменяемой.
    
    ```TypeScript
    // Интерфейс хранилища данных
    interface DataStore {
      save(data: string): void;
    }
    
    // Реализация хранилища данных на основе файла
    class FileDataStore implements DataStore {
      save(data: string): void {
        console.log(`Saving data to a file: ${data}`);
      }
    }
    
    // Реализация хранилища данных на основе облака
    class CloudDataStore implements DataStore {
      save(data: string): void {
        console.log(`Saving data to the cloud: ${data}`);
      }
    }
    
    // Класс приложения, который зависит от абстракции DataStore
    class App {
      private dataStore: DataStore;
    
      constructor(dataStore: DataStore) {
        this.dataStore = dataStore;
      }
    
      saveData(data: string): void {
        this.dataStore.save(data);
      }
    }
    
    // Использование класса приложения с различными хранилищами данных
    const fileStore: FileDataStore = new FileDataStore();
    const cloudStore: CloudDataStore = new CloudDataStore();
    
    const app1: App = new App(fileStore);
    app1.saveData("Hello, File!");
    
    const app2: App = new App(cloudStore);
    app2.saveData("Hello, Cloud!");
    ```
    
    В данном примере мы определили интерфейс `**DataStore**`, который представляет абстракцию хранилища данных. Затем мы создали две реализации этого интерфейса: `**FileDataStore**` и `**CloudDataStore**`. Класс `**App**` зависит только от абстракции `**DataStore**`, а не от конкретных реализаций.