# HTML/CSS/JavaScript 学习笔记

## 第一部分  HTML

### HTML 教程

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



### HTML5 教程

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

### JavaScript 教程

#### 1.  JavaScript 用法

- 位于`<script>` 和 `</script>` 之间。

- 可以在`<head>` 或 `<body>` 内。

- 也可以外部引用脚本：

  ```css
  <script src="myScript.js"></script>
  ```

#### 2.  Chrome 浏览器中执行 JavaScript

##### 1.  Console 窗口调试 JavaScript 代码

##### 2.  Chrome snippets 小脚本

#### 3.  JavaScript 输出

##### 使用 window.alert()

- 弹出警告框来显示数据。

##### 操作 HTML 元素

- 使用 `document.getElementById(*id*)` 方法获取元素。
- 使用 `innerHTML` 来获取或插入元素内容。

##### 写到 HTML 文档

- `document.write()` 可以直接写在 HTML 文档中。

##### 写到控制台

- 使用 `console.log()` 显示 JavaScript 的值。

#### 4.  JavaScript 语法

##### JavaScript 字面量

###### 数字（Number）字面量

- 可以是整数或者是小数，或者是科学技术（e）。

###### 字符串（String）字面量

- 可以使用单引号或双引号。

###### 表达式字面量

- 用于计算。

###### 数组（Array）字面量

- 方括号 `[]` 定义一个数组。

###### 对象（Object）字面量

- 大括号 `{}` ，内部存放键值对。

###### 函数（Function）字面量

- 定义一个函数

  ```javascript
  function myFunction(a, b) { return a * b;}
  ```

##### JavaScript 变量

- 用于存储数据值，用 `let` 定义。

##### JavaScript 操作符

- 使用 **算数运算符** 来计算值。

##### JavaScript 语句

- 用分号分隔。

##### JavaScript 关键字

- 保留一些关键字为自己使用。

##### JavaScript 注释

- 双斜杠 `//` 后面被忽略。

##### JavaScript 数据类型

- 数字、字符串、数组、对象。

##### JavaScript 函数

- 可重复引用。

##### JavaScript 字母大小写

- 大小写敏感。

##### JavaScript 字符集

- 使用 Unicode 字符集。

#### 5.  JavaScript 语句

##### 对代码行进行折行

- 使用 `\` 。

#### 6.  JavaScript 注释

- 单行 `//`
- 多行 `/**/`

#### 7.  JavaScript 变量

- 用于存储信息的”容器“。

##### 一条语句，多个变量

- 以 var 开头，使用逗号分隔。

##### Value = undefined

- 未使用值得变量为 undefined。

##### 重新声明变量

- 不会丢失原来的值。

##### 使用 let 和 const

- let - 仅在声明得代码块内有效。
- const - 一经声明不可更改。

#### 8.  JavaScript 数据类型

- **值类型（基本类型）**：字符串（String）、数字(Number)、布尔(Boolean)、空（Null）、未定义（Undefined）、Symbol。

- **引用数据类型（对象类型）**：对象(Object)、数组(Array)、函数(Function)，还有两个特殊的对象：正则（RegExp）和日期（Date）。

##### 动态类型

- 相同的变量可用作不同得类型。

- 类型可使用 `typeof` 操作符来查看。

##### 字符串

- 存储字符的变量
- 可以是单引号或者双引号。

##### 数字

- 只有一种数字类型。可以带小数点也可以不带。

##### 布尔

- `true` 或 `false`

##### 数组

- 下标从0开始。

##### 对象

- 对象由花括号分隔。在括号内部，对象的属性以名称和值对的形式 (name : value) 来定义。属性由逗号分隔。

##### Undefined 和 Null

- Undefined 这个值表示变量不含有值。

- 可以通过将变量的值设置为 null 来清空变量。

##### 声明变量类型

- 使用 `new` 来声明其类型。

#### 9.  JavaScript 对象

- 拥有属性和方法的数据。

##### JavaScript 对象

- 在 JavaScript中，几乎所有的事物都是对象。

##### 对象定义

- 你可以使用字符来定义和创建 JavaScript 对象。

##### 对象属性

- 键值对通常写法为 **name : value** (键与值以冒号分割)。
- 键值对在 JavaScript 对象通常称为 **对象属性**。

##### 访问对象属性

```javascript
person.lastName;
// 或者
person["lastName"];
```

##### 对象方法

```javascript
// 键值对，值的类型为函数
methodName : function() {
    // 代码 
}
```

##### 访问对象方法

```javascript
objectName.methodName()
// 不加括号会返回函数的定义代码
objectName.methodName
```

#### 10.  JavaScript 函数

- 函数是由事件驱动的或者当它被调用时执行的可重复使用的代码块。

##### JavaScript 函数语法

- 函数就是包裹在花括号中的代码块，前面使用了关键词 function

```javascript
function functionname()
{
    // 执行代码
}
```

##### 调用带参数的函数

- 在调用函数时，您可以向其传递值，这些值被称为参数。
- 这些参数可以在函数中使用。
- 可以发送任意多的参数，由逗号 (,) 分隔：

```javascript
myFunction(argument1,argument2)
function myFunction(var1,var2)
{
	// 代码
}
```

##### 带有返回值的函数

- 使用 return 语句时，函数会停止执行，并返回指定的值。

###### 语法

```javascript
function myFunction()
{
  var x=5;
  return x;
}
```

##### 局部 JavaScript 变量

- 在 JavaScript 函数内部声明的变量（使用 var）是*局部*变量，所以只能在函数内部访问它。（该变量的作用域是局部的）。

- 可以在不同的函数中使用名称相同的局部变量，因为只有声明过该变量的函数才能识别出该变量。

- 只要函数运行完毕，本地变量就会被删除。

##### 全局 JavaScript 变量

- 在函数外声明的变量是全局变量，网页上的所有脚本和函数都能访问它。

##### JavaScript 变量的生存期

- 局部变量会在函数运行以后被删除。

- 全局变量会在页面关闭后被删除。

##### 向未声明的 JavaScript 变量分配值

- 把值赋给未使用 `var` 声明的变量，该变量将被自动作为 window 的一个属性。
- 未声明的变量和声明的变量都可以作为属性调用，但是声明的变量不可删除，未声明的可以删除 `delete var2;` 。

