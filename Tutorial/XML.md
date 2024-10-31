# XML 教程

## 1. XML 基础

### 1.1. XML 基础

- XML 指可扩展标记语言（**eXtensible Markup Language**）；
- XML 是一种很像HTML的标记语言；
- XML 的设计宗旨是传输数据，而不是显示数据；
- XML 标签没有被预定义。您需要自行定义标签；
- XML 被设计为具有自我描述性；
- XML 是 W3C 的推荐标准。

### 1.2. XML 树结构

​	XML 文档必须包含**根元素**。该元素是所有其他元素的父元素。

​	XML 文档中的元素形成了一棵文档树。这棵树从根部开始，并扩展到树的最底端。

### 1.3. XML 语法规则

#### 1.3.1. 声明

​	XML 声明文件的可选部分，如果存在需要放在文档的第一行：

```xml
<?xml version="1.0" encoding="utf-8"?>
```

#### 1.3.2. 根元素

​	XML 必须包含根元素，它是所有其他元素的父元素。

#### 1.3.3. 属性

​	元素可以包含属性，属性提供有关元素的附加信息。

```xml
<person age="30" gender="male">John Doe</person>
```

**注意：**属性值必须加引号。

#### 1.3.4. 标签

​	所有的 XML 元素一般都有一个关闭标签，但也允许单标签的使用的。

```xml
<elementName attribute="value" />
```

**注意：**XML 对标签大小写敏感。

#### 1.3.5. 实体引用

| \&lt   | <    | less than      |
| ------ | ---- | -------------- |
| \&gt   | >    | greater than   |
| \&amp  | &    | ampersand      |
| \&apos | '    | apostrophe     |
| \&quot | "    | quotation mark |

**注意：**在 XML 中，只有字符 "<" 和 "&" 确实是非法的。大于号是合法的。

#### 1.3.6. 注释

```xml
<!-- This is a comment -->
```

#### 1.3.7. 空格 & 换行

​	XML 中不会删减连续的空格字符；XML 中以 LF 存储换行。

### 1.4. XML 元素

​	XML 元素指的是从（且包括）开始标签直到（且包括）结束标签的部分。

​	一个元素可以包含：

- 其他元素；
- 文本；
- 属性；
- 或混合以上所有。

#### 1.4.1. 命名规则

​	XML 元素必须遵循以下命名规则：

- 名称可以包含字母、数字以及其他的字符；
- 名称不能以数字或者标点符号开始；
- 名称不能以字母 xml（或者 XML、Xml 等等）开始；
- 名称不能包含空格。

**注意：**可使用任何名称，没有保留的字词。

### 1.5. XML 属性

​	属性通常提供不属于数据组成部分的信息，但是对需要处理这个元素的软件来说却很重要。

​	XML 的属性必须被引号包围，单引号和双引号均可使用。但是应尽量减少在XML 中使用属性，如果觉得信息很像数据，可以使用元素。

#### 1.5.1. 属性的弊端

- 属性不能包含多个值（元素可以）
- 属性不能包含树结构（元素可以）
- 属性不容易扩展（为未来的变化）

#### 1.5.2. 元数据的属性

​	有时候会向元素分配 ID 引用。这些 ID 索引可用于**标识** XML 元素，它起作用的方式与 HTML 中 id 属性是一样的。元数据（有关数据的数据）应当存储为属性，而数据本身应当存储为元素。

### 1.6. XML 验证器

​	拥有正确语法的 XML 被称为”形式良好"的 XML，通过 DTD 验证的 XML是"合法"的 XML。可以通过在 XML 文件中引用 DTD 文件，用于验证 XML 的文档结构：

```xml
<!DOCTYPE note SYSTEM "Note.dtd">
```

​	而 DTD 的目的是定义 XML 文档的结构，它使用一系列合法的元素来定义文档结构：

