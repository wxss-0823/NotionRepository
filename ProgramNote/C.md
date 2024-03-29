# C 笔记

### C 语言教程

#### 1.  数据类型

1. 基本数据类型：int；char；float；double。
2. 枚举类型：用来定义在程序中只能赋予其一定的离散整数值的变量。
3. void 类型：表示没有值的数据类型，通常用于函数返回值。
4. 派生类型：包括数组类型、指针类型和结构体类型。

##### 类型转换

类型转换是将一个数据类型的值转换为另一种数据类型的值。

C 语言中有两种类型转换：

- **隐式类型转换：**隐式类型转换是在表达式中自动发生的，无需进行任何明确的指令或函数调用。它通常是将一种较小的类型自动转换为较大的类型，例如，将int类型转换为long类型或float类型转换为double类型。隐式类型转换也可能会导致数据精度丢失或数据截断。
- **显式类型转换：**显式类型转换需要使用强制类型转换运算符（type casting operator），它可以将一个数据类型的值强制转换为另一种数据类型的值。强制类型转换可以使程序员在必要时对数据类型进行更精确的控制，但也可能会导致数据丢失或截断。

#### 2.  变量

##### 变量的定义

```c
type variable_list;
```

##### 变量初始化

```c
type variable_name = value;
```

##### 变量的声明

1. 需要建立存储空间：`int a`
2. 不需要建立存储空间：`extern int a`
3. 除非有 extern 关键字，否则都是变量的定义。

##### 左值和右值

1. **左值（lvalue）**：指向内存位置的表达式被称为左值。
2. **右值（rvalue）**：存储在内存中某些地址的数值。

#### 3.  常量

常量是固定值，在程序执行期间不会改变，又叫做字面量。定义后不能进行修改。

##### 整数常量

- 0x 或 0X 表示十六进制；
- 0 表示八进制；
- 不带前缀默认表示十进制。

##### 浮点常量

- 由整数部分、小数点、小数部分和指数部分组成

##### 字符常量

- 括在单引号中
- 有一些特定的转义字符

##### 定义常量

- 使用 **#define** 预处理器：可以在程序中定义一个常量。
- 使用 **const** 关键字：用于声明一个只读变量，即该变量的值不能在程序运行时修改。

###### 区别

- 替换机制：`#define` 是进行简单的文本替换，而 `const` 是声明一个具有类型的常量。`#define` 定义的常量在编译时会被直接替换为其对应的值，而 `const` 定义的常量在程序运行时会分配内存，并且具有类型信息。
- 类型检查：`#define` 不进行类型检查，因为它只是进行简单的文本替换。而 `const` 定义的常量具有类型信息，编译器可以对其进行类型检查。这可以帮助捕获一些潜在的类型错误。
- 作用域：`#define` 定义的常量没有作用域限制，它在定义之后的整个代码中都有效。而 `const` 定义的常量具有块级作用域，只在其定义所在的作用域内有效。
- 调试和符号表：使用 `#define` 定义的常量在符号表中不会有相应的条目，因为它只是进行文本替换。而使用 `const` 定义的常量会在符号表中有相应的条目，有助于调试和可读性。

#### 4.  存储类

##### auto 存储类

所有局部变量默认的存储类。定义在函数中的变量默认为 auto 存储类，这意味着它们在函数开始时被创建，在函数结束时被销毁。

##### register 存储类

用于定义存储在寄存器中而不是 RAM 中的局部变量。变量访问速度更快，但是不能直接取地址。

##### static 存储类

指示编译器在程序的生命周期内保持局部变量的存在，而不需要在每次它进入和离开作用域时进行创建和销毁。

- 静态变量只被初始化一次，即使被函数多次调用，值也不会重置。

##### extern 存储类

用以定义在其他文件中声明的全局变量或函数。不会为变量分配存储空间，只是指示编译器该变量在其他文件中定义。

- 提供一个全局变量的引用，对所有程序文件可见。对于无法初始化的变量，会把变量名指向一个之前定一个过的存储位置。

#### 5.  运算符

