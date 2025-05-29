## 3. Verilog 高级教程

### 3.1. 编码风格

#### 3.1.1.

信号变量、模块等一定要使用有意义的名字，且信号名称在模块间穿梭时也应该保持不变，以便代码本身就具有清晰的说明信息，增强可读性。

当名字单词数量过多时，可以使用 `_` 进行拼接。

建议使用单词缩写的方式对信号进行命名，并懂得取舍，避免过长的信号命名。

虽然 Verilog 区分大小写，但是建议一般功能模块的名称、端口、信号变量等全部使用小写，`parameter` 使用大写，一些电源、Pad 等特殊端口使用大写。只为编写代码方便，容易区分变量常量，不用考虑大小写不一样但名字相同的信号变量的差异。
​	寄存器变量一般加后缀 `_r` ，延迟打拍的变量加后缀 `_r1` 、`_r2` 等。主要有两大好处，一是 RTL 设计时容易根据变量类型对数据进行操作；二是综合后网表的信号名字经常会改变，加入后缀容易在综合后的网表中找到与 RTL 中对应的信号变量。

其他后缀：`_d` 可以表示延迟后的信号，`_t` 可以表示暂时存储的信号，`_n` 可以表示低电平有效的信号，`_s` 可以表示 slave 信号，`_m` 可以表示 master 信号等。

避免使用关键字对信号进行命名。

文件名保持与设计的 `module` 名字一致，文件内尽量只包含一个设计模块。

#### 3.1.2. 注释

每一个设计模块开头，都应该包含文件说明信息，包括版权、模块名字、作者、日期、梗概、修改记录等信息。

```verilog
/**********************************************************
// Copyright 1891.06.02-2017.07.14
// Contact with willrious@sina.com
================ runoob.v ======================
>> Author       : wxss
>> Date         : 2025.09.07
>> Description  : Welcome
>> note         : (1)To 
>>              : (2)My
>> V180121      : World.
************************************************************/
```

注释应该精炼的表达出代码所描述的意义，简短的注释在一行语句代码之后添加，过长的注释提前一行书写。

注释尽量用英文书写，以保证不同操作系统、不同编辑器下能够正常显示。端口信号中，除一般的时钟和复位信号，其他信号最好也进行注释。

#### 3.1.3. 优化

使用圆括号确定程序的优先级或逻辑结构。为避免操作符优先级问题导致设计错误，建议多多使用圆括号。同时，圆括号的巧妙使用有时候优化逻辑综合后的结构。

条件语句尽量使用 `case` 语句代替 `if` 语句。当同级别的条件判断语句过多时，使用 `case` 语句综合后的硬件结构，往往比 `if` 语句消耗更少的资源，拥有更好的时序。

状态机编写时，尽量使用 3 段式，以保证代码具有良好的整洁性和安全性。

系统设计时，尽量采用模块按功能分隔，然后进行模块例化的方法。相比于成千上万行代码都集成在一个文件中，模块分隔有利于团队设计，便于更新维护。

#### 3.1.4. 美观

端口信号保证每行一个信号，逗号跟在端口声明之后，并保持逗号对齐。

一行代码内容过长时，尽量换行编写，无需使用换行符。

尽量使用 `begin` 和 `end` 的方式保证执行语句间的层叠关系，`begin` 与关键字同行，`end` 另起一行。即便在只有一条执行语句时，可以省略 `begin` 和 `end` 关键字，但为保证结构的完整性，以及后续代码的调试与修改，还是建议加入此类关键字。

尽量使用 `tab` 键和空格，保证语句按照层级结构对齐，变量、关键字、操作符之间也应该留有空隙，便于逻辑判断。

模块例化时，端口信号尽量与连接信号隔开，并各自对齐。连接信号为向量时指明其位宽，方便阅读、调式。例化多个相同的模块时，尽量使用 `generate` 语句，避免过长的例化代码描述。

### 3.2. 代码规范

#### 3.2.1. 赋初值

变量声明时不要对变量进行赋初值操作。如果变量声明时设置初始值，仿真时变量会有期望的初值，但综合后电路的初始值，是不确定的。如果信号初值会影响逻辑功能，则仿真过程可能会因验证不充分而错过查找处逻辑错误的机会。

赋初值操作应该在复位状态下完成，也建议寄存器变量都是用复位端，以保证系统商店或紊乱时，可以通过复位操作让系统恢复初始状态。建议设计时，时钟采用正边沿逻辑，复位采用负边沿逻辑。复位时语句块中所有信号都应该赋予初值，不要漏掉相关信号。

####  3.2.2. always 语句

不到万不得已，不要在 2 个 `always` 块中分别使用同一时钟的上升沿和下降沿逻辑，否则会引入相对复杂的时钟质量和时序约束问题。

禁止在一个 `always` 块中同时将时钟的双边沿作为触发条件，编译、仿真可能会按照设计人员的思想进行，但此类电路往往不可综合，或综合后电路功能不符合预期。

禁止在 2 个 `always` 块中为同一个变量赋值。

