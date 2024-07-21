---
layout: wiki
title: 数据类型
cate1: 编程语言
cate2: JavaScript
description: JavaScript 基本数据类型
keywords: JavaScrpit, 数据类型
type:
link:
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
---

# 数据类型

## 类别

1. 数值（Number）

   - 整形
   - 浮点型

   - 其他进制的数字：以以下前缀开头

     - 二进制 0b

     - 八进制 0o

     - 十六进制 0x

2. 大整数（BigInt）

   - 大整数用来表示一些比较大的整数
   - 大整数以n结尾，理论上它可以表示的数字范围是**无穷大**
   - 大整数**不能**和数值类型一同计算

3. 字符串（String）

   - 在JS中使用单引号或双引号来表示字符串

   - 转义字符 `\`

     - \\" --> "

     - \\' --> '

     - \\\ --> \

     - \t --> 制表符

     - \n --> 换行

      ……

   - 模板字符串

     - 使用返单引号 ` 来表示模板字符串

     - 模板字符串中可以嵌入变量

       示例：

       ```js
       let a = 10
       let b = 5
       
       console.log(`a=${a},b=${b}`)
       ```

       输出：

       ```js
       a=10,b=5
       ```

4. 布尔值（Boolean）

   - 布尔值主要用来进行逻辑判断
   - 布尔值只有两个值，即 `true` 和 `false`

5. 空值（null）

   - 空值用来表示空对象
   - 空值只有一个值，即 `null`
   - 使用 `typeof` 检查一个空值时会返回 `object`，故使用 `typeof` 无法检查空值

6. 未定义（undefined）

   - 当声明一个变量而没有赋值时，它的值就是 `undefined`
   - undefined 类型的值只有一个，即 `undefined`
   - 使用 `typeof` 检查一个 `undefined` 类型的值时，会返回 `undefined`

7. 符号（Symbol）

   - 用来创建一个唯一的标识

   - 使用 `typeof` 检查符号时会返回 `symbol`

     示例：

     ```js
     let a = Symbol()
     
     console.log(a)
     console.log(typeof a)
     ```

     输出：

     ```js
     Symbol()
     symbol
     ```

## 类型检查

- typeof 运算符

  - 用来检查不同**值**的类型

    示例：

  ```js
  let a = 10
  let b = 10n
  
  console.log(typeof a)
  console.log(typeof b)
  ```

    输出：

  ```js
  number
  bigint
  ```

## 类型转换

类型转换指将一种数据类型转换为其他类型

### 转换为字符串

1. 调用 `toString()` 方法，将其他类型转换为字符串

   示例：

   ```js
   let a = 10
   a = a.toString() //此方法只创建转换后新的类型数据，并不会修改原变量的值，故需自行对原变量进行赋值
   console.log(typeof a, a)
   ```

   输出：

   ```js
   string 10
   ```

   - 由于 `null` 和 `undefined` 没有 `toString()` 方法，所以对这两种类型的数据调用 `toString()` 时会报错

2. 调用 String() 函数，将其他类型转换为字符串

   示例：

   ```js
   let b = 10
   b = String(b)
   console.log(typeof b, b)
   ```

   输出：

   ```js
   string 10
   ```

   - 原理：

     - 对拥有 `toString()` 方法的值调用 `String()` 函数，实际上就是在调用 `toString()` 方法
     - 对于 `null` ，则直接转换为 `"null"`

     - 对于 `undefined` ，则直接转换为 `"undefined"`

### 转换为数值

1. 使用 `Number()` 函数，将其他类型转换为数值

   - 字符串：
     - 如字符串为合法数字，则转换为相应的数字
     - 如字符串不为合法数字，则转换为 `NaN`
     - 如字符串为空串或纯空格的字符串，则转换为 `0`
   - 布尔值：
     - `true` 转换为 `1`
     - `false` 转换为 `0`
   - `null`：
     - 转换为 `0`
   - `undefined`：
     - 转换为 `NaN`

   示例：

   ```js
   let a = '123'
   a = Number(a)
   console.log(typeof a, a)
   ```

   输出：

   ```js
   string 123
   ```

2. 将字符串转换为数值的两个方法

   - [`parseInt()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/parseInt) 将一个字符串转换为一个整数

     原理：

     - 自左向右逐个字符读取数字，直到读取到字符串中所有有效的整数
     - 若首个字符不为数字，则返回 `NaN`

   - [`parseFloat()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/parseFloat) 将一个字符串转换为一个浮点数

     原理：

     - 自左向右逐个字符读取数字，直到读取到字符串中所有有效的小数
     - 若首个字符不为数字，则返回 `NaN`

### 转换为布尔值

1. 使用 `Boolean()` 函数，将其他类型转换为布尔值

   - 数值：`0` 和 `NaN` 转换为 `flase` ，其余均转换为 `true`
   - 字符串：空串转换为 `flase` ，其余均转换为 `true`
   - `null` 和 `undefined` 均转换为 `false`
   - 对象基本会转换为 `true`

   所有表示空性的、没有的、错误的值，都会转换为 `false`
