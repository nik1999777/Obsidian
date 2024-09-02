[https://ru.reactjs.org/docs/hooks-reference.html#usememo](https://ru.reactjs.org/docs/hooks-reference.html#usememo) - документация useMemo

[https://alexsidorenko.com/blog/react-render-cheat-sheet/](https://alexsidorenko.com/blog/react-render-cheat-sheet/) - крутой гайд по рендеру

  

![[Untitled 49.png|Untitled 49.png]]

В нашем слайдере может быть дополнительная **логика** по какому-то сложному вычислению. (Например по вычислению **countTotal** кол-во слайдеров).

При изменении **state** у нас как обычно происходит **перерендер** страницы и каждый раз будет вызываться **функция** **countTotal** и перезаписывать значение в **total**.

И естественно мы хотим как то запомнить(закэшировать) значение **total**, чтобы каждый раз его не высчитывать. Или вызывать **функцию** в тот момент, когда нам действительно это нужно.

Для таких целей как раз и используется **хук** **useMemo**.

> [!important]  
> useMemo работает точно также, как и useCallback. Его отличие лишь в том, что он позволяет нам мемоизировать значение, а не функцию как это было в useCallback.  

Важно в **useMemo** нельзя помещать **побочные** **эффекты**: **запросы** и **подписки**. Это может привести к багам, так как **useMemo** запускается во время **рендеринга**.

  

Также с помощью **хука** **useMemo** можно **мемоизировать объекты**.

Мы помним из **JS**, что **объекты** сравниваются по **ссылкам**.(если **объекты** содержат одинаковые внутренности - это не значит, что объекты **равны**)

Таким образом в данном коде, когда происходит сравнение **объектов** - **React** решит, что **объект** поменялся. Поэтому каждый раз он все равно будет запускать наш **useEffect**, даже не смотря на то, что мы с **объектом** никак работать не будем.

Поэтому для лучшей оптимизации, мы делаем так, чтобы объект **style** был **закэширован**. (То есть теперь если у нас меняется **state** - **slide**, то у нас будет перерисовывать **объект - style**. Но если меняется совсем другой **state**, то значение будет запомнено)

App.js

```JavaScript
import {useState, useEffect, useMemo} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

const countTotal = (num) => {
    console.log('counting...');
    return num + 10;
}

const Slider = (props) => {

    const [slide, setSlide] = useState(0);
    const [autoplay, setAutoplay] = useState(false);

    function changeSlide(i) {
        setSlide(slide => slide + i);
    }

    function toggleAutoplay() {
        setAutoplay(autoplay => !autoplay);
    }

    const total = useMemo(() => {
        return countTotal(slide);
    }, [slide]);

    const style = useMemo(() => ({
        color: slide > 4 ? 'red' : 'black'
    }), [slide])

    useEffect(() => {
        console.log('styles!');
    }, [style])

    return (
        <Container>
            <div className="slider w-50 m-auto">
                <div className="text-center mt-5">Active slide {slide} <br/>{autoplay ? 'auto' : null}</div>
                <div style={style} className="text-center mt-5">Total slides: {total}</div>
                <div className="buttons mt-3">
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => changeSlide(-1)}>-1</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={() => changeSlide(1)}>+1</button>
                    <button 
                        className="btn btn-primary me-2"
                        onClick={toggleAutoplay}>toggle autoplay</button>
                </div>
            </div>
        </Container>
    )
}

function App() {
    return(
        <Slider/>
    );
}

export default App;
```