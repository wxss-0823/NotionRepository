# Lua 教程

## 1. Lua 基本语法

### 1.1. 交互式编程

```shell
lua -i
# 或
lua
```

### 1.2. 脚本式编程

​	编写脚本，并保存为以 `.lua` 结尾的文件，并执行。

```shell
lua script_name.lua
```

### 1.3. 注释

#### 1.3.1. 单行注释

​	当行注释以两个连字符 `--` 开头，后面跟随的内容将被解释器忽略。

```lua
-- 注释
```

#### 1.3.2. 多行注释

​	多行注释以 `--[[` 开始，以 `]]` 结束。

```lua
--[[
	多行注释
]]
```

**注意：**Lua 不支持嵌套注释。

### 1.4. 标识符

​	Lua 标识符用于定义一个变量，标识符以一个字母 `A ~ Z` 或 `a ~ z` 或 `_` 开头后加上字母，下划线，数字。

### 1.5. 关键词

<table>
  <tr>
  	<td>and</td>
    <td>break</td>
    <td>do</td>
    <td>else</td>
  </tr>
  <tr>
  	<td>elseif</td>
    <td>end</td>
    <td>false</td>
    <td>for</td>
  </tr>
  <tr>
  	<td>function</td>
    <td>if</td>
    <td>in</td>
    <td>local</td>
  </tr>
  <tr>
  	<td>nil</td>
    <td>not</td>
    <td>or</td>
    <td>repeat</td>
  </tr>
  <tr>
  	<td>return</td>
    <td>then</td>
    <td>true</td>
    <td>until</td>
  </tr>
  <tr>
  	<td>while</td>
    <td>goto</td>
  </tr>
</table>

**注意：**以下划线开头连接一串大写字母的名字，如： `_VERSION`，被保留用于 Lua 内部全局变量。

### 1.6. 全局变量

​	在默认情况下，变量总是认为是全局的。全局变量不需要声明，给一个变量赋值后即创建了这个全局变量，访问一个没有初始化的变量也不会出错，会得到结果 `nil` 。

​	如果需要删除一个全局变量，只需要将其赋值为 `nil` 。

## 2. Lua 数据类型

| 数据类型 | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| nil      | 只有值 nil 属于该类，表示一个无效值                          |
| boolean  | 包含两个值：false 和 true                                    |
| number   | 表示双精度类型的实浮点数                                     |
| string   | 字符串由一对双引号或单引号来表示                             |
| function | 由 C 或 Lua 编写的函数                                       |
| userdata | 表示任意存储在变量中的 C 数据结构                            |
| thread   | 表示执行的独立线路，用于执行协同程序                         |
| table    | Lua 中的表是一个关联数组（associative arrays），数组的索引可以是数字、字符串或表类型，创建通过"构造表达式"来完成，最简单构造表达式是 `{}` ，用来创建一个空表 |

### 2.1. nil

​	nil 类型表示一种没有任何有效值，它只有一个值（nil）。对于全局变量和 table，nil 还有一个删除作用，给全局变量和 table 赋一个 nil 值，等同于把它们删掉。

### 2.2. boolean

​	boolean 类型只有两个可选值：true 或者 false，Lua 把 nil 也看做 false，其他都为 true，数字 0 也为 true。

### 2.3. number

​	Lua 默认只有一种 number 类型：double 类型。

### 2.4. String

​	字符串由一对双引号或单引号来表示，也可以用 `[[]]` 来表示一块字符串。在对一个数字字符串进行算术操作时，Lua 会尝试将这个数字字符串转成一个数字。字符串连接使用的是 `..` 。

### 2.5. table

​	在 Lua 里，table 的创建是通过“构造表达式”来完成，用 `{}` 创建一个空表，也可以在表里添加一些数据，直接初始化表。

- Lua 表实际上是一个关联数组，数组的索引可以是数字或者是字符串；
- Lua 表的数组从 1 开始，没有指定索引的元素，一次排列；
- Lua 表不会固定长度大小，有数据添加时，table 长度自动增长，没初始化的表都是 nil 。

### 2.6. function

​	Lua 中，函数被看作第一类值（First-Class Value），函数可以存在变量里。function 可以以匿名函数的方式通过参数传递。

### 2.7. thread

​	Lua 里，最主要的线程是协同程序（coroutine），它与线程（thread）类似，拥有独立的栈、局部变量和指令指针，可以跟其他协同程序共享全局变量；区别在于，线程可以同时多个运行，而协同程序任意时刻只能运行一个，并且处于运行状态的协同程序只有被挂起（suspend）时才会暂停。

### 2.8. userdata

​	userdata 是一种用户自定义类型，用于表示一种由应用程序或者 C/C++ 语言库所创建的语言，可以将 C/C++ 的任意数据类型的数据存储到 Lua 变量中调用。

## 3. Lua 变量

​	变量在使用前，需要在代码中进行声明，即创建该变量。Lua 变量有三种类型：全局变量、局部变量、表中的域。

- 全局变量：Lua 中的变量全是全局变量，包括语句块和函数内的变量；
- 局部变量：使用关键字 `local` 显式的声明为局部变量，作用域从声明位置到语句块结束。

