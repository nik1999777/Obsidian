[https://ru.reactjs.org/docs/react-api.html#reactchildren](https://ru.reactjs.org/docs/react-api.html#reactchildren) - методы React.children

[https://ru.reactjs.org/docs/react-api.html#reactchildren](https://ru.reactjs.org/docs/react-api.html#reactchildren) - cloneElement()

  

Мы не знаем, что может быть внутри компонента **DynamicGreating**.

Такое часто бывает: в sidebar, в различных модальных окнах. Когда у нас есть оболочка модального окна, но мы не знаем что будет внутри.

И для того чтобы решить эту проблему используют свойство **props.children**.

Дословно можно сказать, что вместо **props.children** у нас появятся все те элементы или компоненты, которые мы будет передавать во внутрь компонента **DynamicGreating**.

И мы видим, что внутри компонента **DynamicGreating** отобразилось 2 заголовка **<h2>**. Как раз то, что мы передавали в вызове данного компонента.

Это очень удобный прием.В компоненте **предохранитель** как раз использовался данный прием. Ведь мы **предохранитель** использовали так, что в него можно было помещать абсолютно любой компонент.

![[Untitled 40.png|Untitled 40.png]]

App.js

```JavaScript
import { Component } from 'react';

import './App.css';

const DynamicGreating = (props) => {
    return (
        <div className={'mb-3 p-3 border border-' + props.color}>
            {props.children}
        </div>
    )
}

function App() { 
    return (
        <Wrapper>
            <DynamicGreating color={'primary'}>
                <h2>This weel was hard</h2>
                <h2>Hello world!</h2>
            </DynamicGreating>
        </Wrapper>
    );
}

export default App;
```

  

В данном коде мы не только отображаем элементы или компоненты с помощью **props.children**. Но также перебираем их с помощью команды **React.Children.map()** и модифицируем с помощью команды **React.cloneElement()**.

Мы сделали копию 2-х элементов **<h2>** и мутировали их при помощи **props-ов**: **{className: 'shadow p-3 m-3 border rounded'}**

При разработке сложных интерфейсов, когда у нас будет очень много разных компонентов - это очень удобный прием.

![[Untitled 1 7.png|Untitled 1 7.png]]

![[Untitled 2 6.png|Untitled 2 6.png]]

App.js

```JavaScript
import React, { Component } from 'react';

import './App.css';

const DynamicGreating = (props) => {
    return (
        <div className={'mb-3 p-3 border border-' + props.color}>
            {
                React.Children.map(props.children, child => {
                    return React.cloneElement(child, {className: 'shadow p-3 m-3 border rounded'})
                })
            }
        </div>
    )
}

function App() { 
    return (
        <Wrapper>
            <DynamicGreating color={'primary'}>
                <h2>This weel was hard</h2>
                <h2>Hello world!</h2>
            </DynamicGreating>
        </Wrapper>
    );
}

export default App;
```

  

В данном коде мы создали 2 компонента, которые совершенно не знают, что будет у них внутри.

Компонент **BootstrapTest**, который идет как заготовка для расположения элементов. И компонент **DynamicGreating**, который ничего не знает, что будет внутри, но уже готов модифицировать то, что в него придет.

Вместе мы их скомбинировали и получили вот такой результат.

> Не стоит забывать, что в **props** можно передавать и целые компоненты

![[Untitled 3 3.png|Untitled 3 3.png]]

App.js

```JavaScript
import React, { Component } from 'react';
import styled from 'styled-components';
import BootstrapTest from './BootstrapTest';

import './App.css';

const DynamicGreating = (props) => {
    return (
        <div className={'mb-3 p-3 border border-' + props.color}>
            {
                React.Children.map(props.children, child => {
                    return React.cloneElement(child, {className: 'shadow p-3 m-3 border rounded'})
                })
            }
        </div>
    )
}

function App() { 
    return (
        <Wrapper>
            <BootstrapTest
                left = {
                    <DynamicGreating color={'primary'}>
                        <h2>This weel was hard</h2>
                        <h2>Hello world!</h2>
                    </DynamicGreating>
                }
                right = {
                    <DynamicGreating color={'primary'}>
                        <h2>Right!</h2>
                    </DynamicGreating>
                }
            />
        </Wrapper>
    );
}

export default App;
```

BootstrapTest.js

```JavaScript
import {Container, Row, Col} from 'react-bootstrap';

const BootstrapTest = (props) => {
    return (
        <Container className="mt-5 mb-5">
            <Row>
                <Col>
                    {props.left}
                </Col>
                <Col>
                    {props.right}
                </Col>
            </Row>
        </Container>
    )
}

export default BootstrapTest;
```

  

Зачем нужны все эти возможности? Для оптимизации процесса.

У нас может-быть большое приложение с множеством компонентов, которые мы захотим оптимизировать.