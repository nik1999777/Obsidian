[https://v5.reactrouter.com/web/guides/quick-start](https://v5.reactrouter.com/web/guides/quick-start) - React Router

[https://www.npmjs.com/package/react-router-dom](https://www.npmjs.com/package/react-router-dom) - версии библиотеки React Router

[https://github.com/remix-run/react-router/releases](https://github.com/remix-run/react-router/releases) - список обновлений React Router

[https://github.com/remix-run/react-router/blob/main/docs/upgrading/v5.md#upgrade-to-react-router-v6](https://github.com/remix-run/react-router/blob/main/docs/upgrading/v5.md#upgrade-to-react-router-v6) - гайд по миграции

![[Untitled 53.png|Untitled 53.png]]

![[Untitled 1 14.png|Untitled 1 14.png]]

![[Untitled 2 10.png|Untitled 2 10.png]]

  

В классическом сайте у нас каждая отдельная страница - эта **php** или **html** файл, который отвечает за определенный адрес **url**.

> [!important]  
> В веб-приложениях страницы загружаются без перезагрузки и без перехода по ссылки. Будет просто создаваться новая часть интерфейса на место старого.  

**Маршрутизация(Routing)** - это и есть переключение между такими частями интерфейса.

  

Для маршрутизации существует библиотека **React Router**.

Уже вышла **6 версия** библиотеки, но так как она еще не стабильна и дорабатывается - мы сначала рассмотрим **версию 5.3.0**

Знать ее будет не лишним, так как она может встретиться в старом коде.

  

Устанавливаем **npm** пакет.

```Plain
npm i react-router-dom@5.3.0
```

  

Импортируем 3 сущности: **Router**, **Route** и **Switch**

- **Router** - это ключевой компонент, который оборачивает все **ссылки** и **страницы** по которым будет переходить пользователь
- **Route(маршруты)** - это компонент оборачивает наши **страницы**
- с помощью **атрибута** **path** мы указываем **url** адреса, которые будет отслеживать каждый из **Route(маршрутов)**
- **Switch** - это компонент оборачивает **Route(маршруты)** и нужен для того чтобы:

1. загружать только один нужный нам компонент

Библиотека **React Router** сравнивает строку в атрибуте **path** не строго, а по частям. Сначала загружает **<MainPage/>**,а потом дополнительно она подгружает компонент **<ComicsPage/>**. Получается **композиция** из 2 страниц. Все потому что в обоих путях **path** у нас входит **/**, который обозначает главную страницу. Чтобы такого не случалось нам и необходим компонент **Switch**.

1. комбинировать компоненты(это называется **композицией**)

Это может быть подгрузка какого-то пользователя, либо идет подгрузка какого-то товара с описанием. Поэтому придется комбинировать 2 компонента: главную страницу и пользователя или товар.

- **атрибут** **exact** - говорит, что только полное совпадение пути будет **рендорить** компонент.

App.js

```JavaScript
import { BrowserRouter as Router, Route, Switch } from "react-router-dom";

import {MainPage, ComicsPage} from '../pages/';
import AppHeader from "../appHeader/AppHeader";

const App = () => {
    return (
        <Router>
            <div className="app">
                <AppHeader/>
                <main>
                    <Switch>
                        <Route exact path="/">
                            <MainPage/>
                        </Route>
                        <Route exact path="/comics">
                            <ComicsPage/>
                        </Route>
                    </Switch>
                </main>
            </div>
        </Router>
    )
}

export default App;
```

  

- **Link** - это компонент ссылка с атрибутом to

Когда мы кликаем на ссылку **Link** - компонент **Router** замечает это действие и начинает искать подходящий **Route**.

- **NavLink** - этот компонент делает то же самое, что и **Link**. Отличие лишь в том, что у него есть возможность стилизации активной ссылки.

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
                    <li><NavLink exact activeStyle={{'color': "\#9f0013"}} to="/" href="#">Characters</NavLink></li>
                    /
                    <li><NavLink exact activeStyle={{'color': "\#9f0013"}} to="/comics" href="#">Comics</NavLink></li>
                </ul>
            </nav>
        </header>
    )
}

export default AppHeader;
```

  

Также мы разделили наш код в **App.js** на отдельные страницы.

index.js

```JavaScript
import MainPage from "./MainPage";
import ComicsPage from "./ComicsPage";

export {MainPage, ComicsPage}
```

MainPage.js

```JavaScript
import { useState } from "react";

import RandomChar from "../randomChar/RandomChar";
import CharList from "../charList/CharList";
import CharInfo from "../charInfo/CharInfo";
import ErrorBoundary from "../errorBoundary/ErrorBoundary";

import decoration from '../../resources/img/vision.png';


const MainPage = () => {

    const [selectedChar, setChar] = useState(null);

    const onCharSelected = (id) => {
        setChar(id);
    }

    return (
        <>
           <ErrorBoundary>
                <RandomChar/>
            </ErrorBoundary>
            <div className="char__content">
                <ErrorBoundary>
                    <CharList onCharSelected={onCharSelected}/>
                </ErrorBoundary>
                <ErrorBoundary>
                    <CharInfo charId={selectedChar}/>
                </ErrorBoundary>
            </div>
            <img className="bg-decoration" src={decoration} alt="vision"/>
        </>
    )
}

export default MainPage;
```

ComicsPage.js

```JavaScript
import ComicsList from "../comicsList/ComicsList";
import AppBanner from "../appBanner/AppBanner";

const ComicsPage = () => {
    return (
        <>
            <AppBanner/>
            <ComicsList/>
        </>
    )
}

export default ComicsPage;
```