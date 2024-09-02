  

**HOC** - это такой тип компонента, который принимает другой компонент, оборачивает его своей логикой тем самым расширяя его возможности и возвращает новый.

Разберем код:

- у нас есть HOC - withToggle и он принимает другой компонент
- внутри withToggle у нас с помощью хука useState - определено состояние, которое мы переключаем с помощью метода toggle
- сам метод toggle и состояние - мы передаем в оборачиваемый компонент PassedComponent, тем самым не изменяя логику исходного компонента - мы добавляем ему новый функционал

Начнем типизировать:

Создаем **типы** **type** - **BaseProps** и **InjectedProps**.

И с помощью **Generic** типизируем наш HOC.

```TypeScript
import React, { useState } from 'react';

type BaseProps = {
  primTitle: string,
  secTitle?: string,
}

type InjectedProps = {
  toggleStatus: Boolean,
  toggle: () => void,
}

const Button = ({ primTitle, secTitle, toggle, toggleStatus }: any) => (
  <button onClick={toggle}>
    {toggleStatus ? primTitle: secTitle}
  </button>
);

const withToggle = <BaseProps extends InjectedProps>(PassedComponent: React.ComponentType<BaseProps>) => {
  return (props: BaseProps) => {
    const [toggleStatus, toggle] = useState(false);

    return (
      <PassedComponent
        {...props as BaseProps}
        toggle={() => toggle(!toggleStatus)}
        toggleStatus={toggleStatus}
      />
    );
  }
}

const ToogleButton = withToggle(Button);

const App:React.FC = () => <ToogleButton primTitle="Maint Title" secTitle="Additional Title" />;

export default App;
```