[https://redux-toolkit.js.org/api/createSlice](https://redux-toolkit.js.org/api/createSlice) - официальная документация **createSlice()**

  

**Функция** **createSlice()** объединяет функционал 2-х предыдущих **функций** - **createReducer()** и **createAction()**.

Разработчики **Redux** **Toolkit** подумали и решили - а зачем нам вообще разделять функционал **action creator-ов** и **reducer-ов**?

Почему бы нам не создать одну сущность, которая будет уметь все это делать - так и появился **createSlice()**.

  

В результате работы **функции createSlice()** - мы получаем **объект**, называемым **slice**.

**createSlice()** принимает в себя 4 аргумента для настройки:

- **name** - пространство имен создаваемых **actions**
- **initialState** - начальное состояние **reducer**
- **reducers** - **объекты** с **обработчиками**
- **extraReducers** - **объект**, который содержит **reducers** другого среза (**slice**) - данный параметр может потребоваться в случае необходимости обновления **объекта**, относящемуся к другому срезу (**slice**)

И когда функция **createSlice()** закончит работу - мы с вами в итоге получим объект с 3-мя полями:

- имя среза (**slice**)
- **reducer**
- **actions**

**createSlice()** объединяет все что можно в данном функционале - она и создает **reducers**, она генерирует **action** **creators** и также возвращает имя среза (**slice**), с которым мы будем работать.

И по итогу нам не нужно будет разделять этот функционал на отдельные файлики и на отдельные сущности - у нас все будет в одном месте.

![[Untitled 74.png|Untitled 74.png]]

**heroesSlice.js**

```JavaScript
import { createSlice } from "@reduxjs/toolkit";

const initialState = {
    heroes: [],
    heroesLoadingStatus: 'idle'
}

const heroesSlice = createSlice({
    name: 'heroes',
    initialState,
    reducers: {
        heroesFetching: state => {state.heroesLoadingStatus = 'loading'},
        heroesFetched: (state, action) => {
            state.heroesLoadingStatus = 'idle';
            state.heroes = action.payload;
        },
        heroesFetchingError: state => {
            state.heroesLoadingStatus = 'error';
        },
        heroCreated: (state, action) => {
            state.heroes.push(action.payload);
        },
        heroDeleted: (state, action) => {
            state.heroes = state.heroes.filter(item => item.id !== action.payload);
        }
    }
});

const {actions, reducer} = heroesSlice;

export default reducer;
export const {
    heroesFetching,
    heroesFetched,
    heroesFetchingError,
    heroCreated,
    heroDeleted
} = actions;
```

**filtersSlice.js**

```JavaScript
import { createSlice } from "@reduxjs/toolkit";

const initialState = {
    filters: [],
    filtersLoadingStatus: 'idle',
    activeFilter: 'all'
}

const filtersSlice = createSlice({
    name: 'filters',
    initialState,
    reducers: {
        filtersFetching: state => {state.filtersLoadingStatus = 'loading'},
        filtersFetched: (state, action) => {
            state.filtersLoadingStatus = 'idle';
            state.filters = action.payload;
        },
        filtersFetchingError: state => {
            state.filtersLoadingStatus = 'error';
        },
        filtersChanged: (state, action) => {
            state.activeFilter = action.payload;
        }
    }
});

const {actions, reducer} = filtersSlice;

export default reducer;
export const {
    filtersFetching,
    filtersFetched,
    filtersFetchingError,
    filtersChanged
} = actions;
```