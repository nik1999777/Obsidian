[https://learn.javascript.ru/js-animation#funktsii-raschyota-vremeni](https://learn.javascript.ru/js-animation#funktsii-raschyota-vremeni) - сложный **функции** анимаций с помощью **setInterval**

[https://developer.mozilla.org/ru/docs/Web/API/window/requestAnimationFrame](https://developer.mozilla.org/ru/docs/Web/API/window/requestAnimationFrame) - **requestAnimationFrame** документация

[https://html5.by/blog/what-is-requestanimationframe/](https://html5.by/blog/what-is-requestanimationframe/) - **requestAnimationFrame** простыми словами

[https://html5book.ru/css3-animation/](https://html5book.ru/css3-animation/) - **css3 анимации**

![[Untitled 152.png|Untitled 152.png]]

Сейчас **анимации** легче и лучше создавать при помощи **css3**, но если мы хотим сделать какую-то очень не стандартную **анимацию**, то ее создают с помощью **JS**

Первый способ **анимации** на **JS** - это с использованием **setInterval()** и **setTimeOut()**. Но у такой **анимации** есть свои проблемы. Первая - это то, что мы вручную устанавливаем, как именно у нас будет происходить **анимация** по кадрам. В коде мы поставили задержку в 10 мс. Мы это сделали, чтобы **анимация** казалось плавной. Но если разбираться в технических деталях нашего монитора, то скорость обновления кадров на мониторе и в браузере будет разной. То есть сейчас большинство мониторов пытаются показать 60 кадров/с, а наш браузер постоянно перерисовывает контент, который находится прямо на его странице. И мы этого абсолютно не замечаем, за счет того, что это происходит довольно таки быстро. Эта величина стандартная, примерно 60 кадров/с, но эта величина зависит от нагрузки на наш компьютер. И если у нас параллельно запущено много программ, то конечно же частота **рендеринга** может-быть меньше. И здесь получается **рассинхронизация**, то что наш **setTimeOut()** заставляет перерисовывать страницу не в то же время, когда это делает наш компьютер. Это ведет к доп нагрузки на наш компьютер. Так что это абсолютно неидеальный способ  для того, чтобы создавать какие-то сложные анимации.

**Функция анимации**, которая создавалась при помощи **setInterval()**

```JavaScript
function myAnimation() {
    let pos = 0;

    const id = setInterval(frame, 10);
    function frame() {
        if (pos == 300) {
            clearInterval(id);
        } else {
            pos++;
            elem.style.top = pos + "px";
            elem.style.left = pos + 'px';
        }
    }
}
```

Для решения данной проблемы была создана функция **requestAnimationFrame()**

**requestAnimationFrame** позволяет нам запускать какие-то **функции** в качестве **анимаций**. При этом эта **функция** запускается так, что она берет нашу **анимацию** и подстраивает под чистоту обновления нашего браузера. Таким образом наша **анимация** будет происходить в тот момент, когда у нас идет обновления странички. Соответсвенно мы точно также будем плавно видеть **анимацию**, но при этом нагрузка на браузер сильно снизится.

И также данную анимацию мы можем останавливать **cancelAnimationFrame(id)**

```JavaScript
const btn = document.querySelector('.btn'),
elem = document.querySelector('.box');  
let pos = 0;

function myAnimation() {
pos++;
elem.style.top = pos + "px";
elem.style.left = pos + 'px';

if (pos < 300) {
  requestAnimationFrame(myAnimation);
}
}

btn.addEventListener('click', () => requestAnimationFrame(myAnimation));

let id = requestAnimationFrame(myAnimation);
cancelAnimationFrame(id);
```

```HTML
<!DOCTYPE html>
<html lang="ru">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
   	<title>Java Script</title>
   	<link rel="stylesheet" href="style.css">
  </head>
  <body>
    <button class="btn">Animation</button>
    <div class="wrapper">
        <div class="box"></div>
    </div>

	<script src="script.js"></script>
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
button {
  margin-bottom: 10px;
  margin-top: 10px;
  width: 100px;
  height: 40px;
  background-color: yellow;
  border: none;
}
```