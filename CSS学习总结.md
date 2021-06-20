# CSS学习总结

## 什么是CSS

**CSS**是级联样式表（Cascading Style Sheets）的缩写。HTML 用于撰写页面的内容，而 CSS 将决定这些内容该如何在屏幕上呈现。

> 网页的内容是由 HTML的元素构建的，这些元素如何呈现，涉及许多方面，如整个页面的布局，元素的位置、距离、颜色、大小、是否显示、是否浮动、透明度等等。

## CSS语法

一条CSS样式规则由两个主要的部分构成：选择器，以`{}`包裹的一条或多条声明

- 选择器是您需要改变样式的对象（上图的规则就一级标题生效）。
- 每条声明由一个属性和一个值组成。（无论是一条或多条声明，都需要用`{}`包裹，且声明用`;`分割）
- 属性（property）是您希望设置的样式属性（style attribute）。每个属性有一个值。属性和值被冒号分开。

```css
p{
  color:red;
  text-align:center;  /* 文本居中 */
}
```

#### 选择器

选择器包括**元素选择器**，还有**id选择器**和**class选择器**。其中**class选择器**使用非常普遍。

- **元素选择器**

​       如上例所示。

- **id选择器**

  ```css
  /* 注意：id选择器前有 # 号。 */
  #sky{
    color: blue;
  }
  ```

​       这条规则表明，找到页面上`id`为`sky`的那个元素让它呈现蓝色。

> 由于元素的id值必须唯一， 所以，id 选择器适用范围只有一个元素。

- **class选择器**

  ```css
  /* 注意：class选择器前有 . 号。 */
  .center{
    text-align: center;
  }
  .large{
    font-size: 30px;
  }
  .red{
    color: red;
  }
  ```

​        以上代码定义了三条规则，分别应用于页面上对应的元素，如只要页面上某元素的`class`为`red`,那        

​        么就让它呈现红色。   

```html
<p class="center">我会居中显示的</p>
<p class="red">我是红色的</p>
<p class="center large red">我又红又大还居中</p>
```

​    

> 由于元素的class值可以多个，也可以重复。因此，实际应用中，class 选择器应用非常普遍。

## CSS如何生效

我们一般有三种方法：**外部样式表**，**内部样式表**，**内联样式表**

#### 外部样式表

新建一个 HTML文件（后缀为.html)，再在同一目录新建一个样式表文件mycss.css（注意后缀名为css）,这就叫做外部样式表。如下：

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <!-- 注意下面这个语句，将导入外部的 mycss.css 样式表文件 -->
  <link rel="stylesheet" type="text/css" href="mycss.css">
  <title>页面标题</title>
</head>
<body>
  <h1>我是有样式的</h1>
  <hr>
  <p class="haha">还是有点丑：)</p>
</body>
</html>
```

```css
body {
  background-color: linen;
  text-align: center;
}
h1 {
  color: red;
}
.haha {
  margin-top: 100px;
  color: chocolate;
  font-size: 50px;
}
```

> **提示：** 引入外部样式表是我们使用样式的主流方式，因为众多的样式规则单独放在一个文件中，与 HTML 内容分开，结构清晰。同时其它页面也可使用，达到复用的目的。

#### 内部样式表

我们也可以将样式放在 HTML 文件中，这称为内部样式表。但注意在`<head>`元素中引入了`<style>`标签，放入了样式。如：

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>页面标题</title>
  <style>
    body {
      background-color: linen;
      text-align: center;
    }
    h1 {
      color: red;
    }
    .haha {
      margin-top: 100px;
      color: chocolate;
      font-size: 50px;
    }
  </style>
</head>
<body>
  <h1>我是有样式的</h1>
  <hr>
  <p class="haha">还是有点丑：)</p>
</body>
</html>
```

> **提示：** 一般而言，只有页面的样式规则较少时可采用这种方式。

#### 内联样式表

所谓内联样式，就是直接把样式规则直接写到要应用的元素中，如：

```html
<h3 style="color:green;">I am a heading</h3>
```

> **提示：** 内联样式是最不灵活的一种方式，完全将内容和样式合在一起，实际应用中非常少见。

