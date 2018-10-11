# Difference between Splice Slice and Split functions in JavaScript

## 消除对于JavaScript中Splice,Slice和Split方法的困惑

> 可能是因为`Splice`,`Slice`,`Split`三种常见的JavaScript方法名称非常类似的原因,这三个方法的使用场景和操作方式经常被开发者混淆

> 希望本文撰写完成后可巩固自身对三种方法的理解

### JavaScript的数组

> JavaScript允许在同一个数组中容纳不同类型的元素,数组可以通过如下方式声明

```javascript
let arrayDefinition = [];   // Array declaration in JS
```

> 对于包含不同类型元素的数组,也可以简单地声明

```javascript
let array = [1, 2, 3, "hello world", 4.12, true];
```

### Slice方法

> `slice()`方法复制给定部分的数组,并将复制的部分作为新数组返回

> `slice()`方法不会修改原数组

```bash
array.slice(from, until);
```

- from:从元素索引开始切割数组
- until:将数组切歌至直到另一个元素索引

> 假设希望切割数组的前三个元素

```javascript
let array = [1,2,3,4,5];
let newArray = array.slice(0,3);
console.log(newArray);
// 1,2,3
```

> 值得注意的是unitl所在索引所代表的元素并不包含在被切割的数组中,亦即前包后不包原则

> `slice()`方法也可以用于String类型的变量

```javascript
let testString = '12345';
let newString = testString.slice(0,3);
console.log(newString);
// 123
```

### Splice方法

> `splice()`方法通过修改或删除元素的方式修改原数组

#### 移除元素

```bash
array.splice(index, number_of_elements);
```

- index是删除元素的起点,索引编号小于index的元素将不会被删除
- number_of_elements是将被删除的元素的个数

```javascript
array.splice(2);  // 索引大于等于2的元素都将会被删除
```

> 需要注意的是,如果不添加参数`number_of_elements`,所有从给定的索引位置开始的元素都贱会被删除

```javascript
let array = [1,2,3,'hello',4.5,true];
let deletedArray = array.splice(2,1,);
console.log(deletedArray) //[3]
console.log(array) // [1,2,'hello',4.5,true]
```

> 在存在第二个参数的情况下,将会从指定索引位置开始删除指定量个元素,循环调用时将会在给定的索引目录本身元素不存在时结束

### 增加元素

> 需要添加元素时,需要向`splice()`方法提供可能存在的第三,第四...第n个元素

> 假设希望在数组的开头增加`a`,`b`两个元素

```javascript
let array = [1,2,3,'hello',4.5,true];
array.splice(0,0,'a','b');
// 增加元素的操作将会返回空数组
console.log(array);
// [a,1,2,3,'hello',4.5,true]
```

## Split方法

> 相较之于`splice()`和`slice()`方法大多数情况下作用于Array类型的情况下, `split()`方法只能作用于String类型的变量上

> `split()`方法将一个字符串分成子串并将它们组合为数组返回

```bash
string.split(separator, limit);
```

- separator: 定义了以什么方式分割字符串
- limit: 定义了分割的次数

```javascript
let array = [1,2,3,'hello',4.5,true];
let myString = array.toString();
// myString '1,2,3,hello,4.5,true'
let newArray = myString.split(",", 3);
// newArray ['1','2','3']
```

> myString以`,`为标准切割字符串并保留前三个元素

> 值得注意的是,如果使用`myString.split("")` 切割字符串,字符串将会以每个字符为分割线将每个字符作为一个子字符串切割

## 总结

- Slice()

1. 从数组中拷贝元素
2. 返回新数组
3. 不修改原数组
4. 前包尾不包的切割方式
5. 既可以应用于数组也可以应用于字符串

- Splice()

1. 向数组中添加或删除元素
2. 删除时返回被删除的元素构成的数组
3. 添加时返回空数组
4. 修改原数组
5. 只可以应用于数组类型变量

- Spilt()

1. 将字符串变量拆分为字串数组
2. 返回值为数组类型
3. 包含两个可选参数`separator`和`limit`
4. 不会需改原字串
5. 只可以应用于字符串类型