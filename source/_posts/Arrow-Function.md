---
title: Arrow Function
date: 2019-07-17 23:54:05
tags:
  - ES6
categories: Web
---

### 简介

箭头函数允许我们用更简单的方式书写函数表达式

> **之前:**

```javascript
  hello = function() {
    return "hello world!";
  }
```

> **使用箭头函数之后:**

```javascript
  hello = () => {
    return "hello world!";
  }
```

表达式变得更加简短简洁！如果函数只有一个声明，而且声明返回了一个值，你可以移除花括号和return这个关键字

> **箭头函数默认返回值**

```javascript
  hello = () => "hello world!";
```

注意：在函数只有一个声明的情况下才适用

如果有参数的情况下，你需要把参数传递到括号中

> **带参数的箭头函数**

```javascript
  hello = (val) => "hello" + val;
```

> **事实上，如果只有一个参数的情况下，你也可以省略括号**

```javascript
  hello = val => "hello" + val;
```

---

### 谈谈 this

相对于普通函数来讲，箭头函数对 [this] 的处理是不同的。

简而言之，箭头函数在使用时并没有对 [this] 进行绑定。

在普通的函数中 [this] 关键字代表了调用函数的对象，这个对象可能是window，document，一个button按钮或别的。

使用箭头函数的时候 [this] 关键字代表了定义箭头函数的对象。

让我们用两个例子来理解这个区别。

两个例子都调用了同一个方法两次，第一次调用是在页面加载的时候(loads)，第二次是当用户点击一个按钮的时候。

第一个例子用了一个普通的函数，第二个例子用了箭头函数。

结果表明，第一个例子返回了两个不同的对象(window and button),第二个例子返回了两次window对象，因为window对象是箭头函数的所有者。

> Example
> 普通函数中，[this] 指向 ***调用*** 函数的对象

```javascript
  // 普通函数
  hello = function() => {
    document.getElementById("demo").innerHTML += this;
  }

  // window对象调用了这个函数
  window.addEventListener("load", hello);

  // button对象调用了这个函数
  document.getElementById("btn").addEventListener("click", hello);
```

> Example
> 箭头函数中，[this] 指向 ***调用*** 函数的所有者

```javascript
  // 箭头函数
  hello = () => {
    document.getElementById("demo").innerHTML += this;
  }

  // window对象调用了这个函数
  window.addEventListener("load", hello);

  // button对象调用了这个函数
  document.getElementById("btn").addEventListener("click", hello);
```

当你用函数的时候记住这些不同。有时候普通函数的行为是你想要的，如果不是，用箭头函数。

[Arrow Function | w3school](https://www.w3schools.com/js/js_arrow_function.asp)
