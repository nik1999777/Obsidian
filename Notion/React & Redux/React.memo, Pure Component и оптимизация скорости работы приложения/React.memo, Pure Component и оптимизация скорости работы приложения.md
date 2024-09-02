[https://ru.reactjs.org/docs/react-api.html#reactmemo](https://ru.reactjs.org/docs/react-api.html#reactmemo) - документация React.memo

[https://ru.reactjs.org/docs/react-component.html#shouldcomponentupdate](https://ru.reactjs.org/docs/react-component.html#shouldcomponentupdate) - shouldComponentUpdate()

[https://ru.reactjs.org/docs/optimizing-performance.html](https://ru.reactjs.org/docs/optimizing-performance.html) - оптимизация производительности

![[Untitled 55.png|Untitled 55.png]]

  

В приложении бывают компоненты, которые постоянно могут получать одинаковые значения в **props** и каждый раз бесполезно перерисовываться.

Например: в какой-то компонент приходит каждый раз один и тот же **объект** с данными персонажа.

Если мы понимаем, что у нас есть такое поведение, то нам бы хотелось его оптимизировать.

Для этого и существует метод **React.memo**

> [!important]  
> React.memo занимается тем, что сохраняет компонент, если у него не изменилось значение в props. Он позволяет избежать лишнего рендера.  

  

В данном коде при нажатии на кнопку Click me - второй **render** не вызывается. Так как значения в **props** пришли точно такие же, что и раньше.

App.js

```JavaScript
import {useState, memo} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

const Form = memo((props) => {
    console.log('render');

    return (
        <Container>
            <form className="w-50 border mt-5 p-3 m-auto">
                <div className="mb-3">
                    <label htmlFor="exampleFormControlInput1" className="form-label mt-3">Email address</label>
                    <input value={props.mail} type="email" className='form-control' id="exampleFormControlInput1" placeholder="name@example.com"/>
                    </div>
                    <div className="mb-3">
                    <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                    <textarea value={props.text} className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                </div>
            </form>
        </Container>
    )
})

function App() {
    const [data, setData] = useState({
        mail: "name@example.com",
        text: 'some text'
    });

    return (
        <>
            <Form mail={data.mail} text={data.text}/>
            <button 
                onClick={() => setData({
                    mail: "name@example.com",
                    text: 'some text'
                })}>
                Click me
            </button>
        </>
    );
}

export default App;
```

Сравнение **props-ов** в методе у нас идет **поверхностное**.

Поэтому чтобы использовать **React.memo** на **вложенных структурах:** **объектах или массивах** - мы создаем функцию **propsCompare**, которую передаем вторым **аргументом** в **memo**.

App.js

```JavaScript
import {useState, memo} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

function propsCompare(prevProps, nextProps) {
    return prevProps.mail.name === nextProps.mail.name && prevProps.text === nextProps.text;
}

const Form = memo((props) => {
    console.log('render');

    return (
        <Container>
            <form className="w-50 border mt-5 p-3 m-auto">
                <div className="mb-3">
                    <label htmlFor="exampleFormControlInput1" className="form-label mt-3">Email address</label>
                    <input value={props.mail.name} type="email" className='form-control' id="exampleFormControlInput1" placeholder="name@example.com"/>
                    </div>
                    <div className="mb-3">
                    <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                    <textarea value={props.text} className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                </div>
            </form>
        </Container>
    )
}, propsCompare)

function App() {
    const [data, setData] = useState({
        mail: {
            name: "name@example.com"
        },
        text: 'some text'
    });

    return (
        <>
            <Form mail={data.mail} text={data.text}/>
            <button 
                onClick={() => setData({
                    mail: {
                        name: "name@example.com"
                    },
                    text: 'some text'
                })}>
                Click me
            </button>
        </>
    );
}

export default App;
```

В **классовом** компоненте для реализации данной фичи - мы используем **PureComponent**.

App.js

```JavaScript
import {useState, PureComponent} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

class Form extends PureComponent {
    render() {
        console.log('render');

        return (
            <Container>
                <form className="w-50 border mt-5 p-3 m-auto">
                    <div className="mb-3">
                        <label htmlFor="exampleFormControlInput1" className="form-label mt-3">Email address</label>
                        <input value={this.props.mail} type="email" className='form-control' id="exampleFormControlInput1" placeholder="name@example.com"/>
                        </div>
                        <div className="mb-3">
                        <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                        <textarea value={this.props.text} className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                    </div>
                </form>
            </Container>
        )
    }
}

function App() {
    const [data, setData] = useState({
        mail: "name@example.com",
        text: 'some text'
    });

    return (
        <>
            <Form mail={data.mail} text={data.text}/>
            <button 
                onClick={() => setData({
                    mail: "name@example.com",
                    text: 'some text'
                })}>
                Click me
            </button>
        </>
    );
}

export default App;
```

Если в **классовом** компоненте нам нужно проверять на изменение **states** или **props** какие-то вложенные структуры - **объекты**, **массивы**. То мы используем метод **shouldComponentUpdate** и описываем его вручную.

Но нужно быть осторожным, так как это может легкго привести к багам. Вместо этого лучше использовать **PureCompoent**, который позволяет не описывать поведение **shouldComponentUpdate** вручную. Он сам его описывает автоматически.

App.js

```JavaScript
import {useState, Component} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

class Form extends Component {

    shouldComponentUpdate(nextProps) {
        if (this.props.mail.name === nextProps.mail.name) {
            return false
        } return true;
    }

    render() {
        console.log('render');

        return (
            <Container>
                <form className="w-50 border mt-5 p-3 m-auto">
                    <div className="mb-3">
                        <label htmlFor="exampleFormControlInput1" className="form-label mt-3">Email address</label>
                        <input value={this.props.mail.name} type="email" className='form-control' id="exampleFormControlInput1" placeholder="name@example.com"/>
                        </div>
                        <div className="mb-3">
                        <label htmlFor="exampleFormControlTextarea1" className="form-label">Example textarea</label>
                        <textarea value={this.props.text} className="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                    </div>
                </form>
            </Container>
        )
    }
}

function App() {
    const [data, setData] = useState({
        mail: {
            name: "name@example.com"
        },
        text: 'some text'
    });

    return (
        <>
            <Form mail={data.mail} text={data.text}/>
            <button 
                onClick={() => setData({
                    mail: {
                        name: "name@example.com"
                    },
                    text: 'some text'
                })}>
                Click me
            </button>
        </>
    );
}

export default App;
```

  

- **React.memo** используется в **функциональных** компонентах, **PureComponent** - в **классовых**
- применять такую **мемоизацию** стоит на часто **рендорящихся** компонентах, которые могут получать одинаковые **props**
- ко всем подряд компонентам применять ее не стоит, так как у данной фичи есть обратная сторона медали: если мы начнем применять ее к компонентам, которые постоянно получают разные **props**, то мы добавляем дополнительное действие и замедляем приложение

  

> [!important]  
> Важно:  

- когда мы разрабатываем приложение - всегда нужно держать в голове **принцип работы компонента**. Это позволяет избежать лишних **рендоров**, **запросов на сервер** и **утечек памяти**
- на начальном этапе, если сомневаетесь - добавляйте команду логирования в метод или компонент и смотрите как это все работает. Если обнаружили проблемные места - используйте **хуки** и приемы для оптимизации(**useMemo**, **useCallback**, **React.lazy**, **React.memo**, **PureComponent**)
- следите за **иммутабельностью** **state-ов** и за их изменениями(когда **состояние** зависит от предыдущего)