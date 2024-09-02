[https://ru.reactjs.org/docs/handling-events.html](https://ru.reactjs.org/docs/handling-events.html) - документация про обработку событий

  

![[Untitled 20.png|Untitled 20.png]]

  

1. В **React** на элементы мы можем назначать **события.**
2. На эти **события** мы назначаем **обработчики события**, а в них передаем **методы**, которые будут вызываться при срабатывание **события**.
3. **Методы** - мы создаем

  

В **методе comitInputChanges** внутри **setState()** мы не использовали **callback - функцию**, так как для данного метода совершенно не важно, что было до этого в **state**, нам не нужна последовательность операций. (Когда мы вводим текст в **input** нам интересен только результат, только то, что находится в данном **input**).

  

> [!important]  
> this  

Почему мы используем в создании **методов** **стрелочный синтаксис**?

Все дело в **контексте вызова this**.

Когда мы передаем **метод** в **обработчик события** - мы всегда в начале прописываем **this** для указания **экземпляра класса**.

Также мы прописываем **this** для **props** и **state** - когда мы конкретно указываем, что работаем с определенным **экземпляром класса**.

**this** - указывает конкретно на один **экземпляр класса**, чтобы у каждого **компонента** были свои **свойства**.

Таким образом **this** в **state** и **props** - всегда будет ссылаться на **конкретный экземпляр**.

А вот с **обработчиками события** все сложнее - когда **событие** срабатывает **контекст вызова this** теряется.

Это происходит потому что у нас **метод(функция)** вызывается внутри другого **метода(функции)** - **render()**. И из за этого **this** становится **undefined**.

  

Существует 3 способа решить эту проблему:

- через конструкицю **bind**

App.js

```JavaScript
import { Component } from 'react';
import './App.css';

class WhoAmI extends Component {
    constructor(props) {
        super(props);
        this.state = {
            years: 27,
            text: '+++',
            position: ''
        }
        this.nextYear = this.nextYear.bind(this);
    }

    nextYear() {
        this.setState(state => ({
            years: state.years + 1
        }))
    }

    commitInputChanges = (e) => {
        this.setState({
            position: e.target.value
        })
    }

    render() {
        const {name, surname, link} = this.props;
        const {years, position} = this.props;
				
				console.log(this);
			
        return (
            <div>
                <button onClick={this.nextYear}>{this.state.text}</button>
                <h1>My name is {name}, surame - {surname}, 
                    age - {years}, 
                    position - {position}</h1>
                <a href={link}>My profile</a>
                <form>
                    <span>Введите должность</span>
                    <input type="text" onChange={this.commitInputChanges}/>
                </form>
            </div>
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

- через **стрелочную функцию**

App.js

```JavaScript
import { Component } from 'react';
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

    commitInputChanges = (e) => {
        this.setState({
            position: e.target.value
        })
    }

    render() {
        const {name, surname, link} = this.props;
        const {years, position} = this.props;
        
				console.log(this);
	
        return (
            <div>
                <button onClick={this.nextYear}>{this.state.text}</button>
                <h1>My name is {name}, surame - {surname}, 
                    age - {years}, 
                    position - {position}</h1>
                <a href={link}>My profile</a>
                <form>
                    <span>Введите должность</span>
                    <input type="text" onChange={this.commitInputChanges}/>
                </form>
            </div>
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

- вызвать **событие** через **анонимную стрелочную функцию**

За счет того, что **this** в **стрелочной функции** берет у своего родителя, как раз в него попадет ссылка на наш **экземпляр**.

Только в этом способе есть одна проблема:

Когда каждый раз будет создаваться **компонент** **WhoAmI**, то и будет создаваться **новый callback**. И проблемы начнутся, если этот **callback** куда то дальше передается по иерархии в виде **props** в другой **компонент**. А мы знаем по **алгоритму согласования**, что если у **компонента** меняется **props**, то он заставит его заново **перерисоваться** на странице. И соответственно мы потеряем немного по оптимизации.

App.js

```JavaScript
import { Component } from 'react';
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

    nextYear() {
        this.setState(state => ({
            years: state.years + 1
        }))
    }

    commitInputChanges = (e) => {
        this.setState({
            position: e.target.value
        })
    }

    render() {
        const {name, surname, link} = this.props;
        const {years, position} = this.props;

        console.log(this);

        return (
            <div>
                <button onClick={() => this.nextYear()}>{this.state.text}</button>
                <h1>My name is {name}, surame - {surname}, 
                    age - {years}, 
                    position - {position}</h1>
                <a href={link}>My profile</a>
                <form>
                    <span>Введите должность</span>
                    <input type="text" onChange={this.commitInputChanges}/>
                </form>
            </div>
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

Также в **обработчике события** мы можем использовать **аргументы**. Как раз с помощью 3 способа.

App.js

```JavaScript

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
            <div>
                <button onClick={this.nextYear}>{this.state.text}</button>
                <h1>My name is {name}, surame - {surname}, 
                    age - {years}, 
                    position - {position}</h1>
                <a href={link}>My profile</a>
                <form>
                    <span>Введите должность</span>
                    <input type="text" onChange={(e) => this.commitInputChanges(e, 'some color')}/>
                </form>
            </div>
        )
    }
}
```