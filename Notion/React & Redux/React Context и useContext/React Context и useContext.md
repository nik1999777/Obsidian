[https://ru.reactjs.org/docs/context.html](https://ru.reactjs.org/docs/context.html) - базовая документация контекста в React

  

**Context** в **React** используют как один из вариантов построения приложения с одним общим **состоянием**.

> [!important]  
> Context нужен для того чтобы определенные данные передавать ниже по иерархии компонентов, не используя props.  

  

В данном коде мы видим типичный путь передачи данных через **props**. Многие программисты называют его **антипаттерном** - то есть тем шаблоном, который не нужно использовать. Ведь одни и те же данные путешествуют по лестнице элементов, а это захламляет код.

```JavaScript
<Page user={user} avatarSize={avatarSize} />
// ... который рендерит ...
<PageLayout user={user} avatarSize={avatarSize} />
// ... который рендерит ...
<NavigationBar user={user} avatarSize={avatarSize} />
// ... который рендерит ...
<Link href={user.permalink}>
  <Avatar user={user} size={avatarSize} />
</Link>
```

Чтобы решить данную проблему и существует **context** в **React**.

![[Untitled 56.png|Untitled 56.png]]

![[Untitled 1 16.png|Untitled 1 16.png]]

Сначала разберем как использовать **context** в **классовых** компонентах:

- создаем **context:** в **переменную** **dataContext** помещаем команду **createContext**, которая принимает в себя как единственный **аргумент - значение по умолчанию**
- далее вытаскиваем **переменные** **Provider** и **Consumer** из **dataContext**
- **Provider** предоставляет нам данные, поэтому в компоненте **App** - мы верстку оборачиваем в **Provider**
- с помощью **property** - **value** мы какое-то значение передаем в **Provider**, которое будет распространяться по иерархии ниже (если вдруг мы забудем подставить какое-значение в **value**, то это значение будет браться из **dataContext** из **значений по умолчанию**)
- и далее мы используем **Consumer** в том компоненте, куда хотим передать значение (Тут не совсем удобно, что **Consumer** принимает в себя **функцию** для **рендера** чего-либо. А мы помним что это технология **render-props**)

  

В итоге получается - при нажатии на кнопку **Click me** в **input** и **textarea** у нас меняются данные.

Самое главное - это то, что у нас из общего компонента **App** значение было передано в **классовый** компонент **InputComponent**, которое лежит по иерархии через один. И при этом **props** мы не использовали.

App.js

```JavaScript
import {useState, Component, createContext} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

const dataContext = createContext({
    mail: "name@example.com",
    text: 'some text'
});

const {Provider, Consumer} = dataContext;

const Form = (props) => {

    return (
        <Container>
            <form className="w-50 border mt-5 p-3 m-auto">
                <div className="mb-3">
                    <label htmlFor="exampleFormControlInput1" className="form-label mt-3">Email address</label>
                    <InputComponent/>
                    </div>
                    <div className="mb-3">
                    <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                    <textarea value={props.text} className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                </div>
            </form>
        </Container>
    )
}

class InputComponent extends Component {
    rener () {
        return (
            <Consumer>
                {
                    value => {
                        return (
                            <input 
                                value={value.mail} 
                                type="email" 
                                className='form-control' 
                                placeholder="name@example.com"/>
                        )
                    }
                }
            </Consumer>
        )
    }
}

function App() {
    const [data, setData] = useState({
        mail: "second@example.com",
        text: 'another text'
    });

    return (
        <Provider value={data}>
            <Form text={data.text}/>
            <button 
                onClick={() => setData({
                    mail: "second@example.com",
                    text: 'another text'
                })}>
                Click me
            </button>
        </Provider>
    );
}

export default App;
```

Также есть другой синтаксис использования данной фичи в **классовом** компоненте. Мы к компоненту, в который мы хотим передать значение - привязываем **context**

```JavaScript
class InputComponent extends Component {
    render () {
        return (
            <input 
            value={this.context.mail} 
            type="email" 
            className='form-control' 
            placeholder="name@example.com"/>
        )
    }
}

InputComponent.contextType = dataContext;
```

Есть еще более новый синтаксис привязки через **static**

```JavaScript
class InputComponent extends Component {

    static contextType = dataContext;

    render () {
        return (
            <input 
            value={this.context.mail} 
            type="email" 
            className='form-control' 
            placeholder="name@example.com"/>
        )
    }
```

Чтобы использовать **context** в **функциональном** компоненте мы используем **хук** **useContext**. В качестве **аргумента** он принимает в себя тот **context**, на который мы подписываемся.

```JavaScript
import {useState, createContext, useContext} from 'react';

const InputComponent = () => {

    const context = useContext(dataContext);

    return (
        <input 
            value={context.mail} 
            type="email" 
            className='form-control' 
            placeholder="name@example.com"/>
    )
}
```

  

Чтобы было более наглядно увидеть как используется и работает **context** - разделим весь код на отдельные файлы: **App.js**, **context.js**, **Input.js**, **Form.js**

App.js

```JavaScript
import {useState} from 'react';
import './App.css';
import Form from './Form';
import dataContext from './context';

const {Provider} = dataContext;

function App() {
    const [data, setData] = useState({
        mail: "name@example.com",
        text: 'some text'
    });

    return (
        <Provider value={data}>
            <Form text={data.text}/>
            <button 
                onClick={() => setData({
                    mail: "second@example.com",
                    text: 'another text'
                })}>
                Click me
            </button>
        </Provider>
    );
}

export default App;
```

context.js

```JavaScript
import {createContext} from 'react';

const dataContext = createContext({
    mail: "name@example.com",
    text: 'some text'
});

export default dataContext;
```

Input.js

```JavaScript
import {useContext} from 'react';
import dataContext from './context';

const InputComponent = () => {

    const context = useContext(dataContext);

    return (
        <input 
            value={context.mail} 
            type="email" 
            className='form-control' 
            placeholder="name@example.com"/>
    )
}

export default InputComponent;
```

Form.js

```JavaScript
import {Container} from 'react-bootstrap';
import InputComponent from './Input';

const Form = (props) => {
    return (
        <Container>
            <form className="w-50 border mt-5 p-3 m-auto">
                <div className="mb-3">
                    <label htmlFor="exampleFormControlInput1" className="form-label mt-3">Email address</label>
                    <InputComponent/>
                    </div>
                    <div className="mb-3">
                    <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                    <textarea value={props.text} className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                </div>
            </form>
        </Container>
    )
}

export default Form;
```