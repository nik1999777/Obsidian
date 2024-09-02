[https://redux-toolkit.js.org/api/createReducer](https://redux-toolkit.js.org/api/createReducer) - официальная документация **createReducer()**

  

Когда мы создаем **reducer** - у нас есть проблемы:

- много шаблонного кода
- сильно вложенные конструкции

Эти 2 проблемы **функция** **createReducer()** решает.

  

  

  

![[Untitled 73.png|Untitled 73.png]]

1 способ использования **createReducer()**

**heroes.js**

```JavaScript
import { createReducer } from "@reduxjs/toolkit";

import {
    heroesFetching,
    heroesFetched,
    heroesFetchingError,
    heroCreated,
    heroDeleted
} from '../actions';

const initialState = {
    heroes: [],
    heroesLoadingStatus: 'idle'
}

const heroes = createReducer(initialState, builder => {
    builder
        .addCase(heroesFetching, state => {
            state.heroesLoadingStatus = 'loading';
        })
        .addCase(heroesFetched, (state, action) => {
            state.heroesLoadingStatus = 'idle';
            state.heroes = action.payload;
        })
        .addCase(heroesFetchingError, state => {
            state.heroesLoadingStatus = 'error';
        })
        .addCase(heroCreated, (state, action) => {
            state.heroes.push(action.payload);
        })
        .addCase(heroDeleted, (state, action) => {
            state.heroes = state.heroes.filter(item => item.id !== action.payload);
        })
        .addDefaultCase(() => {});
})

export default heroes;
```

2 способ - он короче, но работает только в **JS**. В **TS** работать он не будет.

```JavaScript
const heroes = createReducer(initialState, {
    [heroesFetching]: state => {state.heroesLoadingStatus = 'loading'},
    [heroesFetched]: (state, action) => {
                    state.heroesLoadingStatus = 'idle';
                    state.heroes = action.payload;
                },
    [heroesFetchingError]: state => {
                    state.heroesLoadingStatus = 'error';
                },
    [heroCreated]: (state, action) => {
                    state.heroes.push(action.payload);
                },
    [heroDeleted]: (state, action) => {
                    state.heroes = state.heroes.filter(item => item.id !== action.payload);
                }
        },
    [],
    state => state
)
```

**index.js**

```JavaScript
import { configureStore } from '@reduxjs/toolkit';
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

const store = configureStore({
    reducer: {heroes, filters},
    middleware: getDefaultMiddleware => getDefaultMiddleware().concat(stringMiddleware),
    devTools: process.env.NODE_ENV !== 'production',
})

export default store;
```