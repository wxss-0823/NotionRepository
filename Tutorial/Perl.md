# Perl 教程

## 1. Perl 基础语法

### 1.1. 交互式编程

```shell
perl -e 'print "Hello World\n"'
```

### 1.2. 脚本式编程

```perl
# path

print "Hello World\n"
```

### 1.3. 脚本文件

​	Perl 代码可以写在一个文本文件中，以 `.pl`，`.PL` 作为结尾。文件名可以包含数字，符号和字母，但不能包含空格，可以使用下划线 `_` 来代替空格。

### 1.4. 注释

​	Perl 注释的方法为在语句的开头用字符 `#` 。

```perl
# 这一行是 Perl 中的注释
```

​	Perl 也支持多行注释，最常用的方法是使用 POD（Plain Old Documentations）来进行多行注释。

```perl
=pod 注释
...
...
=cut
```

**注意**：

- `-pod`，`-cut` 只能在行首；
- 以 `=` 开头，以 `=cut` 结尾；
- `=` 后面要紧接一个字符，`=cut` 后面可以不用。

### 1.5. Perl 中的空白

​	Perl 解释器不会关心有多少个空白。所有类型的空白，如：空格、tab、空行等，如果在引号外，解释器会忽略它，如果在引号内，会原样输出。

### 1.6. 引号

​	Perl 输出字符串可以使用单引号和双引号，双引号可以正常解析转义字符和变量，单引号无法解析，会原样输出。

### 1.7. Here 文档

​	Here 文档又称作 heredoc、hereis、here-string 或 、here-script，是一种在命令行和程序语言里定义一个字符串的方法。

```perl
# 使用双引号输出
$var = <<"EOF"
...
...
EOF

$var = <<"EOF"
...
...
EOF
```

- `$var = <<"EOF"` 必须后接分号，否则编译不过；
- `EOF` 可以用任何其他字符代替，只需保证结束标识与开始标识一致；
- 结束标识必须顶个独自占一行；
- 开始表似乎可以不带引号，或带单双引号，不带引号和带双引号效果一致，解释内嵌的变量和转移符号，带单引号则不解释内嵌的变量和转移符号；
- 当内容需要内嵌引号时，不需要加转义符，本身对单双引号转义。

### 1.8. 转义字符