```xml
<!DOCTYPE note
[
<!ELEMENT note (to,from,heading,body)>
<!ELEMENT to (#PCDATA)>
<!ELEMENT from (#PCDATA)>
<!ELEMENT heading (#PCDATA)>
<!ELEMENT body (#PCDATA)>
]>
```

​	或者可以使用 Schema 验证 XML 文档结构：

```xml
<xs:element name="note">
<xs:complexType>
<xs:sequence>
<xs:element name="to" type="xs:string"/>
<xs:element name="from" type="xs:string"/>
<xs:element name="heading" type="xs:string"/>
<xs:element name="body" type="xs:string"/>
</xs:sequence>
</xs:complexType>
</xs:element>
```

### 1.7. XML 文件查看

​	在所有主流的浏览器中，均能够查看原始的 XML 文件，不要指望 XML 文件会直接显示为 HTML 页面。

​	如果一个错误的XML文件被打开，浏览器会报告错误。

### 1.8. XML 显示

#### 1.8.1 CSS 显示

​	通过使用 CSS（Cascading Style Sheets 层叠样式表），可以添加显示信息到 XML 文档中。

```xml
<?xml-stylesheet type="text/css" href="cd_catalog.css"?>
```

#### 1.8.2. XSLT 显示

​	XSLT（**eXtensible Stylesheet Language Transformations**）远比 CSS 更加完善，通过使用 XSLT，可以把 XML 文档转换成 HTML 格式。XSLT 是在浏览器显示 XML 文件之前，先把它转换为 HTML。

## 2. XML Javascript

### 2.1. XML 解析器（Parser）

​	所有现代浏览器都有内建的 XML 解析器。XML 解析器能把 XML 文档转换为 XML DOM 对象（可通过 JavaScript 操作的对象）。

#### 2.1.1. XMLHttpRequest 对象

​	**XMLHttpRequest** 对象用于在后台与服务器交换数据：

- 在不重新加载页面的情况下更新网页；
- 在页面已加载后从服务器请求数据；
- 在页面已加载后从服务器接收数据；
- 在后台向服务器发送数据。

​	创建 XMLHttpRequest 对象：

```javascript
xmlhttp=new XMLHttpRequest();
```

#### 1.9.2. 解析 XML 文档

```javascript
xmlhttp.open("GET","books.xml",false);
xmlhttp.send();
xmlDoc=xmlhttp.responseXML;
```

#### 1.9.3. 解析 XML 字符串

```javascript
parser=new DOMParser();
xmlDoc=parser.parseFromString(txt,"text/xml");
```

### 2.2. XML DOM

​	XML DOM（**XML Document Object Model**）定义了访问和操作 XML 文档的标准方法。XML DOM 把 XML 文档作为树结构来查看，所有元素可以通过 DOM 树来访问。可以修改或删除它们的内容，并创建新的元素。元素，它们的文本，以及它们的属性，都被认为是节点。

**注意：**即使 XML 文件只包含一个 `<to>` 元素，仍然必须指定数组索引 [0]。这是因为 `getElementsByTagName()` 方法返回一个数组。

## 3. XML 进阶

### 3.1. XML 命名空间

#### 3.1.1. 命名冲突

​	在 XML 中，元素名称是由开发者定义的，当两个不同的文档使用相同的元素名时，就会发生命名冲突。

#### 3.1.2. 前缀 - xmlns 属性

​	在 XML 中的命名冲突可以通过使用名称前缀从而容易地避免。但是在 XML 中使用前缀时，一个所谓的用于前缀的**命名空间**必须被定义，即定义标签的 `xmlns` 属性。定义可以在块标签里，也可以在根标签里。

```xml
<root xmlns:h="http://www.w3.org/TR/html4/"
xmlns:f="http://www.w3cschool.cc/furniture">
</root>

<!-- 或者 -->

<h:table xmlns:h="http://www.w3.org/TR/html4/">
</h:table>
<f:table xmlns:f="http://www.w3cschool.cc/furniture">
</f:table>
```