#### 11.  JavaScript 作用域

##### JavaScript 局部作用域

- 变量在函数内声明，变量为局部变量，具有局部作用域。

- 局部变量：只能在函数内部访问。

##### JavaScript 全局变量

- 变量在函数外定义，即为全局变量。
- 全局变量有 **全局作用域**: 网页中所有脚本和函数均可使用。 

#### 12.  JavaScript 事件

##### HTML 事件

- HTML 事件可以是浏览器行为，也可以是用户行为。

- 以下是 HTML 事件的实例：

  - HTML 页面完成加载

  - HTML input 字段改变时

  - HTML 按钮被点击

- 在事件触发时 JavaScript 可以执行一些代码。
- HTML 元素中可以添加事件属性，使用 JavaScript 代码来添加 HTML 元素。

```javascript
<some-HTML-element some-event='JavaScript 代码'>
```

#### 13.  JavaScript 字符串

##### 字符串长度

- 可以使用内置属性 **length** 来计算字符串的长度。

##### 特殊字符

- 字符中还需要使用字符，通过转义字符 `\` 。

##### 字符串可以是对象

- 可以使用字符创建： **var firstName = "John"**

- 可以使用 new 关键字将字符串定义为一个对象： **var firstName = new String("John")**

- 不要创建 String 对象。它会拖慢执行速度，并可能产生其他副作用。

##### [字符串属性和方法](https://www.runoob.com/jsref/jsref-obj-string.html)

#### 14.  JavaScript 模板字符串

- 一种方便的字符串语法，允许你在字符串中嵌入表达式和变量。

- 使用反引号 **``** 作为字符串的定界符分隔的字面量

##### 语法

```javascript
tagFunction`string text ${expression} string text`
```

- **string text**：将成为模板字面量的一部分的字符串文本。几乎允许所有字符，包括换行符和其他空白字符。但是，除非使用了标签函数，否则无效的转义序列将导致语法错误。
- **expression**：要插入当前位置的表达式，其值被转换为字符串或传递给 tagFunction。
- **tagFunction**：如果指定，将使用模板字符串数组和替换表达式调用它，返回值将成为模板字面量的值。

#### 15.  JavaScript 运算符

- **运算符 = 用于赋值。**
- **运算符 + 用于加值。**

#### 16.  JavaScript 比较 和 逻辑运算符

- 绝对相等尽量使用 `===` ，值和类型都相等。

#### 17.  JavaScript if...Else 语句

- 用于基于不同的条件来执行不同的动作。
- **if 语句** - 只有当指定条件为 true 时，使用该语句来执行代码
- **if...else 语句** - 当条件为 true 时执行代码，当条件为 false 时执行其他代码
- **if...else if....else 语句**- 使用该语句来选择多个代码块之一来执行
- **switch 语句** - 使用该语句来选择多个代码块之一来执行

#### 18.  JavaScript switch 语句

- 用于基于不同的条件来执行不同的动作。

```javascript
switch(n)
{
    case 1:
        执行代码块 1
        break;
    case 2:
        执行代码块 2
        break;
    default:
        与 case 1 和 case 2 不同时执行的代码
}
```

- **default** 关键字 - 用来规定匹配不存在时做的事情。

#### 19.  JavaScript 循环 

- 循环可以将代码块执行指定的次数。

##### for 循环

```javascript
for (语句 1; 语句 2; 语句 3)
{
    被执行的代码块
}
```

- **语句 1** （代码块）开始前执行
- **语句 2** 定义运行循环（代码块）的条件
- **语句 3** 在循环（代码块）已被执行之后执行

##### for/in 循环

```javascript
for (x in person)  // x 为属性名
```

##### while 循环

```javascript
while (条件)
{
    需要执行的代码
}
```

##### do/while 循环

- 该循环会在检查条件是否为真之前执行一次代码块，然后如果条件为真的话，就会重复这个循环。

```javascript
do
{
    需要执行的代码
}
while (条件);
```

#### 20.  JavaScript break 和 continue 语句

- **break** 语句用于跳出循环。

- **continue** 用于跳过循环中的一个迭代。

##### break 语句

- 跳出循环后，会继续执行该循环之后的代码（如果有的话）。

##### continue 语句

- 中断当前的循环中的迭代，然后继续循环下一个迭代。

##### JavaScript 标签

- 用于标注其他由大括号分界的程序体。

```javascript
label:
statements
```

#### 21.  JavaScript typeof, null, 和 undefined

##### typeof 操作符

- 可以使用 typeof 操作符来检测变量的数据类型。

##### null

- 在 JavaScript 中 **null** 表示 "什么都没有"。

- **null** 是一个只有一个值的特殊类型。表示一个空对象引用。

##### undefined

- 在 JavaScript 中, **undefined** 是一个没有设置值的变量。
- **typeof** 一个没有值的变量会返回 **undefined**。

##### undefined 和 null 的区别

- **null** 是值。
- **undefined** 是对象。

#### 22.  JavaScript 类型转换

##### constructor 属性

- **constructor** 属性返回所有 JavaScript 变量的构造函数。

##### 将数字转换为字符串

- 全局方法 **String()** 可以将数字转换为字符串。
-  **toString()** 也是有同样的效果。

##### 将布尔值转换为字符串

- 全局方法 **String()** 可以将布尔值转换为字符串。

##### 将日期转换为字符串

- 全局方法 String() 可以将日期对象转换为字符串。

##### 将字符串转换为数字

- 全局方法 **Number()** 可以将字符串转换为数字。

##### 一元运算符 +

- **Operator +** 可用于将变量转换为数字：

##### 将布尔值转换为数字

- 全局方法 **Number()** 可将布尔值转换为数字。

##### 将日期转换为数字

- 全局方法 **Number()** 可将日期转换为数字。

##### 自动转换类型

- 尝试操作一个 "错误" 的数据类型时，会自动转换为 "正确" 的数据类型。
- 尝试输出一个对象或一个变量时 JavaScript 会自动调用变量的 toString() 方法。

#### 23.  JavaScript 正则表达式

##### 语法

> /正则表达式主体/修饰符(可选)

##### 使用字符串方法

- **search()** 方法用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串，并返回子串的起始位置。

- **replace()** 方法用于在字符串中用一些字符串替换另一些字符串，或替换一个与正则表达式匹配的子串。

##### 使用 RegExp 对象

- 一个预定义了属性和方法的正则表达式对象。

###### 使用 test()

- 用于检测一个字符串是否匹配某个模式。

```javascript
var patt = /e/;
patt.test("The best things in life are free!");
```

- 返回 true

###### 使用 exec()

- 用于检索字符串中的正则表达式的匹配。

```javascript
/e/.exec("The best things in life are free!");
```

- 返回 e

#### 24.  JavaScript 错误

- **try** 语句测试代码块的错误。
- **catch** 语句处理错误。
- **throw** 语句创建自定义错误。
- **finally** 语句在 try 和 catch 语句之后，无论是否有触发异常，该语句都会执行。

##### JavaScript 抛出（throw）错误

- 当错误发生时，当事情出问题时，JavaScript 引擎通常会停止，并生成一个错误消息。

- 描述这种情况的技术术语是：JavaScript 将**抛出**一个错误。

##### JavaScript try 和 catch

- **try** 语句允许我们定义在执行时进行错误测试的代码块。

- **catch** 语句允许我们定义当 try 代码块发生错误时，所执行的代码块。

- JavaScript 语句 **try** 和 **catch** 是成对出现的。

###### 语法

```javascript
try {
    ...    //异常的抛出
} catch(e) {
    ...    //异常的捕获与处理
} finally {
    ...    //结束处理
}
```

##### finally 语句

- 不论之前的 try 和 catch 中是否产生异常都会执行该代码块。

##### Throw 语句

- 允许我们创建自定义错误。

- 正确的技术术语是：创建或**抛出异常**（exception）。

#### 25.  JavaScript 声明提升

- 函数及变量的声明都将被提升到函数的最顶部。

- 变量可以在使用后声明，也就是变量可以先使用再声明。

##### JavaScript 初始化不会提升

- 只有声明的变量会提升，初始化的不会。

#### 26.  JavaScript 严格模式(use strict)

##### 严格模式声明

- 在脚本或函数的头部添加 **`"use strict"`** ；表达式来声明。

##### 严格模式的限制

- 不允许使用未声明的变量。

- 不允许删除变量或对象。

- 不允许删除函数。

- 不允许变量重名。

- 不允许使用八进制。

- 不允许使用转义字符。

- 不允许对只读属性赋值。

- 不允许对一个使用getter方法读取的属性进行赋值。

- 不允许删除一个不允许删除的属性。

- 变量名不能使用 "eval" 字符串。

- 变量名不能使用 "arguments" 字符串。

- 不允许使用以下这种语句:

  ```javascript
  "use strict";
  with (Math){x = cos(2)}; // 报错
  ```

- 在作用域 eval() 创建的变量不能被调用

- 禁止this关键字指向全局对象。

##### 保留关键字

- implements
- interface
- let
- package
- private
- protected
- public
- static
- yield

#### 27.  JavaScript 表单

- 表单验证
- 输入数字验证

#### 28.  JavaScript this 关键字

- 在方法中，this 表示该方法所属的对象。
- 如果单独使用，this 表示全局对象。
- 在函数中，this 表示全局对象。
- 在函数中，在严格模式下，this 是未定义的(undefined)。
- 在事件中，this 表示接收事件的元素。
- 类似 call() 和 apply() 方法可以将 this 引用到任何对象。

##### 显式函数绑定

- 函数也是对象，对象则有方法，apply 和 call 就是函数对象的方法。这两个方法异常强大，他们允许切换函数执行的上下文环境（context），即 this 绑定的对象。
- call - 允许使用对象1的方法，处理对象二的属性。

```javascript
var person1 = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
var person2 = {
  firstName:"John",
  lastName: "Doe",
}
person1.fullName.call(person2);  // 返回 "John Doe"
```

####  29.  JavaScript let 和 const

##### 全局变量

- 在函数外声明的变量作用域是全局的。

##### 局部变量

- 在函数内声明的变量作用域是局部的（函数内）。

##### JavaScript 块级作用域(Block Scope)

- var 关键字声明的变量不具备块级作用域的特性，它在 **{}** 外依然能被访问到。
- let 声明的变量只在 let 命令所在的代码块 **{}** 内有效，在 **{}** 之外不能访问。

##### 重新定义变量

- 块中使用 let 声明变量。

- 循环使用 let 声明变量。

##### HTML 代码中使用全局变量

- 使用 **var** 关键字声明的全局作用域变量属于 window 对象。
- 使用 **let** 关键字声明的全局作用域变量不属于 window 对象。

##### 重置变量

- 使用 **var** 关键字声明的变量在任何地方都可以修改。
- 在相同的作用域或块级作用域中，不能使用 **let** 关键字来重置 **var** 关键字声明的变量。
- 在相同的作用域或块级作用域中，不能使用 **let** 关键字来重置 **let** 关键字声明的变量。
- 在相同的作用域或块级作用域中，不能使用 **var** 关键字来重置 **let** 关键字声明的变量。
- **let** 关键字在不同作用域，或不同块级作用域中是可以重新声明赋值的。

##### 变量提升

- var 关键字定义的变量可以在使用后声明，也就是变量可以先使用再声明。
- let 关键字定义的变量则不可以在使用后声明，也就是变量需要先声明再使用。

##### const 关键字

- 用于声明一个或多个常量，声明时必须进行初始化，且初始化后值不可再修改。
- 本质: const 定义的变量并非常量，并非不可变，它定义了一个常量引用一个值。使用 const 定义的对象或者数组，其实是可变的。

##### 重置变量

- 在相同的作用域或块级作用域中，不能使用 **const** 关键字来重置 **var** 和 **let**关键字声明的变量。
- 在相同的作用域或块级作用域中，不能使用 **const** 关键字来重置 **const** 关键字声明的变量。
- **const** 关键字在不同作用域，或不同块级作用域中是可以重新声明赋值的。

##### 变量提升

- const 关键字定义的变量则不可以在使用后声明，也就是变量需要先声明再使用。

#### 30.  **JavaScript** **JSON**

- JSON 是用于存储和传输数据的格式。
- JSON 通常用于服务端向网页传递数据 。

##### JSON 语法规则

- 数据为 键/值 对。
- 数据由逗号分隔。
- 大括号保存对象
- 方括号保存数组

##### JSON 数据 - 一个名称对应一个值

- JSON 数据格式为 键/值 对，就像 JavaScript 对象属性。

- 键/值对包括字段名称（在双引号中），后面一个冒号，然后是值：

##### JSON 对象

- JSON 对象保存在大括号内。

##### JSON 数组

- JSON 数组保存在中括号内。

##### JSON 字符串转换为 JavaScript 对象

- 使用 JavaScript 内置函数 JSON.parse() 将字符串转换为 JavaScript 对象:

#### 31.  javascript:void(0) 含义

- 表示没有任何效果

##### 语法

```javascript
javascript:void(func())
```

##### href="#"与href="javascript:void(0)"的区别

- **#** 包含了一个位置信息，默认的锚是**#top** 也就是网页的上端。

- **javascript:void(0)** 仅仅表示一个死链接。

#### 32.  JavaScript 异步编程

##### 回调函数

​	回调函数就是一个函数，它是在我们启动一个异步任务的时候就告诉它：等你完成了这个任务之后要干什么。这样一来主线程几乎不用关心异步任务的状态了，他自己会善始善终。

#### 33.  JavaScript Promise

##### 构造 Promise

```
new Promise(function (resolve, reject) {
    // 要做的事情...
});
```

##### Promise 的构造函数

- 用于创建 Promise 对象的内置构造函数。
- 接受一个函数作为参数，该函数是同步的并且会被立即执行，所以我们称之为起始函数。起始函数包含两个参数 resolve 和 reject，分别表示 Promise 成功和失败的状态。
- 起始函数执行成功时，它应该调用 resolve 函数并传递成功的结果。当起始函数执行失败时，它应该调用 reject 函数并传递失败的原因。
- 返回一个 Promise 对象，该对象具有以下几个方法：
  - then：用于处理 Promise 成功状态的回调函数。
  - catch：用于处理 Promise 失败状态的回调函数。
  - finally：无论 Promise 是成功还是失败，都会执行的回调函数。

- resolve() 中可以放置一个参数用于向下一个 then 传递一个值，then 中的函数也可以返回一个值传递给 then。但是，如果 then 中返回的是一个 Promise 对象，那么下一个 then 将相当于对这个返回的 Promise 进行操作。
- reject() 参数中一般会传递一个异常给之后的 catch 函数用于处理异常。
- resolve 和 reject 的作用域只有起始函数，不包括 then 以及其他序列；
- resolve 和 reject 并不能够使起始函数停止运行，别忘了 return。

### JS 函数

#### 1.  **JavaScript** **函数定义**

##### 函数声明

```javascript
function functionName(parameters) {
  // 执行的代码
}
```

##### 函数表达式

- 可以通过一个表达式定义。

```javascript
var x = function (a, b) {return a * b};
```

- 以上函数实际上是一个 **匿名函数** (函数没有名称)。
- 函数存储在变量中，不需要函数名称，通常通过变量名来调用。

##### Function() 构造函数

- 同样可以通过内置的 JavaScript 函数构造器（Function()）定义。

```javascript
var myFunction = new Function("a", "b", "return a * b");
var x = myFunction(4, 3);
```

##### 函数提升（Hoisting）

- 提升（Hoisting）是 JavaScript 默认将当前作用域提升到前面去的行为。
- 提升（Hoisting）应用在变量的声明与函数的声明。

##### 自调用函数

- 函数表达式可以 "自调用"。
- 自调用表达式会自动调用。
- 如果表达式后面紧跟 () ，则会自动调用。

- 不能自调用声明的函数。

```javascript
(function () {
    var x = "Hello!!";      // 我将调用自己
})();
```

##### 函数可作为一个值使用

```javascript
function myFunction(a, b) {return a * b;}
var x = myFunction(4, 3);
```

##### 函数是对象

- 函数有 **属性** 和 **方法**。

##### 箭头函数

- 箭头函数表达式的语法比普通函数表达式更简洁。

```javascript
(参数1, 参数2, …, 参数N) => { 函数声明 }

