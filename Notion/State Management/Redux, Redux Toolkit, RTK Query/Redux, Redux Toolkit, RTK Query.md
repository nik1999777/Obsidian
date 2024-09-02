- **Redux**
    
    **Redux** — это state mananegement для JavaScript-приложений. Он помогает вам писать приложения, которые ведут себя последовательно, могут работать в разных окружениях (клиент, сервер, родные приложения) и легко тестируются. К тому же, он предоставляет отличные инструменты разработчика.
    
    **Принципы работы Redux:**
    
    1. **Единое состояние (store)**: Весь стейт вашего приложения хранится в одном дереве объектов внутри одного store.
    2. **Только для чтения**: Состояние доступно только для чтения. Единственный способ изменить состояние — это вызвать action, описывающий произошедшие изменения.
    3. **Изменения делаются с помощью чистых функций (reducers)**: Чтобы определить, как состояние должно изменяться в ответ на action, вы пишете чистые reducers.
    
    **Пример:**
    
    Допустим, у нас есть следующее приложение:
    
    > **constants:**
    
    ```JavaScript
    // constants/todos.js
    export const ADD_TODO = 'ADD_TODO';
    
    // constants/counter.js
    export const INCREMENT = 'INCREMENT';
    export const DECREMENT = 'DECREMENT';
    ```
    
    > **actions:**
    
    ```JavaScript
    // actions/todos.js
    export function addTodo(todo) {
      return { type: ADD_TODO, payload: todo };
    }
    
    // actions/counter.js
    export function increment() {
      return { type: INCREMENT };
    }
    
    export function decrement() {
      return { type: DECREMENT };
    }
    ```
    
    > **reducers:**
    
    ```JavaScript
    // reducers/todos.js
    import { ADD_TODO } from '../constants/todos';
    
    const initialTodoState = [];
    
    function todos(state = initialTodoState, action) {
      switch (action.type) {
        case ADD_TODO:
          return [...state, action.payload];
        default:
          return state;
      }
    }
    
    // reducers/counter.js
    import { INCREMENT, DECREMENT } from '../constants/counter';
    
    const initialCounterState = { count: 0 };
    
    function counter(state = initialCounterState, action) {
      switch (action.type) {
        case INCREMENT:
          return { count: state.count + 1 };
        case DECREMENT:
          return { count: state.count - 1 };
        default:
          return state;
      }
    }
    
    // reducers/index.js
    import { combineReducers } from 'redux';
    import todos from './todos';
    import counter from './counter';
    
    const rootReducer = combineReducers({
      todos,
      counter
    });
    
    export default rootReducer;
    ```
    
    > **store**:
    
    ```JavaScript
    // store/index.js
    import { createStore } from 'redux';
    import rootReducer from '../reducers';
    
    const store = createStore(rootReducer);
    
    export default store;
    ```
    
    > **использование в React**:
    
    ```JavaScript
    // CounterComponent.js
    import React from 'react';
    import { connect } from 'react-redux';
    import { increment, decrement } from '../actions/counter';
    
    function Counter({ count, increment, decrement }) {
      return (
        <div>
          <p>Счет: {count}</p>
          <button onClick={increment}>Увеличить</button>
          <button onClick={decrement}>Уменьшить</button>
        </div>
      );
    }
    
    const mapStateToProps = state => ({
      count: state.counter.count
    });
    
    const mapDispatchToProps = {
      increment,
      decrement
    };
    
    export default connect(mapStateToProps, mapDispatchToProps)(Counter);
    
    // TodoComponent.js
    import React, { useState } from 'react';
    import { connect } from 'react-redux';
    import { addTodo } from '../actions/todos';
    
    function TodoComponent({ todos, addTodo }) {
      const [todo, setTodo] = useState('');
    
      const handleAddTodo = () => {
        addTodo(todo);
        setTodo('');
      };
    
      return (
        <div>
          <input
            type="text"
            value={todo}
            onChange={(e) => setTodo(e.target.value)}
            placeholder="Введите задачу..."
          />
          <button onClick={handleAddTodo}>Добавить задачу</button>
          <ul>
            {todos.map((task, idx) => (
              <li key={idx}>{task}</li>
            ))}
          </ul>
        </div>
      );
    }
    
    const mapStateToProps = (state) => ({
      todos: state.todos
    });
    
    const mapDispatchToProps = {
      addTodo
    };
    
    export default connect(mapStateToProps, mapDispatchToProps)(TodoComponent);
    ```
    
    **CounterComponent:**  
      
    `**connect**` — это функция высшего порядка из `**react-redux**`, которая создает связь между React-компонентом и Redux store. Она "подключает" компонент к данным и действиям в store, позволяя компоненту быть "осведомленным" о текущем состоянии приложения и диспетчеризировать действия.
    
    `**mapStateToProps**` — это функция, которая берет глобальное состояние приложения (то есть state из Redux store) и возвращает объект, который будет передан в ваш компонент в качестве props. В вашем примере функция принимает `**state**` и возвращает объект с единственным свойством `**count**`. Это значит, что в вашем компоненте `**Counter**` вы можете получить доступ к `**count**` как к пропсу.
    
    `**mapDispatchToProps**` может быть объектом или функцией. Если это объект, он будет объединен с `**dispatch**`. Это упрощает отправку действий. В вашем примере это объект с двумя action creators: `**increment**` и `**decrement**`. Когда они используются в компоненте, действия автоматически диспетчеризуются в store.  
      
    **TodoComponent:**
    
    - Импортируем хук `**useState**` из `**react**`, чтобы управлять локальным состоянием (текущей задачей, которую пользователь вводит).
    - С помощью `**mapStateToProps**` получаем список задач (`**todos**`) из глобального состояния.
    - С помощью `**mapDispatchToProps**` подключаем функцию `**addTodo**` для добавления новой задачи.
    
    ```JavaScript
    // CounterComponent.js
    import React from 'react';
    import { useSelector, useDispatch } from 'react-redux';
    import { increment, decrement } from './actions';
    
    function Counter() {
      const count = useSelector(state => state.count);
      const dispatch = useDispatch();
    
      return (
        <div>
          <p>Счет: {count}</p>
          <button onClick={() => dispatch(increment())}>Увеличить</button>
          <button onClick={() => dispatch(decrement())}>Уменьшить</button>
        </div>
      );
    }
    
    export default Counter;
    
    // TodoComponent.js
    import React, { useState } from 'react';
    import { useSelector, useDispatch } from 'react-redux';
    import { addTodo } from '../actions/todos';
    
    function TodoComponent() {
      const todos = useSelector(state => state.todos);
      const dispatch = useDispatch();
      const [todo, setTodo] = useState('');
    
      const handleAddTodo = () => {
        dispatch(addTodo(todo));
        setTodo('');
      };
    
      return (
        <div>
          <input
            type="text"
            value={todo}
            onChange={(e) => setTodo(e.target.value)}
            placeholder="Введите задачу..."
          />
          <button onClick={handleAddTodo}>Добавить задачу</button>
          <ul>
            {todos.map((task, idx) => (
              <li key={idx}>{task}</li>
            ))}
          </ul>
        </div>
      );
    }
    
    export default TodoComponent;
    ```
    
    `**useSelector**``:` Этот хук позволяет вам извлекать данные из Redux store. Он аналогичен первой функции (mapStateToProps) в `**connect**`. В данном случае мы используем его, чтобы получить `**count**` из состояния.
    
    `**useDispatch**`: Этот хук дает вам доступ к функции `**dispatch**`, которую вы можете использовать для отправки действий в ваш Redux store. Это аналогично второй функции (mapDispatchToProps) в `**connect**`, но вместо того чтобы автоматически связывать действия, вы явно отправляете их с помощью `**dispatch**`.
    
    ```JavaScript
    // App.js
    import React from 'react';
    import TodoComponent from './components/TodoComponent';
    import CounterComponent from './components/CounterComponent';
    
    function App() {
      return (
        <div>
          <h1>Приложение Redux</h1>
          <CounterComponent />
          <TodoComponent />
        </div>
      );
    }
    
    export default App;
    ```
    
    > **традиционная структура Redux (Type-based structure):**
    
    ```Plain
    src/
    |-- actions/
    |   |-- todos.js
    |   |-- counter.js
    |-- reducers/
    |   |-- todos.js
    |   |-- counter.js
    |   |-- index.js
    |-- constants/
    |   |-- todos.js
    |   |-- counter.js
    |-- components/
    |   |-- TodoComponent.js
    |   |-- CounterComponent.js
    |-- store/
    |   |-- index.js
    |-- index.js
    |-- App.js
    ```
    