- 算术运算符
- 关系运算符
- 逻辑运算符
- 位运算符
- 赋值运算符
- 杂项运算符

#### 6.  判断

##### 判断语句

| 语句                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [if 语句](https://www.runoob.com/cprogramming/c-if.html)     | 一个 **if 语句** 由一个布尔表达式后跟一个或多个语句组成。    |
| [if...else 语句](https://www.runoob.com/cprogramming/c-if-else.html) | 一个 **if 语句** 后可跟一个可选的 **else 语句**，else 语句在布尔表达式为假时执行。 |
| [嵌套 if 语句](https://www.runoob.com/cprogramming/c-nested-if.html) | 您可以在一个 **if** 或 **else if** 语句内使用另一个 **if** 或 **else if** 语句。 |
| [switch 语句](https://www.runoob.com/cprogramming/c-switch.html) | 一个 **switch** 语句允许测试一个变量等于多个值时的情况。     |
| [嵌套 switch 语句](https://www.runoob.com/cprogramming/c-nested-switch.html) | 您可以在一个 **switch** 语句内使用另一个 **switch** 语句。   |

##### ? : 运算符(三元运算符)

```c
Exp1 ? Exp2 : Exp3;
```

#### 7.  循环

##### 循环类型

| 循环类型                                                     | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [while 循环](https://www.runoob.com/cprogramming/c-while-loop.html) | 当给定条件为真时，重复语句或语句组。它会在执行循环主体之前测试条件。 |
| [for 循环](https://www.runoob.com/cprogramming/c-for-loop.html) | 多次执行一个语句序列，简化管理循环变量的代码。               |
| [do...while 循环](https://www.runoob.com/cprogramming/c-do-while-loop.html) | 除了它是在循环主体结尾测试条件外，其他与 while 语句类似。    |
| [嵌套循环](https://www.runoob.com/cprogramming/c-nested-loops.html) | 您可以在 while、for 或 do..while 循环内使用一个或多个循环。  |

更多内容：[C while 和 do while 区别](https://www.runoob.com/w3cnote/c-while-and-do-while.html)

##### 循环控制语句

循环控制语句改变你代码的执行顺序。可以实现代码的跳转。

| 控制语句                                                     | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [break 语句](https://www.runoob.com/cprogramming/c-break-statement.html) | 终止**循环**或 **switch** 语句，程序流将继续执行紧接着循环或 switch 的下一条语句。 |
| [continue 语句](https://www.runoob.com/cprogramming/c-continue-statement.html) | 告诉一个循环体立刻停止本次循环迭代，重新开始下次循环迭代。   |
| [goto 语句](https://www.runoob.com/cprogramming/c-goto-statement.html) | 将控制转移到被标记的语句。但是不建议在程序中使用 goto 语句。 |

##### 无限循环

如果条件永远不为假，则循环将变成无限循环。**for** 循环在传统意义上可用于实现无限循环。由于构成循环的三个表达式中任何一个都不是必需的，您可以将某些条件表达式留空来构成一个无限循环。

```c
for( ; ; )
{
    ...
}
```

#### 8.  函数

##### 定义函数

```c
return_type function_name( parameter list )
{
   body of the function
}
```

- **返回类型：**一个函数可以返回一个值。**return_type** 是函数返回的值的数据类型。有些函数执行所需的操作而不返回值，在这种情况下，return_type 是关键字 **void**。
- **函数名称：**这是函数的实际名称。函数名和参数列表一起构成了函数签名。
- **参数：**参数就像是占位符。当函数被调用时，您向参数传递一个值，这个值被称为实际参数。参数列表包括函数参数的类型、顺序、数量。参数是可选的，也就是说，函数可能不包含参数。
- **函数主体：**函数主体包含一组定义函数执行任务的语句。

##### 调用函数

当程序调用函数时，程序控制权会转移给被调用的函数。被调用的函数执行已定义的任务，当函数的返回语句被执行时，或到达函数的结束括号时，会把程序控制权交还给主程序。

- 调用函数时，传递所需参数，如果函数返回一个值，则可以存储返回值。

##### 函数参数

如果函数要使用参数，则必须声明接受参数值的变量。这些变量称为函数的**形式参数**。

形式参数就像函数内的其他局部变量，在进入函数时被创建，退出函数时被销毁。

当调用函数时，有两种向函数传递参数的方式：

| 调用类型                                                     | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [传值调用](https://www.runoob.com/cprogramming/c-function-call-by-value.html) | 该方法把参数的实际值复制给函数的形式参数。在这种情况下，修改函数内的形式参数不会影响实际参数。 |
| [引用调用](https://www.runoob.com/cprogramming/c-function-call-by-pointer.html) | 通过指针传递方式，形参为指向实参地址的指针，当对形参的指向操作时，就相当于对实参本身进行的操作。 |

#### 9.  作用域规则

任何一种编程中，作用域是程序中定义的变量所存在的区域，超过该区域变量就不能被访问。

- 在函数或块内部的**局部**变量
- 在所有函数外部的**全局**变量
- 在**形式**参数的函数参数定义中

##### 局部变量

在某个函数或块的内部声明的变量成为局部变量。它们只能被该函数或该代码块内部的语句使用。

##### 全局变量

定义在函数外部，通常是在程序的顶部。全局变量在整个程序声明周期内都是有效的，在任意的函数内部能被访问全局变量。

##### 形式参数

函数的参数，形式参数，被当作该函数内的局部变量，如果与全局变量同名它们会优先使用。

#### 10.  数组

##### 声明数组

```c
type arrayName [ arraySize ];
```

##### 初始化数组

```c
double balance[5] = {1000.0, 2.0, 3.4, 7.0, 50.0};
```

##### 访问数组元素

数组元素可以通过数组名称加索引进行访问。元素的索引是放在方括号内，跟在数组名称后面。

##### 获取数组长度

可以使用 **sizeof** 运算符来获取数组的长度。

##### 数组名

数组名表示数组的地址，即数组首元素的地址。当我们在声明和定义一个数组时，该数组名就代表着该数组的地址。

##### C 中数组详解

| 概念                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [多维数组](https://www.runoob.com/cprogramming/c-multi-dimensional-arrays.html) | C 支持多维数组。多维数组最简单的形式是二维数组。             |
| [传递数组给函数](https://www.runoob.com/cprogramming/c-passing-arrays-to-functions.html) | 您可以通过指定不带索引的数组名称来给函数传递一个指向数组的指针。 |
| [从函数返回数组](https://www.runoob.com/cprogramming/c-return-arrays-from-function.html) | C 允许从函数返回数组。                                       |
| [指向数组的指针](https://www.runoob.com/cprogramming/c-pointer-to-an-array.html) | 您可以通过指定不带索引的数组名称来生成一个指向数组中第一个元素的指针。 |
| [静态数组与动态数组](https://www.runoob.com/cprogramming/c-static-dynamic-array.html) | 静态数组在编译时分配内存，大小固定，而动态数组在运行时手动分配内存，大小可变。 |

#### 11.  enum（枚举）

##### 枚举类型定义

```c
enum　枚举名　{枚举元素1,枚举元素2,……};
```

**注意：**第一个枚举成员的默认值为整型的 0，后续枚举成员的值在前一个成员上加 1。我们在这个实例中把第一个枚举成员的值定义为 1，第二个就为 2，以此类推。

##### 枚举变量定义

- 先定义枚举类型，再定义枚举变量

```c
enum DAY
{
      MON=1, TUE, WED, THU, FRI, SAT, SUN
};
enum DAY day;
```

- 定义枚举类型的同时定义枚举变量

```c
enum DAY
{
      MON=1, TUE, WED, THU, FRI, SAT, SUN
} day;
```

- 省略枚举名称，直接定义枚举变量

```c
enum
{
      MON=1, TUE, WED, THU, FRI, SAT, SUN
} day;
```

#### 12.  指针

##### 指针变量声明

```c
type *var_name;
```

##### 使用指针

定义一个指针变量、把变量地址赋值给指针、访问指针变量中可用地址的值。这些是通过使用一元运算符 `*` 来返回位于操作数所指定地址的变量的值。

##### NULL 指针

没有确切的地址可以幅值，为指针变量赋一个 NULL 值是一个良好的编程习惯。赋予 NULL 值得指针被成为空指针。

##### C 指针详解

| 概念                                                         | 描述                                                     |
| :----------------------------------------------------------- | :------------------------------------------------------- |
| [指针的算术运算](https://www.runoob.com/cprogramming/c-pointer-arithmetic.html) | 可以对指针进行四种算术运算：++、--、+、-                 |
| [指针数组](https://www.runoob.com/cprogramming/c-array-of-pointers.html) | 可以定义用来存储指针的数组。                             |
| [指向指针的指针](https://www.runoob.com/cprogramming/c-pointer-to-pointer.html) | C 允许指向指针的指针。                                   |
| [传递指针给函数](https://www.runoob.com/cprogramming/c-passing-pointers-to-functions.html) | 通过引用或地址传递参数，使传递的参数在调用函数中被改变。 |
| [从函数返回指针](https://www.runoob.com/cprogramming/c-return-pointer-from-functions.html) | C 允许函数返回指针到局部变量、静态变量和动态内存分配。   |

#### 13.  函数指针

函数指针是指向函数的指针变量。函数指针可以像一般函数一样，用于调用函数、传递参数。

- 函数名等价于指向该函数的函数指针，类似于数组名等价于指向数组的指针。

##### 声明

```c
typedef int (*fun_ptr)(int,int); // 声明一个指向同样参数、返回值的函数指针类型
```

##### 回调函数

###### 函数指针作为某个变量的参考

函数指针变量可以作为某个函数的参数来使用的，回调函数就是一个通过函数指针调用的函数。

#### 14.  字符串

- 字符串实际上是使用空字符 **\0** 结尾的一维字符数组。因此，**\0** 是用于标记字符串的结束。

- **空字符（Null character**）又称结束符，缩写 **NUL**，是一个数值为 **0** 的控制字符，**\0** 是转义字符，意思是告诉编译器，这不是字符 **0**，而是空字符。

#### 15.  结构体

##### 定义结构

```c
struct tag { 
    member-list
    member-list 
    member-list  
    ...
} variable-list ;
```

- **tag** 是结构体标签。

- **member-list** 是标准的变量定义，比如 **int i;** 或者 **float f;**，或者其他有效的变量定义。

- **variable-list** 结构变量，定义在结构的末尾，最后一个分号之前，可以指定一个或多个结构变量。

> **结构体的成员可以包含其他结构体，也可以包含指向自己结构体类型的指针。**

> **如果两个结构体互相包含，则需要对其中一个结构体进行不完整声明。**

##### 结构变量的初始化

1. 定义时指定初始值。
2. 访问结构成员：使用成员访问运算符（.），并使用 `strcpy` 函数指定初始值。

##### 结构作为函数参数

把结构作为函数参数，传参方式与其他类型的变量或指针类似。

##### 指向结构的指针

- 结构体内包含指向该种结构类型的指针，实例化结构体时，可以指定指针所指向的实例。

```c
struct Node
{
	struct Node* next_node;
}

/* 实例化结构体 Node */
struct Node node1;
struct Node node2;

/* 链接 node1 与 node2 */
node1.next_node = &node2;

/* 通过 node1 访问 node2 的成员 */
node1.next_node -> next_node;
```

##### 结构体大小的计算

对于结构体，**sizeof** 将返回结构体的总字节数，包括所有成员变量的大小以及可能的填充字节。

#### 16.  共用体

允许在相同的内存位置存储不同的数据类型。可以定义一个带有多成员的共用体，但是任何时候只能有**一个成员带有值**。共用体提供了一种使用相同的内存位置的有效方式。

##### 定义共用体

```c
union [union tag]
{
   member definition;
   member definition;
   ...
   member definition;
} [one or more union variables];
```

#### 17.  位域

位域（bit-field）是一种特殊的结构体成员，允许我们按位对成员进行定义，指定其占用的位数。

- 结构以4字节为单位，定义的位数小于32bit，4字节，占用4字节内存空间。

- 定义位域时，可以指定成员的位域宽度，即成员所占用的位数。
- 位域的宽度不能超过其数据类型的大小，因为位域必须适应所使用的整数类型。
- 位域的数据类型可以是 `int`、`unsigned int`、`signed int` 等整数类型，也可以是枚举类型。
- 位域可以单独使用，也可以与其他成员一起组成结构体。
- 位域的访问是通过点运算符（`.`）来实现的，与普通的结构体成员访问方式相同。

##### 位域声明

所谓“位域”是把一个字节中的二进位划分为几个不同的区域，并说明每个区域的位数。每个区域有一个域名，允许再程序中按照域名操作。这样就可以把几个不同的对象用一个字节的二进制位域来表示。

##### 位域的定义

```c
struct 位域结构名 
{
	/* 位域列表 */
	type [member_name] : width ;
};
```

##### 几点说明

- 当数据类型为 `unsigned` ，位域存储在同一个字节中，如一个字节所剩空间不够存放另一位域时，则会从下一个单元存放该位域。
- 位域的宽度不能超过它所依附的数据类型的长度，如数据类型为 `int` ，位域宽度不能超过32。
- 位域可以是无名位域，表示作填充或者调整位置。

##### 位域的使用

```c
位域变量名.位域名
位域变量名->位域名
```

#### 18.  typedef

- 为类型去一个新的名字
- 为结构体定义一个新的名字

##### typedef vs #define

- **typedef** 仅限于为类型定义符号名称，**#define** 不仅可以为类型定义别名，也能为数值定义别名。
- **typedef** 是由编译器执行解释的，**#define** 语句是由预编译器进行处理的。

#### 19.  输入 & 输出

- 通常使用 `printf() & scanf()` 两个函数。

##### getchar() & putchar() 函数

- **int getchar(void)** 函数从屏幕读取下一个可用的字符，并把它返回为一个整数。这个函数在同一个时间内只会读取一个单一的字符。您可以在循环内使用这个方法，以便从屏幕上读取多个字符。

- **int putchar(int c)** 函数把字符输出到屏幕上，并返回相同的字符。这个函数在同一个时间内只会输出一个单一的字符。您可以在循环内使用这个方法，以便在屏幕上输出多个字符。

##### gets() & puts() 函数

- **char \*gets(char \*s)** 函数从 **stdin** 读取一行到 **s** 所指向的缓冲区，直到一个终止符或 EOF。

- **int puts(const char \*s)** 函数把字符串 s 和一个尾随的换行符写入到 **stdout**。

##### scanf() & printf() 函数

- **int scanf(const char \*format, ...)** 函数从标准输入流 **stdin** 读取输入，并根据提供的 **format** 来浏览输入。

- **int printf(const char \*format, ...)** 函数把输出写入到标准输出流 **stdout** ，并根据提供的格式产生输出。

#### 20.  文件读写

一个文件，无论是文本文件还是二进制文件，都是代表了一系列的字节。

##### 打开文件

```c
FILE *fopen( const char *filename, const char *mode );
```

##### 关闭文件

```c
 int fclose( FILE *fp );
```

##### 写入文件

```c
/* 写入字符值 */
int fputc( int c, FILE *fp );
/* 写入字符串 */
int fputs( const char *s, FILE *fp );
```

##### 读取文件

```c
/* 读取单个字符 */
int fgetc( FILE * fp );
/* 读取字符串 */
char *fgets( char *buf, int n, FILE *fp );
```

##### 二进制 I/O 函数

```c
size_t fread(void *ptr, size_t size_of_elements, size_t number_of_elements, FILE *a_file);
size_t fwrite(const void *ptr, size_t size_of_elements, size_t number_of_elements, FILE *a_file);
```

#### 21.  预处理器

**C 预处理器**不是编译器的组成部分，但是它是编译过程中一个单独的步骤。简言之，C 预处理器只不过是一个文本替换工具而已，它们会指示编译器在实际编译之前完成所需的预处理。

##### 预定义宏

| 宏        | 描述                                                |
| :-------- | :-------------------------------------------------- |
| \__DATE__ | 当前日期，一个以 "MMM DD YYYY" 格式表示的字符常量。 |
| \__TIME__ | 当前时间，一个以 "HH:MM:SS" 格式表示的字符常量。    |
| \__FILE__ | 这会包含当前文件名，一个字符串常量。                |
| \__LINE__ | 这会包含当前行号，一个十进制常量。                  |
| \__STDC__ | 当编译器以 ANSI 标准编译时，则定义为 1。            |

##### 预处理器运算符

###### 宏延续运算符（\）

一个宏通常写在一个单行上。但是如果宏太长，一个单行容纳不下，则使用宏延续运算符（\）。

###### 字符串化运算符（#）

用于将为被引号包围的数据解释为字符串。

```c
#define stringer( x ) printf_s( #x "\n" )
/* 以下两行代码是等价的 */
stringer( In quotes in the printf function call );
printf_s( "In quotes in the printf function call" "\n" );
```

###### 标记粘贴运算符（##）

宏定义内的标记粘贴运算符（##）会合并两个参数。它允许在宏定义中两个独立的标记被合并为一个标记。

###### 参数化的宏

用参数化的宏模拟函数。

```c
#define square(x) ((x) * (x))
```

#### 22.  头文件

##### 引用头文件的语法

```c
#include <file>
```

##### 只引用一次头文件

```c
/* 如果没有定义 */
#ifndef HEADER_FILE
/* 则定义头文件 */
#define HEADER_FILE
/* 对应 #if */
#endif
```

##### 有条件引用

```c
#if SYSTEM_1
   # include "system_1.h"
#elif SYSTEM_2
   # include "system_2.h"
#elif SYSTEM_3
   ...
#endif
/* 使用宏名称代替 */
 #define SYSTEM_H "system_1.h"
 ...
 #include SYSTEM_H
```

#### 23.  强制类型转换

使用强制类型转换运算符，把值显式地从一种类型转换为另一种类型。

```c
(type_name) expression
```

##### 整数提升

整数提升是指把小于 **int** 或 **unsigned int** 的整数类型转换为 **int** 或 **unsigned int** 的过程

##### 常用的算术转换

**常用的算术转换**是隐式地把值强制转换为相同的类型。编译器首先执行**整数提升**。

#### 24.  错误处理

##### errno、perror() 和 strerror()

- **perror()** 函数显示您传给它的字符串，后跟一个冒号、一个空格和当前 errno 值的文本表示形式。
- **strerror()** 函数，返回一个指针，指针指向当前 errno 值的文本表示形式。

##### 程序退出状态

- 通常情况下，程序成功执行完一个操作正常退出的时候会带有值 EXIT_SUCCESS。在这里，EXIT_SUCCESS 是宏，它被定义为 0。

- 如果程序中存在一种错误情况，当退出程序时，会带有状态值 EXIT_FAILURE，被定义为 -1。

#### 25.  递归

递归指的是在函数的定义中使用函数自身的方法。

#### 26.  可变参数

根据具体的需要接收可变数量的参数

```c
/* arg1 声明了变量的个数 */
int func_name(int arg1, ...);
```

为了使用这个功能，需要使用 **stdarg.h** 头文件，该文件提供了实现可变参数功能的函数和宏。具体步骤如下：

- 定义一个函数，最后一个参数为省略号，省略号前面可以设置自定义参数。
- 在函数定义中创建一个 **va_list** 类型变量，该类型是在 stdarg.h 头文件中定义的。
- 使用 **int** 参数和 **va_start()** 宏来初始化 **va_list** 变量为一个参数列表。宏 **va_start()** 是在 stdarg.h 头文件中定义的。
- 使用 **va_arg()** 宏和 **va_list** 变量来访问参数列表中的每个项。
- 使用宏 **va_end()** 来清理赋予 **va_list** 变量的内存。

常用的宏有：

- `va_start(ap, last_arg)`：初始化可变参数列表。`ap` 是一个 `va_list` 类型的变量，`last_arg` 是最后一个固定参数的名称（也就是可变参数列表之前的参数）。该宏将 `ap` 指向可变参数列表中的第一个参数。
- `va_arg(ap, type)`：获取可变参数列表中的下一个参数。`ap` 是一个 `va_list` 类型的变量，`type` 是下一个参数的类型。该宏返回类型为 `type` 的值，并将 `ap` 指向下一个参数。
- `va_end(ap)`：结束可变参数列表的访问。`ap` 是一个 `va_list` 类型的变量。该宏将 `ap` 置为 `NULL`。

#### 27.  内存管理

| 序号 | 函数和描述                                                   |
| :--- | :----------------------------------------------------------- |
| 1    | **void \*calloc(int num, int size);** 在内存中动态地分配 num 个长度为 size 的连续空间，并将每一个字节都初始化为 0。所以它的结果是分配了 num*size 个字节长度的内存空间，并且每个字节的值都是 0。 |
| 2    | **void free(void \*address);** 该函数释放 address 所指向的内存块,释放的是动态分配的内存空间。 |
| 3    | **void \*malloc(int num);** 在堆区分配一块指定大小的内存空间，用来存放数据。这块内存空间在函数执行完成后不会被初始化，它们的值是未知的。 |
| 4    | **void \*realloc(void \*address, int newsize);** 该函数重新分配内存，把内存扩展到 **newsize**。 |

##### 动态分配内存

编程时，如果预先知道数组的大小，那么定义数组时就比较容易。如果预先不知道需要存储的文本长度，需要定义一个指针，该指针指向未定义所需内存大小的字符，后续再根据需求来分配内存。

##### 重新调整内存的大小和释放内存

- 当程序退出时，操作系统会自动释放所有分配给程序的内存。
- 在不需要内存时，都应该调用函数 **free()** 来释放内存。

- 或者可以通过调用函数 **realloc()** 来增加或减少已分配的内存块的大小。

##### C 语言中常用的内存管理函数和运算符

- malloc() 函数：用于动态分配内存。它接受一个参数，即需要分配的内存大小（以字节为单位），并返回一个指向分配内存的指针。
- free() 函数：用于释放先前分配的内存。它接受一个指向要释放内存的指针作为参数，并将该内存标记为未使用状态。
- calloc() 函数：用于动态分配内存，并将其初始化为零。它接受两个参数，即需要分配的内存块数和每个内存块的大小（以字节为单位），并返回一个指向分配内存的指针。
- realloc() 函数：用于重新分配内存。它接受两个参数，即一个先前分配的指针和一个新的内存大小，然后尝试重新调整先前分配的内存块的大小。如果调整成功，它将返回一个指向重新分配内存的指针，否则返回一个空指针。
- sizeof 运算符：用于获取数据类型或变量的大小（以字节为单位）。
- 指针运算符：用于获取指针所指向的内存地址或变量的值。
- & 运算符：用于获取变量的内存地址。
- ***** 运算符：用于获取指针所指向的变量的值。
- **->** 运算符：用于指针访问结构体成员，语法为 **pointer->member**，等价于 **(\*pointer).member**。
- memcpy() 函数：用于从源内存区域复制数据到目标内存区域。它接受三个参数，即目标内存区域的指针、源内存区域的指针和要复制的数据大小（以字节为单位）。
- memmove() 函数：类似于 memcpy() 函数，但它可以处理重叠的内存区域。它接受三个参数，即目标内存区域的指针、源内存区域的指针和要复制的数据大小（以字节为单位）。

#### 28.  命令行参数

执行程序时，可以从命令行传值给 C 程序。这些值被称为**命令行参数**。

```c
int main( int argc, char *argv[] )  
{
	...
}
```

- **argc** 是指传入参数的个数。
- **argv[]** 是一个指针数组，指向传递给程序的每个参数。

应当指出的是，**argv[0]** 存储程序的名称，**argv[1]** 是一个指向第一个命令行参数的指针，*argv[n] 是最后一个参数。如果没有提供任何参数，argc 将为 1，否则，如果传递了一个参数，**argc** 将被设置为 2。

多个命令行参数之间用空格分隔，但是如果参数本身带有空格，那么传递参数的时候应把参数放置在双引号 "" 或单引号 '' 内部。
