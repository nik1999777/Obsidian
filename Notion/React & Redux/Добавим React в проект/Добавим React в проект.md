![[Untitled 68.png|Untitled 68.png]]

![[Untitled 66.png|Untitled 66.png]]

В данном коде в файле index.js с помощью **метода** **createStore()** - создаем **store** (**глобальное хранилище**).

В данный **метод** передаем - **функцию** **reducer**, которая написана в отдельном файле и отвечает за изменение **store**.

И далее мы берем наш **store** и передаем ниже по всей иерархии нашего дерева компонентов, то есть передаем **store** как **property** в **Provider**.

  

`<Provider store>` — позволяет создавать обёртку для React-приложения и делать состояние Redux доступным для всех компонентов-контейнеров в его иерархии.

  

Это как раз тот механизм, при помощи которого мы берем одну большую сущность **store** (которая является отдельным **хранилищем** для всех наших данных приложений) и связываем его со всем **UI**.

Таким образом - на любом дереве вложенности, в любом компоненте мы сможем обращаться к **store** при помощи **dispatch**.

App.js

```JavaScript
import Counter from "./Counter";

const App = () => {
    return <Counter/>
}

export default App;
```

Counter.js

```JavaScript
const Counter = ({counter, inc, dec, rnd}) => {
    return (
        <div className="jumbotron">
            <h1>{counter}</h1>
            <button onClick={dec} className="btn btn-primary">DEC</button>
            <button onClick={inc} className="btn btn-primary">INC</button>
            <button onClick={rnd} className="btn btn-primary">RND</button>
        </div>
    )
}

export default Counter;
```

  

actions.js

```JavaScript
export const inc = () => ({type: 'INC'});
export const dec = () => ({type: 'DEC'});
export const rnd = (value) => ({type: 'RND', payload: value});
```

index.js

```JavaScript
import React from 'react';
import ReactDOM from 'react-dom';
import { createStore } from 'redux';
import reducer from './reducer';
import { Provider } from 'react-redux';

import App from './components/App';

const store = createStore(reducer);

ReactDOM.render(
    <React.StrictMode>
        <Provider store={store}>
            <App/>
        </Provider>
    </React.StrictMode>,
    document.getElementById('root')
);
```

reducer.js

```JavaScript
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

export default reducer;
```