| title                 | accomplish |
| :-------------------- | ---------- |
| 04-HTML排版：排版标签 | true       |

### 本文主要内容

排版标签：

- `<h1>`
- `<p>`
- `<hr/>`
- `<br/>`
- `<div>`
- `<span>`
- `<center>`
- `<pre>`

### 标签分类

和军队的军衔一样，HTML标签也分等级，HTML将所有的标签分为两种：

- **文本级标签**：p、span、a、b、i、u、em。文本级标签只能放**文字、图片、表单元素**。（a标签里不能放a和input）
- **容器级标签**：div、h系列、li、dt、dd。容器里可放置任何东西。

### 标题标签`<h1>`

标题使用`<h1>`至`<h6>`标签定义。`<h1>`定义最大的标题，`<h6>`定义最小的标题。具有align属性，属性值可以是：left、center、right。

### HTML注释
格式：

```html
<!-- 注释 -->
```

### 段落标签`<p>`

段落，"paragraph"缩写

作用：可以把HTML文档分割为若干段落。

```html
<p align="center">
    This is a paragraph
</p>
```

属性：

- `align="属性值"`：对齐方式。包括left、center、right。

从学习p的第一天开始，就要牢记：**p标签时一个文本级标签，p里面只能放文字、图片、表单元素**。其他的一律不能放。

错误写法：（尝试把h放在p里）

### 水平线标签`<hr/>`

> horizontal&nbsp;单词发音:[ˌhɒrɪˈzɒnt(ə)l]

水平分割线(horizontal rule)可以在视觉上将文档分隔成各个部分。**单标签**

属性介绍：

- `align="属性值"`：设定线条放置位置。属性值可选择：left&nbsp;right&nbsp;center。
- `size="2"`：设置线条粗细，以像素为单位，内定为2。
- `width="500"`或`width=70%`：设定线条长度。可以是绝对值（单位是像素）或相对值。如果设置为相对值的话，内定为100%。
- `color="#0000FF"`：设置线条颜色。
- `noshade`：不要阴影，即设定线条为平面显示。若没有这个属性则表明线条具有阴影或立体。

### 换行标签`<br />`

希望某段文本强制换行显示，就需要使用换行标签。

```html
This<br/>is para<br/>graph width line breaks
```

效果如下：<br/>This<br/>is para<br/>graph width line breaks

### `<div>`和`<span>`标签

div，division“分割”；span，“范围、跨度”。相比听说过“div + css”布局吧。

**div和span的介绍**

- div标签：可以把标签中的内容分割为独立的区块，必须单独占据一行。
- span标签：和div作用一样，但不换行。

> div标签的属性：`align="属性值"`：设置块的位置：left、right、center。

**div和span的区别**

`<div>`和`<span>`唯一的区别在于：`<span>`是不换行的， 而`<div>`是换行的。

单独在网页中插入这两个元素，没什么影响。这两个元素是专门为定义CSS样式定义的。

div在浏览器中，默认不会增加任何的效果，但是语义变了，div中所有的元素是一个小区域。div标签是一个**容器级标签**，里面什么都能放，甚至放div自己。

span也是表达“小区域”的标签，但终究也只是一个**文本级标签**。就是说，span里只能放文字、图片、表单元素。span里面不能放p、h、ul、dl、ol、div。

span举例：

```html
<p>
    产品简介
    <span>
    	<a href="">详细信息</a>
        <a href="">购买</a>
    </span>
</p>
```

div举例：

```html
<div class="header">
    <div class="logo"></div>
</div>
<div class="footer"></div>
```

我们称这种模式叫做“**div+css**”：**div标签负责布局、结构、分块，css负责样式**。

### ~~内容居中标签`<center>`~~

此时center代表是一个标签，而不是一个属性值了。只要在这个标签里面的内容，都会居于浏览器的中间。但一般不用，建议使用CSS布局来实现。

### ~~预定义（预格式化）标签`<pre>`~~

含义：将保留标签内的所有空白字符（空格、换行符），原封不动地输出结果。

但真正排版的时候，几乎用不着。
