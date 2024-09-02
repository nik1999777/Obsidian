[https://ru.reactjs.org/docs/hooks-reference.html#usereducer](https://ru.reactjs.org/docs/hooks-reference.html#usereducer) - документация хука useReducer

![[Untitled 57.png|Untitled 57.png]]

Иногда у нас бывают компоненты с довольно сложной логикой **состояния**. Такие компоненты содержат очень много **функций**

для изменения **state**.

И конечно хотелось бы объединить все эти **функции** в одну общую структуру. Этим как раз и занимается **хук** **useReducer**.

  

**Хук** **useReducer** схож с **хуком** **useState**, но предпочтительней когда у нас сложная логика **состояния** **:**

- 1 **переменная** - это **состояние**, 2 **переменная**(**dispatch**) - **функция**, которая будет менять **state**
- **хук** принимает в себя 3 **аргумента**: первый - **функцию** **reducer**, второй - начальное **состояние** и третий **аргумент** для ленивого создания начального **состояния**

  

Как же у нас все работает в данном коде?

- при срабатывании **события** клика - вызывается **функция** **dispatch**
- она принимает в себя один большой **аргумент** - это **объект**, который называется **action**.
- после запуска **функции** **dispatch** - запускается **функция** **reducer**, которая принимает в себя 2 **аргумента**: первый - текущий **state**, второй - **action**
- далее **функция** **reducer** внутри себя при помощи конструкции **switch/case** определяет какое же действие пришло

  

Также есть еще 2 момента:

- как уже упоминалась мы можем в **useReducer** передавать **функцию**(в данном коде **init**), которая будет лениво создавать начальное значение
- также мы можем расширить **объект** **action** и добавить в него новое **свойство** (в данном коде **payload**)

  

Итог:

В целом логика работы со **state** - чуть усложнилась. Но мы получаем некоторые преимущества:

- нам не нужно создавать целую кучу лишних **функций**
- **функция** **dispatch** - стабильна и не изменяется при повторных **рендерах**

App.js

```JavaScript
import {useState, useReducer} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

function reducer (state, action) {
    switch (action.type) {
        case 'toggle':
            return {autoplay: !state.autoplay};
        case 'slow':
            return {autoplay: 300};
        case 'fast':
            return {autoplay: 700};
        case 'custom':
            return {autoplay: action.payload}
        default:
            throw new Error();
    }
}
 
function init(initial) {
    return {autoplay: initial}
}

const Slider = ({initial}) => {
    const [slide, setSlide] = useState(0);
    const [autoplay, dispatch] = useReducer(reducer, initial, init);

    function changeSlide(i) {
        setSlide(slide => slide + i);
    }

    return (
        <Container>
            <div className="slider w-50 m-auto">
                <img className="d-block w-100" src="https://www.planetware.com/wpimages/2020/02/france-in-pictures-beautiful-places-to-photograph-eiffel-tower.jpg" alt="slide" />
                <div className="text-center mt-5">Active slide {slide} <br/>{autoplay.autoplay ? 'auto' : null} </div>
                <div className="buttons mt-3">
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => changeSlide(-1)}>-1</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => changeSlide(1)}>+1</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => dispatch({type: 'toggle'})}>toggle autoplay</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => dispatch({type: 'slow'})}>toggle autoplay</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => dispatch({type: 'fast'})}>toggle autoplay</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={(e) => dispatch({type: 'custom', payload: +e.target.textContent})}>1000</button>
                </div>
            </div>
        </Container>
    )
}

function App() {
    return (
        <Slider initial={false}/>
    );
}

export default App;
```