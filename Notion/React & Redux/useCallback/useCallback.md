[https://ru.reactjs.org/docs/hooks-reference.html#usecallback](https://ru.reactjs.org/docs/hooks-reference.html#usecallback) - документация useCallback

![[Untitled 48.png|Untitled 48.png]]

Представим ситуацию, что наш слайдер загружает изображения посредством **запроса** **на сервер**.

Для имитации такого **запроса** создадим **функцию** **getSomeImages**, которая возвращает нас **массив** с **2** **строками**.

И далее на основании этих данных мы формируем **верстку**.

  

Когда мы начнем переключать слайдер, а соответственно изменять **state**, то мы каждый раз будем запускать этот **запрос**(**функцию** **getSomeImages**). А это сильно отразится на оптимизации.

Происходит это по той причине, что при каждом изменении **state** у нас каждый раз вызывается **рендеринг** **компонента** и соответственно и вызов **функции** **getSomeImages** будет запускаться каждый раз.

  

А как **закэшировть функцию**? Как сделать так, чтобы **функция** **getSomeImages** вызывалась только один раз и только по надобности?

Для этого и существует **хук** **useCallback**, который вернет нам **мемоизированную** версию **callback**.

**useCallback:**

- данный **хук** используется только при передаче **дочернему** компоненту, который не должен каждый раз меняться при **рендеринге** (в данном коде мы создали **дочерний** компонент **Slide**, в котором мы прописали некий функционал и как **props** передали функцию **getSomeImages** и далее использовали **Slide** внутри **родительского** **Slider**)
- в данном **хуке**: 1 **аргумент** - **функция**, 2 - **массив** **зависимостей**

App.js

```JavaScript
import {useState, useCallback, useEffect} from 'react';
import {Container} from 'react-bootstrap';
import './App.css';

const Slider = (props) => {

    const [slide, setSlide] = useState(0);
    const [autoplay, setAutoplay] = useState(false);

    const getSomeImages = useCallback(() => {
        console.log('fetching')
        return [
            "https://klike.net/uploads/posts/2019-05/1556708032_1.jpg",
            "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR_XpQ3hwSx37x0OsujocBzVNzP3-YdThNeHg&usqp=CAU"
        ]
    }, [])

    function changeSlide(i) {
        setSlide(slide => slide + i);
    }

    function toggleAutoplay() {
        setAutoplay(autoplay => !autoplay);
    }

    return (
        <Container>
            <div className="slider w-50 m-auto">

                <Slide getSomeImages={getSomeImages}/>

                <div className="text-center mt-5">Active slide {slide} <br/>{autoplay ? 'auto' : null}</div>
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

const Slide = ({getSomeImages}) => {
    const [images, setImages] = useState([]);

    useEffect(() => {
        setImages(getSomeImages())
    }, [getSomeImages])

    return (
        <>
            {images.map((url, i) => <img key={i} className="d-block w-100" src={url} alt="slide" />)}
        </>
    )
}

function App() {
    return(
        <Slider/>
    );
}

export default App;
```