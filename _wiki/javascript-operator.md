---
layout: wiki
title: 运算符 / Operator
cate1: JavaScript
cate2: Learning
description: JavaScript 的基本运算符
keywords: JavaScrpit, 运算符
type:
link:
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
---

# 运算符

```js
console.log(2 ** 5) // 幂运算
//32
console.log(16 ** .5)   // 二分之一次幂，相当于平方根
//4
console.log(10 / 3) // 整数相除会保留小数
//3.3333333333333335
console.log(10 / 0)
//Infinty
```

---

## 一元运算符

- `+` 正号：不会改变数值的符号

- `-` 负号：可以对数值进行符号位取反

```js
let a = 10;

a = -a;

console.log(a);
//-10
```

## 隐式类型转换

- JS是一门弱类型语言，当进行运算时会通过自动的类型转换来完成运算

  ```js
  console.log(10 - '7')   // 10 - 7
  //3
  console.log(10 - true)  // 10 - 1
  //9
  console.log(10 - null)  // 10 + 0
  //10
  console.log(10 - undefined) // 10 - NaN
  //NaN
  ```

### 字符串的隐式转换

- 当任意一个值与字符串做**加法**运算时，会先将该值转换为字符串，然后进行**拼串**的操作

  ```js
  console.log('Hello'+'World')
  //HelloWorld
  console.log( 1 + '2')
  //12
  ```

- 可以利用这一特点来进行类型的转换，即为任意类型 `+` 上一个空串，便将该类型转换为了字符串

  ```js
  let a = true
  console.log(typeof a, a)
  //boolean true
  a = true + ''
  console.log(typeof a, a)
  //string true
  ```

### 数值的隐式转换

- 利用[一元运算符](#一元运算符)将字符串转换为数值类型

  ```js
  let b = "123"
  console.log(typeof b, b)
  //string 123
  b = +b
  console.log(typeof b, b)
  //number 123
  ```

## 赋值运算符

`??=` 空赋值：只有当变量为 `null` 或 `undefined` 时，才会赋值