### 3.1. 赋值语句

​	赋值是改变一个变量的值和改变表域的最基本的方法，Lua 可以对多个变量同时赋值，变量列表与值列表用逗号分隔，赋值语句右边的值会依次赋给左边的变量。

​	Lua 在遇到赋值语句时会先计算右边的所有值，再执行赋值操作，所以可以直接使用 `x, y = y, x`  交换变量。当变量个数与值个数不一致时，Lua 会一直以变量个数为基础，补足 nil 或者忽略多余的值。

**注意**：应尽可能使用局部变量，避免命名冲突，其次访问局部变量的速度比全局变量快。

### 3.2. 索引

​	对 table 元素的索引，可以使用 `[]`，当索引为字符串时，也可以使用 `.` 简化。

## 4. Lua 循环

### 4.1. 循环处理方式

| 循环类型       | 描述                                          |
| -------------- | --------------------------------------------- |
| while          | 条件为 true 时，执行                          |
| for            | 重复执行指定语句，重复次数可在 for 语句中控制 |
| repeat...until | 重复执行循环，直到指定条件为真                |
| 循环嵌套       | 可以在循环内嵌套一个或多个循环语句            |

### 4.2. 循环控制语句

| 控制语句 | 描述                                           |
| -------- | ---------------------------------------------- |
| break    | 退出当前循环或语句，并开始脚本执行紧跟着的语句 |
| goto     | 将程序的控制点转移到一个标签 `::label::` 处    |

### 4.3. 无限循环

​	循环体条件永远为 true，循环语句就会永远执行下去。

```lua
while(true) do
	print("Execuate forever")
end
```

## 5. Lua 流程控制

### 5.1. 控制结构语句

| 语句      | 描述                                                  |
| --------- | ----------------------------------------------------- |
| if        | 由一个布尔表达式作为条件判断，其后紧跟语句块          |
| if...else | 可以与 else 语句搭配使用，在 if 表达式为 false 时执行 |
| if 嵌套   | 可以在 if 或 else 中使用一个或多个 if 或 else if 语句 |

## 6. Lua 函数

### 6.1. 函数定义

```lua
optional_function_scope function function_name(arg1, arg2, arg3 ...)
  -- function_body
  return result_params_comma_sepreated
end
```

- `optional_function_scope`：该参数是可选的，用于指定函数是全局的还是局部的，默认是全局函数，需要使用关键字 `local` 声明为局部函数；
- `function_name`：指定函数名称；
- `arg1, arg2, arg3 ...`：函数参数，以逗号隔开，也可以不带参数；
- `function_body`：函数体，函数需要执行的代码语句块；
- `result_params_comma_seperated`：函数返回值，多个值以逗号隔开。

### 6.2. 多返回值

​	Lua 函数可以返回多个结果值，`return` 后列出要返回的列表即可返回多值。

### 6.3. 可变参数

​	Lua 函数可以接收可变数目的参数，在函数列表中使用 `...` 表示函数有可变的参数列表，固定参数必须放在变长参数之前。

​	通常在遍历变长参数时，只需要使用 `{...}` ，将变长参数存入一个表，然而考虑到变长参数中可能会包含一些 nil，可以使用 `select` 函数获取参数列表。

- `select("#", ...)`：返回可变参数的长度；
- `select(n, ...)`：用于返回从起点 n 开始到结束位置的所有参数列表。

## 7. Lua 运算符

### 7.1. 算术运算符

| 操作符 | 描述 |
| ------ | ---- |
| `+`    | 加法 |
| `-`    | 减法 |
| `*`    | 乘法 |
| `/`    | 除法 |
| `%`    | 取余 |
| `^`    | 乘幂 |
| `-`    | 负号 |
| `//`   | 整除 |

### 7.2. 关系运算符

| 操作符 | 描述                 |
| ------ | -------------------- |
| `==`   | 检测两个值是否相等   |
| `~=`   | 检测两个值是否不相等 |
| `>`    | 大于                 |
| `<`    | 小于                 |
| `>=`   | 大于或等于           |
| `<=`   | 小于或等于           |

### 7.3. 逻辑运算符

| 操作符 | 描述   |
| ------ | ------ |
| `and`  | 逻辑与 |
| `or`   | 逻辑或 |
| `not`  | 逻辑非 |

### 7.4. 其他运算符

| 操作符 | 描述           |
| ------ | -------------- |
| `..`   | 连接字符串     |
| `#`    | 返回字符串长度 |

## 8. Lua 字符串

​	Lua 字符串可以用三种方式表示：`''`，`""`，`[[]]`。

### 8.1. 字符串长度

​	可以使用 `string.len` 或者 `utf8.len` 函数，如果字符串包含中文，一般用 `utf8.len`，`string.len` 用于计算只包含 ASCII 字符串的长度。

### 8.2. 转义字符

