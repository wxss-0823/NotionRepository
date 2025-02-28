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

```asp
%.o: %.c
	$(CC) -c
```



## GCC 常用指令