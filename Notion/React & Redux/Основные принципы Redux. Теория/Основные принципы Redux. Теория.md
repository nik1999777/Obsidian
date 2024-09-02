[https://redux.js.org/assets/images/ReduxDataFlowDiagram-49fa8c3968371d9ef6f2a1486bd40a26.gif](https://redux.js.org/assets/images/ReduxDataFlowDiagram-49fa8c3968371d9ef6f2a1486bd40a26.gif) - схема

[https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd/related?hl=ru](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd/related?hl=ru) - redux devtools

  

В ходе обучения мы разработали 2 приложения c разными подходами в разработке:

**Employees app**

- все данные мы хранили в главном компоненте **App**
- и эти данные передавались по иерархии в другие компоненты
- для изменения **состояний** - мы использовали **систему событий** (**property drill**)

Плюсы:

- **централизации состояний** - они все хранятся в одном месте

Минусы:

- **property drill** - это достаточно сложный функционал, нам приходится приходится продумывать как пробрасывать данные выше и ниже
- каждый из компонентов может содержать абсолютно ненужные ему **свойства**

**Marvel** **app**

- у каждого компонента были свои **состояния**

Минусы:

- такой подход сложно масштабировать, особенно если начнут появляться зависимости между компонентами

![[Untitled 65.png|Untitled 65.png]]

Разберем схему:

- у нас есть просто отображение компонентов - **view**
- при выполнении какого-либо действия - создается **action**, который знает что нужно обновить в **state**
- **action** попадает в **reducer**, который знает как именно обновить этот **state**. **Reducer** обновляет **state** и компоненты перерисовываются заново на базе того **state**, который изменился.
- операция по передаче объекта **action** в **reducer** называется **dispatch** - это единственный способ изменить значение внутри **store**

![[Untitled 1 20.png|Untitled 1 20.png]]

![[Untitled 2 14.png|Untitled 2 14.png]]

  

**Redux** - это не обязательная часть **React**. Это один из вариантов **state** **managements**(то есть **управления** **состоянием** в приложениях).

Существует и другие **state** **managements**:

- **MobX**