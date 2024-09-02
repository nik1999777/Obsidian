### **JavaScript Algorithms and Data Structures**

---

- **Basic JavaScript**
    - [Comment Your JavaScript Code](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/comment-your-javascript-code)
        
        **Прокомментируйте свой код JavaScript**
        
        ```JavaScript
        // Hello world 
        
        /* Hello world! */
        ```
        
    - [Declare JavaScript Variables](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/declare-javascript-variables)
        
        **Объявить переменные JavaScript**
        
        ```JavaScript
        var myName;
        ```
        
    - [Storing Values with the Assignment Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/storing-values-with-the-assignment-operator)
        
        **Сохранение значений с помощью оператора присваивания**
        
        ```JavaScript
        var a;
        
        a = 7;
        ```
        
    - [Assigning the Value of One Variable to Another](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/assigning-the-value-of-one-variable-to-another)
        
        **Присвоение значения одной переменной другой**
        
        ```JavaScript
        var a;
        a = 7;
        var b;
        b = a
        ```
        
    - [Initializing Variables with the Assignment Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/initializing-variables-with-the-assignment-operator)
        
        **Инициализация переменных с помощью оператора присваивания**
        
        ```JavaScript
        var a = 9
        ```
        
    - [Declare String Variables](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/declare-string-variables)
        
        **Объявить строковые переменные**
        
        ```JavaScript
        var myFirstName = 'Nikita'
        var myLastName = 'Elin'
        ```
        
    - [Understanding Uninitialized Variables](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/understanding-uninitialized-variables)
        
        **Понимание неинициализированных переменных**
        
        ```JavaScript
        var a = 5;
        var b = 10;
        var c = "I am a";
        
        a = a + 1;
        b = b + 5;
        c = c + " String!";
        ```
        
        ```JavaScript
        6
        15
        I am a String!
        ```
        
    - [Understanding Case Sensitivity in Variables](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/understanding-case-sensitivity-in-variables)
        
        **Понимание чувствительности к регистру в переменных**
        
        ```JavaScript
        var studlyCapVar;
        var properCamelCase;
        var titleCaseOver;
        
        studlyCapVar = 10;
        properCamelCase = "A String";
        titleCaseOver = 9000;
        ```
        
    - [Explore Differences Between the var and let Keywords](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/explore-differences-between-the-var-and-let-keywords)
        
        **Исследуйте различия между ключевыми словами var и let**
        
        ```JavaScript
        let camper = "James";
        let camper = "David";
        ```
        
    - [Declare a Read-Only Variable with the const Keyword](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/declare-a-read-only-variable-with-the-const-keyword)
        
        **Объявите переменную только для чтения с ключевым словом const**
        
        ```JavaScript
        const FCC = "freeCodeCamp";
        let fact = "is cool!";
        fact = "is awesome!";
        console.log(FCC, fact);
        ```
        
    - [Add Two Numbers with JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/add-two-numbers-with-javascript)
        
        **Добавить два числа с помощью JavaScript**
        
        ```JavaScript
        const sum = 10 + 10;
        ```
        
        ```JavaScript
        20
        ```
        
    - [Subtract One Number from Another with JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/subtract-one-number-from-another-with-javascript)
        
        **Вычесть одно число из другого с помощью JavaScript**
        
        ```JavaScript
        const difference = 45 - 33;
        ```
        
        ```JavaScript
        12
        ```
        
    - [Multiply Two Numbers with JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/multiply-two-numbers-with-javascript)
        
        **Умножение двух чисел с помощью JavaScript**
        
        ```JavaScript
        const product = 8 * 10;
        ```
        
        ```JavaScript
        80
        ```
        
    - [Divide One Number by Another with JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/divide-one-number-by-another-with-javascript)
        
        **Разделите одно число на другое с помощью JavaScript**
        
        ```JavaScript
        const quotient = 66 / 33;
        ```
        
        ```JavaScript
        2
        ```
        
    - [Increment a Number with JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/increment-a-number-with-javascript)
        
        **Увеличение числа с помощью JavaScript**
        
        ```JavaScript
        let myVar = 87;
        
        myVar++;
        ```
        
        ```JavaScript
        88
        ```
        
    - [Decrement a Number with JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/decrement-a-number-with-javascript)
        
        **Уменьшить число с помощью JavaScript**
        
        ```JavaScript
        let myVar = 11;
        
        myVar--;
        ```
        
        ```JavaScript
        10
        ```
        
    - [Create Decimal Numbers with JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/create-decimal-numbers-with-javascript)
        
        **Создание десятичных чисел с помощью JavaScript**
        
        ```JavaScript
        const myDecimal = 5.7;
        ```
        
    - [Multiply Two Decimals with JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/multiply-two-decimals-with-javascript)
        
        **Умножение двух десятичных дробей с помощью JavaScript**
        
        ```JavaScript
        const product = 2.0 * 2.5;
        ```
        
        ```JavaScript
        5
        ```
        
    - [Divide One Decimal by Another with JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/divide-one-decimal-by-another-with-javascript)
        
        **Разделение одного десятичного числа на другое с помощью JavaScript**
        
        ```JavaScript
        const quotient = 4.4 / 2.0;
        ```
        
        ```JavaScript
        2.2
        ```
        
    - [Finding a Remainder in JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/finding-a-remainder-in-javascript)
        
        **Поиск остатка в JavaScript**
        
        ```JavaScript
        const remainder = 11 % 3;
        ```
        
        ```JavaScript
        2
        ```
        
    - [Compound Assignment With Augmented Addition](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/compound-assignment-with-augmented-addition)
        
        **Составное присваивание с расширенным сложением**
        
        ```JavaScript
        let a = 3;
        let b = 17;
        let c = 12;
        
        a += 12;
        b += 9;
        c += 7;
        ```
        
        ```JavaScript
        15 26 19
        ```
        
    - [Compound Assignment With Augmented Subtraction](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/compound-assignment-with-augmented-subtraction)
        
        **Составное присваивание с расширенным вычитанием**
        
        ```JavaScript
        let a = 11;
        let b = 9;
        let c = 3;
        
        a -= 6;
        b -= 15;
        c -= 1;
        ```
        
        ```JavaScript
        5 -6 2
        ```
        
    - [Compound Assignment With Augmented Multiplication](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/compound-assignment-with-augmented-multiplication)
        
        **Составное присваивание с расширенным умножением**
        
        ```JavaScript
        let a = 5;
        let b = 12;
        let c = 4.6;
        
        a *= 5;
        b *= 3;
        c *= 10;
        ```
        
        ```JavaScript
        25 36 46
        ```
        
    - [Compound Assignment With Augmented Division](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/compound-assignment-with-augmented-division)
        
        **Составное присваивание с расширенным разделением**
        
        ```JavaScript
        let a = 48;
        let b = 108;
        let c = 33;
        
        a /= 12;
        b /= 4;
        c /= 11;
        ```
        
        ```JavaScript
        4 27 3
        ```
        
    - [Escaping Literal Quotes in Strings](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/escaping-literal-quotes-in-strings)
        
        **Экранирование буквенных кавычек в строках**
        
        ```JavaScript
        const myStr = "I am a \"double quoted\" string inside \"double quotes\"."
        ```
        
        ```JavaScript
        I am a "double quoted" string inside "double quotes".
        ```
        
    - [Quoting Strings with Single Quotes](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/quoting-strings-with-single-quotes)
        
        **Заключение строк в одинарные кавычки**
        
        ```JavaScript
        const myStr = '<a href="http://www.example.com" target="_blank">Link</a>';
        ```
        
        ```JavaScript
        <a href="http://www.example.com" target="_blank">Link</a>
        ```
        
    - [Escape Sequences in Strings](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/escape-sequences-in-strings)
        
        **Escape-последовательности в строках**
        
        |   |   |
        |---|---|
        |**Код**|**Вывод**|
        |`\'`|одинарная кавычка|
        |`\"`|двойная кавычка|
        |`\\`|обратная косая черта|
        |`\n`|новая линия|
        |`\t`|вкладка|
        |`\r`|возврат каретки|
        |`\b`|граница слова|
        |`\f`|подача формы|
        
        |   |   |
        |---|---|
        |**Code**|**Output**|
        |`\'`|single quote|
        |`\"`|double quote|
        |`\\`|backslash|
        |`\n`|newline|
        |`\t`|tab|
        |`\r`|carriage return|
        |`\b`|word boundary|
        |`\f`|form feed|
        
        ```JavaScript
        const myStr = "FirstLine\n\t\\SecondLine\nThirdLine";
        ```
        
        ```JavaScript
        FirstLine
            \SecondLine
        ThirdLine
        ```
        
    - [Concatenating Strings with Plus Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/concatenating-strings-with-plus-operator)
        
        **Объединение строк с помощью оператора +**
        
        ```JavaScript
        const myStr = "This is the start. " + "This is the end.";
        ```
        
        ```JavaScript
        This is the start. This is the end.
        ```
        
    - [Concatenating Strings with the Plus Equals Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/concatenating-strings-with-the-plus-equals-operator)
        
        **Объединение строк с помощью оператора «+=»**
        
        ```JavaScript
        let myStr = "This is the first sentence. ";
        myStr += "This is the second sentence.";
        ```
        
        ```JavaScript
        This is the first sentence. This is the second sentence.
        ```
        
    - [Constructing Strings with Variables](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/constructing-strings-with-variables)
        
        **Создание строк с помощью переменных**
        
        ```JavaScript
        const myName = "Nikita";
        const myStr = "My name is " + myName + " and I am well!";
        ```
        
        ```JavaScript
        My name is Nikita and I am well!
        ```
        
    - [Appending Variables to Strings](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/appending-variables-to-strings)
        
        **Добавление переменных к строкам**
        
        ```JavaScript
        const someAdjective = "difficult";
        let myStr = "Learning to code is ";
        
        myStr += someAdjective
        ```
        
        ```JavaScript
        Learning to code is difficult
        ```
        
    - [Find the Length of a String](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/find-the-length-of-a-string)
        
        **Найдите длину строки**
        
        ```JavaScript
        let lastNameLength = 0;
        const lastName = "Lovelace";
        
        lastNameLength = lastName.length;
        ```
        
        ```JavaScript
        8
        ```
        
    - [Use Bracket Notation to Find the First Character in a String](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-bracket-notation-to-find-the-first-character-in-a-string)
        
        **Используйте нотацию скобок, чтобы найти первый символ в строке**
        
        ```JavaScript
        let firstLetterOfLastName = "";
        const lastName = "Lovelace";
        
        firstLetterOfLastName = lastName[0];
        ```
        
        ```JavaScript
        L
        ```
        
    - [Understand String Immutability](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/understand-string-immutability)
        
        **Понимание неизменности строк**
        
        ```JavaScript
        let myStr = "Jello World";
        myStr = "Hello World";
        ```
        
        ```JavaScript
        Hello World
        ```
        
    - [Use Bracket Notation to Find the Nth Character in a String](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-bracket-notation-to-find-the-nth-character-in-a-string)
        
        **Используйте нотацию скобок, чтобы найти N-й символ в строке**
        
        ```JavaScript
        const lastName = "Lovelace";
        const thirdLetterOfLastName = lastName[2];
        ```
        
        ```JavaScript
        v
        ```
        
    - [Use Bracket Notation to Find the Last Character in a String](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-bracket-notation-to-find-the-last-character-in-a-string)
        
        **Используйте нотацию скобок, чтобы найти последний символ в строке**
        
        ```JavaScript
        const lastName = "Lovelace";
        const lastLetterOfLastName = lastName[lastName.length - 1];
        ```
        
        ```JavaScript
        e
        ```
        
    - [Use Bracket Notation to Find the Nth-to-Last Character in a String](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-bracket-notation-to-find-the-nth-to-last-character-in-a-string)
        
        **Используйте нотацию скобок, чтобы найти N-последний символ в строке**
        
        ```JavaScript
        const lastName = "Lovelace";
        const secondToLastLetterOfLastName = lastName[lastName.length - 2];
        ```
        
        ```JavaScript
        c
        ```
        
    - [Word Blanks](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/word-blanks)
        
        **Пустые слова**
        
        ```JavaScript
        const myNoun = "dog";
        const myAdjective = "big";
        const myVerb = "ran";
        const myAdverb = "quickly";
        
        const wordBlanks = "My " + myAdjective + " " + myNoun + " " + myVerb + " is " + myAdverb + "."
        ```
        
        ```JavaScript
        My big dog ran is quickly.
        ```
        
    - [Store Multiple Values in one Variable using JavaScript Arrays](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/store-multiple-values-in-one-variable-using-javascript-arrays)
        
        **Сохранение нескольких значений в одной переменной с использованием массивов JavaScript**
        
        ```JavaScript
        const myArray = ['Hello', 7];
        ```
        
    - [Nest one Array within Another Array](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/nest-one-array-within-another-array)
        
        **Вложение одного массива в другой массив**
        
        **multi-dimensional array** (многомерный массив)
        
        ```JavaScript
        const myArray = [["myArray"]];
        ```
        
    - [Access Array Data with Indexes](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/access-array-data-with-indexes)
        
        **Доступ к данным массива с помощью индексов**
        
        ```JavaScript
        const myArray = [50, 60, 70];
        const myData = myArray[0]
        ```
        
        ```JavaScript
        50
        ```
        
    - [Modify Array Data With Indexes](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/modify-array-data-with-indexes)
        
        **Изменение данных массива с помощью индексов**
        
        ```JavaScript
        const myArray = [18, 64, 99];
        myArray[0] = 45
        ```
        
        ```JavaScript
        [ 45, 64, 99 ]
        ```
        
    - [Access Multi-Dimensional Arrays With Indexes](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/access-multi-dimensional-arrays-with-indexes)
        
        **Доступ к многомерным массивам с помощью индексов**
        
        ```JavaScript
        const myArray = [
          [1, 2, 3],
          [4, 5, 6],
          [7, 8, 9],
          [[10, 11, 12], 13, 14],
        ];
        
        const myData = myArray[2][1];
        ```
        
        ```JavaScript
        8
        ```
        
    - [Manipulate Arrays With push()](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/manipulate-arrays-with-push)
        
        **Управление массивами с помощью push()**
        
        ```JavaScript
        const myArray = [["John", 23], ["cat", 2]];
        myArray.push(["dog", 3])
        ```
        
        ```JavaScript
        [ [ 'John', 23 ], [ 'cat', 2 ], [ 'dog', 3 ] ]
        ```
        
    - [Manipulate Arrays With pop()](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/manipulate-arrays-with-pop)
        
        **Управление массивами с помощью pop()**
        
        ```JavaScript
        const myArray = [["John", 23], ["cat", 2]];
        const removedFromMyArray = myArray.pop()
        ```
        
        ```JavaScript
        [ 'cat', 2 ]
        ```
        
    - [Manipulate Arrays With shift()](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/manipulate-arrays-with-shift)
        
        **Работа с массивами с помощью shift()**
        
        ```JavaScript
        const myArray = [["John", 23], ["dog", 3]];
        const removedFromMyArray = myArray.shift()
        ```
        
        ```JavaScript
        [ 'John', 23 ]
        ```
        
    - [Manipulate Arrays With unshift()](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/manipulate-arrays-with-unshift)
        
        **Работа с массивами с помощью unshift()**
        
        ```JavaScript
        const myArray = [["John", 23], ["dog", 3]];
        myArray.shift();
        myArray.unshift(["Paul", 35])
        ```
        
        ```JavaScript
        [ [ 'Paul', 35 ], [ 'dog', 3 ] ]
        ```
        
    - [Shopping List](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/shopping-list)
        
        **Список покупок**
        
        ```JavaScript
        const myList = [
          ["Maks", 28],
          ["Niktia,", 23],
          ["Platon", 23],
          ["Danila", 19],
          ["Sergey", 59]
        ];
        ```
        
    - [Write Reusable JavaScript with Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/write-reusable-javascript-with-functions)
        
        **Пишите переиспользуемый JavaScript с помощью функций**
        
        ```JavaScript
        function reusableFunction() {
          console.log("Hi World");
        }
        
        reusableFunction()
        ```
        
        ```JavaScript
        Hi World
        ```
        
    - [Passing Values to Functions with Arguments](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/passing-values-to-functions-with-arguments)
        
        **Передача значений функциям с помощью аргументов**
        
        ```JavaScript
        function functionWithArgs(a, b) {
          console.log(a + b)
        } 
        functionWithArgs(2, 3)
        ```
        
        ```JavaScript
        5
        ```
        
    - [Return a Value from a Function with Return](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/return-a-value-from-a-function-with-return)
        
        **Возврат значения из функции с возвратом**
        
        ```JavaScript
        function timesFive(number) {
          return number * 5
        }
        timesFive(7)
        ```
        
        ```JavaScript
        35
        ```
        
    - [Global Scope and Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-scope-and-functions)
        
        **Глобальная область видимости и функции**
        
        ```JavaScript
        const myGlobal = 10;
        
        function fun1() {
          oopsGlobal = 5;
        }
        
        function fun2() {
          let output = "";
          if (typeof myGlobal != "undefined") {
            output += "myGlobal: " + myGlobal;
          }
          if (typeof oopsGlobal != "undefined") {
            output += " oopsGlobal: " + oopsGlobal;
          }
          console.log(output);
        }
        
        fun1();
        fun2();
        ```
        
        ```JavaScript
        myGlobal: 10 oopsGlobal: 5
        ```
        
    - [Local Scope and Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/local-scope-and-functions)
        
        **Локальная область видимости и функции**
        
        ```JavaScript
        function myLocalScope() {
          const myVar = "Hello"
        
          console.log('inside myLocalScope', myVar);
        }
        
        myLocalScope();
        console.log('outside myLocalScope', myVar);
        ```
        
        ```JavaScript
        inside myLocalScope Hello
        ReferenceError: myVar is not defined
        ```
        
    - [Global vs. Local Scope in Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-vs--local-scope-in-functions)
        
        **Глобальная и локальная область видимости в функциях**
        
        ```JavaScript
        const outerWear = "T-Shirt";
        
        function myOutfit() {
          const outerWear = "sweater";
          return outerWear;
        }
        
        myOutfit();
        ```
        
        ```JavaScript
        sweater
        ```
        
    - [Understanding Undefined Value returned from a Function](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/understanding-undefined-value-returned-from-a-function)
        
        **Понимание неопределенного значения, возвращаемого функцией**
        
        ```JavaScript
        let sum = 0;
        
        function addThree() {
          sum = sum + 3;
        }
        function addFive() {
          sum += 5;
        }
        
        addThree();
        addFive();
        
        console.log(sum);
        ```
        
        ```JavaScript
        8
        ```
        
    - [Assignment with a Returned Value](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/assignment-with-a-returned-value)
        
        **Присваивание с возвращаемым значением**
        
        ```JavaScript
        let processed = 0;
        
        function processArg(num) {
          return (num + 3) / 5;
        }
        
        processed = processArg(7)
        ```
        
        ```JavaScript
        2
        ```
        
    - ==**[Stand in Line](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/stand-in-line)**==
        
        **Стоять в очереди**
        
        ```JavaScript
        function nextInLine(arr, item) {
          arr.push(item)
          return arr.shift();
        }
        
        let testArr = [5,6,7,8,9];
        
        console.log("Before: " + JSON.stringify(testArr));
        console.log(nextInLine(testArr, 1));
        console.log("After: " + JSON.stringify(testArr));
        ```
        
        ```JavaScript
        Before: [5,6,7,8,9]
        5
        After: [6,7,8,9,1]
        ```
        
    - [Understanding Boolean Values](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/understanding-boolean-values)
        
        **Понимание логических значений**
        
        ```JavaScript
        function welcomeToBooleans() {
          return true; 
        }
        
        welcomeToBooleans()
        ```
        
        ```JavaScript
        true
        ```
        
    - [Use Conditional Logic with If Statements](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-conditional-logic-with-if-statements)
        
        **Используйте условную логику с операторами If**
        
        ```JavaScript
        function trueOrFalse(wasThatTrue) {
          if (wasThatTrue) {
            return "Yes, that was true";
          }
          return "No, that was false";
        }
        
        trueOrFalse(true)
        ```
        
        ```JavaScript
        Yes, that was true
        ```
        
    - [Comparison with the Equality Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/comparison-with-the-equality-operator)
        
        **Сравнение с оператором равенства**
        
        ```JavaScript
        function testEqual(val) {
          if (val == 12) { 
            return "Equal";
          }
          return "Not Equal";
        }
        
        testEqual("12");
        ```
        
        ```JavaScript
        Equal
        ```
        
    - [Comparison with the Strict Equality Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/comparison-with-the-strict-equality-operator)
        
        **Сравнение с оператором строгого равенства**
        
        ```JavaScript
        function testStrict(val) {
          if (val === 7) { 
            return "Equal";
          }
          return "Not Equal";
        }
        
        testStrict(10);
        ```
        
        ```JavaScript
        Not Equal
        ```
        
    - [Practice comparing different values](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/practice-comparing-different-values)
        
        **Практика сравнения различных значений**
        
        ```JavaScript
        function compareEquality(a, b) {
          if (a === b) {
            return "Equal";
          }
          return "Not Equal";
        }
        
        compareEquality(10, "10");
        ```
        
        ```JavaScript
        Not Equal
        ```
        
    - [Comparison with the Inequality Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/comparison-with-the-inequality-operator)
        
        **Сравнение с оператором неравенства**
        
        ```JavaScript
        function testNotEqual(val) {
          if (val != 99) { 
            return "Not Equal";
          }
          return "Equal";
        }
        
        testNotEqual(99);
        ```
        
        ```JavaScript
        Equal
        ```
        
    - [Comparison with the Strict Inequality Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/comparison-with-the-strict-inequality-operator)
        
        **Сравнение с оператором строгого неравенства**
        
        ```JavaScript
        function testStrictNotEqual(val) {
          if (val !== 17) { 
            return "Not Equal";
          }
          return "Equal";
        }
        
        testStrictNotEqual("17");
        ```
        
        ```JavaScript
        Not Equal
        ```
        
    - [Comparison with the Greater Than Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/comparison-with-the-greater-than-operator)
        
        **Сравнение с оператором >**
        
        ```JavaScript
        function testGreaterThan(val) {
          if (val > 100) {
            return "Over 100";
          }
          if (val > 10) {
            return "Over 10";
          }
          return "10 or Under";
        }
        
        testGreaterThan(10);
        ```
        
        ```JavaScript
        10 or Under
        ```
        
    - [Comparison with the Greater Than Or Equal To Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/comparison-with-the-greater-than-or-equal-to-operator)
        
        **Сравнение с оператором больше или равно ≥**
        
        ```JavaScript
        function testGreaterOrEqual(val) {
          if (val >= 20) {
            return "20 or Over";
          }
          if (val >= 10) {
            return "10 or Over";
          }
          return "Less than 10";
        }
        
        testGreaterOrEqual(10)
        ```
        
        ```JavaScript
        10 or Over
        ```
        
    - [Comparison with the Less Than Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/comparison-with-the-less-than-operator)
        
        **Сравнение с оператором <**
        
        ```JavaScript
        function testLessThan(val) {
          if (val < 25) {
            return "Under 25";
          }
          if (val < 55) {
            return "Under 55";
          }
          return "55 or Over";
        }
        
        testLessThan(10)
        ```
        
        ```JavaScript
        Under 25
        ```
        
    - [Comparison with the Less Than Or Equal To Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/comparison-with-the-less-than-or-equal-to-operator)
        
        **Сравнение с оператором меньше или равно ≤**
        
        ```JavaScript
        function testLessOrEqual(val) {
          if (val <= 12) {  
            return "Smaller Than or Equal to 12";
          }
          if (val <= 24) {  
            return "Smaller Than or Equal to 24";
          }
          return "More Than 24";
        }
        
        testLessOrEqual(10);
        ```
        
        ```JavaScript
        Smaller Than or Equal to 12
        ```
        
    - [Comparisons with the Logical And Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/comparisons-with-the-logical-and-operator)
        
        **Сравнения с логическим оператором И**
        
        ```JavaScript
        function testLogicalAnd(val) {
          if (val <=50 && val >= 25) {
              return "Yes";
          }
          return "No";
        }
        
        testLogicalAnd(10);
        ```
        
        ```JavaScript
        No
        ```
        
    - [Comparisons with the Logical Or Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/comparisons-with-the-logical-or-operator)
        
        **Сравнения с логическим оператором ||**
        
        ```JavaScript
        function testLogicalOr(val) {
          if (val < 10 || val > 20) {
            return "Outside";
          }
          return "Inside";
        }
        
        testLogicalOr(15);
        ```
        
        ```JavaScript
        Inside
        ```
        
    - [Introducing Else Statements](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/introducing-else-statements)
        
        **Знакомство с операторам Else**
        
        ```JavaScript
        function testElse(val) {
          let result = "";
          if (val > 5) {
            result = "Bigger than 5";
          } else {
            result = "5 or Smaller";
          }
          return result;
        }
        
        testElse(4);
        ```
        
        ```JavaScript
        5 or Smaller
        ```
        
    - [Introducing Else If Statements](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/introducing-else-if-statements)
        
        **Знакомство с операторами Else If**
        
        ```JavaScript
        function testElseIf(val) {
          if (val > 10) {
            return "Greater than 10";
          } else if (val < 5) {
            return "Smaller than 5";
          } else {
            return "Between 5 and 10";
          }
        }
        
        testElseIf(7);
        ```
        
        ```JavaScript
        Between 5 and 10
        ```
        
    - [Logical Order in If Else Statements](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/logical-order-in-if-else-statements)
        
        **Логический порядок в операторах If Else**
        
        ```JavaScript
        function orderMyLogic(val) {
           if (val < 5) {
            return "Less than 5";
          } else if (val < 10) {
            return "Less than 10";
          } else {
            return "Greater than or equal to 10";
          }
        }
        ```
        
        ```JavaScript
        Less than 10
        ```
        
    - [Chaining If Else Statements](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/chaining-if-else-statements)
        
        **Цепочка операторов If Else**
        
        ```JavaScript
        function testSize(num) {
          if (num < 5) {
            return "Tiny";
          } else if (num < 10) {
            return "Small";
          } else if (num < 15) {
            return "Medium";
          } else if (num < 20) {
            return "Large";
          } else if (num >= 20) {
            return "Huge";
          }
        }
        
        testSize(7);
        ```
        
        ```JavaScript
        Small
        ```
        
    - [Golf Code](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/golf-code)
        
        **Гольф-код**
        
        ```JavaScript
        const names = [
          "Hole-in-one!",
          "Eagle",
          "Birdie",
          "Par",
          "Bogey",
          "Double Bogey",
          "Go Home!",
        ];
        
        function golfScore(par, strokes) {
          if (strokes === 1) {
            return names[0];
          } else if (strokes <= par - 2) {
            return names[1];
          } else if (strokes === par - 1) {
            return names[2];
          } else if (strokes === par) {
            return names[3];
          } else if (strokes === par + 1) {
            return names[4];
          } else if (strokes === par + 2) {
            return names[5];
          } else if (strokes >= par + 3) {
            return names[6];
          }
        }
        ```
        
        ```JavaScript
        Birdie
        ```
        
    - [Selecting from Many Options with Switch Statements](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/selecting-from-many-options-with-switch-statements)
        
        **Выбор из множества вариантов с операторами Switch**
        
        ```JavaScript
        function caseInSwitch(val) {
          switch (val) {
            case 1:
              return "alpha";
            case 2:
              return "beta";
            case 3:
              return "gamma";
            case 4:
              return "delta";
          }
        }
        
        caseInSwitch(1);
        ```
        
        ```JavaScript
        alpha
        ```
        
    - [Adding a Default Option in Switch Statements](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/adding-a-default-option-in-switch-statements)
        
        **Добавление параметра по умолчанию в операторы Switch**
        
        ```JavaScript
        function switchOfStuff(val) {
          switch (val) {
            case "a":
              return "apple";
            case "b":
              return "bird";
            case "c":
              return "cat";
            default:
              return "stuff";
          }
        }
        
        switchOfStuff(1)
        ```
        
        ```JavaScript
        stuff
        ```
        
    - [Multiple Identical Options in Switch Statements](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/multiple-identical-options-in-switch-statements)
        
        **Несколько идентичных опций в операторах switch**
        
        ```JavaScript
        function sequentialSizes(val) {
          switch (val) {
            case 1:
            case 2:
            case 3:
              return "Low";
            case 4:
            case 5:
            case 6:
              return "Mid";
            case 7:
            case 8:
            case 9:
              return "High";
          }
        }
        
        sequentialSizes(1);
        ```
        
        ```JavaScript
        Low
        ```
        
    - [Replacing If Else Chains with Switch](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/replacing-if-else-chains-with-switch)
        
        **Замена цепочек If Else на Switch**
        
        ```JavaScript
        function chainToSwitch(val) {
          switch (val) {
            case "bob":
              return "Marley";
            case 42:
              return "The Answer";
            case 1:
              return "There is no \#1";
            case 99:
              return "Missed me by this much!";
            case 7:
              return "Ate Nine";
            default:
              return "";
          }
        }
        
        chainToSwitch(7)
        ```
        
        ```JavaScript
        Ate Nine
        ```
        
    - [Returning Boolean Values from Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/returning-boolean-values-from-functions)
        
        **Возврат логических значений из функций**
        
        ```JavaScript
        function isLess(a, b) {
          return a <= b;
        }
        
        isLess(10, 15);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Return Early Pattern for Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/return-early-pattern-for-functions)
        
        **Возврат ранних шаблонов для функций**
        
        ```JavaScript
        function abTest(a, b) {
          if (a < 0 || b < 0) {
            return undefined;
          }
        
          return Math.round(Math.pow(Math.sqrt(a) + Math.sqrt(b), 2));
        }
        
        abTest(2, 2);
        ```
        
        ```JavaScript
        8
        ```
        
    - [Counting Cards](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/counting-cards)
        
        **Подсчет карт**
        
        ```JavaScript
        let count = 0;
        
        function cc(card) {
          switch (card) {
            case 2:
            case 3:
            case 4:
            case 5:
            case 6:
              count += 1;
              break;
            case 7:
            case 8:
            case 9:
              count += 0;
              break;
            case 10:
            case "J":
            case "Q":
            case "K":
            case "A":
              count -= 1;
              break;
          }
        
          if (count > 0) {
            return `${count} Bet`;
          } else {
            return `${count} Hold`;
          }
        }
        
        cc(2);
        cc(3);
        cc(7);
        cc("K");
        cc("A");
        ```
        
        ```JavaScript
        1 Bet
        2 Bet
        2 Bet
        1 Bet
        0 Hold
        ```
        
    - [Build JavaScript Objects](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/build-javascript-objects)
        
        **Создание объектов JavaScript**
        
        ```JavaScript
        const myDog = {
          name: "Ben",
          legs: 4,
          tails: 1,
          friends: [1]
        };
        ```
        
    - [Accessing Object Properties with Dot Notation](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/accessing-object-properties-with-dot-notation)
        
        **Доступ к свойствам объекта с помощью записи через точку**
        
        ```JavaScript
        const testObj = {
          "hat": "ballcap",
          "shirt": "jersey",
          "shoes": "cleats"
        };
        
        const hatValue = testObj.hat;
        const shirtValue = testObj.shirt;
        ```
        
        ```JavaScript
        ballcap
        jersey
        ```
        
    - [Accessing Object Properties with Bracket Notation](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/accessing-object-properties-with-bracket-notation)
        
        **Доступ к свойствам объекта с помощью нотации скобок**
        
        ```JavaScript
        const testObj = {
          "an entree": "hamburger",
          "my side": "veggies",
          "the drink": "water",
        };
        
        const entreeValue = testObj["an entree"];
        const drinkValue = testObj["the drink"];
        ```
        
        ```JavaScript
        hamburger
        water
        ```
        
    - [Accessing Object Properties with Variables](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/accessing-object-properties-with-variables)
        
        **Доступ к свойствам объекта с помощью переменной**
        
        ```JavaScript
        const testObj = {
          12: "Namath",
          16: "Montana",
          19: "Unitas",
        };
        
        const playerNumber = 16;
        const player = testObj[playerNumber];
        ```
        
        ```JavaScript
        Montana
        ```
        
    - [Updating Object Properties](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/updating-object-properties)
        
        **Обновление свойств объекта**
        
        ```JavaScript
        const myDog = {
          name: "Coder",
          legs: 4,
          tails: 1,
          friends: ["freeCodeCamp Campers"],
        };
        
        myDog.name = "Happy Coder";
        ```
        
        ```JavaScript
        {
          name: 'Happy Coder',
          legs: 4,
          tails: 1,
          friends: [ 'freeCodeCamp Campers' ]
        }
        ```
        
    - [Add New Properties to a JavaScript Object](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/add-new-properties-to-a-javascript-object)
        
        **Добавление новых свойств к объекту JavaScript**
        
        ```JavaScript
        const myDog = {
          name: "Happy Coder",
          legs: 4,
          tails: 1,
          friends: ["freeCodeCamp Campers"],
        };
        
        myDog.bark = "GAFF";
        ```
        
        ```JavaScript
        {
          name: 'Happy Coder',
          legs: 4,
          tails: 1,
          friends: [ 'freeCodeCamp Campers' ],
          bark: 'GAFF'
        }
        ```
        
    - [Delete Properties from a JavaScript Object](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/delete-properties-from-a-javascript-object)
        
        **Удаление свойства из объекта JavaScript**
        
        ```JavaScript
        const myDog = {
          name: "Happy Coder",
          legs: 4,
          tails: 1,
          friends: ["freeCodeCamp Campers"],
          bark: "woof",
        };
        
        delete myDog.tails;
        ```
        
        ```JavaScript
        {
          name: 'Happy Coder',
          legs: 4,
          friends: [ 'freeCodeCamp Campers' ],
          bark: 'woof'
        }
        ```
        
    - [Using Objects for Lookups](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/using-objects-for-lookups)
        
        **Использование объектов для поиска**
        
        ```JavaScript
        function phoneticLookup(val) {
          let result = "";
        
          const lookup = {
            alpha: "Adams",
            bravo: "Boston",
            charlie: "Chicago",
            delta: "Denver",
            echo: "Easy",
            foxtrot: "Frank",
          };
        
          result = lookup[val];
        
          return result;
        }
        
        phoneticLookup("charlie");
        ```
        
        ```JavaScript
        Chicago
        ```
        
    - [Testing Objects for Properties](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/testing-objects-for-properties)
        
        **Проверка объектов на свойства**
        
        ```JavaScript
        function checkObj(obj, checkProp) {
          if (obj.hasOwnProperty(checkProp)) {
            return obj[checkProp];
          } else {
            return "Not Found";
          }
        }
        ```
        
    - [Manipulating Complex Objects](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/manipulating-complex-objects)
        
        **Управление сложными объектами**
        
        ```JavaScript
        const myMusic = [
          {
            artist: "Billy Joel",
            title: "Piano Man",
            release_year: 1973,
            formats: ["CD", "8T", "LP"],
            gold: true,
          },
          {
            artist: "Michael Jackson",
            title: "Thriller",
            release_year: 1982,
            formats: ["CD", "8T", "LP"],
            gold: true,
          },
        ];
        ```
        
    - [Accessing Nested Objects](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/accessing-nested-objects)
        
        **Доступ к вложенным объектам**
        
        ```JavaScript
        const myStorage = {
          "car": {
            "inside": {
              "glove box": "maps",
              "passenger seat": "crumbs"
             },
            "outside": {
              "trunk": "jack"
            }
          }
        };
        
        const gloveBoxContents = myStorage.car.inside["glove box"];
        ```
        
        ```JavaScript
        maps
        ```
        
    - [Accessing Nested Arrays](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/accessing-nested-arrays)
        
        **Доступ к вложенным массивам**
        
        ```JavaScript
        const myPlants = [
          {
            type: "flowers",
            list: [
              "rose",
              "tulip",
              "dandelion"
            ]
          },
          {
            type: "trees",
            list: [
              "fir",
              "pine",
              "birch"
            ]
          }
        ];
        
        const secondTree = myPlants[1].list[1];
        ```
        
        ```JavaScript
        pine
        ```
        
    - [Record Collection](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/record-collection)
        
        **Коллекция записей**
        
        ```JavaScript
        const recordCollection = {
          2548: {
            albumTitle: "Slippery When Wet",
            artist: "Bon Jovi",
            tracks: ["Let It Rock", "You Give Love a Bad Name"],
          },
          2468: {
            albumTitle: "1999",
            artist: "Prince",
            tracks: ["1999", "Little Red Corvette"],
          },
          1245: {
            artist: "Robert Palmer",
            tracks: [],
          },
          5439: {
            albumTitle: "ABBA Gold",
          },
        };
        
        function updateRecords(records, id, prop, value) {
          if (prop !== "tracks" && value !== "") {
            records[id][prop] = value;
          } else if (
            prop === "tracks" &&
            records[id].hasOwnProperty("tracks") === false
          ) {
            records[id][prop] = [value];
          } else if (prop === "tracks" && value !== "") {
            records[id][prop].push(value);
          } else if (value === "") {
            delete records[id][prop];
          }
          return records;
        }
        ```
        
    - [Iterate with JavaScript While Loops](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/iterate-with-javascript-while-loops)
        
        **Итерация с циклами while JavaScript**
        
        ```JavaScript
        const myArray = [];
        let i = 5;
        
        while (i >= 0) {
          myArray.push(i);
          i--;
        }
        ```
        
        ```JavaScript
        [ 5, 4, 3, 2, 1, 0 ]
        ```
        
    - [Iterate with JavaScript While Loops](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/iterate-with-javascript-while-loops)
        
        **Итерация с JavaScript для циклов**
        
        ```JavaScript
        const myArray = [];
        
        for (let i = 1; i <= 5; i++) {
          myArray.push(i);
        }
        ```
        
        ```JavaScript
        [ 1, 2, 3, 4, 5 ]
        ```
        
    - [Iterate with JavaScript For Loops](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/iterate-with-javascript-for-loops)
        
        **Перебор нечетных чисел с помощью цикла for**
        
        ```JavaScript
        const myArray = [];
        
        for (let i = 1; i <= 9; i += 2) {
          myArray.push(i);
        }
        ```
        
        ```JavaScript
        [ 1, 3, 5, 7, 9 ]
        ```
        
    - [Count Backwards With a For Loop](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/count-backwards-with-a-for-loop)
        
        **Расчет в обратном порядке с помощью цикла for**
        
        ```JavaScript
        const myArray = [];
        
        for (let i = 9; i >= 1; i -= 2) {
          myArray.push(i);
        }
        ```
        
        ```JavaScript
        [ 9, 7, 5, 3, 1 ]
        ```
        
    - [Iterate Through an Array with a For Loop](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/iterate-through-an-array-with-a-for-loop)
        
        **Перебор массива с помощью цикла for**
        
        ```JavaScript
        const myArr = [2, 3, 4, 5, 6];
        let total = 0;
        
        for (let i = 0; i < myArr.length; i++) {
          total += myArr[i];
        }
        ```
        
        ```JavaScript
        20
        ```
        
    - [Nesting For Loops](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/nesting-for-loops)
        
        **Вложенные циклов**
        
        ```JavaScript
        function multiplyAll(arr) {
          let product = 1;
        
          for (let i = 0; i < arr.length; i++) {
            for (let j = 0; j < arr[i].length; j++) {
              product *= arr[i][j];
            }
          }
        
          return product;
        }
        ```
        
        ```JavaScript
        5040
        ```
        
    - [Iterate with JavaScript Do...While Loops](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/iterate-with-javascript-do---while-loops)
        
        **Итерация с помощью JavaScript Do...While Loops**
        
        ```JavaScript
        const myArray = [];
        let i = 10;
        
        do {
          myArray.push(i);
          i++;
        } while (i < 5);
        ```
        
        ```JavaScript
        10
        ```
        
    - [Replace Loops using Recursion](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/replace-loops-using-recursion)
        
        **Замена циклов с помощью рекурсии**
        
        ```JavaScript
        function sum(arr, n) {
          if (n <= 0) {
            return 0;
          } else {
            return sum(arr, n - 1) + arr[n - 1];
          }
        }
        
        sum([2, 3, 4, 5], 4)
        ```
        
        ```JavaScript
        14
        ```
        
    - [Profile Lookup](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/profile-lookup)
        
        **Поиск профиля**
        
        ```JavaScript
        function lookUpProfile(name, prop) {
          for (let i = 0; i < contacts.length; i++) {
            if (contacts[i].firstName === name) {
              if (contacts[i].hasOwnProperty(prop)) {
                return contacts[i][prop];
              } else {
                return "No such property";
              }
            }
          }
          return "No such contact";
        }
        
        lookUpProfile("Harry", "likes");
        ```
        
        ```JavaScript
        [ 'Hogwarts', 'Magic', 'Hagrid' ]
        ```
        
    - [Generate Random Fractions with JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/generate-random-fractions-with-javascript)
        
        **Создание случайных дробей с помощью JavaScript**
        
        ```JavaScript
        function randomFraction() {
          return Math.random();
        }
        
        randomFraction();
        ```
        
    - [Generate Random Whole Numbers with JavaScript](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/generate-random-whole-numbers-with-javascript)
        
        **Генерация случайных целых чисел с помощью JavaScript**
        
        ```JavaScript
        function randomWholeNum() {
          return Math.floor(Math.random() * 10);
        }
        
        randomWholeNum()
        ```
        
    - [Generate Random Whole Numbers within a Range](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/generate-random-whole-numbers-within-a-range)
        
        **Генерация случайных целых чисел в диапазоне**
        
        ```JavaScript
        function randomRange(myMin, myMax) {
          return Math.floor(Math.random() * (myMax - myMin + 1)) + myMin;
        }
        
        randomRange(myMin, myMax)
        ```
        
    - [Use the parseInt Function](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-the-parseint-function)
        
        **Использование функции parseInt**
        
        ```JavaScript
        function convertToInteger(str) {
          return parseInt(str);
        }
        
        convertToInteger("56");
        ```
        
        ```JavaScript
        56
        ```
        
    - [Use the parseInt Function with a Radix](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-the-parseint-function-with-a-radix)
        
        **Использование функцию parseInt с основанием**
        
        ```JavaScript
        function convertToInteger(str) {
          return parseInt(str, 2);
        }
        
        convertToInteger("10011");
        ```
        
        ```JavaScript
        19
        ```
        
    - [Use the Conditional (Ternary) Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-the-conditional-ternary-operator)
        
        **Использование условного (тернарного) оператора**
        
        ```JavaScript
        function checkEqual(a, b) {
          return a === b ? "Equal" : "Not Equal";
        }
        
        checkEqual(1, 2);
        ```
        
        ```JavaScript
        Not Equal
        ```
        
    - [Use Multiple Conditional (Ternary) Operators](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-multiple-conditional-ternary-operators)
        
        **Использование несколько условных (тернарных) операторов**
        
        ```JavaScript
        function checkSign(num) {
          return num === 0 ? "zero" : num > 0 ? "positive" : "negative";
        }
        
        checkSign(10);
        ```
        
        ```JavaScript
        positive
        ```
        
    - [Use Recursion to Create a Countdown](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-recursion-to-create-a-countdown)
        
        **Используйте рекурсию для создания обратного отсчета**
        
        ```JavaScript
        function countdown(n) {
          if (n < 1) {
            return [];
          } else {
            const countArray = countdown(n - 1);
            countArray.unshift(n);
            return countArray;
          }
        }
        
        countdown(7)
        ```
        
        ```JavaScript
        [
          7, 6, 5, 4,
          3, 2, 1
        ]
        ```
        
    - [Use Recursion to Create a Range of Numbers](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-recursion-to-create-a-range-of-numbers)
        
        **Используйте рекурсию для создания диапазона чисел**
        
        ```JavaScript
        function rangeOfNumbers(startNum, endNum) {
          if (startNum > endNum) {
            return [];
          } else {
            const array = rangeOfNumbers(startNum, endNum - 1);
            array.push(endNum);
            return array;
          }
        }
        
        rangeOfNumbers(2, 5)
        ```
        
        ```JavaScript
        [ 2, 3, 4, 5 ]
        ```
        
- **ES6**
    - [Compare Scopes of the var and let Keywords](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/compare-scopes-of-the-var-and-let-keywords)
        
        **Сравните области действия переменной let и const**
        
        ```JavaScript
        function checkScope() {
          let i = "function scope";
          if (true) {
            let i = "block scope";
            console.log("Block scope i is: ", i);
          }
          console.log("Function scope i is: ", i);
          return i;
        }
        
        checkScope()
        ```
        
        ```JavaScript
        Block scope i is:  block scope
        Function scope i is:  function scope
        function scope
        ```
        
    - [Mutate an Array Declared with const](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/mutate-an-array-declared-with-const)
        
        **Измените массив, объявленный с помощью const**
        
        ```JavaScript
        const s = [5, 7, 2];
        function editInPlace() {
          s[0] = 2;
          s[1] = 5;
          s[2] = 7;
        
          return s;
        }
        
        editInPlace();
        ```
        
        ```JavaScript
        [ 2, 5, 7 ]
        ```
        
    - [Prevent Object Mutation](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/prevent-object-mutation)
        
        **Предотвратить мутацию объекта**
        
        ```JavaScript
        function freezeObj() {
          const MATH_CONSTANTS = {
            PI: 3.14,
          };
        
          Object.freeze(MATH_CONSTANTS);
        
          try {
            MATH_CONSTANTS.PI = 99;
          } catch (ex) {
            console.log(ex);
          }
          return MATH_CONSTANTS.PI;
        }
        
        const PI = freezeObj();
        ```
        
        ```JavaScript
        3.14
        ```
        
    - [Use Arrow Functions to Write Concise Anonymous Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-arrow-functions-to-write-concise-anonymous-functions)
        
        **Используйте стрелочные функции для написания кратких анонимных функций**
        
        ```JavaScript
        const magic = () => new Date();
        ```
        
    - [Write Arrow Functions with Parameters](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/write-arrow-functions-with-parameters)
        
        **Напишите стрелочные функции с параметрами**
        
        ```JavaScript
        const myConcat = (arr1, arr2) => arr1.concat(arr2);
        myConcat([1, 2], [3, 4, 5])
        ```
        
        ```JavaScript
        [ 1, 2, 3, 4, 5 ]
        ```
        
    - [Set Default Parameters for Your Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/set-default-parameters-for-your-functions)
        
        **Установите параметры по умолчанию для ваших функций**
        
        ```JavaScript
        const increment = (number, value = 1) => number + value;
        
        increment(3)
        ```
        
        ```JavaScript
        4
        ```
        
    - [Use the Rest Parameter with Function Parameters](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-the-rest-parameter-with-function-parameters)
        
        **Используйте параметр Rest с параметрами функции**
        
        ```JavaScript
        const sum = (...args) => {
          return args.reduce((a, b) => a + b, 0);
        };
        
        sum()
        ```
        
        ```JavaScript
        0
        ```
        
    - [Use the Spread Operator to Evaluate Arrays In-Place](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-the-spread-operator-to-evaluate-arrays-in-place)
        
        **Используйте оператор Spread для оценки массивов на месте**
        
        ```JavaScript
        const arr1 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];
        let arr2;
        
        arr2 = [...arr1];
        ```
        
        ```JavaScript
        [ 'JAN', 'FEB', 'MAR', 'APR', 'MAY' ]
        ```
        
    - [Use Destructuring Assignment to Extract Values from Objects](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-destructuring-assignment-to-extract-values-from-objects)
        
        **Используйте присваивание деструктурирования для извлечения значений из объектов**
        
        ```JavaScript
        const HIGH_TEMPERATURES = {
          yesterday: 75,
          today: 77,
          tomorrow: 80
        };
        
        const {today, tomorrow} = HIGH_TEMPERATURES
        ```
        
    - [Use Destructuring Assignment to Assign Variables from Objects](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-destructuring-assignment-to-assign-variables-from-objects)
        
        **Используйте назначение деструктурирования для назначения переменных из объектов**
        
        ```JavaScript
        const HIGH_TEMPERATURES = {
          yesterday: 75,
          today: 77,
          tomorrow: 80,
        };
        
        const { today: highToday, tomorrow: highTomorrow } = HIGH_TEMPERATURES;
        ```
        
    - [Use Destructuring Assignment to Assign Variables from Nested Objects](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-destructuring-assignment-to-assign-variables-from-nested-objects)
        
        **Используйте назначение деструктурирования для назначения переменных из вложенных объектов**
        
        ```JavaScript
        const LOCAL_FORECAST = {
          yesterday: { low: 61, high: 75 },
          today: { low: 64, high: 77 },
          tomorrow: { low: 68, high: 80 },
        };
        
        const {
          today: { low: lowToday, high: highToday },
        } = LOCAL_FORECAST;
        ```
        
    - [Use Destructuring Assignment to Assign Variables from Arrays](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-destructuring-assignment-to-assign-variables-from-arrays)
        
        **Используйте назначение деструктурирования для назначения переменных из массивов**
        
        ```JavaScript
        let a = 8,
          b = 6;
        
        [a, b] = [b, a];
        
        console.log(a, b);
        ```
        
        ```JavaScript
        6 8
        ```
        
    - [Destructuring via rest elements](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-destructuring-assignment-with-the-rest-parameter-to-reassign-array-elements)
        
        **Деструктуризация через остальные элементы**
        
        ```JavaScript
        function removeFirstTwo(list) {
          const [a, b, ...shorterList] = list;
          return shorterList;
        }
        
        const source = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
        const sourceWithoutFirstTwo = removeFirstTwo(source);
        ```
        
        ```JavaScript
        [
          3, 4, 5,  6,
          7, 8, 9, 10
        ]
        ```
        
    - [Use Destructuring Assignment to Pass an Object as a Function's Parameters](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-destructuring-assignment-to-pass-an-object-as-a-functions-parameters)
        
        **Используйте присваивание деструктуризации для передачи объекта в качестве параметров функции**
        
        ```JavaScript
        const stats = {
          max: 56.78,
          standard_deviation: 4.34,
          median: 34.54,
          mode: 23.87,
          min: -0.75,
          average: 35.85,
        };
        
        const half = ({ max, min }) => (max + min) / 2.0;
        
        half(stats)
        ```
        
        ```JavaScript
        28.015
        ```
        
    - [Create Strings using Template Literals](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/create-strings-using-template-literals)
        
        **Создание строк с использованием шаблонных литералов**
        
        ```JavaScript
        const result = {
          success: ["max-length", "no-amd", "prefer-arrow-functions"],
          failure: ["no-var", "var-on-top", "linebreak"],
          skipped: ["no-extra-semi", "no-dup-keys"],
        };
        
        function makeList(arr) {
          let failureItems = [];
        
          for (let i = 0; i < arr.length; i++) {
            failureItems[i] = `<li class="text-warning">${arr[i]}</li>`;
          }
        
          return failureItems;
        }
        
        const failuresList = makeList(result.failure);
        ```
        
        ```JavaScript
        [
          '<li class="text-warning">no-var</li>',
          '<li class="text-warning">var-on-top</li>',
          '<li class="text-warning">linebreak</li>'
        ]
        ```
        
    - [Write Concise Object Literal Declarations Using Object Property Shorthand](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/write-concise-object-literal-declarations-using-object-property-shorthand)
        
        **Напишите краткие литеральные объявления объекта, используя сокращенную запись свойства объекта**
        
        ```JavaScript
        const createPerson = (name, age, gender) => ({ name, age, gender });
        ```
        
    - [Write Concise Declarative Functions with ES6](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/write-concise-declarative-functions-with-es6)
        
        **Пишите краткие декларативные функции с помощью ES6**
        
        ```JavaScript
        const bicycle = {
          gear: 2,
          setGear(newGear) {
            this.gear = newGear;
          },
        };
        
        bicycle.setGear(3);
        console.log(bicycle.gear);
        ```
        
        ```JavaScript
        3
        ```
        
    - [Use class Syntax to Define a Constructor Function](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-class-syntax-to-define-a-constructor-function)
        
        **Используйте синтаксис класса для определения функции конструктора**
        
        ```JavaScript
        class Vegetable {
          constructor(name) {
            this.name = name;
          }
        }
        
        const carrot = new Vegetable("carrot");
        console.log(carrot.name);
        ```
        
        ```JavaScript
        carrot
        ```
        
    - [Use getters and setters to Control Access to an Object](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-getters-and-setters-to-control-access-to-an-object)
        
        **Используйте геттеры и сеттеры для управления доступом к объекту**
        
        ```JavaScript
        class Thermostat {
          constructor(fahrenheit) {
            this.fahrenheit = fahrenheit;
          }
        
          get temperature() {
            return (5 / 9) * (this.fahrenheit - 32);
          }
        
          set temperature(celsius) {
            this.fahrenheit = (celsius * 9.0) / 5 + 32;
          }
        }
        
        const thermos = new Thermostat(76);
        let temp = thermos.temperature;
        console.log(temp);
        thermos.temperature = 26;
        temp = thermos.temperature;
        console.log(temp);
        ```
        
        ```JavaScript
        24.444444444444446
        26
        ```
        
    - [Create a Module Script](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/create-a-module-script)
        
        **Создать сценарий модуля**
        
        ```HTML
        <html>
          <body>
        		<script type="module" src="index.js"></script>
          </body>
        </html>
        ```
        
    - [Use export to Share a Code Block](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use-export-to-share-a-code-block)
        
        **Используйте экспорт, чтобы поделиться блоком кода**
        
        ```JavaScript
        const uppercaseString = (string) => {
          return string.toUpperCase();
        };
        
        const lowercaseString = (string) => {
          return string.toLowerCase();
        };
        
        export { uppercaseString, lowercaseString };
        ```
        
    - [Reuse JavaScript Code Using import](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/reuse-javascript-code-using-import)
        
        **Повторное использование кода JavaScript с помощью импорта**
        
        ```JavaScript
        import { uppercaseString, lowercaseString } from "./string_functions.js";
        
        uppercaseString("hello");
        lowercaseString("WORLD!");
        ```
        
    - [Use * to Import Everything from a File](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/use--to-import-everything-from-a-file)
        
        **Используйте * для импорта всего из файла**
        
        ```JavaScript
        import * as stringFunctions from "./string_functions.js";
        
        stringFunctions.uppercaseString("hello");
        stringFunctions.lowercaseString("WORLD!");
        ```
        
    - [Create an Export Fallback with export default](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/create-an-export-fallback-with-export-default)
        
        **Создайте резервный вариант экспорта с экспортом по умолчанию**
        
        ```JavaScript
        export default function subtract(x, y) {
          return x - y;
        }
        ```
        
    - [Import a Default Export](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/import-a-default-export)
        
        **Импорт экспорта по умолчанию**
        
        ```JavaScript
        import subtract from "./math_functions.js";
        
        subtract(7, 4);
        ```
        
    - [Create a JavaScript Promise](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/create-a-javascript-promise)
        
        **Создайте обещание JavaScript**
        
        ```JavaScript
        const makeServerRequest = new Promise((resolve, reject) => {});
        ```
        
    - [Complete a Promise with resolve and reject](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/complete-a-promise-with-resolve-and-reject)
        
        **Завершите обещание с помощью решения и отклонения**
        
        ```JavaScript
        const makeServerRequest = new Promise((resolve, reject) => {
          let responseFromServer;
        
          if (responseFromServer) {
            resolve("We got the data");
          } else {
            reject("Data not received");
          }
        });
        ```
        
    - [Handle a Fulfilled Promise with then](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/handle-a-fulfilled-promise-with-then)
        
        **Обработайте выполненное обещание с помощью then**
        
        ```JavaScript
        const makeServerRequest = new Promise((resolve, reject) => {
          let responseFromServer = true;
        
          if (responseFromServer) {
            resolve("We got the data");
          } else {
            reject("Data not received");
          }
        });
        
        makeServerRequest.then((result) => {
          console.log(result);
        });
        ```
        
        ```JavaScript
        We got the data
        ```
        
    - [Handle a Rejected Promise with catch](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/handle-a-rejected-promise-with-catch)
        
        **Обработка отклоненного обещания с помощью catch**
        
        ```JavaScript
        const makeServerRequest = new Promise((resolve, reject) => {
          let responseFromServer = false;
        
          if (responseFromServer) {
            resolve("We got the data");
          } else {
            reject("Data not received");
          }
        });
        
        makeServerRequest.catch((error) => {
          console.log(error);
        });
        ```
        
        ```JavaScript
        Data not received
        ```
        
- **Regular Expressions**
    - [Using the Test Method](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/using-the-test-method)
        
        **Использование метода тестирования**
        
        ```JavaScript
        let myString = "Hello, World!";
        let myRegex = /Hello/;
        let result = myRegex.test(myString);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Match Literal Strings](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-literal-strings)
        
        **Совпадение с литеральными строками**
        
        ```JavaScript
        let waldoIsHiding = "Somewhere Waldo is hiding in this text.";
        let waldoRegex = /Waldo/;
        let result = waldoRegex.test(waldoIsHiding);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Match a Literal String with Different Possibilities](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-a-literal-string-with-different-possibilities)
        
        ```JavaScript
        let petString = "James has a pet cat.";
        let petRegex = /dog|cat|bird|fish/;
        let result = petRegex.test(petString);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Ignore Case While Matching](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/ignore-case-while-matching)
        
        **Игнорировать регистр при сопоставлении**
        
        ```JavaScript
        let myString = "freeCodeCamp";
        let fccRegex = /freecodecamp/i;
        let result = fccRegex.test(myString);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Extract Matches](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/extract-matches)
        
        **Извлечь совпадения**
        
        ```JavaScript
        let extractStr = "Extract the word 'coding' from this string.";
        let codingRegex = /coding/;
        let result = extractStr.match(codingRegex);
        ```
        
        ```JavaScript
        [
          'coding',
          index: 18,
          input: "Extract the word 'coding' from this string.",
          groups: undefined
        ]
        ```
        
    - [Find More Than the First Match](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/find-more-than-the-first-match)
        
        **Найдите больше, чем первое совпадение**
        
        ```JavaScript
        let twinkleStar = "Twinkle, twinkle, little star";
        let starRegex = /twinkle/gi;
        let result = twinkleStar.match(starRegex);
        ```
        
        ```JavaScript
        [ 'Twinkle', 'twinkle' ]
        ```
        
    - [Match Anything with Wildcard Period](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-anything-with-wildcard-period)
        
        **Сопоставьте что угодно с точкой подстановки**
        
        ```JavaScript
        let exampleStr = "Let's have fun with regular expressions!";
        let unRegex = /run.|sun.|fun.|pun.|nun.|bun./;
        let result = unRegex.test(exampleStr);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Match Single Character with Multiple Possibilities](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-single-character-with-multiple-possibilities)
        
        **Сопоставьте одного персонажа с несколькими возможностями**
        
        ```JavaScript
        let quoteSample =
          "Beware of bugs in the above code; I have only proved it correct, not tried it.";
        let vowelRegex = /[aeiou]/gi;
        let result = quoteSample.match(vowelRegex);
        ```
        
        ```JavaScript
        [
          'e', 'a', 'e', 'o', 'u', 'i',
          'e', 'a', 'o', 'e', 'o', 'e',
          'I', 'a', 'e', 'o', 'o', 'e',
          'i', 'o', 'e', 'o', 'i', 'e',
          'i'
        ]
        ```
        
    - [Match Letters of the Alphabet](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-letters-of-the-alphabet)
        
        **Совпадение букв алфавита**
        
        ```JavaScript
        let quoteSample = "The quick brown fox jumps over the lazy dog.";
        let alphabetRegex = /[a-z]/gi;
        let result = quoteSample.match(alphabetRegex);
        ```
        
        ```JavaScript
        [
          'T', 'h', 'e', 'q', 'u', 'i', 'c',
          'k', 'b', 'r', 'o', 'w', 'n', 'f',
          'o', 'x', 'j', 'u', 'm', 'p', 's',
          'o', 'v', 'e', 'r', 't', 'h', 'e',
          'l', 'a', 'z', 'y', 'd', 'o', 'g'
        ]
        ```
        
    - [Match Numbers and Letters of the Alphabet](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-numbers-and-letters-of-the-alphabet)
        
        **Совпадение чисел и букв алфавита**
        
        ```JavaScript
        let quoteSample = "Blueberry 3.141592653s are delicious.";
        let myRegex = /[h-s2-6]/gi;
        let result = quoteSample.match(myRegex);
        ```
        
        ```JavaScript
        [
          'l', 'r', 'r', '3', '4',
          '5', '2', '6', '5', '3',
          's', 'r', 'l', 'i', 'i',
          'o', 's'
        ]
        ```
        
    - [Match Single Characters Not Specified](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-single-characters-not-specified)
        
        **Совпадение с отдельными символами, не указанными**
        
        ```JavaScript
        let quoteSample = "3 blind mice.";
        let myRegex = /[^aeiou|0-9]/gi;
        let result = quoteSample.match(myRegex);
        ```
        
        ```JavaScript
        [
          ' ', 'b', 'l',
          'n', 'd', ' ',
          'm', 'c', '.'
        ]
        ```
        
    - [Match Characters that Occur One or More Times](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-characters-that-occur-one-or-more-times)
        
        **Сопоставьте символы, которые встречаются один или несколько раз**
        
        ```JavaScript
        let difficultSpelling = "Mississippi";
        let myRegex = /s+/g;
        let result = difficultSpelling.match(myRegex);
        ```
        
        ```JavaScript
        [ 'ss', 'ss' ]
        ```
        
    - [Match Characters that Occur Zero or More Times](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-characters-that-occur-zero-or-more-times)
        
        **Соответствие символам, которые встречаются ноль или более раз**
        
        ```JavaScript
        let chewieQuote = "Aaaaaaaaaaaaaaaarrrgh!";
        let chewieRegex = /Aa*/;
        let result = chewieQuote.match(chewieRegex);
        ```
        
        ```JavaScript
        [
          'Aaaaaaaaaaaaaaaa',
          index: 0,
          input: 'Aaaaaaaaaaaaaaaarrrgh!',
          groups: undefined
        ]
        ```
        
    - [Find Characters with Lazy Matching](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/find-characters-with-lazy-matching)
        
        **Найдите символы с ленивым сопоставлением**
        
        ```JavaScript
        let text = "<h1>Winter is coming</h1>";
        let myRegex = /<.*?>/;
        let result = text.match(myRegex);
        ```
        
        ```JavaScript
        [
          '<h1>',
          index: 0,
          input: '<h1>Winter is coming</h1>',
          groups: undefined
        ]
        ```
        
    - [Find One or More Criminals in a Hunt](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/find-one-or-more-criminals-in-a-hunt)
        
        **Найдите одного или нескольких преступников на охоте**
        
        ```JavaScript
        let reCriminals = /C+/g;
        ```
        
    - [Match Beginning String Patterns](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-beginning-string-patterns)
        
        **Совпадение с шаблонами начальных строк**
        
        ```JavaScript
        let rickyAndCal = "Cal and Ricky both like racing.";
        let calRegex = /^Cal/;
        let result = calRegex.test(rickyAndCal);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Match Ending String Patterns](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-ending-string-patterns)
        
        **Совпадение с шаблонами конечных строк**
        
        ```JavaScript
        let caboose = "The last car on a train is the caboose";
        let lastRegex = /caboose$/;
        let result = lastRegex.test(caboose);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Match All Letters and Numbers](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-all-letters-and-numbers)
        
        **Сопоставьте все буквы и цифры**
        
        ```JavaScript
        let quoteSample = "The five boxing wizards jump quickly.";
        let alphabetRegexV2 = /\w/g;
        let result = quoteSample.match(alphabetRegexV2).length;
        ```
        
        ```JavaScript
        31
        ```
        
    - [Match Everything But Letters and Numbers](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-everything-but-letters-and-numbers)
        
        **Сопоставьте все, кроме букв и цифр**
        
        ```JavaScript
        let quoteSample = "The five boxing wizards jump quickly.";
        let nonAlphabetRegex = /\W/g;
        let result = quoteSample.match(nonAlphabetRegex).length;
        ```
        
        ```JavaScript
        6
        ```
        
    - [Match All Numbers](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-all-numbers)
        
        **Совпадение со всеми числами**
        
        ```JavaScript
        let movieName = "2001: A Space Odyssey";
        let numRegex = /\d/g;
        let result = movieName.match(numRegex).length;
        ```
        
        ```JavaScript
        4
        ```
        
    - [Match All Non-Numbers](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-all-non-numbers)
        
        **Совпадение со всеми нечисловыми значениями**
        
        ```JavaScript
        let movieName = "2001: A Space Odyssey";
        let noNumRegex = /\D/g;
        let result = movieName.match(noNumRegex).length;
        ```
        
        ```JavaScript
        17
        ```
        
    - [Restrict Possible Usernames](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/restrict-possible-usernames)
        
        **Ограничить возможные имена пользователей**
        
        ```JavaScript
        let username = "JackOfAllTrades";
        let userCheck = /^[a-z]([0-9]{2,}|[a-z]+\d*)$/i; // let userCheck = /^[a-z][a-z]+\d*$|^[a-z]\d\d+$/i;
        let result = userCheck.test(username);
        
        ^- начало ввода
        [a-z]- первый символ - буква
        [0-9]{2,}- оканчивается двумя и более цифрами
        |- или
        [a-z]+- имеет одну или несколько букв рядом
        \d*- и заканчивается нулем или более цифр
        $- конец ввода
        i- игнорировать регистр ввода
        ///
        ^- начало ввода
        [a-z]- первый символ - буква
        [a-z]+- следующие символы являются буквами
        \d*$- ввод заканчивается 0 или более цифрами
        |- или
        ^[a-z]- первый символ - буква
        \d\d+- следующие символы состоят из 2 или более цифр
        $- конец ввода
        ```
        
    - [Match Whitespace](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-whitespace)
        
        **Совпадение с пробелами**
        
        ```JavaScript
        let sample = "Whitespace is important in separating words";
        let countWhiteSpace = /\s/g;
        let result = sample.match(countWhiteSpace);
        ```
        
        ```JavaScript
        [ ' ', ' ', ' ', ' ', ' ' ]
        ```
        
    - [Match Non-Whitespace Characters](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-non-whitespace-characters)
        
        **Совпадение с непробельными символами**
        
        ```JavaScript
        let sample = "Whitespace is important in separating words";
        let countNonWhiteSpace = /\S/g;
        let result = sample.match(countNonWhiteSpace);
        ```
        
        ```JavaScript
        [
          'W', 'h', 'i', 't', 'e', 's', 'p',
          'a', 'c', 'e', 'i', 's', 'i', 'm',
          'p', 'o', 'r', 't', 'a', 'n', 't',
          'i', 'n', 's', 'e', 'p', 'a', 'r',
          'a', 't', 'i', 'n', 'g', 'w', 'o',
          'r', 'd', 's'
        ]
        ```
        
    - [Specify Upper and Lower Number of Matches](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/specify-upper-and-lower-number-of-matches)
        
        **Укажите верхнее и нижнее количество совпадений**
        
        ```JavaScript
        let ohStr = "Ohhh no";
        let ohRegex = /Oh{3,6}\sno/;
        let result = ohRegex.test(ohStr);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Specify Only the Lower Number of Matches](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/specify-only-the-lower-number-of-matches)
        
        **Укажите только меньшее количество совпадений**
        
        ```JavaScript
        let haStr = "Hazzzzah";
        let haRegex = /Haz{4,}ah/;
        let result = haRegex.test(haStr);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Specify Exact Number of Matches](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/specify-exact-number-of-matches)
        
        **Укажите точное количество совпадений**
        
        ```JavaScript
        let timStr = "Timmmmber";
        let timRegex = /Tim{4}ber/;
        let result = timRegex.test(timStr);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Check for All or None](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/check-for-all-or-none)
        
        **Проверить все или ничего**
        
        ```JavaScript
        let favWord = "favorite";
        let favRegex = /favou?rite/; 
        let result = favRegex.test(favWord);
        ```
        
        ```JavaScript
        true
        ```
        
    - [Positive and Negative Lookahead](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/positive-and-negative-lookahead)
        
        **Положительный и отрицательный взгляд вперед**
        
        ```JavaScript
        let sampleWord = "astronaut";
        let pwRegex = /(?=\w{6})(?=\w*\d{2})/;
        let result = pwRegex.test(sampleWord);
        ```
        
    - [Positive and Negative Lookahead](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/positive-and-negative-lookahead)
        
        **Проверьте наличие смешанной группировки символов**
        
        ```JavaScript
        let myString = "Eleanor Roosevelt";
        let myRegex = /(Franklin|Eleanor) (([A-Z]\.?|[A-Z][a-z]+) )?Roosevelt/g;
        let result = myRegex.test(myString);
        ```
        
    - [Reuse Patterns Using Capture Groups](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/reuse-patterns-using-capture-groups)
        
        **Повторное использование шаблонов с помощью групп захвата**
        
        ```JavaScript
        let repeatNum = "42 42 42";
        let reRegex = /^(\d+) \1 \1$/; 
        let result = reRegex.test(repeatNum);
        ```
        
    - [Use Capture Groups to Search and Replace](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/use-capture-groups-to-search-and-replace)
        
        **Используйте группы захвата для поиска и замены**
        
        ```JavaScript
        let str = "one two three";
        let fixRegex = /(\w+)\s(\w+)\s(\w+)/;
        let replaceText = "$3 $2 $1";
        let result = str.replace(fixRegex, replaceText);
        ```
        
        ```JavaScript
        three two one
        ```
        
    - [Remove Whitespace from Start and End](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/remove-whitespace-from-start-and-end)
        
        **Удалить пробелы в начале и конце**
        
        ```JavaScript
        let hello = "   Hello, World!  ";
        let wsRegex = /^\s+|\s+$/g;
        let result = hello.replace(wsRegex, "");
        ```
        
        ```JavaScript
        Hello, World!
        ```
        
- **Debugging**
    - [Use the JavaScript Console to Check the Value of a Variable](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/use-the-javascript-console-to-check-the-value-of-a-variable)
        
        **Используйте консоль JavaScript для проверки значения переменной**
        
        ```JavaScript
        let a = 5;
        let b = 1;
        a++;
        
        console.log(a)
        
        let sumAB = a + b;
        console.log(sumAB);
        ```
        
        ```JavaScript
        6
        7
        ```
        
    - [Understanding the Differences between the freeCodeCamp and Browser Console](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/understanding-the-differences-between-the-freecodecamp-and-browser-console)
        
        **Понимание различий между freeCodeCamp и консолью браузера**
        
        ```JavaScript
        let output = "Get this to show once in the freeCodeCamp console and not at all in the browser console";
        
        console.log(output)
        console.clear()
        ```
        
    - [Use typeof to Check the Type of a Variable](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/use-typeof-to-check-the-type-of-a-variable)
        
        **Используйте typeof для проверки типа переменной**
        
        ```JavaScript
        let seven = 7;
        let three = "3";
        console.log(seven + three);
        console.log(typeof seven)
        console.log(typeof three)
        ```
        
        ```JavaScript
        73
        number
        string
        ```
        
    - [Catch Misspelled Variable and Function Names](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/catch-misspelled-variable-and-function-names)
        
        **Отлавливайте имена переменных и функций с ошибками**
        
        ```JavaScript
        let receivables = 10;
        let payables = 8;
        let netWorkingCapital = receivables - payables;
        console.log(`Net working capital is: ${netWorkingCapital}`);
        ```
        
        ```JavaScript
        Net working capital is: 2
        ```
        
    - [Catch Unclosed Parentheses, Brackets, Braces and Quotes](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/catch-unclosed-parentheses-brackets-braces-and-quotes)
        
        **Поймать незакрытые круглые скобки, квадратные скобки, фигурные скобки и кавычки**
        
        ```JavaScript
        let myArray = [1, 2, 3];
        let arraySum = myArray.reduce((previous, current) =>  previous + current);
        console.log(`Sum of array values is: ${arraySum}`);
        ```
        
        ```JavaScript
        Sum of array values is: 6
        ```
        
    - [Catch Mixed Usage of Single and Double Quotes](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/catch-mixed-usage-of-single-and-double-quotes)
        
        **Улавливайте смешанное использование одинарных и двойных кавычек**
        
        ```JavaScript
        let innerHtml = "<p>Click here to <a href='\#Home'>return home</a></p>";
        console.log(innerHtml);
        ```
        
        ```JavaScript
        <p>Click here to <a href='\#Home'>return home</a></p>
        ```
        
    - [Catch Use of Assignment Operator Instead of Equality Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/catch-use-of-assignment-operator-instead-of-equality-operator)
        
        **Отловить использование оператора присваивания вместо оператора равенства**
        
        ```JavaScript
        let x = 7;
        let y = 9;
        let result = "to come";
        
        if(x === y) {
          result = "Equal!";
        } else {
          result = "Not equal!";
        }
        
        console.log(result);
        ```
        
        ```JavaScript
        Not equal!
        ```
        
    - [Catch Missing Open and Closing Parenthesis After a Function Call](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/catch-missing-open-and-closing-parenthesis-after-a-function-call)
        
        **Поймать пропущенные открытые и закрывающие скобки после вызова функции**
        
        ```JavaScript
        function getNine() {
          let x = 6;
          let y = 3;
          return x + y;
        }
        
        let result = getNine();
        console.log(result);
        ```
        
        ```JavaScript
        9
        ```
        
    - [Catch Arguments Passed in the Wrong Order When Calling a Function](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/catch-arguments-passed-in-the-wrong-order-when-calling-a-function)
        
        **Перехват аргументов, переданных в неправильном порядке при вызове функции**
        
        ```JavaScript
        function raiseToPower(b, e) {
          return Math.pow(b, e);
        }
        
        let base = 2;
        let exp = 3;
        let power = raiseToPower(base, exp);
        console.log(power);
        ```
        
        ```JavaScript
        8
        ```
        
    - [Catch Off By One Errors When Using Indexing](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/catch-off-by-one-errors-when-using-indexing)
        
        **Отлавливайте по одной ошибки при использовании индексации**
        
        ```JavaScript
        function countToFive() {
          let firstFive = "12345";
          let len = firstFive.length;
          for (let i = 0; i < len; i++) {
            console.log(firstFive[i]);
          }
        }
        
        countToFive();
        ```
        
        ```JavaScript
        1
        2
        3
        4
        5
        ```
        
    - [Use Caution When Reinitializing Variables Inside a Loop](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/use-caution-when-reinitializing-variables-inside-a-loop)
        
        **Будьте осторожны при повторной инициализации переменных внутри цикла**
        
        ```JavaScript
        function zeroArray(m, n) {
          let newArray = [];
          for (let i = 0; i < m; i++) {
            let row = [];
        
            for (let j = 0; j < n; j++) {
              row.push(0);
            }
            newArray.push(row);
          }
          return newArray;
        }
        
        let matrix = zeroArray(3, 2);
        console.log(matrix);
        ```
        
        ```JavaScript
        [ [ 0, 0 ], [ 0, 0 ], [ 0, 0 ] ]
        ```
        
    - [Prevent Infinite Loops with a Valid Terminal Condition](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging/prevent-infinite-loops-with-a-valid-terminal-condition)
        
        **Предотвращение бесконечных циклов с допустимым терминальным условием**
        
        ```JavaScript
        function myFunc() {
          for (let i = 1; i <= 4; i += 2) {
            console.log("Still going!");
          }
        }
        
        myFunc()
        ```
        
        ```JavaScript
        Still going!
        Still going!
        ```
        
- **Basic Data Structures**
- **Basic Algorithm Scripting**
- **Object Oriented Programming**
- **Functional Programming**
- **Intermediate Algorithm Scripting**
- **JavaScript Algorithms and Data Structures Projects**