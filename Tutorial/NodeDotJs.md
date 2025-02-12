# NodeDotJs 教程

## 1. 创建应用

​	在传统的 PHP 开发中，需要一个像 Apache 或 Nginx 的 HTTP 服务器，并且需要配置 `mod_php` 或 `php-cgi` 来处理 PHP 脚本，从而生成动态内容，也就是说 PHP 依赖于外部的 HTTP 服务器来接收请求并提供 Web 页面。

​	Node.js 本身就内置了一个 HTTP 服务器模块，这意味着在使用 Node.js 开发时，开发者可以直接使用 Node.js 的 HTTP 模块来创建服务器，处理 HTTP 请求，并生成 Web 页面，而不需要依赖外部的 HTTP 服务器软件。

## 2. NPM 使用介绍

​	NPM（Node Package Manager）是一个 JavaScript 包管理工具，也是 Node.js 的默认包管理器，其允许开发者轻松地下载、安装、共享、管理项目的依赖库和工具。

### 2.1. 版本检查

​	新版的 Node.js 集成了 NPM，可以直接输入 `npm -v` 查看当前版本。如果安装的是旧版本，可以通过 `npm install npm -g` 升级。

### 2.2. 安装模块

```shell
npm install <Module Name>
```

#### 2.2.1. 安装模式

​	NPM 的包安装分为本地安装和全局安装两种，从命令行看，两者只相差 `-g` 参数。

##### 本地安装

- **作用范围**：默认情况下，npm 会将包安装在当前项目的 `node_modules` 文件夹中，这意味着每个使用该包的项目都会有自己的包副本；
- **用途**：用于项目依赖，每个项目可以有自己的依赖版本，有助于确保项目的稳定性和可复现性；
- **安装命令**：在项目目录中运行 `npm install <package-name>` ，会将包安装在 `node_modules` 文件夹中，并在 `package.json` 中添加依赖；
- **版本管理**：通过 `package.json` 和 `package-lock.json` 文件管理依赖的版本，确保项目在不同环境中的一致性。

##### 全局安装

- **作用范围**：全局安装会将包安装在系统级别的目录中，通常是 `/usr/local/bin` 或 `%AppData%\npm` 上；
- **用途**：全局安装用于那些不需要再每个项目中重复安装的工具或命令行实用程序；
- **安装命令**：使用 `-g` 标志来全局安装包；
- **版本管理**：全局安装的包版本有 npm 管理，但不会在项目 `package.json` 中体现，这意味着全局安装的包可能在不同项目之间共享，但也可能因为版本冲突而导致问题。

#### 2.2.2. 查看安装信息

```shell
npm list -g
```

#### 2.2.3. 卸载模块

```shell
npm uninstall express
```

​	可以到 `node_modules` 目录下查看包是否还存在，或者使用如下命令：

```shell
npm ls
```

#### 2.2.4. 更新模块

```shell
npm update express
```

### 2.3. 配置文件说明

​	`package.json` 是 Node.js 项目中的一个核心文件，包含了项目的元数据、依赖、脚本等信息。用于描述项目的元数据和依赖关系，通常位于项目的根目录，并且是项目的配置文件。

- `name`：项目的名称，应该是唯一的，通常使用小写字母和连字符；
- `version`：项目的版本号，遵循语义化版本控制（Semantic Versioning）；
- `description`：项目的简短描述；
- `main`：项目的入口文件，通常是应用程序的启动文件；
- `scripts`：定义了一系列的命令行脚本，可以在项目中执行特定的任务；
- `dependencies`：列出了项目运行所需的所有依赖包及其版本；
- `devDependencies`：列出了只在开发过程中需要的依赖包及其版本；
- `peerDependencies`：列出了项目期望其依赖包也依赖的包；
- `optionalDependencies`：列出了可选的依赖包；
- `engines`：指定了项目兼容的 Node.js 版本；
- `repository`：项目的代码仓库信息，如 GitHub 仓库的 URL；
- `keywords`：项目的关键词，有助于在 npm 搜索中找到项目；
- `author`：项目的作者信息；
- `license`：项目的许可证信息。

