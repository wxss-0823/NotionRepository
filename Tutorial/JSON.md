# JSON 教程

> - **J**ava**S**cript **O**bject **N**otation（JavaScript 对象表示法）；
> - 是一种存储和交换文本信息的语法，类似 XML；
> - 比 XML 更小、更快，更易解析
> - 易于人阅读和编写。

## 1. JSON 基础

### 1.1. JSON 语法

​	JSON 语法是 JavaScript 对象表示语法的**子集**：

- 数据在 `"name":"value"` 对中；
- 数据由逗号 `,` 分隔；
- 使用斜杆 `\` 来转义字符；
- 大括号 `{}` 保存对象；
- 中括号 `[]` 保存数组，数组可以包含多个对象；

#### 1.1.1. JSON 值

- 数字（整数或浮点数）；
- 字符串（在双引号中）；
- 逻辑值（true 或 false）；
- 数组（在中括号中）；
- 对象（在大括号中）；
- `null` 。

### 1.2. JSON  vs XML

​	JSON 与 XML 的**相同**之处：

- 都是 "自我描述" ，都易于理解；
- 都是有层次的结构；
- 数据可以被大多数编程语言使用。

​	JSON 与 XML 的**不同**之处：

- JSON 不需要结束标签；
- JSON 更加简短；
- JSON 读写速度更快；
- JSON 可以使用数组。

**最大的不同是**：XML 需要使用 XML 解析器来解析，JSON 可以使用标准的 JavaScript 函数来解析。

### 1.3. JSON 对象

#### 1.3.1. 对象语法

```json
{ "name1":"string", "name2":int, "name3":null }
```

#### 1.3.2. 访问对象

```javascript
var myOgj, x;
myObJ  = { "name1":"string", "name2":int, "name3":null };
x = myObj.name1;
```

#### 1.3.3. 循环对象

​	可以使用 `for-in` 循环对象属性：

```javascript
var myObj = { "name1":"string", "name2":int, "name3":null };
for (x in myObj) {
	document.getElementById("demo").innerHTML += x + "<br>"
}
```

​	也可以使用 `[]` 访问属性的值：

```javascript
var myObj = { "name1":"string", "name2":int, "name3":null };
for (x in myObj) {
	document.getElementById("demo").innerHTML += myObj[x] + "<br>"
}
```

#### 1.3.4. 嵌套对象

​	JSON 对象中可以包含另外一个 JSON 对象：

```javascript
myObj = {
    "name1":"string",
    "name2":int,
    "name3": {
        "site1":"xxx",
        "site2":"yyy",
        "site3":"zzz"
    }
}
```

​	可以使用 `.` 或者 `[]` 来访问嵌套的 JSON 对象：

```javascript
x = myObj.name3.site1;
// or
x = myObj.name3["site1"];
```

#### 1.3.5. 修改值

​	可以使用 `.` 来修改 JSON 对象的值：

```javascript
myObj.name3.site1 = "xyz";
```

​	也可以使用 `[]` 来修改 JSON 对象的值：

```javascript
myObj.name3.site1 = "xyz";
```

#### 1.3.6. 删除属性

​	可以使用 `delete` 关键字来删除 JSON 对象的属性：

```javascript
delete myObj.name3.site1;
```

​	也可以使用 `[]` 来删除 JSON 对象的属性：

```javascript
delete myObj.name3["site1"]
```

### 1.4. JSON 数组

#### 1.4.1. 数组语法

​	中括号 `[]` 保存的数组是值（**value**）的有序集合。一个数组以左中括号 `[` 开始， 右中括号 `]` 结束，值之间使用逗号 `,` 分隔。

```json
["value1", "value2", "value3"]
```

#### 1.4.2. 循环数组

​	可以使用 `for-in` 来循环访问数组：

```javascript
for (i in myObj.sites) {
    x += myObj.sites[i] + "<br>";
}
```

​	也可以使用 `for` 循环：

```javascript
for (i = 0; i < myObj.sites.length; i++) {
  x += myObj.sites[i] + "<br>";
}
```

#### 1.4.3. 嵌套数组

​	JSON 对象中数组可以包含另外一个数组，或者另外一个 JSON 对象：

```json
{ "name":"网站",
  "num":3,
  "sites": [
    { "name":"Google", "info":[ "Android", "Google 搜索", "Google 翻译" ] },
    { "name":"Runoob", "info":[ "菜鸟教程", "菜鸟工具", "菜鸟微信" ] },
    { "name":"Taobao", "info":[ "淘宝", "网购" ] }
  ]
}
```

#### 1.4.4. 修改数组值

```javascript
myObj.sites[1] = "Github";
```

#### 1.4.5. 删除数组元素

```javascript
delete myObj.sites[1]
```

### 1.5. JSON 方法

#### 1.5.1. JSON.parse()

```javascript
JSON.parse(text[, reviver])
```

- **text ：**必需， 一个有效的 JSON 字符串；
- **reviver ：** 可选，一个转换结果的函数， 将为对象的每个成员调用此函数。

##### Date 对象

​	JSON 不能存储 Date 对象，但是可以将其存储为字符串，需要的时候根据字符串转换为 Date 对象。

```javascript
var text = '{"nowDate":"2024-10-28"}';
var obj = JSON.parse(text);
// 此时 obj.nowDate 是一个字符串
obj.nowDate = new Date(obj.nowDate);
```

​	或者使用 `JSON.parse()` 方法的第二个参数 `reviver` ，转换 text 的对象成员：

```javascript
var text = '{"nowDate":"2024-10-28", "name":"wxss"}';
var obj = JSON.parse(text, fucntion(key, value) {
	for (key == "nowDate") {
  	return new Date(value);
  } else {
    return value;
  }
})
```

##### 解析函数

​	JSON 不允许包含函数，但你可以将函数作为字符串存储，之后再将字符串转换为函数。

```javascript
var text = '{ "name":"function", "func":"function () {return 1;}"}';
var obj = JSON.parse(text);
obj.func = eval("(" + obj.func + ")");
document.getElemntById("demo").innerHTML = obj.name + obj.func();
```

​	不建议在 JSON 中使用函数。

#### 1.5.2. JSON.stringify()

​	JSON 通常用于与服务端交换数据，在向服务器发送数据时一般是字符串，可以使用 `JSON.stringify()` 方法将 JavaScript 对象转换为字符串。

```javascript
JSON.stringify(value[, replacer[, space]])
```

- **value ：**必需， 要转换的 JavaScript 值（通常为对象或数组）；

- **replacer ：**可选，用于转换结果的函数或数组。

  - 若 `replacer` 为函数：则 `JSON.stringify` 将调用该函数，并传入每个成员的键和值。使用**返回值**而不是原始值，如果此函数返回 `undefined`，则排除成员，根对象的键是一个空字符串 `""`；

  - 若 `replacer` 为数组：则仅转换该数组中具有键值的成员。成员的转换顺序与键在数组中的顺序一样。当 value 参数也为数组时，将忽略 `replacer` 数组；

- **space ：**可选，文本添加缩进、空格和换行符。

  - 若 `space` 为数字：则返回值文本在每个级别缩进指定数目的空格；
  - 若 `space` 大于 10：则文本缩进 10 个空格；
  - `space` 也可以使用非数字，如：`\t`。

##### JavaScript 对象转换

```javascript
var myJSON = JSON.stringify(obj);
```

​	数组的转换类似。

##### 存储 Date 对象

```javascript
// JSON 包含 Date 对象
var obj = { "initDate":new Date() };
// 将 JSON 转化为 string
var myJSON = JSON.stringify(obj);
// 写入文档时，会将对象解析
document.getElementById("demo").innerHTML = myJSON;
```

##### 解析函数

​	JSON 不允许包含函数，`JSON.stringify()` 会删除 JavaScript 对象的函数，包括 key 和 value。可以在使用 `JSON.stringify()` 前将函数转化为字符串来避免。

```javascript
var obj = {  "alexa":function () {return 10000;} };
// 将函数转化为字符串
obj.alexa = obj.alexa.toString();
// 此时不会忽略函数
var myJSON = JSON.stringify(obj);
document.getElementById("demo").innerHTML = myJSON;
```