#### 级联的优先级

样式的优先级问题，从高到低分别是：

1. 内联样式
2. 内部样式表或外部样式表
3. 浏览器缺省样式

> **提示：** 其实，一句话可总结为哪个样式定义离元素的距离近，哪个就生效。
>
> 因此虽然内部样式和外部样式是具有相同的优先级，但谁出现的位置靠后，谁就优先。

## 颜色，尺寸，对齐

#### 颜色

可以采用**颜色名称**也可以使用**颜色RGB16进制值**，来设定前景或背景的颜色。

```html
<!-- 颜色名称 -->
<h3 style="background-color:Tomato;">Tomato</h3>
<h3 style="background-color:Orange;">Orange</h3>
<h3 style="background-color:DodgerBlue;">DodgerBlue</h3>
<h3 style="background-color:MediumSeaGreen;">MediumSeaGreen</h3>
<h3 style="background-color:Gray;">Gray</h3>
<h3 style="background-color:SlateBlue;">SlateBlue</h3>
<h3 style="background-color:Violet;">Violet</h3>
<h3 style="background-color:LightGray;">LightGray</h3>
<hr>
<!-- 颜色值，3个字节分别代表RGB（Red，Green，Blue）的0～255的值 -->
<h3 style="background-color:#ff0000;">#ff0000</h3>
<h3 style="background-color:#0000ff;">#0000ff</h3>
<h3 style="background-color:#3cb371;">#3cb371</h3>
<h3 style="background-color:#ee82ee;">#ee82ee</h3>
<h3 style="background-color:#ffa500;">#ffa500</h3>
<h3 style="background-color:#6a5acd;">#6a5acd</h3>
```

#### 尺寸

我们可以用 `height` 和 `width` 设定元素内容占据的尺寸。常见的尺寸单位有：像数 `px`，百分比 `%`等。

```css
.example-1 {
  height: 100px;
  width: 500px;
  background-color: rgb(73, 138, 60);
  text-align: right;
}
```

#### 对齐

对于**元素中的文本**，我们可以简单的设置`text-align`属性为`left, center, right`即可（显然缺省的是左对齐），至于元素本身如何对齐，我们后面再讨论。

## 盒子模型

盒子模型指的是一个 HTML 元素可以看作一个盒子。从内到外，这个盒子是由**内容 content, 内边距 padding, 边框 border, 外边距 margin**构成的，如下图所示：