| 转义字符 | 含义                          |
| -------- | ----------------------------- |
| `\a`     | 响铃（BEL）                   |
| `\b`     | 退格（BS）                    |
| `\f`     | 换页（FF）                    |
| `\n`     | 换行（LF）                    |
| `\r`     | 回车（CR）                    |
| `\t`     | 水平制表（HT）                |
| `\v`     | 垂直制表（VT）                |
| `\\`     | 代表反斜线字符                |
| `\'`     | 代表单引号字符                |
| `\"`     | 代表双引号字符                |
| `\0`     | 空字符（NULL）                |
| `\ddd`   | 1 到 3 位八进制数所代表的字符 |
| `\xhh`   | 1 到 2 位十六进制所代表的字符 |

### 8.3. 字符串函数

#### 8.3.1. 字符串截取

```lua
string.sub(s, i [, j])
```

- `s`：被截取的字符串；
- `i`：截取开始的位置；
- `j`：截取结束的位置，默认为 -1。

#### 8.3.2. 字符串大小写转换

```lua
string.upper(s)
string.lower(s)
```

#### 8.3.3. 字符串查找与反转

```lua
string.find(string, "certain_string")
string.reverse(string)
```

#### 8.3.4. 字符串格式化

```lua
string.format("format_string", arg1, arg2, ...)
```

- `%c`：接受一个数字，并将其转化为 ASCII 码表中对应的字符；
- `%d`，`%i`：接受一个数字，并将其转化为有符号的整数格式；
- `%o`：接受一个数字，并将其转化为八进制数格式；
- `%u`：接受一个数字，并将其转化为无符号整数格式；
- `%x`：接受一个数字，并将其转化为十六进制数格式，使用小写字母；
- `%X`：接受一个数字，并将其转化为十六进制数格式，使用大写字母；
- `%e`：接受一个数字，并将其转化为科学计数法格式，使用小写字母 e；
- `%E`：接受一个数字，并将其转化为科学计数法格式，使用大写字母 E；

- `%f`：接受一个数字，并将其转化为浮点数格式；
- `%g/%G`：接受一个数字，并将其转化为 `%e/%E` 和 `%f` 中较短的一种格式；
- `%q`：接受一个字符串，并将其转化为可安全地被 Lua 编译器读入的格式；
- `%s`：接受一个字符串，并按照给定的参数格式化该字符串；

​	为了进一步细化格式，可以在 `%` 后添加参数，参数将以如下顺序读入：

- `+`：表示数字转义符让正数显示正号；
- `0`：占位符，在指定字符宽度时使用，不填时默认是空格；
- `-`：对齐表示，默认是右对齐，`-` 表示左对齐；
- `n`：字符宽度数值；
- `.n`：小数位数/字符串裁剪。

#### 8.3.5. 字符与整数相互转化

```lua
-- 字符串转整数
string.byte("string", n)
-- 整数转字符串
string.char(num)
```

#### 8.3.6. 其他常用函数

```lua
-- 字符串长度
string.len(string)
-- 字符串复制 n 次
string.rep(string, n)
```

### 8.4. 匹配模式

​	Lua 中的匹配模式直接用常规的字符串来描述，用于模式匹配函数 `string.find`，`string.gmatch`，`string.gsub`，`string.match`。

#### 8.4.1. 匹配语法

- `.`：与任何字符配对；
- `%a`：与任何字母配对；
- `%c`：与任何控制符配对；
- `%d`：与任何数字配对；
- `%l`：与任何小写字母配对；
- `%p`：与任何标点（punctuation）配对；
- `%s`：与空白字符配对；
- `%u`：与任何大写字母配对
- `%w`：与任何字母/数字配对
- `%x`：与任何十六进制数配对；
- `%z`：与任何代表 0 的字符配对；
- `%x`：此处的 x 代表非字母非数字字符，用于处理表达式中有功能的字符；
- `[...]`：与任何 `[]` 中包含的字符类配对；
- `[^...]`：与任何 `[]` 中不包含的字符类配对。

​	特殊字符在匹配模式中，不与 `%` 连用，可以表示不同的含义：

- `*`：匹配零或多个该类字符，匹配尽可能长的串；
- `+`：匹配一个或多个该类字符；
- `-`：匹配零或多个该类字符，匹配尽可能短的串；
- `?`：匹配零或多个该类的字符，只要有可能，它会匹配一个；
- `%n`：这里的 n 可以从 1 到 9，匹配一个等于 n 号捕获物的字串；
- `%bxy`：x 和 y 是两个明确的字符，读到 x 就加一，读到 y 就减一，最终结束处的 y 是第一个记数到 0 的 y；
- `%f[set]`：set 表示匹配模式，只有在当前字符符合要求，上一个字符不符合要求时，通过探测。

#### 8.4.2. 模式

​	指一个模式条目的序列，由匹配语法连接构成，在模式最前面加上符号 `^` ，将锚定从字符串开始处做匹配，在模式最后面加上符号 `$`，将锚定从字符串结尾处开始匹配。

#### 8.4.3. 捕获

​	模式可以在内部用小括号括起，表示当前模式的子模式，这些子模式被称为捕获物，当匹配成功时，由捕获物匹配到的字符串中的字串将被保存起来用于未来的用途，捕获物以它们左括号的次序来编号。

