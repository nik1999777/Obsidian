[https://github.com/tc39/proposals/blob/master/finished-proposals.md](https://github.com/tc39/proposals/blob/master/finished-proposals.md) - Class Fields (поля классов)

[https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Classes/Public_class_fields](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Classes/Public_class_fields) - публичные поля классов

[https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Classes/static](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Classes/static) - static

![[Untitled 32.png|Untitled 32.png]]

- первую возможность **Class** **Fields** частично мы уже использовали - это записывали **методы** в виде **стрелочной** **функции**. Делали это для того, чтобы закрепить за ними **контекст вызова**.
- вторая возможность **Class** **Fields** - это создание любых свойств без конструктора:

```JavaScript
    state = {
        name: '',
        salary: ''
    }
```

Также мы можем создавать **статичные методы и свойства** с помощью ключевого слова **static**.

> [!important]  
> Методы и свойства, которые мы можем использовать без создания класса называются статическими.  

Использование слова **static** оправдано для **методов** и **классов**, где логически отсутствует необходимость в множественных **объектах**. Классический пример - математические функции. **Объекты** класса "калькулятор" не нужны никому. Поэтому в ООП языках, как правило, класс **Math** и ему подобные - **статичны**.

```JavaScript
    static onLog = () => {
        console.log('Hey');
    }

    static logged = 'on';

EmployeesAddForm.onLog();
console.log(EmployeesAddForm.logged);
```

employees-add-form.js

```JavaScript
import { Component } from 'react';

import './employees-add-form.scss';

class EmployeesAddForm extends Component {
    
    state = {
        name: '',
        salary: ''
    }

    onValueChange = (e) => {
        this.setState({
            [e.target.name] : e.target.value
        })
    }

    onSubmit = (e) => {
        e.preventDefault();
        if (this.state.name.length < 3 || !this.state.salary) return;
        this.props.onAdd(this.state.name, this.state.salary);
        this.setState({
            name: '',
            salary: ''
        })
    }

    static onLog = () => {
        console.log('Hey');
    }

    static logged = 'on';

    render() {
        const {name, salary} = this.state;

        return (
            <div className="app-add-form">
                <h3>Добавьте нового сотрудника</h3>
                <form
                    className="add-form d-flex"
                    onSubmit = {this.onSubmit}>
                    <input type="text"
                        className="form-control new-post-label"
                        placeholder="Как его зовут?"
                        name="name"
                        value={name} 
                        onChange={this.onValueChange}/>
                    <input type="number"
                        className="form-control new-post-label"
                        placeholder="З/П в $?"
                        name="salary"
                        value={salary} 
                        onChange={this.onValueChange}/>
    
                    <button type="submit"
                            className="btn btn-outline-light">Добавить</button>
                </form>
            </div>
        )
    }
}

EmployeesAddForm.onLog();
console.log(EmployeesAddForm.logged);

export default EmployeesAddForm;
```