[https://developer.mozilla.org/ru/docs/Learn/HTML/Howto/Use_data_attributes](https://developer.mozilla.org/ru/docs/Learn/HTML/Howto/Use_data_attributes) - про **data -** **атрибуты**

  

Мы можем обратиться к **тэгам** **body** и **head**.

```JavaScript
console.log(document.body);
console.log(document.head);
```

И также, чтобы обратиться к **тэгу** **html** мы используем **свойство** **documentElement**

```JavaScript
console.log(document.documentElement);
```

![[Untitled 114.png|Untitled 114.png]]

![[Untitled 1 52.png|Untitled 1 52.png]]

Также существует такое **свойство** как **childNodes**, которое позволяет нам получить все **Node** (**Ноды**), все **узлы**, которые находятся внутри **родителя** **body**.

```JavaScript
console.log(document.body.childNodes);
```

![[Untitled 2 39.png|Untitled 2 39.png]]

Аналога этого свойства **childNodes** для элементов - нет. Но мы можем перебрать элементы в **псевдомассиве** при помощи **for of**. Таким образом мы получаем все элементы, кроме текстовых **Node**, за счет того, что мы используем оператор **continue**. То есть нужно запомнить, что иногда нам необходимо перебрать какие-то элементы в **псевдомассиве** при помощи **for of** для того, чтобы иметь возможность останавливать **цикл**, либо полностью его прерывать.

```JavaScript
for (let node of document.body.childNodes) {
    if (node.nodeName == '\#text') {
        continue;
    }
    console.log(node);
}
```

![[Untitled 3 27.png|Untitled 3 27.png]]

Какая разница между **DOM - элементами** и **DOM - узлами**?

Все что мы видим в **тэгах** - это будет **DOM - элементом** , все то, что мы возможно не видим - это **DOM - узлом** (**переносы строк**, какие-то **текстовые** **элементы**)

Если посмотреть на данный код, то **<li>** - это **DOM - элемент**, а внутри него текстовый **DOM - узел**, который представлен в виде единички.

```JavaScript
<li>1</li>
```

Также существуют такие **свойства**, которые позволяют получить либо первого ребенка внутри **родителя**, либо последнего. И мы действительно видим, что первым идет **text**, а потом **script**.

```JavaScript
console.log(document.body.firstChild);
console.log(document.body.lastChild);
```

![[Untitled 4 19.png|Untitled 4 19.png]]

А если пропишем **firstElementChild** или **lastElementChild**, то мы получим точно элементы, а не **Node** (ноды)

```JavaScript
console.log(document.body.firstElementChild);
console.log(document.body.lastElementChild);
```

![[Untitled 5 16.png|Untitled 5 16.png]]

Используем команду **parentNode** и получаем наш элемент с классом **class = "first"**. И если мы эту команду **parentNode** дублируем 2 раза, то мы получаем элемент с классом **class = "wrapper"**. Таким образом мы с вами путешествуем по нашему **DOM - дереву**.

```JavaScript
console.log(document.querySelector('\#current').parentNode);
console.log(document.querySelector('\#current').parentNode.parentNode);
```

Если мы пропишем команду **parentElement**, то таким образом мы точно будем знать, что получим элемент, а не **Node**.

```JavaScript
console.log(document.querySelector('\#current').parentElement);
```

![[Untitled 6 15.png|Untitled 6 15.png]]

![[Untitled 7 14.png|Untitled 7 14.png]]

С помощью **data-атрибутов** в верстке очень легко ориентироваться в наших скриптах. Используем свойство **nextSibling**, чтобы получить следующий за ним элемент и получаем с вами в консоле текстовую **Node(ноду)**. А чтобы получить предыдущий элемент, мы используем свойство **previousSibling** и мы тоже получаем текстовую **Node(ноду)**.

```JavaScript
console.log(document.querySelector('[data-current="3"]').nextSibling);
console.log(document.querySelector('[data-current="3"]').previousSibling);
```

![[Untitled 8 12.png|Untitled 8 12.png]]

Чтобы получить следующий или предыдущий элемент, а не **Node(ноду)**, то мы пишем **nextElementSibling** и **previousElementSibling**.

```JavaScript
console.log(document.querySelector('[data-current="3"]').nextElementSibling);
console.log(document.querySelector('[data-current="3"]').previousElementSibling);
```

![[Untitled 9 10.png|Untitled 9 10.png]]

Синтаксис **data-атрибутов** таков, что сначала мы пишем **data-** , а потом какое-то название, например: **current**, **modal**, **close** и т. д. И потом можем записать просто **data-current**, а можем назначить какое-то значение, например **="3"**.

```JavaScript
<div class="second">
            <ul>
                <li>1</li>
                <li>2</li>
                <li data-current="3">3</li>

                <li>4</li>
                <li>5</li>
            </ul>
        </div>
```