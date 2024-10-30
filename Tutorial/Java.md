## Java 笔记

### Java 基础教程

#### 1.  注释

##### 单行注释

以双斜杠 `//` 开始。

##### 多行注释

以 `/*` 开始，以 `*/` 结束。

##### 文档注释

以 `/**` 开始，以 `*/` 结束。

#### 2.  对象和类

##### 类的类型变量

- **局部变量**：在方法、构造方法或者语句块中定义的变量被称为局部变量。变量声明和初始化都是在方法中，方法结束后，变量就会自动销毁。
- **成员变量**：成员变量是定义在类中，方法体之外的变量。这种变量在创建对象的时候实例化。成员变量可以被类中方法、构造方法和特定类的语句块访问。
- **类变量**：类变量也声明在类中，方法体之外，但必须声明为 static 类型。

##### 构造方法

- 每个类都有构造方法。

- 构造方法的名称必须与类同名，一个类可以有多个构造方法。

##### 创建对象

- **声明**：声明一个对象，包括对象名称和对象类型。
- **实例化**：使用关键字 new 来创建一个对象。
- **初始化**：使用 new 创建对象时，会调用构造方法初始化对象。

##### 访问实例变量和方法

- 通过 `.` 运算符。

##### 源文件声明规则

- 一个源文件中只能有一个 public 类
- 一个源文件可以有多个非 public 类
- 源文件的名称应该和 public 类的类名保持一致。
- 如果一个类定义在某个包中，那么 package 语句应该在源文件的首行。
- 如果源文件包含 import 语句，那么应该放在 package 语句和类定义之间。如果没有 package 语句，那么 import 语句应该在源文件中最前面。
- import 语句和 package 语句对源文件中定义的所有类都有效。在同一源文件中，不能给不同的类声明不同的包。

##### Java 包

包主要用来对类和接口进行分类。

##### import 语句

import 语句用来提供一个合理的路径，使得编译器可以找到某个类。

#### 3.  基础数据类型

##### 内置数据类型

**byte：**

- byte 数据类型是8位、有符号的，以二进制补码表示的整数；
- 最小值是 **-128（-2^7）**；
- 最大值是 **127（2^7-1）**；
- 默认值是 **0**；
- byte 类型用在大型数组中节约空间，主要代替整数，因为 byte 变量占用的空间只有 int 类型的四分之一。

**short：**

- short 数据类型是 16 位、有符号的以二进制补码表示的整数
- 最小值是 **-32768（-2^15）**；
- 最大值是 **32767（2^15 - 1）**；
- Short 数据类型也可以像 byte 那样节省空间。一个short变量是int型变量所占空间的二分之一；
- 默认值是 **0**。

**int：**

- int 数据类型是32位、有符号的以二进制补码表示的整数；
- 最小值是 **-2,147,483,648（-2^31）**；
- 最大值是 **2,147,483,647（2^31 - 1）**；
- 一般地整型变量默认为 int 类型；
- 默认值是 **0** 。

**long：**

- long 数据类型是 64 位、有符号的以二进制补码表示的整数；
- 最小值是 **-9,223,372,036,854,775,808（-2^63）**；
- 最大值是 **9,223,372,036,854,775,807（2^63 -1）**；
- 这种类型主要使用在需要比较大整数的系统上；
- 默认值是 **0L**。

**float：**

- float 数据类型是单精度、32位、符合IEEE 754标准的浮点数；
- float 在储存大型浮点数组的时候可节省内存空间；
- 默认值是 **0.0f**；
- 浮点数不能用来表示精确的值，如货币。

**double：**

- double 数据类型是双精度、64 位、符合 IEEE 754 标准的浮点数；
- 浮点数的默认类型为 double 类型；
- double类型同样不能表示精确的值，如货币；
- 默认值是 **0.0d**。

**boolean：**

- boolean数据类型表示一位的信息；
- 只有两个取值：true 和 false；
- 这种类型只作为一种标志来记录 true/false 情况；
- 默认值是 **false**。

**char：**

- char 类型是一个单一的 16 位 Unicode 字符；
- 最小值是 **\u0000**（十进制等效值为 0）；
- 最大值是 **\uffff**（即为 65535）；
- char 数据类型可以储存任何字符。

##### 引用类型

- 引用类型指向一个对象，指向对象的变量是引用变量。这些变量在声明时被指定为一个特定的类型。
- 对象、数组都是引用数据类型。
- 所有引用类型的默认值都是null。
- 一个引用变量可以用来引用任何与之兼容的类型。

##### 常量

常量在程序运行时是不能被修改的。

##### 自动类型转换

**整型、实型（常量）、字符型数据可以混合运算。运算中，不同类型的数据先转化为同一类型，然后进行运算。**

转换从低级到高级。

```java
byte,short,char—> int —> long—> float —> double 
```

数据类型转换必须满足如下规则：

- 不能对boolean类型进行类型转换。
- 不能把对象类型转换成不相关类的对象。
- 在把容量大的类型转换为容量小的类型时必须使用强制类型转换。
- 转换过程中可能导致溢出或损失精度。
- 浮点数到整数的转换是通过舍弃小数得到，而不是四舍五入。

###### 自动类型转换

必须满足转换前的数据类型的位数要低于转换后的数据类型。

###### 强制类型转换

- 条件是转换的数据类型必须是兼容的。

- 格式：(type)value type是要强制类型转换后的数据类型。

###### 隐含强制类型转换

- 整数的默认类型是 int。
- 小数默认是 double 类型浮点型，在定义 float 类型时必须在数字后面跟上 F 或者 f。

#### 4.  变量类型

##### 变量声明

```java
type identifier [ = value][, identifier [= value] ...] ;
```

##### 变量类型

- **局部变量（Local Variables）：**局部变量是在方法、构造函数或块内部声明的变量，它们在声明的方法、构造函数或块执行结束后被销毁，局部变量在声明时需要初始化，否则会导致编译错误。

  ```java
  public void exampleMethod() {
      int localVar = 10; // 局部变量
      // ...
  }
  ```

- **实例变量（Instance Variables）：**实例变量是在类中声明，但在方法、构造函数或块之外，它们属于类的实例，每个类的实例都有自己的副本，如果不明确初始化，实例变量会被赋予默认值（数值类型为0，boolean类型为false，对象引用类型为null）。

  ```java
  public class ExampleClass {
      int instanceVar; // 实例变量
  }
  ```

- **静态变量或类变量（Class Variables）：**类变量是在类中用 static 关键字声明的变量，它们属于类而不是实例，所有该类的实例共享同一个类变量的值，类变量在类加载时被初始化，而且只初始化一次。

  ```java
  public class ExampleClass {
      static int classVar; // 类变量
  }
  ```

- **参数变量（Parameters）：**参数是方法或构造函数声明中的变量，用于接收调用该方法或构造函数时传递的值，参数变量的作用域只限于方法内部。

  ```java
  public void exampleMethod(int parameterVar) {
      // 参数变量
      // ...
  }
  ```

##### 参数变量

- **值传递：**在方法调用时，传递的是实际参数的值的副本。当参数变量被赋予新的值时，只会修改副本的值，不会影响原始值。Java 中的基本数据类型都采用值传递方式传递参数变量的值。
- **引用传递：**在方法调用时，传递的是实际参数的引用（即内存地址）。当参数变量被赋予新的值时，会修改原始值的内容。Java 中的对象类型采用引用传递方式传递参数变量的值。

##### 局部变量

- 局部变量必须在使用前声明，并且不能被访问修饰符修饰，因为它们的作用域已经被限制在了声明它们的方法、代码块或构造函数中。
- 局部变量只在声明它的方法、构造方法或者语句块中可见，不能被其他方法或代码块访问。
- 局部变量是在栈上分配的。
- 局部变量没有默认值，所以局部变量被声明后，必须经过初始化，才可以使用。

##### 成员变量（实例变量）

- 成员变量的值应该至少被一个方法、构造方法或者语句块引用，使得外部能够通过这些方式获取实例变量信息。
- 成员变量可以直接通过变量名访问。但在静态方法以及其他类中，就应该使用完全限定名：**ObjectReference.VariableName**。

##### 类变量（静态变量）

###### 定义方式

静态变量的定义方式是在类中使用 **static** 关键字修饰变量，通常也称为类变量。

###### 访问方式

由于静态变量是与类相关的，因此可以通过类名来访问静态变量，也可以通过实例名来访问静态变量。

###### 生命周期

静态变量的生命周期与程序的生命周期一样长，即它们在类加载时被创建，在整个程序运行期间都存在，直到程序结束才会被销毁。 因此，静态变量可以用来存储整个程序都需要使用的数据，如配置信息、全局变量等。

###### 初始化时机

静态变量在类加载时被初始化，其初始化顺序与定义顺序有关。

##### 静态变量的线程安全性

当多个线程同时访问一个包含静态变量的类时，需要考虑其线程安全性。

##### 静态变量的命名规范

- **使用驼峰命名法：** 静态变量的命名应该使用驼峰命名法，即首字母小写，后续每个单词的首字母大写。 例如：。`myStaticVariable`
- **全大写字母：** 静态变量通常使用全大写字母，单词之间用下划线分隔。 这被称为"大写蛇形命名法"（Upper Snake Case）。 例如：。`MY_STATIC_VARIABLE`
- **描述性：** 变量名应该是有意义的，能够清晰地表达该变量的用途。 避免使用单个字符或不具有明确含义的缩写。
- **避免使用缩写：** 尽量避免使用缩写，以提高代码的可读性。 如果使用缩写是必要的，确保广泛理解，并在注释中进行解释。

##### 静态变量的使用场景

- 存储全局状态或配置信息
- 计数器或统计信息
- 缓存数据或共享资源
- 工具类的常量或方法
- 单例模式中的实例变量

#### 5.  变量命名规则

##### 局部变量

- 使用驼峰命名法，应该以小写字母开头。

##### 实例变量（成员变量）

- 使用驼峰命名法，应该以小写字母开头。

##### 静态变量（类变量）

- 使用驼峰命名法，应该以小写字母开头。
- 通常也可以使用大写蛇形命名法，全大写字母，单词之间用下划线分隔。

##### 常量

- 使用全大写字母，单词之间用下划线分隔。
- 常量通常使用 `final` 修饰。

##### 参数

- 使用驼峰命名法，应该以小写字母开头。

##### 类名

- 使用驼峰命名法，应该以大写字母开头。

#### 6.  修饰符

##### 访问控制修饰符

