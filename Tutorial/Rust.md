# Rust 教程

## 1. Rust 基础语法

### 1.1. 变量 & 常量

​	首先必须说明，Rust 是强类型语言，但具有自动判断变量类型的能力。这很容易让人与弱类型语言产生混淆。默认情况下，Rust 中的变量是不可变的，除非使用 `mut` 关键字声明为可变变量。

#### 1.1.1. 声明变量

​	需要使用 **let** 关键字。

```rust
// 声明不可变变量
let var_name: var_type = value;
// 声明可变变量
let mut var_name: var_type = value;
```

**注意：**

- 不可变变量并不是彻底不能改变，可以通过多次声明，**重新绑定**，更改所存储的值。
- 这是由于 Rust 语言为了高并发安全设计，防止变量随意更改不可追溯所造成的麻烦，引入了不可变变量的概念。
- 不可变变量的每一次重新绑定，debug 时都会被追溯，但是可变变量的值不可追溯。

#### 1.1.2.  声明常量

```rust
const var_name: var_type = value;
```

**注意：**

- 常量是彻底不可改变的值，也不能重新绑定。

### 1.2. 数据类型

​	Rust 是静态类型语言，在变量声明时，可以显式的指定类型，但通常可以依赖类型判断。

#### 1.2.1. 基本类型

​	包含：`i32`，`u32`，`f64`，`bool`，`char`。

### 1.3. 函数

#### 1.3.1. 函数定义

​	Rust 通过 `fn` 关键字定义函数，函数的返回类型通过 `->` 指定。

```rust
fn fn_name(var_1: var_type, var_2: var_type) ->return_type {
  // fn_body
}
```

​	如果没有返回值，类型默认为 `()`，即为空元组。

### 1.4. 控制流

#### 1.4.1. if 表达式

```rust
if condition {
  // if_body
} else {
  // else_body
}
```

#### 1.4.2. loop 表达式

​	`loop` 是 Rust 中的无限循环，可以使用 `break` 推出循环。

```rust
loop {
  // loop_body
}
```

#### 1.4.3. while 循环

```rust
while condition {
  // while_body
}
```

#### 1.4.4. for 循环

```rust
for condition {
	// for_body
}
```

### 1.5. 所有权（Ownership）

​	Rust 中的所有权是独特的内存管理机制，核心概念包括：所有权（ownership），借用（borrowing），引用（reference）。

#### 1.5.1. 所有权

- Rust 中的每个值都有一个所有者；
- 每个值在任意时刻只能有一个所有者；
- 当所有者超出作用域时，值会被删除。

```rust
// 值的所有权在 s1
let s1 = String::from("hello");
// s1 的所有权被转移给了s2，s1 的内存被释放
let s2 = s1; 
```

#### 1.5.2. 借用和引用

​	借用允许引用数据而不获取所有权，通过 `&` 符号实现。

```rust
// 值的所有权在 s1
let s1 = String::from("hello");
// 值的所有权仍然在 s1，但是 s2 借用了 s1 的值
let s2 = &s1;
```

### 1.6. 结构体（Structs）

​	结构体用于创建自定义类型，字段可以包含多种数据类型。

```rust
struct User {
    username: String,
    email: String,
    sign_in_count: u64,
    active: bool,
}
```

### 1.7. 枚举 (Enums)

​	枚举允许定义可能的几种数据类型中的一种。

```rust
enum IpAddrKind {
    V4,
    V6,
}
```

### 1.8. 模式匹配 (match)

​	`match` 是 Rust 中强大的控制流工具，类似于 `switch` 语句。

```rust
match coin {
  Coin::Penny => 1,
  Coin::Nickel => 5,
  Coin::Dime => 10,
  Coin::Quarter => 25,
}
```

### 1.9. 错误处理

​	Rust 有两种主要的错误处理方式：`Result<T, E>` 和 `Option<T>`。

#### 1.9.1. Result

```rust
enum Result<T, E> {
    Ok(T),
    Err(E),
}

fn divide(a: i32, b: i32) -> Result<i32, String> {
    if b == 0 {
        Err(String::from("Division by zero"))
    } else {
        Ok(a / b)
    }
}
```

#### 1.9.2. Option

```rust
fn get_element(index: usize, vec: &Vec<i32>) -> Option<i32> {
    if index < vec.len() {
        Some(vec[index])
    } else {
        None
    }
}
```

### 1.10. 所有权与借用的生命周期

​	Rust 使用生命周期来确保引用的有效性。生命周期标注用 `'a` 等来表示，但常见的情况下，编译器会自动推导。

### 1.11. 重影（Shadowing）

​	重影就是所谓"重新绑定"，指变量名称可以被重新使用的机制，重点在于每一次重新使用都可以追溯。

**注意：**重影与可变变量的重新赋值并不是一个概念。

- 可变变量的重新赋值只能在同类型间进行；
- 重影是指用同一个名字重新代表另一个变量实体，其类型、可变属性、值都可以变化。

## 2. Rust 数据类型

### 2.1. 整数型（Integer）

​	整数型简称整型，按照比特位长度和有无符号分为以下种类：

| 位长度  | 有符号 | 无符号 |
| :------ | :----- | :----- |
| 8-bit   | i8     | u8     |
| 16-bit  | i16    | u16    |
| 32-bit  | i32    | u32    |
| 64-bit  | i64    | u64    |
| 128-bit | i128   | u128   |
| arch    | isize  | usize  |

​	`isize` 和 `usize` 两种整数类型是用来衡量数据大小的，它们的位长度取决于所运行的目标平台，如果是 32 位架构的处理器将使用 32 位位长度整型。

### 2.2. 浮点数型（Floating-Point）

​	Rust 与其它语言一样支持 32 位浮点数 `f32` 和 64 位浮点数 `f64` 。默认情况下，64.0 将表示 64 位浮点数，因为现代计算机处理器对两种浮点数计算的速度几乎相同，但 64 位浮点数精度更高。

### 2.3. 数学运算

​	许多运算符号之后加上 `=` 号是自运算的意思。`sum += 1` 等同于 `sum = sum + 1`。

**注意：**Rust 不支持 `++` 和 `--`，因为这两个运算符出现在变量的前后会影响代码可读性，减弱了开发者对变量改变的意识能力。

### 2.4. 布尔型

​	布尔型用 `bool` 表示，值只能为 true 或 false。

### 2.5. 字符型

​	字符型用 `char` 表示。

​	Rust 的 `char` 类型大小为 4 个字节，代表 Unicode 标量值，这意味着它可以支持中文，日文和韩文字符等非英文字符，甚至表情符号和零宽度空格在 Rust 中都是有效的 char 值。

**注意：**由于中文文字编码有两种（GBK 和 UTF-8），所以编程中使用中文字符串有可能导致乱码的出现，这是因为源程序与命令行的文字编码不一致，所以在 Rust 中字符串和字符都必须使用 UTF-8 编码，否则编译器会报错。

### 2.6. 复合类型

​	元组是用一对 `( )` 包括的一组数据，可以包含不同种类的数据。

```rust
let tup: (i32, f64, u8) = (500, 6.4, 1);
```

​	数组是用一对 `[ ]` 包括的同类型数据，数组的初始化语法为 `let array_var: [data_type; size] = [...]`

```rust
let a = [1, 2, 3, 4, 5];
```

## 3. Rust 注释

​	Rust 中的注释方式与其它语言（C、Java）一样，支持两种注释方式。

