---
title: "jQuery学习小结"
date: 2020-01-12T19:43:19+08:00
draft: false
---

### 1. jQuery 如何获取元素

jQuery的基本设计思想和主要用法，就是"选择某个网页元素，然后对其进行某种操作"。这是它区别于其他Javascript库的根本特点。

使用jQuery的第一步，往往就是将一个选择表达式，放进构造函数jQuery()（简写为$），然后得到被选中的元素。

选择表达式可以是CSS选择器：
~~~javascript
$(document) //选择整个文档对象

$('#myId') //选择ID为myId的网页元素

$('div.myClass') // 选择class为myClass的div元素

$('input[name=first]') // 选择name属性等于first的input元素
~~~
也可以是jQuery特有的表达式：
~~~javascript
$('a:first') //选择网页中第一个a元素

$('tr:odd') //选择表格的奇数行

$('#myForm :input') // 选择表单中的input元素

$('div:visible') //选择可见的div元素

$('div:gt(2)') // 选择所有的div元素，除了前三个

$('div:animated') // 选择当前处于动画状态的div元素
~~~

### 2. jQuery 的链式操作是怎样的

jQuery的链式操作，就是最终选中网页元素以后，可以对它进行一系列操作，并且所有操作可以连接在一起，以链条的形式写出来，比如：
~~~javascript
$('div').find('h3').eq(2).html('Hello');
~~~
分解开来，就是下面这样：
~~~javascript
$('div') //找到div元素

.find('h3') //选择其中的h3元素

.eq(2) //选择第3个h3元素

.html('Hello'); //将它的内容改为Hello
~~~
这是jQuery最令人称道、最方便的特点。它的原理在于每一步的jQuery操作，返回的都是一个jQuery对象，所以不同操作可以连在一起。

jQuery还提供了.end()方法，使得结果集可以后退一步：
~~~javascript
$('div')

.find('h3')

.eq(2)

.html('Hello')

.end() //退回到选中所有的h3元素的那一步

.eq(0) //选中第一个h3元素

.html('World'); //将它的内容改为World
~~~
### 3. jQuery 如何创建元素
创建新元素的方法非常简单，只要把新元素直接传入jQuery的构造函数就行了：
~~~javascript
$('<p>Hello</p>');

$('<li class="new">new list item</li>');

$('ul').append('<li>list item</li>');
~~~

### 4. jQuery 如何移动元素
jQuery移动元素，就是提供两组方法，来操作元素在网页中的位置移动。一组方法是直接移动该元素，另一组方法是移动其他元素，使得目标元素达到我们想要的位置。

假定我们选中了一个div元素，需要把它移动到p元素后面。

第一种方法是使用.insertAfter()，把div元素移动p元素后面：
~~~javascript
$('div').insertAfter($('p'));
~~~

第二种方法是使用.after()，把p元素加到div元素前面：
~~~javascript
$('p').after($('div'));
~~~
表面上看，这两种方法的效果是一样的，唯一的不同似乎只是操作视角的不同。但是实际上，它们有一个重大差别，那就是返回的元素不一样。第一种方法返回div元素，第二种方法返回p元素。你可以根据需要，选择到底使用哪一种方法。

使用这种模式的操作方法，一共有四对：
~~~javascript
.insertAfter()和.after()：在现存元素的外部，从后面插入元素

.insertBefore()和.before()：在现存元素的外部，从前面插入元素

.appendTo()和.append()：在现存元素的内部，从后面插入元素

.prependTo()和.prepend()：在现存元素的内部，从前面插入元素
~~~

### 5. jQuery 如何修改元素的属性
* .addClass() 为每个匹配的元素添加指定的样式类名
* .attr()  获取匹配的元素集合中的第一个元素的属性的值。设置每一个匹配元素的一个或多个属性。
* .hasClass()
确定任何一个匹配元素是否有被分配给定的（样式）类。
* DOM 属性 | DOM 操作 > DOM 插入现有元素内
.html()
获取集合中第一个匹配元素的HTML内容 设置每一个匹配元素的html内容。
* .prop()
获取匹配的元素集中第一个元素的属性（property）值为匹配的元素设置一个或多个属性（properties）。
* .removeAttr()
为匹配的元素集合中的每个元素中移除一个属性（attribute）。
* .removeClass()
移除集合中每个匹配元素上一个，多个或全部样式。
* .removeProp()
为集合中匹配的元素删除一个属性（property）。
* .toggleClass()
在匹配的元素集合中的每个元素上添加或删除一个或多个样式类,取决于这个样式类是否存在或值切换属性。即：如果存在（不存在）就删除（添加）一个类。
* .val()
获取匹配的元素集合中第一个元素的当前值。设置匹配的元素集合中每个元素的值。

参考链接：

[阮一峰的jQuery设计思想](http://www.ruanyifeng.com/blog/2011/07/jquery_fundamentals.html)

[jQuery中文帮助文档](https://www.jquery123.com/category/attributes/)