#### 2.3.1. 使用方法

1. **初始化项目**：在项目目录中运行 `npm init` 命令，npm 会引导创建一个 `package.json` 文件，或者自动生成一个包含默认值的 `package.json` ；
2. **安装依赖**：使用 `npm install <package-name>` 命令安装依赖，npm 会自动将依赖添加到 `package.json` 文件的 `dependencies` 或 `devDependencies` 中，并创建 `package-lock.json` 文件以锁定依赖的版本；
3. **管理脚本**：使用 `scripts` 字段定义命令，例如：`"start": "node app.js"` ，可以通过 `npm start` 命令来运行脚本；
4. **版本控制**：当项目准备好发布到 npm 时，可以使用 `npm publish` 命令，npm 会读取 `package.json` 中的信息来发布包；
5. **发布包**：当项目准备好发布到 npm 时，可以使用 `npm publish` 命令，npm 会读取 `package.json` 中的信息来发布包；
6. **依赖管理**：`package.json` 和 `package-lock.json` 文件一起工作，确保项目在不同环境中的依赖版本一致。

## 3. REPL

​	Node.js 提供了一个内置的 REPL （Read-Eval-Print Loop），这是一个交互式编程环境，可以在终端中运行 JavaScript 代码。

- **Read**：读取用户输入，解析输入的 JavaScript 数据结构并存储在内存中；
- **Eval**：执行输入的数据结构；
- **Print**：输出结果；
- **Loop**：循环操作以上步骤直到用户两次按下 `ctrl + c` 退出。

### 3.1. 启动终端

```shell
node
```

### 3.2. 语法

​	Node 终端中支持简单的表达式运算、变量、多行表达式等。

#### 3.2.1. 表达式运算

```shell
> 1 + 4
```

#### 3.2.2. 变量

​	可以将数据存储在变量中，并在需要的时候使用它。变量声明需要 `var` 关键字，如果没有使用，会直接打印出来。

```shell
> x = 10
> var y = 10
> x + y
```

#### 3.2.3. 多行表达式

​	Node REPL 支持多行表达式，会在回车换行后，自动检测是否为连续的表达式。

#### 3.2.3. 下划线变量

​	可以使用下划线 `_` 获取上一个表达式的运算结果。

```shell
> x + y
> var sum = _
```

## 4. 回调函数

​	Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境，使得 JavaScript 可以脱离浏览器运行在服务器端。其核心特性之一是非阻塞 I/O 模型，非常适合处理高并发网络应用。

### 4.1. 非阻塞代码

​	回调函数，即该函数会在程序块执行结束后，返回一些操作，而程序块运行时，其他程序块可以同时进行，不被阻塞。

### 4.2. 回调地狱

​	当多个异步操作需要按顺序执行时，回调函数会导致代码嵌套，使得代码难以阅读和维护。为了改善代码的可读性和可维护性，可以使用以下几种方法：

- **Promises**：一种新的异步编程模式，允许以链式的方式处理异步操作，避免了回调地狱；
- **async/await**：基于 Promises，提供了一种更接近同步代码风格的异步编程语法糖，使得异步代码更易于理解和维护；
- **事件驱动编程**：Node.js 支持事件驱动编程，通过监听和触发事件来处理异步操作。

#### 4.2.1. async/await

​	async/await 是 ES2017 引入的语法糖，可以更方便地处理异步操作，避免回调地狱。

```javascript
const fs = require('fs').promises;

async function readFiles() {
  try {
    const data1 = await fs.readFile('file1.txt', 'utf8');
    const data2 = await fs.readFile('file2.txt', 'utf8');
    const data3 = await fs.readFile('file3.txt', 'utf8');
    
    console.log('Data from all files: ', data1, data2, data3);
  } catch (err) {
    console.error('Error reading files: ', err);
  }
}

readFiles();
```