一个 `always` 块中，不要存在多个并行或不相关的条件语句，使用多个 `always` 分别描述。当一个 `always` 语句中存在多个并行或不相关的条件语句时，仿真的执行结果或综合的实际电路中，不相关的条件语句都是并行执行的。但是仿真结果可能是顺序执行的，如果有延迟，信息可能会导致不可以预知的错误结果。且该写法可读性差，功能结构划分不明显。

#### 3.2.3. 时钟和异步

设计中尽量使用同步设计。必须使用异步逻辑时，一定要对不同时钟域之间的信号进行同步处理，不能直接使用相关信号，否则会产生亚稳态电路。

尽量不要直接将时钟信号与普通变量信号做逻辑操作，或对时钟信号进行电平信号的检测判断。

#### 3.2.4. 综合

一般情况下，信号变量不要直接使用乘法 `*` 、除法 `\` 、求余 `%` 等操作。这些操作符被综合后，结构和时序往往不易控制。应该使用相关优化后的 IP 模块或工艺库中的集成模块。但是 `parameter` 类型的变量就可以使用此类操作符，因为在编译之初，编译器就会计算出常量运算的结果，不会消耗多余的硬件资源。组合逻辑的条件语句中条件补充完整，组合逻辑的 `always` 中敏感信号罗列完全，以避免不期望的 Latch 产生。

逻辑设计时要考虑代码能不能综合成实际电路，会综合成什么样的电路。

#### 3.2.5. 例化

例化时，连接信号端的信号可以是 `reg` 型或 `wire` 型变量，连接输出端的信号一定是 `wire` 型变量。但是端口信号声明时，输入信号必须是 `wire` 型变量，输出信号可以是 `reg` 型或 `wire` 型变量。

### 3.3. 门的类型

门级建模，是使用基本的逻辑单元，进行更低级抽象层次上的设计。与行为级建模相比，门级建模更注重硬件的实现方法，即通过连接一些基本门电路去实现多种逻辑功能。

虽然，行为级建模最后也会被综合成基本的门级电路，但对于复杂的设计来说，行为级建模的效率远远高于门级建模。所以目前 Verilog 大多数用于描述数字设计的行为级层次（RTL），一般只注重设计实现的算法或流程，而不用特别关心具体的硬件实现方式。

另外一些设计，例如门控时钟，就需要使用基本门单元，来增加电路的可控性与可靠性。

#### 3.3.1. 多输入门

多数入门只有单个输出，由单个或多个输入端。Verilog 内置多输入门有：`and` 、`nand` 、`or` 、`nor` 、`xor` 、`xnor` 。使用基本逻辑门单元去实现一些简单的逻辑功能时，使用模块例化的方式即可。门级单元第一个端口是输出，后面端口是输入，例化时，也可以不指定实例的名字。当输入端口超过 2 个时，只需将输入信号在端口列表中继续排列即可，Verilog 可自动识别。

```verilog
// basic gate instantiation
and 	a1			(OUTX,	IN1, IN2) ;
nand 	na1			(OUTX1, IN1, IN2) ;
or		or1			(OUTY, 	IN1, IN2) ;
nor 	nor1		(OUTY1, IN1, IN2) ;
// 3 input
xor xor1			(OUTZ, 	IN1, IN2, IN3) ;
// no instantiation name
xnor					(OUTZ1, IN1, IN2) ;
```

#### 3.3.2. 多输出门

多出门只有单个输入，有单个或多输出端，又可称之为 `buffer` ，起缓冲、延时作用。

```verilog
// buffer
buf
// not
not
```

和多输入门类似，可以使用模块例化的方式对多输出门进行调用。门级单元第一个端口是输出，最后一个端口是输入。当输入端口超过 1 个时，需将输出信号在最后一个输入端口前排列。

```verilog
// buf
buf buf1		(OUTX2, IN1) ;
// 2 output
buf buf2		(OUTY2, OUTY3, IN2) ;
// no instantiation name
not					(OUTZ3, IN3) ; 
```

#### 3.3.3. 三态门

Verilog 中，还提供了 4 个带有控制端的 buffer 门单元，成为三态门。只有当控制信号有效时，数据才能正常传递，否则输出为高阻抗状态 `z` 。

例化时，三态门第一个端口为输出端，第二个端口为数据输入端，第三个端口为控制输入端。例化时，信号排列顺序要一致，三态门不支持输出端口超过 1 个，但例化时可以不指定实例的名字。

```verilog
// tri
bufif1 buf1		(OUTX, IN1, CTRL1) ;
bufif0 buf2		(OUTZ, IN1, CTRL2) ;
bufif1 buf3		(OUTZ, IN1, CTRL3) ;
// no instantiation name
notif0 					(OUTX1, IN1, CTRL4) ;
```

#### 3.3.4. 上下拉电阻

上拉是将不确定的信号通过一个电阻，钳制在一个高电平；下拉是将不确定的信号是通过一个电阻与地相连，固定在低电平。

模块端口的上拉或下拉电阻，具有限流、提高驱动能力、防静电等作用，可以有效保护电路；当信号方向为输入且没有输入信号（高阻态）时，上拉会将该信号的逻辑值置为 `1`， 下拉会将该信号的逻辑值置为 `0` 。

Verilog 提供了为信号设置上、下拉电阻的逻辑单元，多用于模块端口信号。此类门单元没有输入，只有输出，关键词如下。

```verilog
// set pull up
pullup
// set pull down
pulldown
```

例化调用时，只要填写需要设置上下拉电阻的信号即可，实例的名字也可以不指定。

### 3.4. 开关级建模

开关级建模是比门级建模更为低级抽象层次的射级。在极少数情况下，设计者可能会选择使用晶体管作为设计的底层模块。随着电路设计复杂度及相关先进工具的出现，以开关为基础的数字设计慢慢步入黄昏。目前，Verilog 仅仅提供了用逻辑值 0 、1 、x 、z 作为相关驱动强度的数字设计能力，因此，Verilog 中晶体管也仅被当作导通或截止的开关。

#### 3.4.1. MOS 开关

MOS 开关有 2 种。

```verilog
// N type mos
nmos
// P type mos
pmos
// with high resistance N type mos
rnmos
// with high resistance P type mos
rpmos
```

MOS 管用来作为开关逻辑建模，数据从输入流入输出，可通过适当设置来开、关数据流。带有阻抗的 MOS 管，源极到漏极的阻抗较高，且在传递信号是会减小信号的强度。

例化时，MOS 管第一个端口为输出端，第二个端口为数据输入端，第三个端口为控制输入端。

```verilog
// tri
pmos pmos1		(OUTX, IN1, CTRL1) ;
// no instantiation name
nmos					(OUTX1, IN1, CTRL1) ;
```

#### 3.4.2. CMOS 开关

CMOS 开关用关键字 `cmos` 和 `rcmos` （带有高阻抗）声明。CMOS 有一个数据输出，一个数据输入和 2 个控制输入。可以将 CMOS 开关看作是 NMOS 与 PMOS 开关的组合体。

例化时，CMOS 管第一个端口为输出端，第二个端口为数据输入端，第三个端口为 `Ncontrol` 控制输入端，第四个端口为 `Pcontrol` 控制输入端。

```verilog
// cmos
cmos c1		(OUTY, IN1, NCTRL, PCTRL) ;
// no instantiation name
cmos			(OUTY1, IN1, NCTRL, PCTRL) ;
```

既然 CMOS 可以看作是 NMOS 与 PMOS 开关的组合体，所以还可以用这两种 MOS 开关去搭建 CMOS 开关。

```verilog
// the same 2-way instancetiation of cmos
nmos n2		(OUTY, IN1, NCTRL) ;
pmos p2		(OUTY, IN1, PCTRL) ;
```

#### 3.4.3. 双向开关

NMOS、PMOS、CMOS 开关门都是从漏极向源极导通，方向是单向的。Verilog 中还提供了双向导通的开关器件，数据可以双向流动，两边的信号都可以是驱动信号。

```verilog
tran tranif1 tranif0 rtran rtranif1 rtranif0
```

- `tran` ：为两个信号的直接缓存，`inout1` 或 `inout2` 均可以是驱动信号；
- `tranif1` ：仅当 `control` 信号为 1 时，开关两边的信号导通；当 `control` 为 0 时，两个信号断开，有驱动源的信号会和驱动源保持一致的信号值，没有驱动源的信号色泽呈现为高祖状态；
- `tranif0` ：同理。

因此，双向开关常用来进行总线或信号之间的隔离。例化时，双向开关前两个端口为数据端，第三个端口为 `control` 控制输入端。

```verilog
// tri
tranif0 tr0		(INOUT1, INOUT2, CONTROL) ;
// no instantition name
tranif1				(INOUT1, INOUT2, CONTROL) ;
```

#### 3.4.4. 电源和地

晶体管级电路需要源极（Vdd，逻辑 1）与地级（Vss，逻辑 0），分别用关键字 `supply1` 和 `supply0` 来定义。

```verilog
supply1			VDD ；
supply0			GND ;
wire				siga = VDD ; // siga is connected to logic 1
wire				sigb = GND ; // sigb is connected to logic 0
```

### 3.5. 门延迟

实际门级电路都是有延迟的，Verilog 允许用户使用门延迟，来定义输入到其输出信号的传输延迟。

#### 3.5.1. 延迟类型

##### 上升延迟

在门的输入发生变化时，门的输出从 0 ，x ，z 变化为 1 所需要的转变时间，称为上升延迟。

##### 下降延迟

在门的输入发生变化时，门的输出从 1 ，x ，z 变化为 0 所需要的转变时间，成为下降延迟。

##### 关断延迟

关断延迟是指门的输出从 0 ，1 ，x 变化为高阻态 z 所需要的转变时间。

##### 延迟定义

门延迟可以在单元门例化时定义，定义格式如下。

```verilog
gate_type [delay]	[instance_name] (signal_list)
```

其中，`delay` 的个数可以为 0 个、1 个、2 个、或 3 个。

| 延迟类型 | 无延迟 | 1 个延迟 | 2 个延迟（d1，d2） | 3 个延迟（d1，d2，d3） |
| -------- | :----: | :------: | :----------------: | :--------------------: |
| 上升     |   0    |    d     |         d1         |           d1           |
| 下降     |   0    |    d     |         d2         |           d2           |
| 关断     |   0    |    d     |    min(d1, d2)     |           d3           |
| `to_x`   |   0    |    d     |    min(d1, d2)     |    min(d1, d2, d3)     |

#### 3.5.2. 最小/典型/最大延迟

由于集成电路制造工艺的差异，实际电路中器件的延迟总会在一定的范围内波动。Verilog 中，用户不仅可以指定 3 中类型的门延迟，还可以对每种类型的门延迟指定其最小值、典型值和最大值。在编译或仿真阶段，来选择使用哪一种延迟值，为更切合实际的仿真提供了支持。

### 3.6. UDP 基础知识

门级建模中介绍的内置门单元，均属于 Verilog 自带的一整套标准原语，即通常所说的内置原语。此外，Verilog 还为用户提供了自己编写原语的能力，这种原语就是用户自定义原语（User Defined Primitive，UDP）。在UDP 中，不能调用其他 `module` 或 `primitive`，调用方式和门级原语完全相同。

#### 3.6.1. UPD 定义

UDP 的定义不依赖于模块定义，因此可以出现在模块定义外，也可以单独在文件里定义。

```verilog
primitive UDP_name (
	output_name,
  list_of_input) ;
  
  output_declaration ;
  list_of_input_declaration ;
  [reg_declaration] ;
  [initial_statement] ;
  
  table
    list_of_table_entries ;
  endtable