​	当命名空间被定义在元素的开始标签中时，所有带有相同前缀的子元素都会与同一个命名空间相关联。

**注意：**命名空间 URI 不会被解析器用于查找信息，其目的是赋予命名空间一个惟一的名称。

#### 3.1.3. URI

​	统一资源标识符（**Uniform Resource Identifier**，URI）是一串可以标识因特网资源的字符。最常用的 URI 是用来标识因特网域名地址的**统一资源定位器**（URL），另一个不那么常用的 URI 是**统一资源命名**（URN）。

### 3.2. XML CDATA

​	XML 文档中的所有文本均会被解析器解析。只有 CDATA 区段中的文本会被解析器忽略。某些文本，比如 JavaScript 代码，包含大量 `<` 或 `&` 字符。为了避免错误，可以将脚本代码定义为 CDATA。

```xml
<![CDATA[
...
]]>
```

**注意：**

- CDATA 部分不能包含字符串 `]]>`，也不允许嵌套的 CDATA 部分；

- 标记 CDATA 部分结尾的 `]]>` 不能包含空格或换行。

### 3.3. XML 编码

​	XML 文档可以包含非 ASCII 字符。为了避免错误，需要规定 XML 编码，或者将 XML 文件存为 Unicode。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml version="1.0" encoding="UTF-16"?>
...
```

## 4. XML DOM

​	XML DOM 定义了访问和处理 XML 文档的标准。

### 4.1. XML DOM 节点

​	在 DOM 中，XML 文档中的每个成分都是一个节点。

- 整个文档是一个文档节点；
- 每个 XML 元素是一个元素节点；
- 包含在 XML 元素中的文本是文本节点；
- 每一个 XML 属性是一个属性节点；
- 注释是注释节点。

#### 4.1.1. XML DOM 节点树

​	XML DOM 把 XML 文档视为一种树结构，这种树结构被称为**节点树**。

##### 节点关系

​	节点树中的节点彼此之间都有层级关系。**父节点**、**子节点**和**同级节点**用于描述这种关系。父节点拥有子节点，位于相同层级上的子节点称为同级节点。

- 在节点树中，顶端的节点称为根节点；
- 根节点之外的每个节点都有一个父节点；
- 节点可以有任何数量的子节点；
- 叶子是没有子节点的节点；
- 同级节点是拥有相同父节点的节点。

#### 4.1.2. XML DOM 解析器

​	XML DOM 包含了遍历 XML 树，访问、插入及删除节点的方法。然而，在访问和操作 XML 文档之前，它必须加载到 XML DOM 对象。XML 解析器读取 XML，并把它转换为 XML DOM 对象，这样才可以使用 JavaScript 访问它。

##### 跨域访问

​	出于安全原因，现代的浏览器不允许跨域访问。这意味着，网页以及 XML 文件，它必须位于**同一台服务器**上尝试加载。

### 4.2. XML DOM 加载函数

​	加载 XML 文档中的代码可以存储在一个函数中。一般有两种加载情况，一种是从 `.xml` 文件中加载，一种是从 `.txt` 文件中加载。

#### 4.2.1. 加载 xml 文件

```javascript
function loadXMLDoc(dname)
{
    if (window.XMLHttpRequest)
    {
        xhttp=new XMLHttpRequest();
    }
    else
    {
        xhttp=new ActiveXObject("Microsoft.XMLHTTP");
    }
    xhttp.open("GET",dname,false);
    xhttp.send();
    return xhttp.responseXML;
}
```

#### 4.2.2. 加载 txt 文件

```javascript
function loadXMLString(txt) 
{
    if (window.DOMParser)
    {
        parser=new DOMParser();
        xmlDoc=parser.parseFromString(txt,"text/xml");
    }
    else 
    {
        // Internet Explorer
        xmlDoc=new ActiveXObject("Microsoft.XMLDOM");
        xmlDoc.async=false;
        xmlDoc.loadXML(txt); 
    }
    return xmlDoc;
}
```

### 4.3. XML DOM 属性和方法

#### 4.3.1. XML DOM 属性

​	一些典型的 DOM 属性：

- `x.nodeName` ：x 的名称；
- `x.nodeValue` ：x 的值；
- `x.parentNode` ：x 的父节点；
- `x.childNodes` ：x 的子节点；
- `x.attributes` ：x 的属性节点。

#### 4.3.2. XML DOM 方法

- `x.getElementsByTagName(name)` ：获取带有指定标签名称的所有元素；
- `x.appendChild(node)` ：向 x 插入子节点；
- `x.removeChild(node)` ：从 x 删除子节点。

### 4.4. XML DOM 节点操作

#### 4.4.1. XML DOM 访问节点

##### 访问节点

- 使用 `getElementsByTagName()` 方法；

- 循环（遍历）节点树；

- 利用节点的关系在节点树中导航。

##### 节点列表（Node List）

​	`getElementsByTagName()` 方法返回节点列表，节点列表是节点的数组，可以通过索引访问。

```javascript
x=xmlDoc.getElementsByTagName("title");
y=x[2];
```

##### 节点列表长度（Node List Length）

​	`length` 属性定义节点列表的长度（即节点的数量）。

```javascript
document.getElementById("length").innerHTML = x.length;
```

##### 节点类型（Node Types）

​	XML 文档的 **documentElement** 属性是根节点；节点的 **nodeName** 属性是节点的名称。节点的 **nodeType** 属性是节点的类型。

##### getElementsByTagName() 方法

​	`getElementsByTagName()` 返回拥有指定标签名的所有元素。

```javascript
node.getElementsByTagName("tagname")
```

##### 遍历节点

​	通过循环的方式遍历节点。

```javascript
for (i=0;i<x.length;i++)
{
  // 判断节点类型为元素节点
  if (x[i].nodeType==1)
  {
    document.write(x[i].nodeName);
  }
}
```

##### 导航节点

​	利用节点之间的关系进行导航遍历。

```javascript
x=xmlDoc.getElementsByTagName("book")[0].childNodes;
y=xmlDoc.getElementsByTagName("book")[0].firstChild;