![](https://qige.io/web/brief-css/img/bd78f5d3be0673d6.jpg)

**说明：**

- Content 盒子的内容，如文本、图片等
- Padding 填充，也叫内边距，即内容和边框之间的区域
- Border 边框，默认不显示
- Margin 外边距，边框以外与其它元素的区域

> 留意上图，你会发现一个元素真正占据的宽度应该是：
> 左外边距 + 左边框宽度 + 左内边距 + 内容宽度 + 右内边距 + 右边框宽度 + 右外边距
>
> 因此，我们在用`width`属性设置元素的宽度时，实际上只设置了其内容的宽度

#### 边框与边距

> **提示：** 无论边框、内边距还是外边距，它们都有上下左右四个方向。

**边框**

如下代码所示

```html
<p class="example-1">I have black borders on all sides.</p>
<p class="example-2">I have a blue bottom border.</p>
<p class="example-3">I have rounded grey borders.</p>
<p class="example-4">I have a purple left border.</p>
```

```css
.example-1 {
  border: 1px dotted black; /* 上下左右都相同 */
}
.example-2 {
  border-bottom: 1px solid blue; /* 只设置底部边框 */
}
.example-3 {
  border: 1px solid grey;
  border-radius: 15px; /* 边框圆角 */
}
.example-4 {
  border-left: 5px solid purple;
}
```

**边框样式（border-style属性）：**

| 属性值 | 效果                                                  |
| ------ | ----------------------------------------------------- |
| none   | 默认无边框                                            |
| dotted | 定义一个点线边框                                      |
| dashed | 定义一个虚线边框                                      |
| solid  | 定义一个实线边框                                      |
| double | 定义两个边框， 两个边框的宽度和 border-width 的值相同 |
| groove | 定义3D沟槽边框。效果取决于边框的颜色值                |
| ridge  | 定义3D脊边框。效果取决于边框的颜色值                  |
| inset  | 定义一个3D的嵌入边框。效果取决于边框的颜色值          |
| outset | 定义一个3D突出边框。 效果取决于边框的颜色值           |

[尝试一下](https://www.runoob.com/try/try.php?filename=trycss_border-style)

**边距**

如下代码所示，以内边距为例：

```css
padding: 20px; /* 上下左右都相同 */
padding-top: 20px;
padding-bottom: 100px;
padding-right: 50px;
padding-left: 80px;
padding: 25px 50px 75px 100px; /* 简写形式，按上，右，下，左顺序设置 */
padding: 25px 10px; /* 简写形式，上下为25px，左右为10px */
```

外边距与此类似。

> 简写时的顺序为上，右，下，左（顺时针顺序）。

### 定位

position属性用于对元素进行定位。该属性有以下一些值：

- static静态
- relative相对
- fixed固定
- absolute绝对

> 设置了元素的position属性后，才能使用top，bottom，left，right属性，否则定位无效

**static**

设置为静态定位`position: static`;，这是元素的默认定位方式，也即你设置与否，元素都将按正常的页面布局进行。

> 即：按照元素在 HTML出现的先后顺序从上到下，从左到右进行元素的安排。

**relative**

设置为相对定位`position: relative`;，这将把元素相对于他的静态（正常）位置进行偏移
试试如下的代码：

```css
<!-- HTML -->
<div class="example-relative">我偏移了正常显示的位置。去掉我的样式对比看看？</div>
<!-- CSS -->
.example-relative {
  position: relative;
  left: 60px;
  top: 40px;
  background-color: rgb(173, 241, 241);
}
```

**fixed**

设置为固定定位`position: fixed;`，这将使得元素固定不动（即使你上下左右拖动浏览器的滚动条）。
此时元素固定的位置仍由top, bottom, left, right属性确定，但相对的是视口（viewport，就是浏览器的屏幕可见区域）
如下的代码将会在浏览器右下角固定放置一个按钮元素：

```css
<!-- HTML -->
<div class="broad">占位区域。请将浏览器窗口改变大小，看看右下角的按钮发生了什么？</div>
<div class="example-fixed">这个按钮是固定的</div>
<!-- CSS -->
.example-fixed {
  position: fixed;
  bottom: 40px;
  right: 10px;
  padding: 6px 24px;
  border-radius: 4px;
  color: #fff;
  background-color: #9d0f0f;
  cursor: pointer;
  box-shadow: 0 3px 3px 0 rgba(0,0,0,0.3), 0 1px 5px 0 rgba(0,0,0,0.12), 0 3px 1px -2px rgba(0,0,0,0.2);
}
.broad {
  height: 5000px;
  width: 5000px;
  padding: 20px;
  background-color: darkkhaki;
}
```

**absolute**

设置为绝对定位`position: absolute;`，将使元素相对于其**最近设置了定位属性（非static）的父元素**进行偏移。
如果该元素的所有父元素都没有设置定位属性，那么就相对于`<body>`这个父元素

> **注意：** 绝对定位此处可能有些混淆，请留意其是仍是相对的，不过是相对**最近的父元素**

```css
<!-- HTML -->
<div class="example-relative">这是父元素，有 relative 定位属性
  <div class="example-absolute">
    这是子元素，有 absolute 定位属性
  </div>
</div>
<!-- CSS -->
.example-relative {
  position: relative;
  width: 400px;
  height: 200px;
  border: 3px solid rgb(87, 33, 173);
}
.example-absolute {
  position: absolute;
  top: 80px;
  right: 5px;
  width: 200px;
  height: 100px;
  border: 3px solid rgb(218, 73, 16);
}
```

### 溢出

当元素内容超过其指定的区域时，我们通过溢出`overflow`属性来处理这些溢出的部分。
溢出属性有一下几个值：

- visible 默认值，溢出部分不被裁剪，在区域外面显示
- hidden 裁剪溢出部分且不可见
- scroll 裁剪溢出部分，但提供上下和左右滚动条供显示
- auto 裁剪溢出部分，视情况提供滚动条

关于滚动，我们还可以单独对上下或左右方向进行，如下代码所示：

```css
<!-- HTML -->
<div class="example-overflow-scroll-y">You can use the overflow property when you want to have better control of the
    layout. The overflow property specifies what happens if content overflows an element's box.
</div>
<!-- CSS -->
.example-overflow-scroll-y {
  width: 200px;
  height: 100px;
  background-color: #eee;
  overflow-y: scroll;
}
```

### 浮动

在一个区域或容器内，我们可以设置`float`属性让某元素水平方向上向左或右进行移动，其周围的元素也会重新排列。

让图片向右浮动即可，代码如下：

```css
<html>
<head>
  <style>
    .example-float-right {
      float: right;
    }
  </style>
</head>
<body>
  <img src="https://mdbootstrap.com/img/Photos/Others/placeholder1.jpg" class="example-float-right" alt="">
  <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quidem, architecto officiis, repellendus
  corporis obcaecati, et commodi quam vitae vel laudantium omnis incidunt repellat qui eveniet fugiat totam
  modi nam vero!</p>
</body>
</html>
```

一个浮动元素会尽量向左或向右移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。
浮动元素之后的元素将围绕它。

一个元素浮动后，其后的元素将尽可能包围它，或者说出现在这个浮动元素的左或右方。
如果希望浮动元素后面的元素在其下方显示，可使用`clear: both`样式来进行清除

### 不透明度

我们可以用`opacity`对任何元素（不过常用于图片）设置不透明度。
值在`[0.0～`1.0]之间，值越低，透明度越高。

试试如下代码：

```css
<html>
<head>
  <style>
    img {
      width: 25%;
      border-radius: 10px;
      float: left;
      margin: 10px;
    }
    .opacity-2 {
      opacity: 0.2;
    }
    .opacity-5 {
      opacity: 0.5;
    }
    .opacity-10 {
      opacity: 1;
    }
  </style>
</head>
<body>
  <img class="opacity-2" src="https://mdbootstrap.com/img/Photos/Horizontal/Nature/4-col/img%20(87).jpg">
  <img class="opacity-5" src="https://mdbootstrap.com/img/Photos/Horizontal/Nature/4-col/img%20(87).jpg">
  <img class="opacity-10" src="https://mdbootstrap.com/img/Photos/Horizontal/Nature/4-col/img%20(87).jpg">
</body>
</html>
```

### 组合选择器

**后代选择器**

以空格作为分隔，如：`.haha p` 代表在`div`元素内有`.haha`这种类的所有元素。
参见如下代码：

```css
<html>
<head>
  <style>
    .haha p {
      background-color: yellow;
    }
  </style>
</head>
<body>
  <div class="haha">
    <p>Paragraph 1 in the div .haha.</p>
    <p>Paragraph 2 in the div .haha>.</p>
    <span>
        <p>Paragraph 3 in the div .haha.</p>
    </span>
  </div>
  <p>Paragraph 4. Not in a div .haha.</p>
  <p>Paragraph 5. Not in a div .haha.</p>
</body>
</html>
```

段落1、2、3都将有黄色的背景，而段落4、5没有。

**子选择器**

也称为直接后代选择器，以`>`作为分隔，如：`.haha > p` 代表在有`.haha`类的元素内的**直接**`<p>`元素。
参见如下代码：

```css
<html>
<head>
  <style>
    .haha > p {
      background-color: yellow;
    }
  </style>
</head>
<body>
  <div class="haha">
    <p>Paragraph 1 in the div .haha.</p>
    <p>Paragraph 2 in the div .haha.</p>
    <span>
        <p>Paragraph 3 in the div .haha - it is descendant but not immediate child.</p>
    </span> <!-- not Child but Descendant -->
  </div>
  <p>Paragraph 4. Not in a div .haha.</p>
  <p>Paragraph 5. Not in a div .haha.</p>
</body>
```

虽然段落3在`.haha`类中，但它的直接父元素是`span`，不是`.haha`的直接后代，所以不能选择。只有段落1、2有黄色背景。

### 伪类和伪元素

伪类（pseudo-class）或伪元素（pseudo-element）用于定义元素的某种特定的状态或位置等。
比如我们可能有这样的需求：

- 鼠标移到某元素上变换背景颜色
- 超链接访问前后访问后样式不同
- 离开必须填写的输入框时出现红色的外框进行警示
- 保证段落的第一行加粗，其它正常
- ...

使用伪类/伪元素的语法如下：

```css
/* 选择器后使用 : 号，再跟上某个伪类/伪元素 */
selector:pseudo-class/pseudo-element {
  property:value;
}
```

**anchor伪类**

```css
a:link {color:#FF0000;}     /* 未访问的链接 */
a:visited {color:#00FF00;}  /* 已访问的链接 */
a:hover {color:#FF00FF;}    /* 鼠标移动到链接上 */
a:active{color:#000FF;}     /*已选中的连接*/
```

> **注意：** 在CSS定义中，a:hover 必须被置于 a:link 和 a:visited 之后，才是有效的。
>
> **注意：** 在 CSS 定义中，a:active 必须被置于 a:hover 之后，才是有效的。
>
> **注意：**伪类的名称不区分大小写。

伪类可以与CSS类配合使用：

```css
a.red:visited {color:#FF0000;}
 
<a class="red" href="css-syntax.html">CSS 语法</a>
```

**CSS : first-child伪类**

可以使用` :first-child` 伪类来**选择父元素的第一个子元素**。

```html
<style>
p:first-child
{
	color:blue;
} 
</style>
</head>

<body>
<p>This is some text.</p>
<p>This is some text.</p>
<p><b>注意:</b>对于 :first-child 工作于 IE8 以及更早版本的浏览器, ！DOCTYPE 必须已经声明.</p>
</body>
```

可以使用`p > i:first-child`匹配所有<p>元素的第一个子元素中的<i>元素：

```css
p > i:first-child{
	color:blue;
} 
</style>
</head>

<body>
<p>I am a <i>strong</i> man. I am a <i>strong</i> man.</p>
<p>I am a <i>strong</i> man. I am a <i>strong</i> man.</p>
<p><b>注意:</b> 当 :first-child 作用于 IE8 以及更早版本的浏览器, ！DOCTYPE 必须已经定义.</p>
</body>
```

**CSS所有伪类/元素**

| [:checked](https://www.runoob.com/cssref/sel-checked.html)   | input:checked         | 选择所有选中的表单元素                          |
| ------------------------------------------------------------ | --------------------- | ----------------------------------------------- |
| [:disabled](https://www.runoob.com/css/cssref/sel-disabled.html) | input:disabled        | 选择所有禁用的表单元素                          |
| [:empty](https://www.runoob.com/cssref/sel-empty.html)       | p:empty               | 选择所有没有子元素的p元素                       |
| [:enabled](https://www.runoob.com/cssref/sel-enable.html)    | input:enabled         | 选择所有启用的表单元素                          |
| [:first-of-type](https://www.runoob.com/cssref/sel-first-of-type.html) | p:first-of-type       | 选择的每个 p 元素是其父元素的第一个 p 元素      |
| [:in-range](https://www.runoob.com/cssref/sel-in-range.html) | input:in-range        | 选择元素指定范围内的值                          |
| [:invalid](https://www.runoob.com/cssref/sel-invalid.html)   | input:invalid         | 选择所有无效的元素                              |
| [:last-child](https://www.runoob.com/cssref/sel-last-child.html) | p:last-child          | 选择所有p元素的最后一个子元素                   |
| [:last-of-type](https://www.runoob.com/cssref/sel-last-of-type.html) | p:last-of-type        | 选择每个p元素是其母元素的最后一个p元素          |
| [:not(selector)](https://www.runoob.com/cssref/sel-not.html) | :not(p)               | 选择所有p以外的元素                             |
| [:nth-child(n)](https://www.runoob.com/cssref/sel-nth-child.html) | p:nth-child(2)        | 选择所有 p 元素的父元素的第二个子元素           |
| [:nth-last-child(n)](https://www.runoob.com/cssref/sel-nth-last-child.html) | p:nth-last-child(2)   | 选择所有p元素倒数的第二个子元素                 |
| [:nth-last-of-type(n)](https://www.runoob.com/cssref/sel-nth-last-of-type.html) | p:nth-last-of-type(2) | 选择所有p元素倒数的第二个为p的子元素            |
| [:nth-of-type(n)](https://www.runoob.com/cssref/sel-nth-of-type.html) | p:nth-of-type(2)      | 选择所有p元素第二个为p的子元素                  |
| [:only-of-type](https://www.runoob.com/cssref/sel-only-of-type.html) | p:only-of-type        | 选择所有仅有一个子元素为p的元素                 |
| [:only-child](https://www.runoob.com/cssref/sel-only-child.html) | p:only-child          | 选择所有仅有一个子元素的p元素                   |
| [:optional](https://www.runoob.com/cssref/sel-optional.html) | input:optional        | 选择没有"required"的元素属性                    |
| [:out-of-range](https://www.runoob.com/cssref/sel-out-of-range.html) | input:out-of-range    | 选择指定范围以外的值的元素属性                  |
| [:read-only](https://www.runoob.com/cssref/sel-read-only.html) | input:read-only       | 选择只读属性的元素属性                          |
| [:read-write](https://www.runoob.com/cssref/sel-read-write.html) | input:read-write      | 选择没有只读属性的元素属性                      |
| [:required](https://www.runoob.com/cssref/sel-required.html) | input:required        | 选择有"required"属性指定的元素属性              |
| [:root](https://www.runoob.com/cssref/sel-root.html)         | root                  | 选择文档的根元素                                |
| [:target](https://www.runoob.com/cssref/sel-target.html)     | #news:target          | 选择当前活动#news元素(点击URL包含锚的名字)      |
| [:valid](https://www.runoob.com/cssref/sel-valid.html)       | input:valid           | 选择所有有效值的属性                            |
| [:link](https://www.runoob.com/cssref/sel-link.html)         | a:link                | 选择所有未访问链接                              |
| [:visited](https://www.runoob.com/cssref/sel-visited.html)   | a:visited             | 选择所有访问过的链接                            |
| [:active](https://www.runoob.com/cssref/sel-active.html)     | a:active              | 选择正在活动链接                                |
| [:hover](https://www.runoob.com/cssref/sel-hover.html)       | a:hover               | 把鼠标放在链接上的状态                          |
| [:focus](https://www.runoob.com/cssref/sel-focus.html)       | input:focus           | 选择元素输入后具有焦点                          |
| [:first-letter](https://www.runoob.com/cssref/sel-firstletter.html) | p:first-letter        | 选择每个<p> 元素的第一个字母                    |
| [:first-line](https://www.runoob.com/cssref/sel-firstline.html) | p:first-line          | 选择每个<p> 元素的第一行                        |
| [:first-child](https://www.runoob.com/cssref/sel-firstchild.html) | p:first-child         | 选择器匹配属于任意元素的第一个子元素的 <p> 元素 |
| [:before](https://www.runoob.com/cssref/sel-before.html)     | p:before              | 在每个<p>元素之前插入内容                       |
| [:after](https://www.runoob.com/cssref/sel-after.html)       | p:after               | 在每个<p>元素之后插入内容                       |
| [:lang(*language*)](https://www.runoob.com/cssref/sel-lang.html) | p:lang(it)            | 为<p>元素的lang属性选择一个开始值               |

以下是常用的伪类/伪元素的简单使用：

```css
a:link {color:#FF0000;}     /* 未访问的链接 */
a:visited {color:#00FF00;}  /* 已访问的链接 */
a:hover {color:#FF00FF;}    /* 鼠标划过链接 */
/* 鼠标移到段落则改变背景颜色 */
p:hover {background-color: rgb(226, 43, 144);}
p:first-line{color:blue;}   /* 段落的第一行显示蓝色 */
p:first-letter{font-size: xx-large;}   /* 段落的第一个字超大 */

h1:before { content:url(smiley.gif); } /* 在每个一级标题前插入该图片 */
h1:after { content:url(smiley.gif); } /* 在每个一级标题后插入该图片 */
```