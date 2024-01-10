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



























































## 第三部分 JavaScript



