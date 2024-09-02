[https://developer.mozilla.org/ru/docs/Web/API/Element/classList](https://developer.mozilla.org/ru/docs/Web/API/Element/classList) - про classList

[https://developer.mozilla.org/ru/docs/Web/API/Element/matches](https://developer.mozilla.org/ru/docs/Web/API/Element/matches) - про matches

[https://learn.javascript.ru/event-delegation](https://learn.javascript.ru/event-delegation) - про делегирование событий

[https://medium.com/@stasonmars/%D0%B4%D0%B5%D0%BB%D0%B5%D0%B3%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D1%81%D0%BE%D0%B1%D1%8B%D1%82%D0%B8%D0%B8%CC%86-%D0%B2-javascript-d91cbdd8916a](https://medium.com/@stasonmars/%D0%B4%D0%B5%D0%BB%D0%B5%D0%B3%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D1%81%D0%BE%D0%B1%D1%8B%D1%82%D0%B8%D0%B8%CC%86-%D0%B2-javascript-d91cbdd8916a) - про делигирование событий

  

**Свойство classList** довольно большое, оно содержит как **методы**, так и еще одно полезное **свойство**, с помощью которого мы можем узнать кол-во чего-то у элемента(например кол-во **классов**).

```JavaScript
const btns = document.querySelectorAll('button'),

console.log(btns[0].classList.length);
```

![[Untitled 118.png|Untitled 118.png]]

Также у **свойства classList** есть **методы**:

1) **Метод item()** - позволяет нам получить **класс**, который располагается под определенным индексом.

2) **Метод add()** - добавляет определенные **классы**, их можно добавлять сразу несколько.

3) **Метод remove()** - удаляет ненужные нам **классы**.

4) **Метод toggle()** - он позволяется тоглить классы, то есть если данный класс есть на элементе,  то он будет убран, а если его нет, то наоборот добавлен.

```JavaScript
console.log(btns[0].classList.item(0));
console.log(btns[0].classList.add('red')); - здесь мы можем также добавлять несколько классов, например ('red', 'black', 'green')
console.log(btns[0].classList.remove('blue'));
console.log(btns[0].classList.toggle('blue'));
```

![[Untitled 1 55.png|Untitled 1 55.png]]

![[Untitled 2 42.png|Untitled 2 42.png]]

![[Untitled 3 30.png|Untitled 3 30.png]]

**Метод** **contains()** проверяет наличие **класса** на элементе и возвращает **булиновое значение**, если **класс** есть, то возвращает **true**, если нет, то **false**.

```JavaScript
if (btns[1].classList.contains('red')) {
    console.log('red');
}
```

И этот механизм открывает нам двери в **динамическое преобразование** страницы.

![[Untitled 4 21.png|Untitled 4 21.png]]

Вот пример, как используется данный механизм.

Этот код читается так: Когда мы кликаем на первую кнопку, начинается проверка второй кнопки. Если у второй кнопки нет **класса** **'red'**, то он добавляется, если же тот **класс** у второй кнопки присутствует, то мы его просто убираем.

```JavaScript
btns[0].addEventListener('click', () => {
    if (!btns[1].classList.contains('red')) {
        btns[1].classList.add('red');
    } else {
        btns[1].classList.remove('red');
    }
});
```

И также можно использовать для данного механизма **метод toggle()**, но в сложных скриптах данный **метод** не всегда доступен и применим.

```JavaScript
btns[0].addEventListener('click', () => { 
    btns[1].classList.toggle('red');
});
```

![[Untitled 5 17.png|Untitled 5 17.png]]

Существует устаревшее **свойство className**, которое уже не используется.

```JavaScript
console.log(btns[0].className);
```

**Делегирование событий**

