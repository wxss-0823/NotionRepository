# JQuery 教程

## 1. JQuery 基础

### 1.1. JQuery 简介

​	jQuery 是一个轻量级的"写的少，做的多"的 JavaScript 库，包含以下功能：

- HTML 元素选取；
- HTML 元素操作；
- CSS 操作；
- HTML 事件函数；
- JavaScript 特效和动画；
- HTML DOM 遍历和修改；
- AJAX；
- Utilities。

#### 1.1.1. JQuery 安装

​	可以从 [jquery.com](https://jquery.com/download/) 中下载 js 文件，或者引用 CDN（内容分布网络）来使用内置函数。

### 1.2. JQuery 语法

​	jQuery 语法是通过选取 HTML 元素，并对选取的元素执行某些操作。基础语法： `$(selector).action()`

- **$ ：** 定义 jQuery；
- **(selector) ：**查询和查找 HTML 元素；
- **action() ：**执行对元素的操作。

#### 1.2.1. 文档就绪事件

​	为了防止文档在完全加载之前运行 jQuery 代码，即在 DOM 加载完成后才可以对 DOM 进行操作。需要配置代码在文档就绪后执行。

```javascript
$(document).ready(function(){
   // jQuery 代码...
});
// 或
$(function(){
   // jQuery 代码...
});
```

### 1.3. JQuery 选择器

​	jQuery 选择器允许对 HTML 元素组或单个元素进行操作，基于元素的 id、类、类型、属性、属性值等查找HTML 元素。 jQuery 中所有选择器都以美元符号开头：`$()`。

#### 1.3.1. 元素选择器

​	在页面中选取所有 `<p>` 元素：

```javascript
$("p")
```

#### 1.3.2. id 选择器

​	页面中元素的 id 应该是唯一的，所以您要在页面中选取唯一的元素需要通过 #id 选择器。

```javascript
$("#test")
```

#### 1.3.3. 类选择器

​	jQuery 类选择器可以通过指定的 class 查找元素。

```javascript
$(".test")
```

#### 1.3.4. 其他选择器

| 语法                     | 描述                                                  |
| :----------------------- | :---------------------------------------------------- |
| `$("*")`                 | 选取所有元素                                          |
| `$(this)`                | 选取当前 HTML 元素                                    |
| `$("p.intro")`           | 选取 class 为 intro 的 `<p>` 元素                     |
| `$("p:first")`           | 选取第一个 `<p>` 元素                                 |
| `$("ul li:first")`       | 选取第一个 `<ul>` 元素的第一个 `<li>` 元素            |
| `$("ul li:first-child")` | 选取每个 `<ul>` 元素的第一个 `<li>` 元素              |
| $("[href]")              | 选取带有 `href` 属性的元素                            |
| $("a[target='_blank']")  | 选取所有 `target` 属性值等于 `_blank` 的 `<a>` 元素   |
| $("a[target!='_blank']") | 选取所有 `target` 属性值不等于 `_blank` 的 `<a>` 元素 |

### 1.4. JQuery 事件

​	jQuery 是为事件处理特别设计的。页面对不同访问者的响应叫做事件。

事件处理程序指的是当 HTML 中发生某些事件时所调用的方法。

#### 1.4.1. 事件方法语法

```javascript
$("p").click(function(){
    // 当点击标签 p 时执行的代码
});
```

#### 1.4.2. 常用的事件方法

##### $(document).ready()

​	允许在文档完全加载完后执行函数。

##### click() 

​	当按钮点击事件被触发时会调用一个函数。

##### dblclick()

​	当双击元素时，会发生 `dblclick` 事件。

##### mouseenter()

​	当鼠标指针穿过元素时，会发生 `mouseenter` 事件。

##### mouseleave()

​	当鼠标指针离开元素时，会发生 `mouseleave` 事件。

##### mousedown()

​	当鼠标指针移动到元素上方，并按下鼠标按键时，会发生 `mousedown` 事件。

##### mouseup()

​	当在元素上松开鼠标按钮时，会发生 `mouseup` 事件。

##### hover()

​	用于模拟光标悬停事件。

##### focus()

​	当元素获得焦点时，发生 `focus` 事件。

##### blur()

​	当元素失去焦点时，发生 `blur` 事件。

## 2. JQuery 效果

### 2.1. JQuery 隐藏/显示

#### 2.1.1. hide() & show()

​	通过 jQuery，可以使用 `hide()` 和 `show()` 方法来隐藏和显示 HTML 元素。

#### 2.1.2. toggle()

​	通过 jQuery，可以使用 `toggle()` 方法来切换 `hide()` 和 `show()` 方法。显示被隐藏的元素，并隐藏已显示的元素。

### 2.2. JQuery 淡入/淡出

​	通过 jQuery，可以实现元素的淡入淡出效果。jQuery 拥有下面四种 fade 方法：

- `fadeIn()` ：用于淡入已隐藏的元素；

- `fadeOut()` ：用于淡出可见元素；
- `fadeToggle()` ： 可以在 `fadeIn()` 与 `fadeOut()` 方法之间进行切换；
- `fadeTo()` ：允许渐变为给定的不透明度（值介于 0 与 1 之间）。

### 2.3. JQuery 滑动

​	通过 jQuery，可以在元素上创建滑动效果。jQuery 拥有以下滑动方法：

- `slideDown()` ：用于向下滑动元素；
- `slideUp()` ：用于向上滑动元素；
- `slideToggle()` ：可以在 slideDown() 与 slideUp() 方法之间进行切换。

### 2.4. JQuery 动画

#### 2.4.1. animate() 方法

​	jQuery `animate()` 方法用于创建自定义动画。

```javascript
$(selector).animate({params},speed,callback);
```

- 必需的 `params` 参数定义形成动画的 CSS 属性；

- 可选的 `speed` 参数规定效果的时长；

- 可选的 `callback` 参数是动画完成后所执行的函数名称。

#### 2.4.2. animate() 操作多个属性

```javascript
$("button").click(function(){
  $("div").animate({
    left:'250px',
    opacity:'0.5',
    height:'150px',
    width:'150px'
  });
});
```

#### 2.4.3. animate() 使用相对值

```javascript
$("button").click(function(){
  $("div").animate({
    left:'250px',
    height:'+=150px',
    width:'+=150px'
  });
});
```

#### 2.4.4. animate() 使用预定义的值

​	可以把属性的动画值设置为 `show`、`hide` 或 `toggle`。

```javascript
$("button").click(function(){
  $("div").animate({
    height:'toggle'
  });
});
```

#### 2.4.5. animate() 使用队列功能

​	默认地，jQuery 提供针对动画的队列功能。这意味着如果编写多个 `animate()` 调用，jQuery 会逐一运行这些 `animate()` 调用。

### 2.5. JQuery 停止动画

#### 2.5.1. jQuery stop() 方法

​	用于停止动画或效果，在它们完成之前，`stop()` 方法适用于所有 jQuery 效果函数，包括滑动、淡入淡出和自定义动画。

```javascript
$(selector).stop(stopAll,goToEnd);
```

- 可选的 `stopAll` 参数规定是否应该清除动画队列，默认是 `false`，即仅停止活动的动画，允许任何排入队列的动画向后执行；

- 可选的 `goToEnd` 参数规定是否立即完成当前动画，默认是 false。

### 2.6. JQuery Callback

​	`Callback` 函数在当前事件 100% 完成之后执行。

### 2.7. JQuery 链

​	通过 jQuery，可以把动作/方法链接在一起，`Chaining` 允许在一条语句中运行多个 jQuery 方法（在相同的元素上）。

```javascript
$("#p1").css("color","red").slideUp(2000).slideDown(2000);
```

**注意：**当进行链接时，代码行会变得很长。不过，jQuery 语法不是很严格，可以按照希望的格式来写，包含换行和缩进。

## 3. JQuery HTML

### 3.1. JQuery 捕获

​	jQuery 中非常重要的部分，就是操作 DOM 的能力，其提供了一系列与 DOM 相关的方法，这使访问和操作元素和属性变得很容易。

#### 3.1.1. 获取内容

- **text() ：**设置或返回所选元素的文本内容；
- **html() ：**设置或返回所选元素的内容（包括 HTML 标签）；
- **val() ：** 设置或返回表单字段的值；

#### 3.1.2. 获取属性

- **attr() ：**用于获取属性值。

### 3.2. JQuery 设置内容与属性

​	可以直接通过捕获的方法设置元素的内容，但是会覆盖捕获的全部旧文本。如果需要只改变某一个文本，或者保留旧文本，可以使用回调函数。函数有两个参数：被选中元素列表中当前元素的下标，以及旧文本。

#### 3.2.1. 设置内容

​	直接设置内容：

```javascript
$("#btn1").click(function(){
    $("#test1").text("Hello world!");
});
```

​	调用回调函数实现：

```javascript
$("#btn1").click(function(){
    $("#test1").text(function(i,origText){
        return "旧文本: " + origText + " 新文本: Hello world! (index: " + i + ")"; 
    });
});
```

#### 3.2.2. 设置属性

​	直接设置属性：

```javascript
$("button").click(function(){
  $("#runoob").attr("href","http://www.runoob.com/jquery");
});
```

​	调用回调函数实现：


```javascript
$("button").click(function(){
  $("#runoob").attr("href", function(i,origValue){
    return origValue + "/jquery"; 
  });
});
```

### 3.3. JQuery 添加元素

#### 3.3.1. append() 方法

​	在被选元素的结尾插入内容（仍然在该元素的内部）。

```javascript
$(selector).append(txt1, txt2, txt3);
```

#### 3.3.2. prepend() 方法

​	在被选元素的开头插入内容。

```javascript
$(selector).prepend(txt1, txt2, txt3);
```

#### 3.3.3. after() 和 before() 方法

​	在被选元素之后/之前插入内容。

```javascript
$(selector).after(txt1, txt2, txt3);
$(selector).before(txt1, txt2, txt3);
```

### 3.4. JQuery 删除元素

#### 3.4.1. remove() 方法

​	删除被选元素及其子元素。

```javascript
$(selector).remove();
```

#### 3.4.2. empty() 方法

​	删除被选元素的子元素。

```javascript
$(selector).empty();
```

#### 3.4.3. 过滤被删除的元素

​	`remove()` 方法可以接收一个参数，允许对被删元素进行过滤。

```javascript
$(selector).remove(selector)
```

### 3.5. 操作 CSS

#### 3.5.1. addClass() 方法

​	用于为指定元素添加类。在添加类时，也可以选取多个元素：

```javascript
$("button").click(function(){
  $("h1,h2,p").addClass("blue");
  $("div").addClass("important");
});
```

#### 3.5.2. removeClass() 方法

​	用于在不同的元素中删除指定的 `class` 属性：

```javascript
$("button").click(function(){
  $("h1,h2,p").removeClass("blue");
});
```

#### 3.5.3. toggleClass() 方法

​	用于切换 `class` 类的添加与删除。如果当前有，则删除；没有，则添加：

```javascript
$("button").click(function(){
  $("h1,h2,p").toggleClass("blue");
});
```

#### 3.5.4. css() 方法

##### 返回 CSS 属性

```javascript
css("propertyname");
```

##### 设置 CSS 属性

```javascript
css("propertyname","value");
```

##### 设置多个 CSS 属性

```javascript
css({"propertyname":"value","propertyname":"value",...});
```

### 3.6. JQuery 尺寸

​	JQuery 规定了一套对应于 HTML 页面尺寸的函数，从外向内依次是：

- **Margin ：**`outerWidth(true)`，`outerWidth(true)`；
- **Border ：**`outerWidth(true)`，`outerWidth(true)`；
- **Padding ：**`innerWidth()`，`innerHeight()`；
- **Element ：**`width()`，`height()`。

#### 3.6.1. width() 和 height() 方法

​	`width()` 方法设置或返回元素的宽度（不包括内边距、边框或外边距）。

​	`height()` 方法设置或返回元素的高度（不包括内边距、边框或外边距）。

#### 3.6.2. innerWidth() 和 innerHeight() 方法

​	`innerWidth()` 方法返回元素的宽度（包括内边距）。

​	`innerHeight()` 方法返回元素的高度（包括内边距）。

#### 3.6.3. outerWidth() 和 outerHeight() 方法

​	`outerWidth()` 方法返回元素的宽度（包括内边距和边框）。

​	`outerHeight()` 方法返回元素的高度（包括内边距和边框）。

## 4. JQuery 遍历

### 4.1. JQuery 遍历祖先

#### 4.1.1. parent() 方法

​	`parent()` 方法返回被选元素的直接父元素。该方法只会向上一级对 DOM 树进行遍历。

#### 4.1.2. parents() 方法

​	`parents()` 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 `<html>`。

#### 4.1.3. parentsUntil() 方法

​	`parentsUntil()` 方法返回介于两个给定元素之间的所有祖先元素。

### 4.2. JQuery 遍历后代

#### 4.2.1. children() 方法

​	`children()` 方法返回被选元素的所有直接子元素。该方法只会向下一级对 DOM 树进行遍历。

#### 4.2.2. find() 方法

​	`find()` 方法返回被选元素的后代元素，一路向下直到最后一个后代。

### 4.3. JQuery 遍历同胞（siblings）

#### 4.3.1. siblings() 方法

​	`siblings()` 方法返回被选元素的所有同胞元素。

#### 4.3.2. next() 方法

​	`next()` 方法返回被选元素的下一个同胞元素。

#### 4.3.3. nextAll() 方法

​	`nextAll()` 方法返回被选元素的所有跟随的同胞元素。

#### 4.3.4. nextUntil() 方法

​	`nextUntil()` 方法返回介于两个给定参数之间的所有跟随的同胞元素。

#### 4.3.5. prev() prevAll() & prevUntil() 方法

​	`prev()`，`prevAll()` 以及 `prevUntil()` 方法的工作方式与上面的方法类似，只不过方向相反而已：它们返回的是前面的同胞元素。

### 4.4. JQuery 遍历过滤

#### 4.4.1. first() 方法

​	`first()` 方法返回被选元素的首个元素。

#### 4.4.2. last() 方法

​	`last()` 方法返回被选元素的最后一个元素。

#### 4.4.3. eq() 方法

​	`eq()` 方法返回被选元素中带有指定索引号的元素。

#### 4.4.4. filter() 方法

​	`filter()` 方法允许规定一个标准。不匹配这个标准的元素会被从集合中删除，匹配的元素会被返回。

#### 4.4.5. not() 方法

​	`not()` 方法返回不匹配标准的所有元素。

## 5. JQuery AJAX

### 5.1. load() 方法

​	从服务器加载数据，并把返回的数据放入被选元素中。

```javascript
$(selector).load(URL,data,callback);
```

- **URL ：**必需，规定希望加载的 URL；

- **data ：**可选，规定与请求一同发送的查询字符串键/值对集合；
- **callback ：**可选，是 `load()` 方法完成后所执行的函数名称。
  - `responseTxt` ：包含调用成功时的结果内容；
  - `statusTXT` ：包含调用的状态；
  - `xhr` ：包含 XMLHttpRequest 对象。

### 5.2. get() & post() 方法

​	`get()` 和 `post()` 方法用于通过 HTTP 请求从服务器请求数据。GET 基本上用于从服务器获得数据，但是 GET 方法可能**缓存返回数据**；POST 也可用于从服务器获取数据，不过，POST 方法不会缓存数据，并且常用于连同请求一起发送数据。

#### 5.2.1. $.get() 方法

​	`$.get()` 方法通过 HTTP GET 请求从服务器上请求数据。

```javascript
$.get(URL, callback);
// 或
$.get( URL [, data ] [, callback ] [, dataType ] )
```

- **URL ：**发送请求的 URL字符串；
- **data ：**可选的，发送给服务器的字符串或 key/value 键值对；
- **callback ：**可选的，请求成功后执行的回调函数；
- **dataType ：**可选的，从服务器返回的数据类型。

####  5.2.2. $.post() 方法

​	`$.post()` 方法通过 HTTP POST 请求向服务器提交数据。

```javascript
$.post(URL,callback);
// 或
$.post( URL [, data ] [, callback ] [, dataType ] )
```

- **URL ：**发送请求的 URL字符串；
- **data ：**可选的，发送给服务器的字符串或 key/value 键值对；
- **callback ：**可选的，请求成功后执行的回调函数；
- **dataType ：**可选的，从服务器返回的数据类型。

## 6. JQuery 其他

### 6.1. JQuery 冲突避免

​	jQuery 使用 `$` 符号作为 jQuery 的简写。其他一些 JavaScript 框架可能也使用 `$` 符号作为简写，jQuery 的团队考虑到了这个问题，并实现了 `noConflict()` 方法。

#### 6.1.1. noConflict() 方法

​	用于释放对 `$` 标识符的控制。

```javascript
$.noConfilct();
```

​	`noConflict()` 可返回对 jQuery 的引用，可以把它存入变量，以避免冲突。

```javascript
var jq = $.noConflict();
```

​	把 `$` 符号作为变量传递给回调函数，这样可以在函数内使用 `$` 符号，而在函数外依旧不能使用。

```javascript
$.noConflict();
jQuery(document).ready(function($){
  $("button").click(function(){
    $("p").text("jQuery 仍然在工作!");
  });
});
```

### 6.2. JQuery JSONP

​	Jsonp（JSON with Padding）是 json 的一种”使用模式“。由于同源策略，我们不可以直接从不同域获取数据，但是可以让网页通过 JSONP 从别的域名（网站）获取资料，即跨域读取数据。

​	当我们试图从其他域名获取数据时，期望获得数据的列表，但是实际上会得到等待一个名为 `callbackFunction()` 的函数处理的数据。也即是我们需要编写对应的 `callbackFunction()` 进行数据处理。

```javascript
$.getJSON("[URL]?jsoncallback=?", function(data) {
	// ...
});
```