​	例如：模式 `(a*(.)%w(%s*))` ，`a*(.)%w(%s*)` 匹配的部分，保存在第一个捕获物中；`.` 匹配到的字符是 2 号捕获物，`%s*` 匹配的字符是 3 号捕获物。

## 9. Lua 数组

​	数组，就是相同数据类型的元素按一定顺序排列的集合，可以是一维数组和多维数组。实际上，Lua 中并没有专门的数组类型，而是使用一种被称为 table 的数据结构来实现数组的功能。Lua 数组的索引键值可以使用整数表示，索引值从 1 开始，数组的大小不固定。

### 9.1. 一维数组

```lua
-- 创建数组
myArray = {val1, val2, val3, ...}
-- 获取数组长度
length = #myArray
-- 删除数组的第 n 个元素
table.remove(myArray, n)
-- 添加元素
myArray[n] = valn
```

### 9.2. 多维数组

​	数组中的每个元素是一个数组。

```lua
-- 初始化一维数组
arrar = {}
for i = 1, 3 do
  -- 初始化二维数组
  array[i] = {}
  for j = 1, 3 do
    array[i][j] = i * j
  end
end
```

## 10. Lua 迭代器

​	迭代器是一种对象，能够用来遍历标准模板库容器中的部分或全部元素，

### 10.1. 泛型 for 迭代器

​	执行流程：

1. 初始化，计算 `in` 后面表达式的值，表达式应该返回迭代函数，迭代对象，状态变量；
2. 将迭代对象和状态变量作为参数，调用迭代函数；
3. 将迭代函数的返回值赋给变量列表；
4. 判断返回值是否为 `nil`，不是则重新以当前的键值作为状态变量，调用迭代函数；
5. 是 `nil` ，则结束迭代。

### 10.2. 无状态迭代器

​	无状态迭代器指不需要保留任何状态，通过迭代函数自己保留状态。

### 10.3. 多状态迭代器

​	很多情况下，迭代器需要保存多个状态信息，而不是简单的状态变量和控制变量。可以使用闭包处理多个参数，也可以将多个参数封装到 table 中，作为迭代器的状态变量。

## 11. Lua Table

### 11.1. 构造

​	构造器是创建和初始化表的表达式。表是 Lua 特有的功能强大的东西。最简单的构造函数是 `{}`，用来创建一个空表。

```lua
table_name = {value1, value2, value3, ...}
```

### 11.2. 连接

​	可以使用 `concat()` 输出一个列表中元素连接成的字符串。

```lua
table.concat(table_name, connector, start, stop)
```

- `table_name`：表名；
- `connector`：连接符；
- `strat, stop`：连接起止位置。

### 11.3. 插入 & 移除

```lua
-- 插入
table.insert(table_name, pos, value)
```

- `pos`：插入的位置，缺省表示末尾插入；
- `value`：插入的值。

```lua
-- 移除
table.remove(table_name, pos)
```

### 11.4. 排序

​	使用 `sort()` 对 Table 进行排序。

```lua
table.sort(table_name)
```

## 12. Lua 模块与包

### 12.1. 模块定义

​	Lua 的模块是由变量、函数等已知元素组成的 table。因此创建一个模块，只需要把需要导出的常量、函数放入其中，最后返回这个 table 即可。

```lua
-- 文件名为 module.lua
-- 定义一个名为 module 的模块
module = {}

-- 定义一个常量
module.constant = "This is a constant"

-- 定义一个公有函数
function module.func1()
  ...
end

-- 定义一个私有函数
local function func2()
  ...
end

return module
```

### 12.2. 模块引入

​	Lua 提供一个名为 `require` 的函数来加载模块。

```lua
require("module_name")
```

#### 12.2.1. 引用别名

​	可以给加载的模块定义一个别名，方便调用。

```lua
local m = require("module_name")
```

#### 12.2.2. 加载机制

​	对于自定义的模块，函数 `require` 又自己的文件路径加载策略，它会尝试从 Lua 文件或 C 程序库中加载模块。当 Lua 启动会，会以环境变量 `LUA_PATH` 的值来初始化环境变量，如果没有找到该环境变量，则使用一个编译时定义的默认路径来初始化。

​	如果找过文件，则会调用 `package.loadfile` 来加载模块；搜索的文件路径是从全局变量 `package.cpath` 获取，而这个变量通过环境变量 `LUA_PATH` 来初始化；加载 C 模块是搜索 so 或 dll 类型的文件，如果找得到，就通过 `package.loadlib` 来加载它。

### 12.3. C 包

​	与在 Lua 中写包不同，C 包在使用以前必须首先加载并连接。Lua 在一个 `loadlib` 函数内提供了所有的动态连接的功能。

```lua
-- 使用 assert 返回错误
local f = assert(loadlib(absolute_path, initial_func))
-- 真正打开库
f()
```

- `absolute_path`：库文件的绝对路径；
- `initial_func`：初始化函数。