Бывает так, что на нашей странице много кнопок и мы хотим, чтобы при клике на любую из них вызывалось одно и то же **событие**. И тут мы знакомимся с **делегированием событий**. Суть в чем: мы берем элемент, который является **родителем** для всех этих кнопок( в данном случае наш серый блок) и работаем непосредственно с ним, то есть мы назначаем **обработчик событие** на него. А внутри этого **родителя** мы будем проверять на что мы кликнули, то есть мы назначаем **функцию** для его **потомков**, если они подходят под какие-то определенный параметры.

Посмотрим на пример. Здесь мы устанавливаем **обработчик событие** на **родителя** и проверяем **условие**: нажали ли мы на элемент с **тэгом BUTTON**: **event.target.tagName == "BUTTON"**, если да, то при нажатии на любую из кнопок в консоль выводится сообщение **Hello**.

Вот классический пример использование **делегирования событий**.

```JavaScript
wrapper.addEventListener('click', (event) => {
    if (event.target && event.target.tagName == "BUTTON") {
        console.log('Hello');
    }
});
```

![[Untitled 6 16.png|Untitled 6 16.png]]

В данном примере использовали **метод** **contains()** и здесь выводится сообщение **Hello** при нажатии на первую кнопку с **классом blue**.

```JavaScript
wrapper.addEventListener('click', (event) => {
    if (event.target && event.target.classList.contains('blue')) {
        console.log('Hello');
    }
});
```

Мы можем добавить еще одну копку динаически с помощью **метода createElement()**, добавив ей **класс** со **стилями** и поместив в конец **родителя**. И при нажатии на эту кнопку у нас также будет выводится в консоль **Hello**.

```JavaScript
const btn = document.createElement('button');
btn.classList.add('red');
wrapper.append(btn);
```

![[Untitled 7 15.png|Untitled 7 15.png]]

Если мы используем метод **forEach()**, кликая на те кнопки, которые были изначально в верстке, у нас все срабатывает. Но как только мы кликаем на красную кнопку, которая появилось у нас динамически и у нас ничего не происходит. Эта кнопка абсолютно ничего не знает про этот **обработчик события**, который был добавлен до того, как она еще появилась. Вот вам и классический пример ошибки.

```JavaScript
btns.forEach(btn => {
    btn.addEventListener('click', () => {
        console.log('Hello');
    });
});
```

И еще познакомимся с **методом matches()**, который любит компания **google**. По простому это означает, что какой-то элемент совпадает с чем-то. И вот с чем мы сравниваем мы прописываем, например: **button.red**.

```JavaScript
wrapper.addEventListener('click', (event) => {
    if (event.target && event.target.matches("button.red")) {
        console.log('Hello');
    }
});
```

**Делегирование событий** - это один из полезных приемов для работы с **DOM - деревом**, он отлично подходит, если есть много элементов с одинаковыми **обработчиками**, причем при **динамическом изменени**и они точно также будут применяться к новым элементам. Мы пишем намного меньше кода и экономим память браузера, ведь **обработчик событий** всего лишь один.

  

```HTML
<!DOCTYPE html>
<html lang="ru">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>JavaScript</title>
    <link rel="stylesheet" href="css/style.css">
  </head>
  <body>
    <div id="first" class="btn-block">
      <button class="blue some"></button>
      <button></button>
      <button></button>
      <button></button>
      <button></button>
      <button></button>
      <button></button>
      <button></button>
    </div>
    
  <script src="js/script.js"></script>
  </body>
</html>
```

```CSS
.box {
   position: absolute;
   width: 100px;
   height: 100px;
   background-color: blue;
 }
 .wrapper {
   position: relative;
   width: 400px;
   height: 400px;
   border: 3px solid red;
 }
 .btn-block {
    padding: 10px;
    background-color: grey;
    margin-top: 10px;
 }
 button {
   margin-bottom: 10px;
   margin-top: 10px;
   width: 100px;
   height: 40px;
   background-color: yellow;
   border: none;
   transition: 0.3s all;
 }
 .blue {
     background-color: blue;
 }
 .red {
     background-color: red;
 }
```