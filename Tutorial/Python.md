# Python 笔记


## Python3 教程

### 基础语法

#### 1.  基本数据类型

不需要声明，但是使用前必须赋值。变量没有类型，”类型“是指内存中的对象的类型。

##### 多个变量赋值

```python
a = b = c = 1
a, b, c = 1, 2, "wxss"
```

##### 标准数据类型

- Number（数字）
- String（字符串）
- bool（布尔类型）
- List（列表）
- Tuple（元组）
- Set（集合）
- Dictionary（字典）

- **不可变数据（3 个）：**Number（数字）、String（字符串）、Tuple（元组）；
- **可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）。

##### Number （数字）

支持 **int、float、bool、complex**

可以使用内置函数 **isinstance()、type()**

isinstance 和 type 的区别在于：

- type()不会认为子类是一种父类类型。
- isinstance()会认为子类是一种父类类型。

###### 数值运算

| 运算符号 |   类型   |
| :------: | :------: |
|    +     |   加法   |
|    -     |   减法   |
|    *     |   乘法   |
|    /     |   除法   |
|    //    | 取整除法 |
|    %     | 取余除法 |
|    **    |   乘方   |

##### String（字符串）

用单引号 `''` 或双引号 `""` 包围。同时使用反斜杠 `\` 转义特殊字符。

###### 字符串截取

```python
变量[头下标:尾下标]
```

###### 字符串格式化

```python
f"...{}"
"...{:.2f}".format(1.125)
"...%.2f" % 1.125
```

##### bool（布尔类型）

- 只有 **True**，**False**；
- 比较时分别视作1和0；
- 可以与逻辑运算符一起使用
- 转换为其他类型

##### List（列表）

写在 `[]` 之间。

###### 列表截取

```python
变量[头下标：尾下标]
```

- 以**0**开始，**-1**表示末尾。

**注意：**

- List写在方括号之间，元素用逗号隔开。
- 和字符串一样，list可以被索引和切片。
- List可以使用+操作符进行拼接。
- List中的元素是可以改变的。

##### Tuple（元组）

写在 `()` 之间。可以包含可变元素。

**注意：**

- 与字符串一样，元组的元素不能修改。
- 元组也可以被索引和切片，方法一样。
- 注意构造包含 0 或 1 个元素的元组的特殊语法规则。
- 元组也可以使用+操作符进行拼接。

##### Set（集合）

一种无序、可变的数据类型，用于储存唯一的元素。元素不会重复，可以进行交集、并集、差集等操作。

- 集合用大括号 `{}` 表示，元素之间用 `,` 分隔；
- 可以使用 `set()` 函数创建；
- 创建一个空集合必须使用 `set()` 而不是 `{}` ，因为 `{}` 用来创建一个空字典。

```python
parame = {value01,value02,...}
或者
set(value)
```

##### Dictionary（字典）

字典用 **{ }** 标识，它是一个无序的 **键(key) : 值(value)** 的集合。键(key)必须使用不可变类型。在同一个字典中，键(key)必须是唯一的。

**注意：**

- 字典是一种映射类型，它的元素是键值对。
- 字典的关键字必须为不可变类型，且不能重复。
- 创建空字典使用 **{ }**。

##### bytes（类型）

表示的是不可变的二进制序列。通常用于处理二进制数据，比如图像文件、音频文件、视频文件等等。

- 创建 bytes 对象的方式：
  - 使用 b 前缀；
  - 使用 bytes() 函数；
  - 比较操作时，需要使用相应的整数值。`ord()` 用于将字符转换为相应的整数值。

#### 2.  数据类型转换

##### 隐式类型转换

在隐式类型转换中，Python 会自动将一种数据类型转换为另一种数据类型，不需要干预。

##### 显式类型转换

在显式类型转换中，用户将对象的数据类型转换为所需的数据类型。 我们使用 int()、float()、str() 等预定义函数来执行显式类型转换。

#### 3. 注释

##### 单行注释

以 `#` 开头。

##### 多行注释

1. 单引号 `'''`

2. 双引号 `"""`

#### 4.  运算符

##### 成员运算符

| 运算符 | 描述                                                    |
| :----- | :------------------------------------------------------ |
| in     | 如果在指定的序列中找到值返回 True，否则返回 False。     |
| not in | 如果在指定的序列中没有找到值返回 True，否则返回 False。 |

##### 身份运算符

| 运算符 | 描述                                        |
| :----- | :------------------------------------------ |
| is     | is 是判断两个标识符是不是引用自一个对象     |
| is not | is not 是判断两个标识符是不是引用自不同对象 |

#### 5.  数字（Number）

- **整型(int)** - 通常被称为是整型或整数，是正或负整数，不带小数点。布尔(bool)是整型的子类型。
- **浮点型(float)** - 浮点型由整数部分与小数部分组成，浮点型也可以使用科学计数法表示。
- **复数( (complex))** - 复数由实数部分和虚数部分构成，可以用a + bj,或者complex(a,b)表示， 复数的实部a和虚部b都是浮点型。