```rust
// 这是第一种注释方式

/* 这是第二种注释方式 */

/*
 * 多行注释
 * 多行注释
 * 多行注释
 */
```

### 3.1. 说明文档

​	在 Rust 中使用 `//` 可以使其之后到第一个换行符的内容变成注释。在这种规则下，三个正斜杠 `///` 依然是合法的注释开始。所以 Rust 可以用 `///` 作为说明文档注释的开头。

```rust
/// Adds one to the number given.
///
/// # Examples
///
/// ```
/// let x = add(1, 2);
///
/// ```
```

## 4. Rust 函数

```rust
fn <fn_name> ( <var_list> ) { <fn_body> }
```

### 4.1. 函数参数

​	Rust 中定义函数如果需要具备参数必须声明参数**名称**和**类型**。

### 4.2. 语句和表达式

​	Rust 函数体由一系列可以以表达式（Expression）结尾的语句（Statement）组成。语句是执行某些操作且没有返回值的步骤，表达式有计算步骤且有返回值。Rust 中可以在一个用 `{}` 包括的块里编写一个较为复杂的表达式作为语句的结尾。

```rust
let y = {
	let x = 3;
	x + 1
};
```

​	块中可以使用函数语句，最后一个步骤是表达式，此表达式的结果值是整个表达式块所代表的值。这种表达式块叫做函数体表达式。

**注意：**`x + 1` 之后没有分号，否则它将变成一条语句！

### 4.3. 返回值

​	在参数声明之后用 `->` 来声明函数返回值的类型。在函数体中，随时都可以以 `return` 关键字结束函数运行并返回一个类型合适的值。但是 Rust 不支持自动返回值类型判断！

​	如果没有明确声明函数返回值的类型，函数将被认为是"纯过程"，不允许产生返回值，`return` 后面不能有返回值表达式。这样做的目的是为了让公开的函数能够形成可见的公报。

**注意：**函数体表达式并不能等同于函数体，它不能使用 `return` 关键字。

## 5. Rust 条件语句

```rust
if condition {
  // if_body
} else if condition{
  // else if_body
}	else {
	// else_body
}
```

​	程序中有条件 `if` 语句，`condition` 表达式不需要 `()` ，且不存在单语句不用加 `{}` 的规则，不允许使用一个语句代替一个块。

​	但是块中的语句可以是函数体表达式，即块中的语句可以有返回值作为语句的结尾。在 Rust 中，可以通过  `if-else` 结构实现类似三元表达式的效果。

```rust
let var = if condition {number1} else {number2};
```

## 6. Rust 循环

### 6.1. while 循环

​	`while` 循环是最典型的条件语句循环。

```rust
while condition {
  // while_body
}
```

​	在 C 语言中 `for` 循环使用三元语句控制循环，但是 Rust 中没有这种用法，需要用 while 循环来代替。

```rust
let mut i = 0; 
while i < 10 { 
    // 循环体 
    i += 1; 
}
```

### 6.2. for 循环

​	for 循环是最常用的循环结构，常用来遍历一个线性数据结构（比如数组）。

```rust
let a = [10, 20, 30, 40, 50];
for i in a.iter() {
  println!(i);
}
```

### 6.3. loop 循环

​	某个循环无法在开头和结尾判断是否继续进行循环，必须在循环体中间某处控制循环的进行。Rust 有原生无限循环结构 `loop`。

​	`loop` 循环可以通过 `break` 关键字类似于 `return` 一样使整个循环退出并给予外部一个返回值。

```rust
break i;
```

## 7. Rust 迭代器

### 7.1. 迭代器基本原则

- **惰性求值 (Laziness)**：Rust 中的迭代器是惰性的，意味着迭代器本身不会立即进行任何计算或操作，直到显式地请求数据。这使得迭代器在性能上表现良好，可以避免不必要的计算。
- **所有权和借用检查 (Ownership and Borrowing Checks)**：Rust 迭代器严格遵守所有权和借用规则，避免数据竞争和内存错误。迭代器的生命周期与底层数据相关联，确保数据的安全访问。
- **链式调用 (Chaining)**：Rust 迭代器支持链式调用，即可以将多个迭代器方法链接在一起进行组合操作，这使得代码简洁且具有高度可读性。
- **高效内存管理 (Efficient Memory Management)**：迭代器避免了不必要的内存分配，因为大多数操作都是惰性求值的，并且在使用时直接进行遍历操作。这对于处理大数据集合尤其重要。
- **抽象和通用性 (Abstraction and Generality)**：Rust 的迭代器通过 `Iterator` trait 实现抽象和通用性。任何实现了 `Iterator` trait 的类型都可以在不同的上下文中作为迭代器使用。此设计提高了代码的重用性和模块化。

### 7.2. 创建迭代器

​	最常见的方式是通过集合的 `.iter()`、`.iter_mut()` 或 `.into_iter()` 方法来创建迭代器：

- `.iter()`：返回集合的不可变引用迭代器；
- `.iter_mut()`：返回集合的可变引用迭代器；
- `.into_iter()`：将集合转移所有权并生成值迭代器。

### 7.3. 迭代器方法

​	Rust 的迭代器提供了丰富的方法来处理集合中的元素，其中一些常见的方法包括：

- `map()`：对每个元素应用给定的转换函数；
- `filter()`：根据给定的条件过滤集合中的元素；
- `fold()`：对集合中的元素进行累积处理；
- `skip()`：跳过指定数量的元素；
- `take()`：获取指定数量的元素；
- `enumerate()`：为每个元素提供索引。

### 7.4. 遍历迭代器

​	Rust 提供了 `for` 循环语法来遍历迭代器中的元素，是一种更加简介和直观的遍历方式。

```rust
for var in vec.iter() {
    // for_body
}
```

### 7.5. 适配器

#### 7.5.1. 消耗型适配器

​	有些适配器会使用迭代器直到它被完全消耗。

- `collect()`：将迭代器转换为集合（如向量、哈希集）。
- `sum()`：计算迭代器中所有元素的和。
- `product()`：计算迭代器中所有元素的乘积。
- `count()`：返回迭代器中元素的个数。

#### 7.5.2. 适配器

​	迭代器适配器允许你通过方法链来改变或过滤迭代器的内容，而不会立刻消耗它。

- `map()`：对每个元素应用某个函数，并返回一个新的迭代器。
- `filter()`：过滤出满足条件的元素。
- `take(n)`：只返回前 `n` 个元素的迭代器。
- `skip(n)`：跳过前 `n` 个元素，返回剩下的元素迭代器。

#### 7.5.3. 迭代器链

​	可以将多个迭代器适配器链接在一起，形成迭代器链。

#### 7.5.4. 收集器

​	使用 `collect` 方法将迭代器的元素收集到某种集合中。

### 7.6. 自定义迭代器

​	也可以为自己的类型实现 `Iterator` trait，只需定义 `next()` 方法即可。

```rust
// 定义自己的类型 Counter
struct Counter {

}

// 为 Counter 定义 Iterator
impl Iterator for Counter {
	type Item = usize;
  
