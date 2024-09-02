[https://developer.mozilla.org/ru/docs/Web/API/XMLHttpRequest](https://developer.mozilla.org/ru/docs/Web/API/XMLHttpRequest) - **XMLHttpRequest**

[https://developer.mozilla.org/ru/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest](https://developer.mozilla.org/ru/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest) - использование **XMLHttpRequest**

[https://developer.mozilla.org/ru/docs/Web/API/FormData/Using_FormData_Objects](https://developer.mozilla.org/ru/docs/Web/API/FormData/Using_FormData_Objects) - **объект FormData**

[https://ilikekillnerds.com/2017/09/convert-formdata-json-object/](https://ilikekillnerds.com/2017/09/convert-formdata-json-object/) - из **formData в JSON**

[https://ru.wikipedia.org/wiki/%D0%97%D0%B0%D0%B3%D0%BE%D0%BB%D0%BE%D0%B2%D0%BA%D0%B8_HTTP](https://ru.wikipedia.org/wiki/%D0%97%D0%B0%D0%B3%D0%BE%D0%BB%D0%BE%D0%B2%D0%BA%D0%B8_HTTP) - **заголовки HTTP**

[https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%BA%D0%BE%D0%B4%D0%BE%D0%B2_%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F_HTTP](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%BA%D0%BE%D0%B4%D0%BE%D0%B2_%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F_HTTP) - список **кодов состояния HTTP**

[https://developer.mozilla.org/ru/docs/Web/API/XMLHttpRequest/readyState](https://developer.mozilla.org/ru/docs/Web/API/XMLHttpRequest/readyState) - **XMLHttpRequest.readyState**

  

**XMLHttpRequest это API**, который предоставляет клиенту функциональность для обмена данными между клиентом и **сервером**. Данный **API** предоставляет простой способ получения данных по ссылке без перезагрузки страницы. Это позволяет обновлять только часть веб-страницы не прерывая пользователя.

Чтобы наша страница, наш фронтенд умел общаться с **сервером**, нам необходимы **HTTP запросы**, которые мы будем отправлять.

Мы можем **запрашивать** **данные**, **постить** **данные** и выполнять другие операции и чтобы все это происходило **асинхронно**, без перезагрузки страницы, нам и нужна технология **AJAX**.

  

В данном коде мы получаем элементы со страницы (а конкретно два **input**). Далее мы реализуем, что при вводе чисел в первый **input** и на основании запроса от **сервера**, различных обработок у нас будет показываться другой результат в USD (второй **input**).

Для этого мы назначаем **обработчик события** **input** . Далее самое главное, мы должны сделать **запрос** на **сервер**, и для того, чтобы это сделать, мы воспользуемся **встроенным объектом** в браузер **XMLHttpRequest**.

Создаем **переменную** **request** (в переводе запрос) и далее создаем **новый объект new XMLHttpRequest()**.

Теперь когда мы создали **экземпляр** **объекта** у него есть свои **методы**, свои **свойства** и свои **события**.

Начнем с **методов**, которые у нас будут постепенно вызываться, начнем с **метода open()**.

Этот **метод** не открывает соединение между **frontend** и **backend**, а лишь собирает настройки, которые помогут в будущем сделать **запрос** и как обычно он принимает в себя несколько **аргументов**:

- 1 **аргумент** - это **method**, тот который используется для **запроса**(это может быть **get** или **post**)
- 2 **аргумент**это **url** - путь к нашему **серверу**
- 3 **аргумент** - **async** - он отвечает за **асинхронность** (здесь нужно вспомнить, что такое **синхронный** и **асинхронный** код, **синхронный** код идет по порядку, а **асинхронный** код наоборот, примером является **setTimeout**, **setInreval**; также **AJAX** запросы являются **асинхронным** кодом, то есть мы послали **запрос**, остальной код, который идет после **запроса** продолжит выполняться и потом, когда **сервер** ответит, наш код, который был **асинхронный** закончит свою работу)
- 4 **аргументом** - **login** - логин
- 5 **аргумент** - **pass** - пароль

```JavaScript
const inputRub = document.querySelector('\#rub'),
      inputUsd = document.querySelector('\#usd');

inputRub.addEventListener('input', () => {
    const request = new XMLHttpRequest();

    request.open(method, url, async, login, pass);
});
```

Мы используем **GET** **запрос** и прописываем ссылку на **сервер** **js/current.json** и тут важно знать, что нужно формировать путь относительно **index.html**, потому что именно страничка наша открывается в браузере и на ней работают **скрипты**.

Когда мы отправляем **запрос** нам нужно сказать, что именно мы отправляем, какая информация, в чем закодирована и т д. Делается это для того, чтобы наши **трансферные протоколы** понимали, что они передают, и когда они приходят к **серверу**, **сервер** точно понимал, что он принимает в себя

(это **JSON** файл или это какие-то изображения). Для всего этого есть **HTTP заголовки**. Но пока мы будем использовать заголовок, который нужен непосредственно для передачи **JSON файлов**. Как это делается? Мы используем **метод setRequestHeader()** и записываем внутри несколько значений.

Сначала тип контента, а дальше мы указываем какой тип для нашего JSON и тут же указываем котировку, которую будем использовать: **('Content-type', 'application/json; charset=utf-8')**

И вот теперь, когда все приготовления у нас готовы, мы с вами можем отправить **запрос**, делается это при помощи **метода** **send()**.

  

Далее разберем **события** **объекта** **XMLHttpRequest**.

- Первое **событие** - это **readystatechange** - оно отслеживает статус готовности нашего **запроса** в данный текущий момент, это **событие** следит за **свойством** **readyState**
- Второе часто используемое **событие** - это **load** оно срабатывает, когда наш **запрос** полностью загрузился и мы получили какой-то результат.

Внутри **обработчика события** пишем **условие**:  **if (request.readyState === 4 && request.status === 200)** - оно означает, что если **readyState** строго равен **4** (это четвертое значение - done - операция полностью завершена) и **status** строго равен **200** (это ок, хорошо), то мы выполняем след действия:

**console.log(request.response)** - выводим в консоль с помощью **свойства** **response** ответ от **сервера**

**const data = JSON.parse(request.response)** - переводим наш ответ от **сервера** из **JSON** **формата** в обычный **объект**

**inputUsd.value = (+inputRub.value / data.current.usd).toFixed(2)** - наше введенное значение в **inputRub** делим на наш **объект**, который мы получили с **сервера** и **методом** **toFixed(2)** делаем так, чтобы значение после запятой было 2 знака.

А если у нас **условие** не сработало прописываем: **inputUsd.value = "Что-то пошло не так"**

```JavaScript
const inputRub = document.querySelector('\#rub'),
      inputUsd = document.querySelector('\#usd');

inputRub.addEventListener('input', () => {
    const request = new XMLHttpRequest();

    request.open('GET', 'js/current.json');
    request.setRequestHeader('Content-type', 'application/json; charset=utf-8');
    request.send();

    request.addEventListener('readystatechange', () => {
        if (request.readyState === 4 && request.status === 200) {
            console.log(request.response);
            const data = JSON.parse(request.response);
            inputUsd.value = (+inputRub.value / data.current.usd).toFixed(2);
        } else {
            inputUsd.value = "Что-то пошло не так";
        }
    });
});
```

Нам редко нужны значения, стадии в свойстве **readyState**. Мы чаще будем использовать **событие** **load** - оно проще, оно срабатывает только один раз, когда **запрос** уже готов. Здесь мы удаляем в **условии** **request.readyState === 4** и у нас все отрабатывает точно также.

```JavaScript
request.addEventListener('load', () => {
    if (request.status === 200) {
        const data = JSON.parse(request.response);
        inputUsd.value = (+inputRub.value / data.current.usd).toFixed(2);
    } else {
        inputUsd.value = "Что-то пошло не так";
    }
});
```

![[Untitled 129.png|Untitled 129.png]]

![[Untitled 1 61.png|Untitled 1 61.png]]

Существуют свойства объекта **XMLHttpRequest**:

- 1 **свойство** - **status** - показывает статус от нашего **запроса** (это 404, 0, 200, 403 и т. д)
- 2 **свойство** - **statusText** - это текстовое описание ответа от **сервера** (OK, not found и т д)
- 3 **свойство** - **response** - ответ от **сервера**, соответсвенно здесь у нас лежит тот ответ, который нам задал **backend - разработчик**
- 4 **свойство** - **readyState** - оно содержит текущее состояние нашего **запроса** и у этого **свойства** есть 5 значений:

|Значение|Состояние|Описание|
|---|---|---|
|0|[[UNSENT]]|Объект был создан. Метод open() ещё не вызывался.|
|1|[[OPENED]]|Метод open() был вызван.|
|2|[[HEADERS_RECEIVED]]|Метод send() был вызван, доступны заголовки (headers) и статус.|
|3|[[LOADING]]|Загрузка; responseText содержит частичные данные.|
|4|[[DONE]]|Операция полностью завершена.|

  
  

Это наш **сервер** в формате **JSON**

current.json

```JavaScript
{
    "current": {
        "usd": 74
    }
}
```

```JavaScript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Calc</title>
    <style>
        label {
            display: block;
            font-size: 30px;
        }
        input {
            width: 300px;
            height: 50px;
            font-size: 30px;
        }
    </style>
</head>
<body>
    <label for="rub">RUB</label>
    <input id="rub" type="text">
    <label for="usd">USD</label>
    <input id="usd" type="text">
    <script src="js/script.js"></script>
</body>
</html>
```