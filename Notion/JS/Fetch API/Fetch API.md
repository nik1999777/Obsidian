**API - application programming interface** (то есть интерфейс какого-то **программного обеспечения**, либо **приложения**)

Их называют **айпишками**, если говорить просто, то это набор **данных** и возможностей, которое предоставляет нам какое-то готовое решение

Самый банальный **API**, который мы уже изучили - это **DOM API** - и по факту это различные **методы**, которые позволяют нам работать с **элементами** на странице, например мы обращаемся к **document** и у него есть **метод** **querySelector()**. Это возможность уже встроена в браузер и получается, что нам предоставляют эти возможности для того, чтобы мы их могли использовать. Мы точно также можем использовать и сторонние возможности, например **google maps API**, соотвественно **google** предоставляет возможность работать с их картами, как то их модифицировать, добавлять какое-то поведение и тому подобное, то же самое есть у **яндекс карт**, у других каких-то библиотек. Самое главное, что **API** - это такое обобщающее понятие, которое нам говорит, что нам предоставляют готовые какие-то **методы** и **свойства**, которые мы можем использовать.

Возьмем наш мобильный телефон, у него в **операционной системе** тоже есть уже какой-то **API**, например доступ к вибрации нашего телефона, доступ к каким то функциям вашей камеры, и все это называется тоже **API**.

**Fetch API** - это технология уже встроена в браузер, это современная технология, которая позволяет общаться с **сервером** и она построена на **Promise**

