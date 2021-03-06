| title       | accomplish |
| :---------- | ---------- |
| 03-初始HTML | true       |

### 编辑器相关

前端开发的编辑器软件，首推VS Code，其次推荐Sublime Text。

> 文件的后缀名不能决定文件格式，只能决定打开文件打开的方式。

**HTML 的概述**

### HTML概念

HTML 全称为：Hyper Text Markup Language，译为**超文本标记语言**。

HTML不是一种编程语言，而是一种描述性的**标记语言**。

**作用**：HTML是负责描述文档**语义**的语言。

### **概念**：**超文本**

所谓超文本，有两层含义：

（1）图片、音频、视频、动画、多媒体等内容，称为超文本，因为它们超出了文本的限制。

（2）不仅如此，它还可以从一个文件跳转到另一个文件，与世界各地主机的内容进行连接。即：超级连接文本。

### **概念：标记语言**

HTML不是一种编程语言，是一种描述性的**标记语言**。这主要有两层含义：

（1）**标记语言是一套标记标签**。比如：标签`<a>`表示超链接、标签`<img>`表示图片等等，它们都是属于HTML标签。

通俗来说，网页是由网页元素组成的，这些元素由HTML标签描述出来，然后通过浏览器解析，这就可以显示给用户看了。

（2）编程语言是有编译过程的，而标记语言没有编译过程，HTML标签是直接由浏览器解析执行。

### **HTML是负责描述文档语义的语言**

HTML格式的文件是一个纯文本文件（就是用txt文件改名而成），用一些标签来描述语义，这些标签在浏览器页面上是无法直观看到的，所以被称作“超文本标记语言”。

接下来，我们学习HTML中的很多“标签对”。

### **HTML的历史**

