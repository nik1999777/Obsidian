  

**Портал** - это нативный React компонент, который рендорит свое содержимое в любую часть DOM дерева, то есть вне корневого div.

Такое поведение позволяет отображать элементы - за пределами блоков (например со свойством overflow: hidden) и при этом минимально изменять дерево компонентов.

Следует отметить, что несмотря на то, что в DOM дереве **портал** выглядит, как отдельный элемент - внутри дерева компонентов React - он по-прежнему сохраняет свою вложенную структуру.

Применяются **порталы**:

- для различных всплывающих подсказок (Tooltip)
- модальных окон

В данном коде мы можем видеть простейшую реализацию **портала**.

Мы делаем его типизацию:

- компонент оборачивает элемент - а это значит, что у него появляется поле children - и **тип** этого поля **React.ReactNode**
- далее у нас определяется тип элемент, внутрь которого будет рендорится переданная разметка - **HTMLDivElement**
- методы жизненного цикла ничего не принимают и ничего не возвращают - поэтому тип **void**
- и также для наглядности типизируем метод render

Так как props-ы описываются дважды - то намного лучше будет вынести в отдельный тип - **type PortalProps**.

И как завершающий штрих к типизации **портала** - добавим **модификации**.

![[Untitled 87.png|Untitled 87.png]]

```TypeScript
import React, { Component } from 'react';
import ReactDOM from 'react-dom';


type PortalProps = {
  children: React.ReactNode,
}

class Portal extends Component<PortalProps> {
  private el: HTMLDivElement = document.createElement('div');

  public componentDidMount():void {
    document.body.appendChild(this.el);
  }

  public componentWillUnmount():void {
    document.body.removeChild(this.el);
  }

  public render(): React.ReactElement<PortalProps> {
    return ReactDOM.createPortal(this.props.children, this.el);
  }
}
```

**Контекст** - это способ передачи данных через дерево компонентов без необходимости передавать свойства вручную на каждом уровне.

То есть использование **контекста** помогает избежать - так называемого **props drilling**.

Разберем код:

- для начала мы создаем контекст - AuthContext, используя метод createContext(). В данный метод передается объект со значениями, которое нам нужно передать через дерево компонентов.
- далее идут - классовый компонент Login и функциональный компонент Profile - делают они одно и тоже. Мы специально записали 2 варианта, чтобы разобрать типизацию обоих.
- и в заключении идет классовый компонент, в котором описан метод переключения авторизации. И в методе render - 2 дочерних компонента обернуты в Provider.

Начнем типизацию:

- для начала через **interface** опишем наш контекст и с помощью **Generic** применим его к методу createContext().
- далее типизируем компонент Profile, используя - **React.FC**, **React.ReactElement** и **IContext**.
- и в компонент Login мы типизируем только свойство context, которое мы применяем в методе render - **React.ContextType<typeof AuthContext>**

Теперь компоненты, использующие контекст и сам контекст - строго типизированы с помощью TS.

![[Untitled 1 28.png|Untitled 1 28.png]]

```TypeScript
import React, { Component } from 'react';
import ReactDOM from 'react-dom';

interface IContext {
  isAuth: Boolean,
  toggleAuth: () => void,
}

// Context creation
const AuthContext = React.createContext<IContext>({
  isAuth: false,
  toggleAuth: () => {},
});

// Inner component (new syntax of static property)
class Login extends Component {

  static contextType = AuthContext;
  context!: React.ContextType<typeof AuthContext>

  render() {
    const { toggleAuth, isAuth } = this.context;

    return (
      <button onClick={toggleAuth}>
        {!isAuth ? 'Login' : 'Logout'}
      </button>
    );
  }
}

// Inner component (old variant with Consumer)
const Profile: React.FC = (): React.ReactElement => (
  <AuthContext.Consumer>
    {({ isAuth }: IContext) => (
      <h1>{!isAuth ? 'Please log in' : 'You are logged in'}</h1>
    )}
  </AuthContext.Consumer>
);

// Root component
class Context extends Component<{}, { isAuth: Boolean }> {
  readonly state = {
    isAuth: false,
  };

  toggleAuth = () => {
    this.setState(({ isAuth }) => ({
      isAuth: !isAuth
    }));
  };

  render() {
    const { isAuth } = this.state;
    const context: IContext = { isAuth, toggleAuth: this.toggleAuth };

    return (
      <AuthContext.Provider value={context}>
        <Login />
        <Profile />
      </AuthContext.Provider>
    );
  }
}

const App:React.FC = () => <Context />;

export default App;
```