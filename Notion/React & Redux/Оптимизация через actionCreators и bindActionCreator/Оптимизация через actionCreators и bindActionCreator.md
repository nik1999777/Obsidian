[https://redux.js.org/api/bindactioncreators](https://redux.js.org/api/bindactioncreators) - bindActionCreator

![[Untitled 67.png|Untitled 67.png]]

![[Untitled 66.png|Untitled 66.png]]

В данном коде **actions** и **reducer** - мы поместили в отдельные файлы.

Также мы импортируем **функцию** **bindActionCreators**:

- первым **аргументом** в нее передаем - **объект** с нашими **actions** **creator**
- вторым - **функцию** **dispatch**

И как итог - мы получаем **объект**, где каждый **action** **creator** обернут в **dispatch**. И мы можем вытащить из этого **объекта** отдельные **функции**, которые теперь очень просто использовать.

Ну и также наш слой **View** - совершенно ничего не знает про **Redux**. Он просто запускает какие-то **функции** и ему не особо важно, что в этих **функциях** происходит.

index.js

```JavaScript
import React from 'react';
import ReactDOM from 'react-dom';
import { createStore, bindActionCreators } from 'redux';
import reducer from './reducer';
import * as actions from './actions';

const store = createStore(reducer);

const {dispatch, subscribe, getState} = store;

const update = () => {
    document.getElementById('counter').textContent = getState().value;
}

subscribe(update);

// const bindActionCreator = (creator, dispatch) => (...args) => {
//     dispatch(creator(...args));
// }

const {inc, dec, rnd} = bindActionCreators(actions, dispatch);
// const decDispatch = bindActionCreators(dec, dispatch);
// const rndDispatch = bindActionCreators(rnd, dispatch);

document.getElementById('inc').addEventListener('click', inc);

document.getElementById('dec').addEventListener('click', dec);

document.getElementById('rnd').addEventListener('click', () => {
    const value = Math.floor(Math.random() * 10);
    rnd(value);
});

ReactDOM.render(
  <React.StrictMode>
    <>
    
    </>
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

actions.js

```JavaScript
export const inc = () => ({type: 'INC'});
export const dec = () => ({type: 'DEC'});
export const rnd = (value) => ({type: 'RND', payload: value});
```