![image](https://camo.githubusercontent.com/fb2272c9642c733ce56eb5097fa526ba6e3439de5f8f10d8bfbf1d20ddb2cb79/687474703a2f2f696d672e736d79687661652e636f6d2f32303135313030315f313030312e706e67)

其中，我们专门来对XHTML做一个介绍。

**XHTML介绍：** XHTML：Extensible Hypertext Markup Language，可扩展超文本标注语言。 XHTML的主要目的是为了**取代HTML**，也可以理解为HTML的升级版。 HTML的标记书写很不规范，会造成其它的设备(ipad、手机、电视等)无法正常显示。 XHTML与HTML4.0的标记基本上一样。 XHTML是**严格的、纯净的**HTML。

### HTML 的专有名词

- 网页：由各种标记组成的一个页面就叫网页。
- 主页（首页）：一个网站的起始页面或导航页面
- 标记：比如`<p>`称为开始标记（标签），`</p>`称为结束标记（标签）。每个标签都规定好了特殊的含义。
- 元素：比如`<p>内容</p>`称为元素。
- 属性：给每个标签做的辅助信息。
- XHTML：符合XML语法标准的HTML。
- DHML：dynamic，动态的，`javascript + css + html`合起来的页面就是一个DHML。
- HTTP：超文本传输协议。用来规定客户端浏览器和服务器交互时数据的一个格式。
- SMTP：邮件传输协议。
- FTP：文件传输协议。

### 书写第一个HTML页面

打开VS Code，新建一个文件，名为`test.html`（注意，后缀名未`html`），保存到本地。

紧接着，在文件里，输入`html:5`，然后按下键盘下的<kbd>Tab</kbd>键，就自动生成了如下内容：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

上面的内容就是 `html` 页面的骨架。我们在此基础上，新增几个标签，完整代码为：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h3>我是三级标签</h3>
    <img src="" alt="" >
    <a href="https://baidu.com">我是超链接，点我一下</a>
</body>
</html>
```

标签写完后，我们用浏览器打开上面这个`test.html`文件，看看页面效果：到此，第一个HTML页面就写完了。

### HTML结构详解

HTML通常是成对出现的（**双边标记**），比如`<div>`和`</div>`；也有例外的单标签（**单边标记**），如：`<br/>`、`<hr/>`、`<img src="images/1.jpg"/>`等。

属性与标记之间、各属性之间需要以空格隔开。属性值以双引号括起来。

**html骨架标签分类**

|      标签名       |    定义    | 说明                                                    |
| :---------------: | :--------: | :------------------------------------------------------ |
|  `<html></html>`  |  HTML标签  | 页面最大的标签，称为根标签                              |
|  `<head></head>`  | 文档的头部 | 在head标签里必须要有title标签，就像作文一定要有题目一样 |
| `<title></title>` | 文档的标题 | 让页面拥有一个属于自己的标题                            |
|  `<body></body>`  | 文档的主体 | 元素包含文档的所有内容，页面内容基本都放body里面的      |

#### 1. 文档声明头

任何一个标准的HTML页面，第一行一定是以一个`<!DOCTYPE ......>`开头的语句。这一行，就是文档声明头，即DocType Declaration，简称DTD。

**DTD可告知浏览器文档使用哪种HTML或XHTML规范**。

 **HTML4.01有哪些规范呢？**

**HTML4.01**这个版本是IE6开始兼容的。**HTML5是IE9开始兼容的**。如今，手机、移动端的网页，就可以使用HTML5了，因为其兼容性更高。

说个题外话，html1 至 html3 是美国军方以及高等研究所用的，并未对外公开。

HTML4.01里面有两大种规范，每大种规范里面又各有3种小规范。所以一共6种规范（见下图）。

HTML4.01里面规定了**普通**和**XHTML**两大种规范。HTML觉得自己有一些规定不严谨，比如，标签是否可以用大写字母呢？`<H1></H1>`所以，HTML就觉得，把一些规范严格的标准，又制定了一个XHTML1.0。在XHTML中的字母X，表示“严格的”。

总结一下，HTML4.01一共有6种DTD。说白了，HTML的第一行语句一共有6种情况：

![image](https://camo.githubusercontent.com/04503e60c2614776fe5708701b7db40614f03efcf4fa4bb7ea961c7c2768cb50/687474703a2f2f696d672e736d79687661652e636f6d2f32303137303632395f313630302e706e67)

下面对上图中的三种小规范进行解释：

**strict**：

表示“严格的”，这种模式里面的要求更为严格。这种严格体现在哪里？有一些标签不能使用。 比如，u标签，就是给一个本文加下划线，但是这和HTML的本质有冲突，因为HTML最好是只负责语义，不要负责样式，而u这个下划线是样式。所以，在strict中是不能使用u标签的。

那怎么给文本增加下划线呢？今后将使用css属性来解决。

XHTML1.0更为严格，因为这个体系本身规定比如标签必须是小写字母、必须严格闭合标签、必须使用引号引起属性等等。

**Transitional**：表示“普通的”，这种模式就是没有一些别的规范。

**Frameset**：表示“框架”，在框架的页面使用。

在sublime输入的html:xt，x表示XHTML，t表示transitional。

在HTML5中极大的简化了DTD，也就是说HTML5中就没有XHTML了。HTML5的DTD（文档声明头）如下：

```html
<!DOCTYPE html>
```

#### 2. 页面语言`lang`

```html
<html lang="en">
```

这行标签用于指定页面的语言类型.

- en：定义页面语言为英语。
- zh-CN：定义页面语言为中文。

#### 3.头标签`head`

**html5 的比较完整的骨架：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">
	<meta name="Author" content="">
    <meta name="Keywords" content="厉害很厉害" />
    <meta name="Description" content="网易是中国领先的互联网技术公司，为用户提供免费邮箱、游戏、搜索引擎服务，开设新闻、娱乐、体育等30多个内容频道，及博客、视频、论坛等互动交流，网聚人的力量。" />
    <title>Document</title>
</head>
<body>

</body>
</html>
```

面试题：

- 问：网页的head标签里面，表示的是页面的配置，有什么配置？
- 答：字符集、关键词、页面描述、页面适配、IE适配、视口、iPhone小图标等等。

头标签内部的常见标签有：

- `<title>`：指定整个网页的标题，在浏览器最上方显示。
- `<mata>`：提供网页有关的基本信息。
- `<link>`：定义文档与外部资源的关系。
- `<base>`：为页面上的所有链接规定默认地址或默认目标。

**`<title>`标签**：

用于设置网页标题：

```html
<title>网页的标题</title>
```

**`<meta>`标签**：

meta表示“元”，就是基本的配置项目。

常见的几种meta标签如下：

（1）字符集`charset`：

```html
<meta charset="UFT-8">
```

charset就是character set（"字符集"），即**网页的编码方式**。

字符集是多个字符的集合。计算机要准确的处理各种字符集文字，需要进行字符编码，以便计算机能够识别和存储各种文字。

上面这行代码非常关键， 是必须要写的代码，否则可能导致乱码。比如你保存的时候，meta写的和声明的不匹配，那么浏览器就是乱码。

utf-8是目前最常用的字符集编码方式，常用的字符集编码方式还有gbk和gb2312等。关于“编码方式”，我们在下一段会详细介绍。

（2）视口`viewport`：

```html
<meta name="viewport" content="width=device-width,initial-scal=1.0">
```

`width=device-width`：表示视口宽度等于屏幕宽度。以后学Web移动端的时候会学到。

(3)定义“关键词”：

举例如下：

```html
<meta name="Keywords" content="网易，邮箱，游戏，新闻，体育，娱乐，女性，亚运，论坛，短信" />
```

这些关键词，就是告诉搜索引擎，这个网页是大概干嘛的，能够提高搜索命中率，能让别人找到你，搜索到你。

(4)定义“页面描述”：

举例如下：

```html
<meta name="Description" content="网易是中国领先的互联网技术公司，为用户提供免费邮箱、游戏、搜索引擎服务，开设新闻、娱乐、体育等30多个内容频道，及博客、视频、论坛等互动交流，网聚人的力量。" />
```

只要设置Description页面描述，那么百度搜索结果，就能够显示这些语句，这个技术叫做**SEO**（search engine optimization，搜索引擎优化）。

效果如下：

![image](https://camo.githubusercontent.com/a8b14cfc016129307cbd84605ec2e5a5e1865bc1a064aa739d92cef5c2f07f8c/687474703a2f2f696d672e736d79687661652e636f6d2f32303137303632395f313734332e706e67)

上面的几种`<meta>`都不用记忆，但是另外一个`<meta>`标签是需要记的：

```html
<meta http-equiv="refresh" content="3;http://www.baidu.com">
```

上面这个标签的意思是说，3秒之后，自动跳转到百度页面。

**`<base>`标签**

```html
<base href="/">
```

base标签用于指定基础的路径。指定之后，所有的a链接都是以这个路径为基准。

#### 4.`<body>`标签

`<body>`标签的属性有：

- `<bgcolor>`：设置整个网页的背景颜色。
- `<background>`：设置整个网页的背景图片。
- `<text>`：设置网页中的文本颜色
- `<leftmargin>`：网页的左边距。IE默认是8个像素。
- `<topmargin>`：网页的上边距。
- `<rightmargin>`：网页的右边距。
- `<bottommargin>`：网页的下边距。
- `<link>`：超链接未点击前的默认颜色。
- `<alink>`：鼠标点击但未松开时的颜色。
- `<vlink>`：点击完成之后显示的颜色。

### 计算机编码

计算机，不能直接存储文字，存储的是编码。

众所周知，计算机只能处理二进制数据、其他数据，比如0-9、a-z、A-Z，这些字符，我们可以定义一套规则来表示。假如：A用110表示，B用111表示等。

**ASCII码：** 美国发布的，用1个字节(8位二进制)来表示一个字符，共可以表示2^8=256个字符。 美国的国家语言是英语，只要能表示0-9、a-z、A-Z、特殊符号。

**ANSI编码：** **每个国家为了显示本国的语言，都对ASCII码进行了扩展**。用2个字节(16位二进制)来表示一个汉字，共可以表示2^16＝65536个汉字。例如： 中国的ANSI编码是GB2312编码(简体)，对6763汉字进行编码，含600多特殊字符。另外还有GBK(简体)。 日本的ANSI编码是JIS编码。 台湾的ANSI编码是BIG5编码（繁体）。

**GBK：** 对GB2312进行了扩展，用来显示罕见的、古汉语的汉字。现在已经收录了2.1万左右。并提供了1890个汉字码位。K的含义就是“扩展”。

**Unicode编码(统一编码)：** 用4个字节(32位二进制)来表示一个字符，想法不错，但效率太低。例如，字母A用ASCII表示的话一个字节就够，可用Unicode编码的话，得用4个字节表示，造成了空间的极大浪费。A的Unicode编码是0000 0000 0000 0000 0000 0000 0100 0000

**UTF-8(Unicode Transform Format)编码：** 根据字符的不同，选择其编码的长度。比如：一个字符A用1个字节表示，一个汉字用2个字节表示。

毫无疑问，开发中，都用**UTF-8**编码吧，准没错。

**中文能够使用的字符集两种：**

- 第一种：UTF-8。UTF-8是国际通用字库，里面涵盖了所有地球上所有人类的语言文字，比如阿拉伯文、汉语、鸟语……
- 第二种：GBK（对GB2312进行了扩展）。gb2312 是国标，是中国的字库，里面**仅**涵盖了汉字和一些常用外文，比如日文片假名，和常见的符号。

字库规模： UTF-8（字很全） > gb2312（只有汉字）

**重点1：避免乱码**

我们用meta标签声明的当前这个html文档的字库，一定要和保存的文件编码类型一样，否则乱码（重点）。

拿 sublime编辑器举例，当我们不设置的时候，sublime默认类型就是UTF-8。而一旦更改为gb2312的时候，就一定要记得设置一下sublime的保存类型： `文件→ set File Encoding to → Chinese Simplified(GBK)`。VS Code 的道理一样。

**重点2：UTF-8和gb2312的比较**

保存大小：UTF-8（更臃肿、加载更慢） > gb2312 （更小巧，加载更快）

总结：

- UTF-8：字多，有各种国家的语言，但是保存尺寸大，文件臃肿；
- gb2312：字少，只用中文和少数外语和符号，但是尺寸小，文件小巧。

列出2个使用情形：

1） 你们公司是做日本动漫的，经常出现一些日语动漫的名字，网页要使用UTF-8。如果用gb2312将无法显示日语。 2） 你们公司就是中文网页，极度的追求网页的显示速度，要使用gb2312。如果使用UTF-8将每个汉字多一个byte，所以5000个汉字，多5kb。

我们亲测：

- qq网、网易、搜狐都是使用gb2312。这些公司，都追求显示速度。
- 新华网藏语频道，使用的是UTF-8，保证字符集的数量。

我们是怎么查看网页的编码方式的呢？在浏览器中打开网页，右键，选择“查看网页源代码”，找到meta标签中的charset属性即可。

那么，我们为什么可以查看网页的源代码呢？因为这个打开的html网页已经存到我的临时文件夹里了，临时文件夹里的html是纯文本文件，纯文本文件自然可以查看网页的源代码。

### HTML规范

- HTML不区分大小写，但HTML的标签名、类名、标签属性、大部分属性值建议统一用小写。
- HTML页面的后缀名是html或者htm(有一些系统不支持后缀名长度超过3个字符，比如dos系统)

#### 1.编写XHTML的规范：

（1）所有标记元素都要正确的嵌套，不能交叉嵌套。正确写法举例：`<h1><font></font></h1>`

（2）所有的标记都必须小写。

（3）所有的标签都必须闭合。

- 双标签：`<span></span>`
- 单标签：`<br>` 建议写成 `<br />` `<hr>` 建议转成 `<hr />`，还有`<img src=“URL” />`

（4）所有的属性值必须加引号。`<font color="red"></font>`

（5）所有的属性必须有值。`<hr noshade="noshade">`、`<input type="radio" checked="checked" />`

（6）XHTML文档开头必须要有DTD文档类型定义。

#### 2.HTML的基本语法特性

**（1）HTML对换行不敏感，对tab不敏感**

HTML只在乎标签的嵌套结构，嵌套的关系。谁嵌套了谁，谁被谁嵌套了，和换行、tab无关。换不换行、tab不tab，都不影响页面的结构。

也就是说，HTML不是依靠缩进来表示嵌套的，而是看标签的嵌套关系。但是，我们发现有良好的缩进，代码更易读。建议大家都正确缩进标签。

百度为了追求极致的显示速度，所有HTML标签都没有换行、都没有缩进（tab），HTML和换不换行无关，标签的层次依然清晰，只不过程序员不可读了。

![image](https://camo.githubusercontent.com/aec09c94a1966c7462cb24e882164bd4fc466505c339fe9303b3d501ccecedc4/687474703a2f2f696d672e736d79687661652e636f6d2f32303137303632395f323232362e706e67)

> 程序员骂骂咧咧地走开了。。。

**（2）空白折叠现象**

HTML中所有的**文字之间**，如果有空格、换行、tab都将折叠未一个空格显示。

![image](https://camo.githubusercontent.com/bdcd1ee9cc316a2bd791a762d5320eedbfe520c768cf3657aef221377821ecc6/687474703a2f2f696d672e736d79687661652e636f6d2f32303137303632395f323233302e6a7067)

**(3)标签要严格封闭**

标签不封闭的结果是灾难性的。

标签不封闭的举例如下：

![image](https://camo.githubusercontent.com/357b6a0261002182c06b7b74733495cb36b1cd7f4f611cc36c725a092b0d5b14/687474703a2f2f696d672e736d79687661652e636f6d2f32303137303632395f323234352e6a7067)