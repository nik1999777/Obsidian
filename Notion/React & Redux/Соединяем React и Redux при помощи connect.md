[https://www.samdawson.dev/article/react-redux-use-selector-vs-connect/](https://www.samdawson.dev/article/react-redux-use-selector-vs-connect/) - useSelector vs connect

[https://react-redux.js.org/api/connect](https://react-redux.js.org/api/connect) - документация connect

![[Untitled 66.png|Untitled 66.png]]

Компоненты **React** с **Redux** можно соединять 2-мя способами:

- через **функцию** **connect**
- через **хуки**

  

**Функция** **connect** - это **HOC**, который оборачивает нужный нам компонент и в качестве **props-ов** передает ему что-то из нашего **store**.

`connect([mapStateToProps], [mapDispatchToProps], [mergeProps], [options])` — позволяет создавать **компоненты** **высшего** **порядка**. Это нужно для создания компонентов-контейнеров на основе базовых компонентов React.

  

**Сonnect** принимает четыре различных параметра, все необязательные:

```JavaScript
mapStateToProps?: Function
mapDispatchToProps?: Function | Object
mergeProps?: Function
options?: Object
```

**Сonnect** все равно с чем работать - с **функциональным** компонентом или классовым. Она просто берет компонент и передает ему **объект** **props-ов**.

  

Counter.js

```JavaScript
import { Component } from "react";
import { connect } from "react-redux";
import * as actions from '../actions';

// const Counter = ({counter, inc, dec, rnd}) => {
//     return (
//         <div className="jumbotron">
//             <h1>{counter}</h1>
//             <button onClick={dec} className="btn btn-primary">DEC</button>
//             <button onClick={inc} className="btn btn-primary">INC</button>
//             <button onClick={rnd} className="btn btn-primary">RND</button>
//         </div>
//     )
// }

class Counter extends Component {
    render() {
        const {counter, inc, dec, rnd} = this.props;
        return (
            <div className="jumbotron">
                <h1>{counter}</h1>
                <button onClick={dec} className="btn btn-primary">DEC</button>
                <button onClick={inc} className="btn btn-primary">INC</button>
                <button onClick={rnd} className="btn btn-primary">RND</button>
            </div>
        )
    }
}

const mapStateToProps = (state) => {
    return {
        counter: state.value
    }
}

// const mapDispatchToProps = (dispatch) => {
//	   return bindActionCreators(actions, dispatch)
// }

export default connect(mapStateToProps, actions)(Counter);
```