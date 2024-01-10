# HTML/CSS/JavaScript学习笔记

## 第一部分  HTML

### HTML教程

#### 1.  HTML 简介

- **\<!DOCTYPE html>** 声明为 HTML5 文档
- **\<html>** 元素是 HTML 页面的根元素
- **\<head>** 元素包含了文档的元（meta）数据，如 **\<meta charset="utf-8">** 定义网页编码格式为 **utf-8**。
- **\<title>** 元素描述了文档的标题
- **\<body>** 元素包含了可见的页面内容
- **\<h1>** 元素定义一个大标题
- **\<p>** 元素定义一个段落

#### 2.  HTML 基础

##### 标题

```html
<h1>这是一个标题</h1>
<h2>这是一个标题</h2>
<h3>这是一个标题</h3>
```

##### 段落

```html
<p>这是一个段落。</p>
<p>这是另外一个段落。</p>
```

##### 链接

```html
<a href="https://www.runoob.com">这是一个链接</a>
```

##### 图像

```html
<img src="/images/logo.png" width="258" height="39" />
```

#### 3.  HTML 元素

##### 语法

- HTML 元素以**开始标签**起始
- HTML 元素以**结束标签**终止
- **元素的内容**是开始标签与结束标签之间的内容
- 某些 HTML 元素具有**空内容（empty content）**
- 空元素**在开始标签中进行关闭**（以开始标签的结束而结束）
- 大多数 HTML 元素可拥有**属性**

##### 空元素

​	没有内容的HTML元素被称为空元素。空元素在开始标签中关闭。在开始标签中添加斜杠，比如\<br />，是关闭空元素的正确方法。

#### 4.  HTML 属性

##### 语法

- HTML 元素可以设置**属性**
- 属性可以在元素中添加**附加信息**
- 属性一般描述于**开始标签**
- 属性总是以名称/值对的形式出现，**比如：name="value"**。

##### [HTML属性参考手册](https://www.runoob.com/tags/html-reference.html)

#### 5.  HTML 标题

​	标题（Heading）是通过 \<h1> - \<h6> 标签进行定义的。\<h1> 定义最大的标题。 \<h6> 定义最小的标题。

##### 水平线

​	\<hr>标签在HTML页面中创建水平线。

##### 注释

```html
<!-- 这是一个注释 -->
```

#### 6.  HTML 段落

##### 语法

```html
<p>这是一个段落 </p>
<p>这是另一个段落</p>
```

##### 折行

```html
<p>这个<br>段落<br>演示了分行的效果</p>
```

##### 输出

​	对于 HTML，无法通过在 HTML 代码中添加额外的空格或换行来改变输出的效果。当显示页面时，浏览器会**移除**源代码中多余的空格和空行。所有连续的空格或空行都会被算作一个空格。需要注意的是，HTML 代码中的所有连续的空行（换行）也被显示为**一个空格**。

#### 7.  HTML 文本格式化

​	HTML 使用标签\<b>("bold") 与\<i>("italic") 对输出的文本进行格式。

通常使用**\<strong>**替换**\<b>**，使用**\<em>**替换**\<i>**。

