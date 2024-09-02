[https://medium.com/nuances-of-programming/разбираемся-с-react-render-props-и-hoc-263f498ac841](https://medium.com/nuances-of-programming/%D1%80%D0%B0%D0%B7%D0%B1%D0%B8%D1%80%D0%B0%D0%B5%D0%BC%D1%81%D1%8F-%D1%81-react-render-props-%D0%B8-hoc-263f498ac841) - статья разбираемся с Render Props и HOC в React

[https://ru.reactjs.org/docs/higher-order-components.html](https://ru.reactjs.org/docs/higher-order-components.html) - документация компоненты высшего порядка

[[smogutlireactxukizame]] - смогут ли React-хуки заменить компоненты высшего порядка (HOC)?

![[Untitled 58.png|Untitled 58.png]]

В **JS** **функция** может возвращать другую **функцию**.

```JavaScript
const f = (a) => {
    return (b) => {
        console.log(a + b) // 3
    }
}

f(1)(2);
```

Мы помним, что **классы** - это красивая обертка для **функций - конструкторов**. Поэтому вместо **функции** - мы можем вернуть и какой-то **безымянный** **класс**.

(Также мы можем возвращать и **функциональные** компоненты)

```JavaScript
const f = (a) => {
    return class extends Component  {
        render() {
            return <h1>Hello</h1>
        }
    }
}
```

Вот на таком принципе у нас и строятся **компоненты** **высшего** **порядка** - **HOC**

  

> [!important]  
> HOC - это функции, которые принимают компонент и возвращают новый компонент, но уже с какими-то модификациями  

К примеру **React.memo** - это **компонент** **высшего** **порядка**

  

Существует 2 способа использования **HOC:**

### 1 способ

Часто в приложениях у нас будут очень похожие компоненты с небольшим отличием.

В данном коде у нас 2 компонента слайдера с почти одинаковой логикой. Их отличие лишь в том, что у них разные **функции**, которые вызываются внутри **useEffect**.

И чтобы оптимизировать код создадим **HOC** - **withSlider**

Теперь вместо того, чтобы в каждом компоненте была отдельная, но похожая логика - мы ее заключили полностью в **withSlider**

### 2 способ

С помощью **HOC** - мы можем не только выносить часть общий логики компонентов, но и добавлять к ним какую-то дополнительную логику.

В данном коде мы создали **HOC** - **withLogger**, которая будет добавлять логику.

  

Когда **HOC** не стоит создавать:

- когда нужно передавать много **props** (если кол-во **props** будет разрастаться, то смысла в таком приеме не будет)
- если подходит только один компонент под **HOC** - то нет смысла его использовать
- если вы каждый раз модифицируете **HOC**, когда подключаете новый компонент - то это тоже плохая практика (какой смысл было его создавать, если вы каждый раз его переписываете)

App.js

```JavaScript
import {useState, useEffect} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

const withSlider = (BaseComponent, getData) => {
    return (props) => {
        const [slide, setSlide] = useState(0);
        const [autoplay, setAutoplay] = useState(false);

    useEffect(() => {
        setSlide(getData());
    }, [])

    function changeSlide(i) {
        setSlide(slide => slide + i);
    }

    return <BaseComponent
            {...props}
            slide={slide} 
            autoplay={autoplay} 
            changeSlide={changeSlide} 
            setAutoplay={setAutoplay}/>
    }      
}

const getDataFromFirstFetch = () => {return 10};
const getDataFromSecondFetch = () => {return 20};

const SliderFirst = (props) => {
    return (
        <Container>
            <div className="slider w-50 m-auto">
                <img className="d-block w-100" src="https://www.planetware.com/wpimages/2020/02/france-in-pictures-beautiful-places-to-photograph-eiffel-tower.jpg" alt="slide" />
                <div className="text-center mt-5">Active slide {props.slide}</div>
                <div className="buttons mt-3">
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => props.changeSlide(-1)}>-1</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => props.changeSlide(1)}>+1</button>
                </div>
            </div>
        </Container>
    )
}

const SliderSecond = (props) => {
    return (
        <Container>
            <div className="slider w-50 m-auto">
                <img className="d-block w-100" src="https://www.planetware.com/wpimages/2020/02/france-in-pictures-beautiful-places-to-photograph-eiffel-tower.jpg" alt="slide" />
                <div className="text-center mt-5">Active slide {props.slide} <br/>{props.autoplay ? 'auto' : null} </div>
                <div className="buttons mt-3">
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => props.changeSlide(-1)}>-1</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => props.changeSlide(1)}>+1</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => props.setAutoplay(autoplay => !props.autoplay)}>toggle autoplay</button>
                </div>
            </div>
        </Container>
    )
}

const SliderWithFetch = withSlider(SliderFirst, getDataFromFirstFetch);
const SliderSecondFetch = withSlider(SliderSecond, getDataFromSecondFetch);

const withLogger = WrappedComponent => props => {
    useEffect(() => {
        console.log('first render!');
    }, []);

    return <WrappedComponent {...props} />
}

const Hello = () => {
    return (
        <h1>Hello</h1>
    )
}

const HelloWithLogging = withLogger(Hello);

function App() {
    return (
        <>
            <HelloWithLogging/>
            <SliderWithFetch/>
            <SliderSecondFetch/>
        </>
    );
}

export default App;
```