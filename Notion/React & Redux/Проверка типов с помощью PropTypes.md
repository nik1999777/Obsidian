[https://www.npmjs.com/package/prop-types](https://www.npmjs.com/package/prop-types) - prop-types npm

[https://ru.reactjs.org/docs/typechecking-with-proptypes.html](https://ru.reactjs.org/docs/typechecking-with-proptypes.html) - документация про PropTypes

  

> [!important]  
> Для того чтобы следить за типами данных у props внутри компонентов стоит использовать технологию PropTypes.  

Данную технологию нужно установить как **npm** **пакет**.

```JavaScript
npm i prop-types
```

И импортировать в том месте, где мы ее хотим использовать

```JavaScript
import PropTypes from 'prop-types';
```

> [!important]  
> По простому данная технология позволяет прописывать правила для проверки props-ов. Если props не подходит по типу - будет показываться уведомление об этом в терминале.  

Данная **библиотека** будет работать только в режиме разработки.

  

Здесь **charId** проверяем на число.

```JavaScript
CharInfo.propTypes = {
    charId: PropTypes.number
}
```

Можно добавить **isRequired** к любому типу, чтобы показывать предупреждение, если **prop** не передан.

```JavaScript
CharList.propTypes = {
    onCharSelected: PropTypes.func.isRequired
}
```