for (i=0;i<x.length;i++)
{
  if (y.nodeType==1)
  {
  document.write(y.nodeName + "");
  }
  y=y.nextSibling;
}
```

#### 4.4.2. XML DOM 节点信息

##### 节点属性

###### 节点自身属性

- `nodeName` ：规定节点的名称。
  - `nodeName` 是只读的；
  - 元素节点的 `nodeName` 与标签名相同；
  - 属性节点的 `nodeName` 是属性的名称；
  - 文本节点的 `nodeName` 永远是 `#text`；
  - 文档节点的 `nodeName` 永远是 `#document`。
- `nodeValue` ：规定节点的值。
  - 元素节点的 `nodeValue` 是 `undefined`；
  - 文本节点的 `nodeValue` 是文本本身；
  - 属性节点的 `nodeValue` 是属性的值。
- `nodeType` ：规定节点的类型。
  - **1：**元素；
  - **2：**属性；
  - **3：**文本；
  - **8：**注释；
  - **9：**文档。

###### 节点关系属性

- `parentNode` ：获取父节点；
- `childNodes` ：获取所有子节点；
- `firstChild` ：获取第一个子节点；
- `lastChild` ：获取最后一个子节点；
- `nextSibling` ：获取下一个兄弟节点；
- `previousSibling` ：获取上一个兄弟节点。

##### 节点值

###### 元素值

​	元素节点**没有**文本值。元素节点的文本存储在子文本节点。获取元素文本的方法，就是获取这个子节点（文本节点）的值。

###### 属性值

​	属性节点**拥有**文本值。获取属性的值的方法，就是获取它的文本值。