​	如果需要输出一个特殊的字符，可以使用反斜线 `\` 来转义。

### 1.9. Perl 标识符

​	Perl 标识符时用户编程时使用的名字，在程序中使用的变量名、常量名、函数名，语句块名等统称为标识符。

- 标识符组成单元：英文字符（a ~ z，A ~ Z），数字（0 ~ 9）和下划线 `_` ；
- 标识符由英文字符或下划线开头；
- 标识符区分大小写。

## 2. Perl 数据类型

​	Perl 是一种弱类型语言，所以变量不需要指定类型，Perl 解释器会根据上下文自动选择匹配类型。

### 2.1. 标量

​	标量是 Perl 语言中最简单的一种数据类型，这种数据类型的变量可以是数字，字符串，浮点数，不做严格的区分。在使用时，在变量的名字前面加一个 `$` ，表示是标量。

#### 2.1.1. 整型

​	Perl 实际上把整数存在计算机的浮点寄存器中，所以实际上被当作浮点数看待。8 进制以 0 开始，16 进制以 0x 开始。

```perl
$x = 12345;
```

#### 2.1.2. 浮点数

​	浮点寄存器通常不能精确的存储浮点数，从而产生误差，在运算和比较中要特别注意，指数的范围通常为 -309 到 +308。

```perl
$value = 9.01e+21 + 0.01 -9.01e+21;
```

#### 2.1.3. 字符串

​	Perl 中的字符串使用一个标量来表示，定义方式和 C 很像，但不是以 `\0` 结束。

#### 2.1.4. 特殊字符

​	特殊字符是特殊的标记，不能写在字符串中。

- `__FILE__`：文件名；
- `__LINE__`：行号；
- `__PACKAGE__`：包名。

#### 2.1.5. v 字符串

​	一个以 v 开头，后面跟着一个或多个用句点分隔的整数，会被当做一个字串文本。每一个整数对应一个字符。

### 2.2. 数组

​	数组变量以字符 `@` 开头，索引从 0 开始。

```perl
@array = (1,2,3);
```

#### 2.2.1. 创建数组

​	数组变量以 `@` 符号开始，元素放在括号内，也可以以 `qw` 开始定义数组。

```perl
@array = (val1, val2, ...);
@array = qw/val1 val2 val3/;
```

#### 2.2.2. 访问数组元素

​	访问数组元素使用 `$array_name[index]` 的格式来读取。 

#### 2.2.3. 数组序列号

​	Perl 提供了可以按序列输出的数组形式，格式为：起始值 + .. + 终止值。

```perl
@var = (1..10); # var: 1, 2, 3, ..., 10
```

#### 2.3.4. 数组大小

​	数组大小由数组中的标量上下文决定。数组长度返回的是数组的物理大小，而不是元素的个数。

```perl
@array = (1, 2, 3);
print scalar @array;	# 数组大小为 3
@array[50] = 4;
$size = @array;				# 数组物理大小为 51，个数为 4
$max_index = $#array	# 特殊运算符 $#，返回数组的最大索引 50
```

#### 2.3.5. 添加和删除

​	Perl 提供了一些有用的函数来添加和删除数组元素。

| 类型                   | 描述                                         |
| ---------------------- | -------------------------------------------- |
| `push @ARRAY, LIST`    | 将列表的值放到数组的末尾                     |
| `pop @ARRAY`           | 删除数组的最后一个值                         |
| `shift @ARRAY`         | 弹出数组第一个值，并返回它，数组索引依次减 1 |
| `unshift @ARRAY, LIST` | 将列表放在数组前面，并返回新数组的元素个数   |

#### 2.3.6. 切割数组

​	指定有效的数组索引值，来切割指定数组。

```perl
@site1 = ...;
@site2 = @site1[1, 2, 3];
```

#### 2.3.7. 替换元素

​	Perl 中数组元素替换使用 `splice()` 函数。

```perl
spilce @ARRAY, OFFSET [, LENGTH [, LIST]]
```

#### 2.3.8. 字符串转数组

​	Perl 中将字符串转换为数组使用 `split()` 函数。

```perl
split [PATTERN [, EXPR [, LIMIT]]]
```

- `PATTERN`：分隔符，默认为空格；
- `EXPR`：指定字符串数；
- `LIMIT`：如果指定该参数，则返回该数组的元素个数。

#### 2.3.9. 数组转字符串

​	Perl 中将数组转换为字符串使用 `join()` 函数。

```perl
join EXPR, LIST
```

- `EXPR`：连接符；
- `LIST`：列表或数组。

#### 2.3.10. 数组排序

​	Perl 中数组排序使用 `sort()` 函数。

```perl
sort [SUBROUTINE] LIST
```

- `SUBROUTINE`：指定规则；
- `LIST`：列表或数组。

**注意**：数组排序是根据 ASCII 数字值来排序，所以最好先将每个元素转换为小写后再排序。

#### 2.3.11. 合并数组

​	数组的元素是以逗号来分隔，也可以使用逗号来合并数组。

```perl
@numbers = (1, 3, (4, 5, 6));
@odd = (1,3,5);
@even = (2,4,6);
@numbers = (@odd, @even);
```

#### 2.3.12. 从列表中选择元素

​	一个列表可以当作一个数组使用，在列表后指定索引值可以读取指定的元素。

```perl
$var = (5,4,3,2,1)[4]
```

### 2.3. 哈希

​	哈希是一个无序的 **key/value** 对集合，可以使用键作为下标获取值。哈希变量以字符 `%` 开头。

```perl
%h = ('a'=>1, 'b'=>2);
```

#### 2.3.1. 创建哈希

##### 为每个 key 设置 value

```perl
$data{'google'} = 'google.com';
$data{'runoob'} = 'runoob.com';
$data{'taobao'} = 'taobao.com';
```

##### 通过列表设置

```perl
%data = ('google', 'google.com', 'runoob', 'runoob.com', 'taobao', 'taobao.com');
# 也可以使用 => 符号
%data = ('google' => 'google.com', 'runoob' => 'runoob.com', 'taobao' => 'taobao.com');
```

#### 2.3.2. 访问哈希元素

```perl
$hash_name{key_name};
```

#### 2.3.3. 哈希提取数组

```perl
%data = (-taobao => 45, -google => 30, -runoob => 40);
@array = @data(-taobao, -google);
```

#### 2.3.4. 读取全部键/值

```perl
# 读取哈希全部键
keys %hash_name;
# 读取哈希全部值
values %hash_name;
```

#### 2.3.5. 检查存在

```perl
exists($data{key_name});
```

#### 2.3.6. 获取大小

```perl
# 获取 keys
@keys = keys %data;
# 获取 keys 长度
$size = @keys;
```

#### 2.3.7. 添加/删除元素

​	添加可以通过 key/value 对赋值完成，删除需要使用 `delete()` 函数。

```perl
%data = (key, value);
delete %data{key_name}
```

#### 2.3.8. 迭代哈希

​	可以使用 `foreach` 和 `while` 来迭代哈希。

```perl
foreach $keys (keys %data) {
	...
}