​	`loadlib` 函数加载指定库，并连接到 Lua，但是并不打开库，也就是没有调用初始化函数，它返回初始化函数，并可以直接在 Lua 中调用它，如果加载动态库或者查找初始化代码出错，`loadlib` 将返回 nil 和错误信息。

​	如果把库文件所在目录加入到 `LUA_PATH` 中，也可以使用 `require` 函数加载 C 库。

## 13. Lua Metatable

​	Metatable，即元表，是一种用于解释或扩展表内信息的同类表。Lua 提供了元表，用以实现 table 的复杂行为。

### 13.1. 设置 & 获取元表

```lua
-- Set metatable
setmetatable(table_name, metatable_name)
-- Get metatable
getmetatable(talbe_name)
```

### 13.2. Metamathod

​	元表中的一些特殊键会表示一种特殊的方法。

#### 13.2.1. __index 元方法

​	当 table 没有对应键，Lua 会在该表的 metatable 中寻找 `__index` 键。如果 `__index` 键中包含一个表格，Lua 会在表格中查找对应键；如果 `__index` 包含一个函数的话，Lua 会将 table 和 键作为参数传递给函数。

```lua
setmetatable({}, {__index = {key = value}})
-- __index contains function
setmetatable({key1 = val1}, {__index = 
  function(t, k)
    if k == val2 then
      return t.key1 .. val2
    else
      return nil
    end
  end
})
```

#### 13.2.2. __newindex 元方法

​	`__newindex` 元方法用来对表更新，`__index` 元方法用来对表访问。当给一个 table 缺少的索引赋值，解释器就会查找 `__newindex` 元方法。类似地，`__newindex` 接收 table，函数，或者 nil 作为参数，如果包含一个表格，则在这个表格中赋值；如果包含一个函数，则将 table，键，值作为参数传递给函数。

```lua
setmetatable({}, {__newindex = {})
-- __newindex contains function
setmetatable({}, {__newindex = 
  function(t, k, v)
        ...
  end
)
```

#### 13.2.3. 操作符元方法

##### 加操作

​	通过给元表添加 `__add` 元方法，定义表的加操作。

```lua
setmetatable({}, {
  __add = function(t1, t2)
    ...
  end
})
```

##### 操作符元方法定义表

| 模式       | 描述 |
| ---------- | ---- |
| `__add`    | `+`  |
| `__sub`    | `-`  |
| `__mul`    | `*`  |
| `__div`    | `/`  |
| `_mod`     | `%`  |
| `__unm`    | `-`  |
| `__concat` | `..` |
| `__eq`     | `==` |
| `__lt`     | `<`  |
| `__le`     | `<=` |

#### 13.2.4. __call 元方法

​	该方法在 Lua 使用 table 调用一个值时调用。

```lua
t1 = setmetatable({}, {__call = 
  function(t1, t2)
    ...
  end
})

-- invoke
t1(t2)
```

#### 13.2.5. __tostring 元方法

​	该方法在 Lua 尝试输出一个表时调用。

```lua
t1 = setmetatable({}, {__tostring = 
  function(t1)
    ..
  end
})

-- invoke
print(t1)
```

## 14. Lua Coroutine

### 14.1. 协同定义

​	Lua 协同程序（Coroutine）与线程比较类似：拥有独立的堆栈，独立的局部变量，独立的指令指针，同时又与其他协同程序共享全局变量和其他大部分东西。

​	协同程序可以理解为一种特殊的线程，可以暂停和恢复其执行，从而允许非抢占式的多任务处理。

### 14.2. 基本语法

​	协同程序由 `coroutine` 模块提供支持。

| 方法                  | 描述                                             |
| --------------------- | ------------------------------------------------ |
| `coroutine.create()`  | 创建 Coroutine，参数是一个函数                   |
| `coroutine.resume()`  | 重启 Coroutine，唤醒函数调用                     |
| `coroutine.yield()`   | 挂起 Coroutine                                   |
| `coroutine.status()`  | 查看 Coroutine 的状态：dead，suspanded，running  |
| `coroutine.wrap()`    | 创建 Coroutine，返回一个函数，调用就进入协同程序 |
| `coroutine.running()` | 返回正在运行的 Coroutine 的线程号                |

## 15. Lua 文件 I/O

​	Lua I/O 库用于读取和处理文件，分为简单模式、完全模式。简单模式与 C 一样，完全模式需要使用外部的文件句柄，以面向对象的形式，将所有的文件操作定义为文件句柄的方法。

### 15.1. 简单模式

```lua
file = io.open(filename [, mode])
```

| mode | description                                                  |
| ---- | ------------------------------------------------------------ |
| r    | 以只读方式打开文件，文件必须存在                             |
| w    | 打开只写文件，若文件存在，则清空，若不存在，则创建           |
| a    | 以附加的方式打开只写文件，若文件不存在，则创建，若存在，则追加 |
| r+   | 以可读可写的方式打开文件，文件必须存在                       |
| w+   | 打开可读可写文件，与 w 类似                                  |
| a+   | 打开可读可写文件，与 a 类似                                  |
| b    | 二进制模式打开文件                                           |
| +    | 表示对文件就可以读也可以写                                   |

