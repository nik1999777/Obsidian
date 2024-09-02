[https://ru.reactjs.org/docs/hooks-state.html](https://ru.reactjs.org/docs/hooks-state.html) - документация об использования хука состояния

![[Untitled 46.png|Untitled 46.png]]

В данном коде мы реализовали функционал с помощью **классового** компонента.

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

  

Теперь мы точно такой же функционал переписали в **классовый** компонент и использовали **хук** **состояния** **useState**.

**useState:**

- для того, чтобы использовать данный **хук** мы сначала должны импортировать его из **React**
- **хук** **useState()** возвращает **массив** из 2-х элементов: 1 - **state(состояние)**, 2 - **функция**, которая будет изменять **state**
- этот **массив** мы деструктуризируем на 2 **переменные**: **[slide, setSlide]**.
    
    **slide** - здесь хранится **state**, **setSlide** - а здесь **функция**, которая изменяет **state**
    
- чтобы установить какое-то начальное значение - передаем его как **аргумент** в **useState(0)** (если ничего не установить - будет **undefined**)
- чтобы изменять **state** динамически - создаем какую-то функцию (например **changeSlide()**) и внутри нее используем **функцию**, которая лежит во 2 **переменной** **setSlide**
- в ситуации, когда **state** зависит от предыдущего, то нужно будет передавать **callback** - **функцию**: **slide => slide + i**

  

В данном коде у нас 2 **state** (**состояний**): **slide** и **autoplay**. И мы создали 2 **хука** **useState()**

App.js

```JavaScript
import {Component, useState} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

const Slider = (props) => {

    const [slide, setSlide] = useState(0);
    const [autoplay, setAutoplay] = useState(false);

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

  

А можно ли сделать 2 **state** в качестве одной **переменной**, одного **хука** **useState()**?

Да, вот пример кода, как это можно сделать.

Но такой способ сложнее предыдущего:

- тут нужно работать и с **иммутабельностью**, так как у нас **объект**
- нужно продумать, как не потерять **свойства** (продумываем мы это с помощью **spread** **оператора** **...state**)

Поэтому всегда лучше разбивать **state** на отдельные **переменные**, как мы и делали в прошлый раз.

App.js

```JavaScript
import {Component, useState} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

const Slider = (props) => {

    const [state, setState] = useState({slide: 0, autoplay: false});

    function changeSlide(i) {
        setState(state => ({...state, slide: state.slide + i}));
    }

    function toggleAutoplay() {
        setState(state => ({...state, autoplay: !state.autoplay}));
    }

    return (
        <Container>
            <div className="slider w-50 m-auto">
                <img className="d-block w-100" src="https://www.planetware.com/wpimages/2020/02/france-in-pictures-beautiful-places-to-photograph-eiffel-tower.jpg" alt="slide" />
                <div className="text-center mt-5">Active slide {state.slide} <br/>{state.autoplay ? 'auto' : null}</div>
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

  

Вопрос **оптимизации**.

Наше **начальное состояние** может вычисляться в какой-то операции, например в **функции** **calcValue**.

- Если просто передать ее или передать, как **callback**, то при изменении **state** - будет вызываться только один раз.
- Если мы передадим именно **вызов функции**, то при каждом изменении **state** - будет каждый раз вызываться эта **функция** (это будет считаться уже **тяжелой функцией**, которая ударит по оптимизации)

  

> [!important]  
> Состояние в хуке useState работает точно также как и классовых компонентах. Когда у нас вызываются функции, которые мы прописываем во 2 аргументе: setSlide, setAutoplay - вызывается перендринг компонента.  

![[Untitled 1 9.png|Untitled 1 9.png]]

```JavaScript
const calcValue = () => {
    console.log('random');

    return Math.random() * (50 - 1) + 1;
}

const Slider = (props) => {

    const [slide, setSlide] = useState(calcValue);

		const [slide, setSlide] = useState(calcValue());          

		const [slide, setSlide] = useState(() => calcValue());
```

  

В данном коде мы переписали функционал счетчика с использованием **хука** **useState**.

![[Untitled 2 8.png|Untitled 2 8.png]]

```JavaScript
const App = (props) => {
  const [counter, setCounter] = React.useState(props.counter);
  
  const incCounter = () => {
    if (counter < 50) {
      setCounter(counter => counter + 1)
    }
  }
  
  const decCounter = () => {
    if (counter > -50) {
      setCounter(counter => counter - 1)
    }
  }
  
  const rndCounter = () => {
    setCounter(+(Math.random() * (50 - -50) + -50).toFixed(0))
  }
  
  const resetCounter = () => {
    setCounter(props.counter)
  }
  
  return (
    <div className="app">
      <div className="counter">{counter}</div>
      <div className="controls">
        <button onClick={incCounter}>INC</button>
        <button onClick={decCounter}>DEC</button>
        <button onClick={rndCounter}>RND</button>
        <button onClick={resetCounter}>RESET</button>
      </div>
    </div>
  )
}

ReactDOM.render(<App counter={0}/>, document.getElementById('app'));
```