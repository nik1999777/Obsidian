[https://ru.reactjs.org/docs/hooks-reference.html#useref](https://ru.reactjs.org/docs/hooks-reference.html#useref) - документация useRef

![[Untitled 50.png|Untitled 50.png]]

Мы помним, что **рефы** - это **ссылки** на элементы именно в **DOM** **дереве**. Работают они именно в **классовых** компонентах и могут быть назначены на элементы или другие **классовые** компоненты. (в **функциональных** компонентах **ref** не работает)

  

В данном коде мы выполняем точно такой же функционал с использованием **ref**, как и в **классовом** - при клике на **textarea** фокус переводится на первый **input**.

Но для того, чтобы создать **ref** в **функциональном** компоненте - мы должны использовать **хук** **useRef**.

Как начальное значение нашего **ref** стоит поместить **null**.

**useRef**:

- данный **хук** будет создавать **объект**
- у **объекта** есть свойство **current**
- в это **свойство** как начальное значение мы помещаем **null**
- и потом уже при **рендеринги** верстки в **current** мы записываем **ссылку** на **DOM** элемент, которому мы назначили атрибут **ref**

**Ref** - по факту **объект**

App.js

```JavaScript
import {useRef} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

const Form = () => {
    const myRef = useRef(null)

    const focusFirstTI = () => {
        myRef.current.focus();
    }

    return (
        <Container>
            <form className="w-50 border mt-5 p-3 m-auto">
                <div className="mb-3">
                    <label htmlFor="exampleFormControlInput1" className="form-label">Email address</label>
                    <input ref={myRef} type="email" className="form-control" id="exampleFormControlInput1" placeholder="name@example.com"/>
                    </div>
                    <div className="mb-3">
                    <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                    <textarea onClick={focusFirstTI} className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                </div>
            </form>
        </Container>
    )
}

function App() {
    return (
        <Form/>
    );
}

export default App;
```

![[Untitled 1 11.png|Untitled 1 11.png]]

![[Untitled 2 9.png|Untitled 2 9.png]]

Помимо создания **ссылок** - **useRef** можно использовать и для другого.

**Ref** сохраняется при любом **перерендоринге** компонента, при этом изменение **ref** тоже не вызывает **перерендер**.

Поэтому в **useRef** мы можем сохранять и изменять какие-то данные в свойстве **current** в течении жизни всего компонента, без его **перерендера**.

  

Примеры использования:

- мы можем посчитать кол-во **ререндеров** компонента (если бы мы попробовали это сделать с **useState** - то мы бы попали в бесконечный цикл. Потому что изменение компонента → вызывает изменение **state** → изменение компонента)

```JavaScript
    useEffect(() => {
				myRef.curent++;
        myRef.current = text;
    })
```

- мы можем сохранять предыдущее **состояние** (к примеру, если нам приходят какие-то сотрудники от **сервера** - мы в текущее **состояние** записываем их кол-во, но при этом хотим сохранить кол-во сотрудников, которые были до **запроса** на **сервер**)

App.js

```JavaScript
import {useRef, useState, useEffect} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

const Form = () => {

    const [text, setText] = useState('');

    const myRef = useRef(1);

    useEffect(() => {
        myRef.current = text;
    })

    return (
        <Container>
            <form className="w-50 border mt-5 p-3 m-auto">
                <div className="mb-3">
                    <label htmlFor="exampleFormControlInput1" className="form-label">Email address</label>
                    <input onChange={(e) => setText(e.target.value)} type="email" className="form-control" id="exampleFormControlInput1" placeholder="name@example.com"/>
                    </div>
                    <div className="mb-3">
                    <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                    <textarea value={myRef.current} className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                </div>
            </form>
        </Container>
    )
}

function App() {
    return (
        <Form/>
    );
}

export default App;
```