endprimitive
```

#### 3.6.2. UDP 说明

UDP 分为组合逻辑 UDP 和时序逻辑 UDP。

##### 端口声明

- 端口声明部分和 `module` 类似，可以在端口列表声明时只列出端口信号，然后在 `primitive` 实体中说明其类型，也可以直接在端口列表声明时就指明其类型；
- 输入端口只能采用标量（即 1 位），允许有多个输入端口；
- 输出端口只允许有一个标量（即 1 位），且输出端口必须出现在端口列表的第一个位置是，绝对不允许有多个输出端口；
- 输出端口用 `output` 关键字说明，时许逻辑 UDP 需要保存状态，则其输出端口还需要声明为 `reg` 类型；
- UDP 不支持 `inout` 端口类型。

##### 初始化

可以用 `initial` 语句对时序逻辑 UDP 的输出端口（`reg` 类型）进行初始化是，该语句是可选的。

##### 状态表

- UDP 状态表是 UDP 中最重要的部分，用关键字 `table` 声明，它定义了如何根据输入状态和当前状态得到输出值，类似于逻辑真值表；
- 状态表的项可以为 0，1，或 x，UDP 不能处理 z 值，所以传递给 UDP 的 z 值会被当做 x 处理。

### 3.7. 组合逻辑 UDP

#### 3.7.1. 与非门实例

组合逻辑 UDP 中，状态表规定了不同的输入组合和相对应的输出值，没有指定的任意组合输出值为 x 。

```verilog
primitive nand_my(
  output			out ;
  input 			a, b);
  
  table
  //a			b			:			out ;
    0			0			:			1 ;
    0 		1			:			1 ;
    1			0			:			1 ;
    1 		1			:			0 ;
  endtable