while (($key, $value) = each(%data)) {
	...
}
```

## 3. Perl 变量

​	变量是存储在内存中的数据，创建一个变量即会在内存上开辟一个空间。解释器会根据变量的类型来决定其在内存中的存储空间。标量以 `$` 开始，数组以 `@` 开始，哈希以 `%` 开始。Perl 为每个变量类型设置了独立的命名空间，所以不同类型的变量可以使用相同的名称。

### 3.1. 创建变量

​	变量不需要显式声明类型，在变量赋值后，解释器会自动分配匹配的类型空间。

### 3.2. 变量上下文

​	所谓上下文：指的是表达式所在的位置。上下文是由等号左边的变量类型决定的。Perl 解释器会根据上席文来决定变量的类型。同一个变量应用于不同的上下文会返回不同的结果。

| 上下文 | 描述                                         |
| ------ | -------------------------------------------- |
| 标量   | 赋值给一个标量变量，在标量上下文右侧计算     |
| 列表   | 赋值给一个数组或哈希，在列表上下文的右侧计算 |
| 布尔   | 查看是否为 true 或 false                     |
| Void   | 不需要返回值                                 |
| 插值   | 仅发生在括号内                               |

## 4. Perl 条件语句

​	Perl 条件语句是通过一条或多条语句的执行结果来决定执行的代码块。Perl 提供了下列条件语句：

| 语句                        | 描述                                                     |
| --------------------------- | -------------------------------------------------------- |
| `if ... elsif ... else`     | if 后跟可选的 elsif 与 else，条件满足时执行 if           |
| `unless ... elsif ... else` | unless 后跟可选的 elsif 与 else，条件满足时不执行 unless |
| `switch`                    | 根据不同值选择代码块                                     |

### 4.1. 三元运算符

​	`Exp1` 为 true，则执行 `Exp2`，否则执行 `Exp3`。

```perl
Exp1 ? Exp2 : Exp3;
```

## 5. Perl 循环

​	循环语句允许多次执行一个语句或语句组。Perl 提供了下列循环语句：

| 循环类型       | 描述                                     |
| -------------- | ---------------------------------------- |
| `while`        | 条件为真时，执行循环                     |
| `until`        | 条件为真时，退出循环                     |
| `for`          | 已知执行次数的循环                       |
| `foreach`      | 用于迭代一个列表或集合变量的值           |
| `do ... while` | 在循环结尾判断条件，条件为真时，执行循环 |

### 5.1. 循环控制语句

​	循环控制语句改变了循环中代码的执行顺序。Perl 提供了下列的循环控制语句：

| 控制语句   | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| `next`     | 停止执行从 next 语句的下一语句开始到循环体结束标识符之间的语句，转去执行 continue 语句块，然后再返回到循环体的起始处开始执行下一次循环 |
| `last`     | 退出循环语句块，从而结束循环                                 |
| `continue` | 通常再条件语句再次判断前执行                                 |
| `redo`     | 直接跳转到循环体的第一行开始重新执行本次循环，continue 也不再执行 |
| `goto`     | Perl 有三种 goto 形式：`got LABEL`，`goto EXPR`，`goto &NAME` |

### 5.2. 无限循环

​	如果条件永远不为 false，则循环将变为无限循环。

```perl
for( ; ; ) {
	...
}
```

## 6. Perl 运算符

### 6.1. 算术运算符

| 运算符 | 描述 |
| ------ | ---- |
| `+`    | 加法 |
| `-`    | 减法 |
| `*`    | 乘法 |
| `/`    | 除法 |
| `%`    | 求余 |
| `**`   | 乘幂 |

### 6.2. 比较运算符

| 运算符         | 描述                                                |
| -------------- | --------------------------------------------------- |
| `==` 或 `eq`   | 检查是否相等                                        |
| `!=` 或 `ne`   | 检查是否不相等                                      |
| `<=>` 或 `cmp` | 相等返回 0，左边小于右边返回 -1，右边小于左边返回 1 |
| `>` 或 `gt`    | 检查左边是否大于右边                                |
| `<` 或 `lt`    | 检查右边是否大于左边                                |
| `>=` 或 `ge`   | 检查左边是否大于或等于右边                          |
| `<=` 或 `le`   | 检查右边是否大于或等于左边                          |

### 6.3. 赋值运算符

| 运算符 | 描述       |
| ------ | ---------- |
| `=`    | 赋值       |
| `+=`   | 加且赋值   |
| `-=`   | 减且赋值   |
| `*=`   | 乘且赋值   |
| `/=`   | 除且赋值   |
| `%=`   | 求模且赋值 |
| `**=`  | 乘幂且赋值 |

### 6.4. 位运算

| 运算符 | 描述     |
| ------ | -------- |
| `&`    | 按位与   |
| `|`    | 按位或   |
| `^`    | 按位异或 |
| `~`    | 按位取反 |
| `<<`   | 左移     |
| `>>`   | 右移     |

### 6.5. 逻辑运算符

| 运算符 | 描述           |
| ------ | -------------- |
| `and`  | 逻辑与         |
| `&&`   | C 风格的逻辑与 |
| `or`   | 逻辑或         |
| `||`   | C 风格的逻辑或 |
| `not`  | 逻辑非         |

### 6.6. 引号运算

| 运算符 | 描述               |
| ------ | ------------------ |
| `q{}`  | 为字符串添加单引号 |
| `qq{}` | 为字符串添加双引号 |
| `qx{}` | 为字符串添加反引号 |

### 6.7. 其他运算符

| 运算符 | 描述                |
| ------ | ------------------- |
| `.`    | 连接字符串          |
| `x`    | 返回字符串重复 x 次 |
| `..`   | 范围运算符          |
| `++`   | 自增运算符          |
| `--`   | 自减运算符          |
| `->`   | 指定一个类方法      |

## 7. Perl 时间日期

### 7.1. localtime

​	获取本地时区的时间。一次性返回下列各值：

- `sec`：秒；
- `min`：分钟；
- `hour`：小时；
- `mday`：天，1 ~ 31；
- `mon`：月，0 ~ 11；
- `year`：年，从 1900 开始；
- `wday`：星期几，0 ~ 6，0 表示周日；
- `yday`：一年中的第几天，0 ~ 364，365；
- `isdst`：如果夏令时有效，则为真。

​	如果直接调用 `localtime()` ，而不使用多个参数接收变量，那么会返回系统当前设置时区的时间。

### 7.2. 格林威治时间（GMT）

​	与 `localtime` 类似，但 `gmtime` 返回标准格林威治时间。

### 7.3. 格式化时间

​	可以使用 `localtime()` 函数的 9 个时间元素来输出需要指定的格式时间。`localtime()` 函数还可以接收 `time()` 函数的返回值，并转化为日期。

```perl
$epoch = time();
localtime($epoch);
```

### 7.4. 新纪元时间（Epoch Time）

​	可以使用 `time()` 函数来获取新纪元时间，该函数返回从 1970 年 1 月 1 日起累计的秒数。

### 7.5. POSIX 函数 strftime

函数 `strftime()` 可以格式化时间。

```perl
use POSIX qw(strftime);

