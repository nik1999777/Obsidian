[https://learn.javascript.ru/callbacks](https://learn.javascript.ru/callbacks) - **callback функции**

  

Создадим несколько **функций** function first() и function second(). **Функция**  function first()  будет иметь в себе какую-то задержку, например эта **функция** может общаться с сервером или в ней будет обработка каких-то сложных, тяжелых данных. Для того чтобы с симулировать такое поведение, создадим конструкцию, которая делает определенную задержку в нашем коде.

Во второй **функции** задержки никакой не будет.

Запускаем **функции** и видим, что сначала у нас получается 2, а потом 1. То есть вторая **функция** у нас сработала раньше, чем первая (это и понятно из-за задержки). Но если смотреть только на код все становится не совсем очевидным, потому что эта задержка изначально у нас может-быть не видна (то есть мы можем не знать какая у нас задержка и как долго она будет происходить).

**Поэтому надо запомнить важное правило, если функции идут в коде одна за другой, это не значит, что они выполняются прямо также, да они запускаются одна за другой, но результат могут дать в разное время!**

```JavaScript
function first() {
    
    setTimeout(function() {
        console.log(1);
    }, 500);
}

function second() {
    console.log(2);
}

first();
second();
```

Что такое **Callback**? Если говорить просто, то эта **функция**, которая должна быть выполнена после того, как другая **функция** завершила свое выполнение.

Напишем функцию с 2 **аргументами** (lang, callback), в **аргумент** lang  мы просто передадим какую-то строку с языком, а вторым **аргументом** будет callback, и вот это главный шаблон **callback функции**, то что в другую **функцию** в качестве **аргумента** в будущем мы сможем передать другую **функцию**.

Пишем какое-то действие, например console.log(`Я учу: ${lang}`), подставив **аргумент** ${lang}, то есть язык, который сюда приходит, а вот дальше, чтобы выполнить эту **callback функцию**, которая тоже будет передана, как **аргумент**, мы ее берем и вызываем callback(), то есть теперь получается, что у нас только, когда выполнится действие от первой **функции** console.log(`Я учу: ${lang}`), после этого выполнится строго уже вторая **функция** callback().

И теперь смотрим: learnJS('JavaScript', function(), например мы сначала просто передаем **строку** 'JavaScript' и дальше передаем, как раз **callback функцию** function() - это может-быть **анонимная функция**, которую мы как раз передаем.

Запускаем код и видим, что сначала Я учу: JavaScript, а потом Я прошел этот урок!. Таким образом у нас всегда должна соблюдаться последовательность **функций**.

```JavaScript
function learnJS(lang, callback) {
    console.log(`Я учу: ${lang}`);
    callback();
}

learnJS('JavaScript', function() {
    console.log(`Я прошел этот урок!`);
});
```

Здесь мы передаем **не анонимную функцию**.

Один из важных моментов это то, как мы передаем эту **функцию**. Мы написали просто done без круглых скобок:

learnJS('JavaScript', done)

потому что мы просто передаем **функцию**, **функция** done передается вместо callback и только внутри в нужный момент уже вызывается callback(), именно поэтому мы не ставим круглые скобки, мы не вызываем **функцию**, мы ее передаем, чтобы она в дальнейшем когда-то была использована.

```JavaScript
function learnJS(lang, callback) {
    console.log(`Я учу: ${lang}`);
    callback();
}

function done() {
    console.log(`Я прошел этот урок!`);
}

learnJS('JavaScript', done);
```

В Node js очень часто используют **callback.**