  fn next(&mut self) -> Option<Self::Item> {
    // next defination
  }
}
```

### 7.7. 其他

#### 7.7.1. 并行迭代器

​	如果需要在多线程环境中并行化操作，rayon crate 提供了并行迭代器的支持，通过 `.par_iter()` 代替 `.iter()`，可以在多线程环境中加速迭代操作。

#### 7.7.2. 迭代器和生命周期

​	迭代器的生命周期与它所迭代的元素的生命周期相关联。迭代器可以借用元素，也可以取得元素的所有权。这在迭代器的实现中通过生命周期参数来控制。

#### 7.7.3. 迭代器与闭包

​	迭代器适配器经常与闭包一起使用，闭包允许你为迭代器操作提供定制逻辑。

#### 7.7.4. 迭代器和性能

​	迭代器通常是非常高效的，因为它们允许编译器做出优化。

## 8. Rust 闭包

​	Rust 中的闭包是一种匿名函数，可以捕获并存储其环境中的变量，允许在其定义的作用域之外访问变量，并且可以在需要时将其移动或借用给闭包。闭包在 Rust 中被广泛应用于函数式编程、并发编程和事件驱动编程等领域。

### 8.1. 闭包声明

```rust
|var, var, ...|{expression}
```

- **注解：** 可以有，也可以省略，Rust 编译器会根据上下文推断它们；
- **参数和返回值：** 可以有零个或多个参数，并且可以返回一个值；
- **闭包的调用：** 闭包可以像函数一样被调用。

### 8.2. 闭包特质

#### 8.2.1. 匿名函数

​	闭包在 Rust 中类似于匿名函数，可以在代码中以 `{}` 语法块的形式定义，使用 `||` 符号来表示参数列表。

#### 8.2.2. 捕获外部变量

​	闭包可以捕获周围环境中的变量，这意味着它可以访问定义闭包时所在作用域中的变量。

```rust
let x = 5;
let square = |num| num * x;
```

#### 8.2.3. 移动与借用

​	闭包可以通过 `move` 关键字获取外部变量的所有权，或者通过借用的方式获取外部变量的引用。

##### 借用变量

​	默认情况下，闭包会借用它捕获的环境中的变量，这意味着闭包可以使用这些变量，但不能改变它们的所有权。

##### 获取所有权

​	通过在闭包前添加 `move` 关键字，闭包会获取它捕获的环境变量的所有权。这意味着这些变量的所有权会从外部作用域转移到闭包内部，外部作用域将无法再使用这些变量。

```rust
let print_s = move || println!("{}", s);
```

### 8.3. 迭代器中的闭包

​	闭包在 Rust 中经常与迭代器一起使用，用于对集合中的元素进行处理。

```rust
let vec = vec![1, 2, 3];
let squared_vec: Vec<i32> = vec.iter().map(|x| x * x).collect();
```

### 8.4. 闭包作为参数和返回值

​	闭包可以作为参数传递给函数，也可以作为函数的返回值。

```rust
fn call_fn<F>(f: F) where F: Fn() {
    f();
}

fn find_first_positive(nums: &[i32], is_positive: impl Fn(i32) -> bool) -> Option<usize> {
    nums.iter().position(|&x| is_positive(x))
}
```

### 8.5. 闭包和错误处理

​	闭包可以返回 `Result` 或 `Option` 类型，并且可以处理错误。

### 8.6. 闭包和多线程

​	闭包可以用于多线程编程，因为它们可以捕获并持有必要的数据。

### 8.7. 其他

#### 8.7.1. 闭包和性能

​	Rust 的闭包是轻量级的，并且 Rust 的编译器会进行优化，使得闭包的调用接近于直接调用函数。

#### 8.7.2. 闭包和生命周期

​	闭包的生命周期与它们所捕获的变量的生命周期相关。Rust 的生命周期系统确保闭包不会比它们捕获的任何变量活得更长。

#### 8.7.3. 闭包的类型

​	闭包在 Rust 中是一种特殊的类型，称为 `Fn`、`FnMut` 或 `FnOnce`，它们分别表示不同的闭包特性：

- `Fn`：闭包不可变地借用其环境中的变量；
- `FnMut`：闭包可变地借用其环境中的变量；
- `FnOnce`：闭包获取其环境中的变量的所有权，只能被调用一次。

## 9. Rust 所有权

​	它是 Rust 语言为高效使用内存而设计的语法机制。所有权概念是为了让 Rust 在编译阶段更有效地分析内存资源的有用性以实现内存管理而诞生的概念。

### 9.1. 所有权规则

- Rust 中的每个值都有一个变量，称为其所有者；
- 一次只能有一个所有者；
- 当所有者不在程序运行范围时，该值将被删除。

### 9.2. 变量范围

​	变量范围是变量的一个属性，其代表变量的可行域，默认从声明变量开始有效直到变量所在域结束。

```rust
{
    // 在声明以前，变量 s 无效
    let s = "wxss";
    // 这里是变量 s 的可用范围
}
// 变量范围已经结束，变量 s 无效
```

### 9.3. 变量与数据交互的方式

#### 9.3.1. 移动

##### 栈（stack）中移动

​	当数据是**基本数据**类型的数据，不需要存储到**堆（heap）**中，仅在栈中的数据的**移动**方式是直接**复制**，这不会花费更长的时间或更多的存储空间。

```rust
let x = 5;
let y = x;
```

​	这个程序将值 5 绑定到变量 x，然后将 x 的值复制并赋值给变量 y。现在**栈（stack）**中将有两个值 5。**基本数据**类型有这些：

- **整数类型：**`i32` 、 `u32` 、 `i64` 等；
- **布尔类型：**`bool`，值为 `true` 或 `false` ；
- **浮点类型：**`f32` 和 `f64`；
- **字符类型：**`char`；
- **元组：**仅包含以上类型数据的。

##### 堆（heap）中移动

​	当数据较大，或者数据长度不确定时，需要在**堆（heap）**中存储值，变量仍然存在**栈（stack）**中。

```rust
let s1 = String::from("hello");
let s2 = s1;
```

​	当变量超出范围时，Rust 自动调用释放资源函数并清理该变量的**堆内存**。为了确保安全，在给 `s2` 赋值时 `s1` 已经无效了。

#### 9.3.2. 克隆

​	Rust 会尽可能地降低程序的运行成本，所以默认情况下，长度较大的数据存放在堆中，且采用移动的方式进行数据交互。但如果需要将数据单纯的复制一份以供他用，可以使用数据的第二种交互方式：克隆。

```rust
let s1 = String::from("hello");
let s2 = s1.clone();
```

### 9.4. 涉及函数的所有权机制

#### 9.4.1. 函数参数所有权

​	如果将变量当作参数传入函数，那么它和移动的效果是一样的。

```rust
fn main() {
    let s = String::from("hello");
    // s 被声明有效

    takes_ownership(s);
    // s 的值被当作参数传入函数
    // 所以可以当作 s 已经被移动，从这里开始已经无效

    let x = 5;
    // x 被声明有效

    makes_copy(x);
    // x 的值被当作参数传入函数
    // 但 x 是基本类型，依然有效
    // 在这里依然可以使用 x 却不能使用 s

} // 函数结束, x 无效, 然后是 s. 但 s 已被移动, 所以不用被释放


fn takes_ownership(some_string: String) { 
    // 一个 String 参数 some_string 传入，有效
    println!("{}", some_string);
} // 函数结束, 参数 some_string 在这里释放

