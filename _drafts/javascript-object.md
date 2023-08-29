---
layout: wiki
title: 对象
cate1: JavaScript
cate2: 学习
description: JavaScript Object
keywords: JavaScrpit, JSON, Array, String, Date, Math
type:
link:
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
---
## JSON

JSON（JavaScript Object Notation，JavaScript 对象表示法）是一种由道格拉斯·克罗克福特构想和设计、轻量级的数据交换语言，该语言以易于让人阅读的文字为基础，用来传输由属性值或者序列性的值组成的数据对象。尽管 JSON 是 JavaScript 的一个子集，但 JSON 是独立于语言的**文本格式**，并且采用了类似于 C 语言家族的一些习惯。

> JSON 数据格式与语言无关，脱胎于 JavaScript，但当前很多编程语言都支持 JSON 格式数据的生成和解析。JSON 的官方 MIME 类型是 application/json，文件扩展名是 .json。

注：定义来自维基百科。

两个简单的 json 示例：

```json
{
  "name": "zhangsan",
  "age": 18,
  "gender": "male"
}
```

```json
{
  "students": [
    { "firstName": "san", "lastName": "zhang" },
    { "firstName": "si", "lastName": "li" },
    { "firstName": "wu", "lastName": "wang" }
  ]
}
```

特别需要注意的是：

- JSON 是一种纯数据格式，它只包含属性，没有方法。
- JSON 的属性必须通过双引号引起来。
- JSON 要求两头有 {} 来使其合法。
- 可以把 JavaScript 对象原原本本的写入 JSON 数据，比如：字符串，数字，数组，布尔还有其它的字面值对象。

## 常用内置对象

### Array 对象

1. 常用属性
    - `length` 获取数组长度

2. 常用方法
    - `concat()` 方法用于链接两个或多个数组，并返回结果。

        语法：

        ```js
        arrayObject.concat(arrayX, arrayX, ..., arrayX);
        ```

        例子：

        ```js
        var a = [1, 2, 3];
        var b = [4, 5, 6];
        var c = ["one", "two", "three"];
        console.log(a.concat(b, c));
        //[1, 2, 3, 4, 5, 6, "one", "two", "three"]
        ```

    - `join()` 方法，将数组转换成字符串。
    - `pop()` 方法，删除并返回数组的最后一个元素。
    - `push()` 方法，向数组的末尾添加一个或更多元素，并返回新的长度。
    - `reverse()` 方法，颠倒数组的顺序。

        例子：

        ```js
        var a = [1, 2, 3, 4];
        a.reverse();
        console.log(a);
        //[4, 3, 2, 1]
        ```

    - `shift()` 方法，删除并返回数组的第一个元素。
    - `unshift()` 方法，向数组的开头添加一个或更多元素，并返回新的长度。
    - `slice()` 方法，从某个已有的数组返回选定的元素。

        语法：

        ```js
        arrayObject.slice(start, end);
        // strat 值是必需的，规定从何处开始选取
        // end 值可选，规定从何处结束选取，如果没有设置，默认为从 start 开始选取到数组后面的所有元素
        ```

        例子：

        ```js
        var a = [1, 2, 3, 4, 5, 6];
        a.slice(2, 5);
        //[3, 4, 5]
        console.log(a);
        //[ 1, 2, 3, 4, 5, 6 ]
        ```

        > 需要注意的是，该方法不会修改原数组，只是返回一个子数组，a 数组还是 [1, 2, 3, 4, 5, 6]
    - `splice()` 方法，删除或替换当前数组的某些项目。

        语法：

        ```js
        arrayObject.splice(start, deleteCount, options);
        // start 值是必需的，规定删除或替换项目的位置
        // deleteCount 值是必需的，规定要删除的项目数量，如果设置为 0，则不会删除项目
        // options 值是可选的，规定要替换的新项目
        // 和 slice() 方法不同的是 splice() 方法会修改数组
        ```

        例子：

        ```js
        var a = [1, 2, 3, 4, 5, 6];
        a.splice(2, 2, "abc");
        console.log(a);
        //[1, 2, "abc", 5, 6]
        ```

    - `sort()` 方法，将数组进行排序。

        语法：

        ```js
        arrayObject.sort(sortby);
        // sortby 是可选的，规定排序顺序，必需是函数。如果没有参数的话，将会按照字母顺序进行排序，更准确的说是按照字符编码（可自行百度了解）的顺序进行排序。如果想按照其他标准进行排序，则需要提供比较函数
        ```

        例子：

        ```js
        arr1 = ["a", "z", "k", "w", "x"];
        console.log(arr1);
        //[ 'a', 'z', 'k', 'w', 'x' ]
        console.log(arr1.sort());
        //[ 'a', 'k', 'w', 'x', 'z' ]

        arr2 = [11,55,22,44,66,33];
        console.log(arr2);
        //[ 11, 55, 22, 44, 66, 33 ]
        console.log(arr2.sort());
        //[ 11, 22, 33, 44, 55, 66 ]

        arr3 = [1,22,44,6,55,5,2,4,66];
        console.log(arr3);
        //[1, 22, 44, 6, 55, 5, 2, 4, 66]
        console.log(arr3.sort());
        //[1, 2, 22, 4, 44, 5, 55, 6, 66]
        ```

        `sort()` 函数会对原数组进行修改，并返回排序后的数组。如果不传入比较函数，则默认按照字符编码的顺序进行排序。

        下面这段代码展示了如何使用 `sort()` 函数对数组进行大小排序。`sort()` 函数可以接受一个比较函数作为参数，用于指定排序规则。在这个例子中，`sortNum1` 函数指定了从小到大排序的规则，`sortNum2` 函数指定了从大到小排序的规则。

        ```js
        function sortNum1(a, b) {
            return a - b; // 从小到大排序
        }
        arr4 = [1,22,44,6,55,5,2,4,66];
        console.log(arr4);
        //[1, 22, 44, 6, 55, 5, 2, 4, 66]
        console.log(arr4.sort(sortNum1));
        //[1, 2, 4, 5, 6, 22, 44, 55, 66]

        function sortNum2(a,b) {
            return b - a; // 从大到小排序
        }
        arr4 = [1,22,44,6,55,5,2,4,66];
        console.log(arr4);
        //[1, 22, 44, 6, 55, 5, 2, 4, 66]
        console.log(arr4.sort(sortNum2));
        //[66, 55, 44, 22, 6, 5, 4, 2, 1]
        ```

        具体来说，`sortNum1()` 函数接受两个参数 `a` 和 `b`，它们分别代表数组中的两个元素。函数返回 `a - b` 的结果，如果结果小于 0，则 `a` 排在 `b` 前面，否则 `a` 排在 `b` 后面。这样，`sort()` 函数就可以根据这个比较函数的返回值来对数组进行排序。
    - `toString()` 方法，把数组转换为字符串，并返回结果。