- **Redux Toolkit**
    
    **Redux Toolkit** представляет собой официальную утилиту для упрощения разработки приложений на Redux. Она предоставляет набор утилит, которые автоматизируют часто используемые паттерны и практики, делая код короче и типичные операции менее избыточными.
    
    **Пример:**
    
    > **createSlice**
    
    `**createSlice**` автоматически генерирует действия и редукторы, что уменьшает количество кода.
    
    ```JavaScript
    // todosSlice.js
    import { createSlice } from '@reduxjs/toolkit';
    
    const todosSlice = createSlice({
      name: 'todos',
      initialState: [],
      reducers: {
        addTodo: (state, action) => {
          state.push(action.payload);
        }
      }
    });
    
    export const { addTodo } = todosSlice.actions;
    
    export default todosSlice.reducer;
    
    // counterSlice.js
    import { createSlice } from '@reduxjs/toolkit';
    
    const counterSlice = createSlice({
      name: 'counter',
      initialState: 0,
      reducers: {
        increment: (state) => state + 1,
        decrement: (state) => state - 1
      }
    });
    
    export const { increment, decrement } = counterSlice.actions;
    
    export default counterSlice.reducer;
    ```
    
    > **configureStore**
    
    `**configureStore**` упрощает создание хранилища, автоматически добавляя middleware, такие как `**redux-thunk**` и включая Redux DevTools.
    
    ```JavaScript
    // store.js
    import { configureStore } from '@reduxjs/toolkit';
    import counterReducer from './slices/counterSlice';
    import todosReducer from './slices/todosSlice';
    
    export const store = configureStore({
      reducer: {
        counter: counterReducer,
        todos: todosReducer
      }
    });
    ```
    
    > **использование в React остается тем же самым**
    
    > **структуры Redux-Toolkit**
    
    **Type-based structure (Структруа по типу)**
    
    ```Plain
    src/
    |-- slices/
    |   |-- todosSlice.js
    |   |-- counterSlice.js
    |-- components/
    |   |-- TodosComponent.js
    |   |-- CounterComponent.js
    |-- app/
    |   |-- store.js
    |-- index.js
    |-- App.js
    ```
    
    **Feature-based structure (Структура по особенностям/функционалу):**
    
    ```Plain
    src/
    |-- features/
    |   |-- todos/
    |   |   |-- todosSlice.js
    |   |   |-- TodosComponent.js
    |   |-- counter/
    |       |-- counterSlice.js
    |       |-- CounterComponent.js
    |-- app/
    |   |-- store.js
    |-- index.js
    |-- App.js
    ```
    