fn makes_copy(some_integer: i32) { 
    // 一个 i32 参数 some_integer 传入，有效
    println!("{}", some_integer);
} // 函数结束, 参数 some_integer 是基本类型, 无需释放
```

#### 9.4.2. 函数返回值所有权

​	被当作函数返回值的变量所有权将会被移动出函数并返回到调用函数的地方，而不会直接被无效释放。

```rust
fn main() {
    let s1 = gives_ownership();
    // gives_ownership 移动它的返回值到 s1

    let s2 = String::from("hello");
    // s2 被声明有效

    let s3 = takes_and_gives_back(s2);
    // s2 被当作参数移动, s3 获得返回值所有权
} // s3 无效被释放, s2 被移动, s1 无效被释放.

fn gives_ownership() -> String {
    let some_string = String::from("hello");
    // some_string 被声明有效

    return some_string;
    // some_string 被当作返回值移动出函数
}

fn takes_and_gives_back(a_string: String) -> String { 
    // a_string 被声明有效

    a_string  // a_string 被当作返回值移出函数
}
```

### 9.5. 引用与租借

#### 9.5.1. 引用

​	`&` 运算符可以取变量的"引用"。当一个变量的值被引用时，变量本身不会被认定无效。

- 引用不会获得值的所有权；

- 引用只能租借（Borrow）值的所有权；

- 引用本身也是一个类型并具有一个值，这个值记录的是所引用变量所在的位置；
- 如果被引用的变量被移动，那么引用也会失效，需要重新引用。

#### 9.5.2. 垂直引用（Dangling References）

​	如果放在有指针概念的编程语言里它就指的是那种没有实际指向一个真正能访问的数据的指针（注意，不一定是空指针，还有可能是已经释放的资源）。它们就像失去悬挂物体的绳子，所以叫"垂悬引用"。"垂悬引用"在 Rust 语言里不允许出现，如果有，编译器会发现它。

```rust
fn main() {
	let reference_to_nothing = dangle();
}

fn dangle() -> &String {
	let s = String::from("hello");  	// s 变量被声明

  &s  	// 返回了 s 变量的引用
}  // s 变量被释放
```

​	局部变量 `s` 在函数结束后被释放了，而其引用被返回了，因此无法确定这个引用所指向的值，发生

## 10. Rust Slice（切片）类型

​	切片（Slice）是对数据值的部分引用。

### 10.1. 字符串切片

​	最简单、最常用的数据切片类型是字符串切片（String Slice）。

```rust
let s = String::from("broadcast");
let part1 = &s[0..5];
let part2 = &s[5..9];
```

​	Rust 中的字符串类型实质上记录了字符在内存中的起始位置和其长度。使用 `..` 表示范围的，`x..y` 表示 $[x, y)$ 的数学含义。

#### 10.1.1 String & str

​	在 Rust 中有两种常用的字符串类型：`str` 和 `String`。凡是用双引号包括的字符串常量整体的类型性质都是 `&str`。下面的 s 就是一个 `&str` 类型的变量。

```rust
let s = "hello";
```

​	`String` 类型是 Rust 标准公共库提供的一种数据类型，它的功能更完善，支持字符串的追加、清空等实用的操作。`String` 和 `str` 除了同样拥有一个字符开始位置属性和一个字符串长度属性以外还有一个容量（capacity）属性。`String` 和 `str` 都支持切片。

**注意：**切片结果必须是引用类型，开发者必须自己明示这一点。

```rust
let slice = &s[0..3];
```

### 10.2. 非字符串切片

​	除了字符串以外，其他一些线性数据结构也支持切片操作，像是数组。

```rust
let arr = [1, 3, 5, 7, 9];
let part = &arr[0..3];
```

## 11. Rust 结构体

​	Rust 中的结构体（Struct）与元组（Tuple）都可以将若干个类型不一定相同的数据捆绑在一起形成整体。结构体的每个成员和其本身都有一个名字，这样访问它成员的时候就不用记住下标了；元组常用于非定义的多值传递。结构体的每个成员叫做"字段"。

### 11.1. 结构体定义

```rust
struct Site {
    domain: String,
    name: String,
    nation: String,
    found: u32
}
```

**注意：**在 Rust 里 `struct` 语句仅用来定义，不能声明实例，结尾不需要 `;` 符号，而且每个字段定义之后用 **,** 分隔。

### 11.2. 结构体实例

​	Rust 很多地方受 JavaScript 影响，在实例化结构体的时候用 JSON 对象的 `key: value` 语法来实现定义.

```rust
let struct_name = struct_type {
	key1: value1,
  key2: value2,
  ... ,
  keyn: valuen
};
```

​	如果正在实例化的结构体有字段名称和现存变量名称一样的，可以简化书写。

```rust
let struct_name = struct_type {
  key1,
  key2,
  ... ,
  keyn: valuen
}
```

​	如果想要新建的结构体实例，大部分属性与一个已有实例的相同，只需要修改其中的几项。

```rust
let new_struct_name = strct_type {
	key1: value1,
  key2: value2,
  ... ,
  ..exist_struct_name
}
```

### 11.3. 元组结构体

​	元组结构体是一种形式是元组的结构体，与元组的区别是它有名字和固定的类型格式。它存在的意义是为了处理那些需要定义类型（经常使用）又不想太复杂的简单数据。元组结构体对象的**使用方式**和元组一样，通过 `.` 和**下标**来进行访问。

```rust
struct Color(u8, u8, u8);
struct Point(f64, f64);

let black = Color(0, 0, 0);
let origin = Point(0.0, 0.0);

println!("black = ({}, {}, {})", black.0, black.1, black.2);
println!("origin = ({}, {})", origin.0, origin.1);
```

### 11.4. 结构体所有权

​	结构体必须掌握字段值所有权，因为结构体失效的时候会释放所有字段。但这不意味着结构体中不可以定义引用类型。

### 11.5. 输出结构体

​	调试中，完整地显示出一个结构体实例是非常有用的， Rust 提供了一个方便地输出一整个结构体的方法。

```rust
#[derive(Debug)]

println!("rect1 is {:?}", rect1);
```


​	先导入调试库 `#[derive(Debug)]` ，之后在 `println` 和 `print` 宏中就可以用 `{:?}` 占位符输出一整个结构体。

```shell
rect1 is Rectangle { width: 30, height: 50 }
```

​	如果属性较多的话可以使用另一个占位符 `{:#?}` 。

```shell
rect1 is Rectangle {
    width: 30,
    height: 50
}
```

### 11.6. 结构体方法

​	方法（Method）和函数（Function）类似，只不过它是用来操作结构体实例的。

Rust 语言不是面向对象的，从它所有权机制的创新可以看出这一点。但是面向对象的珍贵思想可以在 Rust 实现。

​	结构体方法的第一个参数必须是 `&self`，不需声明类型，因为 `self` 不是一种风格而是关键字。

```rust
struct Rectangle {
    width: u32,
    height: u32
}
   
impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}
```

**注意：**结构体 impl 块可以写几次，效果相当于它们内容的拼接！

### 11.7. 单元结构体

​	结构体可以只作为一种象征而无需任何成员，我们称这种没有身体的结构体为单元结构体（Unit Struct）。

```rust
struct UnitStruct;
```

## 12. Rust 枚举类

### 12.1. 枚举类定义

```rust
enum name {
  prop1(type),
  prop2(type),
  ... ,
  propn(type)
}
// 或者
enum name {
  prop1{prop1_name: value},
	prop2{prop2_name: value}  
}
```

### 12.2 枚举类使用

```rust
let var_name = enum_name::prop1(type_value);
```

### 12.3. match 语法

​	枚举的目的是对某一类事物的分类，分类的目的是为了对不同的情况进行描述，Rust 通过 `match` 语句来实现分支结构。

