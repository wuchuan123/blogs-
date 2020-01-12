new命令的原理
使用new命令时，它后面的函数依次执行下面的步骤。

创建一个空对象，作为将要返回的对象实例。
将这个空对象的原型，指向构造函数的prototype属性。
将这个空对象赋值给函数内部的this关键字。
开始执行构造函数内部的代码。

重要1:JS公式
第一个重要知识：JS公式
对象.__proto__===其构造函数.prototype
JS唯一公式，如果不会就套公式

重要2:根公理
Object.prototype是所有对象的(直接或间接)原型
加了一个直接或间接，所谓公理就是规定好的

重要3：函数公理
所有函数都是由Function构造的
任何函数.__proto__ === Function.prototype
任意函数有Object/Array/Function

除了静态方法，还有不少方法定义在Object.prototype对象。它们称为实例方法，所有Object的实例对象都继承了这些方法。

Object实例对象的方法，主要有以下六个。

Object.prototype.valueOf()：返回当前对象对应的值。
Object.prototype.toString()：返回当前对象对应的字符串形式。
Object.prototype.toLocaleString()：返回当前对象对应的本地字符串形式。
Object.prototype.hasOwnProperty()：判断某个属性是否为当前对象自身的属性，还是继承自原型对象的属性。
Object.prototype.isPrototypeOf()：判断当前对象是否为另一个对象的原型。
Object.prototype.propertyIsEnumerable()：判断某个属性是否可枚举。

JSON 格式（JavaScript Object Notation 的缩写）

this就是属性或方法“当前”所在的对象
内部的this就会指向f运行时所在的对象（本例是顶层对象）。
现在问题就来了，由于函数可以在不同的运行环境执行，所以需要有一种机制，能够在函数体内部获得当前的运行环境（context）。所以，this就出现了，它的设计目的就是在函数体内部，指代函数当前的运行环境。

this主要有以下几个使用场合。

（1）全局环境

全局环境使用this，它指的就是顶层对象window。

（2）构造函数

构造函数中的this，指的是实例对象。

（3）对象的方法

如果对象的方法里面包含this，this的指向就是方法运行时所在的对象。该方法赋值给另一个对象，就会改变this的指向。