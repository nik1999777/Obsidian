[https://react-redux.js.org/api/hooks](https://react-redux.js.org/api/hooks) - документация про соединение react и redux с помощью хуков

[https://vadim-budarin.medium.com/react-понятно-о-zombie-children-and-stale-props-d31247ea08](https://vadim-budarin.medium.com/react-%D0%BF%D0%BE%D0%BD%D1%8F%D1%82%D0%BD%D0%BE-%D0%BE-zombie-children-and-stale-props-d31247ea08) - статья про zombie children

![[Untitled 66.png|Untitled 66.png]]

Хуки:

- `useSelector()` - приблизительно эквивалентен **mapStateToProps**. В качестве аргумента селектор будет передавать **Redux** **state** и будет вызываться когда компонент перерендеривается, так же он подписывается на **store** и вызывается каждый раз при изменении.
- `useDispatch()` - этот хук возвращает ссылку на `dispatch` функцию из **Redux**. Вы можете использовать его для отправки действий.
- `useStore()` - этот хук возвращает ссылку на то же **хранилище** **Redux**, которое было передано `<Provider>` компоненту.
- `useShallowEqualSelector()` - хук содержащий функцию `shalowEqual`  
     .  
    

Counter.js

```JavaScript
import {inc, dec, rnd} from '../actions';
import { useSelector, useDispatch } from "react-redux";

const Counter = () => {

    const counter = useSelector(state => state.counter);
    const dispatch = useDispatch();
    
    return (
        <div className="jumbotron">
            <h1>{counter}</h1>
            <button onClick={() => dispatch(dec())} className="btn btn-primary">DEC</button>
            <button onClick={() => dispatch(inc())} className="btn btn-primary">INC</button>
            <button onClick={() => dispatch(rnd())} className="btn btn-primary">RND</button>
        </div>
    )
}

export default Counter;
```