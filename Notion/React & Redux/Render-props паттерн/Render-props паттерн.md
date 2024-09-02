[https://ru.reactjs.org/docs/render-props.html](https://ru.reactjs.org/docs/render-props.html) - документация про render props

  

![[Untitled 42.png|Untitled 42.png]]

  

Как сделать так, чтобы 2 отдельных компонента **Message** и **Counter** не зависели друг от друга и мы не теряли их гибкость? При том, что эти компоненты были связаны между собой - один компонент работал внутри другого.

Чтобы решить данную задачу мы применили технологию **render-props:**

1. мы взяли компонент **Counter** и во время вызова передали ему **prop** - **render**, который внутри себя содержит **callback** **функцию**.
2. **callback** **функция** принимает в себя аргумент и возвращает другой компонент **Message**
3. и далее внутри компонента **Counter** в нужном нам месте вызвали эту **callback** функцию - **this.props.render()**
4. при этом чтобы связать наше **состояние** с компонентом **Message** мы передали **аргумент** - **this.state.counter**

В данной технологии мы спокойно можем передавать несколько **props** в виде функций и спокойно делать несколько **вызовов** этих **функций**.

  

Где же применятся технология **render-props**?

К примеру у нас есть компонент, который будет вызываться 3 раза и каждый раз содержать в себе какие-то другие блоки.

В целом компонент будет шаблоном страницы, которая будет содержать разный контент. Вот для такой ситуации отлично подойдет **render-props**. Когда мы через функцию можем рендерить разные компоненты и получать разный контент.

Причем если в **props.children** мы передавали только содержимое: элементы и компоненты. То в **render-props** мы передаем именно **функцию**.

> [!important]  
> Если мы понимаем, что наш компонент не будет знать, что будет в нем находится, то можно использовать одну из технологий: props.children или render-props  

App.js

```JavaScript
import { Component } from 'react';
import styled from 'styled-components';

import './App.css';

const Message = (props) => {
    return (
        <h2>The counter is {props.counter}</h2>
    )
}

class Counter extends Component {
    state = {
        counter: 0
    }

    changeCounter = () => {
        this.setState(({counter}) => ({
            counter: counter + 1
        }))
    }

    render() {
        return (
            <>
                <button
                    className={'btn btn-primary'}
                    onClick={this.changeCounter}>
                    Click me
                </button>
                {this.props.render(this.state.counter)}
            </>
        )
    }
}

function App() { 
    return (
        <Wrapper>
            <Counter render={counter => (
                <Message counter={counter}/>
            )}/>
        </Wrapper>
    );
}

export default App;
```