- **RTK Query**
    
    **Redux Toolkit (RTK) Query** — это встроенный инструмент в Redux Toolkit, который предоставляет утилиты для упрощения выполнения запросов данных и кеширования в Redux-приложении. Он автоматически генерирует код для создания action creators, reducers и селекторов, упрощая работу с асинхронными операциями.
    
    **Принципы работы RTK Query:**
    
    1. **Автоматическое управление состоянием**: RTK Query автоматически кеширует запросы, обрабатывает повторные запросы и управляет состоянием загрузки.
    2. **Создание конечных точек API**: Вы определяете конечные точки API и взаимодействие с ними через сервисы.
    3. **Генерация action creators и reducers**: Нет необходимости писать множество action creators или reducers, RTK Query делает это за вас.
    
    **Пример:**
    
    > **api.js:  
    >   
    > **
    
    ```JavaScript
    import { createApi, fetchBaseQuery } from '@reduxjs/toolkit/query/react';
    
    export const api = createApi({
      baseQuery: fetchBaseQuery({ baseUrl: '/api' }),
      endpoints: (builder) => ({
        getTodos: builder.query({
          query: () => 'todos',
        }),
        addTodo: builder.mutation({
          query: (newTodo) => ({
            url: 'todos',
            method: 'POST',
            body: newTodo
          }),
        }),
      }),
    });
    
    export const { useGetTodosQuery, useAddTodoMutation } = api;
    ```
    
    > **store.js:**
    
    ```JavaScript
    import { configureStore } from '@reduxjs/toolkit';
    import { api } from './api';
    
    export const store = configureStore({
      reducer: {
        [api.reducerPath]: api.reducer,
      },
      middleware: (getDefaultMiddleware) =>
        getDefaultMiddleware().concat(api.middleware),
    });
    
    setupListeners(store.dispatch);
    ```
    
    > **использование в React:**
    
    ```JavaScript
    // TodoComponent.js
    import React, { useState } from 'react';
    import { useGetTodosQuery, useAddTodoMutation } from './api';
    
    function TodoComponent() {
      const [todo, setTodo] = useState('');
      const { data: todos = [], isLoading } = useGetTodosQuery();
      const [addTodo] = useAddTodoMutation();
    
      const handleAddTodo = () => {
        addTodo(todo);
        setTodo('');
      };
    
      if (isLoading) return <p>Loading...</p>;
    
      return (
        <div>
          <input
            type="text"
            value={todo}
            onChange={(e) => setTodo(e.target.value)}
            placeholder="Введите задачу..."
          />
          <button onClick={handleAddTodo}>Добавить задачу</button>
          <ul>
            {todos.map((task) => (
              <li key={task.id}>{task.title}</li>
            ))}
          </ul>
        </div>
      );
    }
    
    export default TodoComponent;
    ```
    
    ```JavaScript
    // App.js
    import React from 'react';
    import { Provider } from 'react-redux';
    import { store } from './store';
    import TodoComponent from './components/TodoComponent';
    
    function App() {
      return (
        <Provider store={store}>
          <div className="app-container">
            <h1>Todo Application with RTK Query</h1>
            <TodoComponent />
          </div>
        </Provider>
      );
    }
    
    export default App;
    ```
    
    > **Структура каталогов с RTK Query**:
    
    ```Plain
    src/
    |-- api/
    |   |-- index.js
    |-- components/
    |   |-- TodoComponent.js
    |-- store/
    |   |-- index.js
    |-- index.js
    |-- App.js
    ```