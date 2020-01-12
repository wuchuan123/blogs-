---
title: "new、call、apply、bine函数的实现"
date: 2020-01-12T17:43:19+08:00
draft: false
---
原型,共有属性：
修改共有属性
obj.__proto__.toString='xxx' //不推荐
Object.prototype.toString='xxx'
修改原型
obj.__proto__=common
let obj = Object.create(common)