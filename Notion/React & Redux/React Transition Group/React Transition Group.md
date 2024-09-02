[https://reactcommunity.org/react-transition-group/](https://reactcommunity.org/react-transition-group/) - документация библиотеки React Transition Group

[https://betacode.net/12167/react-transition-group-api](https://betacode.net/12167/react-transition-group-api) - статься о React Transition с иллюстрациями

[https://github.com/chenglou/react-motion](https://github.com/chenglou/react-motion) - react-motion

> [!important]  
> React Transition Group - это библиотека для создания простых анимаций в React  
  
> [!important]  
> react-motion - библиотека для создания сложных анимаций с помощью скриптов  

  

Команда для того, чтобы установить в проект **React Transition Group**

```Plain
yarn add react-transition-group
```

В библиотеке **React Transition Group** существует 4 компонента:

- [Transition](https://reactcommunity.org/react-transition-group/transition)
- [CSSTransition](https://reactcommunity.org/react-transition-group/css-transition)
- [SwitchTransition](https://reactcommunity.org/react-transition-group/switch-transition)
- [TransitionGroup](https://reactcommunity.org/react-transition-group/transition-group)

Базовые:

- **Transition** - компонент для работы с анимациями, причем он разработан так, чтобы подстраиваться под платформу и не обязательно должен работать с **css** анимациями.
- **CSSTransition** - как раз и разработан для работы с анимациями через **css** **классы**

Остальные компоненты помогают модифицировать поведение базовых:

- **SwitchTransition** - оборачивает один из базовых и устанавливает режим рендеринга
- **TransitionGroup** - оборачивает большое кол-во базовых и следит за ними. И если произойдет какое-то действие, которое приведет к удалению или добавления компонента**,** то он воспроизведет анимацию.

  

Компоненты **Transition** и **CSSTransition** принимают 2 **prop**:

- **in** - контролирует показ элемента на странице и принимает в себя **булиновые** значения: **true** или **false**
- **timeout** - это время анимации

  

Данные компоненты позволяют нам отслеживать 4 **состояния** компонента и 6 **событий** при помощи только 2 **prop**:

**6 событий:**

Когда компонент переходит из **false** в **true**

- **onEnter** - начальная инициация (когда компонент только появляется)
- **onEntering** - средняя (когда у нас идет длительная анимация)
- **onEntered** - конечная (компонент полностью показан на странице)

И обратно из **true** в **false**

- **onExit**
- **onExiting**
- **onExited**

**4 состояния:**

**false** ⇒ **true**

- **entering**
- **entered**

**true** ⇒ **false**

- **exiting**
- **exited**

![[Untitled 59.png|Untitled 59.png]]

![[Untitled 1 17.png|Untitled 1 17.png]]

В данном коде мы реализовали анимацию модального окна при помощи компонента **Transition**

App.js

```JavaScript
import {useState} from 'react';
import {Container} from 'react-bootstrap';
import { Transition } from 'react-transition-group';
import './App.css';

const Modal = (props) => {

    const duration = 300;

    const defaultStyle = {
    transition: `all ${duration}ms ease-in-out`,
    opacity: 0,
    visibility: 'hidden'
    }

    const transitionStyles = {
    entering: { opacity: 1, visibility: 'visible' },
    entered:  { opacity: 1, visibility: 'visible' },
    exiting:  { opacity: 0, visibility: 'hidden' },
    exited:  { opacity: 0,  visibility: 'hidden' },
    };

    return (
        <Transition 
            in={props.show} 
            timeout={duration} 
            onEnter={() => props.setShowTrigger(false)}
            onExited={() => props.setShowTrigger(true)}>
            {state => (
                        <div className="modal mt-5 d-block" style={{
                            ...defaultStyle,
                            ...transitionStyles[state]
                          }}>
                        <div className="modal-dialog">
                            <div className="modal-content">
                            <div className="modal-header">
                                <h5 className="modal-title">Typical modal window</h5>
                                <button onClick={() => props.onClose(false)} type="button" className="btn-close" aria-label="Close"></button>
                            </div>
                            <div className="modal-body">
                                <p>Modal body content</p>
                            </div>
                            <div className="modal-footer">
                                <button onClick={() => props.onClose(false)} type="button" className="btn btn-secondary">Close</button>
                                <button onClick={() => props.onClose(false)} type="button" className="btn btn-primary">Save changes</button>
                            </div>
                            </div>
                        </div>
                    </div>
            )}
        </Transition>
    )
}

function App() {
    const [showModal, setShowModal] = useState(false);
    const [showTrigger, setShowTrigger] = useState(true);

    return (
        <Container>
            <Modal show={showModal} onClose={setShowModal} setShowTrigger={setShowTrigger}/>
            {showTrigger ? 
            <button 
                type="button" 
                className="btn btn-warning mt-5"
                onClick={() => setShowModal(true)}>Open Modal</button> :
                null}
        </Container>
    );
}

export default App;
```

А здесь мы реализовали анимацию модального окна с помощью компонента **CSSTransition**

App.js

```JavaScript
import {useState} from 'react';
import {Container} from 'react-bootstrap';
import { CSSTransition } from 'react-transition-group';
import './App.css';

const Modal = (props) => {

    const duration = 300;

    return (
        <CSSTransition 
            in={props.show} 
            timeout={duration} 
            onEnter={() => props.setShowTrigger(false)}
            onExited={() => props.setShowTrigger(true)}
            classNames="modal"
            mountOnEnter
            unmountOnExit>
            <div className="modal mt-5 d-block">
                <div className="modal-dialog">
                    <div className="modal-content">
                    <div className="modal-header">
                        <h5 className="modal-title">Typical modal window</h5>
                        <button onClick={() => props.onClose(false)} type="button" className="btn-close" aria-label="Close"></button>
                    </div>
                    <div className="modal-body">
                        <p>Modal body content</p>
                    </div>
                    <div className="modal-footer">
                        <button onClick={() => props.onClose(false)} type="button" className="btn btn-secondary">Close</button>
                        <button onClick={() => props.onClose(false)} type="button" className="btn btn-primary">Save changes</button>
                    </div>
                    </div>
                </div>
            </div>
        </CSSTransition>
    )
}

function App() {
    const [showModal, setShowModal] = useState(false);
    const [showTrigger, setShowTrigger] = useState(true);

    return (
        <Container>
            <Modal show={showModal} onClose={setShowModal} setShowTrigger={setShowTrigger}/>
            {showTrigger ? 
            <button 
                type="button" 
                className="btn btn-warning mt-5"
                onClick={() => setShowModal(true)}>Open Modal</button> :
                null}
        </Container>
    );
}

export default App;
```

App.css

```CSS
.modal {
	opacity: 0;
	visibility: hidden;
}
.modal-enter {
	opacity: 0
}
.modal-enter-active {
	opacity: 1;
	visibility: visible;
	transition: opacity 300ms;
}
.modal-enter-done {
	opacity: 1;
	visibility: visible;
}
.modal-exit {
	opacity: 1;
}
.modal-exit-active {
	opacity: 0;
	visibility: hidden;
	transition: all opacity 300ms;
}

.App {
  text-align: center;
}

.App-logo {
  height: 40vmin;
  pointer-events: none;
}

@media (prefers-reduced-motion: no-preference) {
  .App-logo {
    animation: App-logo-spin infinite 20s linear;
  }
}

.App-header {
  background-color: \#282c34;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: calc(10px + 2vmin);
  color: white;
}

.App-link {
  color: \#61dafb;
}

@keyframes App-logo-spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
```

![[Untitled 2 11.png|Untitled 2 11.png]]

  

В данном коде с помощью **CSSTransition** реализована анимация карточек товара.

CharList.js

```JavaScript
import {useState, useEffect, useRef} from 'react';
import PropTypes from 'prop-types';
import {CSSTransition, TransitionGroup} from 'react-transition-group';

import useMarvelService from '../../services/MarvelService';
import Spinner from '../spinner/Spinner';
import ErrorMessage from '../errorMessage/ErrorMessage';

import './charList.scss';

const CharList = (props) => {

    const [charList, setCharList] = useState([]);
    const [newItemLoading, setnewItemLoading] = useState(false);
    const [offset, setOffset] = useState(210);
    const [charEnded, setCharEnded] = useState(false);
    
    const {loading, error, getAllCharacters} = useMarvelService();

    useEffect(() => {
        onRequest(offset, true);
    }, [])

    const onRequest = (offset, initial) => {
        initial ? setnewItemLoading(false) : setnewItemLoading(true);
        getAllCharacters(offset)
            .then(onCharListLoaded)
    }

    const onCharListLoaded = async(newCharList) => {
        let ended = false;
        if (newCharList.length < 9) {
            ended = true;
        }
        setCharList([...charList, ...newCharList]);
        setnewItemLoading(false);
        setOffset(offset + 9);
        setCharEnded(ended);
    }

    const itemRefs = useRef([]);

    const focusOnItem = (id) => {
        itemRefs.current.forEach(item => item.classList.remove('char__item_selected'));
        itemRefs.current[id].classList.add('char__item_selected');
        itemRefs.current[id].focus();
    }

    function renderItems (arr){
        const items =  arr.map((item, i) => {
            let imgStyle = {'objectFit' : 'cover'};
            if (item.thumbnail === 'http://i.annihil.us/u/prod/marvel/i/mg/b/40/image_not_available.jpg') {
                imgStyle = {'objectFit' : 'unset'};
            }
            
            return (
                <CSSTransition key={item.id} timeout={500} classNames="char__item">
                    <li 
                        className="char__item"
                        tabIndex={0}
                        ref={el => itemRefs.current[i] = el}
                        onClick={() => {
                            props.onCharSelected(item.id);
                            focusOnItem(i);
                        }}
                        onKeyPress={(e) => {
                            if (e.key === ' ' || e.key === "Enter") {
                                props.onCharSelected(item.id);
                                focusOnItem(i);
                            }
                        }}>
                            <img src={item.thumbnail} alt={item.name} style={imgStyle}/>
                            <div className="char__name">{item.name}</div>
                    </li>
                </CSSTransition>
            )
        });

        return (
            <ul className="char__grid">
                <TransitionGroup component={null}>
                    {items}
                </TransitionGroup>
            </ul>
        )
    }
    
    const items = renderItems(charList);

    const errorMessage = error ? <ErrorMessage/> : null;
    const spinner = loading && !newItemLoading ? <Spinner/> : null;

    return (
        <div className="char__list">
            {errorMessage}
            {spinner}
            {items}
            <button 
                disabled={newItemLoading} 
                style={{'display' : charEnded ? 'none' : 'block'}}
                className="button button__main button__long"
                onClick={() => onRequest(offset)}>
                <div className="inner">load more</div>
            </button>
        </div>
    )
}

CharList.propTypes = {
    onCharSelected: PropTypes.func.isRequired
}

export default CharList;
```

charList.scss

```Scss
@import '../../style/variables.scss';

.char {
    &__content {
        margin-top: 50px;
        display: grid;
        grid-template-columns: 650px 425px;
        column-gap: 25px;
        align-items: start;
    }
    &__grid {
        display: grid;
        grid-template-columns: repeat(3, 200px);
        column-gap: 25px;
        row-gap: 30px;
    }
    &__item {
        width: 200px;
        height: 318px;
        background-color: $dark;
        box-shadow: 5px 5px 10px rgba(0, 0, 0, .25);
        padding: 15px;
        cursor: pointer;
        transition: 0.3s transform;
        img {
            width: 200px;
            height: 200px;
            object-fit: cover;
            transform: translate(-15px, -15px);
        }
        &_selected {
            box-shadow: 0 5px 20px $main-color;
            transform: translateY(-8px);
        }
        &-enter {
            opacity: 0;
        }
        &-enter-active {
            opacity: 1;
            transition: opacity 500ms ease-in;
        }
        &-exit {
            opacity: 1;
        }
        &-exit-active {
            opacity: 0;
            transition: opacity 500ms ease-in;
        }
    }
    &__name {
        font-weight: bold;
        font-size: 22px;
        line-height: 29px;
        text-transform: uppercase;
        color: \#fff;
    } 
}
```