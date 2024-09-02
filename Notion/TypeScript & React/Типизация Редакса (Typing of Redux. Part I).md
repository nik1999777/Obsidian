  

Redux - это менеджемент состояние нашего приложения.

В философию данной библиотеки входит 3 основных правила:

- один источник истины - это глобальный store - предназначается только для чтения
- есть один путь изменения store - это слежение за actions, который описывают, что происходит
- изменения происходят через чистые функции - то есть мы не мутируем state, а возвращаем его новую копию

```Plain
yarn add redux reeact-redux @types/react-redux redux-localstorage-simple
```

Создаем файл types.ts - где будем описывать все наши типы.

Поскольку приложение небольшое - мы будем использовать один файл для типов.

На реально больших проектах - типизация разбрасывается по разным файлам.

types.ts

```TypeScript
import { ADD_TASK, REMOVE_TASK, COMPLETE_TASK, CHANGE_FILTER } from './constants';

// Store
export type Filter = string;

export interface ITask {
    id: number,
    text: string,
    isCompleted: boolean,
}

// Actions
interface IAddTaskAction {
    type: typeof ADD_TASK,
    payload: ITask,
}

interface IRemoveTaskAction {
    type: typeof REMOVE_TASK,
    payload: {
        id: number,
    }
}

interface ICompleteTaskAction {
    type: typeof COMPLETE_TASK,
    payload: {
        id: number,
    }
}

interface IChangeFilterAction {
    type: typeof CHANGE_FILTER,
    payload: {
        activeFilter: Filter,
    }
}

export type TaskActionTypes = IAddTaskAction | IRemoveTaskAction | ICompleteTaskAction;
export type FilterActionType = IChangeFilterAction;
```

Далее мы полностью типизируем actions.

actionCreator.ts

```TypeScript
import { ADD_TASK, REMOVE_TASK, COMPLETE_TASK, CHANGE_FILTER } from '../constants';
import { TaskActionTypes, FilterActionType, ITask, Filter } from '../types';

export const addTast = (task: ITask): TaskActionTypes => ({
  type: ADD_TASK,
  payload: {
    ...task
  },
});

export const removeTask = (id: number): TaskActionTypes => ({
  type: REMOVE_TASK,
  payload: {
    id,
  },  
});

export const completeTask = (id: number): TaskActionTypes => ({
  type: COMPLETE_TASK,
  payload: {
    id,
  },
});

export const changeFilter = (activeFilter: Filter): FilterActionType => ({
  type: CHANGE_FILTER,
  payload: {
    activeFilter,
  },
});
```