(参数1, 参数2, …, 参数N) => 表达式(单一)
// 相当于：(参数1, 参数2, …, 参数N) =>{ return 表达式; }
```

- 有的箭头函数都没有自己的 **this**。 不适合定义一个 **对象的方法**。
- 当我们使用箭头函数的时候，箭头函数会默认帮我们绑定外层 this 的值，所以在箭头函数中 this 的值和外层的 this 是一样的。
- 箭头函数是不能提升的，所以需要在使用之前定义。
- 使用 **const** 比使用 **var** 更安全，因为函数表达式始终是一个常量。
- 如果函数部分只是一个语句，则可以省略 return 关键字和大括号 {}，这样做是一个比较好的习惯。

#### 2.  JavaScript 函数参数

- 对参数的值没有进行任何的检查。

##### 函数显式参数(Parameters)与隐式参数(Arguments)

- 函数显式参数在函数定义时列出。
- 函数隐式参数在函数调用时传递给函数真正的值。

##### 参数规则

- JavaScript 函数定义显式参数时没有指定数据类型。
- JavaScript 函数对隐式参数没有进行类型检测。
- JavaScript 函数对隐式参数的个数没有进行检测。

##### 默认参数

- 如果函数在调用时未提供隐式参数，参数会默认设置为： **undefined**

- 有时这是可以接受的，但是建议最好为参数设置一个默认值。

##### ES6 函数可以自带参数

ES6 支持函数带有默认参数，就判断 undefined 和 || 的操作：

```javascript
function myFunction(x, y = 10) {    
    // y is 10 if not passed or undefined    
    return x + y; 
}  
myFunction(0, 2) // 输出 2 
myFunction(5); // 输出 15, y 参数的默认值
```

##### arguments 对象

- 有个内置的对象 arguments 对象。

- arguments 对象包含了函数调用的参数数组。

##### 通过值传递参数

- 在函数中调用的参数是函数的隐式参数。
- 隐式参数通过值来传递：函数仅仅只是获取值。
- 如果函数修改参数的值，不会修改显式参数的初始值（在函数外定义）。
- 隐式参数的改变在函数外是不可见的。

##### 通过对象传递参数

- 可以引用对象的值。
- 修改对象属性可作用于函数外部（全局变量）。
- 修改对象属性在函数外是可见的。

#### 3.  JavaScript 函数调用

##### ***this*** 关键字

- this指向函数执行时的当前对象。

##### 作为一个函数调用

###### 全局对象

- 当函数没有被自身的对象调用时 **this** 的值就会变成全局对象。

- 在 web 浏览器中全局对象是浏览器窗口（window 对象）。

##### 函数作为方法调用

- 可以将函数定义为对象的方法。

##### 使用构造函数调用函数

- 如果函数调用前使用了 **new** 关键字, 则是调用了构造函数。

##### 作为函数方法调用函数

- 函数是对象。有它的属性和方法。

- **call()** 和 **apply()** 是预定义的函数方法。 两个方法可用于调用函数，两个方法的第一个参数必须是对象本身。

  - 两个方法都使用了对象本身作为第一个参数。 两者的区别在于第二个参数： apply传入的是一个参数数组，也就是将多个参数组合成为一个数组传入，而call则作为call的参数传入（从第二个参数开始）。

  - 在 JavaScript 严格模式(strict mode)下，在调用函数时第一个参数会成为 **this** 的值， 即使该参数不是一个对象。

  - 在 JavaScript 非严格模式(non-strict mode)下，如果第一个参数的值是 null 或 undefined，它将使用全局对象替代。

#### 4.  JavaScript 闭包

​	闭包是一种保护私有变量的机制，在函数执行时形成私有的作用域，保护里面的私有变量不受外界干扰。

​	直观的说就是形成一个不销毁的栈环境。

### JS 类

#### 1.  JavaScript 类(class)

##### 类是用于创建对象的模板。

- 使用 class 关键字来创建一个类，类体在一对大括号 **{}** 中，我们可以在大括号 **{}** 中定义类成员的位置，如方法或构造函数。

- 每个类中包含了一个特殊的方法 **constructor()**，它是类的构造函数，这种方法用于创建和初始化一个由 **class** 创建的对象。
  - 构造方法名为 constructor()。
  - 构造方法在创建新对象时会自动执行。
  - 构造方法用于初始化对象属性。
  - 如果不定义构造方法，JavaScript 会自动添加一个空的构造方法。

###### 语法

```javascript
class ClassName {
  constructor() { ... }
}
```

##### 使用类

- 定义好类后，我们就可以使用 **new** 关键字来创建对象。

##### 类表达式

- 类表达式是定义类的另一种方法。类表达式可以命名或不命名。命名类表达式的名称是该类体的局部名称。

##### 类的方法

- 我们使用关键字 **class** 创建一个类，可以添加一个 **constructor()** 方法，然后添加任意数量的方法。

#### 2.  JavaScript 类继承

- 使用 extends 关键字。
- **super()** 方法用于调用父类的构造函数。

##### 使用原型链继承

```javascript
// 建立原型链，让 Dog 继承 Animal
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;
```

##### 使用 ES6 类继承

- ES6 引入了 class 关键字，使得定义类和继承更加清晰，extends 关键字用于建立继承关系，super 关键字用于在子类构造函数中调用父类的构造函数。

##### getter 和 setter

- 类中我们可以使用 getter 和 setter 来获取和设置值，getter 和 setter 都需要在严格模式下执行。

- getter 和 setter 可以使得我们对属性的操作变的很灵活。

- 类中添加 getter 和 setter 使用的是 get 和 set 关键字。
  - **`get`** 语法将对象属性绑定到查询该属性时将被调用的函数。
  - **`set`** 语法将对象属性绑定到要调用的函数。

```javascript
class Runoob {
  constructor(name) {
    this._sitename = name;
  }
  set sitename(x) {
    this._sitename = x;
  }
  get sitename() {
    return this._sitename;
  }
}
 
