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