```rust
match 枚举类实例 {
    分类1 => 返回值表达式,
    分类2 => 返回值表达式,
    ...
}
```

​	`match` 除了能够对枚举类进行分支选择以外，还可以对**整数**、**浮点数**、**字符**和**字符串切片**引用（`&str`）类型的数据进行分支选择。其中，浮点数类型被分支选择虽然合法，但不推荐这样使用，因为精度问题可能会导致分支错误。对非枚举类进行分支选择时必须注意处理**例外**情况，例外情况用下划线 `_` 表示。

```rust
match t {
  "abc" => println!("Yes"),
  _ => {},
}
```

### 12.4. Option 枚举类

​	`Option` 是 Rust 标准库中的枚举类，这个类用于填补 Rust 不支持 `null` 引用的空白。

​	许多语言支持 `null` 的存在（C/C++、Java），这样很方便，但也制造了极大的问题，`null` 的发明者也承认这一点，"一个方便的想法造成累计 10 亿美元的损失"。`null` 经常在开发者把一切都当作不是 `null` 的时候给予程序致命一击：毕竟只要出现一个这样的错误，程序的运行就要彻底终止。为了解决这个问题，很多语言默认不允许 `null`，但在语言层面支持 `null` 的出现（常在类型前面用 `?` 符号修饰）。

​	Rust 在语言层面**彻底不允许**空值 `null` 的存在，但无奈null 可以高效地解决少量的问题，所以 Rust 引入了 `Option` 枚举类。

```rust
enum Option<T> {
    Some(T),
    None,
}
```

​	如果需要定义一个可以为空值的类：

```rust
let opt = Option::Some("Hello");
```

​	如果一个变量开始时为空值，需要告诉编译器，当它不为空时的类型：

```rust
let opt: Option<&str> = Option::None;
```

**注意：**这种设计会让空值编程变困难，但这正式构建一个稳定高效系统所需要的。由于 `Option` 是 Rust 编译器默认引入的，在使用时可以省略 `Option::` 直接写 `None` 或者 `Some()`。

### 12.5. if let 语法

​	`if let` 语法可以认为是只区分两种情况的 `match` 语句的"语法糖"（语法糖指的是某种语法的原理相同的便捷替代品）。当源变量等于匹配值时，与不等于时，分别执行对应语句块。

```rust
if let match_value = source_var {
  // block
} else {
	//block
}
```

​	下面是一个使用 `match` 判断变量值的语法。

```rust
let i = 0;
match i {
  0 => println!("zero"),
  _ => {},
}
```

​	现在用 `if let` 语法缩短这段代码。

```rust
let i = 0;
if let 0 = i {
    println!("zero");
```

## 13. Rust 组织管理

​	Rust 中有三个重要的组织概念：箱、包、模块。

### 13.1. 箱（Crate）

- "箱"是二进制程序文件或者库文件，存在于"包"中；
- "箱"是树状结构的，它的树根是编译器开始运行时编译的源文件所编译的程序；

**注意：**"二进制程序文件"不一定是"二进制可执行文件"，只能确定是是包含目标机器语言的文件，文件格式随编译环境的不同而不同。

### 13.2. 包（Package）

- 当使用 Cargo 执行 `new` 命令创建 Rust 工程时，工程目录下会建立一个 `Cargo.toml` 文件；
- 工程的实质就是一个包，包名即是工程名，包必须由一个 `Cargo.toml` 文件来管理，该文件描述了包的基本信息以及依赖项；

- 一个包最多包含一个库"箱"，可以包含任意数量的二进制"箱"，但是至少包含一个"箱"（不管是库还是二进制"箱"）；

- 当使用 `cargo new` 命令创建完包之后，src 目录下会生成一个 `main.rs` 源文件，Cargo 默认这个文件为二进制箱的根，编译之后的二进制箱将与包名相同。

### 13.3. 模块（Module）

​	对于一个软件工程来说，往往按照所使用的编程语言的组织规范来进行组织，组织模块的主要结构往往是树。Rust 中的组织单位是模块（Module）。

```rust
mod module_name1{
  mod module_name2{
    fn fn_name1{}
	}
  mod module_name3{
    fn fn_name2{}
  }
  ...
}
```

​	Rust 中的路径分隔符是 `::` ，路径分为绝对路径和相对路径。绝对路径从 `crate` 关键字开始描述；相对路径从 `self` 或 `super` 关键字或一个标识符开始描述。

```rust
// 绝对路径
crate::module_name1::module_name2::fn_name1();
// 相对路径
module_name1::module_name2::fn_name1();
```

**注意：**如果在主函数中使用路径引用目标函数，外部的模块和函数都是私有的，不允许被访问。

### 13.4. 访问权限

​	Rust 中有两种简单的访问权：公共（public）和私有（private），默认情况下，如果不加修饰符，模块中的成员访问权将是私有的。如果想使用公共权限，需要使用 `pub` 关键字，对于私有的模块，只有在与其平级的位置或下级的位置才能访问，不能从其外部访问。

**注意：**

- 如果模块中定义了**结构体**，结构体除了其本身是私有的以外，其字段也默认是私有的，所以如果想使用模块中的结构体以及其字段，需要 `pub` 声明；
- 如果模块中定义了**枚举类**，枚举类自身是私有的，但是其包含的字段是公开的。

### 13.5. 难以发现的模块

​	在 Rust 中，模块就像是 Java 中的类包装，每一个 Rust 文件的内容都是一个"难以发现"的模块。如果需要使用另一个文件内的函数，可以通过文件名引入“隐藏”的模块。

​	例如，现在有两个文件，一个是入口文件 `main.rs` ，另一个是一个模块文件，文件名为 `module.rs` 。

```rust
// 在 main.rs 中，通过引用模块的方式使用 module.rs 中的函数
mod module.rs

fn main() {
  module.rs::fn_name();
}
```

### 13.6. use & as 关键字

​	`use` 关键字能够将模块标识符引入当前作用域，这样就解决了局部模块路径过长的问题。

```rust
use crate::module_name1::module_name2::fn_name1;

fn main() {
	fn_name1;	// use 将标识符 fn_name1 引入作用域，所以可以直接使用名字
}
```

​	有些情况下，在不同的路径下，存在两个相同的名称，且同样需要导入。如果使用 `use` 关键字直接导入，会引起冲突，可以使用 `as` 关键字为标识符添加别名。

```rust
use crate::module_name1::module_name2::fn_name1;
use crate::module_name3::fn_name1 as module3_fn_name1;
```

### 13.7. 引用标准库

​	Rust 官方标准库字典：https://doc.rust-lang.org/stable/std/all.html

```rust
use std::f64::consts::PI;
```

## 14. Rust 错误处理

​	Rust 有一套独特的处理异常情况的机制，它并不像其它语言中的 `try` 机制那样简单。

​	首先，程序中一般会出现两种错误：**可恢复错误**和**不可恢复错误**。可恢复错误的典型案例是文件访问错误，如果访问一个文件失败，有可能是因为它正在被占用，是正常的，可以通过等待来解决；不可恢复错误是由编程中无法解决的逻辑错误导致的，例如访问数组末尾以外的位置。

​	对于可恢复错误用 `Result<T, E>` 类来处理，对于不可恢复错误使用 `panic!` 宏来处理。

### 14.1. 不可恢复错误

```rust
fn main() {
  panic!("error occured");
  println!("Hello, Rust");
}
```

