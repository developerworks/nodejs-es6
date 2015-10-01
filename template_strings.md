# 模板字符串

模板字符串可以嵌入表达式的字符串字面量. 可以使用模板字符串实现多行字符串和字符串插值功能

## 语法

```
`string text`

`string text line 1
 string text line 2`

`string text ${expression} string text`

tag `string text ${expression} string text`
```

## 描述


### 多行字符串

为了实现多行字符串, 通常情况下采用一般的方式为:

```
console.log("string text line 1\n"+
"string text line 2");
// "string text line 1
// string text line 2"
```

现在,如果使用模板字符串, 代码可以用如下方式书写, 提供可读性:

```
var a = 5;
var b = 10;
console.log(`Fifteen is ${a + b} and\nnot ${2 * a + b}.`);
// "Fifteen is 15 and
// not 20."
```