[https://jsonplaceholder.typicode.com/](https://jsonplaceholder.typicode.com/) - это **Fake Online REST API** - небольшая база **дынных** в формате **JSON**, которая лежит в интернете и которой мы с вами можем обращаться для того, чтобы тестировать наши какие-то ресурсы.

В данном коде мы прописываем **fetch** и внутри помещаем тот **url**, на который мы будем посылать **запрос**. Если больше ничего не указывать, ни каких параметров, то это будет классический **get** **запрос**, который просто получит данные из этого **url**. Но самое главное находится внутри, **fetch()** использует **Promise**. То есть из конструкции fetch() у нас возвращается именно **Promise,** и когда у нас возвращается **Promise** из какой-то **функции** или из какой-то **переменной**, в которую обернута **функция**, то мы его можем обработать при помощи цепочки **then()**.

В данном коде **метод json()** возьмет данные, полученные от **сервера** **response** в формате **JSON** и превратит в обычный **объект**, который можно дальше использовать (важный момент: у **fetch()** есть встроенные возможности, которые помогают укоротить код и вместо **метода** **JSON.parse()**, использовать метод **json()**, который работает точно также.

Но здесь есть важная особенность, эта команда **response.json()** - она возвращает **Promise** для того, чтобы построить дальше цепочку из **then()**

И далее мы уже ответ от **сервера** **response** в формате обычного **объекта**, выводим в консоль.

```JavaScript
fetch('https://jsonplaceholder.typicode.com/todos/1')
    .then(response => response.json())
    .then(json => console.log(json));
```

А как же делать другие **запросы**, например **Post**. Для этого нам нужно добавить дополнительные настройки для **fetch()**, мы помещаем после **url** **объект** с настройками, которые мы будем задавать, он содержит множество настроек, но основных 2 - это **method** и **body** (тело, которое мы будем отправлять), но и желательно также указывать и заголовки **headers**, которые будут определять какой **контент** мы с вами отправляем.

```JavaScript
fetch('https://jsonplaceholder.typicode.com/posts', {
    method: "Post",
    body: JSON.stringify({name: 'Alex'}),
    headers: {
        'Content-type': 'application/json'
    }
})
.then(response => response.json())
.then(json => console.log(json));
```

![[Untitled 132.png|Untitled 132.png]]

Как видите **Fetch API** намного проще, чем если бы мы работали с **XMLHttpRequest** и именно поэтому данная технология почти везде сейчас и используется.

  

В данном коде мы отправляем на **сервер** в формате **formData**.

Здесь внутри **fetch** в **объекте** мы прописываем **method** и **body**, и далее по цепочки **then** мы **аргумент** **data** (данные, которые возвращаются из **Promise,** то есть те, которые нам вернул **сервер**) превращаем в обычный текст с помощью **метода** **text()**. И далее используем блоки кода **catch()** и **finally()**

```JavaScript
// Forms 

    const forms = document.querySelectorAll('form');

    const message = {
        loading: 'img/form/spinner.svg',
        success: 'Спасибо! Скоро мы с вами свяжемся',
        failure: 'Что-то пошло не так...'
    };

    forms.forEach(item => {
        postData(item);
    });

    function postData(form) {
        form.addEventListener('submit', (e) => {
            e.preventDefault();

            const statusMessage = document.createElement('img');
            statusMessage.src = message.loading;
            statusMessage.style.cssText = `
                display: block;
                margin: 0 auto;
            `;
            form.insertAdjacentElement('afterend', statusMessage);

            const formData = new FormData(form);

            fetch('server.php', {
                method: "Post",
                body: formData
            })
            .then(data => data.text())
            .then(data => {
                console.log(data);
                showThanksModal(message.success);
                statusMessage.remove();
            }).catch(() => {
                showThanksModal(message.failure);
            }).finally(() => {
                form.reset();
            });
        });
    }
```

![[Untitled 1 64.png|Untitled 1 64.png]]

![[Untitled 2 49.png|Untitled 2 49.png]]

А в данном коде мы отправляем на **сервер** в формате **JSON**.

Здесь мы меняем **body** на: **body: JSON.stringify(object)**

Добавляем кусочек кода, где из формата **formData** переводим в **JSON**

И добавляем в **fetch()** заголовки:

**headers: {**

**'Content-type': 'application/json',**

**}**

```JavaScript
// Forms 

    const forms = document.querySelectorAll('form');

    const message = {
        loading: 'img/form/spinner.svg',
        success: 'Спасибо! Скоро мы с вами свяжемся',
        failure: 'Что-то пошло не так...'
    };

    forms.forEach(item => {
        postData(item);
    });

    function postData(form) {
        form.addEventListener('submit', (e) => {
            e.preventDefault();

            const statusMessage = document.createElement('img');
            statusMessage.src = message.loading;
            statusMessage.style.cssText = `
                display: block;
                margin: 0 auto;
            `;
            form.insertAdjacentElement('afterend', statusMessage);

            const formData = new FormData(form);

            const object = {};
            formData.forEach(function(value, key){
                object[key] = value;
            });

            fetch('server.php', {
                method: "Post",
                headers: {
                    'Content-type': 'application/json',
                },
                body: JSON.stringify(object)
            })
            .then(data => data.text())
            .then(data => {
                console.log(data);
                showThanksModal(message.success);
                statusMessage.remove();
            }).catch(() => {
                showThanksModal(message.failure);
            }).finally(() => {
                form.reset();
            });
        });
    }
```

Давайте допустим ошибку в пути к **серверу**, то мы получаем какую-то ошибку, при этом модальное окно не поменялось на 'Что-то пошло не так...

И здесь мы сталкиваемся с одной особенностью **fetch()**: **Promise**, который запускается при помощи **fetch()** не перейдет в состояние отклонено, то есть **reject** из за ошибки **404**, **501**, **502** и т д. Он все равно выполнится нормально, единственное, что у него поменяется это **свойство** **status**, перейдет в состояние **false**.

То есть если внутри **fetch()**, **Promise** попадает на ошибку, которая связана с **http-протоколом**, он не выкинет **reject**, для него это не считается ошибкой, он нормально выполнит **resolve()**

**reject** у нас будет возникать при сбое сети или если что-то там помешало **запросу** вообще выполнится

![[Untitled 3 35.png|Untitled 3 35.png]]

Теперь вместо **XMLHttpRequest**, которым мы раньше делали **AJAX** **запросы**, использовать **fetch()**