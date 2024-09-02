[https://ru.reactjs.org/docs/hooks-effect.html#explanation-why-effects-run-on-each-update](https://ru.reactjs.org/docs/hooks-effect.html#explanation-why-effects-run-on-each-update) - почему эффекты выполняются при каждом обновлении

[https://bank.gov.ua/ua/open-data/api-dev](https://bank.gov.ua/ua/open-data/api-dev) - пример API банка

[https://ru.reactjs.org/docs/hooks-effect.html](https://ru.reactjs.org/docs/hooks-effect.html) - использование хука эффекта useEffect

  

> [!important]  
> Эффектами называются операции: по загрузке данных, использовании каких-то сторонних модулей, запуск Time0ut(), логирование или изменение dom структуры.  

Раньше мы говорили, что в **конструкторе** **класса** и методе **render()** не должно быть операций по типу: **запросы на сервер**, **time0ut().** Теперь мы можем правильно говорить, что в них не должно быть **эффектов**.

![[Untitled 47.png|Untitled 47.png]]

В данном коде возникает **эффект**(изменение **dom** структуры) - в **title** изменяется значение **Slide**

Данный функционал мы создаем в **классовом** компоненте и с использованием **методов** **жизненного** **цикла**.

Как видим этот функционал вызывается 2 раза в разных состояниях нашего компонента: когда компоненты был создан - **componentDidMount** и обновлен - **componentDidUpdate** .

А как же объединить все в один **метод**?

App.js

```JavaScript
import {Component} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

class Slider extends Component {
    constructor(props) {
        super(props);
        this.state = {
            autoplay: false,
            slide: 0
        }
    }

    componentDidMount() {
        document.title = `Slide: ${this.state.slide}`;
    }

    componentDidUpdate() {
        document.title = `Slide: ${this.state.slide}`;
    }

    changeSlide = (i) => {
        this.setState(({slide}) => ({
            slide: slide + i
        }))
    }

    toggleAutoplay = () => {
        this.setState(({autoplay}) => ({
            autoplay: !autoplay
        }))
    }

    render() {
        return (
            <Container>
                <div className="slider w-50 m-auto">
                    <img className="d-block w-100" src="https://www.planetware.com/wpimages/2020/02/france-in-pictures-beautiful-places-to-photograph-eiffel-tower.jpg" alt="slide" />
                    <div className="text-center mt-5">Active slide {this.state.slide} <br/> {this.state.autoplay ? 'auto' : null}</div>
                    <div className="buttons mt-3">
                        <button 
                            className="btn btn-primary me-2"
                            onClick={() => this.changeSlide(-1)}>-1</button>
                        <button 
                            className="btn btn-primary me-2"
                            onClick={() => this.changeSlide(1)}>+1</button>
                        <button 
                            className="btn btn-primary me-2"
                            onClick={this.toggleAutoplay}>toggle autoplay</button>
                    </div>
                </div>
            </Container>
        )
    }
}

function App() {
  return (
        <Slider/>
  );
}

export default App;
```

  

Как раз объединить все это можно, используя **хук** **useEffect**.

Для начала мы его импортируем из **react**.

**useEffect**:

- данный **хук** принимает в себя **анонимную стрелочную функцию**, а в нее помещаем действие, которое нам нужно выполнить
- **функция** вызывается после того:

1. как компонент **отрендорился** на странице
2. и каждый раз, когда компонент обновляется (изменение **state** и **props**)

Получается, что мы объединили 2 **хука** **жизненного** **цикла**

**useEffect** - это то место, где мы будем вызывать все **эффекты** (запросы на сервер, изменения **dom** структуры)

  

Как **useEffect** отслеживает **внутренние** **переменные**?

Прицнип **хуков** построен на **замыкании** **функций**. **Внутренние переменные** остаются в области видимости. Поэтому **useEffect** может отслеживать ссылки на текущий **state**.

  

Есть еще один важный момент, который нужно понимать:

**Анонимная** **функция**, которая находится внутри **useEffect** - меняется при каждом **render** (то есть создается каждый раз новая **функция**).

Делается это как раз для того, чтобы не было багов с **замыканием**. И это позволяет получать актуальную **переменную** из **state**.

App.js

```JavaScript
import {useState, useEffect} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

const Slider = (props) => {

    const [slide, setSlide] = useState(0);
    const [autoplay, setAutoplay] = useState(false);

    useEffect(() => {
        document.title = `Slide: ${this.state.slide}`;
    });

    function changeSlide(i) {
        setSlide(slide => slide + i);
    }

    function toggleAutoplay() {
        setAutoplay(autoplay => !autoplay);
    }

    return (
        <Container>
            <div className="slider w-50 m-auto">
                <img className="d-block w-100" src="https://www.planetware.com/wpimages/2020/02/france-in-pictures-beautiful-places-to-photograph-eiffel-tower.jpg" alt="slide" />
                <div className="text-center mt-5">Active slide {slide} <br/>{autoplay ? 'auto' : null}</div>
                <div className="buttons mt-3">
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => changeSlide(-1)}>-1</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => changeSlide(1)}>+1</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={toggleAutoplay}>toggle autoplay</button>
                </div>
            </div>
        </Container>
    )
}

function App() {
  return (
        <Slider/>
  );
}

export default App;
```

  

У **хука** **useEffect** имеется 2 **аргумента**: 1 - это **анонимная функция**, 2 - это **массив зависимостей**

Если не одна из **зависимостей** **массива** не изменилась, то **эффект** будет пропущен.

То есть теперь компонент следит за **state** - **slide**: если он поменялся, то **функция** внутри **useEffect** будет вызвана, если не поменялся - то **функция** будет пропущена.

Этот момент очень важен при оптимизации. (особенно при работе с сервером)

```JavaScript
useEffect(() => {
        document.title = `Slide: ${this.state.slide}`;
    }, [slide]);
```

Если оставить **массив** пустым, то это будет эмуляция **хука** - **componentDidMount**. **Функция** будет вызываться только один раз при первом **рендере**.

```JavaScript
useEffect(() => {
        document.title = `Slide: ${this.state.slide}`;
    }, []);
```

  

Крайне важная особенность данного **хука** заключается в том, что мы должны помнить про те **эффекты**, которые идут как **подписка**.

(Помните, что **timeOut**, который запускался в **классовом** компоненте нам необходимо было останавливать вручную, при удалении компонента со страницы - **timeOut** не удалялся)

Подобные операции называются **подпиской** (это **timeOut**, **обработчики событий**, установленные через **API** браузера, вообщем все то что может существовать длительное время и обмениваться информацией с компонентом)

> [!important]  
> Важно правило: все подписки необходимо удалять при удаления компонента.  

В **классовом** компоненте мы это делали при помощи **хука** **componentWillUnmount()**

В **useEffect** тоже есть такое поведение и реализуется оно возвращением **callback** **функции** из него:

![[Untitled 1 10.png|Untitled 1 10.png]]

```JavaScript
import {useState, useEffect} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

const Slider = (props) => {

    const [slide, setSlide] = useState(0);
    const [autoplay, setAutoplay] = useState(false);

    function logging() {
        console.log('log');
    }

    useEffect(() => {
        document.title = `Slide: ${slide}`;

        window.addEventListener('click', logging);

        return () => {
            window.removeEventListener('click', logging);
        }

    }, [slide]);

    function changeSlide(i) {
        setSlide(slide => slide + i);
    }

    function toggleAutoplay() {
        setAutoplay(autoplay => !autoplay);
    }

    return (
        <Container>
            <div className="slider w-50 m-auto">
                <img className="d-block w-100" src="https://www.planetware.com/wpimages/2020/02/france-in-pictures-beautiful-places-to-photograph-eiffel-tower.jpg" alt="slide" />
                <div className="text-center mt-5">Active slide {slide} <br/>{autoplay ? 'auto' : null}</div>
                <div className="buttons mt-3">
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => changeSlide(-1)}>-1</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => changeSlide(1)}>+1</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={toggleAutoplay}>toggle autoplay</button>
                </div>
            </div>
        </Container>
    )
}

function App() {
    const [slider, setSlider] = useState(true);

    return(
        <>
            <button onClick={() => setSlider(false)}>Click</button>
            {slider ? <Slider/> : null}
        </>
    );
}

export default App;
```

  

> [!important]  
> Хук useEffect объединил в себе сразу 3 хука жизненного цикла: componentDidMount, componentDidUpdate и componentWillUnmount