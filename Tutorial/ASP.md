# ASP 教程

## 1. ASP 基础语法

### 1.1. 向浏览器写输出

​	ASP 文件通常包含 HTML 标签，就像 HTML 文件。然而，ASP 文件也能包含服务器脚本，这些脚本被 `<% %>` 包围起来。服务器脚本再服务器上执行，可包含所选用的脚本语言的合法的表达式、语句、程序或者运算符。

#### 1.1.1. reponse.write 命令

​	`response.write` 命令用来向浏览器写输出。

```asp
<!DOCTYPE html>
<html>
<body>
<%
response.write("Hello World!")
%>
</body>
</html>
```

​	还有一种简写方法。

```asp
<%
="Hello World!"
%>
```

### 1.2. 使用 VBScript

​	可以在 ASP 中使用若干种脚本语言。然而，默认的脚本语言是 VBScript。

### 1.3. 使用 JavaScript

​	如果需要设置 JavaScript 为某个特定页面的默认脚本语言，必须在页面的顶部插入一行语言说明。

```asp
<%@ language="javascript" %>
<!DOCTYPE html>
<html>
<body>
<%
response.write("Hello World!")
%>
</body>
</html>
```

**注意**：与 VBScript 不同， JavaScript 对大小写敏感。必须根据 JavaScript 的需要使用不同的大小写字母编写 ASP 代码。

## 2. ASP 变量

### 2.1. 变量生存期

​	在子程序外声明的变量可被 ASP 文件中的任何脚本访问和修改；在子程序中声明的变量在每次子程序执行时被创建和撤销，子程序外的脚本无法访问和修改该变量。

​	如果需要声明供多个 ASP 文件使用的变量，可以将变量声明为 `session` 变量或者 `application` 变量。

#### 2.1.1. Session 变量

​	Session 变量用于存储单一用户的信息，并且对一个应用程序中的所有页面有效。

#### 2.1.2. Application

​	Application 变量同样对一个应用程序中的所有页面均有效，用于存储一个特定应用程序中所有用户的信息。

## 3. ASP 子程序

​	在 ASP 中，可以通过 VBScript 调用 JavaScript 子程序，反之亦然。

### 3.1. 子程序

```asp
<%
sub vbproc(num1, num2)
  response.write(num1*num2)
end sub
%>

<p>
  Result: <%call vbproc(3, 4)%>
</p>
```

​	通过 `<%@ language="language" %>` 这一行写在 `<html>` 标签上面，就可以使用另一种脚本语言来编写子程序或者函数。

```asp
<%@ language="javascript" %>
<!DOCTYPE html>
<html>
<head>
<%
  function jsproc(num1, num2)
  {
    Response.Write(num1, num2)
  }
%>
</head>
<body>
<p>
  Result: <% jsproc(3, 4) %>
</p>
</body>
</html>
```

### 3.2. VBScript 和 JavaScript 的不同

​	当从一个用 VBScript 编写的 ASP 文件中调用 VBScript 或者 JavaScript 子程序时，可以使用 `call` 关键字，后面跟着子程序名，参数必须包含在括号内，如果省略了 `call` 关键字，则参数不必包含在括号内。

​	当从一个 JavaScript 编写的 ASP 文件中调用 VBScript 或者 JavaScript 子程序时，必须在子程序后使用括号。

## 4. ASP 表单和用户输入

### 4.1. 用户输入

​	Request 对象可用于从表单取回用户信息。

#### 4.1.1. Request.QueryString

​	用于收集使用 `method="get"` 的表单中的值。

```asp
<!DOCTYPE html>
<html>
<body>
<form method="get" action="simpleform.asp">
  First Name: <input type="text" name="fname"><br>
  Last Name: <input type="text" name="lname"><br>
  <input type="submit" name="Submit">
</form>
  

</body>  
</html>

<!-- simpleform.asp file -->
<body>
Welcome
<%
  response.write(request.querystring("fname"))
  response.write(" " & request.querystring("lname"))
%>
</body>
```

#### 4.1.2. Request.Form

​	用于收集使用 `method="post"` 的表单中的值，用法与 Request.QueryString 类似。

### 4.2. 表单验证

​	只要可能，就尽量在浏览器上对用户的输入进行验证，以减少服务器的负载。如果用户输入的数据会保存在数据库中，那么应该使用服务器端验证。验证结果可以传回表单页面，而不是转至不同的页面，以便用户更容易地发现错误。

