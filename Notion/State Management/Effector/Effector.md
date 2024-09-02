`**Effector**` — это эффективная и удобная библиотека для управления состоянием в JavaScript-приложениях, с поддержкой TypeScript. Библиотека основана на концепциях реактивного программирования и предлагает мощные инструменты для работы со сложным состоянием и сайд-эффектами.  
  
  
`**Patronum**` **-** Набор утилит для Effector, предоставляющий дополнительные возможности и упрощающий работу с библиотекой.

### **Основные Концепции**

1. **Store**:
    - Хранит состояние приложения.
    - Может изменяться только под воздействием `**events**` или `**effects**`.
2. **Event**:
    - Представляет собой событие, которое может быть вызвано.
    - Используется для изменения `**stores**` или запуска `**effects**`.
3. **Effect**:
    
    - Описывает асинхронные операции и сайд-эффекты.
    - Влияет на `**stores**`.
    - Может быть использован для взаимодействия с внешними API и других асинхронных операций.
    
    > **Примеры Использования:**
    
    1. Создание Store, Event и Effect
    
    ```TypeScript
    
    import { createEffect, createEvent, createStore } from 'effector';
    
    // Создание Store
    const $counter = createStore(0);
    
    // Создание Event
    const increment = createEvent();
    
    // Создание Effect
    const fetchData = createEffect(async () => {
      const response = await fetch('/data');
      const data = await response.json();
      return data;
    });
    
    // Обновление Store
    $counter.on(increment, (count) => count + 1);
    $counter.on(fetchData.doneData, (count, data) => count + data.length);
    ```
    
    2. Использование в React Компоненте
    
    ```TypeScript
    import React from 'react';
    import { useStore } from 'effector-react';
    import { $counter, increment, fetchData } from './model';
    
    const Component: React.FC = () => {
      const count = useStore($counter);
      
      return (
        <div>
          <p>{count}</p>
          <button onClick={() => increment()}>Increment</button>
          <button onClick={() => fetchData()}>Fetch Data</button>
        </div>
      );
    }
    ```
    
    ### **Дополнительные методы:**
    
    1. **Attach**:
        - Позволяет «прикрепить» эффект к стору или другому эффекту, что удобно для передачи состояния стора в качестве параметра эффекта.
    2. **Sample**:
        - Объединяет сторы, эффекты и ивенты различными способами.
        - Позволяет реагировать на изменения стора или объединять значения из разных сторов.
    3. **createGate (effector-react)**:
        - Создаёт ворота (gate), которые позволяют связывать логику Effector с жизненным циклом компонентов React.
    4. **useStore**
    
    - это хук в **effector-react** для подписки компонента на один конкретный стор. Когда стор изменяется, компонент перерендеривается с новым значением стора.
    
    1. **useUnit**
    
    - это более универсальный хук в **effector-react**, который позволяет подписаться на любые комбинации сторов, событий и эффектов. Он удобен, когда нужно работать сразу с несколькими юнитами в компоненте.
    
    > **Пример использования:**
    
    ```TypeScript
    import { createGate } from 'effector-react';
    import { attach, createEvent, sample } from 'effector';
    import { useGate, useUnit } from 'effector-react';
    import { api } from 'shared/api';
    import { createForm } from 'effector-react-form';
    import { status } from 'patronum/status';
    import { mapServerError } from 'store/utils';
    
    // Предположим, у нас есть интерфейс пользователя
    interface User {
      id: number;
      name: string;
      // ... другие поля
    }
    
    // Параметры для формы поиска пользователей
    interface SearchParams {
      searchQuery?: string; // Например, запрос поиска
    }
    
    // Создаем gate
    export const Gate = createGate();
    const clear = createEvent();
    const load = createEvent();
    
    // Эффект для загрузки пользователей
    const fetchUsersFx = attach({
      effect: api.users.fetchUsers,
      mapParams: (params: SearchParams) => params,
    });
    
    // Стор для хранения пользователей
    export const $users = createStore<User[]>([])
      .on(fetchUsersFx.doneData, (_, data) => data)
      .reset(clear);
    
    // Форма для поиска пользователей
    export const usersSearchForm = createForm<SearchParams>({
      onSubmit: fetchUsersFx,
    });
    
    // Статус загрузки пользователей
    export const $usersStatus = status({
      effect: fetchUsersFx,
    });
    
    // Сэмпл для обработки ошибок
    sample({
      source: fetchUsersFx.failData,
      fn: mapServerError,
      target: usersSearchForm.$outerErrorsInline,
    });
    
    sample({
      clock: Gate.open,
      target: load,
    });
    
    sample({
      clock: Gate.close,
      target: clear,
    });
    
    sample({
      clock: load,
      target: fetchUsersFx,
    });
    
    // Компонент списка пользователей
    const UsersList: FC = () => {
      useGate(Gate);
      const users = useUnit($users);
      const usersStatus = useUnit($usersStatus);
      const { controller, handleSubmit } = useForm({
        form: usersSearchForm,
      });
    
      return (
        <div>
          <h1>Список пользователей</h1>
          {/* Форма поиска */}
          <form onSubmit={handleSubmit}>
            {/* Предположим, что Input - это компонент для ввода текста */}
            <Input controller={controller({ name: 'searchQuery' })} />
            <button type="submit">Поиск</button>
          </form>
          {/* Статус загрузки */}
          {usersStatus === 'pending' && <div>Loading...</div>}
          {/* Список пользователей */}
          <ul>
            {users.map(user => (
              <li key={user.id}>{user.name}</li>
            ))}
          </ul>
        </div>
      );
    };
    
    export default UsersList;
    ```
    
    > **Структура каталогов с Effector**:
    
    ```Plain
    src/
    |-- features/
    |   |-- auth/
    |   |   |-- store/
    |   |   |   |-- index.js
    |   |   |-- ui/
    |   |   |   |-- login-form.js
    |   |-- dashboard/
    |   |   |-- store/
    |   |   |   |-- index.js
    |   |   |-- ui/
    |   |   |   |-- dashboard.js
    |   |-- offline-work/
    |   |   |-- store/
    |   |   |   |-- confirm-offline-work.js
    |   |   |   |-- create-offline-work.js
    |   |   |   |-- offline-work.js
    |   |   |-- ui/
    |   |   |   |-- input/
    |   |   |   |   |-- comment-input.js
    |   |   |   |   |-- date-range-input.js
    |   |   |   |   |-- project-input.js
    |   |   |   |   |-- projects-input.js
    |   |   |   |   |-- spent-time-input.js
    |   |   |   |   |-- task-id-input.js
    |   |   |   |   |-- work-type-input.js
    |   |   |   |-- confirm-offline-work.js
    |   |   |   |-- create-offline-work.js
    |   |   |   |-- offline-work.js
    |-- shared/
    |   |-- api/
    |   |   |-- index.js
    |   |-- hooks/
    |   |   |-- use-store.js
    |   |-- utils/
    |   |   |-- index.js
    |-- store/
    |   |-- index.js
    |-- ui/
    |   |-- common/
    |   |   |-- header.js
    |   |   |-- footer.js
    |-- assets/
    |   |-- styles/
    |   |   |-- main.css
    |-- pages/
    |   |-- home-page.js
    |   |-- about-page.js
    |-- app.js
    |-- index.js
    ```