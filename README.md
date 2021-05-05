# learnjs

### 变量和字符串

#### 使用let 与 const 代替 var

* 全局对象:

    browser -> window

    server -> global

    globalThis

    > globalThis 提供了一个标准的方式来获取不同环境下的全局 this  对象（也就是全局对象自身）。不像 window 或者 self 这些属性，它确保可以在有无窗口的各种环境下正常工作。所以，你可以安心的使用 globalThis，不必担心它的运行环境。为便于记忆，你只需要记住，全局作用域中的 this 就是 globalThis。
* 案例1

    1. 非严格模式——平时我们会称之为正常模式(sloppy mode)，这并不是一个官方说法，但是你会经常见到如上的一些说法，其意义就是指代非严格模式，即正常模式。

        看下面这段简单的代码

        ```javascipt
        message = "hello world";

        console.log(message);
        ```

        在上面代码中 message 不是变量, 实际是给全局对象window新增的属性

        ```javascript
        message = "hello world";

        console.log(window.message);
        ```

        以上两种写法是一致的

        以上代码在非严格模式下是可以正常运行的


    2. 严格模式(strict mode)

        ```javascrpit
        'user strict';
        message = "hello world";
        ```
        运行上述代码 会报错：messge is not defined;

* 案例2

    ```javascript
    console.log(26)
    var age = 26;
    ```

    上述代码执行结果为 null

    ```javascript
    'user strict';
    console.log(age)
    let age = 26;
    ```
    运行上述代码 会报错：Cannot access 'age' before initialization

    改为 const 运行结果也一致

* 建议：避免使用var, 当变量需要改变时, 使用let 代替 var, 当变量初始化后不再更改，使用const 代替 var

#### 块级作用域变量

* 案例

    ```javascript
    var price = 20;
    var isSale = true;
    // variable shadowing
    if (isSale) {
        var price = 20 - 2;
        console.log('sale price', price)
    }
     console.log('price', price)
    ```
    以上代码运行结果为：
    
    sale price, 18

    price, 18

    ```javascript
    var price = 20;
    var isSale = true;
    if (isSale) {
        let price = 20 - 2;
        console.log('sale price', price)
    }
     console.log('price', price)
    ```
    以上代码运行结果为：
    
    sale price, 18

    price, 20

#### 使用模板字符串

* 案例一

    ```javascript
    let name = prompt("enter your name");
    const messgae = "Hi " + name + ", how are you";
    alert(message);
    ```
    使用模板字符串
    ```javascript
    let name = prompt("enter your name");
    const messgae = `Hi ${name}, how are you`;
    alert(message);
    ```

* 案例二

    ```javascript
    const weight = 150;
    const moonWeight = `You weigh ${weight * 0.165} pounds on the moon`;
    console.log(moonWeight);
    ```

* 案例三

    引号嵌套

    ```javascript
    "I'm a string";
    'He said, "I am string"';
    ```

    转义字符
    ```javascript
    'I\'m a string';
    "He said, \"I am string\"";
    ```

    使用模板字符串
     ```javascript
    `I'm a string`;
    `He said, "I am string"`;
    ```

* 案例四

    多行
     ```javascript
    const threeLines = "This is a string\r that spans across\r three lines."
    ```

    使用模板字符串
     ```javascript
    const threeLines = `
    This is a string
    that spans across
    three lines.`
    ```