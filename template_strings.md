# 模板字符串

模板字符串可以嵌入表达式的字符串字面量. 可以使用模板字符串实现多行字符串和字符串插值功能

## 语法

```js
`string text`

`string text line 1
 string text line 2`

`string text ${expression} string text`

tag `string text ${expression} string text`
```

## 描述


### 多行字符串

为了实现多行字符串, 通常情况下采用一般的方式为:

```js
console.log("string text line 1\n"+
"string text line 2");
// "string text line 1
// string text line 2"
```

现在,如果使用模板字符串, 代码可以用如下方式书写, 提供可读性:

```js
var a = 5;
var b = 10;
console.log(`Fifteen is ${a + b} and\nnot ${2 * a + b}.`);
// "Fifteen is 15 and
// not 20."
```

### 标记的模板字符串

模板字符串的一个更加高级的形式是`tagged`模板字符串. 其可以使用一个函数来修改模板字符串的输出. 第一个参数为字符串字面量数组(此例中为"Hello " 和" world"). 


```js
var a = 5;
var b = 10;

function tag(strings, ...values) {
  console.log(strings[0]); // "Hello "
  console.log(strings[1]); // " world "
  console.log(values[0]);  // 15
  console.log(values[1]);  // 50

  return "Bazinga!";
}

tag`Hello ${ a + b } world ${ a * b}`;
// "Bazinga!"
```

### 原始(Raw)字符串

`tagged`模板字符串的第一个函数参数有一个特殊的`raw`属性, 允许你访问模板字符串的原始内容.

```js
function tag(strings, ...values) {
  console.log(strings.raw[0]); 
  // "string text line 1 \\n string text line 2"
}

tag`string text line 1 \n string text line 2`;
```

In addition, the `String.raw()` method exists to create raw strings just like the default template function and string concatenation would create.

```js
String.raw`Hi\n${2+3}!`;
// "Hi\\n5!"
```

### 安全

因为在模板字符串中能够访问函数和变量, 请不要让不被信任的用户使用.(比如由用户提供内容的应用)

```js
`${console.warn("this is",this)}`; // "this is" Window

let a = 10;
console.warn(`${a+=20}`); // "30"
console.warn(a); // 30
```


