​	运行结果：

```shell
thread 'main' panicked at 'error occured', src\main.rs:3:5
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace.
```

​	很显然，程序并不能如约运行到 `println!("Hello, Rust")` ，而是在 `panic!` 宏被调用时停止了运行。不可恢复的错误一定会导致程序受到致命的打击而终止运行。

​	上述报错说明，可以通过使用环境变量 `RUST_BACKTRACE=1` 运行程序，以显示回溯。**回溯**是不可恢复错误的另一种处理方式，它会展开运行的栈并输出所有的信息，然后程序依然会退出。可以根据栈打印的信息，找到编写的 `panic!` 宏触发的错误。

### 14.2. 可恢复的错误

​	在 Rust 中通过 `Result<T, E>` 枚举类作返回值来进行异常表达。在 Rust 标准库中可能产生异常的函数的返回值都是 `Result` 类型的。

```rust
enum Result<T, E> {
    Ok(T),
    Err(E),
}
```

​	如果想使一个可恢复错误按不可恢复错误处理，`Result` 类提供了两个办法：`unwrap()` 和 `expect(message: &str)` 。这两个方法的区别仅在于 `except` 可以向 `panic` 发送一段指定的错误信息。

### 14.3. 可恢复的错误的传递

​	当自定义的函数可能会出现错误时，也可以通过返回 `Result` 类的方式返回错误。Rust 中可以在 `Result` 对象后添加 `?` 操作符将同类的 `Err` 直接传递出去。

​	`?` 符的实际作用是将 `Result` 类非异常的值直接取出，如果有异常就将异常 `Result` 返回出去。所以，`?` 符仅用于返回值类型为 `Result<T, E>` 的函数，其中 `E` 类型必须和 `?` 所处理的 `Result` 的 `E` 类型一致。

### 14.4. kind 方法

​	Rust 中，如果需要判断 `Result` 的 `Err` 类型，可以使用 `kind()` 函数获取 `Err` 类型。

```rust
Err(e) => {
  match e.kind() {
    io::ErrorKind::NotFound => {
      println!("No such file");
    },
    _ => {
      println!("Cannot read the file");
    }
  }
}	
```

## 15. Rust 泛型与特性

​	泛型是一个编程语言不可或缺的机制，泛型机制是编程语言用于表达类型抽象的机制，一般用于功能确定、**数据类型待定**的类，如链表、映射表等。

### 15.1. 函数泛型

```rust
// 将具体的类型替换为抽象类型 T，用于处理多种类型的输入
fn fn_name(var1: &[T]) -> T {
  //	fn_body
}
```

### 15.2. 结构体 & 枚举类泛型

#### 15.2.1. 泛型定义

​	Rust 中的结构体和枚举类都可以实现泛型机制，之前的 `Option` 和 `Result` 枚举类就是泛型的。

```rust
struct Point<T> {
    x: T,
    y: T
}

enum Option<T> {
    Some(T),
    None,
}

enum Result<T, E> {
    Ok(T),
    Err(E),
}
```

​	如果需要为结构体或者枚举类的不同字段设置不同的类型，可以使用多个泛型标识符。

```rust
struct Point<T1, T2> {
	x: T,
  y: T
}
```

#### 15.2.2. 结构体 & 枚举类方法泛型定义

​	结构体与枚举类都可以定义方法，那么方法也应该实现泛型的机制，否则泛型的类将无法被有效的方法操作。

```rust
struct Point<T> {
  x: T,
  y: T,
}

impl<T> Point<T> {
  fn x(&self) -> &T {
    &self.x
  }
}
```

​	`impl` 块本身的泛型并没有阻碍其内部方法具有泛型的能力，即 `impl` 内部的方法不需要使用与其相同的泛型标识符。

```rust
impl<T, U> Point<T, U> {
    fn mixup<V, W>(self, other: Point<V, W>) -> Point<T, W> {
        Point {
            x: self.x,
            y: other.y
        }
    }
}
```

### 15.3. 特性

​	特性（trait）概念接近于 Java 中的接口（Interface），但两者不完全相同。特性与接口**相同**的地方在于，它们都是一种行为规范，可以用于标识哪些类有哪些方法；**不同**的地方在于，接口只能规范方法而不能定义方法，但特性可以定义方法作为默认方法，因为是"默认"，所以对象既可以重新定义方法，也可以不重新定义方法使用默认的方法。

#### 15.3.1. 特性定义

​	下面的代码表示，特性 `Descriptive` 规定了实现者必需有 `describe(&self) -> String` 方法。

```rust
trait Descriptive {
    fn describe(&self) -> String;
}
```

​	实现者的实现语法如下。

```rust
impl <trait_name> for <type_name>
```

**注意：**Rust 同一个类可以实现多个特性，每个 `impl` 块只能实现一个。

#### 15.3.2. 默认特性

​	Rust 中的特性可以在定义的时候，实现一个默认方法。

```rust
trait Descriptive {
    fn describe(&self) -> String {
    	// fn_body
    }
}
```

#### 15.3.3. 特性参数

​	如果需要在 Rust 中，将一个函数作为参数传递，可以通过传递特性参数实现。

```rust
fn fn_name(object: impl Descriptive) {
    // fn_name_body
}
```

​	任何实现了 `Descriptive` 特性的对象都可以作为这个函数的参数，这个函数没必要了解传入对象有没有其他属性或方法，只需要了解它一定有 `Descriptive` 特性规范的方法就可以了。当然，此函数内也**无法使用**其他的属性与方法。

​	也可以用如下的等效语法实现。

```rust
fn fn_name<T: Descriptive>(object: T) {
    // fn_name_body
}
```

​	特性作类型表示时如果涉及**多个特性**，可以用 `+` 符号表示。

```rust
fn fn_name(item: impl Summary + Display)
// 或者
fn fn_name<T: Summary + Display>(item: T)
```

**注意：**仅用于表示类型的时候，并不意味着可以在 impl 块中使用。

#### 15.3.4. 特性返回值

```rust
fn person() -> impl Descriptive {
  Person {
    name: String::from("Cali"),
    age: 24
  }
}
```

**注意：**特性做返回值，只接受实现了该特性的对象作为返回值，并且同一个函数中，返回值类型必须是同一个实现了该特性的对象，不能是不同的对象。

#### 15.3.5. 有条件实现

​	`impl` 功能十分强大，可以用它实现类的方法。但对于泛型类来说，有时我们需要区分一下它所属的泛型已经实现的方法来决定它接下来该实现的方法。

```rust
struct A<T> {}

impl<T: B + C> A<T> {
    fn d(&self) {}
}
```

​	这段代码表明，`A<T>` 类型只有在实现了特性 `B` 和 `C` 的条件下，才实现此 `impl` 块。

## 16. Rust 生命周期

​	Rust 生命周期机制是与所有权机制同等重要的资源管理机制，之所以引入这个概念主要是应对复杂类型系统中资源管理的问题，引用是对待复杂类型时必不可少的机制，毕竟复杂类型的数据不能被处理器轻易地复制和计算。

### 16.1. 生命周期注释

​	是描述引用生命周期的办法，虽然这样并**不能够改变**引用的生命周期，但可以在合适的地方声明两个引用的生命周期一致。生命周期注释用单引号开头，跟着一个小写字母单词。

```rust
&i32					// 常规引用
&'a i32				// 含有生命周期注释的引用
&'a mut i32 	// 可变型含有生命周期注释的引用
```

