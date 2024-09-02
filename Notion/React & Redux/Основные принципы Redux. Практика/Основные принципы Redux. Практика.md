  

![[Untitled 66.png|Untitled 66.png]]

```Plain
npm i redux react-redux
```

  

В данном коде мы реализовали функционал счетчика на **нативном** **JS** с использованием технологии **Redux**.

И здесь мы совершили полный цикл схемы, которую разбирали на прошлом уроке:

- у нас есть **store**, который создается при помощи **redux**
- у нас есть **функция** **reducer**, которую мы создали и добавили в нее какую-то логику
- у нас есть **state**, который содержит текущее **состояние** нашего счетчика
- это текущее **состояние** сначала передается в наш **UI** (на схеме **View**)
- и когда мы используем **обработчики** **событий** - то они принимают в себя **dispatch** и берут какой-то **actions**
- это все переходит в **reducer** и у нас идет опять по кругу: изменение **state** ⇒ обновления нашего **UI** и т д.

index.js

```JavaScript
import React from 'react';
import ReactDOM from 'react-dom';
import { createStore } from 'redux';

const initialState = {value: 0};

const reducer = (state = initialState, action) => {
    switch (action.type) {
        case "INC":
            return {
                ...state,
                value: state.value + 1
            };
        case "DEC":
            return {
                ...state,
                value: state.value - 1
            };
        case "RND":
            return {
                ...state,
                value: state.value * action.payload
            };
        default:
            return state;
    }
}

const store = createStore(reducer);

const update = () => {
    document.getElementById('counter').textContent = store.getState().value;
}

store.subscribe(update);

const inc = () => ({type: 'INC'});
const dec = () => ({type: 'DEC'});
const rnd = (value) => ({type: 'RND', payload: value});

document.getElementById('inc').addEventListener('click', () => {
    store.dispatch(inc());
});

document.getElementById('dec').addEventListener('click', () => {
    store.dispatch(dec());
});

document.getElementById('rnd').addEventListener('click', () => {
    const value = Math.floor(Math.random() * 10);
    store.dispatch(rnd(value));
});

ReactDOM.render(
  <React.StrictMode>
    <>
    
    </>
  </React.StrictMode>,
  document.getElementById('root')
);
```

index.html

```JavaScript
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="\#000000" />
    <meta
      name="My form"
      content="testing Formik"
    />
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    <title>My cool form</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="jumbotron">
       <h1 id="counter">0</h1>
       <button id="dec" class="btn btn-primary">DEC</button>
       <button id="inc" class="btn btn-primary">INC</button>
       <button id="rnd" class="btn btn-primary">RND</button>
    </div>

    <div id="root"></div>
  </body>
</html>
```