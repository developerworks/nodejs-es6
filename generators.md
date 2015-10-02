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