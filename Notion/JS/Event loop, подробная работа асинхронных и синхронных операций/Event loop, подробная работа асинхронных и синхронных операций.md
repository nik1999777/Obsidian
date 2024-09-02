[http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D](http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D) - **Event loop**

  

Посмотрим на код на картинке слева. В консоле у нас идет: **1**, **2**, **timepot** и **timepot_4000**. Такой результат мы получаем за счет **синхронного** и **асинхронного** кода.

Мы уже знаем, что **асинхронные** являются операции, которые запускаются с течением определенного времени - это **setTimeOut()** и **setInterval()**. Также это могут-быть абсолютно любые запросы на **сервер**, это происходит из-за того, что мы не знаем через сколько нам ответит **сервер**.

То есть данные операции запускаются **асинхронно** и абсолютно не мешают другому коду, которые работает в нашем приложении.

Но если капнуть еще в глубь, то на самом деле все **callback - функции**, которые мы используем являются **асинхронными**. Когда мы прописываем **обработчик события scroll**, либо мы отслеживаем **событие scroll,** либо мы используем **событие submit** - все эти операции происходят **асинхронно**

Давайте посмотрим на код на картинке справа. У нас здесь 2 **асинхронные** операции, которые выполняются собственно в одно и то же время. И у нас результат в консоле точно такой же. Сначала **timepot**, а потом  **timepot_4000**. Это логично, потому что первый в коде **setTimeOut()** стоит выше и он соответсвенно раньше запустился.

И теперь самый главный вопрос. А как это реализовано в плане **JS**, то есть внутри этого языка?

Для этого мы сейчас познакомимся с такими понятиями как **stack**, **event loop** и **web apis**.

```JavaScript
console.log(1);

setTimeout(() => {
    console.log('timepot');
}, 2000);

setTimeout(() => {
    console.log('timepot_4000');
}, 4000);

console.log(2);
```

```JavaScript
console.log(1);

setTimeout(() => {
    console.log('timepot');
}, 4000);

setTimeout(() => {
    console.log('timepot_4000');
}, 4000);

console.log(2);
```

```JavaScript
[Running] node "/Users/nikitaelin/Desktop/work/JS_React/react/my-app/src/tempCodeRunnerFile.js"
1
2
timepot
timepot_4000

[Done] exited with code=0 in 4.137 seconds
```

```JavaScript
[Running] node "/Users/nikitaelin/Desktop/work/JS_React/react/my-app/src/tempCodeRunnerFile.js"
1
2
timepot
timepot_4000

[Done] exited with code=0 in 4.137 seconds
```

Для того, чтобы это все было максимально наглядно, мы посмотрим как это работает все изнутри в данном сервисе.

Слево у нас есть: **js** код и ниже кусочек **html** кода, который **рендерится**. И когда мы будем нажимать на кнопку, у нас будет запускаться код.

Справа у нас есть:

- **call stack** - это те операции, то есть вызовы **функции**, которые выполняются в данный момент.
- **web apis** - это специальное хранилище, которое есть в браузере для того, чтобы хранить какие-то промежуточные данные.(Например, когда мы запускаем **setTimeOut()** у нас где-то должно записываться, что такая **функция** должна выполнится через определенное кол-во времени, соответсвенно этот контейнер служит для того, чтобы запоминать такую информацию)
- **callback queue** - все наши операции, которые выполняются в браузере, они на самом деле становятся в какую-то очередь, параллельно они выполнятся не могут и соответсвенно в этот контейнер приходят различные **события**, различные **функции** и просто становятся в очередь.

![[Untitled 153.png|Untitled 153.png]]

В данном коде мы можем видеть, что сначала страница загрузилась, она думает, что-то делает, после этого у нас выводится **alert** и далее у нас идет **рендеринг** нашего текста. Значит наша очень тяжелая задача попала в **call stack**, то есть в **call stack** она очень очень долго обрабатывает какие-то данные, и пока она полностью не закончится, пока **call stack** не освободится, мы абсолютно ничего не сможем сделать на странице.

```JavaScript
let k = 0;

function count() {
    for (let i = 0; i < 1e9; i++) {
        k++;
    }
    alert('done');
}

count();
```

![[Untitled 1 78.png|Untitled 1 78.png]]

![[Untitled 2 57.png|Untitled 2 57.png]]

Теперь разберем вопрос, который очень любят задавать на собеседовании.

В данном коде в консоле мы сначала получили **2**, а потом **1**. И тут дело в том, что **setTimeOut()** все равно проходит через **асинхронную** часть, то есть он попадает в **web apis,** сначала он записывается в нем и после этого идет в **callback queue**.

Ответ таков, что если операция будет **асинхронная**, даже при том, что будет стоять **0 мс**, то в любом случаем сначала выполнится **синхронный** код, который расположен дальше.

И другой нюанс, если **JS** видит **0**, **1**, **2** и **3** , то он все равно подставляет **4** **мс**, сделано это для совместимости между разными браузерами, ведь мы совершенно не можем предугадать, как разные браузеры будут обрабатывать **0 мс**. Поэтому JS ставит **4 ms**, чтобы хоть какая то минимальная задержка все таки была.

```JavaScript
setTimeout(() => {
    console.log(1);
}, 0)

console.log(2);
```