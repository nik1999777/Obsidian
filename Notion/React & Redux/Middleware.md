[https://redux.js.org/api/applymiddleware](https://redux.js.org/api/applymiddleware) - applyMiddleware(...middleware)

  

Как мы уже говорили, что **enhancers** мог расширять любую часть **store** - то **middleware** занимается именно **функцией** **dispatch**, что почти всегда нам и нужно.

**Middleware** - это функции по добавлению функционала и изменению работы **dispatch**.

Чаще всего они позволяют нам в качестве **action** - принимать не только **объекты**, но и **строки**, **функции** и тому подобные конструкции.

Это может быть не только момент оптимизации, но и создание дополнительного функционала.

Почти никогда нам не придется их создавать вручную - в экосистеме React уже есть готовые на любой вкус.

  

index.js .../store

```JavaScript
import { createStore, combineReducers, compose, applyMiddleware } from 'redux';
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
                    compose(applyMiddleware(stringMiddleware),
                            window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__())
                    );

export default store;
```