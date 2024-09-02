[https://github.com/facebook/create-react-app](https://github.com/facebook/create-react-app) - create react app

[https://babeljs.io/docs/en/babel-plugin-transform-react-jsx](https://babeljs.io/docs/en/babel-plugin-transform-react-jsx) - plugin-transform-react-jsx

[https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi) - расширение для chrome

## **Quick Overview**

`npx create-react-app my-app cd my-app npm start`

Основными частями сборки является **Webpack** и **Babel**.

**Webpack** собирает наш проект и следит за изменениями в файлах. И также обновлять страницу, если это необходимо.

**Babel** выступает в роли **компилятора**, он переводит **JSX** в обычный **JS** код. А также поддерживает разные браузеры.

**index.js** - самый главный файл в сборке, в котором мы будем собирать все наше приложение.

![[Untitled 12.png|Untitled 12.png]]

```JavaScript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```