strftime "{format}", function_time;
```

- `function_time`：函数可以是 `localtime` 或 `gmtime`；
- `{format}`：用于指定输出字符串的格式。

​	`{format}` 可选的参数见下表：

| 符号 | 描述                                                |
| ---- | --------------------------------------------------- |
| `%a` | 星期几简称                                          |
| `%A` | 星期几全称                                          |
| `%b` | 月份简称                                            |
| `%B` | 月份全称                                            |
| `%c` | 日期和时间                                          |
| `%C` | 世纪                                                |
| `%d` | 一个月的第几天                                      |
| `%D` | 日期，MM/DD/YY                                      |
| `%e` | 一个月的第几天，使用空格填充个位数                  |
| `%F` | YYYY-MM-DD 的简写                                   |
| `%g` | 年份最后两位                                        |
| `%h` | 月的简称                                            |
| `%H` | 24 小时制                                           |
| `%I` | 12 小时制                                           |
| `%j` | 一年的第几天                                        |
| `%m` | 月份，数字表示，用 0 填充个位数                     |
| `%M` | 分钟，00 ~ 59                                       |
| `%n` | 新行，\n                                            |
| `%p` | 显示 AM 或 PM                                       |
| `%r` | 时间，hh:mm:ss am/pm，12 小时制                     |
| `%R` | 时间，HH:MM，24 小时制                              |
| `%S` | 秒数，00 ~ 61                                       |
| `%t` | 水平制表符，\t                                      |
| `%T` | 时间，hh:mm:ss，24小时制                            |
| `%u` | ISO 8601 的星期几格式，1 ~ 7，星期一为 1            |
| `%U` | 一年中的第几周，星期天为第一天，0 ~ 55              |
| `%V` | ISO 8601 第几周，0 ~ 53                             |
| `%w` | 一个星期的第几天，星期天为第一天，0 ~ 6             |
| `%W` | 一年的第几个星期，星期一为第一天，00 ~ 53           |
| `%x` | 日期，mm/dd/yy                                      |
| `%X` | 时间，hh/mm/ss                                      |
| `%y` | 年，两位数，0 ~ 99                                  |
| `%Y` | 年，四位数                                          |
| `%z` | ISO 8601 与 UTC 的时区偏移，1 min = 1，1 hour = 100 |
| `%Z` | 当前时区名称，如：中国标准时间，CDT                 |
| `%%` | % 符号                                              |

## 8. Perl 子程序（函数）

​	Perl 子程序（subroutine）就是用户自定义的函数，它是执行一个特殊任务的一段分离的代码，可以减少重复代码且使程序易读。

```perl
sub subroutine{
	# statements;
}
```

​	调用子程序语法：

```perl
subroutine(para_list);
```

### 8.1. 向子程序传递参数

​	Perl 子程序可以和其他编程一样接受多个参数，子程序参数使用特殊数组 `@_` 标明，因此子程序的第一个参数为 `$_[0]` ，第二个参数为 `$_[1]`，以此类推。

​	不论参数是标量型还是数组型，用户把参数传给子程序时，Perl 默认按引用的方式调用它们，用户可以通过改变 `@_` 数组中的值来改变相应实际参数的值。

#### 8.1.1. 向子程序传递列表

​	由于 `@_` 变量是一个数组，所以它可以向子程序中传递列表，但如果需要传入标量和数组参数时，需要把列表放在最后一个参数上。也可以传递多个数组，但是这种传递的结果是所有变量被整合进 `@_` 数组，会丢失独立的标识。

```perl
$a = 1;
@b = (2, 3, 4);

