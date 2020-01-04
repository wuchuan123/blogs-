---
title: "CSS 知识总结"
date: 2019-12-31T13:12:19+08:00
draft: false
---

### 一. 浏览器渲染原理

CSSOM 树和 DOM 树合并成渲染树，然后用于计算每个可见元素的布局，并输出给绘制流程，将像素渲染到屏幕上。优化上述每一个步骤对实现最佳渲染性能至关重要。

- DOM 树与 CSSOM 树合并后形成渲染树。
- 渲染树只包含渲染网页所需的节点。
- 布局计算每个对象的精确位置和大小。
- 最后一步是绘制，使用最终渲染树将像素渲染到屏幕上。

第一步是让浏览器将 DOM 和 CSSOM 合并成一个“渲染树”，网罗网页上所有可见的 DOM 内容，以及每个节点的所有 CSSOM 样式信息。

![Image](/images/render-tree-construction.jpg)

### 二. CSS 动画的两种做法（transition 和 animation）

1. **transition CSS** 属性是 transition-property(属性名)，transition-duration(时长)，transition-timing-function(过渡方式) 和 transition-delay(延时) 的一个简写属性。

   **transition**一般配合**transform**使用；

   **transform**属性允许你旋转，缩放，倾斜或平移给定元素。这是通过修改 CSS 视觉格式化模型的坐标空间来实现的。
   **transform**有四个常用属性

   - translate 位移
   - scale 缩放(甚用会出现图片模糊)
   - rotate 旋转
   - skew 倾斜
     他们都作用在 X,Y,Z 轴上；
     下面这段代码定义了属性 transition,动画时长 1s，线性移动；

```html
<!DOCTYPE html>
<!--HTML-->
<html>
  <head>
    <meta charset="utf-8" />
    <title>JS Bin</title>
  </head>
  <body>
    <div class="wrapper">
      <div id="demo"></div>
      <button id="button">开始</button>
    </div>
  </body>
</html>
```

```CSS
/*CSS*/
#demo{
  width: 100px;
  height: 100px;
  border: 1px solid red;
  margin: 50px;
  transition: transform 1s linear;
}

#demo.b{
  transform: translateX(200px);
}
#demo.c{
  transform: translateX(200px) translateY(100px);
}

```

```JavaScript
//JavaScript
button.onclick = ()=>{

  demo.classList.add('b')
  setTimeout(()=>{
    demo.classList.remove('b')
    demo.classList.add('c')
  },1000)
}
```

最终效果：

![示例](/images/示例.gif)

1. **animation**属性是 animation-name(动画名)，animation-duration(持续时长) animation-timing-function(延时)，animation-delay(延时)，animation-iteration-count(次数)，animation-direction(方向)，animation-fill-mode(填充模式) 和 animation-play-state(状态) 属性的一个简写属性形式。

下面是一个关于**animation**使用的案例：

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>JS Bin</title>
  </head>
  <body>
    <div id="heart">
      <div class="left"></div>
      <div class="right"></div>
      <div class="bottom"></div>
    </div>
  </body>
</html>
```

```CSS
/*CSS*/
*{box-sizing: border-box;}
#heart{
  display: inline-block;
  margin: 100px;
  position: relative;
  animation: .5s heart infinite alternate-reverse;

}
@keyframes heart {
  0%{
    transform: scale(1);
  }
  100%{
    transform: scale(1.2);
  }
}

#heart>.left{
  background: red;
  width: 50px;
  height: 50px;
  position: absolute;
  transform: rotate(45deg) translateX(31px);
  bottom: 50px;
  left: -50px;
  border-radius: 50% 0 0 50%;
}
#heart>.right{
  background: red;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  position: absolute;
  transform: rotate(45deg) translateY(31px);
  bottom: 50px;
  right: -50px;
  border-radius: 50% 50% 0 0;
}
#heart>.bottom{
  background: red;
  width: 50px;
  height: 50px;
  transform: rotate(45deg);
}
```

最终效果：

![gif](/images/示例2.gif)

### 三. CSS 学法总结

1. CSS 的规则是没有规则
2. 务必掌握 float、flex 布局，了解 grid 布局
3. 不懂的 MDN
4. 调试大法！调试大法！调试大法！

```CSS
border:1px solid red;
```

5. 起手式！起手式！起手式！

```CSS
*{margin:0;padding:0;box-sizing: border-box;}
```

6. 一定要动手调试每一个属性

<body class="avenir bg-near-white">