### String 对象

1. 常用属性
    - `length` 获取字符串的长度。

2. 常用方法
    - `charAt()` 方法，获取指定位置处字符。  

        语法为：

        ```js
        stringObject.charAt(index);
        // 字符串中第一个字符的下标是 0。如果参数 index 不在 0 与 string.length 之间，该方法将返回一个空字符串
        ```

        例子：

        ```js
        str = "Hello world!";
        console.log(str.charAt(2));
        //l
        ```

    - `charCodeAt()` 方法，获取指定位置处字符的 Unicode 编码。

        语法：

        ```js
        stringObject.charCodeAt(index);
        // 字符串中第一个字符的下标是 0。如果 index 是负数，或大于等于字符串的长度，则 charCodeAt() 返回 NaN
        ```

        例子：

        ```js
        str = "Hello world!";
        console.log(str.charCodeAt(2));
        //108
        ```

    - `concat()` 方法，连接字符串，等效于 “+”，“+” 更常用。与数组中的 `concat()` 方法相似。
    - `slice()` 方法，提取字符串的片断，并在新的字符串中返回被提取的部分。
    - `indexOf()` 方法，检索字符串。
    - `toString()` 方法，返回字符串。
    - `toLowerCase()` 方法，把字符串转换为小写。
    - `toUpperCase()` 方法，把字符串转换为大写。
    - `replace()` 方法，替换字符串中的某部分。
    - `split()` 方法，把字符串分割为字符串数组。

### Date 对象

1. Date 对象方法
    - `Date()`：返回当日的日期和时间（输出的是中国标准时间）

    - `getDate()`：从 Date 对象返回一个月中的某一天 (1 ~ 31)
    - `getDay()`：从 Date 对象返回一周中的某一天 (0 ~ 6)
    - `getMonth()`：从 Date 对象返回月份 (0 ~ 11)
    - `getFullYear()`：从 Date 对象以四位数字返回年份
    - `getHours()`：返回 Date 对象的小时 (0 ~ 23)
    - `getMinutes()`：返回 Date 对象的分钟 (0 ~ 59)
    - `getSeconds()`：返回 Date 对象的秒数 (0 ~ 59)
    - `getMilliseconds()`：返回 Date 对象的毫秒(0 ~ 999)

### Math 对象

1. 常用属性
    - `E` ：返回常数 e (2.718281828...)

    - `LN2` ：返回 2 的自然对数 (ln 2)
    - `LN10` ：返回 10 的自然对数 (ln 10)
    - `LOG2E` ：返回以 2 为底的 e 的对数 (log2e)
    - `LOG10E` ：返回以 10 为底的 e 的对数 (log10e)
    - `PI` ：返回 π（3.1415926535...）
    - `SQRT1_2` ：返回 1/2 的平方根
    - `SQRT2` ：返回 2 的平方根

    例子：

    ```js
    Math.E
    //2.718281828459045
    Math.PI
    //3.141592653589793
    Math.AQRT2
    //1.4142135623730951
    ```

2. 常用对象
    - `abs(x)` ：返回 x 的绝对值

    - `round(x)` ：返回 x 四舍五入后的值
    - `sqrt(x)` ：返回 x 的平方根
    - `ceil(x)` ：返回大于等于 x 的最小整数
    - `floor(x)` ：返回小于等于 x 的最大整数
    - `sin(x)` ：返回 x 的正弦
    - `cos(x)` ：返回 x 的余弦
    - `tan(x)` ：返回 x 的正切
    - `acos(x)` ：返回 x 的反余弦值（余弦值等于 x 的角度），用弧度表示
    - `asin(x)` ：返回 x 的反正弦值
    - `atan(x)` ：返回 x 的反正切值
    - `exp(x)` ：返回 e 的 x 次幂 (e^x)
    - `pow(n, m)` ：返回 n 的 m 次幂 (nm)
    - `log(x)` ：返回 x 的自然对数 (ln x)
    - `max(a, b)` ：返回 a, b 中较大的数
    - `min(a, b)` ：返回 a, b 中较小的数
    - `random()` ：返回大于 0 小于 1 的一个随机数

    例子：

    ```js
    console.log(Math.sqrt(4));
    //2
    console.log(Math.pow(2, 8));
    //256
    console.log(Math.random());
    //0.13970462105621584
    console.log(Math.random());
    //0.7425663847297796
    ```