subroutine_name($a, @b);
```

​	上例中，子程序参数为 `@_ = 1, 2, 3, 4;` 。

#### 8.1.2. 向子程序传递哈希

​	当向子程序传递哈希时，它将复制到 `@_` 中，哈希表将被展开为键/值组合的列表。

```perl
%hash = ('name' => 'wxss', 'age' => 22);
subroutine_name(%hash);
```

​	上例中，子程序参数为 `@_ = 'name', 'wxss', 'age', 22;` 。

### 8.2. 子程序返回值

​	子程序可以像其他编程语言一样使用 `return` 语句来返回函数值，如果没有使用 `return` 语句，则子程序的最后一行语句作为返回值。

### 8.3. 子程序的私有变量

​	默认情况下，Perl 中所有变量都是全局变量，如果需要使用设置私有变量，可以使用 `my` 关键词来设置。`my` 操作符用于创建词法作用域变量，通过 `my` 创建的变量，存活于声明开始的地方，直到闭合作用域的结尾。

### 8.4. 变量的临时复制

​	可以使用 `local` 为全局变量提供临时的值，在退出作用域后将原来的值还原回去。`local` 定义的变量不存在于主程序中，但存在于该子程序和该子程序调用的子程序中。

```perl
# 全局变量
$string = "Hello, World!";

sub PrintWxss{
	local $string = "Hello, Wxss!";
	print $string;
}

# 打印 Hello, Wxss!
PrintWxss();
# 结束后将 string 的值还原
# 打印 Hello, World!
print $string;
```

### 8.5. 静态变量

​	`state` 操作符类似于 C 里的 `static` 修饰符，使局部变量变得持久。`state` 也是词法变量，所以只在定义该变量的词法作用域中有效。

```perl
use feature 'state';
```

### 8.6. 子程序调用上下文

​	子程序调用过程中，会根据上下文来返回不同类型的值。例如：`localtime()` 子程序，在标量上下文中，返回字符串；在列表上下文中，返回列表。

## 9. Perl 引用

​	引用就是指针，Perl 引用是一个标量类型，可以指向变量、数组、哈希表甚至子程序。

### 9.1. 创建引用

​	定义变量的时候，在变量名前面加个 `\` ，就得到了这个变量的引用。

```perl
$scalarref = \$foo;			# 标量变量引用
$arrayref = \@ARGV;			# 列表的引用
$hashref = \%ENV;				# 哈希的引用
$coderef = \&handler;		# 子过程引用
$globref = \*foo;				# GLOB 句柄引用
```

### 9.2. 取消引用

​	取消引用需要根据不同的类型使用 `$`，`@`，`%` 来取消。

```perl
$scalarref = \$foo;
$$scalarref;					# 取消引用
```

​	如果不确定变量的引用类型，可以使用 `ref` 来判断。

```perl
ref($var_name);
```

### 9.3. 循环引用

​	循环引用在两个引用相互包含时出现，需要小心使用，否则会导致内存泄漏。

```perl
my $foo = 100;
$foo = \$foo;
```

### 9.4. 引用函数

​	函数引用格式 `\&` ，调用引用函数格式 `&` 后接引用变量名。

## 10. Perl 格式化输出

​	Perl 是一个非常强大的文本数据处理语言，可以使用 `format` 来定义一个模板，然后使用 `write` 按指定模板输出数据。

```perl
format FormatName =
fieldline
value1, value2, value3
fieldline
value1, value2
.
```

- `FormatName`：格式化名称；
- `fieldline`：一个格式行，用于定义一个输出行的格式，类似 `@ ^ < > |` 这样的字符；
- `value1, value2`：数据行，用来向前面的格式行中插入值；
- `.`：结束符号。

### 10.1. 格式行语法

- 格式行以 `@` 或 `^` 开头，这些行不做任何形式的变量代换；
- `@` 字段是普通的字段，`^` 字段用于多行文本块填充；
- `@` 或 `^` 后的 `< > |` 长度决定了字段的长度，如果超出定义的长度的，将被截断；
- `< > |` 分别表示：左对齐，右对齐，居中对齐。

| 格式     | 值域含义     |
| -------- | ------------ |
| `@<<<`   | 左对齐输出   |
| `@>>>`   | 右对齐输出   |
| `@|||`   | 居中对齐输出 |
| `@##.##` | 固定精度数字 |
| `@*`     | 多行文本     |

**注意**：除了多行值域 `@*` ，域宽都等于其指定的包含字符 `@` 在内的字符个数。

### 10.2. 格式变量

- `$~`：规定文件的默认格式名，如果不指定，Perl 会自动寻找输出名为 `STDOUT` 的格式；
- `$^`：规定输出的表头格式名；
- `$%`：当前输出的页号；
- `$=`：每页的行数；
- `$|`：是否自动刷新输出缓冲区存储；
- `$^L`：规定在每一页（除了第一页）表头之前需要输出的字符串。

### 10.3. 输出到其他文件

#### 10.3.1. write 参数

​	含文件变量的输出，会默认打印与变量同名的格式，`$~` 指定的格式被忽略。因为 `$~` 只对默认文件变量有效，而在下例中，默认文件变量没有更改，只在第三行指定了输出的文件变量。