## 5. ASP Cookie

### 5.1. 创建 Cookie

​	`Response.Cookies` 命令用于创建 cookie，该命令必须出现在 `<html>` 标签之前。

```asp
<%
Response.Cookies("cookieName")="CookieName"
%>
```

### 5.2. 取回 Cookie 的值

​	`Request.Cookies` 命令用于取回 cookie 的值。

```asp
<%
fname=Request.Cookies("cookieName")
response.write("Firstname=" & fname)
%>
```

### 5.3. 带有键的 Cookie

​	如果一个 cookie 包含多个值的集合，就可以说 cookie 带有键（Keys）。

```asp
<%
Response.Cookies("user")("firstname")="Xss"
Response.Cookies("user")("lastname")="Wang"
Response.Cookies("user")("country")="CHN"
Response.Cookies("user")("age")=23
%>
```

## 6. ASP Session 

​	Session 对象用于存储关于用户会话（session）的信息，或者更改用户会话的设置。

### 6.1. 开始 Session

​	Session 开始于：

- 某个新用户请求了一个 ASP 文件，并且 `Global.asa` 文件引用了 `Session_OnStart` 子程序；
- 某个值存储在 Session 变量中；
- 某个用户请求了一个 ASP 文件，并且 `Global.asa` 使用 `<object>` 标签通过 session 的 `scope` 来实例化某个对象。

### 6.2. 结束 Session

​	如果用户没有在规定的时间内，在应用程序中请求或者刷新页面，session 就会结束，默认值为 20 分钟。如果需要自定义超时的时间间隔，可以使用 `Timeout` 属性。

```asp
<% Session.Timeout=5 %>
```

​	如果要立即结束 session，可以使用 Abandon 方法。

```asp
<% Session.Abandon %>
```

### 6.3. 存储与取回 Session 变量

​	Session 对象最大的优点是可以在其中存储变量，以供后续的网页读取，应用范围很广。

```asp
<!-- 存储变量 -->
<%
Session("username")="Donald Duck"
Session("age")=50
%>

<!-- 读取变量 -->
<%
Response.Write(Session("username"))
%>
```

### 6.4. 移除 Session 变量

​	`Contents` 集合包含所有的 session 变量，可以通过 `Remove` 方法来移除 session 变量。

```asp
<%
If Session.Contents("age")<18 Then
  Session.Contents.Remove("sale")
End If
%>
```

### 6.5. 遍历 Contents 集合

```asp
<%
Dim i
For Each i in Session.Contents
  Response.Write(i & "<br>")
Next
%>
```

### 6.6. 遍历 StaticObjects 集合

​	可以通过遍历集合，查看存储在 Session 对象中的所有对象的值。

```asp
<%
Dim i
For Each i in Session.StaticObjects
  Response.Write(i & "<br>")
Next
%>
```

## 7. ASP Application

​	在一起协同工作以完成某项任务的一组 ASP 文件成为一个应用程序。

### 7.1. 存储与取回 Application

```asp
<script language="vbscript" runat="server">

Sub Application_Onstart
	Application("vartime")=""
  Application("users")=1
End Sub

</script>

<% Response.Write(Application("users")) %>
```

### 7.2. 遍历 Contents 集合

```asp
<%
Dim i
For Each i in Application.Contents
  Response.Write(i & "<br>")
Next
%>
```

### 7.3. 遍历 StaticObject 集合

```asp
<%
Dim i
For Each i in Application.Contents
  Response.Write(i & "<br>")
Next
%>
```

### 7.4. 锁定与解锁

​	可以使用 `Lock` 方法来锁定应用程序，当应用程序锁定后，用户们就无法改变 Application 变量（除了正在访问 Application 变量的用户）。也可以使用 `Unlock` 方法来解锁应用程序。

```asp
<%
Application.Lock
'do some application object opreations
Application.Unlock
%>
```

## 8. ASP 引用文件

### 8.1. #include 指令

​	通过使用 `#include` 指令，可以在服务器执行 ASP 文件之前，把另一个 ASP 文件的内容插入到这个 ASP 文件中。

​	使用时需要将指令放于注释中。

```asp
<p>
  <!--#include file="time.inc" -->
</p>
```

### 8.2. 引用语法

```asp
<!--#include virtual="somefilename -->

or

<!--#include file="somefilename" -->
```

#### 8.2.1. Virtual 关键字

​	用来指示以虚拟目录开始的路径。

```asp
<!--#include virtual="/html/header.inc" -->
```