endprimitive
```

####  3.7.2. 状态表项

表示组合逻辑的状态表中的每一行的语法。

```verilog
<input1>		<input2>		...		<inputN> : <output> ;
```

- 状态表中的 `input` 信号顺序要与 UDP 端口列表的顺序一致；
- 输入和输出用冒号 `:` 隔开；
- 状态表的每一行以 `;` 结束；
- 能够产生确定输出值的所有输入项的组合都必须在状态表中列出，否则会输出 x 值。

#### 3.7.3. 无关项

不影响输出结果的输入信号为无关项，可以用 `?` 表示。状态表中的 `?` 项将自动展开为 0，1 或 x 。

#### 3.7.4. UDP 例化

UDP 调用格式与内置门级原语完全一致。

```verilog
nand_my			(G10, G30, G20) ;
```

### 3.8. 时序逻辑 UDP

时序逻辑 UDP 与组合逻辑 UDP 在定义形式和行为功能上均有不同。

- 时序逻辑 UDP 的输出端必须声明为 `reg` 型；

- 时序逻辑 UDP 是可以用 `initial` 语句初始化；

- 时序逻辑 UDP 状态表每行由 3 部分组成：输入部分、当前状态和输出状态，用 `:` 隔开；

  ```verilog
  <input_list> : <current_state> : <nect_state> ;
  ```

- `current_state` 就是输出寄存器的当前值的，`next_state` 就是输出寄存器的新值；`next_state` 由输入和 `current_state` 共同决定；

- 状态表的输入项可以是电平，也可以是跳变沿的形式。

#### 3.8.1. 电平触发 UDP

电平触发 UDP 的输出是根据输入电平状态的改变而改变。

#### 3.8.2. 边沿触发 UDP

边沿触发 UDP 的输出是根据输入跳边沿和输入电平状态的改变而改变。

```verilog
table
//RST			CP				D			:Q			:Q+
  // 时钟下降沿采样
  0				(10)			0			: ?			: 0 ;
  0 			(10)			1			: ?			: 1 ;