##### 数字类型转换

- **int(x)** 将x转换为一个整数。
- **float(x)** 将x转换到一个浮点数。
- **complex(x)** 将x转换到一个复数，实数部分为 x，虚数部分为 0。
- **complex(x, y)** 将 x 和 y 转换到一个复数，实数部分为 x，虚数部分为 y。x 和 y 是数字表达式。

#### 6.  字符串

##### 访问字符串中的值

使用方括号 **[]** 

##### 字符串截取

```python
变量[头下标:尾下标]
```

- 从前面：从0开始；从后面：从-1开始。
- `[0:]` ：表示从0开始直到结尾。
- `[:-1]` ：表示从-1开始直到开头。

##### 字符串更新

使用 + 拼接字符串。

##### 字符串格式化

使用与 C 中 sprintf 函数一样的语法

```python
print("我叫 %s 今年 %d 岁！" %("小明", 10))
```

##### 三引号

允许一个字符串跨多行，字符串中可以包含换行符、制表符以及其他特殊字符。

##### f-string

以 **f** 开头，后面跟着字符串，字符串中的表达式用大括号 {} 包起来，它会将变量或表达式计算后的值替换进去。

#### 7.  列表

用 `[]` 创建列表。

##### 访问列表中的值

与字符串的索引一样，列表索引从 **0** 开始，第二个索引是 **1**，依此类推。

##### 更新列表

可以使用 append() 方法来添加列表项。

##### 删除列表元素

可以使用 del 语句来删除列表的的元素。

##### 列表截取与拼接

列表截取与字符串操作类似。

##### 嵌套列表

使用嵌套列表即在列表里创建其它列表。

##### 列表比较

列表比较需要引入 **operator** 模块的 **eq**。

#### 8.  元组

元组创建很简单，只需要在括号中添加元素，并使用逗号隔开即可。

##### 访问元组

元组可以使用下标索引来访问元组中的值。

##### 修改元组

元组中的元素值是不允许修改的，但我们可以对元组进行连接组合。

```python
tuple3 = tuple1 + tuple2
```

##### 删除元组

元组中的元素值是不允许删除的，但我们可以使用del语句来删除整个元组。

##### 元组索引，截取

因为元组也是一个序列，所以我们可以访问元组中的指定位置的元素，也可以截取索引中的一段元素。

#### 9.  字典

字典是另一种可变容器模型，且可存储任意类型对象。每个键值 **key=>value** 对用冒号 **:** 分割，每个对之间用逗号(**,**)分割，整个字典包括在花括号 **{}** 中。

```python
d = {key1 : value1, key2 : value2, key3 : value3 }
```

##### 创建空字典

- 使用大括号 **{ }** 创建空字典。
- 使用内建函数 **dict()** 创建字典。

##### 访问字典里的值

把相应的键放入到方括号中。

##### 修改字典

向字典添加新内容的方法是增加新的键/值对，修改或删除已有键/值对。对相应的键赋值，如果不存在键，则添加信息；如果存在键则修改信息。

##### 删除字典元素

能删单一的元素也能清空字典，清空只需一项操作。

```python
del dict['Key']  # 删除键 'Key'
dict.clear()     # 清空字典
del dict         # 删除字典
```

##### 字典键的特性

字典值可以是任何的 python 对象，既可以是标准的对象，也可以是用户定义的，但键不行。

两个重要的点需要记住：

1. 不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住，

2. 键必须不可变，所以可以用数字，字符串或元组充当，而用列表就不行，如下实例

#### 10.  集合

可以使用大括号 **{ }** 创建集合，元素之间用逗号 **,** 分隔， 或者也可以使用 **set()** 函数创建集合。

##### 创建格式

```python
parame = {value01,value02,...}
或者
set(value)
```

##### 添加元素

```python
set.add( x )
set.update( x )
```

- add：仅接收一个元素，且是不可变类型。可以添加一个元组元素。
- update：接收多个元素，用都好隔开，但是元组、列表会被拆开，以每个元素添加，列表仅添加键值。

##### 移除元素

```python
set.remove( x )
set.discard( x )	# 元素不存在不会产生错误
set.pop() 		# 随机删除一个
```

##### 计算集合元素个数

```python
len(s)
```

##### 清空集合

```python
set.clear()
```

##### 判断元素是否在集合中

```python
x in set
```

#### 11.  条件控制

通过一条或多条语句的执行结果（True 或者 False）来决定执行的代码块。

##### if 语句

```python
if condition_1:
    statement_block_1
elif condition_2:
    statement_block_2
else:
    statement_block_3
```

##### if 嵌套

```python
if 表达式1:
    语句
    if 表达式2:
        语句
    elif 表达式3:
        语句
    else:
        语句
elif 表达式4:
    语句
else:
    语句
```

##### match...case

```python
match subject:
    case <pattern_1>:
        <action_1>
    case <pattern_2>:
        <action_2>
    case <pattern_3>:
        <action_3>
    case _:
        <action_wildcard>
```

