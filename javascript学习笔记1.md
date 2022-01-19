## JavaScript 基础知识

[TOC]

#### *<u>1 Hello , world !</u>*  

**script标签**：使用 `<script>` 标签将 JavaScript 程序插入到 HTML 文档的任何位置。<script> 标签中包裹了 JavaScript 代码，当浏览器遇到 <script> 标签，代码会自动运行。

```javascript
<!DOCTYPE HTML>
<html>

<body>

  <p>script 标签之前...</p>

  <script>
    alert('Hello, world!');
  </script>

  <p>...script 标签之后</p>

</body>

</html>
```

**外部脚本**：

如果有大量的 JavaScript 代码，可以将它放入一个单独的文件。脚本文件可以通过 `src` 特性（attribute）添加到 HTML 文件中。

```javascript
<script src="/path/to/script.js"></script>
```

使用 `<code>` 标签插入只有几个词的代码，插入多行代码可以使用 `<pre>` 标签，对于超过 10 行的代码，建议你使用沙箱（[plnkr](https://plnkr.co/edit/?p=preview)，[JSBin](https://jsbin.com/)，[codepen](http://codepen.io/)…）



#### *<u>2代码结构</u>* 

**单行注释以两个正斜杠字符 `//` 开始。**

**多行注释以一个正斜杠和星号开始 `“/\*”` 并以一个星号和正斜杠结束 `“\*/”`**



#### *<u>3现代模式，" use strict "</u>* 

```javascript
"use strict";

// 代码以现代模式工作
...
```

这个指令看上去像一个字符串 `"use strict"` 或者 `'use strict'`。当它处于脚本文件的顶部时，则整个脚本文件都将以“现代”模式进行工作。

**确保 “use strict” 出现在最顶部**

```javascript
alert("some code");
// 下面的 "use strict" 会被忽略，必须在最顶部。

"use strict";

// 严格模式没有被激活
```



#### <u>*4变量*</u> 

在 JavaScript 中创建一个变量，我们需要用到 `let` 关键字。

下面的语句创建（也可以称为 **声明** 或者 **定义**）了一个名称为 “message” 的变量：

```javascript
let message;
```

```javascript
let message;
message = 'Hello!';

alert(message); // 显示变量内容
```

简洁一点，我们可以将变量定义和赋值合并成一行：

```javascript
let message = 'Hello!'; // 定义变量，并且赋值

alert(message); // Hello!
```

还可以声明两个变量，然后将其中一个变量的数据拷贝到另一个变量。

```javascript
let hello = 'Hello world!';

let message;

// 将字符串 'Hello world' 从变量 hello 拷贝到 message
message = hello;

// 现在两个变量保存着相同的数据
alert(hello); // Hello world!
alert(message); // Hello world!
```

JavaScript 的变量命名有两个限制：

1. 变量名称必须仅包含字母，数字，符号 `$` 和 `_`。
2. 首字符必须非数字。

**常量**

声明一个常数（不变）变量，可以使用 `const` 而非 `let`：

```javascript
const myBirthday = '18.04.1982';
```

使用 `const` 声明的变量称为“常量”。它们不能被修改，如果你尝试修改就会发现报错：

```javascript
const myBirthday = '18.04.1982';

myBirthday = '01.01.2001'; // 错误，不能对常量重新赋值
```

**大写形式的常数**

一个普遍的做法是将常量用作别名，以便记住那些在执行之前就已知的难以记住的值。

使用大写字母和下划线来命名这些常量。

例如，让我们以所谓的“web”（十六进制）格式为颜色声明常量：

```javascript
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ……当我们需要选择一个颜色
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```



#### <u>*5数据类型*</u> 

***number* 类型代表整数和浮点数。**

数字可以有很多操作，比如，乘法 `*`、除法 `/`、加法 `+`、减法 `-` 等等。

除了常规的数字，还包括所谓的“特殊数值也属于这种类型：`Infinity`、`-Infinity` 和 `NaN`。

- `Infinity` 代表数学概念中的 [无穷大](https://en.wikipedia.org/wiki/Infinity) ∞。是一个比任何数字都大的特殊值。

  我们可以通过除以 0 来得到它：

  ```javascript
  alert( 1 / 0 ); // Infinity
  ```

  或者在代码中直接使用它：

  ```javascript
  alert( Infinity ); // Infinity
  ```

- `NaN` 代表一个计算错误。它是一个不正确的或者一个未定义的数学操作所得到的结果，比如：

  ```javascript
  alert( "not a number" / 2 ); // NaN，这样的除法是错误的
  ```

  `NaN` 是粘性的。任何对 `NaN` 的进一步操作都会返回 `NaN`：

  ```javascript
  alert( "not a number" / 2 + 5 ); // NaN
  ```

  所以，如果在数学表达式中有一个 `NaN`，会被传播到最终结果。

**string类型**

JavaScript 中的字符串必须被括在引号里。

```javascript
let str = "Hello";
let str2 = 'Single quotes are ok too';
let phrase = `can embed another ${str}`;
```

在 JavaScript 中，有三种包含字符串的方式。

1. 双引号：`"Hello"`.
2. 单引号：`'Hello'`.
3. 反引号：``Hello``.

双引号和单引号都是“简单”引用，在 JavaScript 中两者几乎没有什么差别。

反引号是 **功能扩展** 引号。它们允许我们通过将变量和表达式包装在 `${…}` 中，来将它们嵌入到字符串中。例如：

```javascript
let name = "John";

// 嵌入一个变量
alert( `Hello, ${name}!` ); // Hello, John!

// 嵌入一个表达式
alert( `the result is ${1 + 2}` ); // the result is 3
```

`${…}` 内的表达式会被计算，计算结果会成为字符串的一部分。可以在 `${…}` 内放置任何东西：诸如名为 `name` 的变量，或者诸如 `1 + 2` 的算数表达式，或者其他一些更复杂的。

需要注意的是，这仅仅在反引号内有效，其他引号不允许这种嵌入。

```javascript
alert( "the result is ${1 + 2}" ); // the result is ${1 + 2}（使用双引号则不会计算 ${…} 中的内容）
```

**boolean类型**仅包含两个值：`true` 和 `false`。

这种类型通常用于存储表示 yes 或 no 的值：`true` 意味着 “yes，正确”，`false` 意味着 “no，不正确”。

**null值**

```javascript
let age = null;//表示 `age` 是未知的
```

相比较于其他编程语言，JavaScript 中的 `null` 不是一个“对不存在的 `object` 的引用”或者 “null 指针”。

JavaScript 中的 `null` 仅仅是一个代表“无”、“空”或“值未知”的特殊值。

**undefined值**

`undefined` 的含义是 `未被赋值`。

如果一个变量已被声明，但未被赋值，那么它的值就是 `undefined`

```javascript
let age;

alert(age); // 弹出 "undefined"
```

**`object` 类型**是一个特殊的类型。

其他所有的数据类型都被称为“原始类型”，因为它们的值只包含一个单独的内容（字符串、数字或者其他）。相反，`object` 则用于储存数据集合和更复杂的实体。

**`symbol` 类型**用于创建对象的唯一标识符。

**`typeof` 运算符**返回参数的类型。

```javascript
typeof undefined // "undefined"

typeof 0 // "number"

typeof 10n // "bigint"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

typeof Math // "object"

typeof null // "object"

typeof alert // "function"
```



#### <u>*6交互： alert 、 prompt 和 confirm*</u> 

<u>**alert**</u>

它会显示一条信息，并等待用户按下 “OK”。

```javascript
alert("Hello");
```



**<u>prompt</u>**

`prompt` 函数接收两个参数：

```javascript
result = prompt(title, [default]);
```

浏览器会显示一个带有文本消息的模态窗口，还有 input 框和确定/取消按钮。

- `title`

  显示给用户的文本

- `default`

  可选的第二个参数，指定 input 框的初始值。

语法中的方括号 `[...]`

上述语法中 `default` 周围的方括号表示该参数是可选的，不是必需的。

访问者可以在提示输入栏中输入一些内容，然后按“确定”键。然后我们在 `result` 中获取该文本。或者他们可以按取消键或按 Esc 键取消输入，然后我们得到 `null` 作为 `result`。

`prompt` 将返回用户在 `input` 框内输入的文本，如果用户取消了输入，则返回 `null`。

举个例子：

```javascript
let age = prompt('How old are you?', 100);

alert(`You are ${age} years old!`); // You are 100 years old!
```



<u>**confirm：**</u>

```javascript
result = confirm(question);
```

`confirm` 函数显示一个带有 `question` 以及确定和取消两个按钮的模态窗口。

点击确定返回 `true`，点击取消返回 `false`。

例如：

```javascript
let isBoss = confirm("Are you the boss?");

alert( isBoss ); // 如果“确定”按钮被按下，则显示 true
```



#### <u>*7类型转换*</u>

**字符串转换**

`alert(value)` 将 `value` 转换为字符串类型，然后显示这个值。

我们也可以显式地调用 `String(value)` 来将 `value` 转换为字符串类型：

```javascript
let value = true;
alert(typeof value); // boolean

value = String(value); // 现在，值是一个字符串形式的 "true"
alert(typeof value); // string
```



**数字型转换**

```javascript
alert( "6" / "2" ); // 3, string 类型的值被自动转换成 number 类型后进行计算
```

也可以使用 `Number(value)` 显式地将这个 `value` 转换为 number 类型。

```javascript
let str = "123";
alert(typeof str); // string

let num = Number(str); // 变成 number 类型 123

alert(typeof num); // number
```

number 类型转换规则：

| 值              | 变成……                                                       |
| :-------------- | :----------------------------------------------------------- |
| `undefined`     | `NaN`                                                        |
| `null`          | `0`                                                          |
| `true 和 false` | `1` and `0`                                                  |
| `string`        | 去掉首尾空格后的纯数字字符串中含有的数字。如果剩余字符串为空，则转换结果为 `0`。否则，将会从剩余字符串中“读取”数字。当类型转换出现 error 时返回 `NaN` |



**布尔型转换**

```javascript
alert( Boolean(1) ); // true
alert( Boolean(0) ); // false

alert( Boolean("hello") ); // true
alert( Boolean("") ); // false
```

包含 0 的字符串 `"0"` 是 `true`。在 JavaScript 中，非空的字符串总是 `true`。

```javascript
alert( Boolean("0") ); // true
alert( Boolean(" ") ); // 空白，也是 true（任何非空字符串都是 true）
```



#### <u>*8条件分支*</u>

`if(...)` 语句计算括号里的条件表达式，如果计算结果是 `true`，就会执行对应的代码块。

例如：

```javascript
let year = prompt('In which year was ECMAScript-2015 specification published?', '');

if (year == 2015) alert( 'You are right!' );
```

在上面这个例子中，条件是一个简单的相等性检查（`year == 2015`），但它还可以更复杂。

如果有多个语句要执行，我们必须将要执行的代码块封装在大括号内：

```javascript
if (year == 2015) {
  alert( "That's correct!" );
  alert( "You're so smart!" );
}
```

**else语句**

`if` 语句有时会包含一个可选的 “else” 块。如果判断条件不成立，就会执行它内部的代码。

例如：

```javascript
let year = prompt('In which year was ECMAScript-2015 specification published?', '');

if (year == 2015) {
  alert( 'You guessed it right!' );
} else {
  alert( 'How can you be so wrong?' ); // 2015 以外的任何值
}
```

**多个条件：“else if”**

有时我们需要测试一个条件的几个变体。我们可以通过使用 `else if` 子句实现。

例如：

```javascript
let year = prompt('In which year was ECMAScript-2015 specification published?', '');

if (year < 2015) {
  alert( 'Too early...' );
} else if (year > 2015) {
  alert( 'Too late' );
} else {
  alert( 'Exactly!' );
}
```

在上面的代码中，JavaScript 先检查 `year < 2015`。如果条件不符合，就会转到下一个条件 `year > 2015`。如果这个条件也不符合，则会显示最后一个 `alert`



**“？”**

```javascript
let result = condition ? value1 : value2;
```

计算条件结果，如果结果为真，则返回 `value1`，否则返回 `value2`。

**多个 ‘?’**

使用一系列问号 `?` 运算符可以返回一个取决于多个条件的值。

例如：

```javascript
let age = prompt('age?', 18);

let message = (age < 3) ? 'Hi, baby!' :
  (age < 18) ? 'Hello!' :
  (age < 100) ? 'Greetings!' :
  'What an unusual age!';

alert( message );
```

可能很难一下子看出发生了什么。但经过仔细观察，我们可以看到它只是一个普通的检查序列。

1. 第一个问号检查 `age < 3`。
2. 如果为真 — 返回 `'Hi, baby!'`。否则，会继续执行冒号 `":"` 后的表达式，检查 `age < 18`。
3. 如果为真 — 返回 `'Hello!'`。否则，会继续执行下一个冒号 `":"` 后的表达式，检查 `age < 100`。
4. 如果为真 — 返回 `'Greetings!'`。否则，会继续执行最后一个冒号 `":"` 后面的表达式，返回 `'What an unusual age!'`。

这是使用 `if..else` 实现上面的逻辑的写法：

```javascript
if (age < 3) {
  message = 'Hi, baby!';
} else if (age < 18) {
  message = 'Hello!';
} else if (age < 100) {
  message = 'Greetings!';
} else {
  message = 'What an unusual age!';
}
```



#### *<u>9函数</u>*

使用 **函数声明** 创建函数：

```javascript
function showMessage() {
  alert( 'Hello everyone!' );
}
```

`function` 关键字首先出现，然后是 函数名，然后是括号之间的 参数 列表（用逗号分隔，在上述示例中为空，我们将在接下来的示例中看到），最后是花括号之间的代码（即“函数体”）。

```javascript
function name(parameter1, parameter2, ... parameterN) {
  ...body...
}
```

新函数可以通过名称调用：`showMessage()`。

例如：

```javascript
function showMessage() {
  alert( 'Hello everyone!' );
}

showMessage();
showMessage();
```

调用 `showMessage()` 执行函数的代码（两次显示消息）



函数对外部变量拥有全部的访问权限。函数也可以修改外部变量。

例如：

```javascript
let userName = 'John';

function showMessage() {
  userName = "Bob"; // (1) 改变外部变量

  let message = 'Hello, ' + userName;
  alert(message);
}

alert( userName ); // John 在函数调用之前

showMessage();

alert( userName ); // Bob，值被函数修改了
```

输出John-->Hello,Bob--->Bob

**参数**

可以通过参数将任意数据传递给函数。

在如下示例中，函数有两个参数：`from` 和 `text`。

```javascript
function showMessage(from, text) { // 参数：from 和 text
  alert(from + ': ' + text);
}

showMessage('Ann', 'Hello!'); // Ann: Hello! (*)
showMessage('Ann', "What's up?"); // Ann: What's up? (**)
```

**返回值**

函数可以将一个值返回到调用代码中作为结果。

最简单的例子是将两个值相加的函数：

```javascript
function sum(a, b) {
  return a + b;
}

let result = sum(1, 2);
alert( result ); // 3
```

指令 `return` 可以在函数的任意位置。当执行到达时，函数停止，并将值返回给调用代码（分配给上述代码中的 `result`）。

在一个函数中可能会出现很多次 `return`。例如：

```javascript
function checkAge(age) {
  if (age >= 18) {
    return true;
  } else {
    return confirm('Got a permission from the parents?');
  }
}

let age = prompt('How old are you?', 18);

if ( checkAge(age) ) {
  alert( 'Access granted' );
} else {
  alert( 'Access denied' );
}
```