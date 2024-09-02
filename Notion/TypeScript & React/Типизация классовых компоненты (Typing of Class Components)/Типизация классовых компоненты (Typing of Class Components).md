  

Синтаксис типизации **классового** **компонента** выглядет следующим образом:

Мы опять же используем **Generic type** и определяем 2 параметра:

- первый - это типизация props-ов
- второй - типизация state

Мы создали 2 простых типа CounterState и CounterProps с помощью **type** (вполне допустима использовать и **interface**), внутри которых удобно определять значения.

После чего мы просто передаем эти типы в компонент.

  

Как мы знаем классовый компонент может содержать **конструктор**.

А внутри конструктора у нас есть ключевое слово super, которое принимает props.

Соответсвенно тип этих props-ов нужно определить - для этого у нас уже есть CounterProps.

И да в этом случае props-ы типизируются 2 раза:

- в **Generic** **type** компонента
- и в конструкторе

  

Еще один нюанс - это защита от дурака.

В философии React это иммутабельность - именно поэтому если мы хотим поменять значение в state, то используем специальную функцию setState.

Но и такой кейс можно контролировать с помощью TS - для этого достаточно воспользоваться флагом **readonly**.

В новых версиях React и TS значение props и state уже определяется как readonly - следовательно дополнительная проверка не имеет смысла, но знать о ней полезно, так как legacy код еще никто не отменял.

  

Но и касаемо дефолтных значений для props-ов - мы как и раньше можем спокойно использовать свойство **defaultProps**.

  

Ну и последнее - это типизация **методов жизненного цикла**.

Разберем на примере 3:

- **getDerivedStateFromProps()** - должен вернуть объект - для обновления состояния, либо же null - чтобы ничего не обновлять.
- **componentDidMount()** - ничего не возвращает и ничего не принимает, а служит для каких-то дополнительных вычислений перед итоговым рендерингом. Соответсвенно типизируем его как **void**.
- **shouldComponentUpdate(**) - на основании внутренних вычислений определяет должен компонент обновится или нет. Он всегда будет возвращать либо true, либо false. Определяем тип возвращаемых данных, как **boolean**.

В типизации этих методов - нет ничего сложного, поскольку - это обычные функции.

И все что нам нужно сделать - это описать аргументы и возвращаемый результат.

![[Untitled 84.png|Untitled 84.png]]

```TypeScript
import React, { Component } from 'react';

type CounterState = {
  count: number,
}

type CounterProps = {
  title?: string,
}

class Counter extends Component<CounterProps, CounterState> {
  constructor(props: CounterProps) {
    super(props)

    this.state = {
      count: 0,
    }
  }

  static defaultProps: CounterProps = {
    title: "Default counter: ",
  }

  static getDerivedStateFromProps(props: CounterProps, state: CounterState): CounterState | null {
    return false ? { count: 2 } : null;
  }

  componentDidMount():void {

  }

  shouldComponentUpdate(nextProps: CounterProps, nextState: CounterState): boolean {
    return true;
  }

  handleClick = () => {
    this.setState(({ count }) => ({
      count: ++count,
    }));

    // this.state.count = ++count; <-- Never do this
  }

  render() {
    // this.props.title = ''; <-- And this...

    return (
      <div>
        <h1>{this.props.title}{this.state.count}</h1>
        <button onClick={this.handleClick}>+1</button>
      </div>
    );
  }
}

const App = () => <Counter title="Counter: " />

export default App;
```