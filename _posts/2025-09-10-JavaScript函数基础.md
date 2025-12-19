---
title: JavaScript函数基础
date: 2025-09-10
categories: [ 前端, JavaScript ]
tags: [ JavaScript ]
mermaid: true
---

## 函数声明和定义

一个函数定义（也称为函数声明，或函数语句）由 function 关键字，并跟随以下部分组成：

* 函数名称。
* 函数参数列表，包围在括号中并由逗号分隔。
* 定义函数的 JavaScript 语句，用大括号括起来，{ /*…*/ }。

```javaScript
function add(x, y) {
  return x + y;
}
```

### 参数传递

JavaScript 函数参数按值传递。这意味着函数接收参数值的副本，而不是参数本身。在函数内部对参数的修改不会影响传递给函数的原始值。

如果将对象做为参数传递给函数，则传递的是对象引用的副本。这意味着在函数内部对对象属性的修改会影响原始对象.

### 函数表达式

函数可以由函数表达式定义。函数表达式可以是命名的或匿名的，并且可以作为参数传递给其他函数，或赋值给变量。

```javaScript
const multiply = function(x, y) {
  return x * y;
};

const divide = function divide(x, y) {
  return x / y;
};
```

### 箭头函数

箭头函数提供了一种更简洁的函数表达式语法。它们使用箭头符号 (=>) 来分隔参数和函数体。

```javaScript
const subtract = (x, y) => {
    return x - y;
};
```

> 箭头函数与普通函数的区别:
>
> * 简洁
> * 没有自己的 this:箭头函数没有自己的 this，而是使用封闭执行上下文的 this 值。
>