### 15.2. 完全模式

​	如果需要在同一时间处理多个文件，需要使用 `file:function_name` 代替 `io.function_name` 方法。

## 16. Lua 错误处理

### 16.1. 语法错误

​	语法错误通常是由于对程序的组件使用不当引起的，比运行错误更简单，可以很快的解决。

### 16.2. 运行错误

​	运行错误是程序可以正常执行，但是会输出报错信息。

### 16.3. 错误处理

​	可以使用 `assert()` 和 `error()` 函数来处理错误。

```lua
assert(..., message)
```

​	`assert` 首先检查第一个参数，若没问题，不做任何事情；否则，以第二个参数作为错误信息抛出。

```lua
error(message [, level])
```

​	`error` 会终止正在执行的函数，并返回 message 的内容作为错误信息，并且通过 level 决定附加到错误信息头部的内容。

- `level = 1`：默认，调用 error 的位置（文件 + 行号）；
- `level = 2`：调用 error 函数的函数；
- `level = 0`：不添加错误位置信息。

### 16.4. 包装代码

​	Lua 中处理错误，可以使用 `pcall`，`xpcall`，`debug` 来包装需要执行的代码，根据函数的返回状态判断是否有错误发生，并进行错误处理。

#### 16.4.1. pcall

​	`pcall` 接受一个函数和要传递给后者的参数，并执行。如果无错误，返回 `true`，如果有错误，返回 `error` ，`errorinfo`。

```lua
if pcall(function_name, ...) then
  -- no error
else
  -- error
end
```

​	`pcall` 以一种保护模式调用第一个参数，因此可以捕获函数执行中的任何错误，但是会在返回时，销毁调用栈的部分内容。

#### 16.4.2. xpcall

​	Lua 提供了 `xpcall` 函数，该函数接收第二个参数，错误处理函数，当错误发生时，Lua 会在调用栈销展开前调用错误函数。因此 `xpcall` 函数可以使用 `debug` 库来获取额外的错误信息。

- `debug.debug`：提供一个 Lua 提示符，让用户来检查错误的原因；
- `debug.traceback`：根据调用栈来构建一个扩展的错误信息。

```lua
xpcall(function_name, ... , errorhandlefunction_name)
```

## 17. Lua Debug

​	Lua 提供了 Debug 库用于提供创建自定义调试器的功能。

### 17.1. Debug 库

| 方法                                       | 描述                                                         |
| ------------------------------------------ | ------------------------------------------------------------ |
| `debug()`                                  | 进入用户交互模式，运行用户输入的字符串；输入一行仅包含 `cont` 的字符串将结束这个函数 |
| `getfenv(object)`                          | 返回对象的环境变量                                           |
| `gethook(optional thread)`                 | 返回三个表示线程钩子设置的值：当前钩子函数、当前钩子掩码、当前钩子计数 |
| `getinfo([thread,] f [, what])`            | 返回关于一个函数信息的表，可以直接提供该函数，也可以用数字 f 表示函数在调用栈的层次：0 表示当前函数，1 表示调用 `getinfo` 的函数 |
| `debug.getlocal([thread,] f, local)`       | 返回在栈的 f 层处函数的索引为 local 的局部变量的名字和值     |
| `getmetatalbe(value)`                      | 把给定索引指向的值的元表压入堆栈                             |
| `getregistry()`                            | 返回注册表，这是一个预定义的表，可以用来保存任何 C 代码想保存的 Lua 的值 |
| `getupvalue(f, up)`                        | 返回函数 f 的第 up 个上值的名字和值                          |
| `sethook([thread,] hook, mask [, count])`  | 将一个函数作为钩子函数设入，字符串 mask 和数字 count 决定钩子在何时调用，掩码有：`c` ，每当 Lua 调用一个函数时，调用钩子；`r` ，每当 Lua 从一个函数返回时，调用钩子；`l` ，每当 Lua 进入新的一行时，调用钩子 |
| `setlocal([thread,] level, local, value)`  | 将 value 赋给栈上第 level 层函数的第 local 个局部变量        |
| `setmetatable(value, talbe)`               | 将 value 的元表设为 table                                    |
| `setupvalue(f, up, value)`                 | 将 value 设为函数 f 的第 up 个上值                           |
| `traceback([thread,] [message [, level]])` | message 不为空或字符串，则返回 message；否则，返回调用栈的栈回溯信息 |

## 18. Lua 垃圾回收

​	Lua 采用了自动内存管理，这意味着不用操心新创建的对象需要的内存如何分配，也不用考虑在对象不再被使用后如何释放内存。

​	Lua 运行了一个垃圾收集器来收集所有死对象，即在 Lua 中不可能再访问到的对象，来完成自动内存管理的工作。

​	Lua 实现了一个增量标记-扫描收集器，它使用两个数字来控制垃圾收集循环：垃圾收集器间歇率和垃圾收集器步进倍率。这两个数字都是用百分数作为单位。