```perl
open(MYFILE ">>tmp");
$~ = "MYFORMAT";
write MYFILE;
format MYFILE = 
...
.
close MYFILE;
```

#### 10.3.2. 自定义输出格式

​	可以使用 `select` 改变默认输出文件变量，这时候再使用 `$~` 指定新的默认文件变量的默认格式，再输出，就可以自定义输出格式。

```perl
open(MYFILE ">>tmp");
select(MYFILE);
$~ = "MYFORMAT";
write;
format MYFORMAT = 
...
.
close MYFILE;
```

## 11. Perl 文件操作

​	Perl 使用一种叫做**文件句柄**（File Handle）类型的变量来操作文件。从文件读取或者写入数据需要使用文件句柄，文件句柄是一个 I/O 连接的名称。Perl 提供了三种文件句柄：`STDIN`，`STDOUT`，`STDERR` 。

```perl
open FILEHANDLE, EXPR
open FILEHANDLE

sysopen FILEHANDLE, FILENAME, MODE, PERMS
sysopen FILEHANDLE, FILENAME, MODE
```

- `FILEHANDLE`：文件句柄，用于存放一个文件唯一标识符；
- `EXPR`：文件名及文件访问类型组成的表达式；
- `MODE`：文件访问类型；
- `PERMS`：访问权限位（permission bits）。

### 11.1. open 函数

```perl
open(DATA, "<file.txt");
```

- `<`：表示只读方式。

| 模式          | 描述                                                         |
| ------------- | ------------------------------------------------------------ |
| `<` 或 `r`    | 只读方式打开，将文件指针指向文件头；                         |
| `>` 或 `w`    | 写入方式打开，将文件指针指向文件头并将文件大小截为零，如果文件不存在，则尝试创建 |
| `>>` 或 `a`   | 写入方式打开，将文件指针指向文件末尾，如果文件不存在，则尝试创建 |
| `+<` 或 `r+`  | 读写方式打开，将文件指针指向文件头                           |
| `+>` 或 `w+`  | 读写方式打开，将文件指针指向文件头，并将文件大小截为零，如果文件不存在，则尝试创建 |
| `+>>` 或 `a+` | 读写方式打开，将文件指针指向文件末尾，如果文件不存在，则尝试创建 |

### 11.2. sysopen 函数

​	类似于 `open` 函数，只是它们的参数形式不一样。

```perl
sysopen(DATA, "file.txt", O_RDWR);
```

| 模式         | 描述                                                         |
| :----------- | :----------------------------------------------------------- |
| `O_RDWR`     | 读写方式打开，将文件指针指向文件头                           |
| `O_RDONLY`   | 只读方式打开，将文件指针指向文件头                           |
| `O_WRONLY`   | 写入方式打开，将文件指针指向文件头并将文件大小截为零，如果文件不存在，则尝试创建 |
| `O_CREAT`    | 创建文件                                                     |
| `O_APPEND`   | 追加文件                                                     |
| `O_TRUNC`    | 将文件大小截为零                                             |
| `O_EXCL`     | 如果使用 `O_CREAT` 时文件存在，就返回错误信息                |
| `O_NONBLOCK` | 非阻塞 I/O 操作要么成功，要么立即返回错误，不被阻塞          |

### 11.3. close 函数

​	在文件使用完后，需要关闭文件，以刷新与文件句柄相关联的输入输出缓冲区。

```perl
close FILEHANDLE;
close
```

### 11.4. 读写文件

#### 11.4.1. \<FILEHANDLE> 操作符

​	从打开的文件句柄读取信息的主要方法是 `<FILEHANDLE>` 操作符，在标量上下文中，从文件句柄中返回单一行。

```perl
$fileline = <FILEHANDLE>;
```

​	从命令行获取输入可以使用文件句柄 `STDIN` 。

#### 11.4.2. getc

​	`getc` 函数从指定的 FILEHANDLE 返回单一的字符，如果没有指定，则返回 `STDIN` 。

```perl
getc [FILEHANDLE];
```

​	如果发生错误，或在文件句柄末尾，则返回 `undef` 。

#### 11.4.3. read

​	`read` 函数用于从缓冲区的文件句柄读取信息，用于从文件读取二进制数据。

```perl
read FILEHANDLE, SCALAR, LENGTH[, OFFSET]
```

- `FILEHANDLE`：文件句柄，用于存放一个文件唯一标识符；
- `SCALAR`：存储结果，如果没有指定 `OFFSET` ，数据将放在 `SCALAR` 开头，否则数据放在 `SCALAR` 的 `OFFSET` 字节之后；
- `LENGTH`：读取的内容长度；
- `OFFSET`：偏移量。

​	如果读取成功返回读取的字节数，如果在文件结尾返回 0 ，如果发生错误返回 `undef` 。

#### 11.4.4. print

​	对于所有从文件句柄中读取信息的函数，在后端主要的写入函数为 `print` 。利用文件句柄和 `print` 函数可以把程序运行的结果发给输出设备 `STDOUT` 。

```perl
print [FILEHANDLE] [LIST];
```

### 11.5. 文件重命名