- `getAttribute(”attribute“)` ：返回当前节点的 `attribute` 属性的值；
- `getAttributeNode("attribute")` ：返回当前节点中 `attribute` 的属性节点；

**注意：**一个返回的是值，一个返回的是节点。

#### 4.4.3. XML DOM 修改节点

##### 改变节点值

- `nodeValue` ：用于改变节点值；
- `setAttribute()` ：用于改变属性值。

##### 删除节点

- `removeChild()` ：删除指定节点；
- `removeAttribute()` ：删除指定属性；
- `removeAttributeNode(node)` ：删除属性所在节点的全部属性。

##### 替换节点

- `replaceChild()` ：替换指定节点；
- `nodeValue` ：替换文本节点中的文本；
- `replaceData(offset, length, string)` ：替换文本节点中的数据：
  - **offset ：**在何处开始替换字符，offset 值以 0 开始；
  - **length ：**要替换多少字符；
  - **string ：**要插入的字符串。

##### 创建节点

- `createElement()` ：创建一个新的元素节点；
- `createAttribute()` ：创建一个新的属性节点；
- `setAttribute()` ：可以在属性不存在的情况下创建新的属性；
- `createTextNode()` ：创建一个新的文本节点：
- `createCDATASection()` ：创建一个新的 CDATA section 节点；
- `createComment()` ：创建一个注释节点。

**注意：**新创建的节点需要使用 `appendChild()` 追加进文档。

##### 添加节点

- `appendChild()` ：向一个已有的节点添加一个子节点，新节点会添加（追加）到任何已有的子节点之后；
- `insertBefore()` ：在指定节点之前插入节点；
- `setAtttribute()` ：如果属性不存在，则会创建一个新属性；
- `insertData()` ：将数据插入已有的文本节点中；
  - `offset` ：在何处开始插入字符（以 0 开始）；
  - `string` ：要插入的字符串；

##### 克隆节点

- `cloneNode()` ：创建指定节点的副本；
  - `true|false` ：是否复制指定节点的全部属性和子节点。

### 4.5. XMLHttpRequest 对象

> - 在不重新加载页面的情况下更新网页；
> - 在页面已加载后从服务器请求数据；
> - 在页面已加载后从服务器接收数据；
> - 在后台向服务器发送数据。

#### 4.5.1. 创建对象

```javascript
// 现代浏览器
xmlhttp=new XMLHttpRequest();
// 旧版本的 Internet Explorer
xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
```

#### 4.5.2. 发送请求

- `open(method,url,async)` ：规定请求类型；
  - `method` ：请求的类型，`GET` 或 `POST`；
  - `url` ：文件在服务器上的位置；
    `async `：`true`（异步）或 `false`（同步）；
- `send(string)` ：发送请求到服务器；
  - `string`：仅用于 POST 请求

**注意：**

1. `GET` 比 `POST` 简单并且快速，可用于大多数情况下，但是 `POST` 比 `GET` 更强大更安全；

2. 下面的情况下必须使用 `POST` 请求：

   - 缓存的文件不是一个选项（更新服务器上的文件或数据库）；

   - 发送到服务器的数据量较大（`POST` 没有大小的限制）；

   - 发送用户输入（可以包含未知字符）；

3. 异步是指，Javascript 不需要等待服务器响应，等待服务器响应中，执行其他脚本，响应准备时，处理响应；

#### 4.5.3. 服务器响应

- `responseText` ：获取响应数据作为字符串；
- `responseXML` ：返回 XML 文档对象，可以使用 DOM 节点树的方法和属性解析该对象；
- `onreadystatechange` ：在每次 `readyState` 变化时触发；
- `readyState` ：存放服务器响应的状态，范围 0 ~ 4；
  - **0 ：**请求未初始化；
  - **1 ：**服务器建立连接；
  - **2 ：**收到请求；
  - **3 ：**处理请求；
  - **4 ：**请求完成和响应准备就绪；
