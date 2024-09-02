Бинарные или двоичные деревья — это тип дерева, в котором каждый узел имеет не более двух дочерних элементов.

![[Untitled 181.png|Untitled 181.png]]

A binary tree (бинарное дерево)

Одна из ключевых ситуаций, в которой бинарные деревья действительно полезны, — это поиск. А для поиска используется определенный тип бинарных деревьев, называемых **бинарными деревьями поиска (BST - binary search trees)** .

---

BST похожи на бинарные деревья, но информация в них упорядочена таким образом, что делает их подходящей структурой данных для поиска.

---

В BST значения упорядочены таким образом, что каждый узел, который спускается слева от своего родителя, должен иметь значение меньше, чем его родитель, а каждый узел, который спускается справа от своего родителя, должен иметь значение больше, чем его родитель.

![[Untitled 1 85.png|Untitled 1 85.png]]

A binary search tree (бинарное дерево поиска)

Такой порядок значений делает эту структуру данных отличной для поиска, поскольку на каждом уровне дерева мы можем определить, больше или меньше искомое значение, чем родительский узел, и от этого сравнения постепенно отбрасывать примерно половину данных до тех пор, пока мы достигаем нашего значения.

---

При **вставке или удалении значений** алгоритм будет выполнять следующие шаги:

  

- Проверьте, есть ли корневой узел.
- Если есть, проверьте, больше или меньше значение, которое нужно добавить/удалить, чем узел.
- Если он меньше, проверьте, есть ли узел левее, и повторите предыдущую операцию. Если нет, добавьте/удалите узел в этой позиции.
- Если оно больше, проверьте, есть ли узел справа, и повторите предыдущую операцию. Если нет, добавьте/удалите узел в этой позиции.

---

Поиск в BST очень похож, только вместо добавления/удаления значений мы проверяем узлы на равенство с искомым значением.

---

Большая **O (big O)** сложность этих операций **логарифмическая (log(n))**. Но важно признать, что для достижения этой сложности дерево должно иметь сбалансированную структуру, чтобы на каждом шаге поиска можно было «отбросить» примерно половину данных. Если больше значений хранится с одной или другой стороны из трех, это влияет на эффективность структуры данных.

---

Реализация BST может выглядеть так:

```JavaScript
// We create a class for each node within the tree
// Мы создаем класс для каждого узла внутри дерева
class Node{
    // Each node has three properties, its value, a pointer that indicates the node to its left and a pointer that indicates the node to its right
		// Каждый узел имеет три свойства: его значение, указатель, указывающий на узел слева от него, и указатель, указывающий на узел справа от него
    constructor(value){
        this.value = value
        this.left = null
        this.right = null
    }
}
// We create a class for the BST
// Создаем класс для BST
class BinarySearchTree {
    // The tree has only one property which is its root node
		// Дерево имеет только одно свойство, которое является его корневым узлом
    constructor(){
        this.root = null
    }
    // The insert method takes a value as parameter and inserts the value in its corresponding place within the tree
		// Метод вставки принимает значение в качестве параметра и вставляет значение в соответствующее место в дереве
    insert(value){
        const newNode = new Node(value)
        if(this.root === null){
            this.root = newNode
            return this
        }
        let current = this.root
        while(true){
            if(value === current.value) return undefined
            if(value < current.value){
                if(current.left === null){
                    current.left = newNode
                    return this
                }
                current = current.left
            } else {
                if(current.right === null){
                    current.right = newNode
                    return this
                } 
                current = current.right
            }
        }
    }
    // The find method takes a value as parameter and iterates through the tree looking for that value
    // If the value is found, it returns the corresponding node and if it's not, it returns undefined
		// Метод find принимает значение в качестве параметра и выполняет итерацию по дереву в поисках этого значения
    // Если значение найдено, возвращает соответствующий узел, а если нет, то возвращает undefined
    find(value){
        if(this.root === null) return false
        let current = this.root,
            found = false
        while(current && !found){
            if(value < current.value){
                current = current.left
            } else if(value > current.value){
                current = current.right
            } else {
                found = true
            }
        }
        if(!found) return undefined
        return current
    }
    // The contains method takes a value as parameter and returns true if the value is found within the tree
		// Метод contains принимает значение в качестве параметра и возвращает true, если значение найдено в дереве
    contains(value){
        if(this.root === null) return false
        let current = this.root,
            found = false
        while(current && !found){
            if(value < current.value){
                current = current.left
            } else if(value > current.value){
                current = current.right
            } else {
                return true
            }
        }
        return false
    }
}
```