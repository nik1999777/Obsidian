В данном коде мы создали класс `SmallestIntegerFinder` с методом `findSmallestInt()` - который находит наименьшее значение и возвращает его.

В данном решении:

- использовался метод сортирвки массива - **selection sort** (сортировка выбором)

```JavaScript
class SmallestIntegerFinder {
  findSmallestInt(args) {
    for (let i = 0; i < args.length; i++) {
      let indexMin = i;
      for (let j = i + 1; j < args.length; j++) {
        if (args[indexMin] > args[j]) {
          indexMin = j;
        }
      }

      if (indexMin !== i) {
        [args[i], args[indexMin]] = [args[indexMin], args[i]];
      }
    }

    return args[0];
  }
}

SmallestIntegerFinder.prototype.findSmallestInt([34, 15, 88, 2]);
```

В данном решении:

- использовали встроенный объекта `Math` с его методом `min()`

```JavaScript
class SmallestIntegerFinder {
  findSmallestInt(args) {
    return Math.min(...args)
  }
}
```

В данном решении:

- использовали метод `sort()`

```JavaScript
class SmallestIntegerFinder {
  findSmallestInt(args) {
    args.sort((a, b) => a - b);
    return args[0];
  }
}

SmallestIntegerFinder.prototype.findSmallestInt([34, 15, 88, 2]);
```