- `status` ：网页的状态；
  - **200 ：**”OK“；
  - **404 ：**找不到页面。

### 4.6. 节点类型

#### 4.6.1.  节点描述

| 节点类型              | 描述                                                   | 子类                                                         |
| :-------------------- | :----------------------------------------------------- | :----------------------------------------------------------- |
| Document              | 代表整个文档（DOM 树的根节点）                         | Element (max. one), ProcessingInstruction, Comment, DocumentType |
| DocumentFragment      | 代表"轻量级"的 Document 对象，它可以保留文档中的一部分 | Element, ProcessingInstruction, Comment, Text, CDATASection, Entity参考手册 |
| DocumentType          | 为文档中定义的实体提供了一个接口                       | None                                                         |
| ProcessingInstruction | 代表一个处理指令                                       | None                                                         |
| EntityReference       | 代表一个实体引用                                       | Element, ProcessingInstruction, Comment, Text, CDATASection, EntityReference |
| Element               | 表示一个元素                                           | Element, Text, Comment, ProcessingInstruction, CDATASection, EntityReference |
| Attr                  | 代表一个属性                                           | Text, EntityReference                                        |
| Text                  | 代表元素或属性的文本内容                               | None                                                         |
| CDATASection          | 代表文档中的 CDATA 区段（文本不会被解析器解析）        | None                                                         |
| Comment               | 代表一个注释                                           | None                                                         |
| Entity                | 代表一个实体                                           | Element, ProcessingInstruction, Comment, Text, CDATASection, EntityReference |
| Notation              | 定义一个在 DTD 中声明的符号                            | None                                                         |

#### 4.6.2. 节点返回值

| 节点类型              | 返回的节点名称     | 返回的节点值 |
| :-------------------- | :----------------- | :----------- |
| Document              | #document          | null         |
| DocumentFragment      | #document fragment | null         |
| DocumentType          | 文档类型名称       | null         |
| Entity参考手册        | 实体引用名称       | null         |
| Element               | 元素名称           | null         |
| Attr                  | 属性名称           | 属性值       |
| ProcessingInstruction | 目标               | 节点的内容   |
| Comment               | #comment           | 注释文本     |
| Text                  | #text              | 节点的内容   |
| CDATASection          | #cdata-section     | 节点的内容   |
| Entity                | 实体名称           | null         |
| Notation              | 符号名称           | null         |

#### 4.6.3. 节点类型常量

| 节点类型 | 命名常量                    |
| :------- | :-------------------------- |
| 1        | ELEMENT_NODE                |
| 2        | ATTRIBUTE_NODE              |
| 3        | TEXT_NODE                   |
| 4        | CDATA_SECTION_NODE          |
| 5        | ENTITY_REFERENCE_NODE       |
| 6        | ENTITY_NODE                 |
| 7        | PROCESSING_INSTRUCTION_NODE |
| 8        | COMMENT_NODE                |
| 9        | DOCUMENT_NODE               |
| 10       | DOCUMENT_TYPE_NODE          |
| 11       | DOCUMENT_FRAGMENT_NODE      |
| 12       | NOTATION_NODE               |

### 4.7. XML DOM 对象

#### 4.7.1. Node 对象

