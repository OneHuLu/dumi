---
nav:
  title: JavaScript
---

# 什么是类数组？如何转换为数组？

### 什么是类数组

- 类数组是一种对象，具有数组的特征，但是不是真正的数组，并且不可以使用数组方法。列如： 一些具有 length 属性的，并且可以通过索引访问其元素，但它们通常不具备数组的方法（如 push、pop、slice 等）。
- 常见的类数组：
  - DOM 元素列表（例如使用 document.querySelectorAll 返回的 NodeList 对象）
  - 函数的 arguments 对象
  - document.forms

```javascript
const arrayLike = {
  0: 'a',
  1: 'b',
  2: 'c',
  length: 3,
};

// 遍历类数组对象
for (var i = 0; i < arrayLike.length; i++) {
  console.log(arrayLike[i]); // 输出 'a', 'b', 'c'
}

// 尝试使用数组方法会出错
// arrayLike.push('d'); // TypeError: arrayLike.push is not a function
```

### 如何转换为数组

- Array.from(): 可以从类数组对象或可迭代对象中创建一个新的数组实例。

```javascript
const arrayLike = { 0: 'a', 1: 'b', 2: 'c', length: 3 };
const array = Array.from(arrayLike);
console.log(array); // 输出 ["a", "b", "c"]
```

- Array.prototype.slice.call(): 通过调用数组的 slice 方法，并将类数组对象作为参数传递给它，可以将类数组对象转换为数组。

```javascript
const arrayLike = { 0: 'a', 1: 'b', 2: 'c', length: 3 };
const array = Array.prototype.slice.call(arrayLike);
console.log(array); // 输出 ["a", "b", "c"]
```

- 遍历： 遍历类数组对象，并逐个将元素添加到新数组中

```javascript
const arrayLike = { 0: 'a', 1: 'b', 2: 'c', length: 3 };
const array = [];
for (let i = 0; i < arrayLike.length; i++) {
  array.push(arrayLike[i]);
}
console.log(array); // 输出 ["a", "b", "c"]
```