endtable
```

#### 3.8.3. UDP 状态表符号缩写

| 缩写符 | 含义              | 说明                 |
| :----- | ----------------- | -------------------- |
| `?`    | 0 1 x             | 只能用于输入         |
| `b`    | 0 1               | 只能用于输入         |
| `-`    | 保持原值不变      | 只能用于输出         |
| `(ab)` | 信号由 a 变 b     | 用于输入端边沿的指示 |
| `r`    | (01)              | 信号上升沿           |
| `f`    | (10)              | 信号下降沿           |
| `p`    | (01) (0x) 或 (x1) | 可能是信号的上升沿   |
| `n`    | (10) (1x) 或 (x0) | 可能是信号的下降沿   |
| `*`    | (??)              | 信号任意边沿的变化   |

#### 3.8.4. UDP 设计指导

针对数字设计时是选择使用 `module` 还是 `primitive` ，要从设计需求、复杂度等方面进行综合考虑。

- UDP 只能进行功能性建模，不能对电路时序和制造工艺（例如 CMOS，TTL 等）进行建模；使用 UDP 的主要目的是以类似于真值表的简介形式对数字设计进行建模，而 `module` 可以包含电路时序，并指定制造工艺；
- UDP 只能完成由一个输出端口的数字设计，当输出端口大于一个时，只能用 `module` ；
- UDP 是使用内存中的查找表实现的，当输入端口较多时，输入端口的组合将会呈指数增长，UDP 输入端口的数量也会受到仿真器的限制，因此输入端口较多时不宜使用 UDP ；
- 选择使用 UDP 以后，一定要尽可能的使用缩写符完整的描述 UDP 状态表；漏掉输入的组合情况，输出端可能会出现 x 的状态，造成设计错误。

### 3.9. 延迟模型

在实际电路设计时，必须检查设计中的延迟是否满足时序约束要求。可以用时序仿真的方法来检查时序（timing），即在仿真时向元件或路径中加入和实际相符的延迟信息，并进行相关计算来确定时序是否满足。

静态时序分析（Static Timing Analysis，STA），也是一种时序验证的技术。它不关心逻辑功能的正确与否，只对设计中的时序进行计算分析，来确定电路中是否存在违反（violation）时序约束的设计。STA 分析速度快，能够快速定位问题，但会忽略一些异步的问题。

STA + 时序仿真是一种相对完善且相对安全的时序验证方法。

#### 3.9.1. 分布延迟

分布延迟需要给电路每个独立的元件进行延迟定义，不同的路径有不同的延时。

```verilog
module and4(
	output			out,
  input				a, b, c, d);
  
  wire				an1 ,an2 ;
  and #1			(an1, a, b) ;
  and #2 			(an2, c, d) ;
  and #1.5		(out, an1 ,an2) ;
endmodule
```

也可以使用连续赋值语句 `assign` 说明分布延迟。

```verilog
module and4(
   output       out,
   input        a, b, c, d);

   wire         an1, an2 ;
   assign #1    an1 = a & b ;
   assign #2    an2 = c & d ;
   assign #1.5  out = an1 & an2 ;
endmodule
```

#### 3.9.2. 集总延迟

集总延迟是将全部路径累计的延时集中到最后一个门单元上。到最后一个门单元上的延迟会因路径的不同而不同，此时取最大延时作为最后一个门单元的延时。

```verilog
module and4(
	output			out,
  input				a, b, c, d);
  
  wire				an1 ,an2 ;
  and 				(an1, a, b) ;
  and 	 			(an2, c, d) ;
  and #3.5		(out, an1 ,an2) ;
endmodule
```

#### 3.9.3. 路径延迟

路径延迟是对每个输入引脚到每个输出引脚的所有路径指定延迟时间。路径延迟模型需要用关键字 `specify` 定义。

```verilog
specify
  (a => out) = 2.5 ;
  (b => out) = 2.5 ;
  (c => out) = 3.5 ;
  (d => out) = 3.5 ;
