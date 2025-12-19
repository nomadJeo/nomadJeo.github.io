---
title: JavaScript基本数据类型
date: 2025-09-09
categories: [ 前端, JavaScript ]
tags: [ JavaScript ]
mermaid: true
---

## JavaScript基本数据类型

JavaScript有7种基本数据类型（Primitive Data Types）：

1. **Number**：表示整数和浮点数，例如 `42`、`3.14`。Number类型还包括特殊值 `NaN`（非数字）、`Infinity` 和 `-Infinity`。Number类型使用64位双精度浮点数表示。整数的表示范围是 -2^53 - 2^53.
2. **String**：表示文本数据，例如 `"Hello, World!"`
3. **Boolean**：表示逻辑值，只有两个取值：`true` 和 `false`。
4. **Undefined**：表示变量未定义，只有一个值 `undefined`。
5. **Null**：表示空值，只有一个值 `null`。
6. [**Symbol**](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Symbol)：表示唯一标识符，通常用于对象属性的键。
7. **BigInt**：表示任意精度整数，例如 `9007199254740991n`.

## 基本数据类型转换

### 一、字符串（String）转换

显示转换

```js
String(123)    // "123"
String(true)   // "true"
String(null)   // "null"
String(undefined) // "undefined"
String(Symbol("x")) // "Symbol(x)"
```

隐式转换

* 拼接时会把非字符串转成字符串：

  ```js
  "值是 " + 123  // "值是 123"
  true + "!"     // "true!"
  ```

---

### 二、数字（Number）转换

显示转换

```js
Number("123")   // 123
Number("  42 ") // 42
Number("")      // 0
Number("abc")   // NaN
Number(true)    // 1
Number(false)   // 0
Number(null)    // 0
Number(undefined) // NaN
```

隐式转换

* 算术运算：

  ```js
  "5" - 2   // 3  （"5" 转成数字）
  "5" * 2   // 10
  "5" / 2   // 2.5
  "5" + 2   // "52" （注意：这里是字符串拼接）
  ```

---

### 三、布尔值（Boolean）转换

显示转换

```js
Boolean(0)        // false
Boolean("")       // false
Boolean(null)     // false
Boolean(undefined)// false
Boolean(NaN)      // false
Boolean("0")      // true  （非空字符串都是真）
Boolean([])       // true  （空数组也是真）
```

隐式转换

* `if (...)` 判断里会自动转布尔

  ```js
  if ("") { ... } // 不执行
  if ("ok") { ... } // 执行
  ```

* `!` 和 `!!` 常用于快速转布尔

  ```js
  !!"hello"  // true
  !!0        // false
  ```

---

### 四、`null` 和 `undefined`

* 转字符串：`String(null) → "null"`，`String(undefined) → "undefined"`
* 转数字：

  ```js
  Number(null)      // 0
  Number(undefined) // NaN
  ```

* 转布尔：两者都是 `false`

---

### 五、`BigInt`

* 和 Number 类似，但范围更大。
* 不能和 Number 混用算术（会报错）：

  ```js
  1n + 2   // ❌ TypeError
  1n + 2n  // ✅ 3n
  ```

* 转换：

  ```js
  BigInt(42)    // 42n
  BigInt("123") // 123n
  ```

---

### 六、`Symbol`

* `Symbol` 不能自动转成 Number 或 BigInt，否则会抛错：

  ```js
  Number(Symbol("x")) // TypeError
  ```

* 可以显式转字符串：

  ```js
  String(Symbol("x")) // "Symbol(x)"
  ```

---

### 七、特殊的“暗坑”例子

JS 类型转换最著名的“黑魔法”：

```js
[] + {}   // "[object Object]"
{} + []   // 0
[] == ![] // true
```

解释：

* `[] + {}` → 空数组转字符串 `""`，对象转字符串 `"[object Object]"` → 拼接
* `{} + []` → 被当成块语句 + 空数组转数字 `0`
* `[] == ![]` → 左边转成字符串`""`，右边是 `false`，再转数字比较，结果居然相等

---

### 字面量

在 JavaScript 中，字面量可以表示值。这些字面量是脚本中按字面意思给出的固定的值，而不是变量。

支持的字面量：

* 数组字面量
* 布尔字面量
* 数字字面量
* 对象字面量
* RegExp 字面量
* 字符串字面量

## 参照

* [JavaScript 语法与类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Grammar_and_types)

* [JavaScript 数据类型和数据结构 - MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures)
