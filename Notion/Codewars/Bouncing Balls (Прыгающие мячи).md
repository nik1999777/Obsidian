Функция `bouncingBall()` - возвращает число - кол-во раз, которое мать увидит, как мяч проходит перед ее окном (в том числе когда он падает и подпрыгивает).

В данном решении:

- мы создаем function `boucingBall()` с тремя аргументами:
    - `h` - высота дома
    - `bounce` - коэффициент отскока
    - `window` - высота до окна
- внутри создаем условие`(h > 0 && bounce > 0 && bounce < 1 && window < h)` и если оно верно:
    - то к count(счетчик) присваиваем 1 - `count = 1`
    - к current(текущий) присваиваем высоту дома, умноженный на bounce(коэффициент отскока) - `current = h * bounce`
- далее у нас идет цикл `while`, который говорит - что пока current(текущий) больше window(высоты до окна) - `(current > window)`, у нас будет выполняться такие действия:
    - к current присваивается старый current умноженный на bounce - `current = current * bounce`
    - и к count присваиваем старый count + 2 (почему + 2, д потому что когда мячик отскакивает от земли он пролетает перед окном 2 раза) - `count = count + 2`
- и по итогу мы возвращаем получившийся count **-** `return count`
- а если условие - не выполняется, то мы возвращаем - `return -1`

```JavaScript
function bouncingBall(h,  bounce,  window) {
  if (h > 0 && bounce > 0 && bounce < 1 && window < h) {
    count = 1;
    current = h * bounce;
    while (current > window) {
      current = current * bounce;
      count = count + 2;
    }
    return count;
  } else {
    return -1;
  }
}

bouncingBall(3, 0.66, 1.5);
```

```JavaScript
/usr/local/bin/node /Users/nikitaelin/Desktop/test/script.js
3

Process finished with exit code 0
```