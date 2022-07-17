|         title         | accomplish |
| :-------------------- | :--------- |
| 06-HTML标签：图片标签 | true      |

**img标签介绍**

### 介绍

img:英文全称&nbsp;image(图像),代表一张图片。<br/>如果想要网页中显示图片，就可使用img标签，它是一个单标签。

```html
<img src="图片的URL" />
```

### 能插入的图片类型

- 能够插入的图片类型是：jpg(jpeg)、gif、png、bmp等。
- 不能往网页中插入的图片格式是：psd、ai等。

HTML页面不是直接插入图片，而是插入图片的引用地址，所以要先把图片上传到服务器上。

**img标签的`src`属性**

`src`：英文名称为`source`，来源、出处，指图片的路径。<br/>分为相对路径、绝对路径

### 相对路径

相对于当前页面所在的路径。两个标记`.`和`..`分别代表当前目录和上一层目录。

举例1：

```html
<!-- 当前目录的图片 -->
<img src="2.jpg">
<img src="./2.jpg">

<!-- 上一级目录中图片 -->
<img src="../2.jpg">     
```

相对路径不会出现这种情况：

```
aaa/../bbb/1.jpg
```

`../`要么不写，要么就写在开头。

举例2：

```
<img src="images/1.jpg">
```

上方代码的意思是说，当前html页面有一个并列的文件夹`images`，在文件夹`images`中存放了一张图片`1.jpg` 。

相对路径的面试题。现有如下文件层级图：

![image](https://camo.githubusercontent.com/8300b52bf8c01aeb05457192ac027f775ad1faa3929c755342a906196027e6eb/687474703a2f2f696d672e736d79687661652e636f6d2f32303137303633305f313133332e706e67)

问题：如果想在index.html中插入1.png，那么对应的img语句是？

分析：

> 现在document是最大的文件夹，里面有两个文件夹work和photo。work中又有一个文件夹叫做myweb。myweb文件夹里面有index.html。
>
>  所以index.html在myweb文件夹里面，上一级就是work文件夹，上两级就是document文件夹。通过document文件夹当做一个中转站，进入photo文件夹，看到了1.png。

答案：

```html
<img src="../../photo/1.png" />
```

### 绝对路径

以下两种：

（1）以盘符开始的绝对路径。举例：

```html
<img src="C:\Users\qianguyihao\Desktop\html\images\1.jpg">
```

（2）网络路径。举例：

```html
<img src="https://gitee.com/lconfindent/image/raw/master/Introduction_to_Software_Engineering.jpg">
```

### 相对路径和绝对路径的总结

相对路径的好处：站点不管拷贝到哪里，文件和图片的相对路径关系都是不变的。相对路径使用有一个前提，就是网页文件和你的图片，必须在一个服务器上。

**总结一下**：

无论是在 a 标签还是 img 标签上，如果要用路径。只有两种路径能用，就是相对路径和绝对路径：

- 相对路径从自己出发，找到别人。
- 绝对路径，就是`http://`或者`https://`开头的路径。

**img标签的其他属性**

### width、height 属性

- `width`：图像的宽度。
- `height`：图像的高度。

width和height，在 HTML5 中的单位是 CSS 像素。可以只指定 width 和 height 中的一个值，浏览器会根据原始图像进行缩放。

**重要提示**：如果要想保证图片等比例缩放，请只设置width和height中其中一个。

### alt 属性

- `alt`：当图片不可用（无法显示）的时候，代替图片显示的内容。alt是英语 alternate “替代”的意思，代表替换资源。

### title 属性

- `title`：**提示性文本**。鼠标悬停时出现的文本。

title 属性不该被用作一幅图片在 alt 之外的补充说明信息。如果一幅图片需要小标题，使用 figure 或 figcaption 元素。

title 元素的值一般作为提示条(tooltip)呈现给用户，在光标于图片上停下后显示出来。尽管这确实能给用户提供更多的信息，您不该假定用户真的能看到：用户可能只有键盘或触摸屏。如果要把特别重要的信息提供给用户，可以选择上面提供的一种方法将其内联显示，而不是使用 title。

### ~~align 属性~~

- 图片的`align`属性：**图片和周围文字的相对位置**。属性取值可以是：bottom（默认）、center、top、left、right。

如果想实现图文混排的效果，请使用align属性，取值为left或right。

1、`align=""`，图片和文字底端对齐。即默认情况下。

2、`align="center"`：图片和文字水平方向上居中对齐。

3、`align="top"`：图片与文字顶端对齐。

4、`align="left"`：图片在文字的左边。

5、`align="right"`：图片在文字的右边。

### ~~其他已废弃的属性~~

- `Align`（已废弃）：指图片的水平对齐方式，属性值可以是：top、middle、bottom、left、center、right。该属性已废弃，替换为 `vertical-align`这个CSS属性。
- `border`（已废弃）：给图片加边框，单位是像素，边框的颜色默认黑色。该属性已废弃，替换为 `border`这个CSS属性。
- `Hspace`（已废弃）：指图片左右的边距。
- `Vspace`（已废弃）：指图片上下的边距。
