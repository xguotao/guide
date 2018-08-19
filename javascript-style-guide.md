
# JavaScript编码规范


[1 前言](#1-前言)

[2 代码风格](#2-代码风格)

　　[2.1 结构](#21-结构)

　　　　[2.1.1 缩进](#211-缩进)

　　　　[2.1.2 空格](#212-空格)

　　　　[2.1.3 换行](#213-换行)

　　　　[2.1.4 语句](#214-语句)

　　[2.2 命名](#22-命名)

　　[2.3 注释](#23-注释)

　　　　[2.3.1 单行注释](#231-单行注释)

　　　　[2.3.2 多行注释](#232-多行注释)

　　　　[2.3.3 细节注释](#233-细节注释)

[3 语言特性](#3-语言特性)

　　[3.1 变量](#31-变量)

　　[3.2 条件](#32-条件)

　　[3.3 循环](#33-循环)

　　[3.4 类型](#34-类型)

　　　　[3.4.1 类型检测](#341-类型检测)

　　　　[3.4.2 类型转换](#342-类型转换)

　　[3.5 字符串](#35-字符串)

　　[3.6 对象](#36-对象)

　　[3.7 数组](#37-数组)

　　[3.8 函数](#38-函数)

　　　　[3.8.1 函数长度](#381-函数长度)

　　　　[3.8.2 参数设计](#382-参数设计)

[4 DOM](#4-DOM) 仅供参考

　　　　[4.1 元素获取](#41-元素获取)

　　　　[4.2 样式获取](#42-样式获取)

　　　　[4.3 样式设置](#43-样式设置)

　　　　[4.4 DOM操作](#44-DOM操作)

　　　　[4.5 DOM事件](#45-DOM事件)





## 1 前言


> **本文档的目标是使 JavaScript 代码风格保持一致，容易被理解和被维护。**


## 1.1 前言1111





## 2 代码风格


### 2.1 结构


#### 2.1.1 缩进

> **[强制] 使用 `4` 个空格做为一个缩进层级，不允许使用 `2` 个空格 或 `tab` 字符。**


> **[强制] `switch` 下的 `case` 和 `default` 必须增加一个缩进层级。**

示例：

```javascript
// good
switch (variable) {

    case '1':
        // do...
        break;

    case '2':
        // do...
        break;

    default:
        // do...

}

// bad
switch (variable) {

case '1':
    // do...
    break;

case '2':
    // do...
    break;

default:
    // do...

}
```

#### 2.1.2 空格



> **[强制] 二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格。**


示例：

```javascript
var a = !arr.length;
a++;
a = b + c;
```


> **[强制] 在对象创建时，属性中的 `:` 之后必须有空格，`:` 之前不允许有空格。**

示例：

```javascript
// good
var obj = {
    a: 1,
    b: 2,
    c: 3
};

// bad
var obj = {
    a : 1,
    b:2,
    c :3
};
```

> **[强制] 函数声明、具名函数表达式、函数调用中，函数名和 `(` 之间不允许有空格。**

示例：

```javascript
// good
function funcName() {
}

var funcName = function funcName() {
};

funcName();

// bad
function funcName () {
}

var funcName = function funcName () {
};

funcName ();
```

> **[强制] `,` 和 `;` 前不允许有空格。如果不位于行尾，`,` 和 `;` 后必须跟一个空格。**

示例：

```javascript
// good
callFunc(a, b);

// bad
callFunc(a , b) ;
```

> **[强制] 在函数调用、函数声明、括号表达式、属性访问、`if / for / while / switch / catch` 等语句中，`()` 和 `[]` 内紧贴括号部分不允许有空格。**

示例：

```javascript
// good

callFunc(param1, param2, param3);

save(this.list[this.indexes[i]]);

needIncream && (variable += increament);

if (num > list.length) {
}

while (len--) {
}


// bad

callFunc( param1, param2, param3 );

save( this.list[ this.indexes[ i ] ] );

needIncreament && ( variable += increament );

if ( num > list.length ) {
}

while ( len-- ) {
}
```

> **[强制] 单行声明的数组与对象，如果包含元素，`{}` 和 `[]` 内紧贴括号部分不允许包含空格。**

解释：

声明包含元素的数组与对象，只有当内部元素的形式较为简单时，才允许写在一行。元素复杂的情况，还是应该换行书写。


示例：

```javascript
// good
var arr1 = [];
var arr2 = [1, 2, 3];
var obj1 = {};
var obj2 = {name: 'obj'};
var obj3 = {
    name: 'obj',
    age: 20,
    sex: 1
};

// bad
var arr1 = [ ];
var arr2 = [ 1, 2, 3 ];
var obj1 = { };
var obj2 = { name: 'obj' };
var obj3 = {name: 'obj', age: 20, sex: 1};
```

> **[强制] 行尾不得有多余的空格。**


#### 2.1.3 换行


> **[强制] 每个独立语句结束后必须换行。每行不得超过 `120` 个字符。**

解释：

超长的不可分割的代码允许例外，比如复杂的正则表达式。长字符串不在例外之列。


> **[强制] 在函数声明、函数表达式、函数调用、对象创建、数组创建、`for` 语句等场景中，不允许在 `,` 或 `;` 前换行。**

示例：

```javascript
// good
var obj = {
    a: 1,
    b: 2,
    c: 3
};

foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
);


// bad
var obj = {
    a: 1
    , b: 2
    , c: 3
};

foo(
    aVeryVeryLongArgument
    , anotherVeryLongArgument
    , callback
);
```

> **[建议] 在语句的行长度超过 `120` 时，根据逻辑条件合理缩进。**

示例：

```javascript
// 较复杂的逻辑条件组合，将每个条件独立一行，逻辑运算符放置在行首进行分隔，或将部分逻辑按逻辑组合进行分隔。
// 建议最终将右括号 ) 与左大括号 { 放在独立一行，保证与 `if` 内语句块能容易视觉辨识。
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}

// 可使用数组来进行拼接，相对 `+` 更容易调整缩进。
var html = [
    '<article>',
    '<h1>Title here</h1>',
    '<p>This is a paragraph</p>',
    '<footer>Complete</footer>',
    '</article>'
];
html = html.join('');

// 当参数过多时，将每个参数独立写在一行上，并将结束的右括号 ) 独立一行。
// 所有参数必须增加一个缩进。
foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
);

// 当函数调用时，如果有一个或以上参数跨越多行，应当每一个参数独立一行。
// 这通常出现在匿名函数或者对象初始化等作为参数时，如 `setTimeout` 函数等。
setTimeout(
    function () {
        alert('hello');
    },
    200
);

order.data.read(
    'id=' + me.model.id,
    function (data) {
        me.attchToModel(data.result);
        callback();
    },
    300
);

// 三元运算符由3部分组成，因此其换行应当根据每个部分的长度不同，形成不同的情况。
var result = thisIsAVeryVeryLongCondition
    ? resultA : resultB;

var result = condition
    ? thisIsAVeryVeryLongResult
    : resultB;

// 数组和对象初始化的混用，严格按照每个对象的 `{` 和结束 `}` 在独立一行的风格书写。
var array = [
    {
        // ...
    },
    {
        // ...
    }
];
```



#### 2.1.4 语句


> **[强制] 不得省略语句结束的分号。**


> **[强制] 函数定义结束不允许添加分号。**

示例：

```javascript
// good
function funcName() {
}

// bad
function funcName() {
};

// 如果是函数表达式，分号是不允许省略的。
var funcName = function () {
};
```

### 2.2 命名


> **[强制] `变量` 使用 `驼峰式命名法`。**

示例：

```javascript
var loadingModules = {};
```

> **[强制] `常量` 使用 `驼峰式命名法` 的命名方式。**

示例：

```javascript
var loadingModules = {};
```

> **[强制] `函数` 使用 `驼峰式命名法`。**

示例：

```javascript
function stringFormat(source) {
}
```

> **[强制] 函数的 `参数` 使用 `驼峰式命名法`。**

示例：

```javascript
function hear(theBells) {
}
```


> **[强制] `类` 使用 `驼峰式命名法`。**

示例：

```javascript
function TextNode(options) {
}
```

> **[强制] 类的 `方法` / `属性` 使用 `驼峰式命名法`。**

示例：

```javascript
function TextNode(value, engine) {
    this.value = value;
    this.engine = engine;
}

TextNode.prototype.clone = function () {
    return this;
};
```

> **[强制] `命名空间` 使用 `驼峰式命名法`。**

示例：

```javascript
equipments.heavyWeapons = {};
```

> **[强制] 由多个单词组成的缩写词，在命名中，根据当前命名法和出现的位置，所有字母的大小写与首字母的大小写保持一致。**

示例：

```javascript
function XMLParser() {
}

function insertHTML(element, html) {
}

var httpRequest = new HTTPRequest();
```


> **[建议] `boolean` 类型的变量使用 `is` 或 `has` 开头。**

示例：

```javascript
var isReady = false;
var hasMoreCommands = false;
```


### 2.3 注释


#### 2.3.1 单行注释


> **[强制] 必须独占一行。`//` 后跟一个空格，缩进与下一行被注释说明的代码一致。**


#### 2.3.2 多行注释


> **[建议] 避免使用 `/*...*/` 这样的多行注释。有多行注释内容时，使用多个单行注释。**


> **[强制] 文档注释前必须空一行。**


#### 2.3.3 细节注释


对于内部实现、不容易理解的逻辑说明、摘要信息等，我们可能需要编写细节注释。

> **[建议] 细节注释遵循单行注释的格式。说明必须换行时，每行是一个单行注释的起始。**

示例：

```javascript
function foo(p1, p2, opt_p3) {
    // 这里对具体内部逻辑进行说明
    // 说明太长需要换行
    for (...) {
        ....
    }
}
```


## 3 语言特性


### 3.1 变量


> **[强制] 变量、函数在使用前必须先定义。推荐使用es6 中的 let 和 const;(原生小程序不支持)**

解释：

不通过 var 定义变量将导致变量污染全局环境。


示例：

```javascript
// good
var name = 'MyName';

// bad
name = 'MyName';
```

> **[建议] 每个 `var` 只能声明一个变量。**

解释：

一个 `var` 声明多个变量，容易导致较长的行长度，并且在修改时容易造成逗号和分号的混淆。


示例：

```javascript
// good
var hangModules = [];
var missModules = [];
var visited = {};

// bad
var hangModules = [],
    missModules = [],
    visited = {};
```


> **[强制] 变量必须 `即用即声明`，不得在函数或其它形式的代码块起始位置统一声明所有变量。**

解释：

变量声明与使用的距离越远，出现的跨度越大，代码的阅读与维护成本越高。虽然JavaScript的变量是函数作用域，还是应该根据编程中的意图，缩小变量出现的距离空间。


示例：

```javascript
// good
function kv2List(source) {
    var list = [];

    for (var key in source) {
        if (source.hasOwnProperty(key)) {
            var item = {
                k: key,
                v: source[key]
            };

            list.push(item);
        }
    }

    return list;
}

// bad
function kv2List(source) {
    var list = [];
    var key;
    var item;

    for (key in source) {
        if (source.hasOwnProperty(key)) {
            item = {
                k: key,
                v: source[key]
            };

            list.push(item);
        }
    }

    return list;
}
```


### 3.2 条件

> **[建议] 尽可能使用简洁的表达式。**


示例：

```javascript
// 字符串为空

// good
if (!name) {
    // ......
}

// bad
if (name === '') {
    // ......
}
```

```javascript
// 字符串非空

// good
if (name) {
    // ......
}

// bad
if (name !== '') {
    // ......
}
```

```javascript
// 数组非空

// good
if (collection.length) {
    // ......
}

// bad
if (collection.length > 0) {
    // ......
}
```

```javascript
// 布尔不成立

// good
if (!notTrue) {
    // ......
}

// bad
if (notTrue === false) {
    // ......
}
```

```javascript
// null 或 undefined

// good
if (noValue == null) {
  // ......
}

// bad
if (noValue === null || typeof noValue === 'undefined') {
  // ......
}
```

> **[建议] 对于相同变量或表达式的多值条件，用 `switch` 代替 `if`。**

示例：

```javascript
// good
switch (typeof variable) {
    case 'object':
        // ......
        break;
    case 'number':
    case 'boolean':
    case 'string':
        // ......
        break;
}

// bad
var type = typeof variable;
if (type === 'object') {
    // ......
}
else if (type === 'number' || type === 'boolean' || type === 'string') {
    // ......
}
```

> **[建议] 如果函数或全局中的 `else` 块后没有任何语句，可以删除 `else`。**

示例：

```javascript
// good
function getName() {
    if (name) {
        return name;
    }

    return 'unnamed';
}

// bad
function getName() {
    if (name) {
        return name;
    }
    else {
        return 'unnamed';
    }
}
```


### 3.3 循环


> **[建议] 不要在循环体中包含函数表达式，事先将函数提取到循环体外。**

解释：

循环体中的函数表达式，运行过程中会生成循环次数个函数对象。


示例：

```javascript
// good
function clicker() {
    // ......
}

for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', clicker);
}


// bad
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', function () {});
}
```

> **[建议] 对循环内多次使用的不变值，在循环外用变量缓存。**

示例：

```javascript
// good
var width = wrap.offsetWidth + 'px';
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    element.style.width = width;
    // ......
}


// bad
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    element.style.width = wrap.offsetWidth + 'px';
    // ......
}
```

### 3.4 类型


#### 3.4.1 类型检测


> **[建议] 类型检测优先使用 `typeof`。对象类型检测使用 `instanceof`。`null` 或 `undefined` 的检测使用 `== null`。**

示例：

```javascript
// string
typeof variable === 'string'

// number
typeof variable === 'number'

// boolean
typeof variable === 'boolean'

// Function
typeof variable === 'function'

// Object
typeof variable === 'object'

// RegExp
variable instanceof RegExp

// Array
variable instanceof Array

// null
variable === null

// null or undefined
variable == null

// undefined
typeof variable === 'undefined'
```


#### 3.4.2 类型转换


> **[建议] 转换成 `string` 时，使用 `+ ''`。**

示例：

```javascript
// good
num + '';

// bad
new String(num);
num.toString();
String(num);
```

> **[建议] `string` 转换成 `number`，要转换的字符串结尾包含非数字并期望忽略时，使用 `parseInt`。**

示例：

```javascript
var width = '200px';
parseInt(width, 10);
```


> **[建议] 转换成 `boolean` 时，使用 `!!`。**

示例：

```javascript
var num = 3.14;
!!num;
```

> **[建议] `number` 去除小数点，使用 `Math.floor` / `Math.round` / `Math.ceil`，不使用 `parseInt`。**

示例：

```javascript
// good
var num = 3.14;
Math.ceil(num);

// bad
var num = 3.14;
parseInt(num, 10);
```


### 3.5 字符串


> **[强制] 字符串开头和结束使用单引号 `'`。**

解释：

1. 输入单引号不需要按住 `shift`，方便输入。
2. 实际使用中，字符串经常用来拼接 HTML。为方便 HTML 中包含双引号而不需要转义写法。

示例：

```javascript
var str = '我是一个字符串';
var html = '<div class="cls">拼接HTML可以省去双引号转义</div>';
```

> **[建议] 使用 `数组` 或 `+` 拼接字符串。**

解释：

1. 使用 `+` 拼接字符串，如果拼接的全部是 StringLiteral，压缩工具可以对其进行自动合并的优化。所以，静态字符串建议使用 `+` 拼接。
2. 在现代浏览器下，使用 `+` 拼接字符串，性能较数组的方式要高。
3. 如需要兼顾老旧浏览器，应尽量使用数组拼接字符串。

示例：

```javascript
// 使用数组拼接字符串
var str = [
    // 推荐换行开始并缩进开始第一个字符串, 对齐代码, 方便阅读.
    '<ul>',
        '<li>第一项</li>',
        '<li>第二项</li>',
    '</ul>'
].join('');

// 使用 `+` 拼接字符串
var str2 = '' // 建议第一个为空字符串, 第二个换行开始并缩进开始, 对齐代码, 方便阅读
    + '<ul>',
    +    '<li>第一项</li>',
    +    '<li>第二项</li>',
    + '</ul>';
```

### 3.6 对象


> **[强制] 使用对象字面量 `{}` 创建新 `Object`。**

示例：

```javascript
// good
var obj = {};

// bad
var obj = new Object();
```

> **[建议] 对象创建时，如果任何一个 `属性` 需要添加引号，则所有 `属性` 建议添加 `'`。**

解释：

如果属性不符合 Identifier 和 NumberLiteral 的形式，就需要以 StringLiteral 的形式提供。


示例：

```javascript
// good
var info = {
    'name': 'someone',
    'age': 28,
    'more-info': '...'
};

// bad
var info = {
    name: 'someone',
    age: 28,
    'more-info': '...'
};
```

> **[强制] 不允许修改和扩展任何原生对象和宿主对象的原型。**

示例：

```javascript
// 以下行为绝对禁止
String.prototype.trim = function () {
};
```

### 3.7 数组


> **[强制] 使用数组字面量 `[]` 创建新数组，除非想要创建的是指定长度的数组。**

示例：

```javascript
// good
var arr = [];

// bad
var arr = new Array();
```

> **[建议] 遍历数组不使用 `for in`。**

解释：

数组对象可能存在数字以外的属性, 这种情况下 `for in` 不会得到正确结果。

示例：

```javascript
var arr = ['a', 'b', 'c'];

// 这里仅作演示, 实际中应使用 Object 类型
arr.other = 'other things';

// 正确的遍历方式
for (var i = 0, len = arr.length; i < len; i++) {
    console.log(i);
}

// 错误的遍历方式
for (var i in arr) {
    console.log(i);
}
```

> **[建议] 尽量使用数组的 `sort` 方法。**

解释：

自己实现的常规排序算法，在性能上并不优于数组默认的 `sort` 方法。

> **[建议] 清空数组使用 `.length = 0`。**




### 3.8 函数



#### 3.8.1 函数长度


> **[建议] 一个函数的长度控制在 `50` 行以内。**

解释：

将过多的逻辑单元混在一个大函数中，易导致难以维护。一个清晰易懂的函数应该完成单一的逻辑单元。复杂的操作应进一步抽取，通过函数的调用来体现流程。

特定算法等不可分割的逻辑允许例外。


示例：

```javascript
function syncViewStateOnUserAction() {
    if (x.checked) {
        y.checked = true;
        z.value = '';
    }
    else {
        y.checked = false;
    }

    if (a.value) {
        warning.innerText = '';
        submitButton.disabled = false;
    }
    else {
        warning.innerText = 'Please enter it';
        submitButton.disabled = true;
    }
}

// 直接阅读该函数会难以明确其主线逻辑，因此下方是一种更合理的表达方式：

function syncViewStateOnUserAction() {
    syncXStateToView();
    checkAAvailability();
}

function syncXStateToView() {
    y.checked = x.checked;

    if (x.checked) {
        z.value = '';
    }
}

function checkAAvailability() {
    if (a.value) {
        clearWarnignForA();
    }
    else {
        displayWarningForAMissing();
    }
}
```


#### 3.8.2 参数设计


> **[建议] 一个函数的参数控制在 `6` 个以内。**

解释：

除去不定长参数以外，函数具备不同逻辑意义的参数建议控制在 `6` 个以内，过多参数会导致维护难度增大。


## 4 DOM


> **[建议] 第四章仅供参考。**


### 4.1 元素获取

> **[建议] 对于多个元素的集合，尽可能使用 `context.getElementsByTagName` 获取。其中 `context` 可以为 `document` 或其他元素。指定 `tagName` 参数为 `*` 可以获得所有子元素。**

> **[建议] 遍历元素集合时，尽量缓存集合长度。如需多次操作同一集合，则应将集合转为数组。**

解释：

原生获取元素集合的结果并不直接引用 DOM 元素，而是对索引进行读取，所以 DOM 结构的改变会实时反映到结果中。


示例：

```html
<div></div>
<span></span>

<script>
var elements = document.getElementsByTagName('*');

// 显示为 DIV
alert(elements[0].tagName);

var div = elements[0];
var p = document.createElement('p');
docpment.body.insertBefore(p, div);

// 显示为 P
alert(elements[0].tagName);
</script>
```


> **[建议] 获取元素的直接子元素时使用 `children`。避免使用`childNodes`，除非预期是需要包含文本、注释和属性类型的节点。**




### 4.2 样式获取


> **[建议] 获取元素实际样式信息时，应使用 `getComputedStyle` 或 `currentStyle`。**

解释：

通过 style 只能获得内联定义或通过 JavaScript 直接设置的样式。通过 CSS class 设置的元素样式无法直接通过 style 获取。




### 4.3 样式设置


> **[建议] 尽可能通过为元素添加预定义的 className 来改变元素样式，避免直接操作 style 设置。**

> **[强制] 通过 style 对象设置元素样式时，对于带单位非 0 值的属性，不允许省略单位。**

解释：

除了 IE，标准浏览器会忽略不规范的属性值，导致兼容性问题。




### 4.4 DOM操作


> **[建议] 操作 `DOM` 时，尽量减少页面重构。**

解释：

页面重构是非常耗时的行为，非常容易导致性能瓶颈。下面一些场景会触发浏览器的重构：

- DOM元素的添加、修改（内容）、删除。
- 应用新的样式或者修改任何影响元素布局的属性。
- Resize浏览器窗口、滚动页面。
- 读取元素的某些属性（offsetLeft、offsetTop、offsetHeight、offsetWidth、scrollTop/Left/Width/Height、clientTop/Left/Width/Height、getComputedStyle()、currentStyle(in IE)) 。


> **[建议] 尽量减少 `DOM` 操作。**

解释：

DOM 操作也是非常耗时的一种操作，减少 DOM 操作有助于提高性能。举一个简单的例子，构建一个列表。我们可以用两种方式：

1. 在循环体中 createElement 并 append 到父元素中。
2. 在循环体中拼接 HTML 字符串，循环结束后写父元素的 innerHTML。

第一种方法看起来比较标准，但是每次循环都会对 DOM 进行操作，性能极低。在这里推荐使用第二种方法。




### 4.5 DOM事件


> **[建议] 如使用原生语法优先使用 `addEventListener / attachEvent` 绑定事件，避免直接在 HTML 属性中或 DOM 的 `expando` 属性绑定事件处理。**

解释：

expando 属性绑定事件容易导致互相覆盖。


> **[建议] 使用 `addEventListener` 时第三个参数使用 `false`。**

解释：

标准浏览器中的 addEventListener 可以通过第三个参数指定两种时间触发模型：冒泡和捕获。而 IE 的 attachEvent 仅支持冒泡的事件触发。所以为了保持一致性，通常 addEventListener 的第三个参数都为 false。


> **[建议] 在没有事件自动管理的框架支持下，应持有监听器函数的引用，在适当时候（元素释放、页面卸载等）移除添加的监听器。**
