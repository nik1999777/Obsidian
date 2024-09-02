[https://ru.reactjs.org/docs/refs-and-the-dom.html](https://ru.reactjs.org/docs/refs-and-the-dom.html) - документация ref и DOM

[https://ru.reactjs.org/docs/forwarding-refs.html](https://ru.reactjs.org/docs/forwarding-refs.html) - перенапрваление рефов

  

Часто мы хотим что-то сделать с **дочерним компонентом** не перерисовывая его.

Например: поставить или снять фокус, узнать какой текст выделил пользователь и т д.

В таких случая нам можем пригодится технология **Ref**.

> [!important]  
> Ref - по простому это ссылка на элемент или компонент в DOM дереве(то есть уже в отрисованном интерфейсе на странице).  

  

В данном коде мы сделали так, что при загрузке компонента **Form** фокус сразу устанавливался на первый **input**.

Чтобы это реализовать мы используем **Ref:**

1. в **конструкторе** создадим новое свойство **this.myRef** и для того чтобы создать **ссылку** на какой-то элемент - мы используем команду **React.createRef()**
2. далее этот **Ref** (ссылку) мы присваиваем к нужному элементу **input**, используя специальный **атрибут** **ref**.
3. теперь внутри свойства **this.myRef** хранится ссылка на элемент **input** именно в **DOM** **дереве**
4. и далее мы ее используем внутри метода **componentDidMount()**. Мы скажем, что когда компонент появится на странице - мы обратимся к **this.myRef** и используем метод **focus()**. (важный нюанс: ссылка на элемент хранится в специальном свойстве **current**)

![[Untitled 43.png|Untitled 43.png]]

App.js

```JavaScript
import React, {Component} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

class Form extends Component {
    constructor(props) {
        super(props);
        this.myRef = React.createRef();
    }

    componentDidMount() {
        this.myRef.current.focus();
    }

    render() {
        return (
            <Container>
                <form className="w-50 border mt-5 p-3 m-auto">
                    <div className="mb-3">
                        <label htmlFor="exampleFormControlInput1" className="form-label">Email address</label>
                        <input ref={this.myRef} type="email" className="form-control" id="exampleFormControlInput1" placeholder="name@example.com"/>
                    </div>
                    <div className="mb-3">
                        <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                        <textarea className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                    </div>
                </form>
            </Container>
        )
    }
}

function App() {
    return (
        <Form/>
    );
}

export default App;
```

  

**Ref** мы можем вешать также и на компоненты. В таком случае свойство **current** будет получать **экземпляр** созданного компонента.

А зачем нам нужен второй вариант использования **Ref**?

Дело в том что таким образом можно вызывать **методы** самого компонента, на который повешен **Ref**.

> [!important]  
> Ref нельзя назначать на функциональные компоненты, только на классовые.  

![[Untitled 1 8.png|Untitled 1 8.png]]

App.js

```JavaScript
import React, {Component} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

class Form extends Component {
    constructor(props) {
        super(props);
        this.myRef = React.createRef();
    }

    componentDidMount() {
        this.myRef.current.doSmth();
    }

    render() {
        return (
            <Container>
                <form className="w-50 border mt-5 p-3 m-auto">
                    <div className="mb-3">
                        <label htmlFor="exampleFormControlInput1" className="form-label">Email address</label>
                        <TextInput ref={this.myRef} />
                    </div>
                    <div className="mb-3">
                        <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                        <textarea className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                    </div>
                </form>
            </Container>
        )
    }
}

class TextInput extends Component {

    doSmth = () => {
        console.log('smth')
    }

    render() {
        return( 
            <input 
            type="email" 
            className="form-control" 
            id="exampleFormControlInput1" 
            placeholder="name@example.com"/>
        )
    }
}

function App() {
    return (
        <Form/>
    );
}

export default App;
```

  

В данном коде при помощи **Ref** мы создали функционал, что при клике на второе поле ввода - фокус переводится на первое.

Мы создаем **метод** **focusFirstTI**. И он срабатывает при клике на элемент **<textarea>**.

![[Untitled 2 7.png|Untitled 2 7.png]]

App.js

```JavaScript
import React, {Component} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

class Form extends Component {
    myRef = React.createRef();

    focusFirstTI = () => {
        this.myRef.current.focus();
    }

    render() {
        return (
            <Container>
                <form className="w-50 border mt-5 p-3 m-auto">
                    <div className="mb-3">
                        <label htmlFor="exampleFormControlInput1" className="form-label">Email address</label>
                        <input 
                        ref={this.myRef}
                        type="email" 
                        className="form-control" 
                        id="exampleFormControlInput1" 
                        placeholder="name@example.com"/>
                    </div>
                    <div className="mb-3">
                        <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                        <textarea onClick={this.focusFirstTI} className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                    </div>
                </form>
            </Container>
        )
    }
}

function App() {
    return (
        <Form/>
    );
}

export default App;
```

  

И еще есть такое понятие как **callback ref**.

Это когда мы создаем **ref (ссылку)** не с помощью **React.createRef()**, а с помощью **функции**. И записываем **ref (ссылку)** на **экземпляр класса**.

Для этого создаем метод **setInputRef** и вызываем его в нужном нам месте.

Теперь когда будет создаваться **DOM структура**:

- запуститься **ref** c функцией **setInputRef**
- и далее функция возьмет тот элемент, на котором она была вызвана и запишет его в **ref** (то есть в **ссылку** внутри нашего **экземпляра** **класса**)

App.js

```JavaScript
import React, {Component} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

class Form extends Component {
    setInputRef = elem => {
        this.myRef = elem;
    }

    focusFirstTI = () => {
        if (this.myRef) {
            this.myRef.focus();
        }
    }

    render() {
        return (
            <Container>
                <form className="w-50 border mt-5 p-3 m-auto">
                    <div className="mb-3">
                        <label htmlFor="exampleFormControlInput1" className="form-label">Email address</label>
                        <input 
                        ref={this.setInputRef}
                        type="email" 
                        className="form-control" 
                        id="exampleFormControlInput1" 
                        placeholder="name@example.com"/>
                    </div>
                    <div className="mb-3">
                        <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                        <textarea onClick={this.focusFirstTI} className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                    </div>
                </form>
            </Container>
        )
    }
}

function App() {
    return (
        <Form/>
    );
}

export default App;
```

  

В данном коде при реализовали функционал добавления класса активности с помощью **ref (ссылки)** при нажатии на карточку персонажа.

![[Untitled 3 4.png|Untitled 3 4.png]]

  

CharList.js

```JavaScript
import {Component} from 'react';
import PropTypes from 'prop-types';

import Spinner from '../spinner/Spinner';
import ErrorMessage from '../errorMessage/ErrorMessage';
import MarvelService from '../../services/MarvelService';
import './charList.scss';

class CharList extends Component {

    state = {
        charList: [],
        loading: true,
        error: false,
        newItemLoading: false,
        offset: 210,
        charEnded: false
    }
    
    marvelService = new MarvelService();

    componentDidMount() {
        this.onRequest();
    }

    onRequest = (offset) => {
        this.onCharListLoading();
        this.marvelService.getAllCharacters(offset)
            .then(this.onCharListLoaded)
            .catch(this.onError)
    }

    onCharListLoading = () => {
        this.setState({
            newItemLoading: true
        })
    }

    onCharListLoaded = (newCharList) => {
        let ended = false;
        if (newCharList.length < 9) {
            ended = true;
        }

        this.setState(({offset, charList}) => ({
            charList: [...charList, ...newCharList],
            loading: false,
            newItemLoading: false,
            offset: offset + 9,
            charEnded: ended
        }))
    }

    onError = () => {
        this.setState({
            error: true,
            loading: false
        })
    }

    itemRefs = [];

    setRef = (ref) => {
        this.itemRefs.push(ref);
    }

    focusOnItem = (id) => {
        // Я реализовал вариант чуть сложнее, и с классом и с фокусом
        // Но в теории можно оставить только фокус, и его в стилях использовать вместо класса
        // На самом деле, решение с css-классом можно сделать, вынеся персонажа
        // в отдельный компонент. Но кода будет больше, появится новое состояние
        // и не факт, что мы выиграем по оптимизации за счет бОльшего кол-ва элементов

        // По возможности, не злоупотребляйте рефами, только в крайних случаях
        this.itemRefs.forEach(item => item.classList.remove('char__item_selected'));
        this.itemRefs[id].classList.add('char__item_selected');
        this.itemRefs[id].focus();
    }

    // Этот метод создан для оптимизации, 
    // чтобы не помещать такую конструкцию в метод render
    renderItems(arr) {
        const items =  arr.map((item, i) => {
            let imgStyle = {'objectFit' : 'cover'};
            if (item.thumbnail === 'http://i.annihil.us/u/prod/marvel/i/mg/b/40/image_not_available.jpg') {
                imgStyle = {'objectFit' : 'unset'};
            }
            
            return (
                <li 
                    className="char__item"
                    tabIndex={0}
                    ref={this.setRef}
                    key={item.id}
                    onClick={() => {
                        this.props.onCharSelected(item.id);
                        this.focusOnItem(i);
                    }}
                    onKeyPress={(e) => {
                        if (e.key === ' ' || e.key === "Enter") {
                            this.props.onCharSelected(item.id);
                            this.focusOnItem(i);
                        }
                    }}>
                        <img src={item.thumbnail} alt={item.name} style={imgStyle}/>
                        <div className="char__name">{item.name}</div>
                </li>
            )
        });
        // А эта конструкция вынесена для центровки спиннера/ошибки
        return (
            <ul className="char__grid">
                {items}
            </ul>
        )
    }

    render() {

        const {charList, loading, error, offset, newItemLoading, charEnded} = this.state;
        
        const items = this.renderItems(charList);

        const errorMessage = error ? <ErrorMessage/> : null;
        const spinner = loading ? <Spinner/> : null;
        const content = !(loading || error) ? items : null;

        return (
            <div className="char__list">
                {errorMessage}
                {spinner}
                {content}
                <button 
                    className="button button__main button__long"
                    disabled={newItemLoading}
                    style={{'display': charEnded ? 'none' : 'block'}}
                    onClick={() => this.onRequest(offset)}>
                    <div className="inner">load more</div>
                </button>
            </div>
        )
    }
}

CharList.propTypes = {
    onCharSelected: PropTypes.func.isRequired
}

export default CharList;

```