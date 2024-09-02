При кодировании графов мы можем использовать два основных метода: **матрицу смежности** и **список смежности** . Давайте объясним, как работают оба, и посмотрим на их плюсы и минусы.

---

Матрица **смежности — это двумерная структура** , которая представляет узлы нашего графа и связи между ними.

Если мы используем этот пример…

![[Untitled 161.png|Untitled 161.png]]

Наша матрица смежности будет выглядеть так:

![[Untitled 1 81.png|Untitled 1 81.png]]

Вы можете видеть, что матрица похожа на таблицу, где столбцы и строки представляют узлы на нашем графике, а значения ячеек представляют связи между узлами. Если ячейка равна 1, между строкой и столбцом есть связь, а если 0 — нет.

---

Таблицу можно легко реплицировать с помощью двумерного массива:

```JavaScript
[
    [0, 1, 1, 0]
    [1, 0, 0, 1]
    [1, 0, 0, 1]
    [0, 1, 1, 0]
]
```

С другой стороны, **список смежности** можно рассматривать как **структуру пары ключ-значение,** где **ключи представляют каждый узел** на нашем графе, а **значения — это связи** , которые имеет этот конкретный узел.

---

Используя тот же пример графа, наш список смежности может быть представлен следующим объектом:

```JavaScript
{
    A: ["B", "C"],
    B: ["A", "D"],
    C: ["A", "D"],
    D: ["B", "C"],
}
```

Вы можете видеть, что для каждого узла у нас есть ключ, и мы храним все соединения узла в массиве.

---

Так в чем же разница между матрицами смежности и списками? Ну, списки, как правило, более эффективны, когда речь идет о добавлении или удалении узлов, в то время как матрицы более эффективны при запросе конкретных соединений между узлами.

---

Чтобы увидеть это, представьте, что мы хотим добавить новый узел в наш граф:

![[Untitled 2 59.png|Untitled 2 59.png]]

Наша матрица смежности будет выглядеть так:

![[Untitled 3 44.png|Untitled 3 44.png]]

В то время как, чтобы сделать то же самое в списке, достаточно добавить значение к соединениям B и пару ключ-значение для представления E:

```JavaScript
{
    A: ["B", "C"],
    B: ["A", "D", "E"],
    C: ["A", "D"],
    D: ["B", "C"],
    E: ["B"],
}
```

Полная реализация графа с использованием списка смежности может выглядеть так. Для простоты мы представим не ориентированный не взвешенный граф.

```JavaScript
// We create a class for the graph
// Создаем класс для графика
class Graph{
    // The graph has only one property which is the adjacency list
		// Граф имеет только одно свойство — список смежности
    constructor() {
        this.adjacencyList = {}
    }
    // The addNode method takes a node value as parameter and adds it as a key to the adjacencyList if it wasn't previously present
		// Метод addNode принимает значение узла в качестве параметра и добавляет его в качестве ключа в список adjacencyList, если он ранее не присутствовал
    addNode(node) {
        if (!this.adjacencyList[node]) this.adjacencyList[node] = []
    }
    // The addConnection takes two nodes as parameters, and it adds each node to the other's array of connections.
		// addConnection принимает два узла в качестве параметров и добавляет каждый узел в массив соединений другого.
    addConnection(node1,node2) {
        this.adjacencyList[node1].push(node2)
        this.adjacencyList[node2].push(node1)
    }
    // The removeConnection takes two nodes as parameters, and it removes each node from the other's array of connections.
		// removeConnection принимает два узла в качестве параметров и удаляет каждый узел из другого массива соединений.
    removeConnection(node1,node2) {
        this.adjacencyList[node1] = this.adjacencyList[node1].filter(v => v !== node2)
        this.adjacencyList[node2] = this.adjacencyList[node2].filter(v => v !== node1)
    }
    // The removeNode method takes a node value as parameter. It removes all connections to that node present in the graph and then deletes the node key from the adj list.
		// Метод removeNode принимает в качестве параметра значение узла. Он удаляет все соединения с этим узлом, присутствующим в графе, а затем удаляет ключ узла из списка adj.
    removeNode(node){
        while(this.adjacencyList[node].length) {
            const adjacentNode = this.adjacencyList[node].pop()
            this.removeConnection(node, adjacentNode)
        }
        delete this.adjacencyList[node]
    }
}

const Argentina = new Graph()
Argentina.addNode("Buenos Aires")
Argentina.addNode("Santa fe")
Argentina.addNode("Córdoba")
Argentina.addNode("Mendoza")
Argentina.addConnection("Buenos Aires", "Córdoba")
Argentina.addConnection("Buenos Aires", "Mendoza")
Argentina.addConnection("Santa fe", "Córdoba")

console.log(Argentina)
// Graph {
//     adjacencyList: {
//         'Buenos Aires': [ 'Córdoba', 'Mendoza' ],
//         'Santa fe': [ 'Córdoba' ],
//         'Córdoba': [ 'Buenos Aires', 'Santa fe' ],
//         Mendoza: [ 'Buenos Aires' ]
//     }
// }
```