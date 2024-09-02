[https://ru.reactjs.org/docs/fragments.html](https://ru.reactjs.org/docs/fragments.html) - документация про react фрагменты

  

Чтобы не оборачивать по правилам **JSX** нашу верстку в **div** (так как иногда он может сломать нашу верстку) были созданы **react** **фрагменты**, которые используются 2 способами:

1) Импортируем **Fragment** и используем его, как компонент вместо **div**

```JavaScript
import { Component, Fragment } from 'react';

import './App.css';

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
            <Fragment>
                <button onClick={this.nextYear}>{this.state.text}</button>
                <h1>My name is {name}, surame - {surname}, 
                    age - {years}, 
                    position - {position}</h1>
                <a href={link}>My profile</a>
                <form>
                    <span>Введите должность</span>
                    <input type="text" onChange={(e) => this.commitInputChanges(e, 'some color')}/>
                </form>
            </Fragment>
        )
    }
}

function App() {
    return (
        <div className="App">
            <WhoAmI name="James" surname="Smith" link=""/>
            <WhoAmI name="John" surname="Jackson" link=""/>
        </div>
    );
}

export default App;
```

2) Использование пустого **тэга** **<>**

```JavaScript
  <>
    <button onClick={this.nextYear}>{this.state.text}</button>
    <h1>My name is {name}, surame - {surname}, 
        age - {years}, 
        position - {position}</h1>
    <a href={link}>My profile</a>
    <form>
        <span>Введите должность</span>
        <input type="text" onChange={(e) => this.commitInputChanges(e, 'some color')}/>
    </form>
</>
```

В основном мы будем использовать 2 способ.

Но в редких случая, когда к **тэгу** нам нужно добавить **атрибут** **key** мы используем 1 способ. Потому что к пустому **тэгу** **атрибут** **key**, мы добавит не сможем.

```JavaScript
React.Fragment key="" 
```