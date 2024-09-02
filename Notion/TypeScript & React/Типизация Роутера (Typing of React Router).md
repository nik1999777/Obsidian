  

```Plain
yarn add react-router-dom @types/react-router-dom
```

Для того чтобы определить props-ы из **react-router** - существует специальный **тип RouteComponentProps**, который мы импортируем из библиотеки **react-router**.

И далее создаем типы - **type** **RouteParams**, **interface** **IPost** и **type** **PostState**.

И передаем их в виде - **Generic**.

```TypeScript
import React, { Component } from 'react';
import { RouteComponentProps } from 'react-router';

type RouteParams = {
  id: string,
}

interface IPost {
  title?: string,
  body?: string,
}

type PostState = {
  post: IPost,
}

class Post extends Component<RouteComponentProps<RouteParams>, PostState> {
  state = {
    post: {
      title: '',
      body: '',
    },
  }

  componentDidMount() {
    const id = this.props.match.params.id || '';

    fetch(`https://jsonplaceholder.typicode.com/posts/${id}`)
      .then(res => res.json())
      .then(post => { this.setState({ post }) })
  }

  render() {
    const { post } = this.state;
    const { title, body } = post;

    return (
      <section>
        <h1>Post</h1>
        <article>
          <h2>{title}</h2>
          <p>{body}</p>
        </article>
      </section>
    );
  }
};

export default Post;
```

Если нам нужно объединить типы props-ов - то мы воспользоваться отдельным **интерфейсом** и расширить значения одних props-ов другими.

Этот синтаксис очень нагляден - если нам дополнительно нужно создавать типизацию для нескольких видов props-ов.

```TypeScript
interface IPosts extends RouteComponentProps {
  test?: number,
}
```