**MobX** — это библиотека управления состоянием, которая обеспечивает реактивное управление данными в JavaScript-приложениях. Она использует принципы реактивного программирования для автоматического отслеживания зависимостей и обновления данных, что делает управление состоянием более интуитивно понятным и меньше подверженным ошибкам.

**Принципы работы MobX на TypeScript:**

1. **Реактивное состояние**: MobX позволяет определить состояние приложения, которое реактивно обновляется, когда происходят изменения.
2. **Действия**: Изменения состояния в MobX должны быть выполнены через действия, что обеспечивает четкий поток данных.
3. **Вычисляемые значения**: MobX позволяет создавать вычисляемые значения, которые автоматически пересчитываются при изменении зависимых данных.
4. **Наблюдатели**: Компоненты или реакции, которые автоматически отслеживают изменения в состоянии и реагируют на них.

**Пример использования MobX с TypeScript:**

```TypeScript
// store/TodoStore.ts
import { makeAutoObservable } from 'mobx';

export class TodoStore {
  todos: string[] = [];

  constructor() {
    makeAutoObservable(this);
  }

  addTodo(todo: string): void {
    this.todos.push(todo);
  }

  get todoCount(): number {
    return this.todos.length;
  }
}

export const todoStore = new TodoStore();
```

Здесь мы определяем класс `**TodoStore**` с наблюдаемым массивом `**todos**`. Метод `**addTodo**` предназначен для добавления новых задач, а геттер `**todoCount**` возвращает количество задач.

> **components:**

```TypeScript
// components/TodoComponent.tsx
import React, { useState } from 'react';
import { observer } from 'mobx-react-lite';
import { todoStore } from '../store/TodoStore';

const TodoComponent: React.FC = observer(() => {
  const [todo, setTodo] = useState('');

  const handleAddTodo = () => {
    todoStore.addTodo(todo);
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
        {todoStore.todos.map((task, idx) => (
          <li key={idx}>{task}</li>
        ))}
      </ul>
      <p>Всего задач: {todoStore.todoCount}</p>
    </div>
  );
});

export default TodoComponent;
```

`**TodoComponent**` — это функциональный компонент, который использует хук `**useState**` для управления вводом пользователя и `**observer**` из `**mobx-react-lite**` для автоматического отслеживания изменений в `**todoStore**`.

> **использование в React:**

```TypeScript
// App.tsx
import React from 'react';
import TodoComponent from './components/TodoComponent';

const App: React.FC = () => {
  return (
    <div>
      <h1>Приложение на MobX и TypeScript</h1>
      <TodoComponent />
    </div>
  );
}

export default App;
```

**структура проекта:**

```Plain
src/
|-- store/
|   |-- TodoStore.ts
|-- components/
|   |-- TodoComponent.tsx
|-- App.tsx
|-- index.tsx
```

Это структура проекта, где `**TodoStore.ts**` содержит логику управления состоянием задач, `**TodoComponent.tsx**` — компонент для отображения и ввода задач, а `**App.tsx**` и `**index.tsx**` служат точками входа в приложение.