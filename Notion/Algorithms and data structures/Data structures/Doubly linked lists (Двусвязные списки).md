Как уже упоминалось, разница между двусвязными и односвязными списками заключается в том, что узлы двусвязных списков связаны через указатели как с предыдущим, так и со следующим значением. С другой стороны, односвязные списки соединяют свои узлы только со следующим значением.

---

Этот подход с двойным указателем позволяет двусвязным спискам работать лучше с некоторыми методами по сравнению с односвязными списками, но за счет потребления большего количества памяти (с двусвязными списками нам нужно хранить два указателя вместо одного).

---

Полная реализация двусвязного списка может выглядеть примерно так:

```JavaScript
// We create a class for each node within the list
// Мы создаем класс для каждого узла в списке
class Node{
    // Each node has three properties, its value, a pointer that indicates the node that follows and a pointer that indicates the previous node
		// Каждый узел имеет три свойства: его значение, указатель, указывающий на следующий за ним узел, и указатель, указывающий на предыдущий узел
    constructor(val){
        this.val = val;
        this.next = null;
        this.prev = null;
    }
}

// We create a class for the list
// Создаем класс для списка
class DoublyLinkedList {
    // The list has three properties, the head, the tail and the list size
		// Список имеет три свойства: начало, конец и размер списка.
    constructor(){
        this.head = null
        this.tail = null
        this.length = 0
    }
    // The push method takes a value as parameter and assigns it as the tail of the list
		// Метод push принимает значение в качестве параметра и присваивает его хвосту списка
    push(val){
        const newNode = new Node(val)
        if(this.length === 0){
            this.head = newNode
            this.tail = newNode
        } else {
            this.tail.next = newNode
            newNode.prev = this.tail
            this.tail = newNode
        }
        this.length++
        return this
    }
    // The pop method removes the tail of the list
		// Метод pop удаляет конец списка
    pop(){
        if(!this.head) return undefined
        const poppedNode = this.tail
        if(this.length === 1){
            this.head = null
            this.tail = null
        } else {
            this.tail = poppedNode.prev
            this.tail.next = null
            poppedNode.prev = null
        }
        this.length--
        return poppedNode
    }
    // The shift method removes the head of the list
		// Метод shift удаляет начало списка
    shift(){
        if(this.length === 0) return undefined
        const oldHead = this.head
        if(this.length === 1){
            this.head = null
            this.tail = null
        } else{
            this.head = oldHead.next
            this.head.prev = null
            oldHead.next = null
        }
        this.length--
        return oldHead
    }
    // The unshift method takes a value as parameter and assigns it as the head of the list
		// Метод unshift принимает значение в качестве параметра и назначает его в начало списка
    unshift(val){
        const newNode = new Node(val)
        if(this.length === 0) {
            this.head = newNode
            this.tail = newNode
        } else {
            this.head.prev = newNode
            newNode.next = this.head
            this.head = newNode
        }
        this.length++
        return this
    }
    // The get method takes an index number as parameter and returns the value of the node at that index
		// Метод get принимает номер индекса в качестве параметра и возвращает значение узла с этим индексом
    get(index){
        if(index < 0 || index >= this.length) return null
        let count, current
        if(index <= this.length/2){
            count = 0
            current = this.head
            while(count !== index){
                current = current.next
                count++
            }
        } else {
            count = this.length - 1
            current = this.tail
            while(count !== index){
                current = current.prev
                count--
            }
        }
        return current
    }
    // The set method takes an index number and a value as parameters, and modifies the node value at the given index in the list
		// Метод set принимает номер индекса и значение в качестве параметров и изменяет значение узла по данному индексу в списке
    set(index, val){
        var foundNode = this.get(index)
        if(foundNode != null){
            foundNode.val = val
            return true
        }
        return false
    }
    // The insert method takes an index number and a value as parameters, and inserts the value at the given index in the list
		// Метод вставки принимает номер индекса и значение в качестве параметров и вставляет значение по данному индексу в список
    insert(index, val){
        if(index < 0 || index > this.length) return false
        if(index === 0) return !!this.unshift(val)
        if(index === this.length) return !!this.push(val)

        var newNode = new Node(val)
        var beforeNode = this.get(index-1)
        var afterNode = beforeNode.next

        beforeNode.next = newNode, newNode.prev = beforeNode
        newNode.next = afterNode, afterNode.prev = newNode
        this.length++
        return true
    }
}
```

Большой O (big O) методов двусвязных списков заключается в следующем:

- Insertion - O(1) (Вставка)
- Removal - O(1) (Удаление)
- Searching - O(n) (Поиск)
- Access - O(n) (Доступ)