​	函数 `rename` 只接受两个参数，只对已存在的文件进行重命名。

```perl
rename (old_name, new_name);
```

### 11.6. 删除文件

```perl
unlink (file_directory);
```

### 11.7. 指定文件位置

​	可以使用 `tell` 函数来获取文件的位置，并通过使用 `seek` 函数来指定文件内的位置。

#### 11.7.1. tell 函数

​	用于获取文件位置。如果指定 `FILEHANDLE` ，该函数返回文件指针的位置，以字节记；如果没有指定，则返回默认选取的文件句柄。

```perl
tell [FILEHANDLE];
```

#### 11.7.2. seek 函数

​	通过文件句柄来移动文件读写指针的方式来读取或写入文件的指定字节数据。

```perl
seek FILEHANDLE, POSITION, WHENCE;
```

- `FILEHANDLE`：文件句柄，用于存放一个文件唯一标识符；
- `POSITION`：表示文件句柄要移动的字节数；
- `WHENCE`：表示文件句柄开始移动时的起始位置；
  - 0：文件开头；
  - 1：当前位置；
  - 2：文件末尾。

### 11.8. 文件信息

​	Perl 的文件操作也可以先测试文件是否存在，是否可读写等信息。

| 操作符 | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| `-A`   | 文件上一次被访问的时间，以天为单位                           |
| `-B`   | 是否为二进制文件                                             |
| `-C`   | 文件的索引节点（inode）修改时间，以天为单位                  |
| `-M`   | 文件上一次被修改的时间，以天为单位                           |
| `-O`   | 文件被真实的 UID 所有                                        |
| `-R`   | 文件或目录可以被真实的 UID/GID 读取                          |
| `-S`   | 文件为 socket                                                |
| `-T`   | 是否为文本文件                                               |
| `-W`   | 文件或目录可以被真实的 UID/GID 写入                          |
| `-X`   | 文件或目录可以被真实的 UID/GID 执行                          |
| `-b`   | 文件为 block-special 文件，如挂载磁盘                        |
| `-c`   | 文件为 character-special 文件，如 I/O 设备                   |
| `-d`   | 变量为目录                                                   |
| `-e`   | 文件或目录名存在                                             |
| `-f`   | 为普通文件                                                   |
| `-g`   | 文件或目录具有 setgid 属性                                   |
| `-k`   | 文件或目录设置了 sticky 位                                   |
| `-l`   | 为符号链接                                                   |
| `-o`   | 文件被有效 UID 所有                                          |
| `-p`   | 文件是命名管道（FIFO）                                       |
| `-r`   | 文件可以被有效的 UID/GID 读取                                |
| `-s`   | 文件或目录存在且不为 0（返回字节数）                         |
| `-t`   | 文件句柄为 TTY（系统函数 `isatty()` 的返回结果，不能对文件名使用这个测试） |
| `-u`   | 文件或目录具有 setuid 属性                                   |
| `-w`   | 文件可以被有效的 UID/GID 写入                                |
| `-x`   | 文件可以被有效的 UID/GID 执行                                |
| `-z`   | 文件存在，大小为 0 （目录恒为false），即是否为空文件         |

## 12. Perl 目录操作

​	下面列出了一些操作目录的标准函数。

```perl
opendir DIRHANDLE, EXPR			# 打开文件
readdir DIRHANDLE						# 读取目录
rewinddir DIRHANDLE					# 定位指针到开头
telldir DIRHANDLE						# 返回目录的当前位置
seekdir DIRHANDLE, POS			# 定位指定到目录的 POS 位置
closedir DIRHANDLE					# 关闭目录
```

### 12.1. 显示文件

​	显示目录下的所有文件，可以使用 `glob` 操作符。

```perl
$dir = "/tmp/*";
my @files = glob($dir);
foreach (@files){
	print $_ . "\n"
}
```

### 12.2. 创建目录

​	可以使用 `mkdir` 函数创建一个新目录，执行前需要有足够的权限来创建目录。

```perl
mkdir ($dir);
```

### 12.3. 删除目录

​	可以使用 `rmdir` 函数来删除目录，执行该操作前需要有足够的权限，此外，要删除的目录必须是空目录。

```perl
rmdir ($dir);
```

### 12.4. 切换目录

​	可以使用 `chdir` 函数来切换当前目录，执行该操作需要有足够的权限。

```perl
chdir ($dir);
```

## 13. Perl 错误处理

### 13.1. if 语句

​	程序中变量 `$!` 返回了错误信息。

```perl
if (open(DATA, $file)) {
	...
}else{
	die "Error: Can't open file - $!";
}
```

​	上述代码可以简化为：

```perl
open(DATA, $file) || die "Error: Can't open file - $!";
```

### 13.2. unless 函数

​	`unless` 函数与 `if` 相反，只有在表达式返回 false 时才会执行。

```perl
unless (chdir($dir)){
	die "Error: Can't open directory - $!";
}
```

​	`unless` 语句在需要设置错误提醒时非常有用，也可以简化为：

```perl
die "Error: Can't open directory - $!" unless (chdir($dir));
```

