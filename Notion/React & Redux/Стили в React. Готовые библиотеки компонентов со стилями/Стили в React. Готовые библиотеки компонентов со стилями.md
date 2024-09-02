[https://react-bootstrap.github.io/](https://react-bootstrap.github.io/) - react bootstrap

[https://reactstrap.github.io/?path=/story/home-installation--page](https://reactstrap.github.io/?path=/story/home-installation--page) - reactstrap

[https://mui.com/](https://mui.com/) - material design

[https://habr.com/ru/post/335244/](https://habr.com/ru/post/335244/) - практическое руководство по использованию CSS Modules в React приложениях

[https://ant.design/](https://ant.design/) - ant design

  

Существуют готовые библиотеки, которые помогают быстро создать интерфейс сайта или приложения.

Необходимо сначала установить библиотеку в свой проект. Импортировать ее компоненты и использовать их.

  

![[Untitled 31.png|Untitled 31.png]]

index.js

```JavaScript
import React, {StrictMode} from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import {Button} from './App';
import BootstrapTest from './BootstrapTest';
import styled from 'styled-components';

import 'bootstrap/dist/css/bootstrap.min.css';


const BigButton = styled(Button)`
	margin: 0 auto;
	width: 245px;
`;

ReactDOM.render(
	<StrictMode>
		<App/>
		<BigButton as="a">Отправить отчет</BigButton>
		<BootstrapTest/>
	</StrictMode>,
  document.getElementById('root')
);
```

BootstrapTest.js

```JavaScript
import {Container, Row, Col, Carousel, Form, Button} from 'react-bootstrap';

const BootstrapTest = () => {
    return (
        <Container className="mt-5 mb-5">
            <Row>
                <Col>
                    <Form>
                        <Form.Group className="mb-3" controlId="formBasicEmail">
                            <Form.Label>Email address</Form.Label>
                            <Form.Control type="email" placeholder="Enter email" />
                            <Form.Text className="text-muted">
                            We'll never share your email with anyone else.
                            </Form.Text>
                        </Form.Group>

                        <Form.Group className="mb-3" controlId="formBasicPassword">
                            <Form.Label>Password</Form.Label>
                            <Form.Control type="password" placeholder="Password" />
                        </Form.Group>
                        <Form.Group className="mb-3" controlId="formBasicCheckbox">
                            <Form.Check type="checkbox" label="Check me out" />
                        </Form.Group>
                        <Button variant="primary" type="submit">
                            Submit
                        </Button>
                    </Form>
                </Col>
                <Col>
                <Carousel>
                    <Carousel.Item>
                        <img
                        className="d-block w-100"
                        src="https://www.planetware.com/wpimages/2020/02/france-in-pictures-beautiful-places-to-photograph-eiffel-tower.jpg"
                        alt="First slide"
                        />
                        <Carousel.Caption>
                        <h3>First slide label</h3>
                        <p>Nulla vitae elit libero, a pharetra augue mollis interdum.</p>
                        </Carousel.Caption>
                    </Carousel.Item>
                    <Carousel.Item>
                        <img
                        className="d-block w-100"
                        src="https://ichef.bbci.co.uk/news/999/cpsprodpb/15951/production/_117310488_16.jpg"
                        alt="Second slide"
                        />

                        <Carousel.Caption>
                        <h3>Second slide label</h3>
                        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
                        </Carousel.Caption>
                    </Carousel.Item>
                    <Carousel.Item>
                        <img
                        className="d-block w-100"
                        src="https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885__480.jpg"
                        alt="Third slide"
                        />

                        <Carousel.Caption>
                        <h3>Third slide label</h3>
                        <p>Praesent commodo cursus magna, vel scelerisque nisl consectetur.</p>
                        </Carousel.Caption>
                    </Carousel.Item>
                </Carousel>
                </Col>
            </Row>
        </Container>
    )
}

export default BootstrapTest;
```