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
2.  **安装依赖**：使用 `npm install <package-name>` 命令安装依赖，npm 会自动将依赖添加到 `package.json` 文件的 `dependencies` 或 `devDependencies` 中，并创建 `package-lock.json` 文件以锁定依赖的版本；
3. **管理脚本**：使用 `scripts` 字段定义命令，例如：`"start": "node app.js"` ，可以通过 `npm start` 命令来运行脚本；
4. **版本控制**：当项目准备好发布到 npm 时，可以使用 `npm publish` 命令，npm 会读取 `package.json` 中的信息来发布包；
5. **发布包**：当项目准备好发布到 npm 时，可以使用 `npm publish` 命令，npm 会读取 `package.json` 中的信息来发布包；
6. **依赖管理**：`package.json` 和 `package-lock.json` 文件一起工作，确保项目在不同环境中的依赖版本一致。
