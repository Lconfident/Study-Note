## 什么是HTML

HTML是用来描述网页的一种语言

* HTML指超文本标记语言：**H**yper **T**ext **M**arkup **L**anguage
* HTML不是一种编程语言，而是一种**标记**语言
* 标记语言是一套**标记字符**（markup tag）
* HTML使用标记标签来**描述**网页
* HTML文档包含了HTML**标签**及**文本**内容
* HTML文档也叫做**Web页面**

## HTML标签

HTML tag

* HTML标签通常是由尖括号`< >`包围的关键词，比如`<html>`
* HTML标签通常是成对出现的，比如`<b>`和`</b>`
* 标签对中的第一个是<u>开始标签</u>，第二个是<u>结束标签</u>
* 有的标签只有一个，比如`<br>`

HTML元素

“HTML元素”和“HTML标签”通常都是描述同样的意思，但是严格来讲，一个HTML元素包含了开始标签和结束标签。

## 标签介绍

### div

**div标签使用说明**

* 布局最多的为div
* 通常将网页重构说成`div css`制作
* div本身没有什么特别，只是div替代以前的table布局
* 可对div标签对象设置成不同样式来实现我们的需求
* **通常一对未设置任何样式的div，独占一行**

**div作用**

div起分隔作用，是分割内容常使用的标签

**div演示代码**

```html
<!DOCTYPE html>
<html >
<head>
    <title>Document</title>
</head>
<body>
    <div>第一个div</div>
    <div>第二个div</div>
    <div>第三个div</div>
</body>
</html>
```