- **default** (即默认，什么也不写）: 在同一包内可见，不使用任何修饰符。使用对象：类、接口、变量、方法。
- **private** : 在同一类内可见。使用对象：变量、方法。 **注意：不能修饰类（外部类）**
- **public** : 对所有类可见。使用对象：类、接口、变量、方法
- **protected** : 对同一包内的类和所有子类可见。使用对象：变量、方法。 **注意：不能修饰类（外部类）**。

###### 默认访问修饰符-不使用任何关键字

- 如果在类、变量、方法或构造函数的定义中没有指定任何访问修饰符，那么它们就默认具有默认访问修饰符。

- 默认访问修饰符的访问级别是包级别（package-level），即只能被同一包中的其他类访问。

###### 私有访问修饰符-private

- 私有访问修饰符是最严格的访问级别，变量和构造方法只能被所属类访问，并且类和接口不能声明为 **private**。

- 声明为私有访问类型的变量只能通过类中公共的 getter 方法被外部类访问。

- Private 访问修饰符的使用主要用来隐藏类的实现细节和保护类的数据。

###### 公有访问修饰符-public

- 被声明为 public 的类、方法、构造方法和接口能够被任何其他类访问。

- 如果几个相互访问的 public 类分布在不同的包中，则需要导入相应 public 类所在的包。由于类的继承性，类所有的公有方法和变量都能被其子类继承。

###### 受保护的访问修饰符-protected

- **子类与基类在同一包中**：被声明为 protected 的变量、方法和构造器能被同一个包中的任何其他类访问；
- **子类与基类不在同一包中**：那么在子类中，子类实例可以访问其从基类继承而来的 protected 方法，而不能访问基类实例的protected方法。

###### 访问控制和继承

- 父类中声明为 public 的方法在子类中也必须为 public。
- 父类中声明为 protected 的方法在子类中要么声明为 protected，要么声明为 public，不能声明为 private。
- 父类中声明为 private 的方法，不能够被子类继承。

##### 非访问修饰符

###### static 修饰符

- **静态变量：**static 关键字用来声明独立于对象的静态变量，无论一个类实例化多少对象，它的静态变量只有一份拷贝。 静态变量也被称为类变量。局部变量不能被声明为 static 变量。
- **静态方法：**static 关键字用来声明独立于对象的静态方法。静态方法不能使用类的非静态变量。静态方法从参数列表得到数据，然后计算这些数据。

对类变量和方法的访问可以直接使用 **classname.variablename** 和 **classname.methodname** 的方式访问。

###### final 修饰符

- final 变量

  - 变量一旦赋值后，不能被重新赋值。被 final 修饰的实例变量必须显式指定初始值。

  - final 修饰符通常和 static 修饰符一起使用来创建类常量。

- final 方法

  - 父类中的 final 方法可以被子类继承，但是不能被子类重写。

  - 声明 final 方法的主要目的是防止该方法的内容被修改。

- final 类
  - final 类不能被继承，没有类能够继承 final 类的任何特性。

##### abstract 修饰符

###### 抽象类

- 抽象类不能用来实例化对象，声明抽象类的唯一目的是为了将来对该类进行扩充。

- 一个类不能同时被 abstract 和 final 修饰。
- 如果一个类包含抽象方法，那么该类一定要声明为抽象类，否则将出现编译错误。

- 抽象类可以包含抽象方法和非抽象方法。

###### 抽象方法

- 抽象方法是一种没有任何实现的方法，该方法的具体实现由子类提供。

- 抽象方法不能被声明成 final 和 static。

- 任何继承抽象类的子类必须实现父类的所有抽象方法，除非该子类也是抽象类。

- 如果一个类包含若干个抽象方法，那么该类必须声明为抽象类。抽象类可以不包含抽象方法。

- 抽象方法的声明以分号结尾，例如：**public abstract sample();**。

##### synchronized 修饰符

- synchronized 关键字声明的方法同一时间只能被一个线程访问
- synchronized 修饰符可以应用于四个访问修饰符。

##### transient 修饰符

- 序列化的对象包含被 transient 修饰的实例变量时，java 虚拟机(JVM)跳过该特定的变量。

- 该修饰符包含在定义变量的语句中，用来预处理类和变量的数据类型。

##### volatile 修饰符

- volatile 修饰的成员变量在每次被线程访问时，都强制从共享内存中重新读取该成员变量的值。
- 当成员变量发生变化时，会强制线程将变化值回写到共享内存。

#### 7.  运算符

- 算术运算符
- 关系运算符
- 位运算符
- 逻辑运算符
- 赋值运算符
- 其他运算符

#### 8.  循环结构 - for, while 及 do...while

##### while 循环

```java
while( 布尔表达式 ) {
    //循环内容 
}
```

只要布尔表达式为 true，循环就会一直执行下去。

##### do…while 循环

do…while 循环至少会执行一次。

```java
do {
       //代码语句
}while(布尔表达式);
```

**注意：**如果布尔表达式的值为 true，则语句块一直执行，直到布尔表达式的值为 false。

##### for循环

```java
for(初始化; 布尔表达式; 更新) {
    //代码语句 
}
```

- 最先执行初始化步骤。可以声明一种类型，但可初始化一个或多个循环控制变量，也可以是空语句。
- 然后，检测布尔表达式的值。如果为 true，循环体被执行。如果为false，循环终止，开始执行循环体后面的语句。
- 执行一次循环后，更新循环控制变量。

##### 增强 for 循环

```java
for(声明语句 : 表达式) {
    //代码句子 
}
```

**声明语句：**声明新的局部变量，该变量的类型必须和数组元素的类型匹配。其作用域限定在循环语句块，其值与此时数组元素的值相等。

**表达式：**表达式是要访问的数组名，或者是返回值为数组的方法。

##### break 关键字

- break 主要用在循环语句或者 switch 语句中，用来跳出整个语句块。

- break 跳出最里层的循环，并且继续执行该循环下面的语句。

##### continue 关键字

continue 适用于任何循环控制结构中。作用是让程序立刻跳转到下一次循环的迭代。

- 在 for 循环中，continue 语句使程序立即跳转到更新语句。

- 在 while 或者 do…while 循环中，程序立即跳转到布尔表达式的判断语句。

#### 9.  条件语句 - if...else

```java
if(布尔表达式) {
    //如果布尔表达式为true将执行的语句
}
```

##### if...else语句

```java
if(布尔表达式){
    //如果布尔表达式的值为true 
}
else{   
    //如果布尔表达式的值为false 
}
```

##### if...else if...else 语句

```java
if(布尔表达式 1){
    //如果布尔表达式 1的值为true执行代码 
}else if(布尔表达式 2){
    //如果布尔表达式 2的值为true执行代码 
}else if(布尔表达式 3){
    //如果布尔表达式 3的值为true执行代码 
}else {
    //如果以上布尔表达式都不为true执行代码 
}
```

##### 嵌套的 if…else 语句

```java
if(布尔表达式 1){
    ////如果布尔表达式 1的值为true执行代码   
    if(布尔表达式 2){
        ////如果布尔表达式 2的值为true执行代码   
    } 
}
```

#### 10.  switch case 语句

```java
switch(expression){
    case value :
       //语句
       break; //可选
    case value :
       //语句
       break; //可选
    //你可以有任意数量的case语句
    default : //可选
       //语句
}
```

#### 11.  Number & Math 类

##### Number 类

- Java 语言为每一个内置数据类型提供了对应的包装类。
- 所有的包装类**（Integer、Long、Byte、Double、Float、Short）**都是抽象类 Number 的子类。

##### Math 类

- Math 的方法都被定义为 static 形式，通过 Math 类可以在主函数中直接调用。

#### 12.  Character 类

- Character 类用于对单个字符进行操作。

- Character 类在对象中包装一个基本类型 **char** 的值

#### 13.  String 类

##### 创建字符串

```java
String str = "Runoob";
String str2 = new String("Runoob");
```

##### 字符串长度

```java
str.length();
```

##### 链接字符串

```java
string1.concat(string2);
```

##### 创建格式化字符串

```java
String fs = String.format("...%d", intVar);
```

#### 14.  StringBuffer 和 StringBuilder 类

- 在使用 StringBuffer 类时，每次都会对 StringBuffer 对象本身进行操作，而不是生成新的对象。

- StringBuilder 类和 StringBuffer 之间的最大不同在于 StringBuilder 的方法不是线程安全的（不能同步访问）。

- 由于 StringBuilder 相较于 StringBuffer 有速度优势，所以多数情况下建议使用 StringBuilder 类。

#### 15.  数组

数组可以作为函数的参数或者返回值。

##### 新建数组

```java
dataType[] arrayRefVar;   // 首选的方法：
```

```java
arrayRefVar = new dataType[arraySize];
```

##### 处理数组

数组的元素类型和数组的大小都是确定的，所以当处理数组元素时候，我们通常使用基本循环或者 For-Each 循环（增强型 for 循环）。

##### 多维数组

1. 直接为每一维分配空间：

```java
type[][] typeName = new type[typeLength1][typeLength2];
```

2. 从最高维开始，分别为每一维分配空间：

```java
// 声明是一个 2 行数组
String[][] s = new String[2][];
// 声明第 1 行有 2 个元素
s[0] = new String[2];
// 声明第 2 行有 3 个元素
s[1] = new String[3];
```

#### 16.  日期时间

java.util 包提供了 Date 类来封装当前的日期和时间。 Date 类提供两个构造函数来实例化 Date 对象。

- 第一个构造函数使用当前日期和时间来初始化对象。

```java
Date( )
```

- 第二个构造函数接收一个参数，该参数是从 1970 年 1 月 1 日起的毫秒数。

```java
Date(long millisec)
```

##### 日期比较

- 使用 getTime() 方法获取两个日期（自1970年1月1日经历的毫秒数值），然后比较这两个值。
- 使用方法 before()，after() 和 equals()。
- 使用 compareTo() 方法，它是由 Comparable 接口定义的，Date 类实现了这个接口。

##### 使用 SimpleDateFormat 格式化日期

- SimpleDateFormat 是一个以语言环境敏感的方式来格式化和分析日期的类。
- SimpleDateFormat 允许你选择任何用户自定义日期时间格式来运行。

##### 使用printf格式化日期

使用两个字母格式，它以 **%t** 开头并且以下面表格中的一个字母结尾。

| 转换符 | 说明                        | 示例                             |
| :----- | :-------------------------- | :------------------------------- |
| %tc    | 包括全部日期和时间信息      | 星期六 十月 27 14:21:20 CST 2007 |
| %tF    | "年-月-日"格式              | 2007-10-27                       |
| %tD    | "月/日/年"格式              | 10/27/07                         |
| %tr    | "HH:MM:SS PM"格式（12时制） | 02:25:51 下午                    |
| %tT    | "HH:MM:SS"格式（24时制）    | 14:28:16                         |
| %tR    | "HH:MM"格式（24时制）       | 14:28                            |

##### 解析字符串为时间

SimpleDateFormat 类的附加方法parse()，按照给定的格式化存储来解析字符串。

##### Java 休眠(sleep)

sleep() 使当前线程进入停滞状态（阻塞当前线程），让出CPU的使用。目的是不让当前线程独自霸占该进程所获的CPU资源，以留一定时间给其他线程执行的机会。

##### Calendar类

###### 创建一个代表系统当前日期的Calendar对象

```java
Calendar c = Calendar.getInstance();//默认是当前日期
```

###### 创建一个指定日期的Calendar对象

使用Calendar类代表特定的时间，需要首先创建一个Calendar的对象，然后再设定该对象中的年月日参数来完成。

```java
//创建一个代表2009年6月12日的Calendar对象
Calendar c1 = Calendar.getInstance();
c1.set(2009, 6 - 1, 12);
```

###### Calendar类对象信息的设置

**Set 设置**

```java
// 设置年、月、日
public final void set(int year,int month,int date)
// 设置某一个参数，例如日
public void set(int field,int value)
```

**Add 设置**

```java
// 计算当前日期十天后的时间
Calendar c1 = Calendar.getInstance();
c1.add(Calendar.DATE, 10);
```

**get 获取对象信息**

```java
// 获取某一个参数，例如日
public void get(int field,int value)
```

#### 17.  正则表达式

##### java.util.regex 包

- Pattern 类：

  pattern 对象是一个正则表达式的编译表示。Pattern 类没有公共构造方法。要创建一个 Pattern 对象，你必须首先调用其公共静态编译方法，它返回一个 Pattern 对象。该方法接受一个正则表达式作为它的第一个参数。

- Matcher 类：

  Matcher 对象是对输入字符串进行解释和匹配操作的引擎。与Pattern 类一样，Matcher 也没有公共构造方法。你需要调用 Pattern 对象的 matcher 方法来获得一个 Matcher 对象。

- PatternSyntaxException：

  PatternSyntaxException 是一个非强制异常类，它表示一个正则表达式模式中的语法错误。

##### 捕获组

- 捕获组是把多个字符当一个单独单元进行处理的方法，它通过对括号内的字符分组来创建。

##### start 和 end 方法

- 返回匹配字符串开始和结束的位置。

##### matches 和 lookingAt 方法

- matches 要求整个序列都匹配，而lookingAt 不要求。

- lookingAt 方法虽然不需要整句都匹配，但是需要从第一个字符开始匹配。

##### replaceFirst 和 replaceAll 方法

replaceFirst 和 replaceAll 方法用来替换匹配正则表达式的文本。不同的是，replaceFirst 替换首次匹配，replaceAll 替换所有匹配。

##### appendReplacement 和 appendTail 方法

Matcher 类也提供了appendReplacement 和 appendTail 方法用于文本替换。

#### 18.  方法

##### 方法的定义

```java
修饰符 返回值类型 方法名(参数类型 参数名){
    ...    
    方法体
    ...    
    return 返回值; 
}
```

##### 方法调用

- 当方法返回一个值的时候，方法调用通常被当做一个值。
- 当方法返回值是void，方法调用一定是一条语句。

##### void 关键字

一个void方法的调用一定是一个语句。

##### 通过值传递参数

调用一个方法时候需要提供参数，你必须按照参数列表指定的顺序提供。

##### 方法的重载

- 就是说一个类的两个方法拥有相同的名字，但是有不同的参数列表。

- 重载的方法必须拥有不同的参数列表。你不能仅仅依据修饰符或者返回类型的不同来重载方法。

##### 变量作用域

- 变量的范围是程序中该变量可以被引用的部分。

##### 命令行参数的使用

- 运行一个程序时候再传递给它消息。这要靠传递命令行参数给main()函数实现。

- 命令行参数是在执行程序时候紧跟在程序名字后面的信息。

##### 构造方法

- 当一个对象被创建时候，构造方法用来初始化该对象。
- 构造方法和它所在类的名字相同，但构造方法没有返回值。

##### 可变参数

```java
typeName... parameterName
```

- 在方法声明中，在指定参数类型后加一个省略号(...) 。

- 一个方法中只能指定一个可变参数，它必须是方法的最后一个参数。任何普通的参数必须在它之前声明。

##### finalize() 方法

- 在对象被垃圾收集器析构(回收)之前调用，这个方法叫做 finalize( )，它用来清除回收对象。

```java
protected void finalize()
{
   // 在这里终结代码
}
```

- 关键字 protected 是一个限定符，它确保 finalize() 方法不会被该类以外的代码调用。

#### 19.  流(Stream)、文件(File)和IO

##### 读取控制台输入

```java
BufferedReader br = new BufferedReader(new                       InputStreamReader(System.in));
```

##### 从控制台读取多字符输入

```java
int read( ) throws IOException
```

##### 从控制台读取字符串

```java
String readLine( ) throws IOException
```

##### 控制台输出

```java
void write(int byteval)
```

##### 读写文件

###### FileInputStream

- 该流用于从文件读取数据，它的对象可以用关键字 new 来创建。

- 有多种构造方法可用来创建对象。

可以使用字符串类型的文件名来创建一个输入流对象来读取文件。

```java
InputStream f = new FileInputStream("C:/java/hello");
```

也可以使用一个文件对象来创建一个输入流对象来读取文件。

```java
File f = new File("C:/java/hello"); 
InputStream in = new FileInputStream(f);
```

###### FileOutputStream

- 该类用来创建一个文件并向文件中写数据。

- 如果该流在打开文件进行输出前，目标文件不存在，那么该流会创建该文件。

- 有两个构造方法可以用来创建 FileOutputStream 对象。

使用字符串类型的文件名来创建一个输出流对象。

```java
OutputStream f = new FileOutputStream("C:/java/hello")
```

也可以使用一个文件对象来创建一个输出流来写文件。

```java
File f = new File("C:/java/hello"); 
OutputStream fOut = new FileOutputStream(f);
```

##### Java中的目录

###### 创建目录：

File类中有两个方法可以用来创建文件夹：

- **mkdir( )**方法创建一个文件夹，成功则返回true，失败则返回false。失败表明File对象指定的路径已经存在，或者由于整个路径还不存在，该文件夹不能被创建。
- **mkdirs()**方法创建一个文件夹和它的所有父文件夹。

###### 读取目录

- 一个**目录**其实就是一个 **File** 对象，它包含其他文件和文件夹。

- 如果创建一个 File 对象并且它是一个目录，那么调用 **isDirectory()** 方法会返回 true。

- 可以通过调用该对象上的 **list()** 方法，来提取它包含的文件和文件夹的列表。

###### 删除目录或文件

- 删除文件可以使用 **java.io.File.delete()** 方法。

- 当删除某一目录时，必须保证该目录下**没有其他文件**才能正确删除，否则将删除失败。

#### 20.  Scanner 类

- 可以通过 Scanner 类来获取用户的输入。
- 通过 next() 与 nextLine() 方法获取输入的字符串
- 读取前需要使用 hasNext 与 hasNextLine 判断是否还有输入的数据

##### next() 与 nextLine() 区别

**next():**

- 一定要读取到有效字符后才可以结束输入。
- 对输入有效字符之前遇到的空白，next() 方法会自动将其去掉。
- 只有输入有效字符后才将其后面输入的空白作为分隔符或者结束符。
- next() 不能得到带有空格的字符串。

**nextLine()：**

- 以Enter为结束符,也就是说 nextLine()方法返回的是输入回车之前的所有字符。
- 可以获得空白。

#### 21.  异常处理

- **检查性异常：**最具代表的检查性异常是用户错误或问题引起的异常，这是程序员无法预见的。例如要打开一个不存在文件时，一个异常就发生了，这些异常在编译时不能被简单地忽略。
- **运行时异常：** 运行时异常是可能被程序员避免的异常。与检查性异常相反，运行时异常可以在编译时被忽略。
- **错误：** 错误不是异常，而是脱离程序员控制的问题。错误在代码中通常被忽略。例如，当栈溢出时，一个错误就发生了，它们在编译也检查不到的。

##### 捕获异常

```java
try
{
   // 程序代码
}catch(ExceptionName e1)
{
   //Catch 块
}
```

##### 多重捕获块

```java
try{
    // 程序代码 
}catch(异常类型1 异常的变量名1){
    // 程序代码 
}catch(异常类型2 异常的变量名2){
    // 程序代码 
}catch(异常类型3 异常的变量名3){
    // 程序代码 
}
```

##### throws/throw 关键字

**throw** 关键字用于在代码中抛出异常，而 **throws** 关键字用于在方法声明中指定可能会抛出的异常类型。

###### throw 关键字

- 通常情况下，当代码执行到某个条件下无法继续正常执行时，可以使用 **throw** 关键字抛出异常，以告知调用者当前代码的执行状态。

###### throws 关键字

- 用于在方法声明中指定该方法可能抛出的异常。
- 当方法内部抛出指定类型的异常时，该异常会被传递给调用该方法的代码，并在该代码中处理异常。

###### finally关键字

- finally 关键字用来创建在 try 代码块后面执行的代码块。
- 无论是否发生异常，finally 代码块中的代码总会被执行。
- 在 finally 代码块中，可以运行清理类型等收尾善后性质的语句。

###### 注意事项

- catch 不能**独立**于 try 存在。
- 在 try/catch 后面添加 finally 块并**非强制**性要求的。
- try 代码后不能**既没** catch 块**也没** finally 块。
- try, catch, finally 块之间**不能添加**任何代码。

###### try-with-resources

```java
try (resource declaration) {
  // 使用的资源
} catch (ExceptionType e1) {
  // 异常块
}
```

**注意：**try-with-resources 语句关闭所有实现 AutoCloseable 接口的资源。

###### try-with-resources 处理多个资源

- 可以声明多个资源，方法是使用分号 **;** 分隔各个资源。

##### 声明自定义异常

- 所有异常都必须是 Throwable 的子类。
- 如果希望写一个检查性异常类，则需要继承 Exception 类。
- 如果你想写一个运行时异常类，那么需要继承 RuntimeException 类。

```java
class MyException extends Exception{
    ...
}
```

##### 通用异常



- **JVM(Java虚拟机) 异常：**由 JVM 抛出的异常或错误。例如：NullPointerException 类，ArrayIndexOutOfBoundsException 类，ClassCastException 类。
- **程序级异常：**由程序或者API程序抛出的异常。例如 IllegalArgumentException 类，IllegalStateException 类。

### Java 面向对象

#### 1.  继承

##### 类的继承格式

```java
class 父类 {
}  
class 子类 extends 父类 {
}
```

##### 继承的特性

- 子类拥有父类非 private 的属性、方法。
- 子类可以拥有自己的属性和方法，即子类可以对父类进行扩展。
- 子类可以用自己的方式实现父类的方法。
- Java 的继承是单继承，但是可以多重继承。

##### 继承关键字

###### extens 关键字

- 只能继承一个类

###### implements关键字

- 使用 implements 关键字可以变相的使java具有多继承的特性，使用范围为类继承接口的情况，可以同时继承多个接口（接口跟接口之间采用逗号分隔）。

###### super 与 this 关键字

- **super关键字：**可以通过super关键字来实现对父类成员的访问，用来引用当前对象的父类。

- **this关键字：**指向自己的引用。

###### final 关键字

使用 final 关键字声明类，就是把类定义定义为最终类，不能被继承，或者用于修饰方法，该方法不能被子类重写：

- 声明类：

  ```
  final class 类名 {//类体}
  ```

- 声明方法：

  ```
  修饰符(public/private/default/protected) final 返回值类型 方法名(){//方法体}
  ```

**注：** final 定义的类，其中的属性、方法不是 final 的。

##### 构造器

- 子类是不继承父类的构造器，它只是调用（隐式或显式）。
- 如果父类的构造器带有参数，则必须在子类的构造器中显式地通过 **super** 关键字调用父类的构造器并配以适当的参数列表。

- 如果父类构造器没有参数，则在子类的构造器中不需要使用 **super** 关键字调用父类构造器，系统会自动调用父类的无参构造器。

#### 2.  重写（Override）与重载（Overload）

##### 重写（Override）

- 重写是子类对父类的允许访问的方法的实现过程进行重新编写, **返回值和形参**都不能改变。
- 重写的好处在于子类可以根据需要，定义特定于自己的行为。 也就是说子类能够根据需要实现父类的方法。
- 重写方法不能抛出新的检查异常或者比被重写方法申明更加宽泛的异常。

##### 重载(Overload)

- 被重载的方法必须改变参数列表(参数个数或类型不一样)；
- 被重载的方法可以改变返回类型；
- 被重载的方法可以改变访问修饰符；
- 被重载的方法可以声明新的或更广的检查异常；
- 方法能够在同一个类中或者在一个子类中被重载。
- 无法以返回值类型作为重载函数的区分标准。

#### 3.  多态

##### 多态存在的三个必要条件

- 继承
- 重写
- 父类引用指向子类对象：`Parent p = new Child();`

​	当使用多态方式调用方法时，首先检查父类中是否有该方法，如果没有，则编译错误；如果有，再去调用子类的同名方法。

​	多态的好处：可以使程序有良好的扩展，并可以对所有类的对象进行通用处理。

##### 虚函数

- 普通函数就相当于 C++ 的虚函数，动态绑定是Java的默认行为。
- 如果 Java 中不希望某个函数具有虚函数特性，可以加上 final 关键字变成非虚函数。

#### 4.  抽象类

##### 抽象类

- 使用 abstract class 来定义抽象类。
- 抽象类不能被实例化。
- 抽象类可以被继承。

##### 抽象方法

- Abstract 关键字同样可以用来声明抽象方法，抽象方法只包含一个方法名，而没有方法体。

- 抽象方法没有定义，方法名后面直接跟一个分号，而不是花括号。
- 具体内容由其子类实现。

> 如果一个类包含抽象方法，那么该类必须是抽象类。
>
> 任何子类必须重写父类的抽象方法，或者声明自身为抽象类。

##### 抽象类总结规定

- 抽象类不能被实例化。只有抽象类的非抽象子类可以创建对象。
- 抽象类中不一定包含抽象方法，但是有抽象方法的类必定是抽象类。
- 抽象类中的抽象方法只是声明，不包含方法体。
- 构造方法，类方法（用 static 修饰的方法）不能声明为抽象方法。
- 抽象类的子类必须给出抽象类中的抽象方法的具体实现，除非该子类也是抽象类。

#### 5.  封装

##### 实现Java封装的步骤

1. 修改属性的可见性来限制对属性的访问（一般限制为private）；
2. 对每个值属性提供对外的公共方法访问，也就是创建一对赋取值方法，用于对私有属性的访问；

> 采用 **this** 关键字是为了解决实例变量和局部变量之间发生的同名的冲突。

#### 6.  接口

##### 接口与类相似点

- 一个接口可以有多个方法。
- 接口文件保存在 .java 结尾的文件中，文件名使用接口名。
- 接口的字节码文件保存在 .class 结尾的文件中。
- 接口相应的字节码文件必须在与包名称相匹配的目录结构中。

##### 接口与类的区别

- 接口不能用于实例化对象。
- 接口没有构造方法。
- 接口中所有的方法必须是抽象方法，Java 8 之后 接口中可以使用 default 关键字修饰的非抽象方法。
- 接口不能包含成员变量，除了 static 和 final 变量。
- 接口不是被类继承了，而是要被类实现。
- 接口支持多继承。

##### 接口特性

- 接口中每一个方法都是隐式抽象的，接口中的方法会被隐式的指定为 **public abstract**（只能是 public abstract，其他修饰符都会报错）。
- 接口中可以含有变量，但是接口中的变量会被隐式的指定为 **public static final** 变量（并且只能是 public，用 private 修饰会报编译错误）。
- 接口中的方法是不能在接口中实现的，只能由实现接口的类来实现接口中的方法。

##### 抽象类和接口的区别

- 抽象类中的方法可以有方法体，就是能实现方法的具体功能，但是接口中的方法不行。
- 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是 **public static final** 类型的。
- 接口中不能含有静态代码块以及静态方法(用 static 修饰的方法)，而抽象类是可以有静态代码块和静态方法。
- 一个类只能继承一个抽象类，而一个类却可以实现多个接口。

##### 接口的声明

```java
[可见度] interface 接口名称 [extends 其他的接口名] {
    // 声明变量        
    // 抽象方法 
}
```

> - 接口是隐式抽象的，当声明一个接口的时候，不必使用**abstract**关键字。
> - 接口中每一个方法也是隐式抽象的，声明时同样不需要**abstract**关键字。
> - 接口中的方法都是公有的。

##### 接口的实现

- 当类实现接口的时候，类要实现接口中所有的方法。否则，类必须声明为抽象的类。

- 类使用implements关键字实现接口。在类声明中，Implements关键字放在class声明后面。

###### 接口的实现语法

```java
...implements 接口名称[, 其他接口名称, 其他接口名称..., ...] ...
```

重写接口中声明的方法时，需要注意以下规则：

- 类在实现接口的方法时，不能抛出强制性异常，只能在接口中，或者继承接口的抽象类中抛出该强制性异常。
- 类在重写方法时要保持一致的方法名，并且应该保持相同或者相兼容的返回值类型。
- 如果实现接口的类是抽象类，那么就没必要实现该接口的方法。

在实现接口的时候，也要注意一些规则：

- 一个类只能继承一个类，但是能实现多个接口。
- 一个接口能继承另一个接口，这和类之间的继承比较相似。

##### 接口的继承

一个接口能继承另一个接口，使用extends关键字，子接口继承父接口的方法。

##### 接口的多继承

- 在Java中，类的多继承是不合法，但接口允许多继承。

- 在接口的多继承中extends关键字只需要使用一次，在其后跟着继承接口。

```java
public interface Hockey extends Sports, Event
```

##### 标记接口

- 最常用的继承接口是没有包含任何方法的接口。

- 标记接口是没有任何方法和属性的接口。它仅仅表明它的类属于一个特定的类型,供其他代码来测试允许做一些事情。

```java
package java.util; public interface EventListener {}
```

> - 建立一个公共的父接口：
>
>   你可以使用一个标记接口来建立一组接口的父接口。
>
> - 向一个类添加数据类型：
>
>   这种情况是标记接口最初的目的，实现标记接口的类不需要定义任何接口方法(因为标记接口根本就没有方法)，但是该类通过多态性变成一个接口类型。

#### 7.  枚举

##### 声明在内部类中

- 枚举类也可以声明在内部类中

##### 迭代枚举元素

```java
for (Color myVar : Color.values()) {
    ...
}
```

##### 在 switch 中使用枚举类

- 枚举类常应用于 switch 语句中

##### 方法

- **values()** 返回枚举类中所有的值。
- **ordinal()** 方法可以找到每个枚举常量的索引，就像数组索引一样。
- **valueOf()** 方法返回指定字符串值的枚举常量。

##### 枚举类成员

- 枚举跟普通类一样可以用自己的变量、方法和构造函数，构造函数只能使用 private 访问修饰符，所以外部无法调用。

- 枚举既可以包含具体方法，也可以包含抽象方法。 如果枚举类具有抽象方法，则枚举类的每个实例都必须实现它。

#### 8.  包（package）

##### 包的作用

- 把功能相似或相关的类或接口组织在同一个包中，方便类的查找和使用。
- 如同文件夹一样，包也采用了树形目录的存储方式。同一个包中的类名字是不同的，不同的包中的类的名字是可以相同的，当同时调用两个不同包中相同类名的类时，应该加上包名加以区别。因此，包可以避免名字冲突。
- 包也限定了访问权限，拥有包访问权限的类才能访问某个包中的类。

##### 包的语法

```java
package pkg1[．pkg2[．pkg3…]];
```

##### 创建包

- 必须将这个包的声明放在这个源文件的开头。

- 包声明应该在源文件的第一行，每个源文件只能有一个包声明，这个文件中的每个类型都应用于它。

- 如果一个源文件中没有使用包声明，那么其中的类，函数，枚举，注释等将被放在一个无名的包（unnamed package）中。

##### import 关键字

- 用于导入其他类或包中定义的类型，以便在当前源文件中使用这些类型。

- **import** 关键字用于引入其他包中的类、接口或静态成员，它允许你在代码中直接使用其他包中的类，而不需要完整地指定类的包名。

```java
import package1[.package2…].(classname|*);
```

##### package 的目录结构

- 每个 **java** 文件开头定义的包名应该与文件名对应；
- 同一个包定义的多个 **java** 文件应该放在同一个文件夹内；
- 包的路径与文件夹路径对应，子包内的 **java** 文件应该放在子文件夹内。

### Java 高级教程

#### 1.  数据结构

##### 数组（Arrays）

```java
int[] array = new int[5];
```

- **特点：** 固定大小，存储相同类型的元素。
- **优点：** 随机访问元素效率高。
- **缺点：** 大小固定，插入和删除元素相对较慢。

##### 列表（Lists）

Java 提供了多种列表实现，如 ArrayList 和 LinkedList。

```java
List<String> arrayList = new ArrayList<>();
List<Integer> linkedList = new LinkedList<>();
```

###### ArrayList

- **特点：** 动态数组，可变大小。
- **优点：** 高效的随机访问和快速尾部插入。
- **缺点：** 中间插入和删除相对较慢。

###### LinkedList

- **特点：** 双向链表，元素之间通过指针连接。
- **优点：** 插入和删除元素高效，迭代器性能好。
- **缺点：** 随机访问相对较慢。

##### 集合（Sets）

```java
Set<String> hashSet = new HashSet<>();
Set<Integer> treeSet = new TreeSet<>();
```

###### HashSet

- **特点：** 无序集合，基于HashMap实现。
- **优点：** 高效的查找和插入操作。
- **缺点：** 不保证顺序。

###### TreeSet

- **特点：**TreeSet 是有序集合，底层基于红黑树实现。
- **优点：** 提供自动排序功能，适用于需要按顺序存储元素的场景。
- **缺点：** 性能相对较差，不允许插入 null 元素。

##### 映射（Maps）

```java
Map<String, Integer> hashMap = new HashMap<>();
Map<String, Integer> treeMap = new TreeMap<>();
```

###### HashMap

- **特点：** 基于哈希表实现的键值对存储结构。
- **优点：** 高效的查找、插入和删除操作。
- **缺点：** 无序，不保证顺序。

###### TreeMap

- **特点：** 基于红黑树实现的有序键值对存储结构。
- **优点：** 有序，支持按照键的顺序遍历。
- **缺点：** 插入和删除相对较慢。

##### 栈（Stack）

```java
Stack<Integer> stack = new Stack<>();
```

###### Stack 类

- **特点：** 代表一个栈，通常按照后进先出（LIFO）的顺序操作元素。

##### 堆（Heap）

堆（Heap）优先队列的基础，可以实现最大堆和最小堆。

```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
```

##### 树（Trees）

Java 提供了 TreeNode 类型，可以用于构建二叉树等数据结构。

```
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}
```

#### 2.  集合框架

##### 集合接口

| 序号 | 接口描述                                                     |
| :--- | :----------------------------------------------------------- |
| 1    | **Collection 接口**：Collection 是最基本的集合接口，一个 Collection 代表一组 Object，即 Collection 的元素, Java不提供直接继承自Collection的类，只提供继承于的子接口(如List和set)。Collection 接口存储一组不唯一，无序的对象。 |
| 2    | **List 接口**：List接口是一个有序的 Collection，使用此接口能够精确的控制每个元素插入的位置，能够通过索引(元素在List中位置，类似于数组的下标)来访问List中的元素，第一个元素的索引为 0，而且允许有相同的元素。List 接口存储一组不唯一，有序（插入顺序）的对象。 |
| 3    | **Set**：Set 具有与 Collection 完全一样的接口，只是行为上不同，Set 不保存重复的元素。Set 接口存储一组唯一，无序的对象。 |
| 4    | **SortedSet**：继承于Set保存有序的集合。                     |
| 5    | **Map**：Map 接口存储一组键值对象，提供key（键）到value（值）的映射。 |
| 6    | **Map.Entry**：描述在一个Map中的一个元素（键/值对）。是一个 Map 的内部接口。 |
| 7    | **SortedMap**：继承于 Map，使 Key 保持在升序排列。           |
| 8    | **Enumeration**：这是一个传统的接口和定义的方法，通过它可以枚举（一次获得一个）对象集合中的元素。这个传统接口已被迭代器取代。 |

###### Set和List的区别

- Set 接口实例存储的是**无序**的，**不重复**的数据。List 接口实例存储的是**有序**的，可以重复的元素
- Set **检索效率低下**，**删除和插入效率高**，插入和删除不会引起元素位置改变 
- List 和数组类似，可以动态增长，根据实际存储的数据的长度自动增长 List 的长度。**查找元素效率高**，**插入删除效率低**，因为会引起其他元素位置改变

##### 集合实现类

| 序号 | 类描述                                                       |
| :--- | :----------------------------------------------------------- |
| 1    | **AbstractCollection**：实现了大部分的集合接口。             |
| 2    | **AbstractList**：继承于AbstractCollection 并且实现了大部分List接口。 |
| 3    | **AbstractSequentialList**：继承于 AbstractList ，提供了对数据元素的链式访问而不是随机访问。 |
| 4    | [**LinkedList**](https://www.runoob.com/java/java-linkedlist.html)：该类实现了List接口，允许有null（空）元素。主要用于创建链表数据结构，该类没有同步方法，如果多个线程同时访问一个List，则必须自己实现访问同步，解决方法就是在创建List时候构造一个同步的List。LinkedList 查找效率低。 |
| 5    | **[ArrayList](https://www.runoob.com/java/java-arraylist.html)**：该类也是实现了List的接口，实现了可变大小的数组，随机访问和遍历元素时，提供更好的性能。该类也是非同步的,在多线程的情况下不要使用。ArrayList 增长当前长度的50%，插入删除效率低。 |
| 6    | **AbstractSet**：继承于AbstractCollection 并且实现了大部分Set接口。 |
| 7    | [**HashSet**](https://www.runoob.com/java/java-hashset.html)：该类实现了Set接口，不允许出现重复元素，不保证集合中元素的顺序，允许包含值为null的元素，但最多只能一个。 |
| 8    | **LinkedHashSet**：具有可预知迭代顺序的 `Set` 接口的哈希表和链接列表实现。 |
| 9    | **TreeSet**：该类实现了Set接口，可以实现排序等功能。         |
| 10   | **AbstractMap**：实现了大部分的Map接口。                     |
| 11   | [**HashMap**](https://www.runoob.com/java/java-hashmap.html)：HashMap 是一个散列表，它存储的内容是键值对(key-value)映射。 该类实现了Map接口，根据键的HashCode值存储数据，具有很快的访问速度，最多允许一条记录的键为null，不支持线程同步。 |
| 12   | **TreeMap**：继承了AbstractMap，并且使用一颗树。             |
| 13   | **WeakHashMap**：继承AbstractMap类，使用弱密钥的哈希表。     |
| 14   | **LinkedHashMap**：继承于HashMap，使用元素的自然顺序对元素进行排序. |
| 15   | **IdentityHashMap**：继承AbstractMap类，比较文档时使用引用相等。 |

##### 通过java.util包中定义的类

| 序号 | 类描述                                                       |
| :--- | :----------------------------------------------------------- |
| 1    | Vector 该类和ArrayList非常相似，但是该类是同步的，可以用在多线程的情况，该类允许设置默认的增长长度，默认扩容方式为原来的2倍。 |
| 2    | Stack 栈是Vector的一个子类，它实现了一个标准的后进先出的栈。 |
| 3    | Dictionary Dictionary 类是一个抽象类，用来存储键/值对，作用和Map类相似。 |
| 4    | Hashtable Hashtable 是 Dictionary(字典) 类的子类，位于 java.util 包中。 |
| 5    | Properties Properties 继承于 Hashtable，表示一个持久的属性集，属性列表中每个键及其对应值都是一个字符串。 |
| 6    | BitSet 一个Bitset类创建一种特殊类型的数组来保存位值。BitSet中数组大小会随需要增加。 |

##### 集合算法

| 序号 | 算法描述                                               |
| :--- | :----------------------------------------------------- |
| 1    | Collection Algorithms 这里是一个列表中的所有算法实现。 |

##### 如何使用迭代器

| 序号 | 迭代器方法描述                                               |
| :--- | :----------------------------------------------------------- |
| 1    | [使用 Java Iterator](https://www.runoob.com/java/java-iterator.html) 这里通过实例列出 Iterator 和 ListIterator 接口提供的所有方法。 |

#### 3.  ArrayList

##### 添加元素

- 可以使用 `add()` 方法

##### 访问元素

- 可以使用 `get()` 方法

##### 修改元素

- 可以使用 `set()` 方法

##### 删除元素

- 可以使用 `remove()` 方法

##### 计算大小

- 可以使用 `size()` 方法

##### 迭代数组列表

- 可以使用 for 来迭代数组列表中的元素

- 也可以使用 for-each 来迭代元素

##### 其他的引用类型

如果要存储其他类型，而 `<E>` 只能为引用数据类型，这时需要使用到基本类型的包装类。

| 基本类型 | 引用类型  |
| :------- | :-------- |
| boolean  | Boolean   |
| byte     | Byte      |
| short    | Short     |
| int      | Integer   |
| long     | Long      |
| float    | Float     |
| double   | Double    |
| char     | Character |

##### ArrayList 排序

-  sort() 方法可以对字符或数字列表进行排序

##### ArrayList 方法

| 方法                                                         | 描述                                          |
| :----------------------------------------------------------- | :-------------------------------------------- |
| [add()](https://www.runoob.com/java/java-arraylist-add.html) | 将元素插入到指定位置的 arraylist 中           |
| [addAll()](https://www.runoob.com/java/java-arraylist-addall.html) | 添加集合中的所有元素到 arraylist 中           |
| [clear()](https://www.runoob.com/java/java-arraylist-clear.html) | 删除 arraylist 中的所有元素                   |
| [clone()](https://www.runoob.com/java/java-arraylist-clone.html) | 复制一份 arraylist                            |
| [contains()](https://www.runoob.com/java/java-arraylist-contains.html) | 判断元素是否在 arraylist                      |
| [get()](https://www.runoob.com/java/java-arraylist-get.html) | 通过索引值获取 arraylist 中的元素             |
| [indexOf()](https://www.runoob.com/java/java-arraylist-indexof.html) | 返回 arraylist 中元素的索引值                 |
| [removeAll()](https://www.runoob.com/java/java-arraylist-removeall.html) | 删除存在于指定集合中的 arraylist 里的所有元素 |
| [remove()](https://www.runoob.com/java/java-arraylist-remove.html) | 删除 arraylist 里的单个元素                   |
| [size()](https://www.runoob.com/java/java-arraylist-size.html) | 返回 arraylist 里元素数量                     |
| [isEmpty()](https://www.runoob.com/java/java-arraylist-isempty.html) | 判断 arraylist 是否为空                       |
| [subList()](https://www.runoob.com/java/java-arraylist-sublist.html) | 截取部分 arraylist 的元素                     |
| [set()](https://www.runoob.com/java/java-arraylist-set.html) | 替换 arraylist 中指定索引的元素               |
| [sort()](https://www.runoob.com/java/java-arraylist-sort.html) | 对 arraylist 元素进行排序                     |
| [toArray()](https://www.runoob.com/java/java-arraylist-toarray.html) | 将 arraylist 转换为数组                       |
| [toString()](https://www.runoob.com/java/java-arraylist-tostring.html) | 将 arraylist 转换为字符串                     |
| [ensureCapacity](https://www.runoob.com/java/java-arraylist-surecapacity.html)() | 设置指定容量大小的 arraylist                  |
| [lastIndexOf()](https://www.runoob.com/java/java-arraylist-lastindexof.html) | 返回指定元素在 arraylist 中最后一次出现的位置 |
| [retainAll()](https://www.runoob.com/java/java-arraylist-retainall.html) | 保留 arraylist 中在指定集合中也存在的那些元素 |
| [containsAll()](https://www.runoob.com/java/java-arraylist-containsall.html) | 查看 arraylist 是否包含指定集合中的所有元素   |
| [trimToSize()](https://www.runoob.com/java/java-arraylist-trimtosize.html) | 将 arraylist 中的容量调整为数组中的元素个数   |
| [removeRange()](https://www.runoob.com/java/java-arraylist-removerange.html) | 删除 arraylist 中指定索引之间存在的元素       |
| [replaceAll()](https://www.runoob.com/java/java-arraylist-replaceall.html) | 将给定的操作内容替换掉数组中每一个元素        |
| [removeIf()](https://www.runoob.com/java/java-arraylist-removeif.html) | 删除所有满足特定条件的 arraylist 元素         |
| [forEach()](https://www.runoob.com/java/java-arraylist-foreach.html) | 遍历 arraylist 中每一个元素并执行特定操作     |

#### 4.  LinkedList

​	链表（Linked list）是一种常见的基础数据结构，是一种线性表，但是并不会按线性的顺序存储数据，而是在每一个节点里存到下一个节点的地址。

**以下情况使用 ArrayList :**

- 频繁访问列表中的某一个元素。
- 只需要在列表末尾进行添加和删除元素操作。

**以下情况使用 LinkedList :**

- 你需要通过循环迭代来访问列表中的某些元素。
- 需要频繁的在列表开头、中间、末尾等位置进行添加和删除元素操作。

​	更多的情况下，使用 ArrayList 访问列表中的随机元素更加高效，但以下几种情况 LinkedList 提供了更高效的方法。

##### 在列表开头添加元素

- 使用 addFirst() 在头部添加元素

##### 在列表结尾添加元素

- 使用 addLast() 在尾部添加元素

##### 在列表开头移除元素

- 使用 removeFirst() 移除头部元素

##### 在列表结尾移除元素

- 使用 removeLast() 移除尾部元素

##### 获取列表开头的元素

- 使用 getFirst() 获取头部元素

##### 获取列表结尾的元素：

- 使用 getLast() 获取尾部元素

##### 迭代元素

-  可以使用 for 配合 size() 方法来迭代列表中的元素

- 也可以使用 for-each 来迭代元素

##### 常用方法

| 方法                                           | 描述                                                         |
| :--------------------------------------------- | :----------------------------------------------------------- |
| public boolean add(E e)                        | 链表末尾添加元素，返回是否成功，成功为 true，失败为 false。  |
| public void add(int index, E element)          | 向指定位置插入元素。                                         |
| public boolean addAll(Collection c)            | 将一个集合的所有元素添加到链表后面，返回是否成功，成功为 true，失败为 false。 |
| public boolean addAll(int index, Collection c) | 将一个集合的所有元素添加到链表的指定位置后面，返回是否成功，成功为 true，失败为 false。 |
| public void addFirst(E e)                      | 元素添加到头部。                                             |
| public void addLast(E e)                       | 元素添加到尾部。                                             |
| public boolean offer(E e)                      | 向链表末尾添加元素，返回是否成功，成功为 true，失败为 false。 |
| public boolean offerFirst(E e)                 | 头部插入元素，返回是否成功，成功为 true，失败为 false。      |
| public boolean offerLast(E e)                  | 尾部插入元素，返回是否成功，成功为 true，失败为 false。      |
| public void clear()                            | 清空链表。                                                   |
| public E removeFirst()                         | 删除并返回第一个元素。                                       |
| public E removeLast()                          | 删除并返回最后一个元素。                                     |
| public boolean remove(Object o)                | 删除某一元素，返回是否成功，成功为 true，失败为 false。      |
| public E remove(int index)                     | 删除指定位置的元素。                                         |
| public E poll()                                | 删除并返回第一个元素。                                       |
| public E remove()                              | 删除并返回第一个元素。                                       |
| public boolean contains(Object o)              | 判断是否含有某一元素。                                       |
| public E get(int index)                        | 返回指定位置的元素。                                         |
| public E getFirst()                            | 返回第一个元素。                                             |
| public E getLast()                             | 返回最后一个元素。                                           |
| public int indexOf(Object o)                   | 查找指定元素从前往后第一次出现的索引。                       |
| public int lastIndexOf(Object o)               | 查找指定元素最后一次出现的索引。                             |
| public E peek()                                | 返回第一个元素。                                             |
| public E element()                             | 返回第一个元素。                                             |
| public E peekFirst()                           | 返回头部元素。                                               |
| public E peekLast()                            | 返回尾部元素。                                               |
| public E set(int index, E element)             | 设置指定位置的元素。                                         |
| public Object clone()                          | 克隆该列表。                                                 |
| public Iterator descendingIterator()           | 返回倒序迭代器。                                             |
| public int size()                              | 返回链表元素个数。                                           |
| public ListIterator listIterator(int index)    | 返回从指定位置开始到末尾的迭代器。                           |
| public Object[] toArray()                      | 返回一个由链表元素组成的数组。                               |
| public T[] toArray(T[] a)                      | 返回一个由链表元素转换类型而成的数组。                       |

#### 5.  HashSet

##### 基础性质

- **HashSet** 基于 **HashMap** 来实现的，是一个不允许有重复元素的集合。

- **HashSet** 允许有 null 值。
- **HashSet** 是无序的，即不会记录插入的顺序。
- **HashSet** 不是线程安全的， 如果多个线程尝试同时修改 **HashSet**，则最终结果是不确定的。 您必须在多线程访问时显式同步对 HashSet 的并发访问。
- **HashSet** 实现了 Set 接口。

##### 基本类型的包装类

| 基本类型 | 引用类型  |
| :------- | :-------- |
| boolean  | Boolean   |
| byte     | Byte      |
| short    | Short     |
| int      | Integer   |
| long     | Long      |
| float    | Float     |
| double   | Double    |
| char     | Character |

##### 添加元素

- 使用 `add()` 方法

##### 判断元素是否存在

- 使用 `contains()` 方法来判断元素是否存在于集合当中

##### 删除元素

- 使用 `remove()` 方法来删除集合中的元素
- 删除集合中的所有元素使用 `cleat()` 方法

##### 计算大小

- 计算 **HashSet** 中的元素数量可以使用 `size()` 方法

##### 迭代 HashSet

- 可以使用 **for-each** 来迭代 **HashSet** 中的元素

#### 6.  HashMap

##### 基础性质

- **HashMap** 是一个散列表，它存储的内容是键值对(key-value)映射
- **HashMap** 实现了 Map 接口，根据键的 HashCode 值存储数据，具有很快的访问速度，最多允许一条记录的键为 null，不支持线程同步
- **HashMap** 是无序的，即不会记录插入的顺序
- **HashMap** 继承于**AbstractMap**，实现了 **Map**、**Cloneable**、**java.io.Serializable** 接口

##### 基本类型对应的包装类表如下

| 基本类型 | 引用类型  |
| :------- | :-------- |
| boolean  | Boolean   |
| byte     | Byte      |
| short    | Short     |
| int      | Integer   |
| long     | Long      |
| float    | Float     |
| double   | Double    |
| char     | Character |

##### 添加元素

- 添加键值对(key-value)可以使用 `put()` 方法

##### 访问元素

- 可以使用 `get(key)` 方法来获取 key 对应的 value

##### 删除元素

- 可以使用 `remove(key)` 方法来删除 key 对应的键值对(key-value)
- 删除所有键值对(key-value)可以使用 clear 方法

##### 计算大小

- 计算 **HashMap** 中的元素数量可以使用 `size()` 方法

##### 迭代 HashMap

- 可以使用 for-each 来迭代 **HashMap** 中的元素。

- 如果只想获取 **key**，可以使用 `keySet()` 方法，然后可以通过 get(key) 获取对应的 value；如果只想获取 **value**，可以使用 `values()` 方法

##### 常用方法列表如下

| 方法                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [clear()](https://www.runoob.com/java/java-hashmap-clear.html) | 删除 hashMap 中的所有键/值对                                 |
| [clone()](https://www.runoob.com/java/java-hashmap-clone.html) | 复制一份 hashMap                                             |
| [isEmpty()](https://www.runoob.com/java/java-hashmap-isempty.html) | 判断 hashMap 是否为空                                        |
| [size()](https://www.runoob.com/java/java-hashmap-size.html) | 计算 hashMap 中键/值对的数量                                 |
| [put()](https://www.runoob.com/java/java-hashmap-put.html)   | 将键/值对添加到 hashMap 中                                   |
| [putAll()](https://www.runoob.com/java/java-hashmap-putall.html) | 将所有键/值对添加到 hashMap 中                               |
| [putIfAbsent()](https://www.runoob.com/java/java-hashmap-putifabsent.html) | 如果 hashMap 中不存在指定的键，则将指定的键/值对插入到 hashMap 中 |
| [remove()](https://www.runoob.com/java/java-hashmap-remove.html) | 删除 hashMap 中指定键 key 的映射关系                         |
| [containsKey()](https://www.runoob.com/java/java-hashmap-containskey.html) | 检查 hashMap 中是否存在指定的 key 对应的映射关系             |
| [containsValue()](https://www.runoob.com/java/java-hashmap-containsvalue.html) | 检查 hashMap 中是否存在指定的 value 对应的映射关系           |
| [replace()](https://www.runoob.com/java/java-hashmap-replace.html) | 替换 hashMap 中是指定的 key 对应的 value                     |
| [replaceAll()](https://www.runoob.com/java/java-hashmap-replaceall.html) | 将 hashMap 中的所有映射关系替换成给定的函数所执行的结果      |
| [get()](https://www.runoob.com/java/java-hashmap-get.html)   | 获取指定 key 对应对 value                                    |
| [getOrDefault()](https://www.runoob.com/java/java-hashmap-getordefault.html) | 获取指定 key 对应对 value，如果找不到 key ，则返回设置的默认值 |
| [forEach()](https://www.runoob.com/java/java-hashmap-foreach.html) | 对 hashMap 中的每个映射执行指定的操作                        |
| [entrySet()](https://www.runoob.com/java/java-hashmap-entryset.html) | 返回 hashMap 中所有映射项的集合集合视图                      |
| [keySet](https://www.runoob.com/java/java-hashmap-keyset.html)() | 返回 hashMap 中所有 key 组成的集合视图                       |
| [values()](https://www.runoob.com/java/java-hashmap-values.html) | 返回 hashMap 中存在的所有 value 值                           |
| [merge()](https://www.runoob.com/java/java-hashmap-merge.html) | 添加键值对到 hashMap 中                                      |
| [compute()](https://www.runoob.com/java/java-hashmap-compute.html) | 对 hashMap 中指定 key 的值进行重新计算                       |
| [computeIfAbsent()](https://www.runoob.com/java/java-hashmap-computeifabsent.html) | 对 hashMap 中指定 key 的值进行重新计算，如果不存在这个 key，则添加到 hasMap 中 |
| [computeIfPresent()](https://www.runoob.com/java/java-hashmap-computeifpresent.html) | 对 hashMap 中指定 key 的值进行重新计算，前提是该 key 存在于 hashMap 中 |

#### 7.  Iterator

##### 基础性质

- Java迭代器（Iterator）是 Java 集合框架中的一种机制，是一种用于遍历集合（如列表、集合和映射等）的接口

- 它提供了一种统一的方式来访问集合中的元素，而不需要了解底层集合的具体实现细节。
- Java Iterator（迭代器）不是一个集合，它是一种用于访问集合的方法，可用于迭代 [ArrayList](https://www.runoob.com/java/java-arraylist.html) 和 [HashSet](https://www.runoob.com/java/java-hashset.html) 等集合。
- Iterator 是 Java 迭代器最简单的实现，ListIterator 是 Collection API 中的接口， 它扩展了 Iterator 接口。

##### 常用方法

- **next()** - 返回迭代器的下一个元素，并将迭代器的指针移到下一个位置
- **hasNext()** - 用于判断集合中是否还有下一个元素可以访问
- **remove()** - 从集合中删除迭代器最后访问的元素（可选操作）

#### 8.  Object

##### 基础性质

- Java Object 类是所有类的父类，也就是说 Java 的所有类都继承了 Object，**子类可以使用 Object 的所有方法**
- Object 类位于 java.lang 包中，编译时会自动导入，我们创建一个类时，如果没有明确继承一个父类，那么它就会自动继承 Object，成为 Object 的子类

##### 类的构造函数

| 序号 |      构造方法 & 描述       |
| :--- | :------------------------: |
| 1    | **Object()**构造一个新对象 |

##### 类的方法

| 序号 |                         方法 & 描述                          |
| :--- | :----------------------------------------------------------: |
| 1    | [protected Object clone()](https://www.runoob.com/java/java-object-clone.html)创建并返回一个对象的拷贝 |
| 2    | [boolean equals(Object obj)](https://www.runoob.com/java/java-object-equals.html)比较两个对象是否相等 |
| 3    | [protected void finalize()](https://www.runoob.com/java/java-object-finalize.html)当 GC (垃圾回收器)确定不存在对该对象的有更多引用时，由对象的垃圾回收器调用此方法 |
| 4    | [Class getClass()](https://www.runoob.com/java/java-object-getclass.html)获取对象的运行时对象的类 |
| 5    | [int hashCode()](https://www.runoob.com/java/java-object-hashcode.html)获取对象的 hash 值 |
| 6    | [void notify()](https://www.runoob.com/java/java-object-notify.html)唤醒在该对象上等待的某个线程 |
| 7    | [void notifyAll()](https://www.runoob.com/java/java-object-notifyall.html)唤醒在该对象上等待的所有线程 |
| 8    | [String toString()](https://www.runoob.com/java/java-object-tostring.html)返回对象的字符串表示形式 |
| 9    | [void wait()](https://www.runoob.com/java/java-object-wait.html)让当前线程进入等待状态。直到其他线程调用此对象的 notify() 方法或 notifyAll() 方法 |
| 10   | [void wait(long timeout)](https://www.runoob.com/java/java-object-wait-timeout.html)让当前线程处于等待(阻塞)状态，直到其他线程调用此对象的 notify() 方法或 notifyAll() 方法，或者超过参数设置的timeout超时时间 |
| 11   | [void wait(long timeout, int nanos)](https://www.runoob.com/java/java-object-wait-nanos.html)与 wait(long timeout) 方法类似，多了一个 nanos 参数，这个参数表示额外时间（以纳秒为单位，范围是 0-999999）。 所以超时的时间还需要加上 nanos 纳秒 |

#### 9.  泛型

​	泛型提供了编译时类型安全检测机制，该机制允许程序员在编译时检测到非法的类型。泛型的本质是参数化类型，也就是说所操作的数据类型被指定为一个参数。

##### 泛型方法

​	该方法在调用时可以接收不同类型的参数。根据传递给泛型方法的参数类型，编译器适当地处理每一个方法调用。

- 所有泛型方法声明都有一个类型参数声明部分（由尖括号分隔），该类型参数声明部分在方法返回类型之前（在下面例子中的 **<E>**）。
- 每一个类型参数声明部分包含一个或多个类型参数，参数间用逗号隔开。一个泛型参数，也被称为一个类型变量，是用于指定一个泛型类型名称的标识符。
- 类型参数能被用来声明返回值类型，并且能作为泛型方法得到的实际参数类型的占位符。
- 泛型方法体的声明和其他方法一样。注意类型参数只能代表引用型类型，不能是原始类型（像 **int、double、char** 等）。

###### java 中泛型标记符

- **E** - Element (在集合中使用，因为集合中存放的是元素)
- **T** - Type（Java 类）
- **K** - Key（键）
- **V** - Value（值）
- **N** - Number（数值类型）
- **？** - 表示不确定的 java 类型

###### 有界的类型参数

- 可能有时候，你会想限制那些被允许传递到一个类型参数的类型种类范围。例如，一个操作数字的方法可能只希望接受Number或者Number子类的实例。这就是有界类型参数的目的。

- 要声明一个有界的类型参数，首先列出类型参数的名称，后跟extends关键字，最后紧跟它的上界。

##### 泛型类

- 泛型类的声明和非泛型类的声明类似，除了在类名后面添加了类型参数声明部分。

- 和泛型方法一样，泛型类的类型参数声明部分也包含一个或多个类型参数，参数间用逗号隔开。一个泛型参数，也被称为一个类型变量，是用于指定一个泛型类型名称的标识符。因为他们接受一个或多个参数，这些类被称为参数化的类或参数化的类型。

##### 类型通配符

- 类型通配符一般是使用 **?** 代替具体的类型参数。例如 **List<?>** 在逻辑上是 **List<String>,List<Integer>** 等所有 **List<具体类型实参>** 的父类。

- 类型通配符上限通过形如List来定义，如此定义就是通配符泛型值接受Number及其下层子类类型。

- 类型通配符下限通过形如 **List<? super Number>** 来定义，表示类型只能接受 **Number** 及其上层父类类型，如 **Object** 类型的实例。

#### 10.  序列化

- Java 序列化是一种将对象转换为字节流的过程，以便可以将对象保存到磁盘上，将其传输到网络上，或者将其存储在内存中，以后再进行反序列化，将字节流重新转换为对象。

- 序列化在 Java 中是通过 **java.io.Serializable** 接口来实现的，该接口没有任何方法，只是一个标记接口，用于标识类可以被序列化。

- 当你序列化对象时，你把它包装成一个特殊文件，可以保存、传输或存储。反序列化则是打开这个文件，读取序列化的数据，然后将其还原为对象，以便在程序中使用。

- 序列化是一种用于保存、传输和还原对象的方法，它使得对象可以在不同的计算机之间移动和共享，这对于分布式系统、数据存储和跨平台通信非常有用。

##### 基本概念

- 要使一个类可序列化，需要让该类实现 java.io.Serializable 接口，这告诉 Java 编译器这个类可以被序列化。

##### 序列化对象

- **序列化对象：** 使用 ObjectOutputStream 类来将对象序列化为字节流。

##### 反序列化对象

- **反序列化对象：** 使用 ObjectInputStream 类来从字节流中反序列化对象。

#### 11.  网络编程

​	网络编程是指编写运行在多个设备（计算机）的程序，这些设备都通过网络连接起来。

​	java.net 包中 J2SE 的 API 包含有类和接口，它们提供低层次的通信细节。你可以直接使用这些类和接口，来专注于解决问题，而不用关注通信细节。java.net 包中提供了**两种常见的网络协议**的支持：

- **TCP**：TCP（英语：Transmission Control Protocol，传输控制协议） 是一种面向连接的、可靠的、基于字节流的传输层通信协议，TCP 层是位于 IP 层之上，应用层之下的中间层。TCP 保障了两个应用程序之间的可靠通信。通常用于互联网协议，被称 TCP / IP。
- **UDP**：UDP （英语：User Datagram Protocol，用户数据报协议），位于 OSI 模型的传输层。一个无连接的协议。提供了应用程序之间要发送数据的数据报。由于UDP缺乏可靠性且属于无连接协议，所以应用程序通常必须容许一些丢失、错误或重复的数据包。

##### Socket 编程

> ​	java.net.Socket 类代表一个套接字，并且 java.net.ServerSocket 类为服务器程序提供了一种来监听客户端，并与他们建立连接的机制。套接字使用TCP提供了两台计算机之间的通信机制。 客户端程序创建一个套接字，并尝试连接服务器的套接字。当连接建立时，服务器会创建一个 Socket 对象。客户端和服务器现在可以通过对 Socket 对象的写入和读取来进行通信。

以下步骤在两台计算机之间使用套接字建立TCP连接时会出现：

- 服务器实例化一个 ServerSocket 对象，表示通过服务器上的端口通信。
- 服务器调用 ServerSocket 类的 accept() 方法，该方法将一直等待，直到客户端连接到服务器上给定的端口。
- 服务器正在等待时，一个客户端实例化一个 Socket 对象，指定服务器名称和端口号来请求连接。
- Socket 类的构造函数试图将客户端连接到指定的服务器F和端口号。如果通信被建立，则在客户端创建一个 Socket 对象能够与服务器进行通信。
- 在服务器端，accept() 方法返回服务器上一个新的 socket 引用，该 socket 连接到客户端的 socket。

连接建立后，通过使用 I/O 流在进行通信，每一个socket都有一个输出流和一个输入流，客户端的输出流连接到服务器端的输入流，而客户端的输入流连接到服务器端的输出流。TCP 是一个双向的通信协议，因此数据可以通过两个数据流在同一时间发送。

##### ServerSocket 类的方法

> 服务器应用程序通过使用 java.net.ServerSocket 类以获取一个端口，并且侦听客户端请求。

###### ServerSocket 类有四个构造方法

| **序号** | **方法描述**                                                 |
| -------- | ------------------------------------------------------------ |
| 1        | **public ServerSocket(int port) throws IOException** 创建绑定到特定端口的服务器套接字。 |
| 2        | **public ServerSocket(int port, int backlog) throws IOException** 利用指定的 backlog 创建服务器套接字并将其绑定到指定的本地端口号。 |
| 3        | **public ServerSocket(int port, int backlog, InetAddress address) throws IOException** 使用指定的端口、侦听 backlog 和要绑定到的本地 IP 地址创建服务器。 |
| 4        | **public ServerSocket() throws IOException** 创建非绑定服务器套接字。 |

​	创建非绑定服务器套接字。 如果 ServerSocket 构造方法没有抛出异常，就意味着你的应用程序已经成功绑定到指定的端口，并且侦听客户端请求。

###### ServerSocket 类的常用方法

| **序号** | **方法描述**                                                 |
| -------- | ------------------------------------------------------------ |
| 1        | **public int getLocalPort()**  返回此套接字在其上侦听的端口。 |
| 2        | **public Socket accept() throws IOException** 侦听并接受到此套接字的连接。 |
| 3        | **public void setSoTimeout(int timeout)**  通过指定超时值启用/禁用 SO_TIMEOUT，以毫秒为单位。 |
| 4        | **public void bind(SocketAddress host, int backlog)** 将 ServerSocket 绑定到特定地址（IP 地址和端口号）。 |

##### Socket 类的方法

> java.net.Socket 类代表客户端和服务器都用来互相沟通的套接字。客户端要获取一个 Socket 对象通过实例化 ，而服务器获得一个 Socket 对象则通过 accept() 方法的返回值。

###### Socket 类有五个构造方法

| **序号** | **方法描述**                                                 |
| -------- | ------------------------------------------------------------ |
| 1        | **public Socket(String host, int port) throws UnknownHostException, IOException.** 创建一个流套接字并将其连接到指定主机上的指定端口号。 |
| 2        | **public Socket(InetAddress host, int port) throws IOException** 创建一个流套接字并将其连接到指定 IP 地址的指定端口号。 |
| 3        | **public Socket(String host, int port, InetAddress localAddress, int localPort) throws IOException.** 创建一个套接字并将其连接到指定远程主机上的指定远程端口。 |
| 4        | **public Socket(InetAddress host, int port, InetAddress localAddress, int localPort) throws IOException.** 创建一个套接字并将其连接到指定远程地址上的指定远程端口。 |
| 5        | **public Socket()** 通过系统默认类型的 SocketImpl 创建未连接套接字 |

​	当 Socket 构造方法返回，并没有简单的实例化了一个 Socket 对象，它实际上会尝试连接到指定的服务器和端口。

##### 服务端与客户端通用方法

| **序号** | **方法描述**                                                 |
| -------- | ------------------------------------------------------------ |
| 1        | **public void connect(SocketAddress host, int timeout) throws IOException** 将此套接字连接到服务器，并指定一个超时值。 |
| 2        | **public InetAddress getInetAddress()**  返回套接字连接的地址。 |
| 3        | **public int getPort()** 返回此套接字连接到的远程端口。      |
| 4        | **public int getLocalPort()** 返回此套接字绑定到的本地端口。 |
| 5        | **public SocketAddress getRemoteSocketAddress()** 返回此套接字连接的端点的地址，如果未连接则返回 null。 |
| 6        | **public InputStream getInputStream() throws IOException** 返回此套接字的输入流。 |
| 7        | **public OutputStream getOutputStream() throws IOException** 返回此套接字的输出流。 |
| 8        | **public void close() throws IOException** 关闭此套接字。    |

------

##### InetAddress 类的方法

这个类表示互联网协议(IP)地址。下面列出了 Socket 编程时比较有用的方法：

| **序号** | **方法描述**                                                 |
| -------- | ------------------------------------------------------------ |
| 1        | **static InetAddress getByAddress(byte[] addr)** 在给定原始 IP 地址的情况下，返回 InetAddress 对象。 |
| 2        | **static InetAddress getByAddress(String host, byte[] addr)** 根据提供的主机名和 IP 地址创建 InetAddress。 |
| 3        | **static InetAddress getByName(String host)** 在给定主机名的情况下确定主机的 IP 地址。 |
| 4        | **String getHostAddress()**  返回 IP 地址字符串（以文本表现形式）。 |
| 5        | **String getHostName()**   获取此 IP 地址的主机名。          |
| 6        | **static InetAddress getLocalHost()** 返回本地主机。         |
| 7        | **String toString()** 将此 IP 地址转换为 String。            |

#### 12.   多线程编程

> Java 给多线程编程提供了内置的支持。 一条线程指的是进程中一个单一顺序的控制流，一个进程中可以并发多个线程，每条线程并行执行不同的任务。
>
> 多线程是多任务的一种特别的形式，但多线程使用了更小的资源开销。
>
> 进程：一个进程包括由操作系统分配的内存空间，包含一个或多个线程。一个线程不能独立的存在，它必须是进程的一部分。一个进程一直运行，直到所有的非守护线程都结束运行后才能结束。
>
> 多线程能满足程序员编写高效率的程序来达到充分利用 CPU 的目的。

##### 线程的生命周期

- 新建状态:

  使用 **new** 关键字和 **Thread** 类或其子类建立一个线程对象后，该线程对象就处于新建状态。它保持这个状态直到程序 **start()** 这个线程。

- 就绪状态:

  当线程对象调用了start()方法之后，该线程就进入就绪状态。就绪状态的线程处于就绪队列中，要等待JVM里线程调度器的调度。

- 运行状态:

  如果就绪状态的线程获取 CPU 资源，就可以执行 **run()**，此时线程便处于运行状态。处于运行状态的线程最为复杂，它可以变为阻塞状态、就绪状态和死亡状态。

- 阻塞状态:

  如果一个线程执行了sleep（睡眠）、suspend（挂起）等方法，失去所占用资源之后，该线程就从运行状态进入阻塞状态。在睡眠时间已到或获得设备资源后可以重新进入就绪状态。可以分为三种：

  - 等待阻塞：运行状态中的线程执行 wait() 方法，使线程进入到等待阻塞状态。
  - 同步阻塞：线程在获取 synchronized 同步锁失败(因为同步锁被其他线程占用)。
  - 其他阻塞：通过调用线程的 sleep() 或 join() 发出了 I/O 请求时，线程就会进入到阻塞状态。当sleep() 状态超时，join() 等待线程终止或超时，或者 I/O 处理完毕，线程重新转入就绪状态。

- 死亡状态:

  一个运行状态的线程完成任务或者其他终止条件发生时，该线程就切换到终止状态。

##### 线程的优先级

- 每一个 Java 线程都有一个优先级，这样有助于操作系统确定线程的调度顺序。

- Java 线程的优先级是一个整数，其取值范围是 `1(Thread.MIN_PRIORITY ) - 10(Thread.MAX_PRIORITY )`

- 默认情况下，每一个线程都会分配一个优先级 NORM_PRIORITY（5）。

- 具有较高优先级的线程对程序更重要，并且应该在低优先级的线程之前分配处理器资源。但是，线程优先级不能保证线程执行的顺序，而且非常依赖于平台。

##### 创建一个线程

Java 提供了三种创建线程的方法：

- 通过实现 Runnable 接口；
- 通过继承 Thread 类本身；
- 通过 Callable 和 Future 创建线程。

##### 通过实现 Runnable 接口来创建线程

​	创建一个线程，最简单的方法是创建一个实现 Runnable 接口的类。为了实现 Runnable，一个类只需要执行一个方法调用 run()，声明如下：

```java
public void run()
```

​	你可以重写该方法，重要的是理解的 run() 可以调用其他方法，使用其他类，并声明变量，就像主线程一样。在创建一个实现 Runnable 接口的类之后，你可以在类中实例化一个线程对象。Thread 定义了几个构造方法，下面的这个是我们经常使用的：

```java
Thread(Runnable threadOb,String threadName);
```

​	这里，threadOb 是一个实现 Runnable 接口的类的实例，并且 threadName 指定新线程的名字。新线程创建之后，你调用它的 start() 方法它才会运行。

```java
void start();
```

##### 通过继承Thread来创建线程

​	创建一个线程的第二种方法是创建一个新的类，该类继承 Thread 类，然后创建一个该类的实例。继承类必须重写 run() 方法，该方法是新线程的入口点。它也必须调用 start() 方法才能执行。该方法尽管被列为一种多线程实现方式，但是本质上也是实现了 Runnable 接口的一个实例。

##### Thread 方法

###### Thread 对象调用的方法

| **序号** |                         **方法描述**                         |
| :------- | :----------------------------------------------------------: |
| 1        | **public void start()** 使该线程开始执行；**Java** 虚拟机调用该线程的 run 方法 |
| 2        | **public void run()** 如果该线程是使用独立的 Runnable 运行对象构造的，则调用该 Runnable 对象的 run 方法；否则，该方法不执行任何操作并返回 |
| 3        | **public final void setName(String name)** 改变线程名称，使之与参数 name 相同 |
| 4        | **public final void setPriority(int priority)**  更改线程的优先级 |
| 5        | **public final void setDaemon(boolean on)** 将该线程标记为守护线程或用户线程 |
| 6        | **public final void join(long millisec)** 等待该线程终止的时间最长为 millis 毫秒 |
| 7        |             **public void interrupt()** 中断线程             |
| 8        | **public final boolean isAlive()** 测试线程是否处于活动状态  |

###### Thread 静态方法

| **序号** |                         **方法描述**                         |
| :------- | :----------------------------------------------------------: |
| 1        | **public static void yield()** 暂停当前正在执行的线程对象，并执行其他线程 |
| 2        | **public static void sleep(long millisec)** 在指定的毫秒数内让当前正在执行的线程休眠（暂停执行），此操作受到系统计时器和调度程序精度和准确性的影响 |
| 3        | **public static boolean holdsLock(Object x)** 当且仅当当前线程在指定的对象上保持监视器锁时，才返回 true |
| 4        | **public static Thread currentThread()** 返回对当前正在执行的线程对象的引用 |
| 5        | **public static void dumpStack()** 将当前线程的堆栈跟踪打印至标准错误流 |

##### 通过 Callable 和 Future 创建线程

- 创建 Callable 接口的实现类，并实现 call() 方法，该 call() 方法将作为线程执行体，并且有返回值。
- 创建 Callable 实现类的实例，使用 FutureTask 类来包装 Callable 对象，该 FutureTask 对象封装了该 Callable 对象的 call() 方法的返回值。
- 使用 FutureTask 对象作为 Thread 对象的 target 创建并启动新线程。
- 调用 FutureTask 对象的 get() 方法来获得子线程执行结束后的返回值。

##### 创建线程的三种方式的对比

- 采用实现 Runnable、Callable 接口的方式创建多线程时，线程类只是实现了 Runnable 接口或 Callable 接口，还可以继承其他类。
- 使用继承 Thread 类的方式创建多线程时，编写简单，如果需要访问当前线程，则无需使用 Thread.currentThread() 方法，直接使用 this 即可获得当前线程。

##### 线程的几个主要概念

- 线程同步
- 线程间通信
- 线程死锁
- 线程控制：挂起、停止和恢复

##### 多线程的使用

- 有效利用多线程的关键是理解程序是并发执行而不是串行执行的。例如：程序中有两个子系统需要并发执行，这时候就需要利用多线程编程。

- 通过对多线程的使用，可以编写出非常高效的程序。不过请注意，如果你创建太多的线程，程序执行的效率实际上是降低了，而不是提升了。

- 请记住，上下文的切换开销也很重要，如果你创建了太多的线程，CPU 花费在上下文的切换的时间将多于执行程序的时间！

#### 13.  Applet 基础

​	Applet 是一种 Java 程序。它一般运行在支持 Java 的 Web 浏览器内。因为它有完整的 Java API支持,所以Applet 是一个全功能的 Java 应用程序。如下所示是独立的 Java 应用程序和 applet 程序之间重要的不同：

- Java 中 Applet 类继承了 java.applet.Applet 类。
- Applet 类没有定义 main()，所以一个 Applet 程序不会调用 main() 方法。
- Applet 被设计为嵌入在一个 HTML 页面。
- 当用户浏览包含 Applet 的 HTML 页面，Applet 的代码就被下载到用户的机器上。
- 要查看一个 Applet 需要 JVM。 JVM 可以是 Web 浏览器的一个插件，或一个独立的运行时环境。
- 用户机器上的 JVM 创建一个 Applet 类的实例，并调用 Applet 生命周期过程中的各种方法。
- Applet 有 Web 浏览器强制执行的严格的安全规则，Applet 的安全机制被称为沙箱安全。
- Applet 需要的其他类可以用 Java 归档（JAR）文件的形式下载下来。

##### Applet的生命周期

Applet 类中的四个方法给我们提供了一个框架，可以在该框架上开发小程序：

- **init:** 该方法的目的是为你的 Applet 提供所需的任何初始化。在 Applet 标记内的 param 标签被处理后调用该方法。
- **start:** 浏览器调用 init 方法后，该方法被自动调用。每当用户从其他页面返回到包含 Applet 的页面时，则调用该方法。
- **stop:** 当用户从包含 Applet 的页面移除的时候，该方法自动被调用。因此，可以在相同的 Applet 中反复调用该方法。
- **destroy:** 此方法仅当浏览器正常关闭时调用。因为 Applet 只有在 HTML 网页上有效，所以你不应该在用户离开包含 Applet 的页面后遗漏任何资源。
- **paint:** 该方法在 start() 方法之后立即被调用，或者在 Applet 需要重绘在浏览器的时候调用。paint() 方法实际上继承于 java.awt。

##### Applet 类

​	每一个 Applet 都是 java.applet.Applet 类的子类，基础的 Applet 类提供了供衍生类调用的方法,以此来得到浏览器上下文的信息和服务。这些方法做了如下事情：

- 得到 Applet 的参数
- 得到包含 Applet 的 HTML 文件的网络位置
- 得到 Applet 类目录的网络位置
- 打印浏览器的状态信息
- 获取一张图片
- 获取一个音频片段
- 播放一个音频片段
- 调整此 Applet 的大小

​	除此之外，Applet 类还提供了一个接口，该接口供 Viewer 或浏览器来获取 Applet 的信息，并且来控制 Applet 的执行。Viewer 可能是：

- 请求 Applet 作者、版本和版权的信息
- 请求 Applet 识别的参数的描述
- 初始化 Applet
- 销毁 Applet
- 开始执行 Applet
- 结束执行 Applet

​	Applet 类提供了对这些方法的默认实现，这些方法可以在需要的时候重写。"Hello，World"applet 都是按标准编写的。唯一被重写的方法是 paint 方法。

##### Applet 的调用

​	Applet 是一种 Java 程序。它一般运行在支持 Java 的 Web 浏览器内。因为它有完整的 Java API 支持,所以 Applet 是一个全功能的 Java 应用程序。

##### 获得applet参数

- CheckerApplet 在 `init()` 方法里得到它的参数。也可以在 `paint()` 方法里得到它的参数。然而，在 Applet 开始得到值并保存了设置，而不是每一次刷新的时候都得到值，这样是很方便，并且高效的。

- Applet viewer 或者浏览器在 Applet 每次运行的时候调用 `init()` 方法。在加载 Applet 之后，Viewer 立即调用 `init()` 方法（Applet.init()什么也没做），重写该方法的默认实现，添加一些自定义的初始化代码。

- Applet.getParameter() 方法通过给出参数名称得到参数值。如果得到的值是数字或者其他非字符数据，那么必须解析为字符串类型。

##### 指定 applet 参数

​	如下的例子是一个HTML文件，其中嵌入了 CheckerApplet 类。HTML文件通过使用 <param> 标签的方法给 applet 指定了两个参数。

```html
<applet code="CheckerApplet.class" width="480" height="320">
<param name="color" value="blue">
<param name="squaresize" value="30">
</applet>
```

##### 生存现状

​	**目前已经被主流浏览器淘汰，不建议学习。**

#### 14.  文档注释

- 单行注释：**//** 
- 多行注释：**/\* \*/**
- 文档注释：以 **/\**** 开始，以 ***/** 结束

##### javadoc 标签

| **标签**      |                        **描述**                        |                           **示例**                           |
| :------------ | :----------------------------------------------------: | :----------------------------------------------------------: |
| @author       |                    标识一个类的作者                    |                     @author description                      |
| @deprecated   |                 指名一个过期的类或成员                 |                   @deprecated description                    |
| {@docRoot}    |                指明当前文档根目录的路径                |                        Directory Path                        |
| @exception    |                  标志一个类抛出的异常                  |            @exception exception-name explanation             |
| {@inheritDoc} |                  从直接父类继承的注释                  |      Inherits a comment from the immediate surperclass.      |
| {@link}       |               插入一个到另一个主题的链接               |                      {@link name text}                       |
| {@linkplain}  |  插入一个到另一个主题的链接，但是该链接显示纯文本字体  |          Inserts an in-line link to another topic.           |
| @param        |                   说明一个方法的参数                   |              @param parameter-name explanation               |
| @return       |                     说明返回值类型                     |                     @return explanation                      |
| @see          |               指定一个到另一个主题的链接               |                         @see anchor                          |
| @serial       |                   说明一个序列化属性                   |                     @serial description                      |
| @serialData   | 说明通过writeObject( ) 和 writeExternal( )方法写的数据 |                   @serialData description                    |
| @serialField  |             说明一个ObjectStreamField组件              |              @serialField name type description              |
| @since        |               标记当引入一个特定的变化时               |                        @since release                        |
| @throws       |                 和 @exception标签一样.                 | The @throws tag has the same meaning as the @exception tag.  |
| {@value}      |         显示常量的值，该常量必须是static属性。         | Displays the value of a constant, which must be a static field. |
| @version      |                      指定类的版本                      |                        @version info                         |

##### 文档注释

- 在开始的 **/\**** 之后，第一行或几行是关于类、变量和方法的主要描述。

- 之后，你可以包含一个或多个各种各样的 **@** 标签。每一个 **@** 标签必须在一个新行的开始或者在一行的开始紧跟星号 *****。

- 多个相同类型的标签应该放成一组。例如，如果你有三个 **@see** 标签，可以将它们一个接一个的放在一起。

```java
/*** 这个类绘制一个条形图
* @author runoob
* @version 1.2
*/
```

##### javadoc 输出什么

- javadoc 工具将你 Java 程序的源代码作为输入，输出一些包含你程序注释的HTML文件。

- 每一个类的信息将在独自的HTML文件里。javadoc 也可以输出继承的树形结构和索引。

- 由于 javadoc 的实现不同，工作也可能不同，你需要检查你的 Java 开发系统的版本等细节，选择合适的 Javadoc 版本。

#### 15.  MySQL 连接

- 创建 JDBC 驱动名和数据库 URL；
- 使用 `Class.forName()` 注册 JDBC 驱动；
- 使用 `DriverManager.getConnection()` 打开链接；
- 使用 `createstatement()` 实例化 statement 对象，用于将 SQL 命令发送到数据库执行；
- 使用 `excuteQuery()` 进行 SQL 语言的查询操作；
- 返回值用 `ResultSet` 存储，为集合形式，可以做后续数据处理。







