​	垃圾收集器间歇率控制着收集器需要再开启新的循环前等待多久。增大这个值会减少收集器的积极性。当这个值小于 100 时，收集器在开启新的循环前不会有等待；设置这个值为 200，会让收集器等到总内存使用量达到之前的两倍时才开始新的循环。

​	垃圾收集器步进倍率控制着收集器运作速度相对于内存分配速度的倍率。增大这个值不仅会让收集器更加积极，还会增加每个增量步骤的长度。不要把这个值设置得小于 100，否则收集器工作得太慢，永远都干不完一个循环。默认值是 200，表示收集器以内存分配得两倍速工作。

### 18.1. 垃圾回收器函数

​	Lua 提供了函数 `collectgarbage([opt, [arg]])` 来控制自动内存管理。

- `collectgarbage("collect")`：做一次完整得垃圾收集循环，通过参数 opt，它提供了一组不同的功能；
- `collectgarbage("count")`：以 K 字节数为单位返回 Lua 使用的内存总数；
- `collectgarbage("restart")`：重启垃圾收集器的自动运行；
- `collectgarbage("setpause")`：将 arg 设置为收集器的间歇率，返回间歇率的前一个值；
- `collectgarbage("step")`：单步运行垃圾收集器，步长大小由 arg 控制。传入 0 时，收集器步进一步；传入非 0 值，收集器收集相当于 Lua 分配对应 K 字节内存的工作；如果收集器结束一个循环，返回 true；
- `collectgarbage("stop")`：停止垃圾收集器的运行，在调用重启前，收集器只会因显示的调用运行。

## 19. Lua 面向对象

​	Lua 中的类可以通过 table 和 function 模拟出来，至于继承，可以通过 metatable 模拟出来。

```lua
-- 创建一个表作为类
ClassName = {}
-- 创建类的构造函数
function ClassName:new(...)
  -- 创建一个新的空表作为类的实例
  local obj = {}
  -- 标识实例继承类的方法
  setmetatable(obj, self)
  -- 确保可以正确调用类的方法和属性
  self.__index = self
  -- 初始化实例，调用初始化函数
  obj:init(...)
  return obj
end
-- 创建类的方法
function ClassName:mathod(...)
  ...
end
```

## 20. Lua 数据库访问