### 16.2. 静态生命周期

​	生命周期注释有一个特别的：`'static` 。所有用双引号包括的字符串常量所代表的精确数据类型都是 `&'static str` ，`'static` 所表示的生命周期从程序运行开始到程序运行结束。

## 17. Rust 文件与 IO

### 17.1. 接收命令行参数

​	在 Rust 中主函数是个无参函数，环境参数需要开发者通过 `std::env` 模块取出。

```rust
let args = std::env::args();
```

​	在 `launch.json` ，找到 `"args": []`，这里可以设置运行时的参数。

### 17.2. 命令行输入

​	在 Rust 中，`std::io` 模块提供了标准输入（可认为是命令行输入）的相关功能。`std::io::Stdin` 包含 `read_line` 读取方法，可以读取一行字符串到缓冲区，返回值都是 `Result` 枚举类，用于传递读取中出现的错误，所以常用 `expect` 或 `unwrap` 函数来处理错误。

```rust
use std::io::stdin;

fn main() {
	let mut str_buf = String::new();
  stdin().read_line(&mut str_buf).expect("Failed to read line.");
  println!("Your input line is **\n**{}", str_buf);
}
```

**注意**：目前 Rust 标准库还没有提供**直接**从命令行读取数字或格式化数据的方法，可以读取一行字符串并使用字符串识别函数处理数据。

### 17.3. 文件读取

#### 17.3.1. 一次性读取

​	在 Rust 中读取内存可容纳的一整个文件，`std::fs` 模块中的 `read_to_string` 方法可以轻松完成文本文件的读取；但如果要读取的文件是二进制文件，可以用 `std::fs::read` 函数读取 `u8` 类型集合。

#### 17.3.2. 流读取

​	以上两种方式是一次性读取，十分适合 Web 应用的开发。但是对于一些底层程序来说，传统的按流读取的方式依然是无法被取代的，因为更多情况下文件的大小可能远超内存容量。

- `std::fs` 模块中的 `File` 类是描述文件的类，可以用于打开文件；
- 在打开文件之后，可以使用 `File` 的 `read` 方法按流读取文件的下面一些字节到缓冲区（缓冲区是一个 u8 数组）；
- 读取的字节数等于缓冲区的长度。

**注意：**`std::fs::File` 的 `open` 方法是**只读**打开文件，并且没有配套的 `close` 方法，因为 Rust 编译器可以在文件不再被使用时**自动关闭**文件。

### 17.4. 文件写入

#### 17.4.1. 一次性写入

​	与一次性读取类似，可以使用 `std::fs::write` 函数一次性写入内容，但是这种写入是覆盖式的，目标文件的内容将被覆盖为本次执行的内容，之前的内容将丢失，如果文件不存在，会创建文件。

#### 17.4.2. 流写入

##### 新建写入

​	可以使用 `std::fs::File::create` 函数，新建一个对应文件，并使用 `write` 函数覆盖式写入内容。

```rust
let mut file = File::create("D:\\text.txt").unwrap();
file.write(b"FROM RUST PROGRAM").unwrap();
```

**注意**：打开的文件一定存放在可变的变量中才能使用 `File` 的方法。

##### 追加写入

​	`File` 类中不存在 `append` 静态方法，作为替代，可以使用 `OpenOptions` 来实现用特定方法打开文件。

```rust
let mut file = OpenOptions::new().append(true).open("D:\\text.txt")?;
file.write(b" APPEND WORD")?;
```

​	这种方式写入的内容将被添加至文件末尾。

### 17.5. OpenOptions 方法

​	`OpenOptions` 是一个灵活的打开文件的方法，可以设置打开权限，除 `append` 权限以外还有 `read` 权限和 `write` 权限。如果以读写权限打开一个文件，那么添加的内容将从第一个字节开始替换原有的内容。

```rust
let mut file = OpenOptions::new().read(true).write(true).open("D:\\text.txt")?;
file.write(b"COVER")?;
```

## 18. Rust 集合与字符串

### 18.1. 向量

​	向量（Vector）是一个存放多值的单数据结构，该结构将相同类型的值线性的存放在内存中。

```rust
let vector: Vec<i32> = Vec::new(); // 创建类型为 i32 的空向量
let vector = vec![1, 2, 4, 8];     // 通过数组创建向量
```

​	 `push` 方法用于追加单个元素。

```rust
vector.push(12);
```

​	 `append` 方法用于将一个向量拼接到另一个向量尾部。

```rust
v1.append(&mut v2);
```

​	`get` 方法用于取出向量中的值。

```rust
vector.get(1);
```

​	由于向量的长度无法从逻辑上判断，`get` 方法无法保证一定取到值，因此返回值是 `Option` 枚举类，有可能为空。

### 18.2. 字符串

#### 18.2.1. 字符串方法

##### 字符串转换

```rust
let one = 1.to_string();         // 整数到字符串
let float = 1.3.to_string();     // 浮点数到字符串
let slice = "slice".to_string(); // 字符串切片到字符串
```

##### 字符串追加

```rust
s.push_str("oob");	// 追加字符串切片
s.push("!");	// 追加字符
```

##### 字符串拼接

```rust
s3 = s1 + s2;
```

​	或者可以使用 `format!` 宏。

```rust
let s = format!("{}-{}-{}", s1, s2, s3);
```

##### 字符串长度

```rust
// 统计字符串字节长度
let len = s.len();
// 统计字符串字符长度
let len = s.chars().count();
```

​	例如，同样的两个字符串”你好“，`len` 统计结果为 6，这是因为中文是 `UTF-8` 编码的，每个字符 3 个字节，一共 6 个字节；而 `chars().count()` 统计结果为 2，因为是两个字符。统计字符的速度比统计字节的速度慢得多。

##### 字符串取单个字符

```rust
let a = s.chars().nth(2);
```

**注意：**`nth` 函数是从迭代器中取出某值的方法，不要在遍历中这样使用，因为 `UTF-8` 每个字符的长度不一定相等。

### 18.3. 映射表

​	映射表（Map）在其他语言中广泛存在。其中应用最普遍的就是键值散列映射表（Hash Map）。`insert` 方法和 `get` 方法是映射表最常用的两个方法。

```rust
use std::collections::HashMap;

let mut map = HashMap::new();

map.insert("color", "red");
map.insert("size", "10 m^2");

println!("{}", map.get("color").unwrap());
```

​	Rust 的映射表是十分方便的数据结构，当使用 `insert` 方法添加新的键值对的时候，如果已经存在相同的键，会直接覆盖对应的值。如果需要在确认当前不存在某个键时才执行的插入动作：

```rust
map.entry("color").or_insert("red")
```

## 19. Rust 面向对象

​	面向对象的编程语言通常实现了数据的封装与继承并能基于数据调用方法。Rust 不是面向对象的编程语言，但这些功能都得以实现。

### 19.1. 封装

​	封装就是对外显示的策略，在 Rust 中可以通过模块的机制来实现最外层的封装，并且每一个 Rust 文件都可以看作一个模块，模块内的元素可以通过 `pub` 关键字对外明示，可以使用结构体或枚举类来实现类的功能。

### 19.2. 继承

​	继承是多态（Polymorphism）思想的实现，多态指的是编程语言可以处理多种类型数据的代码。在 Rust 中，通过特性（trait）实现多态。但是特性无法实现属性的继承，只能实现类似于"接口"的功能，所以想继承一个类的方法最好在"子类"中定义"父类"的实例。

