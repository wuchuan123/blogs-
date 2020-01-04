---
title: "HTML5常用标签"
date: 2019-12-28T10:12:19+08:00
draft: false
---

### 一. a 标签的用法

1. 他的作用：

   - 跳转外部页面
   - 跳转内部锚点
   - 跳转到邮箱或电话等

2. 他的属于有:

   href:

   - 取值：
     - 网址例如：
       - https://qq.com
       - http://qq.com
       - //qq.com(推荐这种)
     - 路径例如：
       - /a/b/c
       - a/b/c
       - index.html 或者 ./index.html
     - 伪协议：
       - javascript：代码；
       - maito:邮箱
       - tel:手机号
     - id：
       - href=#xxx；

   target:

   - 取值：
   - 内置名字：
     - \_blank
     - \_top
     - \_parent
     - \_self
   - 程序员命名：
     - window 的 name
     - iframe 的 name

   download:

   作用：

   - 不是打开页面，而是下载页面

   - 问题：
   - 不是所有浏览器都支持，尤其是手机浏览器可能不支持

   rel = noopener:

   作用：

   - 是否新开一个页面

### 二. img 标签的用法:

1. 他的作用：

   - 发出 get 请求，展示一张图片

2. 他的属于有:

   - alt:属性包含一条对图像的文本描述，这不是强制性的，但对可访问性而言，它难以置信地有用——屏幕阅读器会将这些描述读给需要使用阅读器的使用者听，让他们知道图像的含义。

   * height:图片的高度

   * width:图片的宽度

   * src:属性是必须的，它包含了你想嵌入的图片的文件路径

3. 支持事件:

   - onload(加载)/onerror(加载失败)

4. 响应式:
   - max-width:100%(可以自适应屏幕宽度)
5. 他是可替换元素

### 三. table 标签的用法:

1. 相关的标签:

   - table
   - thead
   - tbody
   - tfoot
   - tr
   - td
   - th

建立表格示例：

```html5
<table>
    <thead>
        <tr>
            <th></th>
            <th></th>
        </tr>
    <th>
    </thead>

    <tbody>
        <tr>
            <td></td>
            <td></td>
        </tr>
    </tbody>

    <tfoot>
        <tr>
            <td></td>
            <td></td>
        </tr>
    </tfoot>
</table>  //table必须与这几个元素搭配使用。
```

1. 相关的样式：

**table-layout**：CSS 属性定义了用于布局表格单元格，行和列的算法。

table-layout 取值：

- auto(默认值):大多数浏览器采用自动表格布局算法对表格布局。表格及单元格的宽度取决于其包含的内容。

* fixed:表格和列的宽度通过表格的宽度来设置，某一列的宽度仅由该列首行的单元格决定。在当前列中，该单元格所在行之后的行并不会影响整个列宽。

**border-collapse**:是用来决定表格的边框是分开的还是合并的。在分隔模式下，相邻的单元格都拥有独立的边框。在合并模式下，相邻单元格共享边框。

border-collapse 取值：

- collapse:合并（collapsed ）模式下，表格中相邻单元格共享边框。在这种模式下，CSS 属性 border-style 的值 inset 表现为槽，值 outset 表现为脊。

* separate:分隔（separated）模式是 HTML 表格的传统模式。相邻单元格都拥有不同的边框。边框之间的距离是通过 CSS 属性 border-spacing 来确定的。

**border-sapcing**:属性指定相邻单元格边框之间的距离,初始值 "0".

### 四. 个人感想:

1. HTML5 标签和属性一定要多用
2. 不懂的标签和属性 MDN 上查找
3. 标签要理解记忆，死记容易忘记
4. 前端工程师最大的忌讳是图片在网页上变形