#### 8.2.2. File 关键字

​	用来指示一个相对路径，以引用文件同级目录开始。

```asp
<!--#include file="header.inc"
```

### 8.3. 提示和注释

​	如果用户尝试直接浏览 INC 文件，文件中的内容将被显示出来；如果需要隐藏内容，可以使用 `.asp` 文件。

**注意**：在脚本执行前，被引用的文件就会被处理和插入；不能在脚本分隔符之间包含文件引用，但可以截断脚本使用。

```asp
<% For i = 1 to n %>
<!--#include file="Hello.inc"
<% Next %>
```

## 9. Global.asa 文件

​	`Global.asa` 文件是一个可选文件，可包含被 ASP 应用程序中每个页面访问的对象、变量和方法的声明。其只能包含下列内容：

- `Application` 事件；
- `Session` 事件；
- `<object>` 声明；
- `TypeLibrary` 声明；
- `#include` 指令。

**注意**：`Global.asa` 文件必须存放在 ASP 应用程序的根目录中，而且每个应用程序只能有一个 `Global.asa` 文件。

### 9.1. 事件

​	在 `Global.asa` 中，可以包含四种类型的事件：

- `Application_OnStart`：此事件会在第一个用户调用 ASP 应用程序的第一个页面时发生，或是在 Web 服务器重启或者 `Global.asa` 文件被编辑之后发生；
- `Session_OnStart`：在 `Application_OnStart` 发生之后立即发生；
- `Session_OnEnd`：此事件会在每当用户结束 session 时发生，在规定的时间内如果用户没有请求任何页面，用户 session 就会结束；
- `Application_OnEnd`：此事件会在最后一个用户结束其 session 之后发生，像是 Web 服务器停止时。

```asp
<script>

Sub Application_OnStart
	'some code
End Sub

Sub Session_OnStart
	'some code
End Sub

Sub Session_OnEnd
	'some code
End Sub

Sub Application_OnEnd
	'some code
End Sub

</script>
```

**注意**：由于无法在 `Global.asa` 文件中使用 ASP 脚本分隔符 `<% %>` 插入脚本，需要把子例程放在 HTML 的 `<script>` 元素内部。

### 9.2. \<object> 声明

​	可通过使用 `<object>` 标签在 `Global.asa` 文件中创建带有 session 或者 application 作用域的对象。标签应位于 `<script>` 标签的外部。

```asp
<object runat="server" scope="scope" id="id" {progid="progID"|classid="classID"}>
....
</object>
```

| 参数    | 描述                                                        |
| ------- | ----------------------------------------------------------- |
| scope   | 设置对象的作用域，Session 或者 Application                  |
| id      | 为对象指定一个唯一的 id                                     |
| ProgID  | 与 ClassID 关联的 id，格式为 `[Vendor.]Component[.Version]` |
| ClassID | 为 COM 类对象指定一个唯一的 id                              |

**注意**：创建的对象可以在任何 ASP 文件中使用。

### 9.3. TypeLibrary 声明

​	TypeLibrary 是一个容器，装有对应于 COM 对象的 DLL 文件。通过在 `Global.asa` 文件中包含对 TypeLibrary 的调用，可以访问 COM 对象的常量，同时 ASP 代码也能更好的报告错误。

```asp
<!--METADATA TYPE="TypeLib"
file="filename" uuid="id" version="number" lcid="localeid"
-->
```

| 参数    | 描述                         |
| ------- | ---------------------------- |
| file    | 规定指向类型库的绝对路径     |
| uuid    | 规定类型库的唯一标识符       |
| version | 可选，用于选择版本           |
| lcid    | 可选，用于类型库的地区标识符 |

#### 9.3.1. 错误值

| 错误代码 | 描述             |
| -------- | ---------------- |
| ASP 0222 | 无效的类型库规范 |
| ASP 0223 | 没有找到类型库   |
| ASP 0224 | 无法加载类型库   |
| ASP 0225 | 无法包装类型库   |

### 9.4. 限定

​	关于可以在 `Global.asa` 文件中引用的内容的限定：

- 无法显示 `Global.asa` 文件中的文本，此文件无法显示信息；
- 只能在 `Application_OnStart` 和 `Application_OnEnd` 子例程中使用 Server 和 Application对象；在 `Session_OnEnd` 子例程中，可以使用 Server、Application 和 Session 对象；在 `Session_OnStart` 子例程中，可以使用任何内建的对象。
