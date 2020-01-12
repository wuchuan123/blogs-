---
title: "JavaScript this "
date: 2020-01-11T13:12:19+08:00
draft: false
---


#### 1. 之前我们说过 this 是在运行时进行绑定的， 并不是在编写时绑定， 它的上下文取决于函数调
用时的各种条件。 this 的绑定和函数声明的位置没有任何关系， 只取决于函数的调用方式。


#### 2. 当一个函数被调用时， 会创建一个活动记录（有时候也称为执行上下文）。 这个记录会包
含函数在哪里被调用（调用栈）、 函数的调用方法、 传入的参数等信息。 this 就是记录的
其中一个属性， 会在函数执行的过程中用到。

#### 3. 默认绑定 => 绑定全局
~~~javascript
function foo() {
    console.log( this.a );
}

var a = 2;
foo(); // 2
~~~

#### 4. 显示绑定（call,apply,bind)
   1. 硬绑定
~~~javascript
function foo() {
  console.log(this.a);
}

var obj = {
  a: 2
};

var bar = function() {
  foo.call(obj);
};

bar(); // 2

setTimeout(bar, 100); // 2

// 硬绑定的 bar 不可能再修改它的 this
bar.call(window); // 2
~~~

我们来看看这个变种到底是怎样工作的。 我们创建了函数 bar()， 并在它的内部手动调用
了 foo.call(obj)， 因此强制把 foo 的 this 绑定到了 obj。 无论之后如何调用函数 bar， 它总会手动在 obj 上调用 foo。 这种绑定是一种显式的强制绑定， 因此我们称之为硬绑定。
   
   #### 2. API调用的“上下文”


#### 5. 隐式绑定 =>当函数引用有上下文对象时， 隐式绑定规则会把函数调用中的 this 绑定到这个上下文对象。对象属性引用链中只有最顶层或者说最后一层会影响调用位置。在分析隐式绑定时， 我们必须在一个对象内部包含一个指向函数的属性， 并通过这个属性间接引用函数， 从而把 this 间接（隐式） 绑定到这个对象上。
~~~javaScript
function foo() {
  console.log(this.a);
};

var obj = {
  a: 2,
  foo: foo
};

obj.foo(); // 2
~~~

   * 隐式丢失，一个最常见的 this 绑定问题就是被隐式绑定的函数会丢失绑定对象， 也就是说它会应用默认绑定， 从而把 this 绑定到全局对象或者 undefined 上， 取决于是否是严格模式。
~~~javaScript
function foo() {
  console.log(this.a);
};

var obj = {
  a: 2,
  foo: foo
};
var bar = obj.foo; // 函数别名！

var a = "oops, global"; // a 是全局对象的属性

bar(); // "oops, global""
~~~
   * 回调函数
~~~javaScript
function foo() {
  console.log(this.a);
};

function doFoo(fn) {
  // fn 其实引用的是 foo
  fn(); // <-- 调用位置！
};
var obj = {
  a: 2,
  foo: foo
};
var a = "oops, global"; // a 是全局对象的属性
doFoo(obj.foo); // "oops, global"
~~~

#### 6. new绑定
   首先我们重新定义一下 JavaScript 中的“构造函数”。 在 JavaScript 中， 构造函数只是一些使用 new 操作符时被调用的函数。 它们并不会属于某个类， 也不会实例化一个类。 实际上，它们甚至都不能说是一种特殊的函数类型， 它们只是被 new 操作符调用的普通函数而已。
   
   实际上并不存在所谓的“构造函数”， 只有对于函数的“构造调用”。

#### 7. 优先级
    
    显式>new>隐式>默认

### 特殊引用
#### 1. 软绑定

之前我们已经看到过， 硬绑定这种方式可以把 this 强制绑定到指定的对象（除了使用 new
时）， 防止函数调用应用默认绑定规则。 问题在于， 硬绑定会大大降低函数的灵活性， 使
用硬绑定之后就无法使用隐式绑定或者显式绑定来修改 this。
如果可以给默认绑定指定一个全局对象和 undefined 以外的值， 那就可以实现和硬绑定相
同的效果， 同时保留隐式绑定或者显式绑定修改 this 的能力。
~~~javaScript
if (!Function.prototype.softBind) {
  Function.prototype.softBind = function(obj) {
    var fn = this;
    // 捕获所有 curried 参数
    var curried = [].slice.call(arguments, 1);
    var bound = function() {
      return fn.apply(
        (!this || this === (window || global)) ?
        obj : this curried.concat.apply(curried, arguments)
      );
    };
    bound.prototype = Object.create(fn.prototype);
    return bound;
  };
}
~~~
#### 2. 间接引用

另一个需要注意的是， 你有可能（有意或者无意地） 创建一个函数的“间接引用”， 在这
种情况下， 调用这个函数会应用默认绑定规则

箭头函数并不是使用 function 关键字定义的， 而是使用被称为“胖箭头” 的操作符 => 定
义的。 箭头函数不使用 this 的四种标准规则， 而是根据外层（函数或者全局） 作用域来决
定 this。箭头函数的绑定无法被修改。

#### 现在我们可以根据优先级来判断函数在某个调用位置应用的是哪条规则。 可以按照下面的顺序来进行判断：
1. 函数是否在 new 中调用（new 绑定） ？ 如果是的话 this 绑定的是新创建的对象。
var bar = new foo()
2. 函数是否通过 call、 apply（显式绑定） 或者硬绑定调用？ 如果是的话， this 绑定的是
指定的对象。
var bar = foo.call(obj2)
3. 函数是否在某个上下文对象中调用（隐式绑定） ？ 如果是的话， this 绑定的是那个上
下文对象。
var bar = obj1.foo()
4. 如果都不是的话， 使用默认绑定。 如果在严格模式下， 就绑定到 undefined， 否则绑定到
全局对象。
var bar = foo()


#### 使用 new 来调用函数， 或者说发生构造函数调用时， 会自动执行下面的操作。
1. 创建（或者说构造） 一个全新的对象。
2. 这个新对象会被执行 [[ 原型 ]] 连接。
3. 这个新对象会绑定到函数调用的 this。
4. 如果函数没有返回其他对象， 那么 new 表达式中的函数调用会自动返回这个新对象.

#### 如果要判断一个运行中函数的 this 绑定， 就需要找到这个函数的直接调用位置。 找到之后
就可以顺序应用下面这四条规则来判断 this 的绑定对象。
1. 由 new 调用？ 绑定到新创建的对象。
2. 由 call 或者 apply（或者 bind） 调用？ 绑定到指定的对象。
3. 由上下文对象调用？ 绑定到那个上下文对象。
4. 默认： 在严格模式下绑定到 undefined， 否则绑定到全局对象。