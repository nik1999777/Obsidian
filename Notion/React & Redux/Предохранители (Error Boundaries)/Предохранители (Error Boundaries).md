[https://ru.reactjs.org/docs/react-component.html#componentdidcatch](https://ru.reactjs.org/docs/react-component.html#componentdidcatch) - componentDidCatch()

[https://ru.reactjs.org/docs/react-component.html#static-getderivedstatefromerror](https://ru.reactjs.org/docs/react-component.html#static-getderivedstatefromerror) - getDerivedStateFromError

![[Untitled 38.png|Untitled 38.png]]

  

  

  

> [!important]  
> Предохранители - это классовые компоненты, которые оборачивают другие компоненты. И если в их дочерних компонентах происходит ошибка, то предохранители будут ее ловить. (то есть полностью приложение не падает, ломается лишь только дочерний компонент).  

В **хуках** использовать **предохранители** к сожалению пока невозможно.

Внутри **предохранителя** мы как раз используем один из **методов** **жизненного** **цикла** **componentDidCatch()**.

  

**Предохранители** ловят не все ошибки.

**Предохранители** ловят ошибки:

- при запуске метода **render()**
- в методах **жизненного** **цикла**
- и в **конструкторах** **дочерних** **компонентов**

**Предохранители** не ловят ошибки:

- не ловят ошибки, которые произошли внутри **обработчиков** **событий**. Почему так? Потому что **событие** у нас происходит вне метода **render()**
- в **асинхронном** коде (мы не знаем, когда эта операция закончится). Например **сетевые** **запросы**
- в самом **предохранители**, он ловит ошибки только в **дочерних** **элементах**, но не внутри себя

  

> [!important]  
> Вообщем предохранители помогают не дать сломаться приложению и обеспечивает максимально комфортное использование пользователем  

ErrorBoundry.js

```JavaScript
import { Component } from "react";
import ErrorMessage from "../errorMessage/ErrorMessage";

class ErrorBoundary extends Component {
    state = {
        error: false
    }

    componentDidCatch(error, errorInfo) {
        console.log(error, errorInfo);
        this.setState({
            error: true
        })
    }

    render() {
        if (this.state.error) {
            return <ErrorMessage/>
        }

        return this.props.children;
    }
}

export default ErrorBoundary;
```

App.js

```JavaScript
import { Component } from "react";
import AppHeader from "../appHeader/AppHeader";
import RandomChar from "../randomChar/RandomChar";
import CharList from "../charList/CharList";
import CharInfo from "../charInfo/CharInfo";
import ErrorBoundary from "../errorBoundary/ErrorBoundry";

import decoration from '../../resources/img/vision.png';

class App extends Component {
    state = {
        selectedChar: null
    }

    onCharSelected = (id) => {
        this.setState({
            selectedChar: id
        })
    }

    render() {
        return (
            <div className="app">
                <AppHeader/>
                <main>
                    <ErrorBoundary>
                        <RandomChar/>
                    </ErrorBoundary>
                    <div className="char__content">
                        <ErrorBoundary>
                            <CharList onCharSelected={this.onCharSelected}/>
                        </ErrorBoundary>
                        <ErrorBoundary>
                            <CharInfo charId={this.state.selectedChar}/>
                        </ErrorBoundary>
                    </div>
                    <img className="bg-decoration" src={decoration} alt="vision"/>
                </main>
            </div>
        )
    }
}

export default App;
```

Существует **метод** **getDerivedStateFromError()**. Он тоже используется в **предохранителях** на равне с **componentDidCatch()**. Но его суть в том, что он только обновляет **state**. Никаких другие операций в нем больше не должно быть.

Но есть нам необходимо сделать что-то еще, к примеру **console.log()** - то смело используем **componentDidCatch().**

```JavaScript
static getDerivedStateFromError(error) {
        return {error: true};
    }
```