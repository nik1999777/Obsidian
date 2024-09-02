[https://reactjs.org/blog/2020/09/22/introducing-the-new-jsx-transform.html](https://reactjs.org/blog/2020/09/22/introducing-the-new-jsx-transform.html) - блог с записью о том, что теперь не нужно импотрровать React и ReactDOM

[https://ru.reactjs.org/docs/introducing-jsx.html](https://ru.reactjs.org/docs/introducing-jsx.html) - базовая докумнетация JSX

  

1. Мы импортируем библиотеку **React**, которая отвечает за работу с **JSX** и внутренностями **React**
2. Мы импортируем библиотеку **ReactDOM**, которая работает с **DOM** структурой на странице

> [!important]  
> Важное замечание. Теперь импортировать эти библиотеки в каждом файле - не нужно. Только в главном файле index.js и все  

```JavaScript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

В **React** мы используем препроцессор **JSX**.

**Babel** переводит **JSX** формат кода в обычный **JS** код.

В обычном **JS** коде используется библиотека **React** и ее **метод createElement()**. Данный **метод** принимает в себя **3 аргумента**: **тэг**, **класс**(если его нет, то **null**) и **содержимое тэга**.

Когда запускается данный **метод** у нас возвращается **объект**(мы его можем наблюдать на картинке снизу), который и помещается уже на страницу.

```JavaScript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';

const elem = <h2>Hello world!</h2>;

const elem = React.createElement('h2', null, 'Hello world');

const elem = {
  type: 'h2',
  props: {
    className: null, 
    children: 'Привет, мир'
  }
};

ReactDOM.render(
  elem,
  document.getElementById('root')
)
```

![[Untitled 25.png|Untitled 25.png]]

Важные правила в использовании **JSX**:

> [!important]  
> когда мы создаем элемент - всегда нужно использовать круглые скобки, если это многострочная структура  
  
> [!important]  
> использовать один корневой элемент(в примере у нас <div>) для обертки всей структуры  
  
> [!important]  
> не забывать закрывать тэги, особенно если они самозакрывающиеся(пример <button/>)  
  
> [!important]  
> при использовании различных атрибутов помните, что 2 атрибута у нас отличаются от стандартной верстки - className и htmlFor(потому что слова class и for - зарезервированы). А также то что все атрибуты у нас пишутся в формате CamelCase  
  
> [!important]  
> мы можем спокойно вставлять значения, как в атрибуты, так и во внутрь элементов при помощи фигурных скобок(в атрибуты можно при помощи кавычек)  
  
> [!important]  
> и во внутрь фигурных скобок мы можем помещать все что угодно, кроме объектов(связано это с тем, что любое значение будет преобразовано к строке для того чтобы у нас не было никаких вмешательств со стороны). А преобразование объекта к строчному формату - выдаст ошибку.  

```JavaScript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';

const text = <h2>Hello world!</h2>;

const elem = (
  <div>
    <h2 className="text">Текст: {text}</h2>
    <h2>Текст: {2+2}</h2>
    <h2>Текст: {new Date()}</h2>
    <h2>Текст: {[2123]}</h2>
    <input type="text" />
    <label htmlFor=""></label>
    <button tabIndex="0"></button>
    <button></button>
  </div>
);

ReactDOM.render(
  elem,
  document.getElementById('root')
);
```