#### 4.2.2. then

​	Promises 是另一种处理异步操作的方式，可以链式调用 then 方法，避免嵌套回调。

```javascript
const fs = require('fs').promises;

fs.readFiles('file1.txt', 'utf8')
	.then(data1 => {
  	console.log('Data from file1: ', data1);
  	return fs.readFile('file2.txt', 'utf8');
	})
	.then(data2 => {
  	console.log('Data from file2: ', data2);
  	return fs.readFile('file3.txt', 'utf8');
	})
	.then(data3 => {
  	console.log('Data from file3: ', data3);
  })
	.catch(err => {
  	console.error('Error reading files: ', err);
	});
```

## 5. 事件循环

​	事件循环是 Node.js 处理非阻塞 I/O 操作的核心机制，使得单线程能够高效处理多个并发请求。

### 5.1. 事件循环的阶段

​	事件循环分为多个阶段，每个阶段处理特定的任务。

- **Times**：执行 `setTimeout()` 和 `setInterval()` 的回调；
- **I/O Callbacks**：处理一些延迟的 I/O 回调；
- **ldle prepare**：内部使用，不常见；
- **Poll**：检索新的 I/O 事件，执行与 I/O 相关的回调；
- **Check**：执行 `setImmediate()` 回调；
- **Close Callbacks**：处理关闭的回调。

### 5.2. 事件循环的流程

- 任务进入事件循环队列；
- 事件循环按照阶段顺序进行处理，每个阶段有自己的回调队列；
- 事件循环会在 poll 阶段等待新的事件到达，如果没有事件，会检查其他阶段的回调；
- 如果 `setImmdiate()` 和 `setTimeout()` 都存在，`setImmediate()` 在 check 阶段先执行，而 `setTimeout()` 在 times 阶段执行。

### 5.3. 宏任务与微任务

- **宏任务**：`setImmdiate` 、`setInterval` 、`setImmediate` 、I/O 操作等；
- **微任务**：`process.nextTick` ，`Promise.then` 。

**执行顺序**：微任务优先级高于宏任务，会在当前阶段的回调结束后立即执行。

### 5.4. 事件驱动程序

​	在 Node.js 中，事件驱动编程主要通过 EventEmitter 类来实现，通过继承其可以创建自己的事件发射器，并注册和触发事件。

#### 5.4.1. 基本概念

- **事件**：在程序中发生的动作或状态改变；
- **事件触发器**：EventEmitter 是 Node.js 的内置模块，用来发出和监听事件；
- **事件处理器**：与事件关联的回调函数，事件发生时被调用。

#### 5.4.2. 事件驱动流程

- **注册事件**：在程序中通过 EventEmitter 实例注册事件和对应的处理器；
- **触发事件**：当指定事件发生时，EventEmitter 会触发该事件；
- **处理事件**：事件循环会调度相应的回调函数来执行任务。

## 6. EventEmitter

​	Node.js 所有的异步 I/O 操作在完成时都会发送一个事件到事件队列。

### 6.1. EventEmitter 类

​	events 模块只提供了一个对象：`event.EventEmitter` 。其核心就是事件触发与事件监听器功能的封装。

​	EventEmitter 对象如果在实例化时发生错误，会触发 error 事件；当添加新的监听器时，`newListener` 事件会触发，当监听器被移除时，`removeListener` 事件被触发。

### 6.2. error 事件

​	EventEmitter 定义了一个特殊的事件 error，它包含了错误的语义，在遇到异常的时候通常会触发 error 事件。当 error 被触发时，EventEmitter 规定如果没有响应的监听器，Node.js 会把它当作异常，退出程序并输出错误信息。

```javascript
var events = require('events');
var emitter = new events.EventEmitter();
emitter.emit('error');
```

