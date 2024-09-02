  

В данном уроке мы разберем тему - улучшения **store** и добавление ему новых возможностей.

**Store enhancer** — **это** функция высшего порядка, которая создает генератор стора, возвращающий новый, расширенный генератор стора. ... Расширители стора аналогичны понятию - "компоненты высшего порядка" в React, которые также иногда называются "усилителями компонент".

Также на следующем уроке мы разберем понятие - **Middleware**.

Готовых **enhancer** и **middleware** очень много - нам почти никогда не придется создавать свои варианты, но чтобы понять как они работают и зачем нужны и если когда-то придется создавать свой - то придется капнуть немного глубже.

  

В данном коде - мы реализовали механизм усиления **store** внутри переменной **enhancer**, причем тут идет работа со всем большим объектом store.

Но по факту мы меняем работу только **функции** **dispatch**.

Так будет почти всегда - нам не особо интересно менять работу **store**.

И вот механизм, который работает также, но меняет только работу **функции** **dispatch** - называется **middleware** (они будут использоваться намного чаще).

index.js .../store

```JavaScript
import { createStore, combineReducers, compose } from 'redux';
import heroes from '../reducers/heroes';
import filters from '../reducers/filters';

const enhancer = (createStore) => (...args) => {
    const store = createStore(...args);

    const oldDispatch = store.dispatch;
    store.dispatch = (action) => {
        if (typeof action === 'string') {
            return oldDispatch({
                type: action
            })
        }
        return oldDispatch(action)
    }
    return store;
}

const store = createStore( 
                    combineReducers({heroes, filters}),
                    compose(
                        enhancer,
                        window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
                    ));

export default store;
```