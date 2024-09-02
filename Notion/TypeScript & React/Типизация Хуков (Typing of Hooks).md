  

**Хуки** - это новый нативный API, который был добавлен в библиотеку для того, чтобы уровнять возможности функциональных и классовых компонентов.

Также - это очень мощный инструмент для создания переиспользуемых компонентов. Фактически - эта была самая прорывная фича 2019 года.

  

**Типизация** **useState.**

Здесь есть несколько вариантов:

- если как в первом случае используется простое значение - то выполнять дополнительную типизацию не требуется.
    
    setState - эта чистая функция и она всегда будет возвращать значение того типа - который в нее передали.
    
- в случае если значение комплексное или оно может отсутствовать при инициализации - нам может понадобится TS
    
    Как вариант можно воспользоваться **Generic**, где указать типы возможных значений.
    
- третий пример - это использование **интерфейса** (можно использовать и **type**)

Вообщем и целом алгоритм точно такой же, как и при **типизации обычных функций**.

```TypeScript
import React, { Component } from 'react';

// --------- useState ---------
// Inferred as number
const [value, setValue] = useState(0);

// Explicitly setting the types
const [value, setValue] = useState<number | undefined>(undefined);
const [value, setValue] = useState<Array<number>>([]);

interface IUser {
  name: string;
  age?: number;
}
const [value, setValue] = useState<IUser>({ name: 'Yauhen' });
```

**Типизация useRef**

Здесь также возможны 2 варианта:

- первый пример типизации сделает ref - доступной только для чтения и управляемой только через React.
- второй вариант типизации сделает ref - модифицируемым и предназначенным для изменяемых экземпляров, которыми управляете уже вы.

То есть в первом случае мы отдаем управление - библиотеке, а во втором - конфигурируем самостоятельно.

```TypeScript
// --------- useRef ---------
const ref1 = useRef<HTMLElement>(null!);
const ref2 = useRef<HTMLElement | null>(null);
```

**Типизация useContext**

Точно также как и **useState** - это чистая функция, которая возвращает точно такие же типы, какие ей были переданы.

А следовательно нет необходимости **явной типизации**.

Но если все таки есть желание заморочиться - то можно типизировать как на коде ниже.

```TypeScript
// --------- useContext ---------
interface ITheme {
  backgroundColor: string;
  color: string;
}
// Context creation
const ThemeContext = createContext<ITheme>({
  backgroundColor: 'black',
  color: 'white',
})
// Accessing context in a child component
const themeContext = useContext<ITheme>(ThemeContext);
```

**Типизация useReducer**

useReducer - хук для управления глобальным состоянием приложения, за основу которого взят паттерн введенный Redux-ом.

Если коротко:

- у нас есть store - глобальное хранилище состояний.
- action - функция, которая вызывается с определенным типом действия и данными
- reducer - глобальный механизм изменения state, в основе которого лежит иммутабельность - то есть при попытке изменения сами данные не изменяются, а просто возвращается новое состояние

В примере у нас есть - **interface** для state.

**type** - для action

Для аргументов функции counterReducer - используем типы, которые уже были заданы, то есть **State** и **Action**.

В самом хуке - мы можем ничего явно не типизировать.

```TypeScript
// --------- useReducer ---------
interface State { count: number; }
type Action = { type: 'increment' | 'decrement' }
const counterReducer = ({ count }: State, { type }: Action) => {
  switch (type) {
    case 'increment': return { count: count + 1 };
    case 'decrement': return { count: count - 1 };
    default: return {};
  }
};
const [state, dispatch] = useReducer(counterReducer, { count: 0 });
dispatch({ type: 'increment' });
dispatch({ type: 'decrement' });
```

**Типизация useCallback** и **useMemo**

Эта 2 очень похожих хука, основная задача которых - это уменьшение общего кол-ва перерендеринга в компонентах.

Их функциональность заменяет метод жизненного цикла - shouldComponentUpdate().

У нас есть 2 переменные memoizedCallback и memoizedValue - их значения будут изменяться в том случае, если в хуке useCallback и useMemo будут проброшены новые переменные.

В примере результат выполнения функции sum() зависит от a и b - и просчет состоится только в том случае - если хоть одна из переменных поменяет свое значение.

Оба метода - это чистые функции, а значит возвращаемый тип зависит от переданного - явная типизация не требуется.

Но как вариант можно указать типы - передаваемых аргументов.

```TypeScript
// --------- useCallback & useMemo ---------
// Callback
// Inferred as number
const memoizedCallback = useCallback(() => { sum(a, b); }, [a, b]);
// Memo
// Inferred as (value1: number, value2: number) => number
const memoizedValue = useMemo((a: number, b: number) => sum(a, b), [a, b]);
```

**Типизация useEffect** и **useLayoutEffect**

Оба используются для **Side Effect-ов** **(Побочный эффект)** - на подобие получения данных или подписки на какие-то события.

Заменяют собой методы жизненного цикла - componentDidMount и componentWillUnmount().

И как можно догадаться - никакой дополнительной типизации не понадобится.

По факту - TS сам проверяет правильность структуры метода, который вы используете.

```TypeScript
// --------- useEffect & useLayoutEffect ---------
useEffect(() => {
  const subscriber = subscribe(options);
  return () => {
    unsubscribe(subscriber)
  };
}, [options]);
```

Как мы можете видеть в большинстве своем React хуки - практически не требуют дополнительной типизации со стороны TS.