### 6.3. 继承 EventEmitter

​	大多数时候，不会直接使用 EventEmitter，而是在对象中继承它，包括 `fs`、`net`、`http` 在内的，只要是支持事件响应的核心模块都是 EventEmitter 的子类。

```javascript
class MyEmitter extends EventEmitter {}
```

## 7. Buffer

​	JavaScript 语言自身只有字符串数据类型，没有二进制数据类型。Node.js 中的 Buffer 类是用于处理二进制数据的核心工具，提供了对二进制数据的高效操作。

- **二进制数据**：Buffer 对象是一个包含原始二进制数据的固定大小的数组。每个元素占用一个字节；
- **不可变性**：虽然 Buffer 对象的内容可以在创建后修改，但其长度是固定的，不能动态改变。

### 7.1. Buffer 与字符编码

​	Buffer 实例一般用于表示编码字符的序列，通过显式的字符编码，就可以在 Buffer 实例与普通的 JavaScript 字符串之间进行相互转换。

### 7.2. 创建 Buffer 类

​	Buffer 提供了以下的 API 来创建 Buffer 类：

- `Buffer.alloc(size[, fill[, encoding]])`：创建了一个长度为 size 字节的 Buffer。
- `Buffer.allocUnsafe(size)`：创建了一个长度为 size 字节的 Buffer，但 Buffer 中可能存在旧的数据，可能影响执行结果，所以叫 Unsafe；
- `Buffer.allocUnsafeSlow(size)`：用于分配给定大小 size 的新 Buffer 实例，但不对其进行初始化；
- `Buffer.from(array)`：返回一个被 array 的值初始化的新的 Buffer 实例（传入的 array 元素只能是数字，不然就会自动被 0 覆盖）；
- `Buffer.from(arrayBuffer[, byteOffset[, [length]])`：返回一个新建的与给定的 ArrayBuffer 共享同一内存的 Buffer；
- `Buffer.from(buffer)`：复制传入的 Buffer 实例的数据，并返回一个新的 Buffer 实例；
- `Buffer.from(string[, encoding])`：通过字符串创建 Buffer，可以指定编码，默认为 UTF-8 。

### 7.3. 写入缓冲区

```javascript
buf.write(string[, offset[, length]][, encoding])
```

- `string`：写入缓冲区的字符串；
- `offset`：缓冲区开始写入的索引值，默认为 0；
- `length`：写入的字节数，默认为 `buffer.length`；
- `encoding`：使用的编码，默认为 UTF-8 。

#### 7.3.1. 返回值

​	返回实际写入的大小，如果 Buffer 空间不足，则只会写入部分字符串。

### 7.4. 从缓冲区读取数据

```javascript
buf.toString([encoding[, start[, end]]])
```

- `encoding`：使用的编码，默认为 UTF-8；
- `start`：指定开始读取的索引位置，默认为 0；
- `end`：结束位置，默认为缓冲区的末尾。

#### 7.4.1. 返回值

​	解码缓冲区数据并使用指定的编码返回字符串。

### 7.5. 转换为 JSON 对象

​	当字符串化一个 Buffer 实例时，`JSON.stringify()` 会隐式的调用 `toJSON()` 。

```javascript
buf.toJSON()
```

####  7.5.1. 返回值

​	返回 JSON 对象。

### 7.6. 缓冲区合并

```javascript
Buffer.concat(list[, totalLength])
```

- `list`：用于合并的 Buffer 对象数组列表；
- `totalLength` 指定合并后 Buffer 对象的总长度。

#### 7.6.1. 返回值

​	返回一个由多个成员合并的新 Buffer 对象。

### 7.7. 缓冲区比较

```javascript
buf.compare(otherBuffer);
```

- `otherBuffer`：与 buf 对象比较的另外一个 Buffer 对象。

#### 7.7.1. 返回值

​	返回一个数字，表示 buf 在 otherBuffer 之前（<0）、之后（>0）或相同（=0）。