- **case _:** 当其他 case 都无法匹配时，匹配这条，保证永远会匹配成功。

#### 12.  循环语句

##### while 循环

```python
while 判断条件(condition)：
    执行语句(statements)
```

##### 无限循环

通过设置条件表达式永远不为 false 来实现无限循环。

##### while 循环使用 else 语句

如果 while 后面的条件语句为 false 时，则执行 else 的语句块。

```python
while <expr>:
    <statement(s)>
else:
    <additional_statement(s)>
```

##### 简单语句组

类似 if 语句的语法，如果 while 循环体中只有一条语句，你可以将该语句与 while 写在同一行中。

```python
while (condition): <statement(s)>
```

##### for 语句

可以遍历任何可迭代对象。

```python
for <variable> in <sequence>:
    <statements>
```

##### for...else

for...else 语句用于在循环结束后执行一段代码。

```python
for item in iterable:
    # 循环主体
else:
    # 循环结束后执行的代码
```

##### range() 函数

如果需要遍历数字序列，可以使用内置 range() 函数。它会生成数列。

```python
range(start, end, step)
```

##### break 和 continue 语句及循环中的 else 子句

- **break** 语句可以跳出 for 和 while 的循环体。如果从 for 或 while 循环中终止，任何对应的循环 else 块将不执行。

- **continue** 语句被用来跳过当前循环块中的剩余语句，然后继续进行下一轮循环。

- 循环语句可以有 else 子句，它在穷尽列表(以for循环)或条件变为 false (以while循环)导致循环终止时被执行，但循环被 break 终止时不执行。

##### pass 语句

空语句，是为了保持程序结构的完整性。不做任何事情，一般用做占位语句。

#### 13.  推导式

##### 列表推导式

```python
[表达式 for 变量 in 列表] 
[表达式 for 变量 in 列表 if 条件]
```

##### 字典推导式

```python
{ key_expr: value_expr for value in collection }
{ key_expr: value_expr for value in collection if condition }
```

##### 集合推导式

```python
{ expression for item in Sequence }
{ expression for item in Sequence if conditional }
```

##### 元组推导式

```python
(expression for item in Sequence )
(expression for item in Sequence if conditional )
```

#### 14.  迭代器与生成器

##### 迭代器

迭代器是一个可以记住遍历的位置的对象。从集合的第一个元素开始访问，直到所有的元素被访问完结束。迭代器只能往前不会后退。

迭代器有两个基本的方法：**iter()** 和 **next()**。

##### 创建一个迭代器

把一个类作为一个迭代器使用需要在类中实现两个方法 __iter__() 与 __next__() 

- \__iter__() 方法返回一个特殊的迭代器对象。
- \__next__() 方法（Python 2 里是 next()）会返回下一个迭代器对象。

##### StopIteration

用于标识迭代的完成，防止出现无限循环的情况。

##### 生成器

使用了 **yield** 的函数被称为生成器（generator）。

- **yield** 是一个关键字，用于定义生成器函数，生成器函数是一种特殊的函数，可以在迭代过程中逐步产生值，而不是一次性返回所有结果。

- 每次调用生成器的 **next()** 方法或使用 **for** 循环进行迭代时，函数会从上次暂停的地方继续执行，直到再次遇到 **yield** 语句。这样，生成器函数可以逐步产生值，而不需要一次性计算并返回所有结果。

- 调用一个生成器函数，返回的是一个迭代器对象。

#### 15.  函数

##### 定义一个函数

- 函数代码块以 **def** 关键词开头，后接函数标识符名称和圆括号 **()**。
- 任何传入参数和自变量必须放在圆括号中间，圆括号之间可以用于定义参数。
- 函数的第一行语句可以选择性地使用文档字符串—用于存放函数说明。
- 函数内容以冒号 **:** 起始，并且缩进。
- **return [表达式]** 结束函数，选择性地返回一个值给调用方，不带表达式的 return 相当于返回 None。

##### 语法

```python
def 函数名（参数列表）:
    函数体
```

##### 函数调用

函数的基本结构完成以后，可以通过另一个函数调用执行。

##### 参数传递

- **不可变类型：**类似 C++ 的值传递，如整数、字符串、元组。如 fun(a)，传递的只是 a 的值，没有影响 a 对象本身。如果在 fun(a) 内部修改 a 的值，则是新生成一个 a 的对象。
- **可变类型：**类似 C++ 的引用传递，如 列表，字典。如 fun(la)，则是将 la 真正的传过去，修改后 fun 外部的 la 也会受影响。

##### 参数

##### 必需参数

必需参数须以正确的顺序传入函数。调用时的数量必须和声明时的一样。

##### 关键字参数

关键字参数和函数调用关系紧密，函数调用使用关键字参数来确定传入的参数值。

##### 默认参数

调用函数时，如果没有传递参数，则会使用默认参数。即可选参数。

##### 不定长参数

