---
title: JavaScript变量声明和提升
date: 2025-09-09
categories: [ 前端, JavaScript ]
tags: [ JavaScript ]
mermaid: true
---

## 声明方式

JavaScript 有三种变量声明方式。

**var**声明一个变量，可选择将其初始化为一个值。

**let**声明一个块级作用域的局部变量，可选择将其初始化为一个值。

**const**声明一个块级作用域的只读命名常量。

## 初始化

在 let x = 42 这样的语句中，let x 称作声明，= 42称作初始化器。声明允许在后续的代码中访问变量时不会抛出 ReferenceError，而初始化器会给变量赋值。在 var 和 let 声明中，初始化器是可选的。如果声明变量时没有进行初始化，变量会被赋值为 undefined。

const 声明总是需要初始化器，因为它们禁止在声明后进行任何类型的赋值，以及隐式地将其初始化为 undefined 很可能是程序员犯的错。

## 作用域

一个变量可能属于下列作用域之一：

**全局作用域**：在脚本模式中运行的所有代码的默认作用域。

**模块作用域**：在模块模式中运行的代码的作用域。

**函数作用域**：由函数创建的作用域。
此外，用 let 或 const 声明的变量属于另一个作用域：

**块级作用域**：用一对花括号创建的作用域（块）。
当你在函数的外部声明变量时，该变量被称作全局变量，因为当前文档中任何其他代码都能使用它。当你在函数内声明变量时，该变量被称作局部变量，因为它仅在那个函数内可用。

let 和 const 声明也会被限制在声明所在的块语句中。

## 提升

变量提升是 JavaScript 的一个行为，其中变量和函数的声明被提升到其所在作用域的顶部。换句话说，无论变量或函数在代码中的位置如何，它们都可以在声明之前使用。

对于var声明的变量，提升意味着变量声明被提升到其作用域的顶部，但初始化不会被提升。这意味着在变量声明之前访问该变量会返回 undefined，而不是抛出错误。

```js
console.log(x); // 输出: undefined
var x = 5;
console.log(x); // 输出: 5
```

对于let和const声明的变量，提升行为有所不同。虽然它们的声明也被提升到作用域的顶部，但它们不会被初始化。这意味着在变量声明之前访问该变量会抛出ReferenceError。这种行为被称为“暂时性死区”（Temporal Dead Zone, TDZ）。

```js
console.log(y); // 抛出 ReferenceError
let y = 10;
console.log(y); // 输出: 10
```

函数声明也会被提升，这意味着你可以在函数声明之前调用该函数。函数的提升不仅包括声明，还包括函数体。

## 参考

- [MDN - 语法与类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Grammar_and_types)
- [MDN - 变量提升](https://developer.mozilla.org/zh-CN/docs/Glossary/Hoisting)