### 7.8. 拷贝缓冲区

```javascript
buf.copy(targetBuffer[, targetStart[, sourceSrart[, sourceEnd]]])
```

- `targetBuffer`：要拷贝的 Buffer 对象；
- `targetStart`：数字，可选，默认为 0；
- `sourceStart`：数字，可选，默认为 0；
- `sourceEnd`：数字，可选，默认为 0 。

#### 7.8.1. 返回值

​	没有返回值。

### 7.9. 缓冲区裁剪

```javascript
buf.slice([start[, end]])
```

- `start`：数字，可选，默认为 0；
- `end`：数字，可选，默认为 0 。

#### 7.9.1. 返回值

​	返回一个新的缓冲区，它和就缓冲区指向同一块内存，但是从索引 `start` 开始，`end` 结束。

### 7.10. 缓冲区长度

```javascript
buf.length;
```

#### 7.10.1. 返回值

​	返回 Buffer 对象所占据的内存长度。

## 8. Stream

​	Node.js 的 Stream 是一种处理流式数据的抽象接口，广泛应用于文件操作、网络通信等场景。流式数据处理的一个主要优点是可以在数据传输过程中就开始处理数据，而不需要等待整个数据加载完毕，这使得 Node.js 能够高效地处理大量数据，而不用占用过多的内存。

​	Stream 是一个抽象接口，Node 中有很多对象实现了这个接口。它允许以流的形式处理数据，而不是一次性将数据全部加载到内存中。这对于处理大量数据或者实现高效的数据传输非常有用。

### 8.1. 读取数据

​	常见的可读流包括文件读取流和网络请求响应流。

```javascript
let readableStream = fs.createReadStream('filename');
```

### 8.2. 写入流

​	可写流用于将数据写入目的地，常见的可写流包括文件写入流和网络请求发送流。

```javascript
let writableStream = fs.createWriteStream('filename');
```

### 8.3. 双工流

​	双工流（Duplex）同时具有可读和可写的能力。

```javascript
const server = net.createServer(...);
```

### 8.4. 转换流

​	转换流是一种特殊的双工流，可以修改或转换数据。常见的转换流包括压缩和解压缩流。

```javascript
const gzip = zlib.createGzip();
```

### 8.5. 管道流

​	管道提供了一个输出流到输入流的机制。通常用于从一个流中获取数据并将数据传递到另外一个流中。

```javascript
readableStream.pipe(gzip);
```

### 8.6. 链式流

​	链式是通过连接输出流到另外一个流并创建多个流操作链的机制。链式流一般用于管道操作。

```javascript
readableStream.pipe(gzip).pipe(writableStream);
```

### 8.7. 暂停和恢复

​	可读流可以暂定和恢复数据的读取。

```javascript
readableStream.pause();
readableStream.resume();
```

### 8.8. 销毁

​	可以销毁流，释放资源。

```javascript
readableStream.destory();
```

## 9. 模块系统

​	Node.js 模块系统是其核心功能之一，它允许开发者将代码组织成小的、可重用的单元，这些单元被称为模块。模块是一个封装了特定功能的独立文件，可以在其他文件中引入和使用。模块系统遵循 CommonJS 规范，但也支持 ES 模块。

### 9.1. 导入内置模块

​	内置模块是由 Node.js 自带的模块，无需额外安装。

```javascript
const fs = require('fs');
```

### 9.2. 导入第三方模块

​	第三方模块是开发者或开源社区发布的模块，可以通过 npm 安装到项目中。

```javascript
const express = require('express');
```

### 9.3. 自定义模块导出与导入

#### 9.3.1. 导入模块

​	在 Node.js 中，引入一个模块非常简单。

```javascript
let hello = require('./hello');
```

​	以上代码，引入了当前目录下的 `hello.js` 文件。

#### 9.3.2. 导出模块