可能需要一个函数能处理比当初声明时更多的参数。这些参数叫做不定长参数，和上述 2 种参数不同，声明时不会命名。

```python
def functionname([formal_args,] *var_args_tuple ):
   "函数_文档字符串"
   function_suite
   return [expression]
```

参数带两个星号 ***\***基本语法如下：

```python
def functionname([formal_args,] **var_args_dict ):
   "函数_文档字符串"
   function_suite
   return [expression]
```

- 如果单独出现星号 *****，则星号 ***** 后的参数必须用关键字传入。

#### 16.  lambda（匿名函数）

lambda 函数是一种小型、匿名的、内联函数，它可以具有任意数量的参数，但只能有一个表达式。

- 匿名函数不需要使用 **def** 关键字定义完整函数。

- 通常用于编写简单的、单行的函数，通常在需要函数作为参数传递的情况下使用，例如在 map()、filter()、reduce() 等函数中。

##### lambda 语法格式：

```python
lambda arguments: expression
```

#### 17.  模块

##### import 语句

```python
import module1[, module2[,... moduleN]
```

##### from … import 语句

 from 语句让你从模块中导入一个指定的部分到当前命名空间中。

```python
from modname import name1[, name2[, ... nameN]]
```

##### from … import * 语句

把一个模块的所有内容全都导入到当前的命名空间。

```python
from modname import *
```

##### \__name__属性

一个模块被另一个程序第一次引入时，其主程序将运行。如果想在模块被引入时，模块中的某一程序块不执行，可以用\__name__属性来使该程序块仅在该模块自身运行时执行。

```python
if __name__ == '__main__':
```

##### dir() 函数

内置的函数 dir() 可以找到模块内定义的所有名称。以一个字符串列表的形式返回。

##### 包

包是一种管理 Python 模块命名空间的形式，采用"点模块名称"。

##### 从一个包中导入*

Python 会进入文件系统，找到这个包里面所有的子模块，然后一个一个的把它们都导入进来。

```python
__all__ = ["echo", "surround", "reverse"]
```

- 如果包定义文件 **__init__.py** 存在一个叫做 **__all__** 的列表变量，那么在使用 **from package import \*** 的时候就把这个列表中的所有名字作为包内容导入。

#### 18.  输入输出

##### 输出格式美化

- 表达式语句、 print() 函数、使用文件对象的 write() 方法

- 输出的形式：可以使用 str.format() 函数来格式化输出值。
  - format() 中使用了关键字参数, 那么它们的值会指向使用该名字的参数。

- 将输出的值转成字符串：

  - **str()：** 函数返回一个用户易读的表达形式。

  - **repr()：** 产生一个解释器易读的表达形式。
    - 字符串对象的 rjust() 方法, 它可以将字符串靠右, 并在左边填充空格。

##### 旧式字符串格式化

**%** 操作符也可以实现字符串格式化。 它将左边的参数作为类似 **sprintf()** 式的格式化字符串, 而将右边的代入, 然后返回格式化后的字符串。

##### 读取键盘输入

