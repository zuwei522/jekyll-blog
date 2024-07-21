---
layout: wiki
title: 函数
cate1: 编程语言
cate2: JavaScript
description: JavaScript 函数
keywords: JavaScrpit, 函数
type:
link:
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
---

# 函数

## 浏览器内置函数（部分）

### alert() 方法

> 弹出警告框，并显示内容，等待用户点击确定后继续。

- 语法

  ```js
  alert()
  alert(message)
  ```

- 参数

  - **message** 可选

    是要显示在警告对话框中的字符串，如果传入其他类型的值，会转换成字符串。

- 示例

  ```js
  window.alert("Hello world!");
  alert("Hello world!");
  ```

  ![alert 弹窗：Hello World!](/images/wiki/alert-hello-world.png)

### console.log() 方法

> 向 Web 控制台输出一条信息。

```js
console.log("Hello World!");
```

### document.write() 方法

> 将一个文本字符串写入一个由 [`document.open()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/open) 打开的文档流（document stream）。

## 创建函数

### 函数声明创建函数

- 语法

  ```js
  function functionName(parameters) {
    // 执行的代码
  }
  ```

- 举个例子

  ```js
  function f(a, b) {
    console.log(a + b);
  } // 创建一个名为 f 的函数，它有两个形参 a，b

  f(2, 3); // 调用函数 f，传入实参 2 和 3，最终运行结果为在控制台上打印出 5
  ```

### 函数表达式创建函数

> JavaScript 函数可以通过一个表达式定义。函数表达式可以存储在变量中。

- 语法

  ```js
  var functionName = function (parameters) {
    // 执行的代码
  };
  ```

- 把前面[函数声明创建函数](#函数声明创建函数)的例子改写为用函数表达式创建函数：

  ```js
  var f = function (a, b) {
    console.log(a + b);
  };
  f(2, 3);
  ```

### 函数声明和函数表达式的区别

- 函数声明

  ```js
  // 此处的代码执行没有问题，JavaScript 解析器首先会把当前作用域的函数声明提前到整个作用域的最前面。
  f(2, 3);
  
  function f(a, b) {
    console.log(a + b);
  }
  ```

- 函数表达式

  ```js
  // 报错：f is not a function
  // 这是因为函数表达式，如同定义其它基本类型的变量一样，只在执行到某一句时也会对其进行解析
  
  f(2, 3);
  
  var f = function (a, b) {
    console.log(a + b);
  };
  ```

### 函数的参数

- 在 JavaScript 中，实参个数和形参个数**可以不相等**。

### 在 JavaScript 中没有重载

> 重载，从简单说，就是函数或者方法有相同的名称，但是参数列表不相同的情形，这样的同名不同参数的函数或者方法之间，互相称之为重载函数或者重载方法。在Java中同一个类中的2个或2个以上的方法可以有同一个名字，只要它们的参数声明不同即可。这种情况下，该方法就被称为重载，这个过程称为方法重载。  
*[原文链接：https://blog.csdn.net/thinkingcao/article/details/55045171](https://blog.csdn.net/thinkingcao/article/details/55045171)*

```js
function f(a, b) {
  return a + b;
}
function f(a, b, c) {
  return a + b + c;
}
var result = f(5, 6);
result; // returns NaN
```

上述代码中三个参数的 f 把两个参数的 f 覆盖，调用的是三个参数的 f，最后执行结果为 NaN，而不是 11。

### 在 JavaScript 中函数的返回值

- 如果函数中没有 `return` 语句，那么函数默认的返回值是：undefined。
- 如果函数中有 `return` 语句，那么跟着 `return` 后面的值就是函数的返回值。
- 如果函数中有 `return` 语句，但是 `return` 后面没有任何值，那么函数的返回值也是：undefined。

### 匿名函数

- 匿名函数就是没有命名的函数，一般用在绑定事件的时候。语法为：

  ```js
  function(){
      // 执行的代码
  }
  ```

- 例子：

  ```js
  var myButton = document.querySelector("button");
  
  myButton.onclick = function () {
    alert("hello");
  };
  ```

  > 注：将匿名函数分配为变量的值，也就是我们前面所讲的函数表达式创建函数。一般来说，创建功能，我们使用函数声明来创建函数。使用匿名函数来运行负载的代码以响应事件触发（如点击按钮），使用事件处理程序。

### 自调用函数

- 匿名函数不能通过直接调用来执行，因此可以通过匿名函数的自调用的方式来执行。比如：

  ```js
  (function () {
    alert("hello");
  })();
  ```