​	Node.js 提供了 `exports` 和 `require` 两个像，其中 `exports` 是模块公开的接口。

```javascript
exports.world = function () {
  console.log('Hello World');
}
```

​	以上代码，通过 `exports` 对象把 world 作为模块的访问接口，导入模块后，可以直接访问 `exports` 的成员函数。

​	有时候，需要把一个对象封装到模块中，而不仅仅是一个函数。

```javascript
module.exports = function {
  ...
}
```

#### 9.3.3. ES 模块

​	ES 模块使用 `import` 和 `export`，是现代的 JavaScript 的模块规范。

- ES 模块使用 `import` 和 `export` 关键字，需将文件扩展名设置为 `.mjs` ，或者在 `package.json` 中声明 `"type": "module"` ；
- ES 模块支持静态导入（`import ... from ...`）和动态导入 `import()` 。

#### 9.3.4. 模块缓存

​	Node.js 会将已加载的模块缓存起来，以提高性能。再次 `require()` 同一模块时，直接返回缓存中的模块，而不是重新加载。要重新加载缓存可以删除缓存。

```javascript
delete require.cache[require.resolve('filepath')];
```

#### 9.3.5. 循环依赖

​	当两个或多个模块相互导入时，称为循环依赖。Node.js 能够处理简单的循环依赖，但可能导致部分模块导出的对象未完全初始化。

#### 9.3.6. 模块包装与作用域

​	Node.js 会将每个模块包装在一个函数中，使得每个模块都有独立的作用域。这意味着在模块内定义的变量不会污染全局变量。

#### 9.3.7. 服务端模块导入策略

##### 从文件模块缓存中加载

​	尽管原生模块与文件模块的优先级不同，但是都会优先从文件模块的缓存中加载已经存在的模块。

##### 从原生模块加载

​	原生模块的优先级仅次于文件模块缓存的优先级。`require` 方法在解析文件名之后，优先检查模块是否在原生模块列表中。

​	原生模块也有一个缓存区，同样也是优先从缓存区加载。如果缓存区没有被加载过，则调用原生模块的加载方式进行加载和执行。

##### 从文件加载

​	当文件模块缓存中不存在，而且不是原生模块的时候，Node.js 会解析 `require` 方法传入的参数，并从文件系统中加载实际的文件。

## 10. 函数

​	在 Node.js 中，函数是 JavaScript 的核心组成部分之一，用于封装和执行特定任务。

### 10.1. 函数声明

​	使用 `function` 关键字声明一个函数。

```javascript
function func_name(para_list) {
  // func body
}
```

### 10.2. 函数表达式

```javascript
const variable = fucntion(para_list) {
  // func body
}
```

### 10.3. 箭头函数

​	ES6 引入的简洁的函数表达式。

```javascript
const variable = (para_list) => {
  // func body
}
```

### 10.4. 函数类型

#### 10.4.1. 普通函数

​	最常见的函数类型，有函数名、参数和返回值。

#### 10.4.2. 匿名函数

​	没有名字的函数，通常作为参数传递给其他函数。

```javascript
func1(function(para_list) {
  // func body
}, para_list);
```

#### 10.4.3. 回调函数

​	作为参数传递给另一个函数，并在某个操作完成后被调用。

```javascript
function fetchData(callback) {
  setTime(() => {
    const data = 'Some data';
    callback(data);
  });
}

fetchData((data) => {
  console.log(data);
})
```

#### 10.4.4. 异步函数

​	使用 `async` 和 `await` 关键字处理异步操作。

### 10.5. 高级用法

#### 10.5.1. 闭包

​	闭包指一个函数能够记住并访问其词法作用域，即使这个函数在其词法作用域之外执行。

```javascript
function createCounter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}

const counter = createCounter();
console.log(counter());
console.log(counter());
```

#### 10.5.2. 高阶函数

​	接受函数作为参数或返回函数的函数。

#### 10.5.3. 默认参数