提供了 [input() 内置函数](https://www.runoob.com/python3/python3-func-input.html)从标准输入读入一行文本，默认的标准输入是键盘。

##### 读和写文件

open() 将会返回一个 file 对象。

```python
open(filename, mode)
```

- filename：包含了你要访问的文件名称的字符串值。
- mode：决定了打开文件的模式：只读，写入，追加等。所有可取值见如下的完全列表。这个参数是非强制的，默认文件访问模式为只读(r)。

##### 文件对象的方法

###### f.read()

调用 f.read(size)，这将读取一定数目的数据, 然后作为字符串或字节对象返回。

###### f.readline()

f.readline() 会从文件中读取单独的一行。换行符为 '\n'。f.readline() 如果返回一个空字符串, 说明已经已经读取到最后一行。

###### f.readlines()

f.readlines() 将返回该文件中包含的所有行。如果设置可选参数 sizehint, 则读取指定长度的字节, 并且将这些字节按行分割。

###### f.write()

f.write(string) 将 string 写入到文件中, 然后返回写入的字符数。

###### f.tell()

f.tell() 用于返回文件当前的读/写位置（即文件指针的位置）。文件指针表示从文件开头开始的字节数偏移量。

###### f.seek()

如果要改变文件指针当前的位置, 可以使用 f.seek(offset, from_what) 函数。

- seek(x,0) ： 从起始位置即文件首行首字符开始移动 x 个字符
- seek(x,1) ： 表示从当前位置往后移动x个字符
- seek(-x,2)：表示从文件的结尾往前移动x个字符

###### f.close()

调用 f.close() 来关闭文件并释放系统的资源。

###### with 关键字

```python
with open('/tmp/foo.txt', 'r') as f:
    read_data = f.read()
```

- 结束后，会帮你正确的关闭文件。

###### pickle 模块

实现了基本的数据序列和反序列化。

- 通过pickle模块的序列化操作我们能够将程序中运行的对象信息保存到文件中去，永久存储。

- 通过pickle模块的反序列化操作，我们能够从文件中创建上一次程序保存的对象。

```python
pickle.dump(obj, file, [,protocol])
```

#### 19.  File(文件) 方法

##### open() 方法

用于打开一个文件，并返回文件对象。

#### 20.  OS 文件/目录方法

[常用的方法](https://www.runoob.com/python3/python3-os-file-methods.html)

#### 21.  错误和异常

##### 异常处理

###### try/except

- 首先，执行 try 子句（在关键字 try 和关键字 except 之间的语句）。
- 如果没有异常发生，忽略 except 子句，try 子句执行后结束。
- 如果在执行 try 子句的过程中发生了异常，那么 try 子句余下的部分将被忽略。如果异常的类型和 except 之后的名称相符，那么对应的 except 子句将被执行。
- 如果一个异常没有与任何的 except 匹配，那么这个异常将会传递给上层的 try 中。

同时处理多个异常，这些异常将被放在一个括号里成为一个元组，例如:

```python
except (RuntimeError, TypeError, NameError):
  pass
```

###### try/except...else

**try/except** 语句还有一个可选的 **else** 子句，如果使用这个子句，那么必须放在所有的 except 子句之后。else 子句将在 try 子句没有发生任何异常的时候执行。

###### try/except/finally 语句

finally 语句无论是否发生异常都将执行最后的代码。

##### 抛出异常

使用 raise 语句抛出一个指定的异常。

```python
raise [Exception [, args [, traceback]]]
```

##### 用户自定义异常

可以通过创建一个新的异常类来拥有自己的异常。异常类继承自 Exception 类，可以直接继承，或者间接继承，

##### with 关键字

- **with** 语句用于异常处理，封装了 **try…except…finally** 编码范式，提高了易用性。

- **with** 语句使代码更清晰、更具可读性， 它简化了文件流等公共资源的管理。

```python
# 使用 try/except 语句
file = open('./test_runoob.txt', 'w')
try:
    file.write('hello world')
finally:
    file.close()
# 使用 with 语句
with open('./test_runoob.txt', 'w') as file:
    file.write('hello world !')
```

#### 22.  面向对象

##### 类定义

```python
class ClassName:    
    <statement-1>    
    ...   
    <statement-N>
```

##### 类对象

- 类对象支持两种操作：属性引用和实例化。

- 类有一个名为 __init__() 的特殊方法（**构造方法**），该方法在类实例化时会自动调用。

##### self代表类的实例，而非类

类的方法必须有一个额外的**第一个参数名称**，按照惯例它的名称是 self。

##### 类的方法

在类的内部，使用 **def** 关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 self，且为第一个参数，self 代表的是类的实例。

##### 继承

```python
class DerivedClassName(BaseClassName):
    <statement-1>
	...
    <statement-N>
```

- 子类（派生类 DerivedClassName）会继承父类（基类 BaseClassName）的属性和方法。

BaseClassName（实例中的基类名）必须与派生类定义在一个作用域内。除了类，还可以用表达式，基类定义在另一个模块中时这一点非常有用。

```python
class DerivedClassName(modname.BaseClassName):
```

##### 多继承

```python
class DerivedClassName(Base1, Base2, Base3):    
    <statement-1>
    ...
    <statement-N>
```

- 需要注意圆括号中父类的顺序，若是父类中有相同的方法名，而在子类使用时未指定，python从左至右搜索 即方法在子类中未找到时，从左到右查找父类中是否包含方法。

##### 方法重写

可以在子类重写你父类的方法。[super() 函数](https://www.runoob.com/python/python-func-super.html)是用于调用父类（超类）的一个方法。

##### 类的私有属性与方法

###### 类的私有属性

**__private_attrs**：两个下划线开头，声明该属性为私有，不能在类的外部被使用或直接访问。在类内部的方法中使用时 **self.__private_attrs**。

###### 类的私有方法

**__private_method**：两个下划线开头，声明该方法为私有方法，只能在类的内部调用 ，不能在类的外部调用。**self.__private_methods**。

##### 类的专有方法：

- **\__init__ :** 构造函数，在生成对象时调用
- **\__del__ :** 析构函数，释放对象时使用
- **\__repr__ :** 打印，转换
- **\__setitem__ :** 按照索引赋值
- **\__getitem__:** 按照索引获取值，类 + [] 等于调用该方法。
- **\__len__:** 获得长度
- **\__cmp__:** 比较运算
- **\__call__:** 函数调用
- **\__add__:** 加运算
- **\__sub__:** 减运算
- **\__mul__:** 乘运算
- **\__truediv__:** 除运算
- **\__mod__:** 求余运算
- **\__pow__:** 乘方

##### 运算符重载

可以对类的专有方法进行重载。

#### 23.  命名空间和作用域

##### 命名空间

命名空间(Namespace)是从名称到对象的映射，大部分的命名空间都是通过 Python 字典来实现的。

- **内置名称（built-in names**）， Python 语言内置的名称，比如函数名 abs、char 和异常名称 BaseException、Exception 等等。
- **全局名称（global names）**，模块中定义的名称，记录了模块的变量，包括函数、类、其它导入的模块、模块级的变量和常量。
- **局部名称（local names）**，函数中定义的名称，记录了函数的变量，包括函数的参数和局部定义的变量。（类中定义的也是）

###### 命名空间查找顺序

**局部的命名空间 -> 全局命名空间 -> 内置命名空间**。

###### 命名空间的生命周期

命名空间的生命周期取决于对象的作用域，如果对象执行完成，则该命名空间的生命周期就结束。

##### 作用域

作用域就是一个 Python 程序可以直接访问命名空间的正文区域。

- **L（Local）**：最内层，包含局部变量，比如一个函数/方法内部。
- **E（Enclosing）**：包含了非局部(non-local)也非全局(non-global)的变量。比如两个嵌套函数，一个函数（或类） A 里面又包含了一个函数 B ，那么对于 B 中的名称来说 A 中的作用域就为 nonlocal。
- **G（Global）**：当前脚本的最外层，比如当前模块的全局变量。
- **B（Built-in）**： 包含了内建的变量/关键字等，最后被搜索。

只有模块（module），类（class）以及函数（def、lambda）才会引入新的作用域，其它的代码块（如 if/elif/else/、try/except、for/while等）是不会引入新的作用域的，也就是说这些语句内定义的变量，外部也可以访问。

##### 全局变量和局部变量

定义在函数内部的变量拥有一个局部作用域，定义在函数外的拥有全局作用域。

##### global 和 nonlocal关键字

当内部作用域想修改外部作用域的变量时，用到 global 和 nonlocal 关键字。

- **global**：将内部变量声明为全局变量。
- **nonlocal**：将内部变量声明为外部变量。

### 高级教程

#### 1.  正则表达式

使用 **re** 模块来处理正则表达式。re 模块提供了一组函数，允许在字符串中进行模式匹配、搜索和替换操作。

##### re.match函数

```python
re.match(pattern, string, flags=0)
```

- pattern：匹配的正则表达式。
- string：要匹配的字符串。
- flags：标志位，用于控制正则表达式的匹配方式。[正则表达式修饰符 - 可选标志](https://www.runoob.com/python3/python3-reg-expressions.html#flags)

| 匹配对象方法 | 描述                                                         |
| :----------- | :----------------------------------------------------------- |
| group(num=0) | 匹配的整个表达式的字符串，group() 可以一次输入多个组号，在这种情况下它将返回一个包含那些组所对应值的元组。 |
| groups()     | 返回一个包含所有小组字符串的元组，从 1 到 所含的小组号。     |

##### re.search方法

re.search 扫描整个字符串并返回第一个成功的匹配。

```python
re.search(pattern, string, flags=0)
```

##### re.match & re.search

**re.match** 只匹配字符串的开始，如果字符串开始不符合正则表达式，则匹配失败，函数返回 None，而 **re.search** 匹配整个字符串，直到找到一个匹配。

##### 检索和替换

re 模块提供了 re.sub 用于替换字符串中的匹配项。

```python
re.sub(pattern, repl, string, count=0, flags=0)
```

- repl : 替换的字符串，也可为一个函数。
- count : 模式匹配后替换的最大次数，默认 0 表示替换所有的匹配。

##### compile 函数

compile 函数用于编译正则表达式，生成一个正则表达式（ Pattern ）对象，供 match() 和 search() 这两个函数使用。

```python
re.compile(pattern[, flags])
```

##### findall

在字符串中找到正则表达式所匹配的所有子串，并返回一个列表，如果有多个匹配模式，则返回元组列表，如果没有找到匹配的，则返回空列表。

```python
re.findall(pattern, string, flags=0)
或
pattern.findall(string[, pos[, endpos]])
```

- **pos** 可选参数，指定字符串的起始位置，默认为 0。
- **endpos** 可选参数，指定字符串的结束位置，默认为字符串的长度。

##### re.finditer

在字符串中找到正则表达式所匹配的所有子串，并把它们作为一个迭代器返回。迭代器里存放的是多个对象。

```python
re.finditer(pattern, string, flags=0)
```

##### re.split

split 方法按照能够匹配的子串将字符串分割后返回列表。

```python
re.split(pattern, string[, maxsplit=0, flags=0])
```

- **maxsplit**：分割次数，maxsplit=1 分割一次，默认为 0，不限制次数。

##### 正则表达式对象

###### re.RegexObject

re.compile() 返回 RegexObject 对象。

###### re.MatchObject

group() 返回被 RE 匹配的字符串。

- **start()** 返回匹配开始的位置
- **end()** 返回匹配结束的位置
- **span()** 返回一个元组包含匹配 (开始,结束) 的位置

#### 2.  SMTP 发送邮件

SMTP（Simple Mail Transfer Protocol）即简单邮件传输协议，它是一组用于由源地址到目的地址传送邮件的规则，由它来控制信件的中转方式。

##### 创建 STMP 对象

```python
import smtplib


smtpObj = smtplib.SMTP( [host [, port [, local_hostname]]] )
```

- **host**：SMTP 服务器主机。 你可以指定主机的ip地址或者域名如:runoob.com，这个是可选参数。
- **port**：如果你提供了 host 参数, 你需要指定 SMTP 服务使用的端口号，一般情况下SMTP端口号为25。
- **local_hostname**：如果SMTP在你的本机上，你只需要指定服务器地址为 localhost 即可。

##### 发送邮件

```python
smtpObj.sendmail(from_addr, to_addrs, msg[, mail_options, rcpt_options]
```

- **from_addr**：邮件发送者地址。
- **to_addrs**：字符串列表，邮件发送地址。
- **msg**：发送消息

#### 3.  多线程

常用的两个模块为：

- **_thread**
- **threading(推荐使用)**

##### 调用 _thread 模块

```python
_thread.start_new_thread ( function, args[, kwargs] )
```

- **function** - 线程函数。
- **args** - 传递给线程函数的参数，他必须是个tuple类型。
- **kwargs** - 可选参数。

###### while 1: pass

多线程运行时，不会等待调用函数中的循环执行完再跳出循环往下走，而是直接返回一个值 1 ，告诉程序往下走（报错除外）。

##### 线程模块

**_thread** 提供了低级别的、原始的线程以及一个简单的锁.

**threading** 模块提供的其他方法：

- **threading.currentThread()**：返回当前的线程变量。
- **threading.enumerate()**：返回一个包含正在运行的线程的list。正在运行指线程启动后、结束前，不包括启动前和终止后的线程。
- **threading.activeCount()**：返回正在运行的线程数量。

线程模块同样提供了Thread类来处理线程，Thread类提供了以下方法:

- **run()**：用以表示线程活动的方法。
- **start()**：启动线程活动。
- **join([time])**：设置等待时间，或者等待至线程中止。
- **isAlive()**：返回线程是否活动的。
- **getName()**：返回线程名。
- **setName()**：设置线程名。

##### 线程同步

如果多个线程共同对某个数据修改，则可能出现不可预料的结果，为了保证数据的正确性，需要对多个线程进行同步。

##### 线程优先级队列（ Queue）

Queue 模块中提供了同步的、线程安全的队列类。可以使用队列来实现线程间的同步。

#### 4.  日期和时间

提供了一个 time 和 calendar 模块可以用于格式化日期和时间。

##### 时间元组

| 序号 | 属性     | 值                                                           |
| :--- | :------- | :----------------------------------------------------------- |
| 0    | tm_year  | 2008                                                         |
| 1    | tm_mon   | 1 到 12                                                      |
| 2    | tm_mday  | 1 到 31                                                      |
| 3    | tm_hour  | 0 到 23                                                      |
| 4    | tm_min   | 0 到 59                                                      |
| 5    | tm_sec   | 0 到 61 (60或61 是闰秒)                                      |
| 6    | tm_wday  | 0 到 6 (0是周一)                                             |
| 7    | tm_yday  | 一年中的第几天，1 到 366                                     |
| 8    | tm_isdst | 是否为夏令时，值有：1(夏令时)、0(不是夏令时)、-1(未知)，默认 -1 |

## Python CGI 编程

### 1. HTTP 头部

​	它会发送给浏览器告诉浏览器文件的内容类型。

| 头                  | 描述                                                      |
| :------------------ | :-------------------------------------------------------- |
| Content-type:       | 请求的与实体对应的MIME信息                                |
| Expires: Date       | 响应过期的日期和时间                                      |
| Location: URL       | 用来重定向接收方到非请求URL的位置来完成请求或标识新的资源 |
| Last-modified: Date | 请求资源的最后修改时间                                    |
| Content-length: N   | 请求的内容长度                                            |
| Set-Cookie: String  | 设置 Http Cookie                                          |

### 2. CGI 环境变量

所有的CGI程序都接收以下的环境变量，这些变量在CGI程序中发挥了重要的作用：

| 变量名          | 描述                                                         |
| :-------------- | :----------------------------------------------------------- |
| CONTENT_TYPE    | 这个环境变量的值指示所传递来的信息的 MIME 类型               |
| CONTENT_LENGTH  | 这个环境变量在使用 POST 读取所输入的数据时必须使用           |
| HTTP_COOKIE     | 客户机内的 COOKIE 内容                                       |
| HTTP_USER_AGENT | 提供包含了版本数或其他专有数据的客户浏览器信息               |
| PATH_INFO       | 这个环境变量的值表示紧接在 CGI 程序名之后的其他路径信息，它常常作为 CGI 程序的参数出现 |
| QUERY_STRING    | 这个环境变量在使用 GET 读取所输入的信息时使用，跟在 CGI 程序名的后面，两者中间用一个问号 `?` 分隔 |
| REMOTE_ADDR     | 这个环境变量的值是发送请求的客户机的IP地址                   |
| REMOTE_HOST     | 这个环境变量的值包含发送 CGI 请求的客户机的主机名            |
| REQUEST_METHOD  | 提供脚本被调用的方法                                         |
| SCRIPT_FILENAME | CGI 脚本的完整路径                                           |
| SCRIPT_NAME     | CGI 脚本的的名称                                             |
| SERVER_NAME     | 这是你的 WEB 服务器的主机名、别名或IP地址                    |
| SERVER_SOFTWARE | 这个环境变量的值包含了调用 CGI 程序的 HTTP 服务器的名称和版本号 |

### 3. GET 和 POST 方法

#### 3.1. 使用 GET 方法传输数据

​	GET 方法发送编码后的用户信息到服务端，数据信息包含在请求页面的URL上，以 `?` 号分割。

```url
http://www.test.com/cgi-bin/hello.py?key1=value1&key2=value2
```

- GET 请求可被缓存；
- GET 请求保留在浏览器历史记录中；
- GET 请求可被收藏为书签；
- GET 请求不应在处理敏感数据时使用；
- GET 请求有长度限制；
- GET 请求只应当用于取回数据。

#### 3.2. 使用 POST 方法传递数据

​	使用 POST 方法向服务器传递数据是更安全可靠的，一些敏感信息，如：**用户密码**等，需要使用 POST 传输数据。POST 方法只需要修改对应属性 `method='post'` 即可。

### 4. CGI 中使用 Cookie

​	在 http 协议一个很大的缺点就是不对用户身份的进行判断，这样给编程人员带来很大的不便， 而 cookie 功能的出现弥补了这个不足。cookie 就是在客户访问脚本的同时，通过客户的浏览器，在客户硬盘上写入纪录数据 ，当下次客户访问脚本时取回数据信息，从而达到身份判别的功能，cookie 常用在身份校验中。

#### 4.1 cookie 语法

​	http cookie 的发送是通过 http 头部来实现的，他早于文件的传递，头部 set-cookie 的语法如下：

```html
Set-cookie:name=name;expires=date;path=path;domain=domain;secure 
```

- **name=name:** 需要设置 cookie 的值（name不能使用 `;` 和 `,` 号），有多个name值时用 `;` 分隔；
- **expires=date:** cookie 的有效期限，格式：`expires="Wdy,DD-Mon-YYYY HH:MM:SS"`；
- **path=path:** 设置 cookie 支持的路径，如果 path 是一个路径，则 cookie 对这个目录下的所有文件及子目录生效；
- **domain=domain:** 对 cookie 生效的域名；
- **secure:** 如果给出此标志，表示 cookie 只能通过 SSL 协议的 https 服务器来传递。

**注意：**cookie 的接收是通过设置环境变量 HTTP_COOKIE 来实现的，CGI 程序可以通过检索该变量获取 cookie 信息。

## 常用语法小记

- `*args` & `**kwargs`

  可选的参数输入：其中`*args`为元组类型，`**kwargs`为字典类型。

  在方法定义中用`kwargs.item[]`读取输入的参数，并根据键值执行相应的功能

- `class` & `def`

  `class`：定义类，其下可以包含多个方法，第一个方法一般为`__init__`；其下所有方法第一个参数必须为`self`，方便在将类实例化后的自我调用，且`self`不接收参数；

  `def`：定义方法，一定存在`return`

- 在方法实参中加入条件判定

```python
mpl_fonts = set(f.name for f in FontManager().ttflist)
```

- `print` ：`end` 关键字，用于将结果输出到同一行。

## 第三方库

### Requests

用于向服务器发送请求，并接收返回内容。

```python
response = requests.get(url, ...)
# 返回查询状态代码
response.status_code
# 返回 html 文本信息
response.text
```

### BeautifulSoup

用于查询 html 文件中的特定内容。

```python
# 初始化类
soup = BeautifulSoup(html, "html.parser")
# 在 html 中查找所有 span 块，且类名为title
all_titles = soup.findAll("span", attrs={"class": "title"})
```

### Numpy

内容



### Manim

#### 内容

#### 运行方法

```shell
# 终端输入
manim/manimgl foldername.py classname
```

### Matplotlib

- 画图中存在中文乱码的问题

```python
# 1.使用plt.rcParams
# 指定默认字体：解决plot不能显示中文问题
plt.rcParams['font.sans-serif'] = ['Microsoft YaHei']
# 解决保存图像是负号'-'显示为方块的问题
plt.rcParams['axes.unicode_minus'] = False

# 2.使用matplotlib.rc
# 查询当前系统所有字体
from matplotlib.font_manager import FontManager
import subprocess

mpl_fonts = set(f.name for f in FontManager().ttflist)

print('all font list get from matplotlib.font_manager:')
for f in sorted(mpl_fonts):
    print('\t' + f)
# 修改字体
import matplotlib
matplotlib.rc("font",family='YouYuan')
```

