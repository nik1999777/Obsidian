[https://redux-toolkit.js.org/introduction/getting-started#whats-included](https://redux-toolkit.js.org/introduction/getting-started#whats-included) - что включено в Redux Toolkit

[https://github.com/reduxjs/cra-template-redux](https://github.com/reduxjs/cra-template-redux) - cra-template-redux

[https://redux-toolkit.js.org/api/configureStore](https://redux-toolkit.js.org/api/configureStore) - официальная документация configureStore

  

При создании больших приложений с использованием Redux:

- во-первых - очень много повторения кода при создании **reducer-ов** и **action creator-во**
- во-вторых - хотелось бы намного удобнее создавать **store**
- в-третьих - когда у нас будут очень вложенные структуры, которые лежат внутри **store** - то не очень приятно будет соблюдать иммутабельность и что-то менять внутри

  

Поэтому Redux выпустил пакет **Redux Toolkit**, который решает эти проблемы.

**Redux Toolkit** - это всего лишь инструмент, чтобы писать код было немного удобнее и лаконичнее.

Он ничего не вносит в логику с работой хранилищем.

  

NPM

```Plain
npm install @reduxjs/toolkit
```

Yarn

```Plain
yarn add @reduxjs/toolkit
```

Redux + Plain JS template

```Plain
npx create-react-app my-app --template redux
```

Redux + TypeScript template

```Plain
npx create-react-app my-app --template redux-typescript
```

  

Функция **СonfigureStore** предназначена она для того, чтобы:

- удобно и автоматически комбинировать **reducer-ы**
- подключать дополнительный функционал - **middleware** или **enhancer**
- и автоматически подключать **redux devtools** без с той страшной строки

  

index.js .../store

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