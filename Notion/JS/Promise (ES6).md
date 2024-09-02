[https://learn.javascript.ru/promise-basics](https://learn.javascript.ru/promise-basics) - **Promise**

[https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise) - **Promise**

  

**Promise** - **промисы** - **обещания**, они позволяет нам достаточно успешно и приятно работать с различными **асинхронными** операциями.

Вспомним, что **асинхронный код** бывает в **TimeOut** и при запросах на **сервер**.

Запускаем код и видим, что через небольшие интервалы появляются **данные**. У нас идет абсолютно **асинхронный код**  при этом **callback** у нас позволяют соблюдать определенный порядок этих действий, и чтобы мы не попадали в **callback hell** (это ласково называют адом **обратных вызовов**),

нам понадобятся **Promise**

```JavaScript
console.log('Запрос данных');

setTimeout(() => {
    console.log('Подготовка данных...');

    const product = {
        name: 'TV',
        price: 2000
    };

    setTimeout(() => {
        product.status = 'order';
        console.log(product);
    }, 2000);
}, 2000);
```

```JavaScript
[Running] node "/Users/nikitaelin/Desktop/work/JS_React/react/my-app/src/tempCodeRunnerFile.js"
Запрос данных
Подготовка данных...
{ name: 'TV', price: 2000, status: 'order' }

[Done] exited with code=0 in 4.053 seconds
```

Мы создаем **обещание**, которое помещаем во внутрь **переменной** **req**: **const req = new Promise()**

Когда мы создаем **обещание**, мы предполагаем, что оно может завершиться, как положительно, так и отрицательно. Но в данный момент мы не знаем, как оно завершится, у нас есть определенный промежуток времени до того, как мы получим результат. (То же самое у нас происходит с **сервером**: мы посылаем **запрос** на **сервер** и ждем ответа от него, мы не знаем, как нам ответит **сервер** - положительно или отрицательно)

Внутри **Promise** у нас лежит **callback - функция** с 2 **аргументами**: **resolve, reject** - по факту это **аргументы**, вместо которых будут подставляться **функции**

Если у нас все хорошо отработало, **сервер** нам ответил, то мы будем вызывать **функцию** **resolve()**, если вдруг что-то пошло не так, то мы будем с вами вызывать **reject()**

Внутри **Promise** у нас идет имитация **асинхронного кода**: мы используем **setTimeout()** и говорим, чтобы **сервер** нам вернул это сообщение: **console.log('Подготовка данных...')**

и эти данные :

**const product = {**

**name: 'TV',**

**price: 2000**

**};**

Мы эти данные получаем, все в порядке, значит мы вызываем **функцию** **resolve()**, которая говорит все окей, наше **обещание** выполнилось в положительную сторону.

И это все произойдет через 2 секунды.

Дальше когда мы начинаем использовать эти **промисы**, мы с вами должны обработать все эти варианты, как **resolve**, так и **reject**.

Для того, чтобы обработать положительный результат у нас есть блок кода **then()**. Он внутри себя как раз принимает тот **аргумент** с **функцией**, который называется **resolve()**.

И еще в данном коде, чтобы **объект** **product** и его данные попали из одной **функции** в другую, мы передаем **product** в **функцию resolve(product)** и далее **функция** **resolve()**, там где используется блок кода **then()** будет уже принимать в качестве **аргумента** **product**: **req.then((product) => {});**

```JavaScript
console.log('Запрос данных');

const req = new Promise(function(resolve, reject) {
    setTimeout(() => {
        console.log('Подготовка данных...');
    
        const product = {
            name: 'TV',
            price: 2000
        };
    
        resolve(product);
    }, 2000);
});

req.then((product) => {
    setTimeout(() => {
        product.status = 'order';
        console.log(product);
    }, 2000);
});
```

```JavaScript
[Running] node "/Users/nikitaelin/Desktop/work/JS_React/react/my-app/src/tempCodeRunnerFile.js"
Запрос данных
Подготовка данных...
{ name: 'TV', price: 2000, status: 'order' }

[Done] exited with code=0 in 4.163 seconds
```

Допустим кроме этих манипуляций:

**setTimeout(() => {**

**product.status = 'order';**

**resolve(product);**

**}, 2000);**

нам необходимо сделать еще какие-то действия, для этого нам необходимо данную конструкцию обернуть в **Promise**. И дальше, чтобы использовать второй **Promise**, нам нужно будет написать **req2.then(data => {});**  - сказать, что нам пришли какие-то данные **data** и запустить **функцию**, которая является вот этим вот **resolve(product),** и **product** придет уже в качестве **data**. (картина слева)

И тут возникает вопрос, а чем этот код отличается от того, что был без **Promise**. У **промисов** есть огромное преимущество перед **callback - функциями**, мы можем возвращать **Promise** и **then** по цепочки. Когда одна **асинхронная** операция выполнится, мы выполним следующую, потом следующую и т д.

Посмотрим как это реализуется на картинке слева:  изначально у нас был один **Promise**, который возвращал нам **переменную** **req**, с которой мы и работаем при помощи блок кода **then()**. Дальше внутри мы создали еще один **Promise** и уже внутри него использовали обычную **callback - функцию**, и это поведение мы можем поменять. Вместо того, чтобы создавать **переменную req2** мы будем просто возвращать новый **Promise**: **return new Promise** и уже создавать цепочку.(картинка по середине)

При этом мы можем возвращать не только **Promise**. Мы напишем **data.modify = true**, в этой же **функции** вернем **data**:  **return data** и далее эти же данные мы по цепочке можем обработать:

**then(data => {**

**console.log(data);**

(картинка справа)

И самое главное чего мы так добиваемся это последовательности нашего кода, даже несмотря на то, какой код внутри: **синхронный** или **асинхронный**.

```JavaScript
console.log('Запрос данных');

const req = new Promise(function(resolve, reject) {
    setTimeout(() => {
        console.log('Подготовка данных...');
    
        const product = {
            name: 'TV',
            price: 2000
        };
    
        resolve(product);
    }, 2000);
});

req.then((product) => {
    const req2 = new Promise((resolve, reject) => {
        setTimeout(() => {
            product.status = 'order';
            console.log(product);
        }, 2000);
    });

    req2.then(data => {
        console.log(data);
    });
});
```

```JavaScript
console.log('Запрос данных');

const req = new Promise(function(resolve, reject) {
    setTimeout(() => {
        console.log('Подготовка данных...');
    
        const product = {
            name: 'TV',
            price: 2000
        };
    
        resolve(product);
    }, 2000);
});

req.then((product) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            product.status = 'order';
            console.log(product);
        }, 2000);
    });
}).then(data => {
    console.log(data);
});
```

```JavaScript
console.log('Запрос данных');

const req = new Promise(function(resolve, reject) {
    setTimeout(() => {
        console.log('Подготовка данных...');
    
        const product = {
            name: 'TV',
            price: 2000
        };
    
        resolve(product);
    }, 2000);
});

req.then((product) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            product.status = 'order';
            console.log(product);
        }, 2000);
    });
}).then(data => {
    data.modify = true;
    return data;
}).then(data => {
    console.log(product);
});
```

Тепер разберем 2 **аргумент** **reject**. Эта тоже **функция**, которую мы самостоятельно прописываем и выполняется эта **функция**, когда наш **Promise** завершился какой-то неудачей. В коде на (картинке слева) мы **reslove()** меняем на **reject()**. И чтобы обработать эту ошибку у нас есть специальный блок кода **catch()** - действие внутри него выполнится при какой-то ошибке, обычно **catch()** ставится в конце.

Также у нас есть блок кода **finally()** - он используется всегда в конце, он позволяет выполнить нам действие в абсолютно любом исходе **Promise**, то есть это действия, которые должны быть произведены абсолютно всегда.

```JavaScript
console.log('Запрос данных');

const req = new Promise(function(resolve, reject) {
    setTimeout(() => {
        console.log('Подготовка данных...');
    
        const product = {
            name: 'TV',
            price: 2000
        };
    
        resolve(product);
    }, 2000);
});

req.then((product) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            product.status = 'order';
            console.log(product);
        }, 2000);
    });
}).then(data => {
    data.modify = true;
    return data;
}).then(data => {
    console.log(product);
}).catch(() => {
    console.error('Произошла ошибка');
});
```

```JavaScript
console.log('Запрос данных');

const req = new Promise(function(resolve, reject) {
    setTimeout(() => {
        console.log('Подготовка данных...');
    
        const product = {
            name: 'TV',
            price: 2000
        };
    
        resolve(product);
    }, 2000);
});

req.then((product) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            product.status = 'order';
            console.log(product);
        }, 2000);
    });
}).then(data => {
    data.modify = true;
    return data;
}).then(data => {
    console.log(product);
}).catch(() => {
    console.error('Произошла ошибка');
}).finally(() => {
    console.log('Finally');
});
```

Давайте рассмотрим ситуацию, когда мы с вами отправляем данные из нашей **формы**, допустим мы делаем это при помощи **Promise**, нам возвращается **обещание**, что либо **сервер** примет успешно данные, либо не примет. Соответсвенно мы можем его обработать при помощи **resolve()**, если все пошло по положительному сценарию, то мы какие-то действия выполняем с помощью блока кода **then()**: показываем модальное окно, потом его скрываем и т д. Если же что-то пошло не так, то срабатывает блок код **catch()**. И потом у нас остается **finally()**, в этот блок кода мы с вами можем поместить участок нашей структуры, где мы очищаем **форму**, здесь не важно, **форма** у нас успешно отправилась, либо произошла ошибка, нам **форму** все равно надо очистить от старых данных, которые были в ней.

Также в **Promise** существуют такие **методы** как **all([])** и **race([])**.

**Метод Promise.all([])** во внутрь себя принимает **массив** с **промисами** и далее обрабатываем блоком кода **then()**:

**Promise.race([test(1000), test(2000)]).then(() => {**

**console.log('All');**

**});**

**Метод Promise.all([])** он ждет окончание всех **промисов**, которые были переданы в **массив** и только потом он будет выполнять какое-то действие.

**Метод** **Promise.race([])** выполняет свои действия только тогда, когда самый первый **Promise** уже правильно отработал.

```JavaScript
const test = time => {
    return new Promise(resolve => {
        setTimeout(() => resolve(), time);
    });
};

test(1000).then(() => console.log('1000'));
test(2000).then(() => console.log('2000'));
```

```JavaScript
const test = time => {
    return new Promise(resolve => {
        setTimeout(() => resolve(), time);
    });
};

Promise.all([test(1000), test(2000)]).then(() => {
    console.log('All');s
});
```

```JavaScript
const test = time => {
    return new Promise(resolve => {
        setTimeout(() => resolve(), time);
    });
};

Promise.race([test(1000), test(2000)]).then(() => {
    console.log('All');s
});
```