  

События в React - это непросто событие в их классическом понимании.

Библиотека React использует собственную обертку - так называемый **Synthetic** **Event** над каждым событием.

Это необходимо для обеспечения лучшей кроссбраузерности.

Каждое событие оборачивается собственной имплементацией. (event implementation)

> [!important]  
> Имплементация это реализация на практике, то есть претворение в жизнь какой-либо теории, договора, закона или идеи. ... В компьютерных науках имплементация, как правило, означает выражение в программном коде какого-либо алгоритма или функции.  

А раз существует такая обертка - то для нее и были разработаны специальные **событийные** **типы**.

Полный список **типов** **событий**:

```TypeScript
- AnimationEvent
- ClipboardEvent
- DragEvent
- MouseEvent
- TouchEvent
- WheelEvent
- ChangeEvent
- CompositionEvent
- FocusEvent
- KeyboardEvent
- PointerEvent
- TransitionEvent
```

Давайте предположим, что помимо увеличения значения счетчика мы хотим получать какие-то дополнительные сведения при клике на кнопку.

Для того чтобы работать с событием в наш метод мы можем передать объект события.

И чтобы не получить ошибку - соответсвенно нам нужно определить тип события - **React.MouseEvent**.

Элемент, на котором срабатывает событие мы также можем типизировать - для этой задачи используется **Generic** - **<HTMLButtonElement | HTMLAnchorElement>**.

Насколько точно мы можем типизировать события - мало того что мы определяем **тип** самого **события**, также мы определяем и контролируем **тип** **элемента**, на котором это событие может сработать.

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
  state = {
    count: 0,
  }

  handleClick = (e: React.MouseEvent<HTMLButtonElement | HTMLAnchorElement>) => {
    console.log(`${e.clientX}, ${e.clientY}`);
    this.setState(({ count }) => ({
      count: ++count,
    }));
  }

  render() {
    return (
      <div>
        <h1>{this.props.title}{this.state.count}</h1>
        <button onClick={this.handleClick}>+1</button>
        <a href="#" onClick={this.handleClick}>Link</a>
      </div>
    );
  }
}
```

В данном коде мы определили 3 **типа** **событий**:

- **React.FocusEvent**
- **React.FormEvent**
- **React.ClipboardEvent**

А также мы типизировали элементы, на которых срабатывает событие с помощью **Generic**.

![[Untitled 85.png|Untitled 85.png]]

```TypeScript
class Form extends Component<{}, {}> {

  handleFocus = (e: React.FocusEvent<HTMLInputElement>) => {
    console.log(e.currentTarget);
  }

  handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    console.log('Submitted!');
  }

  handleCopy = (e: React.ClipboardEvent<HTMLInputElement>) => {
    console.log('Coppied!');
  }

  render() {
    return (
      <form
        onSubmit={this.handleSubmit}
      >
        <label>
          Simple text:
          <input
            onFocus={this.handleFocus}
            onCopy={this.handleCopy}
            type="text"
            name="text"
          />
          <button
            type="submit"
          >Submit</button>
        </label>
      </form>
    );
  }
}

const App:React.FC = () => <Form />;

export default App;
```