let noob = new Runoob("菜鸟教程");
noob.sitename = "RUNOOB";
document.getElementById("demo").innerHTML = noob.sitename;
```

##### 提升

- 函数声明和类声明之间的一个重要区别在于, 函数声明会提升，类声明不会。

#### 3.  JavaScript 静态方法

- 静态方法是使用 static 关键字修饰的方法，又叫类方法，属于类的，但不属于对象，在实例化对象之前可以通过 **类名.方法名** 调用静态方法。

- 静态方法不能在对象上调用，只能在类中调用。

### JavaScript HTML DOM

#### 1.  DOM 简介

- 通过 HTML DOM，可访问 JavaScript HTML 文档的所有元素。

#### 2.  DOM HTML 

##### 改变 HTML 输出流

- JavaScript 能够创建动态的 HTML 内容：

##### 改变 HTML 内容

- 修改 HTML 内容的最简单的方法是使用 innerHTML 属性。

##### 改变 HTML 属性

```javascript
document.getElementById(id).attribute=新属性值
```

#### 3.  DOM CSS

##### 改变 HTML 样式

```javascript
document.getElementById(id).style.property=新样式
```

##### 使用事件

- 元素被点击。
- 页面加载完成。
- 输入框被修改。

#### 4.  DOM 事件

##### 对事件做出反应

- 可以在事件发生时执行 JavaScript，比如当用户在 HTML 元素上点击时。

```javascript
onclick=JavaScript
```

##### HTML 事件属性

- 需向 HTML 元素分配 事件，您可以使用事件属性。

```javascript
<button onclick="displayDate()">点这里</button>
```

##### 使用 HTML DOM 来分配事件

- 允许使用 JavaScript 来向 HTML 元素分配事件：

```javascript
document.getElementById("myBtn").onclick=function(){displayDate()};
```

##### onload 和 onunload 事件

- onload 和 onunload 事件会在用户进入或离开页面时被触发。

- onload 事件可用于检测访问者的浏览器类型和浏览器版本，并基于这些信息来加载网页的正确版本。

- onload 和 onunload 事件可用于处理 cookie。

##### onchange 事件

- 常结合对输入字段的验证来使用。

##### onmouseover 和 onmouseout 事件

- onmouseover 和 onmouseout 事件可用于在用户的鼠标移至 HTML 元素上方或移出元素时触发函数。

##### onmousedown、onmouseup 以及 onclick 事件

- onmousedown, onmouseup 以及 onclick 构成了鼠标点击事件的所有部分。
- 首先当点击鼠标按钮时，会触发 onmousedown 事件。
- 当释放鼠标按钮时，会触发 onmouseup 事件。
- 最后，当完成鼠标点击时，会触发 onclick 事件。

#### 5.  DOM EventListener

##### addEventListener() 方法

###### 语法

```javascript
element.addEventListener(event, function, useCapture);
```

- 用于向指定元素添加事件句柄。
- 添加的事件句柄不会覆盖已存在的事件句柄。
- 可以向一个元素添加多个事件句柄。
- 可以向同个元素添加多个同类型的事件句柄，如：两个 "click" 事件。
- 可以向任何 DOM 对象添加事件监听，不仅仅是 HTML 元素。如： window 对象。
- 可以更简单的控制事件（冒泡与捕获）。
- 当使用 addEventListener() 方法时, JavaScript 从 HTML 标记中分离开来，可读性更强， 在没有控制HTML标记时也可以添加事件监听。
- 可以使用 removeEventListener() 方法来移除事件的监听。

##### 向元素添加事件句柄

```javascript
element.addEventListener("click", function(){ alert("Hello World!"); });
```

##### 向同一个元素中添加多个事件句柄

```javascript
element.addEventListener("click",myFunction);element.addEventListener("click", mySecondFunction);
```

##### 向 Window 对象添加事件句柄

```javascript
window.addEventListener("resize", function(){ document.getElementById("demo").innerHTML = sometext;});
```

##### 传递参数

- 当传递参数值时，使用"匿名函数"调用带参数的函数：

```javascript
element.addEventListener("click", function(){myFunction(p1, p2); });
```

##### 事件冒泡或事件捕获

- 在 *冒泡* 中，内部元素的事件会先被触发，然后再触发外部元素。

- 在 *捕获* 中，外部元素的事件会先被触发，然后才会触发内部元素的事件。

###### 语法

```javascript
addEventListener(event, function, useCapture);
```

- 默认值为 false, 即冒泡传递，当值为 true 时, 事件使用捕获传递。

##### removeEventListener() 方法

- 移除由 addEventListener() 方法添加的事件句柄：

```javascript
element.removeEventListener("mousemove", myFunction);
```

#### 6.  DOM 元素 (节点)

##### 创建新的 HTML 元素 (节点) - appendChild()

- 先创建一个元素，然后在已存在的元素中添加它。

##### 创建新的 HTML 元素 (节点) - insertBefore()

- **appendChild()** 方法，它用于添加新元素到尾部。

- **insertBefore()** 方法，将新元素添加到开始位置

##### 移除已存在的元素

- 要移除一个元素，你需要知道该元素的父元素。

##### 替换 HTML 元素 - replaceChild()

- 可以使用 replaceChild() 方法来替换 HTML DOM 中的元素。

#### 7.  DOM 集合(Collection)

##### HTMLCollection 对象

- getElementsByTagName() 方法返回 [HTMLCollection](https://www.runoob.com/jsref/dom-htmlcollection.html) 对象。

##### HTMLCollection 对象 length 属性

- HTMLCollection 对象的 length 属性定义了集合中元素的数量。

#### 8.  DOM 节点列表

- **NodeList** 对象是一个从文档中获取的节点列表 (集合) 。

- NodeList 对象类似 [HTMLCollection](https://www.runoob.com/js/js-htmldom-elements.html) 对象。

##### NodeList 对象 length 属性

- NodeList 对象 length 属性定义了节点列表中元素的数量。

##### HTMLCollection 与 NodeList 的区别

- [HTMLCollection](https://www.runoob.com/js/js-htmldom-collections.html) 是 HTML 元素的集合。NodeList 是一个文档节点的集合。
- NodeList 与 HTMLCollection 都与数组对象有点类似，可以使用索引 (0, 1, 2, 3, 4, ...) 来获取元素。
- NodeList 与 HTMLCollection 都有 length 属性。
- HTMLCollection 元素可以通过 name，id 或索引来获取。
- NodeList 只能通过索引来获取。
- 只有 NodeList 对象有包含属性节点和文本节点。

### JS 高级教程

#### 1.  JavaScript 对象

- JavaScript 中的所有事物都是对象：字符串、数值、数组、函数...

##### 创建 JavaScript 对象

- 使用 Object 定义并创建对象的实例。
- 使用函数来定义对象，然后创建新的对象实例。

###### 使用 Object

- 如果给定值是 null 或 undefined，将会创建并返回一个空对象。
- 如果传进去的是一个基本类型的值，则会构造其包装类型的对象。
- 如果传进去的是引用类型的值，仍然会返回这个值，经他们复制的变量保有和源对象相同的引用地址。
- 当以非构造函数形式被调用时，Object 的行为等同于 new Object()。

```javascript
// 以构造函数形式来调用
new Object([value])
```

###### 使用对象字面量

```javascript
var myObject = {
    key1: value1,
    key2: value2,
    // 更多键值对...
};
```

- **myObject:** 变量名，用于引用整个对象。
- **key1, key2:** 属性名称，可以是字符串或标识符。
- **value1, value2:** 属性的值，可以是任意 JavaScript 数据类型，包括数字、字符串、布尔值、函数、数组、甚至其他对象。

###### 使用对象构造器

```javascript
function person(firstname,lastname,age,eyecolor)
{
    this.firstname=firstname;
    this.lastname=lastname;
    this.age=age;
    this.eyecolor=eyecolor;
}
```

###### 创建 JavaScript 对象实例

一旦有了对象构造器，就可以创建新的对象实例，就像这样：

```
var myFather=new person("John","Doe",50,"blue");
var myMother=new person("Sally","Rally",48,"green");
```

###### 把属性添加到 JavaScript 对象

- 可以通过为对象赋值，向已有对象添加新属性：

##### 把方法添加到 JavaScript 对象

- 在构造器函数内部定义对象的方法。

##### JavaScript 类

- JavaScript 是面向对象的语言，但 JavaScript 不使用类。
- 在 JavaScript 中，不会创建类，也不会通过类来创建对象（就像在其他面向对象的语言中那样）。
- JavaScript 基于 prototype，而不是基于类的。

##### JavaScript for...in 循环

- 循环遍历对象的属性。

###### 语法

```javascript
for (variable in object)
{
    执行的代码……
}
```

##### JavaScript 的对象是可变的

- 对象是可变的，它们是通过引用来传递的。

#### 2.  JavaScript prototype

- 所有的 JavaScript 对象都会从一个 prototype（原型对象）中继承属性和方法。

##### prototype 继承

所有的 JavaScript 对象都会从一个 prototype（原型对象）中继承属性和方法：

- `Date` 对象从 `Date.prototype` 继承。
- `Array` 对象从 `Array.prototype` 继承。
- `Person` 对象从 `Person.prototype` 继承。

##### 添加属性和方法

- 使用 prototype 属性就可以给对象的构造函数添加新的属性：

#### 3.  JavaScript Number 对象

##### JavaScript 数字

- 可以使用也可以不使用小数点来书写。

##### 所有 JavaScript 数字均为 64 位

- 其中 0 到 51 存储数字（片段），52 到 62 存储指数，63 位存储符号。

##### 精度

- 整数（不使用小数点或指数计数法）最多为 15 位。
- 小数的最大位数是 17，但是浮点运算并不总是 100% 准确。

##### 八进制和十六进制

如果前缀为 0，则 JavaScript 会把数值常量解释为八进制数，如果前缀为 0 和 "x"，则解释为十六进制数。

##### 无穷大（Infinity）

- 当数字运算结果超过了所能表示的数字上限（溢出），结果为一个特殊的无穷大（infinity）值，以Infinity表示。
- 同样地，当负数的值超过了所能表示的负数范围，结果为负无穷大，在中以-Infinity表示。

##### NaN - 非数字值

- NaN 属性是代表非数字值的特殊值。该属性用于指示某个值不是数字。可以把 Number 对象设置为该值，来指示其不是数字值。

- 你可以使用 `isNaN()` 全局函数来判断一个值是否是 NaN 值。

##### 数字可以是数字或者对象

- 数字可以私有数据进行初始化，就像 x = 123;
- JavaScript 数字对象初始化数据， var y = new Number(123);

#### 4.  JavaScript 字符串（String） 对象

##### JavaScript 字符串

- 一个字符串用于存储一系列字符就像 "John Doe"。
- 一个字符串可以使用单引号或双引号。

##### 字符串（String）

- 字符串（String）使用长度属性**length**来计算字符串的长度：

##### 在字符串中查找字符串

- 使用 indexOf() 来定位字符串中某一个指定的字符首次出现的位置：

##### 内容匹配

- **match()**函数用来查找字符串中特定的字符，并且如果找到的话，则返回这个字符。

##### 替换内容

- **replace()** 方法在字符串中用某些字符替换另一些字符。

##### 字符串大小写转换

- 字符串大小写转换使用函数 **toUpperCase()** / **toLowerCase()**。

##### 字符串转为数组

- 字符串使用**split()**函数转为数组。

##### 特殊字符

- 使用反斜线（\）插入特殊符号，如：撇号,引号等其他特殊符号。

#### 5.  JavaScript Date（日期） 对象

##### 创建日期

- Date 对象用于处理日期和时间。 

##### 设置日期

- 通过使用针对日期对象的方法，我们可以很容易地对日期进行操作。

```javascript
var myDate=new Date();
myDate.setFullYear(2010,0,14);// 第二个参数为月份， 0 到 11 之间的整数值，表示从一月到十二月
```

##### 两个日期比较

- 日期对象也可用于比较两个日期。

#### 6.  JavaScript Array（数组） 对象

##### 创建一个数组

1. 常规方式：

```javascript
var myCars=new Array();
myCars[0]="Saab"; 
myCars[1]="Volvo";
myCars[2]="BMW";
```

2. 简洁方式：

```javascript
var myCars=new Array("Saab","Volvo","BMW");
```

3. 字面：

```javascript
var myCars=["Saab","Volvo","BMW"];
```

##### 访问数组

- 通过指定数组名以及索引号码，可以访问某个特定的元素。

##### 在一个数组中你可以有不同的对象

- 所有的变量都是对象。数组元素是对象。函数是对象。

- 因此，你可以在数组中有不同的变量类型。

#### 7.  JavaScript Boolean（布尔） 对象

##### 创建 Boolean 对象

- Boolean 对象代表两个值:"true" 或者 "false"

```javascript
var myBoolean=new Boolean();
```

#### 8.  JavaScript Math（算数） 对象

##### Math 对象

- Math（算数）对象的作用是：执行普通的算数任务。

- Math 对象提供多种算数值类型和函数。无需在使用这个对象之前对它进行定义。

##### 算数值

```javascript
Math.E
Math.PI
Math.SQRT2
Math.SQRT1_2
Math.LN2
Math.LN10
Math.LOG2E
Math.LOG10E
```

##### 算数方法

- 除了可被 Math 对象访问的算数值以外，还有几个函数（方法）可以使用。

#### 9.  JavaScript RegExp 对象

​	RegExp：是正则表达式（regular expression）的简写。

​	 [JavaScript RegExp 对象的参考手册](https://www.runoob.com/jsref/jsref-obj-regexp.html)

### JS 浏览器BOM

#### 1.  JavaScript Window

##### Window 对象

- 所有浏览器都支持 window 对象。它表示浏览器窗口。
- 所有 JavaScript 全局对象、函数以及变量均自动成为 window 对象的成员。
- 全局变量是 window 对象的属性。
- 全局函数是 window 对象的方法。

##### Window 尺寸

- document.body.clientHeight
- document.body.clientWidth

##### 其他 Window 方法

- window.open() - 打开新窗口
- window.close() - 关闭当前窗口
- window.moveTo() - 移动当前窗口
- window.resizeTo() - 调整当前窗口的尺寸

#### 2.  JavaScript Window Screen

##### Window Screen

- **window.screen**对象在编写时可以不使用 window 这个前缀。

一些属性：

- screen.availWidth - 可用的屏幕宽度
- screen.availHeight - 可用的屏幕高度

##### Window Screen 可用宽度

- screen.availWidth 属性返回访问者屏幕的宽度，以像素计，减去界面特性，比如窗口任务栏。

##### Window Screen 可用高度

- screen.availHeight 属性返回访问者屏幕的高度，以像素计，减去界面特性，比如窗口任务栏。

#### 3.  JavaScript Window Location

##### Window Location

- **window.location** 对象在编写时可不使用 window 这个前缀。 

一些实例:

- location.hostname 返回 web 主机的域名
- location.pathname 返回当前页面的路径和文件名
- location.port 返回 web 主机的端口 （80 或 443）
- location.protocol 返回所使用的 web 协议（http: 或 https:）

##### Window Location href

- **`location.href`** 属性返回当前页面的 URL。

##### Window Location pathname

- **`location.pathname`** 属性返回 URL 的路径名。

#### Window Location assign

- **`location.assign()`** 方法加载新的文档。

#### 4.  JavaScript Window History

##### Window History

- **window.history**对象在编写时可不使用 window 这个前缀。

一些方法：

- history.back() - 与在浏览器点击后退按钮相同
- history.forward() - 与在浏览器中点击向前按钮相同

##### Window history.back()

- history.back() - 方法加载历史列表中的前一个 URL。

##### Window history.forward()

- history.forward() - 方法加载历史列表中的下一个 URL。

#### 5.  JavaScript Window Navigator

- window.navigator 对象包含有关访问者浏览器的信息。

##### Window Navigator

- **window.navigator** 对象在编写时可不使用 window 这个前缀。

##### 警告!!!

来自 navigator 对象的信息具有误导性，不应该被用于检测浏览器版本，这是因为：

- navigator 数据可被浏览器使用者更改
- 一些浏览器对测试站点会识别错误
- 浏览器无法报告晚于浏览器发布的新操作系统

#### 6.  JavaScript 弹窗

##### 警告框

- 警告框经常用于确保用户可以得到某些信息。
- 当警告框出现后，用户需要点击确定按钮才能继续进行操作。

###### 语法

```javascript
window.alert("sometext");
```

- **window.alert()** 方法可以不带上window对象，直接使用**alert()**方法。

##### 确认框

- 确认框通常用于验证是否接受用户操作。
- 当确认框弹出时，用户可以点击 "确认" 或者 "取消" 来确定用户操作。
- 当你点击 "确认", 确认框返回 true， 如果点击 "取消", 确认框返回 false。

###### 语法

```javascript
window.confirm("sometext");
```

- **window.confirm()** 方法可以不带上window对象，直接使用**confirm()**方法。

##### 提示框

- 提示框经常用于提示用户在进入页面前输入某个值。
- 当提示框出现后，用户需要输入某个值，然后点击确认或取消按钮才能继续操纵。
- 如果用户点击确认，那么返回值为输入的值。如果用户点击取消，那么返回值为 null。

###### 语法

```javascript
window.prompt("sometext","defaultvalue");
```

- **window.prompt()** 方法可以不带上window对象，直接使用**prompt()**方法。

##### 换行

- 弹窗使用 反斜杠 + "n"(\n) 来设置换行。

#### 7.  JavaScript 计时事件

##### JavaScript 计时事件

- setInterval() - 间隔指定的毫秒数不停地执行指定的代码。
- setTimeout() - 在指定的毫秒数后执行指定代码。

##### setInterval() 方法

- setInterval() 间隔指定的毫秒数不停地执行指定的代码

###### 语法

```javascript
window.setInterval("javascript function",milliseconds);
```

##### setTimeout() 方法

###### 语法

```javascript
myVar= window.setTimeout("javascript function", milliseconds);
```

- setTimeout() 方法会返回某个值。在上面的语句中，值被储存在名为 myVar 的变量中。假如你希望取消这个 setTimeout()，你可以使用这个变量名来指定它。

- setTimeout() 的第一个参数是含有 JavaScript 语句的字符串。这个语句可能诸如 "alert('5 seconds!')"，或者对函数的调用，诸如 alertMsg。

##### 停止执行

- clearInterval() 方法用于停止 setInterval() 方法执行的函数代码。

###### 语法

```javascript
window.clearInterval(intervalVariable)
```

- **window.clearInterval()** 方法可以不使用window前缀，直接使用函数**clearInterval()**。

#### 8.  JavaScript Cookie

- 用于存储 web 页面的用户信息。

##### 使用 JavaScript 创建Cookie

- 可以使用 **document.cookie** 属性来创建 、读取、及删除 cookie。

```javascript
document.cookie="username=John Doe";
```

- 可以为 cookie 添加一个过期时间（以 UTC 或 GMT 时间）。默认情况下，cookie 在浏览器关闭时删除。

```javascript
document.cookie="username=John Doe; expires=Thu, 18 Dec 2043 12:00:00 GMT";
```

- 可以使用 path 参数告诉浏览器 cookie 的路径。默认情况下，cookie 属于当前页面。

```javascript
document.cookie="username=John Doe; expires=Thu, 18 Dec 2043 12:00:00 GMT; path=/";
```

##### 使用 JavaScript 读取 Cookie

- 可以使用以下代码来读取 cookie：

```javascript
var x = document.cookie;
```

##### 使用 JavaScript 修改 Cookie

- 修改 cookie 类似于创建 cookie：

```javascript
document.cookie="username=John Smith; expires=Thu, 18 Dec 2043 12:00:00 GMT; path=/";
```

- 旧的 cookie 将被覆盖。

##### 使用 JavaScript 删除 Cookie

- 设置 expires 参数为以前的时间即可。

##### Cookie 字符串

- document.cookie 属性看起来像一个普通的文本字符串，其实它不是。
- 在 document.cookie 中写入一个完整的 cookie 字符串, 当重新读取该 cookie 信息时，cookie 信息是以名/值对的形式展示的。
- 如果设置了新的 cookie，旧的 cookie 不会被覆盖。 新 cookie 将添加到 document.cookie 中。
