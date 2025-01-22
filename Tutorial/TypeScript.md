# TypeScript 教程

​	TypeScript 是 JavaScript 的一个超级，支持 [ECMAScript 6 标准](https://www.w3school.com.cn/js/js_es6.asp) 。

## 1. TypeScript 特性

​	相对 JavaScript，TypeScript 增加了许多关键功能，特别是围绕类型系统和代码结构的增强功能。

- **静态类型检查**：TypeScript 在编译时会检查代码类型是否匹配，能够发现许多潜在的错误。即使是简单的错误，也可以在编写代码时被捕获；
- **类型推断**：TypeScript 能够自动推断变量的类型，不需要显示声明类型；
- **接口和类型定义**：TypeScript 提供了 `interface` 和 `type` 关键字，允许定义复杂的数据结构，这对于项目中不同部分的代码协作和数据交互来说非常重要；
- **类和模块支持**：TypeScript 支持面向对象编程中的类（class）概念，增加了构造函数、继承、访问控制修饰符，并且支持 ES 模块化规范；
- **工具和编译器支持**：TypeScript 拥有良好的编译器支持；
- **兼容 JavaScript**：TypeScript 是 JavaScript 的超集，这意味着所有合法的 JavaScript 代码都是合法的 TypeScript 代码，这使得 JavaScript 项目可以逐步迁移到 TypeScript，而无需完全重写。

### 1.1. 静态类型

​	TypeScript 最大的特性就是增加了静态类型系统。在 TypeScript 中，开发者可以显示地声明变量、参数、返回值的类型，这样可以在编译时捕获很多潜在的类型错误。常见类型包括：`number`、`string`、`boolean`、`array`、`tuple`、`enum` 等，此外也支持自定义类型。

```typescript
let name: string = "wxss";
let age: number = 25;
```

### 1.2. 类型判断

​	TypeScript 可以自动判断变量类型，即使不显式声明类型，TypeScript 也会根据变量的赋值内容来推断类型，从而在大多数情况下，减少类型注解的书写量。

### 1.3. 接口

​	TypeScript 提供了接口（interface），允许定义复杂的对象结构。接口可以定义属性和方法，还可以通过 `implement` 关键字实现接口，或者通过 `extends` 进行扩展，便于定义复杂的数据类型。

### 1.4. 类型别名

​	类型别名（Type Aliases）可以为复杂的类型定义简短的别名，便于代码复用。

```typescript
type StringOrNumber = string | number;
let value: StringOrNumber = 42;
```

### 1.5. 枚举

​	TypeScript 引入了 `enum` 类型，用于定义一组命名的常量，提高代码的可读性。枚举在 JavaScript 中没有直接的对应。

```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right
}

let dir: Direction = Direction.Up;
```

### 1.6. 元组

​	元组允许定义具有固定数量和类型的数组。它适用于需要固定数据结构的场景。

```typescript
let point: [number, number] = [10, 20];
```

### 1.7. 访问控制修饰符

​	TypeScript 在类中提供了 `public`、`private` 和 `protected` 修饰符，允许控制属性或方法的可见性，支持更好的封装。

```typescript
class Person {
  private name: string;
  protected age: number;
  public constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
```

### 1.8. 抽象类

​	TypeScript 支持抽象类，抽象类不能直接实例化，需要由子类实现。抽象类适用于定义通用行为和抽象方法的类层次结构。

```typescript
abstract class Animal {
  abstract makeSound(): void
}

class Dog extends Animal {
  makeSound() {
    console.log("Woof!")
  }
}
```

### 1.9. 泛型

​	TypeScript 支持泛型（Generics），允许在类、接口和函数中使用参数化泛型，使得代码可以使用不同类型需求，同时保持类型安全。

```typescript
function identity<T>(value: T): T {
  return value;
}

let num = identity<number>(42);
```

### 1.10. 模块和命名空间

​	TypeScript 提供了基于 ES6 的模块系统，使用 `import` 和 `export` 导入和导出模块。此外，TypeScript 还支持命名空间（Namespace），用于组织代码和避免命名冲突。

```typescript
// math.ts
export function add(a: number, b: number): number {
  return a + b;
}

//main.ts
import { add } from "./math";
console.log(add(2, 3));
```

### 1.11. 类型守卫

​	TypeScript 提供了类型守卫（Type Guards），可以在代码中检查变量类型，帮助编译器推断更加具体的类型。这对于联合类型尤为重要。

```typescript
function printId(id: string | number) {
  if (typeof id === "string") {
    console.log(id.toUpperCase());
  } else {
    console.log(id.toFixed(2))
  }
}
```

### 1.12. 可选链和空值合并运算符

​	TypeScript 增加了 JavaScript 的可选链（`?.`）和空值合并运算符（`??`），简化了代码中对可能为 `null` 或 `undefined` 值的处理。

```typescript
let users = {name: "wxss", address: {city: "YinChuan"}};
console.log(users?.address?.city);	// 如果 address 及 city 存在，则输出对应值，否则返回 undefined

let value = null;
console.log(value ?? "default")			// 如果 value 为 null 或 undefined，则返回 default
```

### 1.13. 类型兼容性和工具选择

​	TypeScript 提供了一些工具类型，如 `partial`、`pick`、`readonly`、`record` 等，这些类型可以帮助生成新的类型，简化类型定义。

```typescript
interface Todo {
	title: string;
  description: string;
}

let partialTdo: Partial<Todo> = { title: "Learn TypeScript" };		// 可选属性
```

### 1.14. 编译器错误检查

​	TypeScript 提供的编译器错误检查可以捕获 JavaScript 中不易发现的错误，如拼写错误、类型不匹配等，帮助提升代码质量。

### 1.15. ES 新特性支持

​	TypeScript 提前支持了一些还未在所有环境中普及的 ES 特性，如装饰器（Decorators）、异步迭代器等，且能够将其编译成兼容 JavaScript 的版本。

## 2. TypeScript 基础语法

### 2.1. 保留关键字

| 关键字       | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| `abstract`   | 用于定义抽象类或抽象方法                                     |
| `any`        | 表示任意类型，禁用类型检查                                   |
| `as`         | 类型断言，用于将某种类型转换为另一种类型                     |
| `await`      | 用于异步函数中，暂停代码执行直到 Promise 解决                |
| `boolean`    | 表示布尔类型                                                 |
| `case`       | 用于 switch 语句中的分支                                     |
| `catch`      | 用于捕获异常                                                 |
| `class`      | 用于定义类                                                   |
| `const`      | 定义常量变量                                                 |
| `continue`   | 跳过当前循环，继续下一次循环                                 |
| `debugger`   | 启动调试器，暂停代码执行                                     |
| `declare`    | 声明一个变量或模块，通常用于类型声明文件                     |
| `default`    | 定义 switch 语句的默认分支                                   |
| `delete`     | 删除对象的属性或数组的元素                                   |
| `do`         | 用于 do…while 循环                                           |
| `else`       | 定义条件语句中的 else 部分                                   |
| `enum`       | 定义枚举类型                                                 |
| `export`     | 用于从模块中导出变量、函数或类                               |
| `extends`    | 用于类的继承，表示类继承自其他类                             |
| `false`      | 布尔值 false                                                 |
| `finally`    | 定义 try…catch 语句中的最终执行代码块                        |
| `for`        | 用于 for 循环                                                |
| `from`       | 用于从模块导入语句，指定模块的来源                           |
| `function`   | 定义函数                                                     |
| `get`        | 用于对象的 getter 方法                                       |
| `if`         | 用于条件判断                                                 |
| `implements` | 用于类实现接口                                               |
| `import`     | 用于从模块中导入内容                                         |
| `in`         | 用于检查对象中是否包含指定的属性，或用于 for…in 循环         |
| `infer`      | 用于条件类型中推断类型                                       |
| `instanceof` | 检查对象是否是指定类的实例                                   |
| `interface`  | 用于定义接口                                                 |
| `let`        | 定义块级作用域的变量                                         |
| `module`     | 定义模块（较早版本使用）                                     |
| `namespace`  | 定义命名空间（较早版本使用）                                 |
| `new`        | 创建类的实例                                                 |
| `null`       | 表示空值                                                     |
| `number`     | 表示数字类型                                                 |
| `object`     | 表示非原始类型                                               |
| `of`         | 用于 for…of 循环                                             |
| `package`    | 用于模块系统，标识包                                         |
| `private`    | 用于类成员的访问修饰符，表示私有                             |
| `protected`  | 用于类成员的访问修饰符，表示受保护                           |
| `public`     | 用于类成员的访问修饰符，表示公有                             |
| `readonly`   | 表示只读属性                                                 |
| `return`     | 退出函数并可返回值                                           |
| `set`        | 用于对象的 setter 方法                                       |
| `string`     | 表示字符串类型                                               |
| `super`      | 用于调用父类的方法或构造函数                                 |
| `switch`     | 用于 switch 语句                                             |
| `symbol`     | 表示符号类型                                                 |
| `this`       | 引用当前类或对象的实例                                       |
| `throw`      | 抛出异常                                                     |
| `try`        | 用于异常处理语句 try…catch                                   |
| `true`       | 布尔值 true                                                  |
| `type`       | 用于定义类型别名                                             |
| `typeof`     | 获取变量或表达式的类型                                       |
| `undefined`  | 表示未定义的值                                               |
| `unique`     | 用于 symbol 类型的唯一标识符                                 |
| `var`        | 用于声明变量（不推荐使用）                                   |
| `void`       | 表示没有返回值的类型                                         |
| `while`      | 用于 while 循环                                              |
| `with`       | 用于创建一个作用域，在该作用域内可以省略对象的引用（不推荐使用） |
| `yield`      | 用于生成器函数中，暂停和恢复生成器的执行                     |

### 2.2. 空白和换行

​	TypeScript 会忽略程序中出现的空格、制表符和换行符。空格、制表符通常用来缩进代码，使代码易于阅读和理解。

### 2.3. 大小写

​	TypeScript 区分大写和小写字符。

### 2.4. 分号

​	每行指令都是一段语句，可以使用分号或不适用，分号在 TypeScript 中是可选的，建议使用。

### 2.5. 注释

​	注释是一个良好的习惯，虽然很多程序员讨厌注释，但还是建议在每段代码写上文字说明。注释可以提高程序的可读性。

​	注释可以包含有关程序的一些信息，如代码的作者，有关函数的说明等。

- 单行注释：`//`；
- 多行注释：`/* */`。

## 3. TypeScript 基础类型

| 类型        | 描述                             |
| ----------- | -------------------------------- |
| `string`    | 表示文本数据                     |
| `number`    | 表示数字，包括整数和浮点数       |
| `boolean`   | 表示布尔值                       |
| `array`     | 表示相同类型的元素数组           |
| `tuple`     | 表示已知类型和长度的数组         |
| `enum`      | 定义一组命名常量                 |
| `any`       | 任意类型，不进行类型检查         |
| `void`      | 无返回值（null 或 undefined）    |
| `null`      | 表示空值                         |
| `undefined` | 表示未定义                       |
| `never`     | 表示不会有返回值                 |
| `object`    | 表示非原始类型                   |
| `union`     | 联合类型，表示可以是多种类型之一 |
| `unknown`   | 不确定类型，需类型检查后使用     |

## 4. TypeScript 变量声明

​	变量是一种使用方便的占位符，用于引用计算机的内存地址。

```typescript
var [var_name]: var_type = value;
```

- 没有初始值，变量值会被设置为 `undefined`；
- 没有类型，该变量可以是任意类型；

### 4.1. 类型断言

​	类型断言（Type Assertion）可以用来手动指定一个值的类型，即允许变量从一种类型更改为另一种类型。

```typescript
<type>value
// 或
value as type
```

#### 4.1.1. 断言的充足性

​	当 S 类型是 T 类型的子集，或者 T 类型是 S 类型的子集，S 能被成功断言为 T。这是为了在进行类型断言时提供额外的安全性，完全毫无根据的断言时危险的。如果想这么做，可以使用 any。

​	之所以不被称为**类型转换**，是因为转换通常意味着某种运行时的支持，但是类型断言纯粹是一个编译时的语法，同时它也是一种为编译器提供关于如何分析代码的方法。

#### 4.1.2. 类型推断

​	当类型没有给出时，TypeScript 编译器利用类型推断来推断类型。如果缺乏声明而不能推断出类型，那么它的类型被视作默认的动态 any 类型。

### 4.2. 变量作用域

​	变量作用域制定了变量定义的位置。程序中变量的可用性由变量作用域决定。

- 全局作用域：全局变量定义在程序结构的外部，可以在代码的任何位置使用；
- 类作用域：这个变量也可以称为字段。类变量声明在一个类里面，但在类的方法外面，该变量可以通过类的对象来访问。类变量也可以是静态的，静态的变量可以通过类名直接访问；
- 局部作用域：局部变量，局部变量只能在声明它的一个代码块中使用。

## 5. TypeScript 运算符

### 5.1. 算术运算符

| 运算符 | 描述         |
| :----- | :----------- |
| `+`    | 加法         |
| `-`    | 减法         |
| `*`    | 乘法         |
| `/`    | 除法         |
| `%`    | 取模（余数） |
| `++`   | 自增         |
| `--`   | 自减         |

### 5.2. 关系运算符

| 运算符 | 描述       |
| :----- | :--------- |
| `==`   | 等于       |
| `!=`   | 不等于     |
| `>`    | 大于       |
| `<`    | 小于       |
| `>=`   | 大于或等于 |
| `<=`   | 小于或等于 |

### 5.3. 逻辑运算符

| 运算符 | 描述 |
| :----- | :--- |
| `&&`   | and  |
| `||`   | or   |
| `!`    | not  |

### 5.4. 位运算符

| 运算符 | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| `&`    | AND，按位与处理两个长度相同的二进制数                        |
| `|`    | OR，按位或处理两个长度相同的二进制数                         |
| `~`    | 取反，对一个二进制数的每一位执行逻辑反操作                   |
| `^`    | 异或，按位异或运算，对等长二进制模式按位或二进制数的每一位执行逻辑异按位或操作 |
| `<<`   | 左移，把 `<<` 左边的运算数的各二进位全部左移若干位，高位丢弃，低位补 0 |
| `>>`   | 右移，把 `>>` 左边的运算数的各二进位全部右移若干位           |
| `>>>`  | 无符号右移，与有符号右移位类似，除了左边一律使用0 补位       |

### 5.5. 赋值运算符

| 运算符 | 描述               |
| :----- | :----------------- |
| `=`    | 赋值               |
| `+=`   | 先进行加运算后赋值 |
| `-=`   | 先进行减运算后赋值 |
| `*=`   | 先进行乘运算后赋值 |
| `/=`   | 先进行除运算后赋值 |

**注意**：类似的逻辑运算符也可以与赋值运算符联合使用：`<<=`、`>>=`、`>>>=`、`&=`、`|=`、`^=`。

### 5.6. 三元运算符

```typescript
Test ? expr1 : expr2
```

### 5.7. 类型运算符

#### 5.7.1. typeof 运算符

​	一元运算符，返回操作数的数据类型。

#### 5.7.2. instanceof 运算符

​	用于判断对象是否为指定的类型。

### 5.8. 其他运算符

#### 5.8.1. 负号运算符

​	更改操作数的符号。

```typescript
let y = -x;
```

#### 5.8.2. 字符串运算符

​	可以拼接字符串。

```typescript
let msg: string = "w" + "xss"
```

## 6. TypeScript 条件语句

​	条件语句用于基于不同的条件执行不同的动作。

### 6.1. if 语句

```typescript
if (boolean_expr) {
  // boolean_expr = true
} else if (boolean_expr2) {
  // boolean_expr2 = true
} else {
	//boolean_expr && boolean_expr2 = false
}
```

### 6.2. switch 语句

```typescript
switch (expr) {
  case constant-expr :
    // 
    break;
  case cosntan-expr2 :
    //
    break;
    ...
  default : /* optional */
  	//
}
```

## 7. TypeScript 循环

​	循环语句允许多次执行一个语句或语句组。

### 7.1. for 循环

```typescript
for ( init; condition; increment ) {
  statements(s);
}
```

#### 7.1.1. for…in 循环

​	用于迭代集合或者列表。

```typescript
for ( let val in list) {
	statements(s);
}
```

#### 7.1.2. for…of 循环

​	创建一个循环来迭代所有可迭代对象。

```typescript
for ( let entry of someArray ) {
  statements(s);
}
```

### 7.2. while 循环

```typescript
while ( condition ) {
  statements(s);
}
```

#### 7.2.1. do…while 循环

​	循环至少执行一次，满足 condition 时，重复。

```typescript
do {
  statements(s);
}while( condition );
```

### 7.3. break 语句

​	当 `break` 出现在一个循环内，循环会立即终止，且程序流将继续执行紧接循环的下一条语句；它也可以用于终止 `switch` 语句中的一个 `case`。

### 7.4. continue 语句

​	类似于 `break` 语句，但 `continue` 不强制终止，会跳过当前循环中的代码，强迫开始下一次循环。对于 `for` 循环，`continue` 语句执行后自增语句仍然会执行；对于 `while` 和 `do…while` 循环，`continue` 语句重新执行条件判断语句。

### 7.5. 无限循环

```typescript
for(;;) {
  // block
}
// 或
while(true) {
  // block
}
```

## 8. TypeScript 函数

### 8.1. 函数定义

```typescript
function func_name () {
  // func block
}
```

### 8.2. 调用函数

```typescript
func_name();
```

### 8.3. 函数返回值

```typescript
function func_name (): return_type {
  // func block
  return value;
}
```

### 8.4. 带参数函数

```typescript
function func_name (param[: datatype], param2[: datatype]) {
  // func block
}
```

### 8.5. 可选参数和默认参数

#### 8.5.1. 可选参数

​	在 TypeScript 中，如果定义了参数，则必须传入这些参数，除非将这些参数设置为可选，可选参数使用 `?` 标识。

```typescript
function func_name(param: datatype, optional?: datatype)
```

​	可选参数必须跟在必须参数后面。

#### 8.5.2. 默认参数

```typescript
function func_name (param: datatype, param2: datatype = default_value) {
  statements(s);
}
```

**注意**：参数不能同时设置为默认和可选。

#### 8.5.3. 剩余参数

​	如果不明确向函数传入的参数数量，可以使用剩余参数来定义。剩余参数语法允许将一个不确定数量的参数作为一个数组传入。

```typescript
function func_name (param: datatype, param2: datatype, ...remaining_param: string[]) {
  statements(s);
}
```

### 8.6. 匿名函数

​	匿名函数是一个没有函数名的函数。在程序运行时动态声明，除了没有函数名外，其他与标准函数一样。可以将匿名函数赋值给一个变量，这种表达式被称为函数表达式。

```typescript
let res = function( [args] ) {...}
```

#### 8.6.1. 匿名函数子调用

```typescript
(fucntion () {
  statements(s);
})()
```

### 8.7. 构造函数

​	TypeScript 支持使用 JavaScript 内置的构造函数 `Function()` 来定义函数。

```typescript
let res = new Function ([arg1[, arg2[, ...argN]]], function_body);
```

- `arg1, arg2, … , argN`：参数列表；
- `function_body`：一个含有包括函数定义的 JavaScript 语句的字符串。

### 8.8. 递归函数

​	递归函数即在函数内调用函数自身。

```typescript
function func_name() {
	return func_name();
}
```

### 8.9. Lambda 函数

​	Lambda 函数也称之为箭头函数，表达式语法比函数表达式更短。

```typescript
( [param1, param2, ... , paramN] ) => statement;
```

### 8.10. 函数重载

​	重载是方法名字相同，而参数不同，返回类型可以相同也可以不同。定义函数重载需要定义重载签名和一个实现签名，重载签名定义函数的形参和返回类型，标识可以的调用方式，没有函数体，实现签名定义函数的功能。一个函数可以有多个重载签名。

```typescript
// 重载签名
function func_name(param_list1): return_type;
function func_name(param_list2): return_type;
// 实现签名
function func_name(param_list):return_type {
  // 形参列表必须同时满足所有重载签名
}
```

## 9. TypeScript Number

​	TypeScript 与 JavaScript 类似，支持 Number 对象，但其与 numbe 类型不同。

```typescript
let num = new Number(value);
```

**注意**：这会创建一个引用类型的对象，而非基本的 number 类型；`value` 部位数值，或不能转换为数字，则返回 NaN。

​	推荐使用基本类型 number，避免不必要的开销和封装类的混淆。

## 10. TypeScript String

​	String 对象用于处理文本/字符串。不建议使用 `String` 对象，而是直接使用字符串字面量 `string`，因为 String 对象会带来一些性能和类型上的问题。

```typescript
let txt = new String("string");
```

## 11. TypeScript Array

​	数组对象是使用单独的变量名来存储一系列的值。

```typescript
let sites: string[] = ["var1", "var2", "var3"];
```

### 11.1. Array 对象

​	也可以使用 Array 对象创建数组。可以接收两种值：表示数组大小的数值；初始化的数组列表，元素使用逗号分隔值。

```typescript
let arr_name: string[] = new Array(4);
// 或
let arr_name: string[] = new Array("var1", "var2", "var3");
```

### 11.2. 数组解构

​	可以把数组元素赋值给变量。

```typescript
let arr: number[] = [1, 2];
let [x, y] = arr;
```

### 11.3. 数组迭代

​	可以使用 for 语句来循环输出数组的各个元素。

```typescript
for (i in arr) {
  statements(s);
}
```

### 11.4. 多维数组

​	一个数组的元素可以是另一个数组，这样就构成了多维数组（Multi-dimensional Array）。最简单的多维数组是二维数组。

```typescript
let arr: datatype[][] = [ [val1, val2, val3], [val1, val2, val3] ];
```

### 11.5. 数组在函数中的使用

#### 11.5.1. 作为参数传递给函数

```typescript
function func_name (arr: string[]) {
  statements
}
```

#### 11.5.2. 作为函数的返回值

```typescript
function func_name () {
  return arr;
}
```

## 12. TypeScript Map

​	Map 对象保存键值对，并且能够记住键的原始插入顺序。任何值都可以作为一个键或一个值。

### 12.1. 创建 Map

```typescript
let map = new Map([
	["key1", "val1"],
  ["key2", "val2"]
]);
```

### 12.2. 迭代方法

#### 12.2.1. keys

​	返回一个包含 Map 所有键的迭代器。

```typescript
for (const key of map.keys()) {
  statements(s);
}
```

#### 12.2.2. values

​	返回一个包含 Map 所有值的迭代器。

```typescript
for (const value of map.values()) {
  statements(s);
}
```

#### 12.2.3. entries

​	返回一个包含 Map 中所有键值对的迭代器，每个元素是一个 `[value, key]` 数组。

```typescript
for (const entry of map.entries()) {
}
// 或
for (const [value, key] of map.entries()) {
}
```

#### 12.2.4. forEach

​	对 Map 中的每个键值对执行一次提供的回调函数。

```typescript
map.forEach((value, key) => {
  statements(s);
})
```

## 13. TypeScript 元组

​	数组中元素的数据类型一般是相同的，如果存储的元素数据类型不同，（`any[]` 类型的数组可以不同），则需要使用元组。

​	TypeScript 中的元组（Tuple）是一种特殊类型的数组，它允许在数组中存储不同类型的元素，与普通数组不同，元组中每个元素都有明确的类型和位置。元组可以在很多场景下用于表示固定长度、且各元素类型已知的数据结构。

```typescript
let tuple: [type1, type2, ... , typen] = [];
```

### 13.1. 访问元组

​	元组中元素使用索引来访问，第一个元素索引为 0，以此类推。

```typescript
tuple_name[index];
```

### 13.2. 元组运算

#### 13.2.1. push

​	`push` 方法可以向元组的末尾添加一个元素，类型必须符合元组定义中的类型约束。如果超出元组的类型约束，TypeScript 会报错。

#### 13.2.2. pop

​	`pop` 方法可以从元组的末尾移除一个元素，并返回该元素。返回的元素类型将根据元组的定义类型推断。

### 13.3. 更新元组

​	元组是可变的，这意味着我们可以对元组进行更新操作。

```typescript
tuple_name[index] = value;
```

### 13.4. 解构元组

​	可以把元组的元素值赋值给变量。

```typescript
let tuple: [number, string, boolean] = [42, "wxss", true];
var [a, b] = tuple;
```

### 13.5. 使用标签元组

​	TypeScript 还允许为元组中的每个元素添加标签。

```typescript
let tuple: [id: nmber, name: string] = [1, "wxss"];
```

### 13.6. 元组的类型推断

​	TypeScript 可以根据数组的元素自动推断出元组的类型。

```typescript
let tuple = [42, "wxss"] as const;
```

​	通过 `as const` 断言，TypeScript 会将元组视为一个不可变的常量元组。

### 13.7. 连接元组

​	元组可以使用数组的 `conact` 方法进行连接，但需要注意连接后的结果是一个普通的数组，而不是元组。

```typescript
let tuple1;
let tuple2;
let tupel12 = tuple1.conact(tuple2);
```

### 13.8. 切片元组

​	可以使用 `slice` 方法对元组进行切片操作，返回一个新的数组。

```typescript
let tuple: [number, string, boolean] = [42, "wxss", true];
let sliced = tuple.slice(1);
```

### 13.9. 遍历元组

​	可以使用 for…of 循环或者 forEach 方法遍历元组中的元素。

```typescript
let tuple...

for (let item of tuple) {
  statements(s);
}

tuple.forEach(item => statements(s));
```

### 13.10. 转换为普通数组

​	虽然元组是一个固定长度、固定类型的数组，但可以通过 `Array.from` 的方法将其转换为普通数组。

```typescript
let tuple...

let array = Array.from(tuple);
```

### 13.11. 扩展元组

​	使用剩余运算符可以轻松地将多个元组合并成一个新的元组。

```typescript
let tuple1...
let tuple2...

let extendedTuple: [number, string, ...typeof tuple1] = [42, "wxss", ...tuple2];
```

**注意**：剩余运算符后面应该指定扩展目标的类型，这个类型是元组的实例类。

## 14. TypeScript 联合类型

​	联合类型（Union Types）可以通过管道 `|` 将变量设置为多种类型，赋值时可以根据设置的类型来赋值。

**注意**：只能赋值指定的类型，如果赋值其他类型就会报错。

```typescript
type1 | type2 | type3
```

### 14.1. 联合类型数组

​	可以将数组声明为联合类型。

```typescript
var arr: number[] | string[] = [];
```

## 15. TypeScript 接口

​	接口是一系列抽象方法的声明，是一些方法特征的集合，这些方法都应该是抽象的，需要由具体的类去实现，然后第三方就可以通过这组方法调用，让具体的类执行具体的方法。

```typescript
interface interface_name {
}
```

### 15.1. 联合类型和接口

```typescript
interface Interface_name {
  attr: datatype;
  commandline: string | string[] | (()=>string);
}
```

### 15.2. 接口和数组

​	接口中可以将数组的索引值和元素设置为不同类型，索引值可以是数字或字符串。

```typescript
interface Interface_name {
  [index: number]: string;
}
```

### 15.3. 接口继承

​	接口继承即接口可以通过其他接口扩展自身。TypeScript 允许接口继承多个接口，继承使用关键字 `extends` 。

```typescript
Child_interface_name extends super_interface1_name, super_interface2_name, ...
```

## 16. TypeScript 类

​	TypeScript 是面向对象的 JavaScript。

```typescript
class class_name {
  // class block
}
```

### 16.1. 数据成员

```typescript
class class_name {
  // 字段
  attr1: datatype;
  attr2: datatype;
  
  // 构造函数
  constructor (attr: datatype) {
    this.attr1 = attr;
  }
  
  // 方法
  method_name(): return_type {
    // method block
  }
}
```

### 16.2. 实例化对象

​	使用 `new` 关键字来实例化类的对象。类在实例化时会调用构造函数。

```typescript
let obj_name = new class_name([args]);
```

​	类的字段属性和方法可以使用 `.` 号来访问。

```typescript
// 访问属性
obj.field_name;
// 访问方法
obj.func_name();
```

### 16.3. 类的继承

​	TypeScript 支持继承类，即可以在创建类的时候继承一个已存在的类，这个已存在的类称为父类，继承他的类称为子类。继承使用关键字 `extends` ，子类除了不能继承父类的私有成员和构造函数，其他都可以继承。

​	TypeScript 一次只能继承一个类，不支持继承多个类，但 TypeScript 支持多重继承（A 继承 B，B 继承 C）。

```typescript
class Child_class_name extends Parent_class_name
```

### 16.4. 继承方法重写

​	类继承后，子类可以对父类的方法重新定义，这个过程称之为方法的重写。其中 `super` 关键字是对父类的直接引用，该关键字可以引用父类的属性和方法。

### 16.5. static 关键字

​	`static` 关键字用于定义类的数据成员为静态的，静态成员可以直接通过类名调用。

### 16.6. isntanceof 运算符

​	用于判断对象是否是指定的类型，如果是返回 true，否则返回 false。

### 16.7. 访问控制修饰符

​	TypeScript 中，可以使用访问控制修饰符来保护对类、变量、方法和构造方法的访问。

- **public（默认）**：公有，可以在任何地方被访问；
- **protected**：受保护，可以被其自身以及其子类访问；
- **private**：私有，只能被其定义所在的类访问。

### 16.8. 类和接口

​	类可以实现接口，使用关键字 `implements`，并将对应字段作为类的属性使用。实现接口的时候，可以实现部分接口字段，但必须实现全部的接口函数。

## 17. TypeScript 对象

​	对象是包含一组键值对的实例。值可以是标量、函数、数组、对象等。

```typescript
let obj = {
  key1: value1;
  key2: value2;
  key3: function() {
    
  }
	key4: ["..."]
}
```

### 17.1. 类型模板

​	TypeScript 中的对象必须是特定类型的实例。因此不能向对象直接添加没有定义的成员。

```typescript
var obj = {
  attr1: datatype;
  attr2: datatype;
  // 类型模板，必须有此定义，才能实例化
  method_name: function() {};
}

obj.method_name = function() {// method block};
obj.method_name();
```

### 17.2. 鸭子类型（Duck Type）

​	鸭子类型是动态类型的一种风格，是多态（polymorphism）的一种形式。在这种风格中，一个对象有效的语句，不是由继承自特定的类或实现特定的接口，而是由当前方法和属性的集合决定。

​	在这种类型中，关注对象能做什么，而不关注对象所属的类型。任何具有相对应形式和属性的对象，都属于该类。

```typescript
interface IPoint {
  x: number;
  y: number;
}

function addPoints(p1: IPoint, p2: IPoint): IPoint {
  let x = p1.x + p2.x;
  let y = p1.y + p2.y;
  return {x: x, y: y}
}

let newPoint = addPoint({x: 3, y: 4}, {x: 5, y: 1});
```

​	在上述的代码中，返回值类型并不是接口 `IPoint` 的对象，但是由于其具有相同的属性，所以判决其类型为 `IPoint`。此外，调用中也并没有使用 `IPoint` 的对象，而是使用与其属性相同的对象。

## 18. TypeScript 泛型

​	泛型（Generics）是一种编程语言特性，允许在定义函数、类、接口等时，使用占位符来表示类型，而不是具体的类型。

### 18.1. 泛型标识符

​	在泛型中，通常使用一些约定俗成的标识符，如：`T`、`K, V`、`E` 等。但实际上可以使用任何标识符。

​	`T` 代表 Type，是最常见的泛型类型参数名。

```typescript
function identity<T>(arg: T): T {
  return arg;
}
```

​	`K, V` 表示键和值的泛型类型参数。

```typescript
interface KeyValuePair<K, V> {
  key: K;
  value: V;
}
```

​	`E` 表示数组元素的泛型类型参数。

```typescript
function method_name<E>(array: E[]): void {
  //  method block
}
```

​	`R` 表示函数返回值的泛型类型参数。

```typescript
function method_name<R>(value: R): R {
  // method block
}
```

​	`U, V` 用于表示第二、第三个泛型参数类型。

```typescript
function method_name<U, V>(first: U, second: V): string {
  return `${first} ${second}`;
}
```

​	这些标识符是约定俗成的，实际上可以选择任何符合标识符规范的名称。关键是使得代码易读和易于理解，所以建议在泛型类型参数上使用描述性的名称，以便于理解其用途。

### 18.2. 泛型函数

​	使用泛型可以创建一个可以处理不同类型的函数。

```typescript
function identity<T>(arg: T): T {
  return arg;
}
```

### 18.3. 泛型接口

​	可以使用泛型来定义接口，使接口的成员能够使用任意类型。

```typescript
interface Pair<T, U> {
  first: T;
  second: U;
}
```

### 18.4. 泛型类

```typescript
class Box<T> {
  private value: T;
  
  constructor(value: T){
    this.value = value;
  }
  
  getValue(): T {
    return this.value;
  }
}
```

### 18.5. 泛型约束

​	如果需要限制泛型的类型范围，可以使用泛型约束。

```typescript
interface Lengthwise {
  length: number;
}

function logLength<T extends Lengthwise>(arg: T): void {
  console.log(arg.length);
}
```

​	上述代码表示，函数 `logLength` 接受的类型继承自接口 `Lengthwise` ，即要求调用时输入的参数必须具有 `length` 属性，进而限定泛型的类型范围。

### 18.6. 泛型与默认值

​	可以给泛型设置默认值，使得在不指定类型参数时能够使用默认类型。

```typescript
function defaultValue<T = string>(arg: T): T {
  return arg;
}
```

## 19. TypeScript 命名空间

​	命名空间一个最明确的目的就是解决重名问题。命名空间定义了标识符的可见范围，一个标识符可在多个命名空间中定义。

```typescript
namespace SomeNameSpaceName {
  export interface ISomeInterfaceName {}
  export class SomeClassName {}
}
```

​	如果命名空间在一个单独的 TypeScript 文件中，则应使用三斜杠 `///` 引用它。

```typescript
/// <reference path = "SomeFileName.ts" />
```

### 19.1. 嵌套命名空间

​	命名空间支持嵌套，可以将命名空间定义在另一个命名空间里面。

```typescript
namespace namespace_name1 {
  export namespace namespace_name2 {
    export class class_name {}
  }
}
```

## 20. TypeScript 模块

​	TypeScript 模块的设计理念是可以更换的组织代码。模块是在其自身的作用域里执行，并不是全局作用域，这意味着定义在模块里的变量、函数和类等在模块外部是不可见的，除非明确地使用 `export` 导出它们。类似地，必须通过 `import` 导入其他模块导出的变量、函数和类。

​	两个模块的关系是通过文件级别上使用 `import` 和 `export` 建立的。模块使用模块加载器去导入其他的模块。在运行时，模块加载器的作用是在执行此模块代码前，去查找并执行这个模块的所有依赖。

```typescript
// filename: SomeInterface.ts
export interface SomeInterface {
  // interface block
}
```

​	导入模块需要使用关键字 `import` 。

```typescript
import someInterfaceRef = require("./SomeInterface");
```

## 21. TypeScript 声明文件

​	TypeScript 作为 JavaScript 的超集，在开发过程中不可避免地要引用其他第三方地 JavaScript 的库。虽然通过直接引用可以调用库的类和方法，但是无法使用 TypeScript 诸如类型检查等特性功能。

​	为了解决这个问题，需要将这些库里的函数和方法体去掉后只保留导出类型声明，而产生了一个描述 JavaScript 库和模块信息的声明文件。通过引用这个声明文件，就可以借用 TypeScript 的各种特性来使用库文件。

### 21.1. 声明文件

```typescript
// filename: example.d.ts
declare module Module_Name {
}
```