​	总结地说，Rust **没有**提供跟继承有关的语法糖，也没有官方的继承手段，但灵活的语法依然**可以实现**相关的功能。

## 20. Rust 并发编程

​	安全高效的处理并发是 Rust 诞生的目的之一，主要解决的是服务器高负载承受能力。

### 20.1. 线程

​	线程（thread）是一个程序中独立运行的一个部分。线程不同于进程（process）的地方是线程是程序以内的概念，程序往往是在一个进程中执行的，在有操作系统的环境中进程往往被交替地调度得以执行；线程则在进程以内由程序进行调度。由于线程并发很有可能出现并行的情况，所以在并行中可能遇到的死锁、延宕错误常出现于含有并发机制的程序。为了解决这些问题，很多其它语言（如 Java、C#）采用特殊的运行时（runtime）软件来协调资源，但这样无疑极大地降低了程序的执行效率。

​	Rust 不依靠运行时环境，但 Rust 在语言本身就设计了包括所有权机制在内的手段来尽可能地把最常见的错误消灭在编译阶段，这一点其他语言不具备。

#### 20.1.1. 创建线程

​	Rust 中通过 `std::thread::spawn()` 函数创建新线程。

```rust
std::thread::spawn(spawn_function);
```

#### 20.1.2. join 方法

​	`join` 方法可以使子线程运行结束后再停止运行程序。

```rust
let handle = thread::spawn(|| {
	// ...
});

handle.join().unwrap();
```

#### 20.1.3. move 方法

​	在子线程中尝试使用当前函数的资源，这一定是**错误**的。因为所有权机制禁止这种危险情况的产生，它将破坏所有权机制销毁资源的一定性。可以使用闭包的 `move` 关键字，强制转移资源的所有权至子线程中。

```rust
use std::thread;

fn main() {
    let s = "hello";
   	// 如果没有 move 关键字，相当于在子线程中使用主线程的函数
    let handle = thread::spawn(move || {
        println!("{}", s);
    });

    handle.join().unwrap();
}
```

#### 20.1.4.消息传递

​	Rust 中一个实现消息传递并发的主要工具是通道（channel），通道有两部分组成，一个发送者（transmitter）和一个接收者（receiver）。`std::sync::mpsc` 包含了消息传递的方法。

```rust
use std::thread;
use std::sync::mpsc;

fn main() {
    let (tx, rx) = mpsc::channel();

    thread::spawn(move || {
        let val = String::from("hi");
        tx.send(val).unwrap();
    });

    let received = rx.recv().unwrap();
    println!("Got: {}", received);
}
```

## 21. Rust 宏

​	Rust 宏（Macros）是一种在编译时生成代码的强大工具，它允许你在编写代码时创建自定义语法扩展。宏在 Rust 中有两种类型：声明式宏（Declarative Macros）和过程宏（Procedural Macros）。

### 21.1. 声明式宏

​	使用 `macro_rules!` 关键字来定义声明式宏。

```rust
macro_rules! my_macro {
    // 模式匹配和展开
    ($arg:expr) => {
        // 生成的代码
        // 使用 $arg 来代替匹配到的表达式
    };
}
```

### 21.2. 过程宏

​	过程宏是一种更为灵活和强大的宏，允许在编译时通过自定义代码生成过程来操作抽象语法树（AST）。过程宏在功能上更接近于函数，但是它们在编写和使用上更加复杂。

- **派生宏（Derive Macros）：**用于自动实现 `trait`（比如 `Copy`、`Debug`）的宏；
- **属性宏（Attribute Macros）：**用于在声明上附加额外的元数据，如 `#[derive(Debug)]`。

​	过程宏的实现通常需要使用 `proc_macro` 库提供的功能，例如 `TokenStream` 和 `TokenTree`，以便更直接地操纵源代码。

## 22. Rust 智能指针

​	智能指针（Smart pointers）是一种在 Rust 中常见的数据结构，它们提供了额外的功能和安全性保证，以帮助管理内存和数据；是一种封装了对动态分配内存的所有权和生命周期管理的数据类型。

### 22.1. Box\<T> 智能指针

​	`Box<T>` 是 Rust 中最简单的智能指针之一，它允许在堆上分配一块内存，并将值存储在这个内存中，由于 Rust 的所有权规则，使用 Box 可以在**堆**上创建具有已知大小的数据。

```rust
let b = Box::new(5);
```

### 22.2. Rc\<T> 智能指针

​	`Rc<T>`（引用计数指针）允许多个所有者共享数据，它使用引用计数来跟踪数据的所有者数量，并在所有者数量为零时释放数据。`Rc<T>` 适用于**单线程环境**下的数据共享。

```rust
use std::rc::Rc;

let data = Rc::new(5);
let data_clone = Rc::clone(&data);
```

### 22.3. Arc\<T> 智能指针

​	`Arc<T>`（原子引用计数指针）与 `Rc<T>` 类似，但是可以安全地在**多线程环境**中共享数据，因为它使用原子操作来更新引用计数。

```rust
use std::sync::Arc;

let data = Arc::new(5);
let data_clone = Arc::clone(&data);
```

### 22.4. RefCell\<T> 智能指针

​	`RefCell<T>` 允许在运行时检查借用规则，它使用内部可变性来提供了一种安全的内部可变性模式，允许在不可变引用的情况下修改数据。但是，`RefCell<T>` 只能用于**单线程环境**。

```rust
use std::cell::RefCell;

let data = RefCell::new(5);
let mut borrowed_data = data.borrow_mut();
*borrowed_data = 10;
```

### 22.5. Mutex\<T> 智能指针

​	`Mutex<T>` 是一个互斥锁，它保证了在任何时刻只有一个线程可以访问 `Mutex` 内部的数据。

```rust
use std::sync::Mutex;

let m = Mutex::new(5);
let mut data = m.lock().unwrap();
```

### 22.6. RwLock\<T> 智能指针

​	`RwLock<T>` 是一种读取/写入锁，允许多个读取者同时访问数据，但在写入时是排他的。

```rust
use std::sync::RwLock;

let lock = RwLock::new(5);
let read_guard = lock.read().unwrap();
```

### 22.7. Weak\<T> 智能指针

​	`Weak<T>` 是 `Rc<T>` 的非拥有智能指针，它不增加引用计数，用于解决循环引用问题。

```rust
use std::rc::{Rc, Weak};

let five = Rc::new(5);
let weak_five = Rc::downgrade(&five);
```

### 22.8. 智能指针的生命周期管理

​	智能指针可以帮助管理数据的生命周期，当智能指针被销毁时，它们会自动释放内存，从而避免了内存泄漏和野指针的问题。此外，智能指针还允许在创建时指定特定的析构函数，以实现自定义的资源管理。

## 23. Rust 异步编程

​	异步编程是一种在 Rust 中处理非阻塞操作的方式，允许程序在执行长时间的 I/O 操作时不被阻塞，而是在等待的同时可以执行其他任务。实现方法包括 `async` 和 `await` 关键字、`futures` 和异步运行时（如 `tokio`、`async-std` 等），以及其他辅助工具。

- **Future：**`Future` 是 Rust 中表示异步操作的抽象。它是一个可能还没有完成的计算，将来某个时刻会返回一个值或一个错误。
- **async/await：**`async` 关键字用于定义一个异步函数，它返回一个 `Future`。`await` 关键字用于暂停当前 `Future` 的执行，直到它完成。



