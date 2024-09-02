[https://www.npmjs.com/package/sass](https://www.npmjs.com/package/sass) - npm sass

  

**npm** **пакет** для для работы с **препроцессорами** **sass** и **scss**

> npm i sass --save

  

Чтобы использовать **scss** **переменную** **$main-color**, то путь к ней нужно будет импортировать в каждом файле, где мы ее хотим использовать.

![[Untitled 28.png|Untitled 28.png]]

![[Untitled 1 4.png|Untitled 1 4.png]]

employees-add-form.js

```JavaScript
import './employees-add-form.scss';
```

employees-add-form.scss

```Scss
@import '../../variables.scss';

.add-form {
    margin-top: 20px;
    input {
        width: 350px;
        margin-right: 20px;
    }
}

.app-add-form {
    margin-top: 30px;
    padding: 25px;
    background-color: \#3d5a80;
    border-radius: 4px;
    box-shadow: 15px 15px 30px rgba(0,0,0, .15);
    color: $main-color;
}
```

variables.scss

```Scss
$main-color: rgba(0, 204, 255, 0.705);
```

  

Также можем заметить, что **стили** находятся вместе с версткой. Дело в том, что **webpack** учитывает, что мы в режиме **разработки**. Поэтому он собирает все **стили** в **тэгах**, чтобы в консоле можно было легко подправить их. В финальной сборке все **style** конечно же соберутся.

  

![[Untitled 2 4.png|Untitled 2 4.png]]