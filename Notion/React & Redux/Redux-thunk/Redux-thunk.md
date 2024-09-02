[https://github.com/reduxjs/redux-thunk](https://github.com/reduxjs/redux-thunk) - redux-thunk

  

```Plain
npm i redux-thunk --save
```

  

![[Untitled 72.png|Untitled 72.png]]

**Redux-thunk** - это самый популярный **middleware**, который есть почти во всех проектах.

Он довольно простой и позволяет нам в качестве действий отправлять не **объекты** - а **функции**.

В в свою очередь если будут **dispatch-иться** **функции** - то внутри мы можем делать все что угодно, в том числе и **асинхронные** **операции** (Чаще всего ради них все это и организовывают).

Главная задача **thunk** - передавать функцию, которая потом что-то будет делать асинхронно (это может быть запрос на сервер, таймауты, промисы - а в них уже вкладывается необходимый персонал)

  

index.js .../store

```JavaScript
import { createStore, combineReducers, compose, applyMiddleware } from 'redux';
import ReduxThunk from 'redux-thunk';
import heroes from '../reducers/heroes';
import filters from '../reducers/filters';

const stringMiddleware = () => (next) => (action) => {
    if (typeof action === 'string') {
        return next({
            type: action
        })
    }
    return next(action)
};

const store = createStore( 
                combineReducers({heroes, filters}),
                compose(applyMiddleware(ReduxThunk, stringMiddleware),
                        window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__())
                );

export default store;
```