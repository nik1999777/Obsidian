[https://ru.reactjs.org/docs/react-api.html#reactlazy](https://ru.reactjs.org/docs/react-api.html#reactlazy) - документация React.lazy

[https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/import](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/import) - документация импортов

  

Приложение в процессе разработки становится все больше и больше. В какой-то момент можно придти к тому, что оно будет долго грузится. Поэтому для оптимизации нашего **приложения** нужно задуматься о разделении его на отдельные загружающие кусочки.

Пример:

(Допустим у нас 10 страниц. Нам же не нужно грузить оставшиеся 9 при самом первом запуске. Мы хотим это сделать только при необходимости)

В этом могут помочь - **динамические импорты**

До этого мы работали только со **статическими импортами**.

**Динамический** **импорт** используется, когда мы хотим загрузить модуль, страницу, функцию тогда, когда нам это действительно нужно, по определенному требованию.

  

Рассмотрим 3 синтаксиса использования **динамического импорта** в **нативном** **JS**:

1. В данном коде **функция** **logger**, которая находится в файле **someFunc.js** запускается в файле **App.js** при определенном **условие**. В синтаксисе мы видим, что это уже запуск **функции** - **import()**, а не просто **import**, как в **статическом**. **Динамический** **импорт** всегда возвращает **promise** с **объектом** **модуля**. И этот **promise** конечно же мы должны обработать.

someFunc.js

```JavaScript
export function logger() {
    console.log('hello world');
}
```

App.js

```JavaScript
const App = () => {
    return (
        if (loading) {
            import('./someFunc');
                .then(obj => obj.logger())
                .catch()
        }
    )
}
```

1. Если из файла нам необходимо вытащить и в нужный момент использовать 2 **функции**, то мы можем использовать **деструктуризацию**. Но в данном синтаксисе **использования** **динамического импорта** мы должны использовать **async/await**, так как операция **асинхронная**.(мы не знаем через сколько код нам отдаст результат из другого файла)

someFunc.js

```JavaScript
export function logger() {
    console.log('hello world');
}
 
export function secondLog() {
    console.log('2nd');
}
```

App.js

```JavaScript
const App = async () => {
    const {logger, secondLog} = await import('./someFunc');
    logger();
}
```

1. Если у нас экспортируется по умолчанию(**default**) - то мы должны обращаться именно к свойству **default**.

someFunc.js

```JavaScript
export default function logger() {
    console.log('hello world');
}
```

App.js

```JavaScript
const App = async () => {
    if (loading) {
        import('./someFunc');
            .then(obj => obj.default())
            .catch()
    }
}
```

  

В **React** для того чтобы использовать такую **динамическую** **подгрузку** существует **метод** **React.lazy**

Но есть один нюанс. В **нативном** **JS** мы могли обработать ошибку **динамического** **импорта** через блок **catch**.

В **React** для использования **метода** **React.lazy** мы используем компонент **Suspense**, который и будет отвечать за ошибки в импортах и отображения запасного содержимого.

В компонент - **Suspense** мы оборачиваем те **ленивые(lazy)** компоненты, которые будут подгружаться **динамически**.

**Suspense** принимает в себя обязательный атрибут **fallback**

  

Если приложение маленькое - особо можно не увлекаться данным **методом**. Но если приложение большое, то использование **ленивой** **загрузки** может сильно оптимизировать и ускорить его.

App.js

```JavaScript
import { lazy, Suspense } from "react";
import { BrowserRouter as Router, Route, Routes } from "react-router-dom";

import AppHeader from "../appHeader/AppHeader";
import Spinner from "../spinner/Spinner";

const Page404 = lazy(() => import('../pages/404'));
const SingleComicPage = lazy(() => import('../pages/SingleComicPage'));
const MainPage = lazy(() => import('../pages/MainPage'));
const ComicsPage = lazy(() => import('../pages/ComicsPage'));

const App = () => {
    return (
        <Router>
            <div className="app">
                <AppHeader/>
                <main>
                    <Suspense fallback={<Spinner/>}>
                        <Routes>
                            <Route path="/" element={<MainPage/>}/>
                            <Route path="/comics" element={<ComicsPage/>}/>
                            <Route path="/comics/:comicId" element={<SingleComicPage/>}/>
                            <Route path="*" element={<Page404/>}/>
                        </Routes>
                    </Suspense>
                </main>
            </div>
        </Router>
    )
}

export default App;
```