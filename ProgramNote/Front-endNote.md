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

#### HTML CSS

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

#### HTML 图像

- 图像标签(**\<img>**)

​	\<img> 是空标签，意思是说，它只包含属性，并且没有闭合标签。

- 图像源属性(**Src**)

​	src 指 "source"。源属性的值是图像的 URL 地址。

- 图像Alt属性(**Alt**)

​	alt 属性用来为图像定义一串预备的可替换的文本。在浏览器无法载入图像时，替换文本属性告诉读者她们失去的信息。

- 图像高度与宽度(**width & height**)

​	height（高度） 与 width（宽度）属性用于设置图像的高度与宽度。默认单位为像素(px)。

#### HTML 表格

- HTML 表格由 **\<table>** 标签来定义。
- **\<thead > 用于定义表格的标题部分:** 在 \<thead > 中，使用 \<th > 元素定义列的标题，以上实例中列标题分别为"列标题1"，"列标题2"和"列标题3"。
- **\<tbody > 用于定义表格的主体部分:** 在 \<tbody > 中，使用 \<tr > 元素定义行，并在每行中使用 \<td > 元素定义单元格数据，以上实例中有两行数据，每行包含三个单元格。

- 每个表格均有若干行（由 **\<tr>** 标签定义），每行被分割为若干单元格（由 **\<td>** 标签定义），表格可以包含标题行（**\<th>**）用于定义列的标题。

  - **tr**：tr 是 table row 的缩写，表示表格的一行。

  - **td**：td 是 table data 的缩写，表示表格的数据单元格。

  - **th**：th 是 table header的缩写，表示表格的表头单元格。

[更多属性](https://www.runoob.com/html/html-tables.html)









### HTML5教程

### HTML 媒体

### HTML 参考手册

































## 第二部分  CSS





































## 第三部分 JavaScript



