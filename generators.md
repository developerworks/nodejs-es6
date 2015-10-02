# 生成器

`function*`声明(function关键字后跟一个`*`号)定义一个生成器函数, 它返回一个`Generator`对象.

也可以使用`生成器函数构造器`和`function*`表达式定义生成器函

## 语法

```js
function* name([param[, param[, ... param]]]) {
   statements
}
```

**name**

<p style="text-indent:2em;">函数名称</p>

**param**

<p style="text-indent:2em;">传递给函数的参数名称, 一个函数最多可以又255个参数.</p>

**statements**

<p style="text-indent:2em;">组成函数体的语句</p>

## 描述

生成器是可以退出和从入的函数. 退出时保留上下文, 从入时恢复.

调用生成器函数是并不立即执行其函数体, 而是返回一个迭代器对象. 调用迭代器的`next()`方法后开始执行函数体, 知道碰到第一个`yield`表达式是暂停, `next()`方法返回一个对象, 其中包含一个函数返回的值和一个`done`状态标记字段, `yield*`可以委派其他生成器函数(也就是在生成器函数中调用其他生成器函数), 如果`done`为true, 表示生成器到达了函数中的最后一个`yield`, 生成器函数执行完成.

## 例子

简单例子

```js
function* idMaker(){
  var index = 0;
  while(index < 3)
    yield index++;
}

var gen = idMaker();

console.log(gen.next().value); // 0
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // undefined
// ...
```

生成器函数例子

```js
function* anotherGenerator(i) {
  yield i + 1;
  yield i + 2;
  yield i + 3;
}

function* generator(i){
  yield i;
  yield* anotherGenerator(i);
  yield i + 10;
}

var gen = generator(10);

console.log(gen.next().value); // 10
console.log(gen.next().value); // 11
console.log(gen.next().value); // 12
console.log(gen.next().value); // 13
console.log(gen.next().value); // 20
```