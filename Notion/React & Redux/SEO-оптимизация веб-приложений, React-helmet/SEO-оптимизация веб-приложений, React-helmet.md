[https://validator.w3.org/](https://validator.w3.org/) - валидотор w3

[https://pixelplus.ru/samostoyatelno/stati/indeksatsiya/seo-i-razrabotka-sayta.html](https://pixelplus.ru/samostoyatelno/stati/indeksatsiya/seo-i-razrabotka-sayta.html) - статья про seo в верстке

  

## SSR:

[https://nextjs.org/](https://nextjs.org/) - next js

[https://yalantis.com/blog/search-engine-optimization-for-react-apps/](https://yalantis.com/blog/search-engine-optimization-for-react-apps/) - статья про серверный рендеринг(Server Side Rendering) и как работает поисковый бот

---

**Next.js** — открытый [JavaScript](https://ru.wikipedia.org/wiki/JavaScript) [фреймворк](https://ru.wikipedia.org/wiki/%D0%A4%D1%80%D0%B5%D0%B9%D0%BC%D0%B2%D0%BE%D1%80%D0%BA), созданный поверх [React.js](https://ru.wikipedia.org/wiki/React) для создания [веб-приложений](https://ru.wikipedia.org/wiki/%D0%92%D0%B5%D0%B1-%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5), созданный компанией [Vercel](https://vercel.com/) (ранее ZEIT). Фреймворк был предназначен для решения проблемы [React.js](https://ru.wikipedia.org/wiki/React), связанную с отрисовкой приложения на стороне сервера - SSR. Работает на сервере и в [браузере](https://ru.wikipedia.org/wiki/%D0%91%D1%80%D0%B0%D1%83%D0%B7%D0%B5%D1%80).

**Server Side Rendering**

Server Side Rendering (сокращенно SSR) — принцип веб-приложений, используемый Next.js, переводится с английского языка как «Отрисовка ([Рендеринг](https://ru.wikipedia.org/wiki/%D0%A0%D0%B5%D0%BD%D0%B4%D0%B5%D1%80%D0%B8%D0%BD%D0%B3)) на стороне сервера». SSR [Рендеринг](https://ru.wikipedia.org/wiki/%D0%A0%D0%B5%D0%BD%D0%B4%D0%B5%D1%80%D0%B8%D0%BD%D0%B3) помогает снизить нагрузку на устройство, которое использует приложение (например на [сайте](https://ru.wikipedia.org/wiki/%D0%A1%D0%B0%D0%B9%D1%82) в [браузере](https://ru.wikipedia.org/wiki/%D0%91%D1%80%D0%B0%D1%83%D0%B7%D0%B5%D1%80)), ведь большинство операций производимых в приложении, относящиеся к его отображению, происходит на сервере, а не на устройстве пользователя (телефоне, планшете, компьютере и т.п.).

**SEO-оптимизация**

SSR также улучшает [SEO](https://ru.wikipedia.org/wiki/SEO), так как в обычном подходе, который использует [React](https://ru.wikipedia.org/wiki/React) (подход [SPA](https://ru.wikipedia.org/wiki/%D0%9E%D0%B4%D0%BD%D0%BE%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%87%D0%BD%D0%BE%D0%B5_%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5)), все отрисовывается на стороне клиента (устройстве пользователя [сайта](https://ru.wikipedia.org/wiki/%D0%A1%D0%B0%D0%B9%D1%82)), поэтому код страниц подгружается когда пользователь заходит на страницу, но [робот поисковых систем](https://ru.wikipedia.org/wiki/%D0%9F%D0%BE%D0%B8%D1%81%D0%BA%D0%BE%D0%B2%D1%8B%D0%B9_%D1%80%D0%BE%D0%B1%D0%BE%D1%82) может только просмотреть изначальный код страницы, ещё не обработанный [React](https://ru.wikipedia.org/wiki/React). Next.js решает эту проблему.

## Пререндеринг:

[https://github.com/stereobooster/react-snap](https://github.com/stereobooster/react-snap) - react-snap

[https://habr.com/ru/company/rshb/blog/529636/](https://habr.com/ru/company/rshb/blog/529636/) - статья про SEO-оптимизация сайта на React (почему **пререндеринг** лучше чем **SSR**)

---

  

## React Helmet :

[https://github.com/nfl/react-helmet](https://github.com/nfl/react-helmet) - react helmet

---

![[Untitled 63.png|Untitled 63.png]]

![[Untitled 1 19.png|Untitled 1 19.png]]

![[Untitled 2 13.png|Untitled 2 13.png]]

  

**Мета-теги** и **tiltle** должны быть на каждой странице в **React** - разными. Для этого существует библиотека **react helmet**

  

index.html

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="\#000000" />
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
  </body>
</html>
```

MainPage.js

```JavaScript
import { useState } from "react";
import { Helmet } from "react-helmet";

import RandomChar from "../randomChar/RandomChar";
import CharList from "../charList/CharList";
import CharInfo from "../charInfo/CharInfo";
import CharSearchForm from '../charSearchForm/CharSearchForm';
import ErrorBoundary from "../errorBoundary/ErrorBoundary";

import decoration from '../../resources/img/vision.png';

const MainPage = () => {

    const [selectedChar, setChar] = useState(null);

    const onCharSelected = (id) => {
        setChar(id);
    }

    return (
        <>
            <Helmet>
                <meta
                    name="description"
                    content="Marvel information portal"
                    />
                <title>Marvel information portal</title>
            </Helmet>
            <ErrorBoundary>
                <RandomChar/>
            </ErrorBoundary>
            <div className="char__content">
                <ErrorBoundary>
                    <CharList onCharSelected={onCharSelected}/>
                </ErrorBoundary>
                <div>
                    <ErrorBoundary>
                        <CharInfo charId={selectedChar}/>
                    </ErrorBoundary>
                    <ErrorBoundary>
                        <CharSearchForm/>
                    </ErrorBoundary>
                </div>
            </div>
            <img className="bg-decoration" src={decoration} alt="vision"/>
        </>
    )
}

export default MainPage;
```

ComicsPage.js

```JavaScript
import { Helmet } from "react-helmet";

import ComicsList from "../comicsList/ComicsList";
import AppBanner from "../appBanner/AppBanner";

const ComicsPage = () => {
    return (
        <>
            <Helmet>
                <meta
                    name="description"
                    content="Page with list of our comics"
                    />
                <title>Comics page</title>
            </Helmet>
            <AppBanner/>
            <ComicsList/>
        </>
    )
}

export default ComicsPage;
```

SingleComicLayout.js

```JavaScript
import { Link } from 'react-router-dom';
import { Helmet } from "react-helmet";

import './singleComicLayout.scss';

const SingleComicLayout = ({data}) => {

    const {title, description, pageCount, thumbnail, language, price} = data;

    return (
        <div className="single-comic">
            <Helmet>
                <meta
                    name="description"
                    content={`${title} comics book`}
                    />
                <title>{title}</title>
            </Helmet>
            <img src={thumbnail} alt={title} className="single-comic__img"/>
            <div className="single-comic__info">
                <h2 className="single-comic__name">{title}</h2>
                <p className="single-comic__descr">{description}</p>
                <p className="single-comic__descr">{pageCount}</p>
                <p className="single-comic__descr">Language: {language}</p>
                <div className="single-comic__price">{price}</div>
            </div>
            <Link to="/comics" className="single-comic__back">Back to all</Link>
        </div>
    )
}

export default SingleComicLayout;
```