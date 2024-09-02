  

Здесь мы выполним типизацию reducers и store.

  

**reducers:**

filter.ts

```TypeScript
import { CHANGE_FILTER } from '../constants';
import { Filter, FilterActionType } from '../types';

const BASE_FILTER: Filter = 'all';

const filter = (state = BASE_FILTER, { type, payload }: FilterActionType):Filter => {
  switch (type) {
    case CHANGE_FILTER:
      return payload.activeFilter;
    default:
      return state;
  }
}

export default filter;
```

tasks.ts

```TypeScript
import { ADD_TASK, REMOVE_TASK, COMPLETE_TASK } from '../constants';
import { load } from 'redux-localstorage-simple';
import { ITask, TaskActionTypes } from '../types';

type stateTasks = ITask[];

const savedTasks: any = load({ namespace: 'todo-list' });

const initialState: stateTasks = (savedTasks && savedTasks.tasks) ? savedTasks.tasks : [];

const tasks = (state = initialState, action: TaskActionTypes): stateTasks => {
  switch (action.type) {
    case ADD_TASK :
      return [
        ...state, {
          id: action.payload.id,
          text: action.payload.text,
          isCompleted: action.payload.isCompleted,
        }
      ];
    case REMOVE_TASK:
        return [...state].filter(task => task.id !== action.payload.id);
      case COMPLETE_TASK:
        return [...state].map(task => {
          if(task.id === action.payload.id) {
            task.isCompleted = !task.isCompleted;
          }
          return task;
        });
    default:
      return state;
  }
}

export default tasks;
```

index.ts

```TypeScript
import { combineReducers } from 'redux';
import tasks from './tasks';
import filters from './filters';

const rootReducer = combineReducers({ tasks, filters });

export default rootReducer;
export type RootState = ReturnType<typeof rootReducer>;
```

  

**store:**

store.ts

```TypeScript
import { createStore, compose, applyMiddleware } from 'redux';
import rootReducer from './reducers';
import { save } from 'redux-localstorage-simple'

/* eslint-disable no-underscore-dangle */
const composeEnhancers =
  process.env.NODE_ENV !== 'production' &&
  typeof window === 'object' &&
  (window as any).__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ ?
    (window as any).__REDUX_DEVTOOLS_EXTENSION_COMPOSE__({}) : compose;
/* eslint-enable */

const configureStore = (preloadedState: any) => (
  createStore(
    rootReducer,
    preloadedState,
    composeEnhancers(
      applyMiddleware(save({ namespace: 'todo-list' }))
    ),
  )
);

const store = configureStore({});

export default store;
```