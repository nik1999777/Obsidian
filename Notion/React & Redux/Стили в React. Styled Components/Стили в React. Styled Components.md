[https://styled-components.com/](https://styled-components.com/) - styled components

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#tagged_templates](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#tagged_templates) - tagged templates

  

Существует такая технология, как **CSS in JS**. То есть использование **CSS** кода прямо внутри **JS** компонентов.

Одним из представителей этой технологии - это библиотека **styled components**.

> **npm install --save styled-components**

Но у данного подхода есть минусы:

> [!important]  
> мы можем в результате получить очень много компонентов, в которых сложно будет ориентироваться  
  
> [!important]  
> мы видели в консоле, что классы наши будут создаваться рандомным набором букв и соответственно дебажить наш код будет сложно  
  
> [!important]  
> и также есть еще одна проблема, что css и js написаны в одном файле, то вместе они будут до конца, отдельно закэшировать мы их не сможем  
  
> [!important]  
> но и самый банальный минус, если мы где то ошиблись при использовании styled components, то наше приложение рухнет  

![[Untitled 30.png|Untitled 30.png]]

App.js

```JavaScript
import { Component } from 'react';
import styled from 'styled-components';

import './App.css';

const EmpItem = styled.div`
    padding: 20px;
    margin-bottom: 15px;
    border-radius: 5px;
    box-shadow: 5px 5px 10px rgba(0,0,0 .2);
    a {
        display: block;
        margin: 10px 0 10px 0;
        color: ${props => props.active ? 'orange' : 'black'};
    }
    input {
        display: block;
        margin-top: 10px;
    }
`;

const Header = styled.h2`
    font-size: 22px;
`;

export const Button = styled.button`
    display: block;
    padding: 5px 15px;
    background-color: gold;
    border: 1px solid rgba(0,0,0 .2);
    box-shadow: 5px 5px 10px rgba(0,0,0 .2);

`;

class WhoAmI extends Component {
    constructor(props) {
        super(props);
        this.state = {
            years: 27,
            text: '+++',
            position: ''
        }
    }

    nextYear = () => {
        this.setState(state => ({
            years: state.years + 1
        }))
    }

    commitInputChanges = (e, color) => {
        console.log(color);
        this.setState({
            position: e.target.value
        })
    }

    render() {
        const {name, surname, link} = this.props;
        const {years, position} = this.props;

        console.log(this);

        return (
            <EmpItem active>
                <Button onClick={this.nextYear}>{this.state.text}</Button>
                <Header>My name is {name}, surame - {surname}, 
                    age - {years}, 
                    position - {position}</Header>
                <a href={link}>My profile</a>
                <form>
                    <span>Введите должность</span>
                    <input type="text" onChange={(e) => this.commitInputChanges(e, 'some color')}/>
                </form>
            </EmpItem>
        )
    }
}

const Wrapper = styled.div`
    width: 600px;
    margin: 80px auto 0 auto;
`;

function App() {
    return (
        <Wrapper>
            <WhoAmI name="James" surname="Smith" link=""/>
            <WhoAmI name="John" surname="Jackson" link=""/>
        </Wrapper>
    );
}

export default App;
```

index.js

```JavaScript
import React, {StrictMode} from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import {Button} from './App';
import styled from 'styled-components';

const BigButton = styled(Button)`
	margin: 0 auto;
	width: 245px;
`;

ReactDOM.render(
	<StrictMode>
		<App/>
		<BigButton as="a">Отправить отчет</BigButton>
	</StrictMode>,
  document.getElementById('root')
);
```