​	在函数声明时，为参数提供默认值。

```javascript
function funcname(para1 = defaultVar) {
  // func body
}
```

#### 10.5.4. 剩余参数

​	允许将不定数量的参数表示为一个数组。

```javascript
function funcname(...para_list) {
  // func body
}
```

#### 10.5.5. 解构参数

​	从对象或数组中提取数据并将其赋值给变量。

```javascript
function getUserInfo({name, age}) {
  console.log(`Name: ${name}, Age: ${age}`);
}

const user = {name: "wxss", age: 23};
getUserInfo(user);
```

## 11. 全局变量

​	JavaScript 中有一个特殊的对象，称为全局对象（Global Object），它及其所有属性都可以在程序的任何地方访问，即全局变量。

### 11.1. 全局对象与全局变量

​	`global` 最根本的作用是作为全局变量的宿主。按照 ECMAScript 的定义，满足以下条件的变量是全局变量。

​	当定义一个全局变量时，这个变量同时也会成为全局对象的属性。需要注意的是，在 Node.js 中，不可能在最外层定义变量，因为所有用户代码都是属于当前模块的，而模块本身不是最外层上下文。

**注意**：最好不要使用 `var` 定义变量，以避免引入全局变量，因为全局变量会污染命名空间，提高代码的耦合风险。

### 11.2. __filename

​	表示当前正在执行的脚本的文件名。它将输出文件所在位置的绝对路径，且和命令行参数所指定的文件名不一定相同。如果在模块中，返回值是模块文件的路径。

### 11.3. __dirname

​	表示当前正在执行的脚本所在的目录。

### 11.4. setTimeout(cb, ms)

​	全局函数在指定的毫秒（ms）后执行指定函数（cb）。只执行一次指定函数，返回一个代表定时器的句柄值。

### 11.5. clearTimeout(t)

​	全局函数用于停止一个之前通过 `setTimeout()` 创建的定时器。参数 `t` 是通过 `setTimeout()` 函数创建的定时器。

### 11.6. setInterval(cb, ms)

​	全局函数在指定的毫秒（ms）数后执行指定函数（cb）。返回一个代表定时器的句柄值。可以使用 `clearInterval(t)` 函数来清除定时器。

​	该方法会不停的调用函数，直到 `clearInterval()` 被调用或窗口被关闭。

### 11.7. console

​	用于提供控制台标准输出，它是由 Internel Explorer 的 JScript 引擎提供的调试工具。

### 11.8. process

​	一个全局变量，即 `global` 对象的属性。用于描述当前 Node.js 进程状态的对象，提供了一个与操作系统的简单接口。

## 12. 常用工具

​	util 模块是 Node.js 的一个内置模块，包含了实用工具函数，用于支持 JavaScript 编程中的调试、错误处理、格式化等功能。

​	util 提供常用函数的集合，用于弥补核心 JavaScript 的功能过于精简的不足。

​	util 模块中的功能涵盖了从对象检查、继承到格式化字符串等多个方面。

### 12.1. 导入模块

```javascript
const util = require('util');
```

### 12.2. util.types

​	一个包含许多类型检测方法的集合，扩展了 JavaScript 的 `typeof` 和 `instanceof` 。

## 13. 文件系统

​	Node.js 的文件系统模块（fs 模块）提供了丰富的 API，用于读取、写入、删除文件以及执行其他文件系统操作。

​	fs 模块既支持同步方法也支持异步方法，使得开发者可以根据具体需求选择合适的方式来处理文件操作。

### 13.1. 导入模块

```javascript
let fs = require('fs');
```

### 13.2. 异步和同步

​	Node.js 文件系统（fs 模块）模块中的方法均有异步和同步版本。异步的方法函数最后一个参数为回调函数，回调函数的第一个参数包含了错误信息（error）。

### 13.3. 更多内容

​	详见[官方手册](https://nodejs.org/api/fs.html) 。
