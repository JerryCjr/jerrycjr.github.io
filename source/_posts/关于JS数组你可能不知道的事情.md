---
title: 关于JS数组你可能不知道的事情
date: 2019-07-23 23:31:50
tags:
  - JavaScript
categories: Web
---
## 类数组

JavaScript 提供是类数组（array-like）特性的对象

## 长度

1. length属性的值是一个0-2^32-1的整数
2. 设置更大的length不会给数组分配更多的空间 而把length设小将导致所有下表大于等于新length的属性被删除

```javascript
// 这两种写法都可以
number[’numbers.length] = ’shi’; // 这种性能是不是会更好一点？
numbers.push(‘go);
```

## 删除

```javascript
delete numbers[2]; // 可以用delete运算符
// numbers 是 [‘zero’, ‘one’, undefined, ’shi’, ‘go’]

numbers.splice(2, 1); // 也可以用splice 一般用这个
// numbers 是 [‘zero’, ‘one’, ’shi’, ‘go’]
// 因为被删除属性后面的每个属性必须被移除，并且以一个新的键值重新插入，这对于大型数组来说可能会效率不高。--这个需要注意下
```

## 区分对象和数组

```javascript
if (!Array.isArray) {
  Array.isArray = function(arg) {
    return Object.prototype.toString.call(arg) === '[object Array]';
  };
}
// 鲜为人知的事实：其实 Array.prototype 也是一个数组。
Array.isArray(Array.prototype);
```

## 指定初始值

### 一维数组指定初始值

```javascript
Array.dim = function (dimension, initial) {
  let arr = [];
  for (let i = 0; i < dimension; i++) {
    arr[i] = initial;
  }
  return arr;
}

var myArray = Array.dim(10, 1);
var myArray2 = Array.dim(10, []); // 注意这样会导致变量都指向一个数组的引用 后果不堪设想
// console.log(myArray);
// console.log(myArray2);
myArray2[3][9] = 1; // 不堪设想的后果
// console.log(myArray2); // 后果不堪设想了
```

### 二维数组指定初始值

```javascript
if (!Array.isArray) {
  Array.isArray = function (arg) {
    return Object.prototype.toString.call(arg) === '[object Array]';
  };
}

Array.dim = function (m, n, initial) {
  let r = [];
  for (let i = 0; i < m; i++) {
    r[i] = [];
    for (let j = 0; j < n; j++) {
      if (typeof initial === 'object') {
        if (Array.isArray(initial)) {
          r[i][j] = [ ...initial ];
        } else {
          r[i][j] = { ...initial };
        }
      } else {
        r[i][j] = initial;
      }
    }
  }
  return r;
}

let myArray = Array.dim(10, 20, 0);
let myArray2 = Array.dim(10, 20, [9, 10]);
let myArray3 = Array.dim(10, 20, { abc: 1 });
myArray[0][1] = 9;
myArray2[1][2][10] = 10;
myArray3[1][2][0] = 1;
// console.log(myArray);
// console.log(myArray2);
// console.log(myArray3);
```

#### 实现单位矩阵

``` javascript
Array.identity = function (n) {
  let mat = Array.dim(n, n, 0);
  for (let index = 0; index < n; index++) {
    mat[index][index] = 1;
  }
  return mat;
}

let myArray4 = Array.identity(4);
console.log(myArray4);
```
