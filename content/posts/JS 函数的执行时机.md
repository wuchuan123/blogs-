---
title: "JS 函数的执行时机"
date: 2020-01-05T18:58:19+08:00
draft: false
---

### 1. 解释为什么如下代码会打印 6 个 6

~~~JavaScript
let i = 0
for(i = 0; i<6; i++){
    setTimeout(()=>{
    console.log(i)
    },0)
}
~~~
#### 答： 
因为 **setTimeout()** 方法的意思是等一会打印出 **i** 的值，他要等循环先执行完，才会打印。循环执行完**i===6**，所以会打印6个6。

1. 就是for循环要先执行完6次，**i**变成了6；
2. 然后 **setTimeout()** 方法在进入循环，打印6次；

### 2. 写出让上面代码打印 0、1、2、3、4、5 的方法
#### 答：
~~~JavaScript
for(let i = 0; i<6; i++){
    setTimeout(()=>{
    console.log(i)
    },0)
}
~~~
### 3. 除了使用 for let 配合，还有什么其他方法可以打印出 0、1、2、3、4、5
#### 答：
~~~JavaScript
let i = 0;
while (i < 5) {
  i++;
  console.log(i)
}
~~~