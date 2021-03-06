# 对象

JavaScript的简单数据类型包括数字、字符串、布尔值、null值和undefined值。其他所有的值都是对象。

JavaScript中的对象是可变的键控集合。

对象是属性的容器，其中每个属性都拥有名字和值。属性的名字可以是包括空字符串在内的任意字符。属性值可以是除undefined值以外的任何值。

JavaScript里的对象是无类型的，对新属性的名字和属性的值没有限制。对象适合用于汇集和管理数据。

## 对象字面量

一个对象字面量就是包围在一对花括号中的零或多个Key/Value对。

```javascript
var empty_object = {};

var stooge = {
    "first-name" : "Jerome",
    "last-name" : "Howard"
};
```

属性名可以是包括空字符串在内的任何字符串。

如果属性名是一个合法的JavaScript标识符且不是保留字，则并不强制要求用括号括住属性名。

对象是可嵌套的。

## 检索

检索对象里包含的值可以采用`[]`括住一个字符串表达式的方式。如果字符串表达式是一个字符串字面量，而且是一个合法的JavaScript标识符且不是保留字，那么也可以用`.`表示法替代。

优先使用`.`，因为更加紧凑且可读性更好。

如果尝试检索一个并不存在的成员属性的值，则将返回**undefined**；

`||`可以用来填充默认值：

```javascript
var status = flight.status || "unknown"; //默认值为"unknown"
```

## 更新

对象里的值可以通过赋值语句来更新，如果属性名已经存在 于对象里，那么这个属性的值就会被替换。

## 引用

对象通过引用来传递

```javascript
var a = {}, b = {}, c = {};
// a、b、c每个都引用一个不同的空对象
var a = b = c = {};
// a、b、c每个都引用同一个空对象
```

## 原型

每个对象都连接到一个原型对象，并且它可以从中继承属性。

所有通过对象字面量创建的对象都连接到`Object.prototype`，它是JavaScript中的标配对象。

原型连接只有在检索值的时候才被用到。如果尝试去获取对象的某个属性值，但该对象没有该属性名，那么JavaScript会试着从原型中寻找，依此类推，直到该过程最后到达终点`Object.prototype`。如果想要的属性完全不存在于原型链中，那么结果就是undefined值。这个过程称为委托。

原型关系是一种动态的关系，如果添加一个新的属性到原型中，该属性会立即对所有基于该原型创建的对象可见。

## 反射

检查对象并确定对象有什么属性是很容易的事，只要尝试去检索该属性并验证取得的值。

两种方法去除不需要的属性：

1. 让程序做检查并丢弃为函数的属性
2. 使用`hasOwnProperty`方法

## 枚举

`for in`语句可用来遍历一个对象中的所有属性名。属性名出现的顺序是不确定的，因此`for in`语句不保证顺序。解决办法之一：创建一个数组，在其中以正确的顺序包含属性名。

## 删除

delete运算符可以用来删除对象的属性，不会触及原型链中的任何对象。

删除对象的属性可能会让来自原型链中的属性透现出来。

## 减少全局变量污染

JavaScript可以随意地定义全局变量来容纳应用的所有资源。但是全局变量削弱了程序的灵活性，应该避免使用。

闭包是另外一种有效减少全局污染的方法。