[详细手册](https://www.runoob.com/dom/dom-node.html)

#### 4.7.2. NodeList 对象

[详细手册](https://www.runoob.com/dom/dom-nodelist.html)

#### 4.7.3. NamedNodeMap 对象

[详细手册](https://www.runoob.com/dom/dom-namednodemap.html)

#### 4.7.4. Document 对象

[详细手册](https://www.runoob.com/dom/dom-document.html)

#### 4.7.5. DocumentImplementation 对象

[详细手册](https://www.runoob.com/dom/dom-documentimplementation.html)

#### 4.7.6. DocumentType 对象

[详细手册](https://www.runoob.com/dom/dom-documenttype.html)

#### 4.7.7. ProcessingInstruction 对象

[详细手册](https://www.runoob.com/dom/dom-processinginstruction.html)

#### 4.7.8. Element 对象

[详细手册](https://www.runoob.com/dom/dom-element.html)

#### 4.7.9. Attr 对象

[详细手册](https://www.runoob.com/dom/dom-attribute.html)

#### 4.7.10. Text 对象

[详细手册](https://www.runoob.com/dom/dom-text.html)

#### 4.7.11. CDATASection 对象

[详细手册](https://www.runoob.com/dom/dom-cdatasection.html)

#### 4.7.12. Comment 对象

[详细手册](https://www.runoob.com/dom/dom-comment.html)

#### 4.7.13. XMLHttpRequest 对象

[详细手册](https://www.runoob.com/dom/dom-http.html)

#### 4.7.14. Parse Error 对象

[详细手册](https://www.runoob.com/dom/dom-errors.html)

## 5. XPath



## 6. XML XSLT

​	XSL 指扩展样式表语言（**EXtensible Stylesheet Language**）, 它是一个 XML 文档的样式表语言。XSLT 指 XSL 转换，用于将 XML 文档转换为其他文档，比如 XHTML。

### 6.1.  XSLT 转换

#### 6.1.1. 样式表声明

```html
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www...">
<!-- 或者 -->
<xsl:transform version="1.0"
xmlns:xsl="http://www...">
```

​	并且把样式表链接到 XML 文档：

```xml
<?xml-stylesheet type="text/xsl" href="filename.xsl"?>
```

### 6.2. XSLT 元素

#### 6.2.1. \<xsl:template>

​	`<xsl:template>`  元素用于关联 XML 元素与模板。`match` 属性的值时 XPath 表达式，用来限定模板生效的范围。

#### 6.2.2 \<xsl:value-of>

​	`<xsl:value-of>` 元素用于提取某个 XML 元素的值，并把值添加到转换的输出流中。

#### 6.2.3. \<xsl:for-each>

​	`<xsl:for-each>` 元素可用于选取指定的节点集中的每个 XML 元素，允许在 XSLT 中循环。

```html
<xsl:for-each select="XPath">
  ...
</xsl:for-each>
```

​	可以添加一个选择属性的判别式，用于过滤输出结果：

```html
<xsl:for-each select="XPath[attribute="value"]">
  ...
</xsl:for-each>
```

**注意：**合法的运算符有：

- `=`  ：等于；
- `!=` ：不等于；
- `&lt` ：小于；
- `&gt` ：大于。

#### 6.2.4. \<xsl:sort>

​	`<xsl:sort>` 用于对输出结果进行排序。如果某个地方需要对输出结果排序，那么只需要在指定地方放置 `<xsl:sort>` 元素，并指定排序标签。

#### 6.2.5. \<xsl:if> 

​	`<xsl:if>` 元素用于放置针对 XML 文件内容的条件测试。

```html
<xsl:if test="expression">
...如果条件成立则输出...
</xsl:if>
```

**注意：**必需包含 **test** 属性，其值包含了需要求值的表达式。

#### 6.2.6. \<xsl:choose>

​	`<xsl:choose>` 元素用于结合 `<xsl:when>` 和 `<xsl:otherwise>` 来表达多重条件测试。

```html
<xsl:choose>
<xsl:when test="expression">
... some output ...
</xsl:when>
<xsl:otherwise>
... some output ....
</xsl:otherwise>
</xsl:choose>
```

#### 6.2.7. \<xsl:apply-templates>

​	`<xsl:apply-templates>` 元素可把一个模板应用于当前的元素或者当前元素的子节点。

#### 6.2.8. 更多

- [XSLT 元素参考手册](https://www.runoob.com/xsl/xsl-w3celementref.html) ；
- [XSLT 函数参考手册](https://www.runoob.com/xsl/xsl-functions.html) 。