[完整标签参考手册](https://www.runoob.com/html/html-formatting.html)

#### 8.  HTML 链接

##### 语法

```html
<a href="url">链接文本</a>
```

- `href`：指定链接目标的URL，这是链接的最重要属性。可以是另一个网页的URL、文件的URL或其他资源的URL。
- `target`（可选）：指定链接如何在浏览器中打开。常见的值包括 `_blank`（在新标签或窗口中打开链接）和 `_self`（在当前标签或窗口中打开链接）。
- `title`（可选）：提供链接的额外信息，通常在鼠标悬停在链接上时显示为工具提示。
- `rel`（可选）：指定与链接目标的关系，如 nofollow、noopener 等。

##### 链接属性

###### target属性

```html
<a href="https://www.runoob.com/" target="_blank" rel="noopener noreferrer">访问菜鸟教程!</a>
```

###### id属性

```html
<!-- 链接的id是tips -->
<a id="tips">有用的提示部分</a>
<!-- 链接到id为tips的目标 -->
<a href="#tips">访问有用的提示部分</a>
```

##### 链接模式

###### 文本链接

```html
<a href="https://www.example.com">访问示例网站</a>
```

###### 图片链接

```html
<a href="https://www.example.com">
  <img src="example.jpg" alt="示例图片">
</a>
```

###### 锚点链接

```html
<a href="#section2">跳转到第二部分</a>
<!-- 在页面中的某个位置 -->
<a name="section2"></a>
```

###### 下载链接

```html
<a href="document.pdf" download>下载文档</a>
```

#### 9.  HTML 头部

##### \<head> 元素

- \<head> 元素包含了所有的头部标签元素。在 \<head>元素中你可以插入脚本（scripts）, 样式文件（CSS），及各种meta信息。

- 可以添加在头部区域的元素标签为: \<title>, \<style>, \<meta>, \<link>, \<script>, \<noscript> 和 \<base>

##### \<title> 元素

- \<title> 标签定义了不同文档的标题。

- \<title> 在 HTML/XHTML 文档中是必需的。

- \<title> 元素:

  - 定义了浏览器工具栏的标题

  - 当网页添加到收藏夹时，显示在收藏夹中的标题

  - 显示在搜索引擎结果页面的标题

##### \<base> 元素

- 描述了基本的链接地址/链接目标，该标签作为HTML文档中所有链接标签的默认链接。

##### \<link> 元素

- 定义了文档与外部资源之间的关系。
- 通常用于链接到样式表

```html
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

#####  \<style> 元素

- 定义了HTML文档的样式文件引用地址。
- 可以直接添加样式来渲染HTML文档。

##### \<meta> 元素

- 描述基本的元数据。
- 元数据不显示在页面上，但会被浏览器解析。
- 通常用于指定网页的描述，关键词，文件的最后修改时间，作者，和其他元数据。元数据可以使用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他Web服务。

```html
<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">
```

##### \<script> 元素

- 用于加载脚本文件。

[详述](https://www.runoob.com/html/html-head.html)

#### 10.  HTML CSS

CSS 可以通过以下方式添加到HTML中:

- 内联样式- 在HTML元素中使用"style" **属性**
- 内部样式表 -在HTML文档头部 <head> 区域使用<style> **元素** 来包含CSS
- 外部引用 - 使用外部 CSS **文件**

##### 内联样式

```html
<p style="color:blue;margin-left:20px;">这是一个段落。</p>
```

##### 内部样式表

```html
<head>
<style type="text/css">
body {background-color:yellow;}
p {color:blue;}
</style>
</head>
```

##### 外部样式表

```html
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

#### 11.  HTML 图像

- 图像标签(**\<img>**)

​	\<img> 是空标签，意思是说，它只包含属性，并且没有闭合标签。

- 图像源属性(**Src**)

​	src 指 "source"。源属性的值是图像的 URL 地址。

- 图像Alt属性(**Alt**)

​	alt 属性用来为图像定义一串预备的可替换的文本。在浏览器无法载入图像时，替换文本属性告诉读者她们失去的信息。

- 图像高度与宽度(**width & height**)

​	height（高度） 与 width（宽度）属性用于设置图像的高度与宽度。默认单位为像素(px)。

#### 12.  HTML 表格

- HTML 表格由 **\<table>** 标签来定义。
- **\<thead > 用于定义表格的标题部分:** 在 \<thead > 中，使用 \<th > 元素定义列的标题，以上实例中列标题分别为"列标题1"，"列标题2"和"列标题3"。
- **\<tbody > 用于定义表格的主体部分:** 在 \<tbody > 中，使用 \<tr > 元素定义行，并在每行中使用 \<td > 元素定义单元格数据，以上实例中有两行数据，每行包含三个单元格。

- 每个表格均有若干行（由 **\<tr>** 标签定义），每行被分割为若干单元格（由 **\<td>** 标签定义），表格可以包含标题行（**\<th>**）用于定义列的标题。

  - **tr**：tr 是 table row 的缩写，表示表格的一行。

  - **td**：td 是 table data 的缩写，表示表格的数据单元格。

  - **th**：th 是 table header的缩写，表示表格的表头单元格。

[更多属性](https://www.runoob.com/html/html-tables.html)

#### 13.  HTML 列表

##### 无序列表

​	使用\<ul>标签

```html
<ul>
<li>Coffee</li>
<li>Milk</li>
</ul>
```

##### 有序列表

​	使用\<ol>标签

```html
<ol>
<li>Coffee</li>
<li>Milk</li>
</ol>
```

##### 自定义列表

​	自定义列表以 \<dl> 标签开始。每个自定义列表项以 \<dt> 开始。每个自定义列表项的定义以 \<dd> 开始。

#### 14.  HTML 区块

##### 块级元素

块级元素在浏览器显示时，通常会以新行来开始（和结束）。

##### 内联元素

内联元素在显示时通常不会以新行开始。

##### \<div> 元素

- 是块级元素，可用于组合其他 HTML 元素的容器。
- 没有特定的含义。浏览器会在其前后显示折行。

- 与 CSS 一同使用，可用于对大的内容块设置样式属性。

- 另一个常见的用途是文档布局。它取代了使用表格定义布局的老式方法。使用 \<table> 元素进行文档布局不是表格的正确用法。\<table> 元素的作用是显示表格化的数据。

##### \<span> 元素

- 是内联元素，可用作文本的容器

- 没有特定的含义。

- 与 CSS 一同使用时，可用于为部分文本设置样式属性。

#### 15.  HTML 布局

​	大多数网站可以使用 **\<div>** 或者 **\<table>** 元素来创建多列。CSS 用于对元素进行定位，或者为页面创建背景以及色彩丰富的外观。但**不建议使用**table作为布局工具。

#### 16.  HTML 表单和输入

- HTML 表单用于收集用户的输入信息。

- HTML 表单表示文档中的一个区域，此区域包含交互控件，将用户收集到的信息发送到 Web 服务器。

- HTML 表单通常包含各种输入字段、复选框、单选按钮、下拉列表等元素。

##### 表单

- 表单是一个包含表单元素的区域。

- 表单元素是允许用户在表单中输入内容，比如：文本域（textarea）、下拉列表（select）、单选框（radio-buttons）、复选框（checkbox） 等等。

- 我们可以使用 **\<form>** 标签来创建表单:

##### 表单 - 输入元素

- 多数情况下被用到的表单标签是输入标签 **<input>**。

- 输入类型是由 **type** 属性定义。

###### 文本域

通过`<input type="text">`设定

**注意:**表单本身并不可见。同时，在大多数浏览器中，文本域的默认宽度是 20 个字符。 

###### 密码字段

通过`<input type="password">`设定

**注意：**密码字段字符不会明文显示，而是以星号 ***** 或圆点 **.** 替代。

###### 单选按钮

通过`<input type="radio">`设定

###### 复选框

通过`<input type="checkbox">`设定

###### 提交按钮

通过`<input type="submit">`设定

[更多标签列表](https://www.runoob.com/tags/ref-byfunc.html)

#### 17.  HTML 框架

##### iframe语法

```html
<iframe src="URL"></iframe>
```

##### 高度与宽度

```html
<iframe src="demo_iframe.htm" width="200" height="200"></iframe>
```

##### 去除边框

```html
<iframe src="demo_iframe.htm" frameborder="0"></iframe>
```

##### 使用iframe来显示目标链接的页面

```html
<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
<p><a href="https://www.runoob.com" target="iframe_a" rel="noopener">RUNOOB.COM</a></p>
```

#### 18.  HTML 颜色

##### [颜色名](https://www.runoob.com/html/html-colornames.html)

##### 颜色值

- 颜色值由十六进制来表示红、绿、蓝（RGB）。

- 每个颜色的最低值为 0(十六进制为 00)，最高值为 255(十六进制为FF)。

- 十六进制值的写法为 # 号后跟三个或六个十六进制字符。三位数表示法为：#RGB，转换为6位数表示为：#RRGGBB。

#### 19.  HTML 脚本

##### \<script> 标签

- 用于定义客户端脚本，比如 JavaScript。

- 既可包含脚本语句，也可通过 src 属性指向外部脚本文件。

##### \<noscript> 标签

- 提供无法使用脚本时的替代内容，比方在浏览器禁用脚本时，或浏览器不支持客户端脚本时。

- 可包含普通 HTML 页面的 body 元素中能够找到的所有元素。

#### 20.  HTML 字符实体

- HTML 中的预留字符必须被替换为字符实体。

- 一些在键盘上找不到的字符也可以使用字符实体来替换。

##### 不间断空格

`&nbsp;`

##### [HTML实体参考手册](https://www.runoob.com/tags/ref-entities.html)

#### 21.  HTML URL

​	统一资源定位器(Uniform Resouce Locators)是一个网页地址。可以有字母组成，或互联网协议(IP)地址。

```html
scheme`://`host.domain`:`port`/`path`/`filename
```

- scheme - 定义因特网服务的类型。最常见的类型是 http
- host - 定义域主机（http 的默认主机是 www）
- domain - 定义因特网域名，比如 runoob.com
- :port - 定义主机上的端口号（http 的默认端口号是 80）
- path - 定义服务器上的路径（如果省略，则文档必须位于网站的根目录中）。
- filename - 定义文档/资源的名称

[**URL编码参考手册**](https://www.runoob.com/tags/html-urlencode.html)

#### 22.  HTML 实用手册

#####   [HTML 速查列表](https://www.runoob.com/html/html-quicklist.html)

[**HTML 标签简写及全称**](https://www.runoob.com/html/html-tag-name.html)



### HTML5教程

#### 1.  HTML5 新元素

​	可以为HTML添加新元素可，**"教会"** 浏览器处理 **"未知"** 的 HTML 元素。

```html
<style>
myHero {
    display: block;
    background-color: #ddd;
    padding: 50px;
    font-size: 30px;
}
</style> 
```

​	向HTML添加新元素**\<myHero>**，并定义样式。

#### 2.  HTML5 Canvas 

​	\<canvas> 标签定义图形，比如图表和其他图像，您必须使用脚本来绘制图形。在画布上（Canvas）画一个红色矩形，渐变矩形，彩色矩形，和一些彩色的文字。

[Canvas参考手册](https://www.runoob.com/html/html5-canvas.html)

#### 3.  HTML5 SVG

##### SVG的优势

- SVG 定义为可缩放矢量图形。

- HTML5 支持内联 SVG。

- HTML **\<svg>** 元素是 SVG 图形的容器。

- SVG 有多种绘制路径、框、圆、文本和图形图像的方法。

##### SVG 与 Canvas两者间的区别

- SVG 是一种使用 XML 描述 2D 图形的语言。
- Canvas 通过 JavaScript 来绘制 2D 图形。

- SVG 基于 XML，这意味着 SVG DOM 中的每个元素都是可用的。您可以为某个元素附加 JavaScript 事件处理器。

- 在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够自动重现图形。

- Canvas 是逐像素进行渲染的。在 canvas 中，一旦图形被绘制完成，它就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象。

#### 4.  HTML5 MathML

​	HTML5 可以在文档中使用 MathML 元素，对应的标签是 \<math>...\</math> 。

​	MathML 是数学标记语言，是一种基于XML（标准通用标记语言的子集）的标准，用来在互联网上书写数学符号和公式的置标语言。

**注意：**目前只有 Firefox 或 Safari 浏览器支持，大部分浏览器还不支持 MathML 标签，如果你的浏览器不支持该标签，可以使用最新版的 Firefox 或 Safari 浏览器查看。另外我们可以使用第三方的[样式库](https://static.runoob.com/assets/js/mathml/mathml.zip)来支持数学标记.

#### 5.  HTML5 拖放（Drag 和 Drop）

- 拖放是一种常见的特性，即抓取对象以后拖到另一个位置。

- 在 HTML5 中，拖放是标准的一部分，任何元素都能够拖放。

##### 设置元素为可拖放

```html
<img draggable="true">
```

##### 拖动什么 - ondragstart 和 setData()

​	当监测到拖拽行为时，触发ondragstart，进入对应函数，函数中规定了拖拽的元素是什么，及其id对于的名称。

##### 放到何处 - ondragover

​	当拖拽至可放置的地方时，但不松开鼠标放置，触发ondragover，此时执行对应函数，取消默认不可放置的设置。

##### 进行放置 - ondrop

​	当放置被拖数据时，会发生drop事件。

#### 6.  HTML5 地理定位

​	Geolocation API 用于获得用户的地理位置。

##### 使用地理定位

- 使用 getCurrentPosition() 方法来获得用户的位置。

##### 其他有趣的方法

- watchPosition() - 返回用户的当前位置，并继续返回用户移动时的更新位置（就像汽车上的 GPS）。

- clearWatch() - 停止 watchPosition() 方法。

#### 7.  HTML5 Video

##### 如何工作

```html
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
您的浏览器不支持Video标签。
</video>
```

- 提供了播放、暂停和音量控件来控制视频。

- 提供了 width 和 height 属性控制视频的尺寸。如果设置的高度和宽度，所需的视频空间会在页面加载时保留。如果没有设置这些属性，浏览器不知道大小的视频，浏览器就不能再加载时保留特定的空间，页面就会根据原始视频的大小而改变。

- \<video> 与\</video> 标签之间插入的内容是提供给不支持 video 元素的浏览器显示的。

- 支持多个 \<source> 元素。\<source> 元素可以链接不同的视频文件。浏览器将使用第一个可识别的格式。


#### 8.  HTML5 Audio

##### 如何工作

```html
<audio controls>
  <source src="horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
您的浏览器不支持 audio 元素。
</audio>
```

- control 属性供添加播放、暂停和音量控件。

- 在\<audio> 与 \</audio> 之间你需要插入浏览器不支持的\<audio>元素的提示文本 。

- 允许使用多个 \<source> 元素。 \<source> 元素可以链接不同的音频文件，浏览器将使用第一个支持的音频文件。

#### 9.  HTML5 Input类型

​	[大部分类型查阅](https://www.runoob.com/html/html5-form-input-types.html)

#### 10.  HTML5 表单

##### 表单元素

###### \<datalist>元素

- 规定输入域的选项列表。

- 规定 form 或 input 域应该拥有自动完成功能。当用户在自动完成域中开始输入时，浏览器应该在该域中显示填写的选项。

- 使用 \<input> 元素的列表属性与 \<datalist> 元素绑定。

```html
<input list="browsers">
 
<datalist id="browsers">
  <option value="Internet Explorer">
  <option value="Firefox">
  <option value="Chrome">
  <option value="Opera">
  <option value="Safari">
</datalist>
```

###### \<keygen> 元素

- 提供一种验证用户的可靠方法。

- 用于表单的密钥对生成器字段。

- 当提交表单时，会生成两个键，一个是私钥，一个公钥。私钥（private key）存储于客户端，公钥（public key）则被发送到服务器。公钥可用于之后验证用户的客户端证书（client certificate）。

```html
<form action="demo_keygen.asp" method="get">
用户名: <input type="text" name="usr_name">
加密: <keygen name="security">
<input type="submit">
</form>
```

###### \<output> 元素

- 用于不同类型的输出。

```html
<form oninput="sum.value=parseInt(one.value)+parseInt(two.value)">0
<input type="range" id="a" value="50">100 +
<input type="number" id="b" value="50">=
<output name="x" for="a b"></output>
</form>
```

##### 表单属性

###### \<form> / \<input> autocomplete 属性

- 规定 form 或 input 域应该拥有自动完成功能。
- 当用户在自动完成域中开始输入时，浏览器应该在该域中显示填写的选项。

###### \<form> novalidate 属性

- 是一个布尔（true 或 false）属性。用于设置浏览器不对表单进行验证。

- 当该属性被添加到 <form> 元素上时，浏览器将不会执行默认的表单验证，不会检查输入字段是否符合指定的验证规则。

- 使用 novalidate 属性可以完全控制表单验证的逻辑，可以通过 JavaScript 或其他方式来自定义表单验证的行为。

###### \<input> autofocus 属性

- 是一个布尔属性。

- 规定在页面加载时，域自动地获得焦点。

###### \<input> form 属性

- 规定输入域所属的一个或多个表单。（在表单区域外，引用form属性，仍然属于表单）
- 如需引用一个以上的表单，请使用空格分隔的列表。

###### \<input> formaction 属性

- 用于描述表单提交的URL地址。

- 覆盖 \<form> 元素中的action属性。

- 用于 type="submit" 和 type="image"。

###### \<input> formenctype 属性

- 描述了表单提交到服务器的数据编码 (只对form表单中 method="post" 表单)

- 覆盖 form 元素的 enctype 属性。

- 用于type="submit" 和 type="image" 。

###### \<input> formmethod 属性

- 定义了表单提交的方式。

- 覆盖了 <form> 元素的 method 属性。

- 用于type="submit" 和 type="image" 。

###### \<input> formnovalidate 属性

- 是一个 boolean 属性。

- 描述了 <input> 元素在表单提交时无需被验证。

- 会覆盖 <form> 元素的novalidate属性。

- 用于**type="submit"**。

###### \<input> formtarget 属性

- 指定一个名称或一个关键字来指明表单提交数据接收后的展示。

- 覆盖 \<form>元素的target属性。
- 用于**type="submit"** 和 **type="image"** 。

###### \<input> height &width 属性

- 规定用于 image 类型的 \<input> 标签的图像高度和宽度。

- 只适用于 image 类型的 \<input> 标签。

###### \<input> list 属性

- 规定输入域的datalist。datalist的是输入域的选项列表。

- 用相同的关键字，关联input窗口和内部候选内容datalist。

###### \<input> min & max & step 属性

- 用于为包含数字或日期的 input 类型规定限定（约束）。

- 用于以下类型的 \<input> 标签：date pickers、number 以及 range。

###### \<input> multiple 属性

- 是一个 boolean 属性.

- 规定 \<input> 元素中可选择多个值。

- 适用于以下类型的 \<input> 标签：email 和 file:

###### \<input> pattern 属性

- 描述了一个正则表达式用于验证 \<input> 元素的值。

- 适用于以下类型的 \<input> 标签: text, search, url, tel, email, 和 password。

###### \<input> placeholder 属性

- 提供一种提示（hint），描述输入域所期待的值。

- 简短的提示在用户输入值前会显示在输入域上。

- 适用于以下类型的 \<input> 标签：text, search, url, telephone, email 以及 password。

###### \<input> required 属性

- 是一个 boolean 属性.

- 规定必须在提交之前填写输入域（不能为空）。

- 适用于以下类型的 \<input> 标签：text, search, url, telephone, email, password, date pickers, number, checkbox, radio 以及 file。

#### 11.  HTML5 语义元素

- 一个语义元素能够清楚的描述其意义给浏览器和开发者。

- **无语义** 元素实例: \<div> 和 \<span> - 无需考虑内容。

- **语义**元素实例: \<form>, \<table>, and \<img> - 清楚的定义了它的内容。

##### \<section> 元素

- 定义文档中的节（section、区段）。比如章节、页眉、页脚或文档中的其他部分。

##### \<article> 元素

- 定义独立的内容。.

- 使用实例:

  - Forum post

  - Blog post

  - News story

  - Comment

##### \<nav> 元素

- 定义导航链接的部分。

- 用于定义页面的导航链接部分区域，但是，不是所有的链接都需要包含在 \<nav> 元素中！

##### \<aside> 元素

- 定义页面主区域内容之外的内容（比如侧边栏）。

- 内容应与主区域的内容相关。

##### \<header> 元素

- 描述了文档的头部区域。

- 主要用于定义内容的介绍展示区域。
- 在页面中你可以使用多个<header> 元素。

##### \<footer> 元素

- 描述了文档的底部区域。

- 应该包含它的包含元素。

- 一个页脚通常包含文档的作者，著作权信息，链接的使用条款，联系信息等。

- 文档中你可以使用多个 \<footer>元素。

##### \<figure> & \<figcaption> 元素

###### \<figure>

- 规定独立的流内容（图像、图表、照片、代码等等）。

- 应该与主内容相关，但如果被删除，则不应对文档流产生影响。

###### \<figcaption>

- 定义 \<figure> 元素的标题.

- 应该被置于 "figure" 元素的第一个或最后一个子元素的位置。

#### 12.  HTML5 Web 存储

##### localStorage & sessionStorage

客户端存储数据的两个对象为：

- localStorage - 用于长久保存整个网站的数据，保存的数据没有过期时间，直到手动去除。
- sessionStorage - 用于临时保存同一窗口(或标签页)的数据，在关闭窗口或标签页之后将会删除这些数据。

###### localStorage

- 存储的数据没有时间限制。第二天、第二周或下一年之后，数据依然可用。
- 可使用的API：
  - 保存数据：localStorage.setItem(key,value);
  - 读取数据：localStorage.getItem(key);
  - 删除单个数据：localStorage.removeItem(key);
  - 删除所有数据：localStorage.clear();
  - 得到某个索引的key：localStorage.key(index);

###### sessionStorage

- 针对一个 session 进行数据存储。当用户关闭浏览器窗口后，数据会被删除。

#### 13.  HTML5 Web SQL 数据库

##### 核心方法

1. **openDatabase**：这个方法使用现有的数据库或者新建的数据库创建一个数据库对象。
2. **transaction**：这个方法让我们能够控制一个事务，以及基于这种情况执行提交或者回滚。
3. **executeSql**：这个方法用于执行实际的 SQL 查询。

##### 打开数据库

openDatabase()对应参数说明：

1. 数据库名称
2. 版本号
3. 描述文本
4. 数据库大小
5. 创建回调

##### 执行查询操作

database.transaction()

##### 插入数据

SQL语言

##### 读取数据

SQL语言

##### 删除记录

SQL语言

##### 更新记录

SQL语言

#### 14.  HTML5 Web Workers

- 运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。
- 您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web worker 在后台运行。

##### 创建 Web Worker 文件

- 创建一个JS脚本。

##### 创建 Web Worker 对象

- 从HTML页面调用它。

##### 终止 Web Worker

- 使用terminate()方法

##### Web Workers 和 DOM

由于 web worker 位于外部文件中，它们无法访问下列 JavaScript 对象：

- window 对象
- document 对象
- parent 对象

#### 15.  HTML5 服务器发送事件（SSE，Server-Sent Events）

- 允许网页获得来自服务器的更新。
- Server-Sent 事件 - 单向消息传递。
- EventSource 对象用于接收服务器发送事件通知。

#### 16.  HTML5 WebSocket

- 是HTML5 开始提供的一种在单个 TCP 连接上进行全双工通讯的协议。

- 使得客户端和服务器之间的数据交换变得更加简单，允许服务端主动向客户端推送数据。
- 在 WebSocket API 中，浏览器和服务器只需要完成一次握手，两者之间就直接可以创建持久性的连接，并进行双向数据传输。


### HTML 媒体

#### 1.  HTML 插件

- 辅助应用程序（helper application）是可由浏览器启动的程序。辅助应用程序也称为插件。

- 辅助程序可用于播放音频和视频（以及其他）。辅助程序是使用 \<object> 标签来加载的。

- 使用辅助程序播放视频和音频的一个优势是，您能够允许用户来控制部分或全部播放设置。

- 插件可以通过 \<object> 标签或者 \<embed> 标签添加在页面中。 

##### \<object> 元素

- 定义了在 HTML 文档中嵌入的对象。

- 该标签用于插入对象 (例如在网页中嵌入 Java 小程序, PDF 阅读器, Flash 播放器) 。
- 同样可用于包含HTML文件或者插入一张图片。

##### \<embed> 元素

- 表示一个 HTML Embed 对象 。
- 同样可用于包含HTML文件或者插入一张图片。

#### 2.  HTML 音频（Audio）

##### 使用 \<embed> 元素

- 定义外部（非 HTML）内容的容器。（这是一个 HTML5 标签，在 HTML4 中是非法的，但是所有浏览器中都有效）。

问题：

- \<embed> 标签在 HTML 4 中是无效的。页面无法通过 HTML 4 验证。
- 不同的浏览器对音频格式的支持也不同。
- 如果浏览器不支持该文件格式，没有插件的话就无法播放该音频。
- 如果用户的计算机未安装插件，无法播放音频。
- 如果把该文件转换为其他格式，仍然无法在所有浏览器中播放。

##### 使用 \<object> 元素

- 可以定义外部（非 HTML）内容的容器。

问题：

- 不同的浏览器对音频格式的支持也不同。
- 如果浏览器不支持该文件格式，没有插件的话就无法播放该音频。
- 如果用户的计算机未安装插件，无法播放音频。
- 如果把该文件转换为其他格式，仍然无法在所有浏览器中播放。

##### \<audio> 元素

- 是一个 HTML5 元素，在 HTML 4 中是非法的，但在所有浏览器中都有效。

问题：

- \<audio> 标签在 HTML 4 中是无效的。您的页面无法通过 HTML 4 验证。
- 您必须把音频文件转换为不同的格式。
- \<audio> 元素在老式浏览器中不起作用。

##### 使用超链接

- 如果网页包含指向媒体文件的超链接，大多数浏览器会使用"辅助应用程序"来播放文件。

#### 3.  HTML 视频（Video）

##### 使用 \<embed> 元素

- 作用是在 HTML 页面中嵌入多媒体元素。

问题：

- HTML4 无法识别 <embed> 标签。您的页面无法通过验证。
- 如果浏览器不支持 Flash，那么视频将无法播放
- iPad 和 iPhone 不能显示 Flash 视频。
- 如果您将视频转换为其他格式，那么它仍然不能在所有浏览器中播放。

##### 使用 \<object> 元素

- 作用是在 HTML 页面中嵌入多媒体元素。

问题：

- 如果浏览器不支持 Flash，将无法播放视频。
- iPad 和 iPhone 不能显示 Flash 视频。
- 如果您将视频转换为其他格式，那么它仍然不能在所有浏览器中播放。

##### \<video> 元素

- HTML5 \<video> 标签定义了一个视频或者影片。
- 所有现代浏览器中都支持。

问题：

- 您必须把视频转换为很多不同的格式。
- \<video> 元素在老式浏览器中无效。

##### 使用超链接

- 如果网页包含指向媒体文件的超链接，大多数浏览器会使用"辅助应用程序"来播放文件。

## 第二部分  CSS

### CSS 教程

#### 1.  CSS 语法

##### CSS 实例

CSS声明总是以分号 **`;`** 结束，声明总以大括号 **`{}`** 括起来:

```css
p {
    color:red;
    text-align:center;
}
```

##### CSS 注释

注释是用来解释你的代码，并且可以随意编辑它，浏览器会忽略它。CSS注释以 **`/*`** 开始, 以 **`*/`** 结束

```html
/*这是个注释*/
p
{
    text-align:center;
    /*这是另一个注释*/
    color:black;
    font-family:arial;
}
```

#### 2.  CSS id 和 class

##### id 选择器

```css
#para1
{
    text-align:center;
    color:red;
}
```

##### class 选择器

```css
.center 
{
    text-align:center;
}
```

#### 3.  CSS 创建

##### 如何插入样式表

- 外部样式表（External style sheet）
- 内部样式表（Internal style sheet）
- 内联样式（Inline style）

##### 外部样式表

```css
<head>
	<link rel="stylesheet" type="text/css" 				href="mystyle.css">
</head>
```

##### 内部样式表

```css
<head>
	<style>
		hr {color:sienna;}
		p {margin-left:20px;}
		body {background-								image:url("images/back40.gif");}
</style>
</head>
```

##### 内联样式

```css
<p style="color:sienna;margin-left:20px">这是一个段落。</p>
```

##### 多重样式

- 如果某些属性在不同的样式表中被同样的选择器定义，那么属性值将从更具体的样式表中被继承过来。 

##### 多重样式优先级

**（内联样式）Inline style > （内部样式）Internal style sheet >（外部样式）External style sheet > 浏览器默认样式**

#### 4.  CSS 背景

##### 背景颜色

- 由 background-color 属性定义

```css
body {background-color:#b0c4de;}
```

##### 背景图像

- 由 background-image 属性定义、

```css
body {background-image:url('paper.gif');}
```

##### 背景图像 - 水平或垂直平铺

- 由 background-repeat 属性定义：repeat-x or repeat-y

```css
body
{
background-image:url('gradient2.png');
background-repeat:repeat-x;
}
```

##### 背景图像 - 设置定位与不平铺

- background-repeat:no-repeat：设置不平铺
- background-position:right top：设置定位

##### 背景 - 简写属性

- 将属性合并到一个属性中，简写为background：

```css
body {background:#ffffff url('img_tree.png') no-repeat right top;}
```

- 当使用简写属性时，属性值的顺序为：:

  - background-color
  - background-image

  - background-repeat

  - background-attachment
  - background-position

#### 5.  CSS 文本格式

##### 文本颜色

- 由 color 属性定义

```css
body {color:red;}
h1 {color:#00ff00;}
h2 {color:rgb(255,0,0);}
```

##### 文本的对齐方式

- 由 text-align 定义

```css
h1 {text-align:center;}
p.date {text-align:right;}
/* 每一行的展开宽度相等，左右边距是对齐的 */
p.main {text-align:justify;}
```

##### 文本修饰

- text-decoration：用来设置或删除文本的装饰，主要用来删除链接的下划线
- 包含：overline；line-through；underline

```css
a {text-decoration:none;}
```

##### 文本转换

- 由 text-transform 定义：用来指定一个文本中的大写和小写字母。可用于所有字句变成大写或小写字母，或每个单词的首字母大写。
- 包含：uppercase；lowercase；capitalize

##### 文本缩进

- 由 text-indent 定义：用来指定文本的第一行的缩进。

```css
p {text-indent:50px;}
```

#### 6.  CSS 字体

##### CSS 字型

- **通用字体系列** - 拥有相似外观的字体系统组合（如“Serif”或“Monospace”）

- **特定字体系列** - 一个特定的字体系列（如“Times”或“Courier”）

##### 字体系列

- 由 font-family 属性设置文本的字体系列。

-  font-family 属性应该设置几个字体名称作为一种"后备"机制，如果浏览器不支持第一种字体，他将尝试下一种字体。

- 如果字体系列的名称超过一个字，它必须用引号，如Font Family："宋体"。

- 多个字体系列是用一个逗号分隔指明。

##### 字体样式

- 正常 - 正常显示文本
- 斜体 - 以斜体字显示的文本
- 倾斜的文字 - 文字向一边倾斜（与斜体类似，但不太支持）

```css
p.normal {font-style:normal;}
p.italic {font-style:italic;}
p.oblique {font-style:oblique;}
```

##### 字体大小

- 由 font-size 属性设置文本的大小。

###### 绝对大小

- 设置一个指定大小的文本
- 不允许用户在所有浏览器中改变文本大小
- 确定了输出的物理尺寸时绝对大小很有用

设置字体大小的像素：

```css
h1 {font-size:40px;}
h2 {font-size:30px;}
p {font-size:14px;}
```

###### 相对大小

- 相对于周围的元素来设置大小
- 允许用户在浏览器中改变字体的大小

用**EM**来设置字体大小：

- 1em 和当前字体大小相等。在浏览器中默认的字体大小时16px。

```css
h1 {font-size:2.5em;} /* 40px/16=2.5em */
h2 {font-size:1.875em;} /* 30px/16=1.875em */
p {font-size:0.875em;} /* 14px/16=0.875em */
```

使用百分比和**EM**组合：

- 在所有浏览器的解决方案中，设置\<body>元素的默认字体大小是百分比

```css
body {font-size:100%;}
h1 {font-size:2.5em;}
h2 {font-size:1.875em;}
p {font-size:0.875em;}
```

#### 7.  CSS 链接

##### 链接样式

​	链接的样式，可以用任何CSS属性（如颜色，字体，背景等）。不同的链接可以有不同的样式。

- a:link - 正常，未访问过的链接
- a:visited - 用户已访问过的链接
- a:hover - 当用户鼠标放在链接上时
  - 必须跟在 a:link 和 a:visited后面

- a:active - 链接被点击的那一刻
  - 必须跟在 a:hover后面


##### 文本修饰

- text-decoration 属性主要用于删除链接中的下划线

##### 背景颜色

- background-color 属性用于指定连接背景颜色

#### 8.  CSS 列表

##### 列表

- 无序列表**`ul`** - 列表项标记用特殊图形
- 有序列表**`ol`** - 列表项的标记有数字或字母

##### 不同的列表项标记

```css
ul.a {list-style-type: circle;}
ul.b {list-style-type: square;}
 
ol.c {list-style-type: upper-roman;}
ol.d {list-style-type: lower-alpha;}
```

##### 作为列表项标记的图像

- list-style-image：定义使用的列表样式图像

```css
ul
{
    list-style-image: url('sqpurple.gif');
}
```

##### 列表 - 简写属性

- 在单个属性中可以指定所有的列表属性。

```css
ul
{
    list-style: square url("sqpurple.gif");
}
```

- list-style-type
- list-style-position (有关说明，请参见下面的CSS属性表)
- list-style-image

允许缺项，其余项按照顺序即可。

#### 9.  CSS 表格

##### 表格边框

- 由 border 属性定义

指定一个表格的 th & td 元素的黑色边框

```css
table, th, td
{
    border: 1px solid black;
}
```

##### 折叠边框

- 由 border-collapse 属性定义

##### 表格的宽度和高度

- 由 width & height 定义

##### 表格文字对齐

- 由 text-align 属性定义水平对齐方式
- 由 vertical-align 属性定义垂直对齐方式

##### 表格填充

- 由 padding 属性定义

##### 表格颜色

- 由 background-color 属性定义

#### 10.  CSS 盒子模型（Box Model）

- **Margin(外边距)** - 清除边框外的区域，外边距是透明的。
- **Border(边框)** - 围绕在内边距和内容外的边框。
- **Padding(内边距)** - 清除内容周围的区域，内边距是透明的。
- **Content(内容)** - 盒子的内容，显示文本和图像。

​	**当指定一个 CSS 元素的宽度和高度时，只是设置内容区域的宽度和高度，而不是总宽度，需要自己计算总宽度。**

#### 11.  CSS 边框

##### 边框样式

- none: 默认无边框

- dotted: 定义一个点线边框
- dashed: 定义一个虚线边框
- solid: 定义实线边框、
- double: 定义两个边框。 两个边框的宽度和 border-width 的值相同
- groove: 定义3D沟槽边框。效果取决于边框的颜色值
- ridge: 定义3D脊边框。效果取决于边框的颜色值
- inset:定义一个3D的嵌入边框。效果取决于边框的颜色值
- outset: 定义一个3D突出边框。 效果取决于边框的颜色值

##### 边框宽度

- 由 border-width 属性定义
- 可以使用px，pt，cm，em等，或者使用关键字：thick，medium（默认值）和thin。

##### 边框颜色

- 由 border-color 属性设置
  - name - 指定颜色的名称
  - RGB - 指定RGB值
  - Hex - 指定16进制值

- 可以设置为 transparent
- 单独设置颜色不起作用，必须先设置边框样式

##### 边框 - 单独设置各边

- 使用 border-top-style || border-right-style || border-bottom-style || border-left-style
- 为 border-style 设置多个参数，一次性按顺序设置每个边框
  - `border-style:dotted solid double dashed;`
    - 上 dotted
    - 右 solid
    - 下 double
    - 左 dashed

##### 边框 - 简写属性

```css
border:5px solid red;
```

- border-width
- border-style（required）
- border-color

#### 12.  CSS 轮廓（outline）

- 是绘制于元素周围的一条线，位于边框边缘的外围，可以起到突出元素的作用

#### 13.  CSS 外边框（margin）

- 清除周围的元素区域。没有背景颜色，是完全透明的。
- 可以是：auto，length，%

##### 单边外边距属性

- 由 margin-top || margin-bottom || margin-right || margin-left

##### 简写属性

- 一次性指定 margin 所有边距属性：

```css
margin:100px 50px;
```

#### 14.  CSS 填充（padding）

- 使用 padding 内边距被清除时，所释放的区域将会收到元素背景颜色的填充。
- 可以是：length，%

##### 单边外边距属性

- 由 padding-top || padding-bottom || padding-right || padding-left

##### 简写属性

- 一次性指定 padding 所有填充属性：

```css
padding:25px 50px;
```

#### 15.  CSS 分组和嵌套选择器

##### 分组选择器

```css
h1,h2,p
{
    color:green;
}
```

##### 嵌套选择器

- 适用于选择器内部的选择器的样式。
  - `p{ }`: 为所有 p 元素指定一个样式。
  - `.marked{ }`: 为所有 class="marked" 的元素指定一个样式。
  - `.marked p{ }`: 为所有 class="marked" 元素内的 p 元素指定一个样式。
  - `p.marked{ }`: 为所有 class="marked" 的 p 元素指定一个样式。

#### 16.  CSS 尺寸（Dimension）

- 允许控制元素的高度和宽度。同样，允许增加行间距。

- [实例](https://www.runoob.com/css/css-dimension.html)



#### 17.  CSS 显示（Display）与可见性（Visibility）

##### 隐藏元素 

- `display:none` ：隐藏元素，且隐藏的元素不会占用任何空间。

  ```css
  h1.hidden {display:none;}
  ```

- `visibility:hidden`：隐藏元素，且隐藏的元素仍需占用与为隐藏之前一样的空间。

  ```css
  h1.hidden {visibility:hidden;}
  ```

##### Display - 块和内联元素

- 快元素是一个元素，占用了全部宽度，前后都是换行符。
- 内联元素只需要必要的宽度，不强制换行。

##### 改变一个元素显示

- 将块元素显示为内联元素：`li {display:inline;}`

- 将内联元素作为块元素：`span {display:block;}`
  - 内联元素显示为块，不允许内部嵌套块元素。

#### 18.  CSS 定位（Position）

- 由 position 属性定义，它有五个值。
  - static
  - relative
  - fixed
  - absolute
  - sticky

##### static 定位

- HTML元素的默认值，即没有定位，遵循正常的文档流对象。
- 不受top，bottom，left，right的影响。

##### fixed 定位

- 元素的位置相对于浏览器窗口是固定位置。即使窗口是滚动的它也不会移动。
- 元素位置与文档流无关，因此不占据空间。
- 可与其它元素重叠

##### relative 定位

- 相对定位元素的定位是相对其正常位置。移动相对定位元素，但它原本所占空间不会改变。
- 经常被用来作为绝对定位元素的容器块。即通过 relative 设置父元素的缩进，通过 absolute 设置子元素相对于父元素的缩进。

##### absolute 定位

- 绝对定位的元素位置相对于最近的以定位的父元素，如果元素没有以定位的父元素，它的位置相对于 \<html>。
- 使元素位置与文档流无关，不占据空间。
- 定位的元素和其他元素重叠。

##### sticky 定位

- 基于用户的滚动位置定位。
- 粘性定位的元素是依赖于用户的滚动，在 **position:relative** 与 **position:fixed** 定位之间切换。它的行为就像 **position:relative;** 而当页面滚动超出目标区域时，它的表现就像 **position:fixed;**，它会固定在目标位置。元素定位表现为在跨越特定阈值前为相对定位，之后为固定定位。

##### 重叠的元素

- 元素的定位与文档流无关，所以他们可以覆盖页面上的其他元素。
- z-index 属性制定了一个元素的堆叠顺序，可正可负。

#### 19.  CSS 布局 - Overflow

- 用于控制内容溢出元素框时显示的方向。

| 值      | 描述                                                     |
| :------ | :------------------------------------------------------- |
| visible | 默认值。内容不会被修剪，会呈现在元素框之外。             |
| hidden  | 内容会被修剪，并且其余内容是不可见的。                   |
| scroll  | 内容会被修剪，但是浏览器会显示滚动条以便查看其余的内容。 |
| auto    | 如果内容被修剪，则浏览器会显示滚动条以便查看其余的内容。 |
| inherit | 规定应该从父元素继承 overflow 属性的值。                 |

#### 20.  CSS 浮动（Float）

##### 元素浮动

- 一个浮动元素会尽量向左或向右移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。
- 浮动元素之后的元素将围绕它。
- 浮动元素之前的元素将不会受到影响。

```css
img
{
    float:right;
}
```

##### 彼此相邻的浮动元素

- 如果你把几个浮动的元素放到一起，如果有空间的话，它们将彼此相邻。

##### 清除浮动 - 使用 clear

- 元素浮动后周围的元素会重新排列，使用 clear 避免这种情况。
- **clear** 属性指定元素两侧不能出现浮动元素。

```css
.text_line
{
    clear:both;
}
```

#### 21.  CSS 布局 - 水平 & 垂直分布

##### 元素居中对齐

- 使用`margin: auto;`，并设置元素的宽度将防止它溢出容器的边缘。
- 如果没有设置`width`属性（或者设置100%），居中对齐将不起作用。

```css
.center {
    margin: auto;
    width: 50%;
    border: 3px solid green;
    padding: 10px;
}
```

##### 文本居中对齐

- 使用`text-align: center;`

##### 图片居中对齐

- 使用`margin: auto;`并将它放到**块**元素中。

##### 左右对齐 - 使用定位方式

- 使用`position: absolute;`属性来对齐元素。
- 绝对定位的元素会被从正常流中删除，并且能够交叠元素。
- 当使用**`position`**来对齐元素时，通常**`<body>`**元素会设置**`margin`**和**`padding`**。避免在不同的浏览器中出现差异。

##### 左右对齐 - 使用 float 方式

- 对 \<body> 元素的外边距和内边距进行预定义是一个好主意。这样可以避免在不同的浏览器中出现可见的差异。

- 如果子元素的高度大于父元素，且子元素设置了浮动，那么子元素将溢出。

  - 添加 `clearfix` 类。

  - 使用 `overflow: auto;`

```css
.clearfix {
    overflow: auto;
}
```

##### 垂直居中对齐 - 使用 padding

- 头部顶部使用padding。

##### 垂直居中 - 使用 line-height

- 设置 line-height 为居中。
- 文本有多行

```css
.center p {
    line-height: 1.5;
    display: inline-block;
    vertical-align: middle;
}
```

##### 垂直居中 - 使用 position & transform

- 使用绝对定位和**`transform`**来设置垂直居中。

#### 22.  CSS 组合选择符

##### 后代选择器

- 选取某元素的后代元素

```css
div p
{
  background-color:yellow;
}
```

##### 子元素选择器

- 只能选择作为某元素直接/一级子元素的元素

```css
div>p
{
  background-color:yellow;
}
```

##### 相邻兄弟选择武器（Adjacent sibling selector）

- 选择紧接在另一元素后面的元素，且二者具有相同的父元素。

```css
div+p
{
  background-color:yellow;
}
```

##### 后续兄弟选择器

- 选取所有指定元素之后的相邻兄弟元素

```css
div~p
{
  background-color:yellow;
}
```

#### 23.  CSS 伪类（Pseudo-classes）

##### 语法

- 伪类的语法：

​	`selector:pseudo-class {property:value}`

- 也可以使用伪类：

  `selector.class:pseudo-class {property:value}`

##### anchor 伪类

```css
a:link {color:#FF0000;} /* 未访问的链接 */
a:visited {color:#00FF00;} /* 已访问的链接 */
a:hover {color:#FF00FF;} /* 鼠标划过链接 */
a:active {color:#0000FF;} /* 已选中的链接 */
```

##### CSS - :first-child 伪类

- 选择父元素的第一个子元素。
- 一定是第一个元素，而不是第一次出现的该类元素。

###### 匹配所有元素的第一个 \<p> 元素

- 匹配任何元素的第一个子元素，且子元素为 \<p> 元素。 

```css
p:first-child
{
    color:blue;
}
```

###### 匹配所有 \<p> 元素中的第一个 \<i> 元素

- 匹配所有 \<p> 元素中，第一个元素是 \<i> 的元素。

```css
p > i:first-child
{
    color:blue;
}
```

###### 匹配所有作为元素的第一个子元素的 \<p> 元素中所有 \<i>  元素

- 匹配所有元素的第一个子元素是 \<p> 的元素，并匹配其下所有\<i> 元素。

```css
p:first-child i
{
    color:blue;
}
```

##### CSS - :lang 伪类

- 为不同的语言定义特殊的规则。

```css
q:lang(no) {quotes: "~" "~";}
```

#### 24.  CSS 伪元素

##### 语法

- 伪元素的语法：

  `selector:peseudo-element {property:value}`

- 也可以使用伪元素：

  `selector.class:pseudo-element {property:value}`

##### CSS - :first-line 伪元素

- 用于向文本首行设置特殊样式。

```css
p:first-line 
{
    color:#ff0000;
    font-variant:small-caps;
}
```

##### CSS - :first-letter 伪元素

- 用于向文本首字母设置特殊样式。

###### 伪元素和CSS类

```css
p.article:first-letter {color:#ff0000;}

<p class="article">文章段落</p>
```

###### 多个伪元素

- 可以结合多个伪元素来使用

##### CSS - :before 伪元素

- 在元素内容前面插入新内容。

##### CSS - :after 伪元素

- 在元素内容之后插入新的内容。

#### 25.  CSS 导航栏

##### 导航栏 = 连接列表

- 使用 \<ul> & \<li> 元素建立一个链接列表。
- 从列表中删除边距和填充。

##### 垂直导航栏

- 使用 \<a> 元素的样式，建立一个垂直的导航栏。

```css
a
{
    display:block;
    width:60px;
}
```

- display:block - 显示块元素的链接，让整体变为可点击链接区域（不只是文本），它允许我们指定宽度
- width:60px - 块元素默认情况下是最大宽度。我们要指定一个60像素的宽度

###### 激活/当前导航条

- 添加`active`类来标注哪个选项被选中。

```css
li a.active {
    background-color: #4CAF50;
    color: white;
}
```

###### 创建链接并添加边框

- 可以在 \<li> or \<a> 上添加**text-align:center** 样式来让链接居中。

- 可以在 **border** \<ul> 上添加 **border** 属性来让导航栏有边框。如果要在每个选项上添加边框，可以在每个 \<li> 元素上添加**border-bottom** :

###### 全屏高度固定导航条

```css
ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    width: 25%;
    background-color: #f1f1f1;
    height: 100%; /* 全屏高度 */
    position: fixed; 
    overflow: auto; /* 如果导航栏选项多，允许滚动 */
}
```

##### 水平导航栏

- 两种方法创建横向导航栏，**内联（inline）**或者**浮动（float）**的列表项。
- 如果想要链接具有相同的大小，必须使用浮动。

###### 内联列表项

- 创建一个横向导航栏的方法之一是指定元素。

  ```css
  li
  {
      display:inline;
  }
  ```

  - `display:inline;` - 默认情况下，**`<li>`** 元素是块元素。在这里，我们删除换行符之前和之后每个列表项，以显示一行。

###### 浮动列表项

- 对于所有链接宽度相等，浮动`<li>`元素，并指定`<a>`元素的宽度。

  ```css
  li
  {
      float:left;
  }
  a
  {
      display:block;
      width:60px;
  }
  ```

  - float:left - 使用浮动块元素的幻灯片彼此相邻

  - display:block - 显示块元素的链接，让整体变为可点击链接区域（不只是文本），它允许我们指定宽度

  - width:60px - 块元素默认情况下是最大宽度。我们要指定一个60像素的宽度

###### 激活/当前导航条实例

- 添加`active`类来标记哪个选项被选中。

###### 链接右对齐

- 将导航条最右边的选项设置右对齐（`float:right`）。

###### 添加分割线

- 通过**border-right**样式来添加分割线。

###### 固定导航条

- 设置页面的导航条固定在头部或者底部。

##### 灰色水平导航条

```css
ul {
    border: 1px solid #e7e7e7;
    background-color: #f3f3f3;
}
 
li a {
    color: #666;
}
```

#### 26.  CSS 下拉菜单

- 创建一个鼠标移动上去后显示下拉菜单的效果。

##### 基本下拉菜单

- 当鼠标移动到指定元素上时，会出现下拉菜单。

##### 下拉菜单

- 创建下拉菜单，并允许用户选取列表中的某一项。

##### 下拉内容对齐方式

```css
.dropdown-content {    
    right: 0;
}
```

#### 27.  CSS 提示工具（Tooltip）

##### 基础提示框（Tooltip）

- 指示框在鼠标移动到指定元素上时显示。

##### 定位提示工具

- 指示在元素的左右正中间，使用 `top:-5px` 修正位置。具体像素大小由 padding 决定。
- 指示在元素的上下正中间，使用 `margin-left: -60px` 修正位置，具体大小由表格宽度决定。

##### 添加箭头

- 使用伪元素 `::after` 及 content 属性为提示工具创建一个小箭头标志。箭头是由边框组成的，但组合起来后提示工具类似语音信息框。
- `border-color` ：将四边形按对角线分为四个三角形，仅显示上三角就类似箭头效果。

##### 淡入效果

- 使用 CSS3 的 transition 属性及 opacity 属性来实现提示工具的淡入效果。

#### 28.  CSS 图片廊

​	[实例](https://www.runoob.com/try/try.php?filename=trycss_image_gallery)

#### 29.  CSS 图像透明/不透明

​	[实例](https://www.runoob.com/css/css-image-transparency.html)

#### 30.  CSS 图像拼合技术

- 使用一个拼合图像，利用偏移完成目标。

  [实例](https://www.runoob.com/css/css-image-sprites.html)

#### 31.  CSS 媒体类型

##### @media 规则

- 允许在相同样式表为不同媒体设置不同的样式。
- 可使用 `@media screen` ， `@media print` ， `@media screen,print`

##### [其他媒体类型](https://www.runoob.com/css/css-mediatypes.html)

#### 32.  CSS 属性选择器

- 具有特定属性的HTML元素样式不仅仅是 class 和 id。

##### 属性选择器

- 将包含某个属性的全部元素匹配，例如：`[title]` 会匹配所有设置了该属性的元素。

##### 属性和值选择器

```css
[title=runoob]
{
    border:5px solid green;
}
```

##### 属性和值的选择器 - 多值

- 属性的值中包含特定值即被匹配。
- 包含指定值的 `title` 属性，使用（~）分割属性和值。

```css
[title~=hello] { color:blue; }
```

- 包含指定值的 `lang` 属性，使用（|）分割属性和值。

```css
[lang|=en] { color:blue; }
```

##### 表单样式

- 属性选择器无需使用 class 或 id 的形式

```css
input[type="text"] {
	...
}
```

#### 33.  CSS 表单

##### 输入框（input）样式

- `input[type=text]` - 选取文本输入框
- `input[type=password]` - 选取密码输入框
- `input[type=number]` - 选取数字输入框

##### 输入框填充

- 使用 `padding` 属性可以在输入框中添加内边距。

##### 输入框（input）边框

- 使用 `border` 属性可以修改 input 边框的大小或颜色，使用 `border-radius` 属性可以给 input 添加圆角。

##### 输入框（input）颜色

- 使用 `background-color` 属性来设置输入框的背景颜色，`color` 属性用于修改文本颜色。

##### 输入框（input）聚焦

- 默认情况，输入框获取焦点时，会有蓝色轮廓，设置 input 样式为 `outline: none;` 来忽略该效果。
- 使用 `:focus` 选择器可以设置输入框在获取焦点时的样式。

```css
input[type=text]:focus {
  background-color: lightblue;
}
```

##### 输入框（input）图标

- 在输入框中添加图标，可以使用 `background-image` 属性和用于定位的 `background-position` 属性。
- 注意设置图标的左边距，让图标有一定的空间。

##### 带动画的搜索框

- 使用 CSS `transition` 属性，该属性设置了输入框在获取焦点时会向右延展。

##### 文本框（textarea）样式

- 使用 `resize` 属性来禁用文本框可以重置大小的功能
- `resize: none;`

##### 下拉菜单（select）样式

```css
select {
	...
}
```

##### 按钮样式

```css
input[type=button], input[type=submit], input[type=reset] {
	...
}
 
/* 提示: 使用 width: 100% 设置全宽按钮 */
```

##### 响应式表单

- 可以根据浏览器窗口大小重新布局各个元素，可以通过重置浏览器窗口大小来查看效果。

```css
/* 响应式布局 layout - 在屏幕宽度小于 600px 时， 设置为上下堆叠元素 */
@media screen and (max-width: 600px) {
  .col-25, .col-75, input[type=submit] {
    width: 100%;
    margin-top: 0;
  }
}
```

#### 34.  CSS 计数器

- 通过一个变量来设置，根据规则递增变量。

##### 使用计数器自动编号

- `counter-reset` - 创建或者重置计数器
- `counter-increment` - 递增变量
- `content` - 插入生成的内容
- `counter()` 或 `counters()` 函数 - 将计数器的值添加到元素

```css
body {
  counter-reset: section;
}
 
h2::before {
  counter-increment: section;
  content: "Section " counter(section) ": ";
}
```

##### 嵌套计数器

- 在页面创建一个计时器，在每个 \<h1> 元素前添加计数值，嵌套的计数值则放在 \<h2> 元素前面。

#### 35.  CSS 网页布局

##### 头部区域

- 位于整个网页的顶部，一般用于设置网页的标题或者网页的logo。

##### 菜单导航区域

- 包含了一些链接，可以引导用户浏览其他页面。

##### 内容区域

- 相等的列
  - 两列可以设置 width 为50%，四列可以设置为25%。
- 不相等的列
  - 在中间部分设置内容区域，左右设置导航，加起来100%。 

##### 底部区域

- 在网页的最下方，一般包含版权信息和联系方式等。

##### 响应式网页布局

- 页面的布局会根据屏幕的大小来调整。

#### 36.  CSS !important 规则

- 用于增加样式的权重。
- 与优先级无关，与最终结果直接相关，会覆盖其他声明。

##### 使用建议

- **一定**要优先考虑使用样式规则的优先级来解决问题而不是 `!important`
- **只有**在需要覆盖全站或外部 CSS 的特定页面中使用 `!important`
- **永远不要**在你的插件中使用 `!important`
- **永远不要**在全站范围的 CSS 代码中使用 `!important`

##### 何时使用 !important

- 在网站上设定一个全站样式的 CSS 样式可以使用 `!important` 

### CSS3 教程

#### 1.  CSS3 边框

##### 圆角

- 由 border-radius 属性定义。
- 只有两个输入，第一个对应左上角与右下角。

##### 盒阴影

- 由 box-shadow 属性定义。

##### 边界图片

- 由 border-image 属性定义。
- 允许指定一个图片作为边框。

#### 2.  CSS3 背景

##### background-image 属性

- 添加背景图片。

##### background-size 属性

- 指定背景图像的大小。

##### background-origin 属性

- 指定了背景图像的位置区域。
- content-box，padding-box，border-box区域可以放置背景图片。
- 移动图片至指定区域。

##### 多个背景图片

- 允许放置多个背景图片。

##### background-clip 属性

- 背景裁剪属性是从指定位置开始绘制。
- 裁剪指定区域外的部分。

#### 3.  CSS3 渐变（Gradients）

- 可以在多个指定颜色之间显示平稳的过渡。
- 定义了两种类型的渐变：
  - 线性渐变（Linear Gradients） - 向下/向上/向左/向右/对角方向。
  - 径向渐变（Radial Gradients） - 由它们的中心定义。

##### 线性渐变

###### 使用预定义方向

```css
background-image: linear-gradient(direction, color-stop1, color-stop2, ...);
```

###### 使用角度

```css
background-image: linear-gradient(angle, color-stop1, color-stop2);
```

###### 使用透明度（transparent）

- rgba() 函数中最后一个参数表示透明度：0表示完全透明，1表示完全不透明。

###### 重复的线性渐变

- 由 repeating-linear-gradient() 定义。

##### 径向渐变

- 至少定义两种颜色节点、指定渐变的中心、形状、大小。

###### 语法

```css
background-image: radial-gradient(shape size at position, start-color, ..., last-color);
```

###### 径向渐变 - 颜色节点均匀分布（默认情况下）

```css
#grad {
  background-image: radial-gradient(red, yellow, green);
}
```

###### 径向渐变 - 颜色节点不均匀分布

```css
#grad {
  background-image: radial-gradient(red 5%, yellow 15%, green 60%);
}
```

###### 设置形状

- 可以是 circle 或 ellipse。

###### 不同尺寸大小关键词

- **closest-side**
- **farthest-side**
- **closest-corner**
- **farthest-corner**

###### 重复的径向渐变

- 由 repeating-radial-gradient() 函数定义。

#### 4.  CSS3 文本效果

##### 文本阴影

- 由 text-shadow 属性定义。
- 指定水平阴影、垂直阴影、模糊的距离及阴影的颜色。

##### box-shadow 属性

- 适用于盒子阴影。
- 可以添加阴影颜色、阴影模糊。
- 也可以在 `::before` & `::after` 两个伪元素中添加阴影效果。
- 用于创建卡片效果。

##### Text Overflow 属性

- 指定应向用户如何显示溢出内容。

##### CSS3 的换行

- 自动换行属性允许强制文本换行 - 即使这意味着分裂它中间的一个字。

```css
p {word-wrap:break-word;}
```

##### 单词拆分换行

- 指定换行规则。

```css
/* 在 - 出换行 */
p.test1 {
    word-break: keep-all;
}

/* 在任意字符处换行 */
p.test2 {
    word-break: break-all;
}
```

#### 5.  CSS3 字体

##### @font-face 规则

- 将字体文件包含在网站中，它会自动下载给需要的用户。

##### 使用自己的字体

```css
@font-face
{
    font-family: myFirstFont;
    src: url(sansation_light.woff);
}
```

##### 使用粗体文本

- 必须添加另一个包含粗体文字的 `@font-face` 规则。

#### 6.  CSS3 2D 转换

- 对元素进行移动、缩放、转动、拉长或拉伸。

##### translate() 方法

- 根据左(X轴)和顶部(Y轴)位置给定的参数，从当前元素位置移动。

 ##### rotate() 方法

- 给定度数顺时针旋转元素。负值是允许的，这样是元素逆时针旋转。

##### scale() 方法

- 该元素增加或减少的大小，取决于宽度（X轴）和高度（Y轴）的参数。

##### skew() 方法

###### 语法

```css
transform:skew(<angle> [,<angle>]);
```

- 包含两个参数值，分别表示X轴和Y轴倾斜的角度，如果第二个参数为空，则默认为0，参数为负表示向相反方向倾斜。
  - `skewX(<angle>);`表示只在X轴(水平方向)倾斜。
  - `skewY(<angle>);`表示只在Y轴(垂直方向)倾斜。

##### matrix() 方法

- 有六个参数，包含旋转、缩放、移动、倾斜。

#### 7.  CSS3 3D 转换

- 允许使用 3D 转换来对元素进行格式化。

##### rotateX() 方法

- 围绕其在一个给定度数X轴旋转的元素。

##### rotateY() 方法

- 围绕其在一个给定度数Y轴旋转的元素。

#### 8.  CSS3 过渡

- 指定要添加效果的 CSS 属性。
- 指定效果持续的时间。

- 若未指定期限，则 transition 无效果，因为默认值为0。

##### 多项改变

- 添加多个样式的变换效果，添加的属性由逗号分隔。

#### 9.  CSS3 动画

##### @keyframes 规则

- 规则是创建动画。
- 指定一个 CSS 样式和动画将逐步从目前的样式更改为新的样式。

##### 动画

- 由 @keyframes 创建动画后，绑定至一个选择器，否则动画不会生效。
  - 规定动画名称。
  - 规定动画时长。

#### 10.  CSS3 多列

- 可以将文本内容设计成像报纸一样的多列布局

##### 创建多列

- `column-count` 属性指定了需要分割的列数。

##### 多列中间隙

- `column-gap` 属性指定了列与列间的间隙。

##### 列边框

- `column-rule-style` 属性指定了列与列间的边框样式。
- `column-rule-width` 属性指定了两列的边框厚度。
- `column-rule-color` 属性指定了两列的边框颜色。

##### 元素跨越列

- `column-span` 属性制定了元素跨越多少列。

##### 列的宽度

- `column-width` 属性指定了列的宽度。

#### 11.  CSS3 用户界面

##### 调整尺寸（Resizing）

- 指定一个元素是否应该由用户去调整大小。

##### 方框大小调整（Box Sizing）

- 定义了用户应该如何计算一个元素的总大小。
- `box-sizing: border-box;` 意为 `width` 表示整个边框的总大小；
- `box-sizing: content-box;` 意为 `width` 表示整个内容的总大小。

##### 外形修饰（outline-offset）

- 对轮廓进行偏移，并在超出边框边缘的位置绘制轮廓。
  - 轮廓不占用空间。
  - 轮廓可能是非矩形。

```css
div {
    border:2px solid black;
    outline:2px solid red;
    outline-offset:15px;
}
```

#### 12. CSS3 图片

##### 圆角图片

###### 圆角图片

```css
img {border-radius: 8px;}
```

###### 椭圆角图片

```css
img {border-radius: 50%;}
```

##### 缩略图

- 使用 border 属性来创建缩略图。

##### 响应式图片

- 自动适配各种尺寸的屏幕。

```css
img {    
    max-width: 100%;    
    height: auto;
}
```

##### 图片文本

- 通过定位，父类设置为 `relative` ，子类设置为 `absolute` 。通过相对于父类的偏移使文本显示在图片上。

##### 卡片式图片

- 通过添加 `box-shadow` ，`background-color` 等属性，达到效果。

##### 图片滤镜

- `filter` 属性为元素添加可视效果。

#### 13.  CSS3 按钮

##### 按钮颜色

- `background-color` 设置按钮颜色。

##### 按钮大小

- `font-size` 设置按钮大小。

##### 圆角按钮

- `border-radius` 设置圆角按钮。

##### 边框颜色

- `border` 设置按钮边框颜色。

##### 悬停按钮

- `:hover` 修改鼠标悬停在按钮上的样式。

##### 按钮阴影

- `box-shadow` 属性来为按钮添加阴影。

##### 禁用按钮

- `opacity` 属性为按钮添加透明度。
- `cursor` 属性设置为 `not-allowed` 来设置一个禁用的图片。

##### 按钮宽度

- 默认由按钮上的文本内容决定。
- 设置固定宽度用像素（px）；设置响应式按钮用百分比。

##### 按钮组

- 移除外边距并添加 `float:left` 来设置按钮组。
- 使用 `border` 属性来设置带边框的按钮组。

##### 按钮动画

​	[实例](https://www.runoob.com/try/try.php?filename=trycss_buttons_animate1)

#### 14.  CSS3 框大小

##### 不适用 box-sizing 属性

- **width(宽) + padding(内边距) + border(边框) = 元素实际宽度**
- **height(高) + padding(内边距) + border(边框) = 元素实际高度**

##### 使用 box-sizing 属性

- 如果在元素上设置了 `box-sizing: border-box;` 则 padding(内边距) 和 border(边框) 也包含在 width 和 height 中。

#### 15.  CSS3 弹性盒子（Flex Box）

##### 内容

- 由弹性容器（Flex container）和弹性子元素（Flex item）组成。
- 通过设置 `display` 属性为 flex 或 inline-flex ，将其定义为弹性容器。
- 包含了一个或多个弹性子元素。

##### flex-direction 

- 指定了弹性子元素在父容器中的位置。

###### 语法

```css
flex-direction: row | row-reverse | column | column-reverse
```

- row：横向从左到右排列（左对齐），默认的排列方式。
- row-reverse：反转横向排列（右对齐，从后往前排，最后一项排在最前面。
- column：纵向排列。
- column-reverse：反转纵向排列，从后往前排，最后一项排在最上面。

##### justify-content 属性

- 应用在弹性容器上，把弹性项沿着弹性容器的主轴线对齐。

###### 语法

```css
justify-content: flex-start | flex-end | center | space-between | space-around
```

- flex-start：

  弹性项目向行头紧挨着填充。这个是默认值。第一个弹性项的main-start外边距边线被放置在该行的main-start边线，而后续弹性项依次平齐摆放。

- flex-end：

  弹性项目向行尾紧挨着填充。第一个弹性项的main-end外边距边线被放置在该行的main-end边线，而后续弹性项依次平齐摆放。

- center：

  弹性项目居中紧挨着填充。（如果剩余的自由空间是负的，则弹性项目将在两个方向上同时溢出）。

- space-between：

  弹性项目平均分布在该行上。如果剩余空间为负或者只有一个弹性项，则该值等同于flex-start。否则，第1个弹性项的外边距和行的main-start边线对齐，而最后1个弹性项的外边距和行的main-end边线对齐，然后剩余的弹性项分布在该行上，相邻项目的间隔相等。

- space-around：

  弹性项目平均分布在该行上，两边留有一半的间隔空间。如果剩余空间为负或者只有一个弹性项，则该值等同于center。否则，弹性项目沿该行分布，且彼此间隔相等（比如是20px），同时首尾两边和弹性容器之间留有一半的间隔（1/2*20px=10px）。

##### align-items 属性

- 设置或检索弹性盒子元素在侧轴（纵轴）方向上的对齐方式。

###### 语法

```css
align-items: flex-start | flex-end | center | baseline | stretch
```

- flex-start：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴起始边界。
- flex-end：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴结束边界。
- center：弹性盒子元素在该行的侧轴（纵轴）上居中放置。（如果该行的尺寸小于弹性盒子元素的尺寸，则会向两个方向溢出相同的长度）。
- baseline：如弹性盒子元素的行内轴与侧轴为同一条，则该值与'flex-start'等效。其它情况下，该值将参与基线对齐。
- stretch：如果指定侧轴大小的属性值为'auto'，则其值会使项目的边距盒的尺寸尽可能接近所在行的尺寸，但同时会遵照'min/max-width/height'属性的限制。

##### flex-wrap 属性

- 用于指定弹性盒子的子元素换行方式。

###### 语法

```css
flex-wrap: nowrap|wrap|wrap-reverse|initial|inherit;
```

- **nowrap** - 默认， 弹性容器为单行。该情况下弹性子项可能会溢出容器。
- **wrap** - 弹性容器为多行。该情况下弹性子项溢出的部分会被放置到新行，子项内部会发生断行
- **wrap-reverse** -反转 wrap 排列。

##### align-content 属性

- 用于修改 `flex-wrap` 属性的行为。类似于 `align-items`, 但它不是设置弹性子元素的对齐，而是设置各个行的对齐。

###### 语法

```css
align-content: flex-start | flex-end | center | space-between | space-around | stretch
```

- `stretch` - 默认。各行将会伸展以占用剩余的空间。
- `flex-start` - 各行向弹性盒容器的起始位置堆叠。
- `flex-end` - 各行向弹性盒容器的结束位置堆叠。
- `center` -各行向弹性盒容器的中间位置堆叠。
- `space-between` -各行在弹性盒容器中平均分布。
- `space-around` - 各行在弹性盒容器中平均分布，两端保留子元素与子元素之间间距大小的一半。

##### 弹性子元素的属性

###### 排序语法

```css
order: 
```

- `<integer>`：用整数值来定义排列顺序，数值小的排在前面。可以为负值。

##### 对齐

- 设置"margin"值为"auto"值，自动获取弹性容器中剩余的空间。
- 设置垂直方向margin值为"auto"，可以使弹性子元素在弹性容器的两上轴方向都完全居中。

##### align-self

- 用于设置弹性元素自身在侧轴（纵轴）方向上的对齐方式。

###### 语法

```css
align-self: auto | flex-start | flex-end | center | baseline | stretch
```

- auto：如果'align-self'的值为'auto'，则其计算值为元素的父元素的'align-items'值，如果其没有父元素，则计算值为'stretch'。
- flex-start：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴起始边界。
- flex-end：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴结束边界。
- center：弹性盒子元素在该行的侧轴（纵轴）上居中放置。（如果该行的尺寸小于弹性盒子元素的尺寸，则会向两个方向溢出相同的长度）。
- baseline：如弹性盒子元素的行内轴与侧轴为同一条，则该值与'flex-start'等效。其它情况下，该值将参与基线对齐。
- stretch：如果指定侧轴大小的属性值为'auto'，则其值会使项目的边距盒的尺寸尽可能接近所在行的尺寸，但同时会遵照'min/max-width/height'属性的限制。

##### flex 简写属性

- 用于指定弹性子元素如何分配空间。
- [ flex-grow ]：定义弹性盒子元素的扩展比率。
- [ flex-shrink ]：定义弹性盒子元素的收缩比率。
- [ flex-basis ]：定义弹性盒子元素的默认基准值。

###### 语法

```css
flex: flex-grow flex-shrink flex-basis
/* 或者使用关键字 */
flex: auto | initial | none | inherit   
```

按顺序，关键字对应的简写值：

- auto: 计算值为 1 1 auto
- initial: 计算值为 0 1 auto
- none：计算值为 0 0 auto
- inherit：从父元素继承

#### 16.  多媒体查询

##### 多媒体查询语法

- 由多种媒体组成，可以包含一个或多个表达式，表达式根据条件是否成立返回 true 或 false。

```css
@media not|only mediatype and (expressions) {
    CSS 代码...;
}
```

- **not:** not是用来排除掉某些特定的设备的，比如 @media not print（非打印设备）。
- **only:** 用来定某种特别的媒体类型。对于支持Media Queries的移动设备来说，如果存在only关键字，移动设备的Web浏览器会忽略only关键字并直接根据后面的表达式应用样式文件。对于不支持Media Queries的设备但能够读取Media Type类型的Web浏览器，遇到only关键字时会忽略这个样式文件。
- **all:** 所有设备，这个应该经常看到。

##### 不同的媒体上使用不同的样式文件

```css
<link rel="stylesheet" media="mediatype and|not|only (expressions)" href="print.css">
```

#### 17. CSS 网格布局

##### 网格元素

- 由一个父元素及一个或多个子元素组成。

##### display 属性

- 将 display 属性设置为 grid 或 inline-grid 后，它就变成了一个网格容器，这个元素的所有直系子元素将成为网格元素。

##### 网格轨道

- 通过 **grid-template-columns** 和 **grid-template-rows** 属性来定义网格中的行和列。

- 这些属性定义了网格的轨道，一个网格轨道就是网格中任意两条线之间的空间。

###### fr 单位

- 轨道可以使用任何长度单位进行定义。

- 网格引入了 **fr** 单位来帮助我们创建灵活的网格轨道。一个 fr 单位代表网格容器中可用空间的一等份。

###### 网格单元

- 一个网格单元是在一个网格元素中最小的单位， 从概念上来讲其实它和表格的一个单元格很像。
- 一旦一个网格元素被定义在一个父级元素当中，那么他的子级元素将会排列在每个事先定义好的网格单元中。

###### 网格区域

- 网格元素可以向行或着列的方向扩展一个或多个单元，并且会创建一个网格区域。网格区域的形状应该是一个矩形 - 也就是说你不可能创建出一个类似于"L"形的网格区域。

##### 网格列

- 网格元素的垂直线方向称为列（Column）。

##### 网格行

- 网格元素的水平线方向称为行（Row）。

##### 网格间隔

- 两个网格单元之间的网格横向间距或网格纵向间距。
- 使用以下属性来调整间隙大小：
  - grid-column-gap
  - grid-row-gap
  - grid-gap

##### 网格线

- 列与列，行与行之间的交接处就是网格线。

- Grid 会为我们创建编号的网格线来让我们来定位每一个网格元素。

#### 18.  CSS 网格容器

- 将 **display** 属性设置为 **grid** 或 **inline-grid**。
- 网格容器内放置着由列和行内组成的网格元素。

##### grid-template-columns 属性

- 定义了网格布局中的列的数量，它也可以设置每个列的宽度。
- 属性值是一个以空格分隔的列表，其中每个值定义相对应列的宽度。

##### grid-template-rows 属性

- 设置每一行的高度
- 属性值是一个以空格分隔的列表，其中每个值定义相对应行的高度。

##### justify-content 属性

- 用于对齐容器内的网格，设置如何分配顺着弹性容器主轴(或者网格行轴) 的元素之间及其周围的空间。
- 网格的总宽度必须小于容器的宽度才能使 justify-content 属性生效。

##### align-content 属性

- 用于设置垂直方向上的网格元素在容器中的对齐方式。
- 网格元素的总高度必须小于容器的高度才能使 align-content 属性生效。

#### 19.  CSS 网格元素

- 包含了一个或多个网格元素。
- 默认情况下，网格容器的每一列和每一行都有一个网格元素，也可以设置网格元素跨越多个列或行，行和列为行号。

##### grid-column 属性

- 定义了网格元素列的开始和结束位置。
- `grid-column` 是 `grid-column-start` 和 `grid-column-end` 属性的简写属性。

##### gird-row 属性

- 定义了网格元素行开始和结束的地方。
- `grid-row` 是 `grid-row-start` 和 `grid-row-end` 属性的简写属性。

##### grid-area 属性

- `grid-area` 属性是 `grid-row-start` ， `grid-column-start` ， `grid-row-end` 以及 `grid-column-end` 属性的简写。

##### 网格元素命名

- grid-area 属性可以对网格元素进行命名。

- 命名的网格元素可以通过容器的 grid-template-areas 属性来引用。

  ```css
  .item1 {
    grid-area: myArea;
  }
  .grid-container {
    /* 该示例表示，表格模板为一行有五个元素，且第一行有五个命名元素，后续行列数相同，元素依次填入。 */
    grid-template-areas: 'myArea myArea myArea . .';
  }
  ```

  - 每行由单引号内 **' '** 定义，以空格分隔。
  - 第一行按照模板定义填写，后续行按照模板依次填入剩余元素。

  - **.** 号表示没有名称的网格项。

##### 网格元素的顺序

- 网格布局允许我们将网格元素放置在我们喜欢的任何地方。

### CSS 响应式设计

#### 1.  Viewport

- 用户的可视区域。

##### 设置 Viewport

```css
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

#### 2. 网络视图

##### 创建响应式网格视图

- 确保所有的 HTML 元素都有 **box-sizing** 属性且设置为 **border-box** 。
- 确保边距和边框包含在元素的宽度和高度间。

​	[实例](https://www.runoob.com/try/try.php?filename=tryresponsive_styles)

#### 3.  媒体查询

##### 添加断点

```css
@media only screen and (max-width: 768px) {
    /* For mobile phones: */
    [class*="col-"] {
        width: 100%;
    }
}
```

##### 方向：横屏/竖屏

###### 语法

```css
orientation：portrait | landscape
```

- **portrait**：指定输出设备中的页面可见区域高度大于或等于宽度。
- **landscape**：除 portrait 值情况外，都是 landscape 。

#### 4.  图片

##### width 属性

- 如果 width 属性设置为100%，图片会根据上下范围实现响应式功能。

##### max-width 属性

- 如果 max-width 属性设置为100%，图片永远不会大于其原始大小。

##### 网页中添加图片

```css
img {
    width: 100%;    height: auto;
}
```

##### 背景图片

- `background-size` 属性设置为 `contain`，背景图片将按比例自适应内容区域，图片比例保持不变。
- `background-size` 属性设置为 `100% 100%` ，背景图片将延展覆盖整个区域。
- `background-size` 属性设置为 `cover` ，则会把背景图像扩展至足够大，以使背景图像完全覆盖背景区域。注意该属性保持了图片的比例因此 背景图像的某些部分无法显示在背景定位区域中。

##### 不同设备显示不同图片

- 使用媒体查询

```css
/* For width 400px and larger: */
@media only screen and (min-width: 400px) {
    body {
        background-image: url('img_flowers.jpg');
    }
}
```

#### 5.  视频（Video）

##### width 属性

- 如果 width 属性设置为 100%，视频播放器会根据屏幕大小自动调整比例。

##### max-width 属性

- 如果 max-width 属性设置为 100%, 视频播放器会根据屏幕自动调整比例，但不会超过其原始大小。

##### 在网页中添加视频

```css
video {
    width: 100%;    height: auto;
}
```

#### 6.  框架

​	 [Bootstrap 教材](https://www.runoob.com/bootstrap/bootstrap-tutorial.html)

## 第三部分 JavaScript



