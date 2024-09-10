Задачи
1. В функции logArrayInfo вместо перебора через forEach пробежаться через цикл for of   
 ``` 
  async function logArrayInfo(array) {
    for (const item of array) {
        await logWithDelay(item);
    }
    console.log('Done!');
}
```
- Можно исправить через map и указать в метод Promise all 
```
async function logArrayInfo(array) {
    const promises = array.map(async (item) => {
        await logWithDelay(item);
    });
    await Promise.all(promises);
    console.log('Done!');
}
```

2. Данный код создаст массив из котиков. Каждая функция в массиве должна вывести свой порядковый номер, но что то пошло не
так и все кошки говорят, что их номер 10. Почему у всех кошек одинаковые номера? Исправьте код, чтобы он работал как
задумано.
- Решить через замыкание: 
```
function createCats() {
    let cats = [];
    let i = 0;
    while (i < 10) {
        let cat = function(index) {
            return function() {
                console.log(`My index is ${index}`);
            };
        }(i);
        cats.push(cat);
        i++;
    }
    return cats;
}
```

3. Необходимо найти сумму всех вершин, значение которых кратно 2
- Решаем через стэк:

```
const getSumTwoValue = (tree) => {
    const stack = [tree];
    let sum = 0;
    while (stack.length > 0) {
        const node = stack.pop();
        if (node.value % 2 === 0) {
            sum += node.value;
        }
        if (node.children.length > 0) {
            stack.push(...node.children);
        }
    }
    return sum;
};
```