endspecify
```

#### 3.9.4. 延迟模型比较

- 分布延迟：分布延迟将延迟时间分散在了每一个门单元上，但仍然不能描述基本单元中不同引脚上延时的差异，当设计规模变大时，结构将变得复杂；
- 集总延迟：该方式模型简单，适用于小规模的电路，但是不同描述输入端到输出端不同路径的延迟；
- 路径延迟：指定了引脚到引脚的延迟，延迟信息比较齐全，虽然信息比较多，但对于大规模电路也更容易实现；因为设计者无需关心模块内部的实现逻辑，只需要了解输入到输出引脚的延迟即可；即便模块内部逻辑有所改变，路径延迟的说明也可以保持不变。

### 3.10. specify 块语句

#### 3.10.1. 并行连接

每条路径都有一个源引脚和目的引脚，将这些路径的延迟一次用 `specify` 语句描述出来，称为并行链接。

```verilog
(<source_io) => <destination_io>) = <delay_value> ;
```

可以用 `specparam` 在 `specify` 块中定义延迟数值常量，然后赋值给路径延迟。`specparam` 定义的常量只能在 `specify` 块内部使用。

```verilog
specparam name = value ;
```

#### 3.10.2. 全连接

在全连接中，源引脚中的每一位于目标引脚的每一位相连接。源引脚和目标引脚的连接是组合遍历的，且不要求位宽对应。

```verilog
(<multiple_source_io> *> <multiple_destination_io>) = <delay_value> ; 
```

#### 3.10.3. 边沿敏感路径

边沿敏感路径用于输入到输出延迟的时序建模，并使用边缘标识符指明触发条件。如果没有指明的话，任何变化都会触发源引脚到目的引脚的延迟值的变化。

```verilog
// 在 clk 上升沿触发，从 clk 上升沿至 out 上升沿，延迟为 1；从 clk 上升沿至 out 下降沿，延迟为 2
// 从 in 到 out 的数据路径是同向的，即 out = in
(posedge clk => (out +: in)) = (1, 2) ;
```

#### 3.10.4. 条件路径

Verilog 也允许模型中根据信号值的不同，有条件的给路径延迟进行不同的赋值。条件中的操作数可以是标量可以是向量，条件表达式也可以包含任意操作符。

```verilog
specify
  if (a)			(a => out) = 2.5 ;
  if (~a)			(a => out) = 1.5 ;
  
  if (b & c)			(b => out) = 2.5 ;
  if (!(b & c))		(b => out) = 1.5 ;
  
  if ({c, d} == 2'b01)
    					(c, d *> out) = 3.5 ;
  ifnone 			(c, d *> out) = 3 ;
endspecify
```

**注意**：

- 应当只使用 `if` 语句将条件路径中所有的输入状态都完整的声明；
- 没有声明的路径会使用分布延迟，分布延迟也没有声明的话，将使用零延迟；
- 如果路径延迟和分布延迟同时声明，将选择最大的延迟作为路径延迟；
- `specify` 中的 `if` 语句不能使用 `else` 结构，可以使用 `ifnone` 描述条件缺省时的路径延迟。

####  3.10.5. 门延迟路径

门延迟（上升延迟、下降延迟、关断延迟）的数值也可以通过路径延迟的方法来描述。可以定义的延迟路径个数为 1 个，2 个，3 个， 6 个，12 个，其他数量的延迟值都是错误的。

```verilog
// 1 param: rise, fall and shut use the same parameter
specify
  specparam t_delay = 1.5 ;
  (clk => q) = t_delay ;
endspecify

// 2 param: rise	(0 -> 1, z -> 1, 0 -> z)
//					fall	(1 -> 0, z -> 0, 1 -> z)
specify
  specparam t_rise = 1.5, t_fall = 2 ;
  (clk => q) = (t_rise, t_fall) ;
endspecify

// 3 param: rise	(0 -> 1, z -> 1)
//					fall	(1 -> 0, z -> 0)
specify
  specparam t_rise = 1.5, t_fall = 2.5, t_turnoff = 1.8 ;
  (clk => q) = (t_rise, t_fall, t_turnoff) ;
endspecify

// 6 param: 0 -> 1, 1 -> 0, 0 -> z, z -> 1, 1 -> z, z -> 0 respectively
specify
  specparam t_01 = 1.5, t_10 = 2, 	t_0z = 1.8 ;
  specparam t_z1 = 2,   t_1z = 2.2, t_z0 = 2.1 ;
  (clk => q) = (t_01, t_10, t_0z, t_z1, t_1z, t_z0) ;
endspecify

// 12 param: 0 -> 1, 1 -> 0, 0 -> z, z -> 1, 1 -> z, z -> 0
//					 0 -> x, x -> 1, 1 -> x, x -> 0, x -> z, z -> x repectively
specify
  specparam t_01 = 1.5, t_10 = 2, 	t_0z = 1.8 ;
  specparam t_z1 = 2,   t_1z = 2.2, t_z0 = 2.1 ;
  specparam t_0x = 1.1, t_x1 = 1.2, t_1x = 2.1 ;
  specparam t_x0 = 2,   t_xz = 2,   t_zx = 2.1 ;
  
  (clk => q) = (t_01, t_10, t_0z, t_z1, t_1z, t_z0, 
                t_0x, t_x1, t_1x, t_x0, t_xz, t_zx) ;
endspecify
```

门延迟路径模型中，也可以指定最大值、最小值和典型值。

```verilog
// rise, fall and turnoff's delay: min: typicla: max
specify
  specparam t_rise = 1:1.5:1.8 			;
  specparam t_fall = 1:1.8:2	 			;
  specparam t_turnoff = 1.1:1.2:1.3 ;
  (clk => q) = (t_rise, t_fall, t_turnoff) ;
endspecify
```

#### 3.10.6. x 传输延迟

如果没有指定 x 转换时间的延迟（门路径延迟中没有给出 12 个延迟参数），则规定：

- 从 x 转换为已知状态的延迟时间为，可能需要的最大延迟时间；
- 从已知状态转换为 x 的延迟时间为，可能需要的最小延迟时间。

### 3.11. 建立时间和保持时间

#### 3.11.1. 基本概念

建立时间是时钟触发事件来临之前，数据需要保持稳定的最小时间，以便数据能够被时钟正确的采样；保持时间是时钟触发事件来临之后，数据需要保持稳定的最小时间，以便数据能够被电路准确的传输。

#### 3.11.2. 约束条件

##### 建立时间约束条件

时钟到来之前，数据需要提前准备好，才能被时钟正确采样，要求数据路径（data path）比时钟路径（clock path）更快，即数据到达时间（data arrival time）小于数据要求时间（data required time）。

$$
T_{cq} + T_{comb} + T_{su} \le T_{clk} + T_{skew}
$$

- $T_{cq}$ ：寄存器 `clock` 端到 `Q` 端的延迟；
- $T_{comb}$ ：data path 中组合逻辑延迟；
- $T_{su}$ ：建立时间；
- $T_{clk}$ ：时钟周期；
- $T_{skew}$ ：时钟偏移。

理论上，电路能够承载的最小时钟周期为 $T_{cq} + T_{comb} + T_{su} - T_{skew}$ 。

##### 保持时间约束条件

时钟到来之后，数据还要稳定一段时间，这就要求前一级的数据延迟（data delay time）不要大于触发器的保持时间，以免数据被冲刷掉。
$$
T_{cq} + T_{comb} \ge Thd + T_{skew}
$$

- $T_{cq}$ ：寄存器 clock 端到 Q 端的延迟；
- $T_{comb}$ ：data path 中的组合逻辑延迟；
- $Thd$ ：保持时间；
- $T_{skew}$ ：时钟偏移。

### 3.12. 时序检查

指定路径延迟，目的是让仿真的时序更加接近实际数字电路的时序。利用时序约束对数字设计进行时序仿真，检查设计是否存违反（violation）时序约束的地方，并加以修改。Verilog 提供了一些系统任务，用于时序检查，这些任务只能在 `specify` 块中调用。

#### 3.12.1. $setup \$hold

系统任务 `$setup` 用来检查设计中元件的建立时间约束条件，`$hold` 用来检查保持时间约束条件。

```verilog
$setup(data_event, ref_event, setup_limit);
```

- `data_event` ：被检查的信号，判断它是否违反约定；
- `ref_event` ：用于检查的参考信号，一般为时钟信号的跳变沿；
- `setup_limit` ：设置的最小建立时间。

**注意**：如果 $T(ref\_event - data\_event) < setup\_limit$ ，则会打印存在 `violation` 的报告。

```verilog
$hold(ref_event, data_event, hold_limit);
```

- `data_event` ：被检查的信号，判断它是否违反约定；
- `ref_event` ：用于检查的参考信号，一般为时钟信号的跳变沿；
- `setup_limit` ：设置的最小保持时间。

**注意**：如果 $T(data\_event - ref\_event) < hold\_limit$ ，则会打印存在 `violation` 的报告。

Verilog 还提供了同时检查建立时间和保持时间的系统任务 `$setuphold (ref_event, data_event, setup_limit, hold_limit);`

#### 3.12.2. $recovery \$removal

建立时间和保持时间的概念都是出现在同步电路的设计中。对于异步复位的触发器来说，异步复位信号也需要满足 recovery time（恢复时间）和 removal time（去除时间），才能有效的复位和释放复位，防止出现亚稳态。

释放复位时，复位信号在时钟有效沿来临之前就需要提前一段时间恢复到非复位状态，这段时间为 recovery time 。类似于同步时钟下的触发器的 setup time 。

复位时，复位信号在时钟有效沿来临之后，还需要在一段时间内保持不变，这段时间为 removal time 。类似于同步时钟下触发器的 hold time 。

系统任务 `$recovery$` 与 `$removal$` 分别用于 recovery 和 removal time 的检查。

```verilog
$recovery (ref_event, data_event, recovery_limit) ;
```

- `ref_event` ：用于检查的参考信号，一般为清零或复位信号跳变沿；
- `data_event` ：被检查的信号，一般为时钟信号跳变沿；
- `recovery_limit` ：设置的最小 recovery time 。

**注意**：当 `ref_event(reset) < data_event(clock)` 且 `T(data_event - ref_event) < recovery_limit` 时，即复位信号在时钟信号到来之前，如果不满足 recovery time ，则报告中会打印 violation 。

```verilog
$removal (ref_event, data_event, removal_limit) ;
```

- `ref_event` ：用于检查的参考信号，一般为清零或复位信号跳变沿；
- `data_event` ：被检查的信号，一般为时钟信号跳变沿；
- `removal_limit` ：设置的最小 removal time 。

**注意**：当 `ref_event(reset) < data_event(clock)` 且 `T(data_event - ref_event) > removal_limit` 时，即复位信号在时钟信号到来之前，如果不满足 removal time ，则报告中会打印 violation 。

Verilog 还提供了同时检查 removal 和 recovery 的系统任务。

```verilog
$recrem (ref_event, data_event, recovery_limit, removal_limit) ;
```

#### 3.12.3. $width \$period

有些数字设计，例如 flash 存储器，还需要对脉冲宽度或周期进行检查，为此 Verilog 分别提供了系统任务 `$width` 和 `$period` 。

```verilog
$width(ref_event, time_limit) ;
```

- `ref_event` ：边沿触发事件；
- `time_limit` ：脉冲的最小宽度。

如果两次相反跳变沿之间的时间小于 time_limit ，则会报告 violation 。

```verilog
$period(ref_event, time_limit) ;
```

如果两次同样跳变沿之间的时间小于 time_limit ，则会报告 violation 。

### 3.13. 延迟反标注

延迟反标注是设计者根据单元库工艺、门级网表、版图中的电容电阻等信息，借助数字设计工具将延迟信息标注到门级网表中的过程。利用延迟反标注后的网表，就可以进行精确的时序仿真，使仿真更接近实际工作的数字电路。

#### 3.13.1. 过程

1. 利用硬件描述语言完成 RTL 层级的描述，进行功能仿真；
2. 对时钟、复位、输出端口等信号进行一定的时序约束，并用于逻辑综合；
3. 去除综合出的门级网表所包含的延迟信息，并初步验证 setup 等时序是否满足要求；
4. 对门级网表进行布局布线，转换为版图级网表，并根据元器件几何形状和制造工艺等计算版图延迟值；
5. 将布局布线后版图中的延迟信息反标注至版图级网表，并验证时序是否满足；
6. 验证通过，则可以进行下载或实现，如果有 violation ，首先需要检查时序约束设置，再重新布局布线验证，如果还是无法消除，则需要回到设计初始，优化 RTL 的描述。

#### 3.13.2. SDF 文件

SDF（Standard Delay Format），标准延时格式文件，常用延迟反标注。该文件包含了仿真用到的所有 IOPATH、INTERCONNECTION、TIMING CHECK 等延迟时间和时序约束的参数。

##### 文件格式

SDF 文件用关键字 DELAYFILE 声明，并包含 DESIGN、DATE 等关键字信息。延迟时间和时序约束参数均在 CELL 中说明。SDF 文件就是有文件声明信息和很多个不同的 CELL 组成的。

```verilog
(DELAYFILE
  (DESIGN "top")
  (DATE "...")
...
  (TIMESCALE 1ns)
  (CELL
  ...
  )
  (CELL
  ...
  )
...
)
```

##### 延迟类型

SDF 文件中的延迟类型包括 cell delay 和 wire delay 。cell delay 指逻辑门单元器件内部的延迟，wire delay 是指器件之间通过 wire 互联的延迟。

###### cell delay

用于定义输入、输出端口之间的上升延迟和下降延迟。

```verilog
(CELL
  (CELLTYPE "module_name")
  (INSTANCE instance_name)
  (DELAY
    (ABSOLUTE
      (IOPATH A Z (1.5::1.8) (1.3::1.7))
      (IOPATH B Z (1.5::1.8) (1.3::1.7))
    )
  )
)
```

###### wire delay

用于定义不同模块之间的走线延迟。

```verilog
(CELL
  (CELLTYPE "module_name")
  (INSTANCE instance_name)			// can be omitted if here is top module
  (DELAY
    (ABSOLUTE
      (INTERCONNECT u_and.Z u_dt.D (0.500::0.751) (0.400::0.551))
      // (INTERCONNECT u_and/Z u_dt/D (0.500::0.751) (0.400::0.551))
      // Hierarchical access symbol: some support / , other suport .
    )
  )
)
```

##### 条件延迟及时序检查

CELL 中还可以用关键字 COND 指定条件延迟。同时，也可以再 CELL 内做时序检查。

```verilog
(CELL
  (CELLTYPE "d_gate")
  (INSTANCE u_dt)
  (DELAY
    (ABSOLUTE
    // when D is 1, positive delay is  1.3, negative delay is 1.5
    (COND D==1'b1 (IOPATH CP Q (1.3::2.3) (1.5::2.2)))
    // when D is 0, positive delay is  1.2, negative delay is 1.4
    // Here is only 
    // This is just to illustrate COND usage，D=1时下降延迟参数不可能用到
    // the negative delay for D is 1 is impossible
    (COND D==1'b0 (IOPATH CP Q (1.2::2.1) (1.4::2.0)))
    )
  )
  //setup check, when D-CP time is less than 0.8 or 1, print violation
  (TIMINGCHECK
  (SETUP D (posedge CP) (0.8::1)) 
  )
)
```

#### 3.13.3. 使用方法

Verilog 提供了系统函数 `$sdf_annotate` 去调用SDF 文件完成延迟反标注的过程。

```verilog
$sdf_annotate ('sdf_file'[, module_instance] [, 'sdf_configfile'] [, 'sdf_logfile'] [, 'mtm_spec'] [, 'scale_factors'] [, 'scale_type']) ;
```

- `sdf_file` ：SDF 文件名字，包含路径信息；
- `module_instance` ：例化的设计模块名字，一般为 testbench 中所例化的数字设计模块名称，注意和 SDF 文件内容中的声明保持层次的一致；
- `log_file` ：编译时关于 SDF 的日志；
- `mtm_spec` ：指定使用的延迟类型，选项包括 `MAXIMUM` 、`MINIMUM` 、`TYPICAL` ，分别表示使用 SDF 文件中标注的最大值、最小值或典型值。