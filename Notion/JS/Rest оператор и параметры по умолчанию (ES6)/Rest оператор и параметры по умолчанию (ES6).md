[https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/Rest_parameters](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/Rest_parameters) - **оператор rest**

[https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/Default_parameters](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/Default_parameters) - **параметры по умолчанию**

  

**Оператор rest** - это брат **spread оператора**, который использует точно такой же синтаксис, но уже в других **условиях**.

Если **spread** брал сущность и раскладывал ее на отдельные элементы, то **rest** занимается у нас обратным, он отдельные элементы объединяет в один **массив**.

Синтаксис **оставшихся параметров** **функции** позволяет представлять неограниченное множество **аргументов** в виде **массива**.

Пример как работает **оператор rest**: мы передаем обязательно 2 **аргумента**, а вот дальше мы не знаем, сколько следующих **аргументов** у нас может-быть, может ни одного, а может 10, 20 или тысяча.

Более реальный пример: допустим мы хотим добавить определенные **классы** к нашему элементу на странице, мы знаем, что там будет четко **классы** **item**, **menu**. А остальные **классы** буду **опциональные**, они могут быть или нет, но самое главное, они тоже к нам приходят в виде **аргументов** **функции**.

И нам нужен механизм, который будет это контролировать, и вот **rest** **оператор** этим и занимается.

В данном коде мы видим, как сработал у нас **rest оператор**, он собрал отдельные сущности (конкретно:  **'operator', 'usage'**) в **массив**.

```JavaScript
const log = function(a, b, ...rest) {
    console.log(a, b, rest);
}

log('basic', 'rest', 'operator', 'usage');
```

```JavaScript
[Running] node "/Users/nikitaelin/Desktop/work/JS_React/react/my-app/src/tempCodeRunnerFile.js"
basic rest [ 'operator', 'usage' ]

[Done] exited with code=0 in 0.114 seconds
```

А теперь давайте разберем **параметры по умолчанию**.

Посмотрим на код (картинка слева), **функция** отрабатывает, все рабоатает.

И допустим мы не укажем второй **аргумент**, конечно выйдет ошибка. И например, мы хотим подкорректировать **функцию** так, чтобы если вдруг у нас не был передан второй **аргумент**, то он поставлялся бы автоматически, то есть был какой-то **параметр по умолчанию**. До стандарта ES6 использовали прием с использованием **логического оператора или** (картинка посередине).

Но в стандарте ES6 делать это стало гораздо проще, теперь **параметр по умолчанию** можно записывать прямо при объявлении **функции**(картинка справа). И мы тоже получаем **6**, потому что **basic = 2**.

```JavaScript
function calcOrDouble(number, basic) {
    console.log(number * basic);
}

calcOrDouble(2, 3);
```

```JavaScript
function calcOrDouble(number, basic) {
    basic = basic || 2;
    console.log(number * basic);
}

calcOrDouble(3);
```

```JavaScript
function calcOrDouble(number, basic = 2) {
    console.log(number * basic);
}

calcOrDouble(3);
```

В данном коде мы добавляем **rest** **оператор**: **constructor(src, alt, title, descr, price, parentSelector, ...classes)** и записываем этот **оператор** в **свойства**, чтобы дальше мы могли его использовать **this.classes = classes** и не забываем, что это у нас будет **массив**, поэтому работать с ним придется, как с **массивом**.

А в **методе render()** прописываем **условие**:

```JavaScript
if (this.classes.length === 0) {
    this.element = 'menu__item';
    element.classList.add(this.element);
} else {
    this.classes.forEach(className => element.classList.add(className));  
}
```

В условии прописывается: если не один элемент в **классы** не был передан: **(this.classes.length === 0)**, то в таком случае будет ставиться дефолтный **класс**: **this.element = 'menu__item';**

**element.classList.add(this.element);**

А если есть хотя бы один **класс**, то будет запускаться вот этот код:  **this.classes.forEach(className => element.classList.add(className))**, в котором сказано, что мы будем перебирать **this.classes методом** **forEach**, так как мы работаем с **массивом** и добавлять каждый класс, который будет находиться в этом **массиве**.

```JavaScript
//Используем классы для карточек 

    class MenuCard {
        constructor(src, alt, title, descr, price, parentSelector, ...classes){
            this.src = src;
            this.alt = alt;
            this.title = title;
            this.descr = descr;
            this.price = price;
            this.classes = classes;
            this.parent = document.querySelector(parentSelector);
            this.transfer = 27;
            this.changeToUAH();
        }

        changeToUAH() {
            this.price = this.price * this.transfer;
        }

        render() {
            const element = document.createElement('div');

            if (this.classes.length === 0) {
                this.element = 'menu__item';
                element.classList.add(this.element);
            } else {
                this.classes.forEach(className => element.classList.add(className));  
            }

            element.innerHTML = `                
                <img src=${this.src} alt=${this.alt}>
                <h3 class="menu__item-subtitle">${this.title}</h3>
                <div class="menu__item-descr">${this.descr}</div>
                <div class="menu__item-divider"></div>
                <div class="menu__item-price">
                    <div class="menu__item-cost">Цена:</div>
                    <div class="menu__item-total"><span>${this.price}</span> грн/день</div>
                </div>
            `;
            this.parent.append(element);
        }
    }
    
    new MenuCard(
        "img/tabs/vegy.jpg",
        "vegy",
        'Меню "Фитнес"',
        'Меню "Фитнес" - это новый подход к приготовлению блюд: больше свежих овощей и фруктов. Продукт активных и здоровых людей. Это абсолютно новый продукт с оптимальной ценой и высоким качеством!',
        9,
        '.menu .container',
    ).render();

    new MenuCard(
        "img/tabs/elite.jpg",
        "elite",
        'Меню “Премиум”',
        'В меню “Премиум” мы используем не только красивый дизайн упаковки, но и качественное исполнение блюд. Красная рыба, морепродукты, фрукты - ресторанное меню без похода в ресторан!',
        14,
        '.menu .container',
    ).render();

    new MenuCard(
        "img/tabs/post.jpg",
        "post",
        'Меню "Постное"',
        'Меню “Постное” - это тщательный подбор ингредиентов: полное отсутствие продуктов животного происхождения, молоко из миндаля, овса, кокоса или гречки, правильное количество белков за счет тофу и импортных вегетарианских стейков.',
        21,
        '.menu .container',
    ).render();
```

![[Untitled 128.png|Untitled 128.png]]