> 效果如下：
>
> ![div](http://www.manongjc.com/images/jiaochen/html_div.png)
>
> 说明：以上使用了div来分隔开“第一个div”、“第二个div”和“第三个div”文字

### span

**span语法**

`<span> 内容 </span>`

**span使用**

* 可设置样式
* **特性：通常一对未设置任何样式的span，高宽是自适应内容**

**span演示代码**

```html
<!DOCTYPE html>
<html >
<head>
    <title>Document</title>
</head>
<body>
    <span>我是码农教程！</span>
    <span>码农教程网址www.manongjc.com </span>
</body>
</html>
```

> 效果如下：
>
> ![span](http://www.manongjc.com/images/jiaochen/html_span.png)

### a

**a语法**

`<a href = "https://github.com/Lconfident" target = "目标" title = "说明"> 被链接内容</a>`

常用属性：

* href：网址

* target：打开目标方式

* > 默认为在浏览网页中重新载入对应链接网页
  >
  > `_blank` ：新建标签窗口页
  >
  > `_parent` ：重新刷新本窗口页

**a作用**

利用a锚实现网页跳转

**a应用实例**

1. 图片超链接
   `<a href = "http://www.manongjc.com/" target = "_blank" title = "转到码农教程主页" ><img src = "http://manongjc.com/Public/images/logo.gif"/></a>`

   <a href = "http://www.manongjc.com/" target = "_blank" title = "转到码农教程主页" ><img src = "http://manongjc.com/Public/images/logo.gif"/></a>

2. 锚文本超链接
   `<a href = "https://github.com/Lconfident" title = "我的Github主页"> Github Web</a>`

   <a href = "https://github.com/Lconfident" title = "我的Github主页"> Github Web</a>

**a应用扩展**

同页面跳转至指定位置

> 我们常常会点击`回到顶部`链接，就会跳转到网页顶部

1. 在body内最上面添加一个`<span id = "top" name = "top"></span>`
2. 在需要跳转至顶部的地方，添加`<a href = "#top">回到顶部</a>`
3. 完成顶部跳转实现

> 注意：
>
> * 以`#`开头，`英文字母`命名
> * `id`、`name`和`a`命名相同

### br

`<br />`

强制换行

### p

**p语法**

```html
<p>第一大段</p>
<p>第二大段</p>
```

实现文章换段落

> 通常同等初始化下网页里，要实现上下文字间隔相同，**2个br换行**标签相当于使用**p**段落标签
>
> 我们需要**文字小换行**时候我们使用**br**换行标签，如果要**实现段落**可以使用**p**标签，这样HTML结构清晰有利于搜索引擎与用户阅读文章，适当的段落与换行布局应该从用户阅读习惯。

### h

**标题标签**

`<h1>最重要的标题</h1>`

### px em pt

**一般用px**

* `px`：像素（`Pixel`）；相对长度单位
* `em`：相对长度单位；相对于当前对象内文本的字体尺寸
* `pt`：点（`Point`）；绝对长度单位

**px与em单位换算**

任意浏览器的默认字体高度16px（16像素）。所有未经调整的浏览器都符合:

1em=16px。

12px=0.75em

10px=0.625em

> 为了简化font-size的换算，需要在css中的body选择器中声明font-size=62.5%，这就使em值变为 16px*62.5%=10px, 这样12px=1.2em, 10px=1em, 也就是说只需要将你的原来的px数值除以10，然后换上em作为单位就行了
>
> 具体使用时候：
>
> 我们在对全体html标签声明初始一次font-size=62.5%
> 如：
> `*{font-size=62.5%}`
>
> 即可此后面布局可依据以下技巧进行设置em单位
>
> `font-size:1.2em`等于`font-size:12px`
>
> `font-size:1.4em`等于`font-size:14px`
>
> 以此类推相当于初始`font-size=62.5%`后，em与px单位就只有10倍差距，以便方便计算与设置em长度数值使用。

### B

**加粗**

`<b>B</b>`

<b>B</b>

### strong

Html strong加粗标签与html B加粗标签显示效果相同

`<strong> Strong </strong>` 

### em

**强调**

`<em>em</em>`

<em>em</em>

### i

Html i斜体标签与html em强调标签效果相同

`<i>斜体</i>`

<i>斜体</i>

### u

`<u>下划线</u>`

<u>下划线</u>

### s

`<s>删除线</s>`

<s>删除线</s>

### img

`<img src = "路径" width = "175" height = "45" alt = ""/>`

* `src` ：路径
* `width` ：宽度
* `height`：高度
* `alt`：图片备注

`<img src = "https://github.com/Lconfident/Pictures/blob/main/f525a3b4f0d47c28b673a6061716a39.jpg" alt = "个人图片"/>`

<img src = "https://github.com/Lconfident/Pictures/blob/main/f525a3b4f0d47c28b673a6061716a39.jpg" alt = "个人图片"/>

### sup&sub

上标：`<sup>上浮内容</sup>`

<sup>上浮内容</sup>

下标：`<sub>下沉内容</sub>`

<sub>下沉内容</sub>

### nobr

禁止换行内容标签

不换行内容放入`<nobr></nobr>`之间即可

### hr

水平分割线

`<hr/>`

<hr/>

### form

```html
<!DOCTYPE html>
<html>
<head>
<title>html form表单实例</title>
</head>
<body>
<form action="" method="get"> 
<input name="" type="text" size="22" /> 
<input name="" type="submit" value="提交" /> 
</form> 
</body>
</html>
```



> 常常我们使用在一个网页中数据提交标签
>
> 比如我们留言板、评论等可以填写数据，提交处理地方都需要表单标签
>
> 而form表单标签内放输入框input、单选、多选、select下拉列表、提交按钮等标签内容。

form表单区域标签语法

* `<form action = "" method = "get"> </form>`

  > 值为get时，是通过URL传递参数,这个时候我们通过网址URL能看见自己填写的内容

* `<form action = "" method = "post"> </form>`

  > 值为post时，是通过类似缓存传递参数，URL是不能看到form表单填写的内容

### label

一般要实现点击单选按钮框文字或多选按钮框文字对应选择按钮被选择，使用label标签即可

点击`<label>`标签文字时，实现对应控件被选择

需要对应表单控件`id`的值与`label`标签内的`for`值相同

```html
<form action="" method="get">
性别：<br/>
<input name="sex" id="man" type="radio" value=""/>
<label for="man">男</label>
<input name="sex" id="woman" type="radio" value=""/>
<label for="woman">女</label> 
</form> 
```

