---
title: "JS对象的基本用法"
date: 2020-01-01T13:12:19+08:00
draft: false
---

### 1. 声明对象的两种语法

示例：

```JavaScript
let obj = {'name': 'frank', 'age': 18}

let obj = new Object({'name': 'frank', 'age': 18})
// 一般使用第一种
```

### 2. 如何删除对象的属性

- delete 命令用于删除对象的属性，删除成功后返回 true。
- delete obj.xxx 或者 delete obj['xxx'] 这俩种都可以删除对象属性。

- 下面代码中，**delete**命令删除对象**obj**的**p**属性。删除后，再读取**p**属性就会返回**undefined**，而且**Object.keys**方法的返回值也不再包括该属性。

  ```JavaScript
  var obj = { p: 1 };
  Object.keys(obj) // ["p"]
  delete obj.p // true
  obj.p // undefined
  Object.keys(obj) // []
  ```

### 3. 如何查看对象的属性

- 查看一个对象本身的所有属性，可以使用**Object.keys**方法。

  ```JavaScript
  var obj = {
  key1: 1,
  key2: 2
    };

  Object.keys(obj);
  // ['key1', 'key2']
  ```

### 4. 如何修改或增加对象的属性

- 修改自身属性，直接赋值，如下代码：

  ```javascript
  let obj = { name: "frank" };
  obj.name; //"frank"
  let key = "name";
  obj[key] === "frank"; //true
  ```

- 批量赋值，如下代码:
  ```javascript
  Object.assign(obj, { color: "red", age: 18 });
  ```
- 修改共有属性

  ```javascript
  Object.prototype["toString"] = "xxx";
  //
  obj.__proto__["toString"] = "xxx";
  //不推荐这种
  ```

- 改原型

  ```javascript
  let obj = Object.create(common);
  //
  obj.__proto__ = common;
  //不推荐这种
  ```

- 增加属性

  基本和改一样，已有属性则该，没有属性就增加；

### 5. 'name' in obj 和 obj.hasOwnProperty('name') 的区别

- 他们俩个都是判断属性名是否存在在对象里
- 区别是**in** 会继承原型链上的属性，而 obj.hasOwnPropert 不会继承原型链的属性。
