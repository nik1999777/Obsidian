  

Хороший практический пример для чего нам нужен TS?

Если вдруг back что-то поменяет в структуре ответа или типах - то благодаря TS мы будем тут же об этом знать.

Поэтому мы разберемся с типизацией асинхронных функций.

  

В данном коде с помощью **Generic** - мы определили типы у асинхронного запроса.

Теперь наша функция http принимает **Generic** **type**, который мы строго определяем как **IPost** - при вызове в методе componentDidMount().

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

export async function http<T>(reques: string): Promise<T> {
  const response = await fetch(reques);
  const body = await response.json();
  return body;
}

class Post extends Component<RouteComponentProps<RouteParams>, PostState> {
  state = {
    post: {
      title: '',
      body: '',
    },
  }

  async componentDidMount() {
    const id = this.props.match.params.id || '';

    const post = await http<IPost>(`https://jsonplaceholder.typicode.com/posts/${id}`);
    this.setState({ post });
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

Теперь типизируем запрос другим способом - еще проще.

Все что мы делаем - это добавляем строку - **as Promise<IPost[]**

То есть мы получаем промис с **Generic** **type**.

```TypeScript
import React, { Component } from 'react';
import { Link } from 'react-router-dom';
import { RouteComponentProps } from 'react-router';

interface IPost {
  title?: string,
  id?: number,
}

type PostState = {
  data: IPost[],
}

interface IPosts extends RouteComponentProps {
  test?: number,
}

class Posts extends Component<IPosts, PostState> {
  state = {
    data: [],
  }

  componentDidMount() {
    fetch('https://jsonplaceholder.typicode.com/posts/')
      .then(res => res.json() as Promise<IPost[]>)
      .then(data => { this.setState({ data }) })
  }

  render() {
    const { data } = this.state;
    console.log(this.props.match.params);

    return (
      <div>
        <h1>Posts:</h1>
        <ul className="posts">
          {data.map(({ id, title }: IPost) =>
            <li key={id}><Link to={`/posts/${id}`}>{title}</Link></li>
          )}
        </ul>
      </div>
    );
  }
};

export default Posts;
```