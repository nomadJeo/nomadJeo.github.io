---
title: JavaScript循环与迭代
date: 2025-09-10
categories: [ 前端, JavaScript ]
tags: [ JavaScript ]
mermaid: true
order: 304
---

## for...in语句

for...in 语句循环一个指定的变量来循环一个对象所有可枚举的属性。JavaScript 会为每一个不同的属性执行指定的语句。

```javaScript
for (variable in object) {
  statements
}
```

虽然使用 for...in 来迭代数组 Array 元素听起来很诱人，但是它返回的东西除了数字索引外，还有可能是你自定义的属性名字。因此还是用带有数字索引的传统的 for 循环来迭代一个数组比较好，因为，如果你想改变数组对象，比如添加属性或者方法，for...in 语句迭代的是自定义的属性，而不是数组的元素。

```javaScript
const arr = [1,2,3];
arr['a'] = 'hello';

for(let i in arr){
  console.log(arr[i]); // 1,2,3,'hello'
}
```

## for...of语句

for...of 语句在可迭代对象（包括Array、Map、Set、arguments 等等）上创建了一个循环，对值的每一个独特属性调用一次迭代。

```javaScript
for (variable of object) {
  statement
}
```

下面的这个例子展示了 for...of 和 for...in 两种循环语句之间的区别。 for...in 循环遍历的结果是数组元素的下标，而 for...of 遍历的结果是元素的值：

```javaScript
let arr = [3, 5, 7];
arr.foo = "hello";

for (let i in arr) {
  console.log(i); // 输出 "0", "1", "2", "foo"
}

for (let i of arr) {
  console.log(i); // 输出 "3", "5", "7"
}

// 注意 for...of 的输出没有出现 "hello"
```

## 参考

[MDN 循环与迭代](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Loops_and_iteration)