​	Lua 提供了数据库的操作库 LuaSQL，可以通过安装数据库驱动来连接到数据库。LuaSQL 可以通过 Luarocks 安装，安装教程详见：[Luarocks 安装](https://www.cnblogs.com/icefoxhz/articles/16809098.html) 。

​	配置完成对应的项目结构后，需要在 VS 环境中执行命令，否则报错 `mingw32-gcc 不是内部或外部命令`。本机 VS 路径 `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2022\Visual Studio Tools\VC`。

​	此时应该可以正常安装包文件，用如下命令测试是否配置成功。

```shell
luarocks --lua-version=5.4 --tree=D:/Users/ProjectFiles/Codes/VSCode/Lua/lua/luarocks install luasocket --verbose
```

​	再确认配置成功后，尝试下载 luasql-mysql 依赖。使用如下命令：

```shell
luarocks --tree=D:/Users/ProjectFiles/Codes/VSCode/Lua/lua/luarocks install luasql-mysql MYSQL_INCDIR=D:/Users/MySQL/mysql-9.1.0-winx64/include MYSQL_LIBDIR=D:/Users/MySQL/mysql-9.1.0-winx64/lib --verbose
```

​	安装成功后即可开始访问连接数据库。

### 20.1. 问题

#### 20.1.1. [未解决]无法获取授权的问题

> Error: Could not fetch rock file: Failed creating temporary directory luarocks-rock-luafilesystem-1.8.0-1: Failed setting permission exec for all

​	根据 `--verbose` 的跟踪显示，Lua 5.3.6 问题出现在代码 `fs.execute_quiet(vars.ICACLS .. " " .. fs.Q(filename) .. " /inheritance:d /grant:r \"%USERNAME%\":" .. perms)` 处，显示 Wang 不可用。

​	然而，这应该与命名的空格无关，Lua 5.4.2 相同的代码可以执行。不同之处在于，Lua 5.4.2 执行代码 `fs.execute_quiet(vars.ICACLS .. " " .. fs.Q(filename) .. " /inheritance:d /grant:r *S-1-1-0:" .. others_perms)`，而 Lua 5.3.6 执行代码 `fs.execute_quiet(vars.ICACLS .. " " .. fs.Q(filename) .. " /inheritance:d /grant:r Everyone:" .. others_perms)` 。

​	一些可能的解决方案详见：[Github-luarock #1312](https://github.com/luarocks/luarocks/issues/1312) 。

#### 20.1.2. [未解决]无法解析外部符号的问题

> 正在创建库 C:\Users\WANGXI~1\AppData\Local\Temp\luarocks_build-LuaSQL-MySQL-2.6.0-3-4254843\luasql\mysql.lib 和对象 C:\Users\WANGXI~1\AppData\Local\Temp\luarocks_build-LuaSQL-MySQL-2.6.0-3-4254843\luasql\mysql.exp
> mysqlclient.lib(my_init.obj) : error LNK2019: 无法解析的外部符号 \_\_imp_RegCloseKey，函数 "bool \_\_cdecl win32_have_tcpip(void)" (?win32_have_tcpip@@YA_NXZ) 中引 用了该符号
> mysqlclient.lib(my_init.obj) : error LNK2019: 无法解析的外部符号 \_\_imp_RegEnumValueA，函数 "void \_\_cdecl win_init_registry(void)" (?win_init_registry@@YAXXZ) 中引用了该符号
> mysqlclient.lib(my_init.obj) : error LNK2019: 无法解析的外部符号 \_\_imp_RegOpenKeyExA，函数 "bool \_\_cdecl win32_have_tcpip(void)" (?win32_have_tcpip@@YA_NXZ) 中 引用了该符号
> mysqlclient.lib(common.obj) : error LNK2019: 无法解析的外部符号 \_\_imp_EqualSid，函数 "public: bool \_\_cdecl Sid::operator==(class Sid const &)const " (??8Sid@@QEBA_NAEBV0@@Z) 中引用了该符号
> mysqlclient.lib(common.obj) : error LNK2019: 无法解析的外部符号 \_\_imp_GetTokenInformation，函数 "public: _\_cdecl Sid::Sid(void *)" (??0Sid@@QEAA@PEAX@Z) 中引用 了该符号
> mysqlclient.lib(common.obj) : error LNK2019: 无法解析的外部符号 \_\_imp_IsValidSid，函数 "public: bool \_\_cdecl Sid::is_valid(void)const " (?is_valid@Sid@@QEBA_NXZ) 中引用了该符号
> mysqlclient.lib(common.obj) : error LNK2019: 无法解析的外部符号 \_\_imp_LookupAccountNameW，函数 "public: \_\_cdecl Sid::Sid(wchar_t const *)" (??0Sid@@QEAA@PEB_W@Z) 中引用了该符号C:\Users\WANGXI~1\AppData\Local\Temp\luarocks_build-LuaSQL-MySQL-2.6.0-3-4254843\luasql\mysql.dll : fatal error LNK1120: 7 个无法解析的外部命令

​	上述报错调用的函数位于系统动态链接库，理应存在，并且检索存在，对应的目录均添加至环境变量，并且 `mysql.h` 文件包含 `#include <windows.h>` 。已尝试更换不同版本的 `mysqlclient.lib` 文件，均无效，推测与 mysql 版本无关；已尝试更换不同编译器版本的 `lua54.lib` 文件，均无效，推测与 Lua lib 版本无关。

​	Luarocks 版本 3.11.1， Lua 版本 5.4.2，VS 版本 17.12.1，Linker 版本 14.42.34433.0，Lua lib，dll & include 版本 `lua-5.4.2_Win64_dll[14|17]_lib`，Luarocks 经过验证，可以正常运行，推测可能由于 Luasql 内部原因无法自动适配 mysql，可能需要手动编译源码。

##### 手动编译

​	根据命令行打印信息，获取编译过程，进入源码的根目录后，依次执行：

```shell
# manually compile rockspec to install luasql-mysql
luarocks --tree=D:/Users/ProjectFiles/Codes/VSCode/Lua/lua/luarocks install "D:\Program Files (x86)\Microsoft Edge\luasql-2.6.0\luasql-2.6.0\rockspec\luasql-mysql-2.6.0-1.rockspec" MYSQL_INCDIR=D:/Users/MySQL/mysql-9.1.0-winx64/include MYSQL_LIBDIR=D:/Users/MySQL/mysql-9.1.0-winx64/lib

# process luasql.o
mingw32-gcc -O2 -c -o src/luasql.o -ID:/Users/ProjectFiles/Codes/VSCode/Lua/lua/include src/luasql.c -ID:/Users/MySQL/mysql-9.1.0-winx64/include

# process ls_mysql.o
mingw32-gcc -O2 -c -o src/ls_mysql.o -ID:/Users/ProjectFiles/Codes/VSCode/Lua/lua/include src/ls_mysql.c -ID:/Users/MySQL/mysql-9.1.0-winx64/include

# link .o for dll
mingw32-gcc  -shared -o luasql/mysql.dll src/luasql.o src/ls_mysql.o -LD:/Users/MySQL/mysql-9.1.0-winx64/lib -lmysqlclient D:\Users\ProjectFiles\Codes\VSCode\Lua\lua\lua54.dll -lm
```

​	最新的源码仍然无法通过编译，猜测问题并不在 Luasql 内部，可能是 MySQL Lib 的问题，详细指令见 [Github-Command](https://github.com/wxss-0823/Codes/blob/master/VSCode/Lua/lua/command/Luarocks_sh-cmd.sh) 。

##### 更换 Lib

​	更换了多个 Lib，还是存在外部命令无法识别的报错，尝试在 `mysql.c` 中加入 `#include <windows.h>` ，无效，无法识别操作系统的环境库。猜测可能新版的 Luasql 与 mysql 间存在适配问题，Luasql 长达近 1 年未更新，更新日志也未详细描述兼容的版本。



