Очереди работают очень похоже на стеки, но элементы добавляются и удаляются по другому шаблону. Очереди допускают только **шаблон FIFO (первым пришел, первым обслужен)** . В очередях элементы нельзя добавлять или удалять не по порядку, они всегда должны следовать шаблону FIFO.

---

Чтобы понять это, представьте себе людей, стоящих в очереди за едой. Логика здесь заключается в том, что если вы попадете в очередь первым, вас обслужат первым. Если вы доберетесь туда первым, вы будете первым - **FIFO**.😉

![[Untitled 157.png|Untitled 157.png]]

A queue of clients (очередь клиентов)

Некоторые примеры использования очереди:

- Фоновые задачи.
- Печать/обработка заданий.

---

Как и в случае с очередями, существует несколько способов реализации стека. Но, вероятно, самым простым является использование массива с его методами `push` и `shift`.

---

Если мы будем использовать `push` и `shift` только для добавления и удаления элементов, мы всегда будем следовать шаблону **FIFO** и работать с ним как с очередью.

---

Другой способ — реализовать его как список, который может выглядеть так:

```JavaScript
// We create a class for each node within the queue
// Мы создаем класс для каждого узла в очереди
class Node {
    // Each node has two properties, its value and a pointer that indicates the node that follows
		// Каждый узел имеет два свойства, его значение и указатель, указывающий следующий за ним узел
    constructor(value){
        this.value = value
        this.next = null
    }
}

// We create a class for the queue
// Создаем класс для очереди
class Queue {
    // The queue has three properties, the first node, the last node and the stack size
	  // Очередь имеет три свойства: первый узел, последний узел и размер стека
    constructor(){
        this.first = null
        this.last = null
        this.size = 0
    }
    // The enqueue method receives a value and adds it to the "end" of the queue
	  // Метод enqueue получает значение и добавляет его в "конец" очереди
    enqueue(val){
        var newNode = new Node(val)
        if(!this.first){
            this.first = newNode
            this.last = newNode
        } else {
            this.last.next = newNode
            this.last = newNode
        }
        return ++this.size
    }
    // The dequeue method eliminates the element at the "beginning" of the queue and returns its value
		// Метод dequeue удаляет элемент в "начале" очереди и возвращает его значение
    dequeue(){
        if(!this.first) return null

        var temp = this.first
        if(this.first === this.last) {
            this.last = null
        }
        this.first = this.first.next
        this.size--
        return temp.value
    }
}

const quickQueue = new Queue

quickQueue.enqueue("value1")
quickQueue.enqueue("value2")
quickQueue.enqueue("value3")

console.log(quickQueue.first) /* 
        Node {
            value: 'value1',
            next: Node { value: 'value2', next: Node { value: 'value3', next: null } }
        }
    */
console.log(quickQueue.last) // Node { value: 'value3, next: null }
console.log(quickQueue.size) // 3

quickQueue.enqueue("value4")
console.log(quickQueue.dequeue()) // value1
```

Большой О (big O) методов очереди заключается в следующем:

- Insertion - O(1) (Вставка)
- Removal - O(1) (Удаление)
- Searching - O(n) (Поиск)
- Access - O(n) (Доступ)