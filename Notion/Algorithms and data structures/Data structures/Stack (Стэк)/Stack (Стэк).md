Стеки — это структуры данных, которые хранят информацию в виде списка. Они позволяют добавлять и удалять элементы только по **шаблону LIFO (последний пришел, первый ушел)**. В стеках элементы нельзя добавлять или удалять не по порядку, они всегда должны следовать шаблону **LIFO**.

---

Чтобы понять, как это работает, представьте себе стопку бумаг на столе. Вы можете добавить больше бумаг в стопку, только поместив их поверх всех остальных. А убрать бумагу из стопки можно, только взяв ту, что лежит поверх всех остальных. Последний пришел, первый вышел - **LIFO**.

![[Untitled 156.png|Untitled 156.png]]

A stack of papers (пачка бумаг)

Стеки полезны, когда нам нужно убедиться, что элементы следуют **шаблону LIFO**. Некоторые примеры использования стека:

- Стек вызовов JavaScript.
- Управление вызовами функций в различных языках программирования.
- Функциональность отмены/возврата, предлагаемая многими программами.

---

Существует несколько способов реализации стека, но, вероятно, самым простым является использование **массива с его методами** `**push**` **и** `**pop**` . Если мы будем использовать `pop` и `push` только для добавления и удаления элементов, мы всегда будем следовать шаблону **LIFO** и работать с ним как со стеком.

---

Другой способ — реализовать его как список, который может выглядеть так:

```JavaScript
// We create a class for each node within the stack
// Мы создаем класс для каждого узла в стеке
class Node {
    // Each node has two properties, its value and a pointer that indicates the node that follows
	  // Каждый узел имеет два свойства, его значение и указатель, указывающий следующий за ним узел
    constructor(value){
        this.value = value
        this.next = null
    }
}

// We create a class for the stack
// Создаем класс для стека
class Stack {
    // The stack has three properties, the first node, the last node and the stack size
		// Стек имеет три свойства: первый узел, последний узел и размер стека
    constructor(){
        this.first = null
        this.last = null
        this.size = 0
    }
    // The push method receives a value and adds it to the "top" of the stack
    // Метод push получает значение и добавляет его на «верх» стека
    push(val){
        var newNode = new Node(val)
        if(!this.first){
            this.first = newNode
            this.last = newNode
        } else {
            var temp = this.first
            this.first = newNode
            this.first.next = temp
        }
        return ++this.size
    }
    // The pop method eliminates the element at the "top" of the stack and returns its value
	  // Метод pop удаляет элемент на «верху» стека и возвращает его значение
    pop(){
        if(!this.first) return null
        var temp = this.first
        if(this.first === this.last){
            this.last = null
        }
        this.first = this.first.next
        this.size--
        return temp.value
    }
}

const stck = new Stack

stck.push("value1")
stck.push("value2")
stck.push("value3")

console.log(stck.first) /* 
        Node {
        value: 'value3',
        next: Node { value: 'value2', next: Node { value: 'value1', next: null } }
        }
    */
console.log(stck.last) // Node { value: 'value1', next: null }
console.log(stck.size) // 3

stck.push("value4")
console.log(stck.pop()) // value4
```

Большой О (big O) методов стека заключается в следующем:

- Insertion - O(1) (Вставка)
- Removal - O(1) (Удаление)
- Searching - O(n) (Поиск)
- Access - O(n) (Доступ)