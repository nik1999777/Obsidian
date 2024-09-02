[https://redux-toolkit.js.org/api/createAction](https://redux-toolkit.js.org/api/createAction) - официальаня докуменатция о createAction()

  

**Функция** **createAction()** и **createReducer()** - используются довольно редко.

В **Redux Toolkit** есть отдельная **функция** - **createSlice()**, которая объединяет 2 этих функционала в одно целое.

  

Когда мы создаем **action creators** у нас получается довольно много одинакового кода, который хотелось бы все таки упростить - в этом и помогает функция - **createAction()**.

Данная **функция** принимает 2 **аргумента**:

- тип действия
- вспомогательную функцию

В данном коде мы видим, как теперь используется **createAction()**.

```JavaScript
import { createAction } from "@reduxjs/toolkit";

export const fetchHeroes = (request) => (dispatch) => {
    dispatch(heroesFetching());
    request("http://localhost:3001/heroes")
        .then(data => dispatch(heroesFetched(data)))
        .catch(() => dispatch(heroesFetchingError()))
}

export const fetchFilters = (request) => (dispatch) => {
    dispatch(filtersFetching());
    request("http://localhost:3001/filters")
        .then(data => dispatch(filtersFetched(data)))
        .catch(() => dispatch(filtersFetchingError()))
}

// export const heroesFetching = () => {
//     return {
//         type: 'HEROES_FETCHING'
//     }
// }

export const heroesFetching = createAction('HEROES_FETCHING');

// export const heroesFetched = (heroes) => {
//     return {
//         type: 'HEROES_FETCHED',
//         payload: heroes
//     }
// }

export const heroesFetched = createAction('HEROES_FETCHED');

export const heroesFetchingError = () => {
    return {
        type: 'HEROES_FETCHING_ERROR'
    }
}

export const filtersFetching = () => {
    return {
        type: 'FILTERS_FETCHING'
    }
}

export const filtersFetched = (filters) => {
    return {
        type: 'FILTERS_FETCHED',
        payload: filters
    }
}

export const filtersFetchingError = () => {
    return {
        type: 'FILTERS_FETCHING_ERROR'
    }
}

export const activeFilterChanged = (filter) => {
    return {
        type: 'ACTIVE_FILTER_CHANGED',
        payload: filter
    }
}

export const heroCreated = (hero) => {
    return {
        type: 'HERO_CREATED',
        payload: hero
    }
}

export const heroDeleted = (id) => {
    return {
        type: 'HERO_DELETED',
        payload: id
    }
}
```