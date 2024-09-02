[https://github.com/remix-run/react-router/blob/main/docs/upgrading/v5.md#upgrade-to-react-router-v6](https://github.com/remix-run/react-router/blob/main/docs/upgrading/v5.md#upgrade-to-react-router-v6) - гайд по миграции

[https://github.com/remix-run/react-router/releases](https://github.com/remix-run/react-router/releases) - список обновлений React Router

[https://developer.mozilla.org/ru/docs/Web/API/History_API](https://developer.mozilla.org/ru/docs/Web/API/History_API) - History API

![[Untitled 53.png|Untitled 53.png]]

![[Untitled 1 14.png|Untitled 1 14.png]]

![[Untitled 2 10.png|Untitled 2 10.png]]

  

В данном уроке мы рассматриваем новейшую 6 версию библиотеки.

Все обновления и функции библиотеки можем посмореть в гайде по миграции.

```Plain
yarn add react-router-dom
```

  

В 6 версии библиотеки **React Router v6+**:

- все компоненты **Switch** меняем на **Routes**
- у компонента **Route** появился **prop** - **element**, в который мы помешаем компонент
- проблемы с размещением компонентов больше нет. Компоненты теперь можно размещать в любом порядке. Поэтому **exact** - удаляем, его больше не существует.

App.js

```JavaScript
import { BrowserRouter as Router, Route, Routes } from "react-router-dom";

import {MainPage, ComicsPage} from '../pages/';
import AppHeader from "../appHeader/AppHeader";

const App = () => {
    return (
        <Router>
            <div className="app">
                <AppHeader/>
                <main>
                    <Routes>
                        <Route path="/" element={<MainPage/>}/>
                        <Route path="/comics" element={<ComicsPage/>}/>
                    </Routes>
                </main>
            </div>
        </Router>
    )
}

export default App;
```

  

- в **NavLink** **exact** меняем на **end**
- **activeStyle** меняем на **style**

AppHeader.js

```JavaScript
import {Link, NavLink} from "react-router-dom";
import './appHeader.scss';

const AppHeader = () => {
    return (
        <header className="app__header">
            <h1 className="app__title">
                <Link to="/">
                    <span>Marvel</span> information portal
                </Link>
            </h1>
            <nav className="app__menu">
                <ul>
                    <li><NavLink 
                        end
                        style={({ isActive }) => ({ color: isActive ? '\#9F0013' : 'inherit' })}
                        to="/" 
                        >Characters</NavLink></li>
                    /
                    <li><NavLink 
                        end 
                        style={({ isActive }) => ({ color: isActive ? '\#9F0013' : 'inherit' })}
                        to="/comics">Comics</NavLink></li>
                </ul>
            </nav>
        </header>
    )
}

export default AppHeader;
```