### 13.3. 三元运算符

​	可以通过三元运算符来处理逻辑错误信息。

```perl
print(exist($hash{value}) ? "Exist" : "Non-existent", "\n");
```

### 13.4. warn 函数

​	`warn` 函数用于触发一个警告信息，不会有其他操作，输出到 `STDERR` 中，通常用于给用户提示。

```perl
chdir($dir) or warn "Can't change directory";
```

### 13.5. die 函数

​	`die` 函数类似于 `warn` ，但它会退出执行，一般用于错误信息的输出。

```perl
chdir($dir) or die "Can't change directory";
```

### 13.6. Carp 模块

​	在 Perl 脚本中，报告错误的常用方法是使用 `warn()` 或 `die()` 函数来报告或产生错误。而对于 Carp 模块，它可以对产生的消息提供额外级别的控制，尤其是在模块内部。

​	标准 Carp 模块提供了 `warn()` 和 `die()` 函数的替代方法，它们在提供错误定位方面提供更多信息，而且更加友好。当在模块中使用时，错误消息中包含模块名称和行号。

#### 13.6.1. carp 函数

​	`carp` 函数可以输出程序的跟踪信息，类似于 `warn` 函数，通常会将该信息发送到 `STDERR` 。

```perl
require Exporter;
carp error_msg;
```

#### 13.6.2. cluck 函数

​	`cluck` 函数与 `warn` 类似，提供了从错误处的栈回溯追踪。

```perl
require Exporter;
cluck error_msg;
```

#### 13.6.3. croak 函数

​	`croak` 函数与 `die` 类似，可以结束脚本。

```perl
require Exporter;
croak error_msg;
```

#### 13.6.4. confess 函数

​	`confess` 函数与 `die` 类似，但提供了从产生错误处的栈回溯追踪。

```perl
require Exporter;
confess error_msg;
```

## 14. Perl 特殊变量

​	Perl 语言中定义了一些特殊的变量，通常以 `$ @ %` 作为前缀，很多特殊的变量有一个很长的英文名，操作系统变量 `$!` 可以写为 `$OS_ERROR` 。如果想要使用英文名的特殊变量，需要在程序头部添加 `use English;`，可以使用具有描述性的英文特殊变量。

​	详见[官方文档](https://perldoc.perl.org/perlvar#SPECIAL-VARIABLES) 。

## 15. Perl 正则表达式

​	正则表达式（Regular Expression）描述了一种字符串匹配模式，Perl 语言的正则表达式功能非常强大，基本上是常用语言中最强大的。

​	匹配运算符为 `=~` ，左接需要源字符串，右接正则表达式。

### 15.1. 匹配操作符

​	匹配操作符 `m//` 用于匹配一个字符串语句或者一个正则表达式，返回一个逻辑真或假。m 可以省略，写作 `//` 。

```perl
$bar = "test";
$bar =~ m/te/;
```

#### 15.1.1. 模式匹配修饰符

| 修饰符 | 描述                                  |
| :----- | :------------------------------------ |
| `i`    | 忽略模式中的大小写                    |
| `m`    | 多行模式                              |
| `o`    | 仅赋值一次                            |
| `s`    | 单行模式，"." 匹配 "\n"（默认不匹配） |
| `x`    | 忽略模式中的空白                      |
| `g`    | 全局匹配                              |
| `cg`   | 全局匹配失败后，允许再次查找匹配串    |

#### 15.1.2. 正则表达式变量

​	Perl 处理完后会将匹配结果存在三个特殊变量中。

- **$`**：匹配部分的前一部分字符串；
- `$&`：匹配的字符串；
- `$'`：还没有匹配的剩余字符串。

### 15.2. 替换操作符

​	替换操作符 `s///` 是匹配操作符的扩展，使用新的字符串替换指定的字符串。

```perl
$string =~ s/PATTERN/REPLACEMENT/;
```

- `PATTERN`：匹配模式；
- `REPLACEMENT`：替换的字符串。

#### 15.2.1. 替换操作修饰符

| 修饰符 | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| i      | 取消大小写敏感性                                             |
| m      | 开始和结束会指字符串的每一行，每一行的开头是 `^`，结尾是 `$`（默认的正则开始 `^` 和结束 `$` 是对于整个字符串） |
| o      | 表达式只执行一次。                                           |
| s      | 默认的 `.` 代表除了换行符以外的任何字符，将会变成任意字符    |
| x      | 忽略表达式中的空白字符                                       |
| g      | 替换所有匹配的字符串                                         |
| e      | 替换字符串作为表达式                                         |

### 15.3. 转化操作符

```perl
$string =~ tr/a-z/A-Z/;
```

#### 15.3.1. 转化操作修饰符

| 修饰符 | 描述                         |
| :----- | :--------------------------- |
| `c`    | 转化所有未指定字符           |
| `d`    | 删除所有指定字符             |
| `s`    | 把多个相同的输出字符缩成一个 |

### 15.4. 更多正则表达式规则

​	详见[官方文档](https://perldoc.perl.org/perlre#Metacharacters) 。






















