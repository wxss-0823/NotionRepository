# Makefile 教程

​	Makefile 是用于管理项目构建过程的工具，广泛用于 C/C++ 等语言的编译。它通过定义规则和指令，自动化编译、链接等步骤，大大简化了开发者的工作。

## 1. Makefile 基本概念

​	Makefile 是 `make` 命令所读取的配置文件，以 MinGW 为例，当执行 `make` 命令时，会调用 `mingw-make.exe` 可执行文件，并自动在当前目录下寻找 Makefile 文件，执行其中定义的 gcc 指令集，从而避免手动输入每一条 gcc 编译指令。

​	Makefile 中包含了构建项目的规则，主要作用是检查项目文件的依赖关系，自动执行必要的命令，从而更新目标文件。一般来说，Makefile 主要包括以下三部分内容：

- **目标（Target）**：需要生成的文件；
- **依赖（Dependencies）**：生成目标所依赖的文件或目标；
- **命令（Commands）**：构建目标时需要执行的命令。

## 2. Makefile 基本语法

```makefile
target: dependencies
	command
```

- `target`：目标文件，可以是一个目标文件或一个动作名称；
- `dependencies`：生成目标所依赖的文件或其他目标；
- `command`：构建目标的命令，必须以 `Tab` 开头。

## 3. Makefile 工作原理

​	`make` 会根据 Makefile 中的规则，依次检查目标文件的时间戳和依赖文件的时间戳。如果依赖文件的时间戳比目标文件新，或者目标文件不存在，`make` 就会执行对应的命令来更新目标文件。`make` 会递归检查依赖关系，直到所有目标都更新完成。

## 4. Makefile 变量

​	Makefile 支持定义变量，可以简化重复的命令。

```makefile
VARIABLE_NAME = value
```

​	在引用变量式使用 `$(VARIABLE_NAME)` 。

### 4.1. 常用的内置变量

- `$@` ：表示目标文件；
- `$^` ：表示所有依赖文件；
- `$<` ：表示第一个依赖文件。

## 5. Makefile 伪目标

​	伪目标（Phony targets）并不是文件，而不是一种命令名称，可以用于执行一些常见的操作。

```makefile
.PHONY: clean
clean:
	rm -f *.o main
```

## 6. Makefile 模式匹配

​	当所要编译的文件过多时，使用模式匹配能够简化操作。

```makefile
%.o: %.c
	$(CC) -c $< -o $@
```

- `%.o: %.c` ：一个通用规则，表示将任意 `.c` 文件编译为对应的 `.o` 文件，`%` 是一个通配符。

## 7. Makefile 函数

### 7.1. 获取指定文件

​	`$(wildcard PATTERN)` 可以用于获取指定目录下的指定类型的文件列表。

- `PATTERN`：某个或多个目录下的对应的某种类型的文件，多个目录采用空格分隔，缺省则默认为当前目录；
- `return`：若干个目标文件的文件列表，文件名之间使用空格间隔

### 7.2. 替换文件名

​	`$(patsubst <pattern>, <replacement>, <text>)` 可以用于替换指定范围内的符合格式的文件名至目标格式。

- `pattern`：表示需要被替换的文件格式；
- `replacement`：表示目标文件格式；
- `text`：表示替换范围。

### 7.3. 执行 shell 命令

​	`$(shell <command>)` 可以用于执行 shell 命令。

- `command`：符合 shell 语法的命令。

**注意**：可以使用 shell 命令，获取子目录，进而实现 Makefile 文件的递归调用。

### 7.4. 传递变量

​	有些复杂的项目可能涉及多层 Makefile 的嵌套，顶层 Makefile 需要递归调用子层的 Makefile，重复的变量可以通过 `export` 关键字导出，使其在全部 Makefile 文件中可用。

## 8. GCC 常用指令

### 8.1. 简介

​	GCC（GNU Compiler Collection）是一个开源的编译器集合，支持多种编程语言。

### 8.2. 基本命令

#### 8.2.1. 预处理

​	使用 `-E` 修饰符，处理源代码中的宏定义和头文件包含指令，生成 `.i` 后缀的文件。

```shell
gcc -E test.c -o test.i
```

#### 8.2.2. 编译

​	使用 `-S` 修饰符，预处理后的代码被编译成汇编语言，生成 `.s` 后缀的文件。

```shell
gcc -S test.i -o test.s
```

#### 8.2.3. 汇编

​	使用 `-c` 修饰符，汇编器将汇编代码转换为机器代码，生成 `.o` 后缀的目标文件。

```shell
gcc -c test.s -o test.o
```

#### 8.2.4. 链接

​	不使用修饰符，链接器将一个或多个目标文件与库文件链接成最终的可执行文件。

```shell
gcc test.o -o test
```

### 8.3. 链接库文件

​	在开发中，经常需要链接到第三方库。GCC 允许使用 `-L` 修饰符，指定库文件的路径，使用 `-l` 修饰符，指定需要链接库。

```shell
gcc -L /usr/dev/mysql/lib -lmysqlclient test.o -o test
```

### 8.4. 其他常用选项

- `-o` ：指定输出文件名称；
- `-I` ：添加头文件的搜索路径；
- `-D` ：定义宏；
- `-g` ：生成调试信息；
- `-Wall` ：开启所有编译警告；
- `-fPIC` ：生成位置无关的代码，适用于共享库。