# NodeDotJs 教程

## 1. 创建应用

​	在传统的 PHP 开发中，需要一个像 Apache 或 Nginx 的 HTTP 服务器，并且需要配置 `mod_php` 或 `php-cgi` 来处理 PHP 脚本，从而生成动态内容，也就是说 PHP 依赖于外部的 HTTP 服务器来接收请求并提供 Web 页面。

​	Node.js 本身就内置了一个 HTTP 服务器模块，这意味着在使用 Node.js 开发时，开发者可以直接使用 Node.js 的 HTTP 模块来创建服务器，处理 HTTP 请求，并生成 Web 页面，而不需要依赖外部的 HTTP 服务器软件。

# 2. NPM 使用介绍

​	NPM（Node Package Manager）是一个 JavaScript 包管理工具，也是 Node.js 的默认包管理器，其允许开发者轻松地下载、安装、共享、管理项目的依赖库和工具。

## 2.1. 版本检查

​	新版的 Node.js 集成了 NPM，可以直接输入 `npm -v` 查看当前版本。如果安装的是旧版本，可以通过 `npm install npm -g` 升级。

## 2.2. 安装模块

```shell
npm install <Module Name>
```

### 2.2.1. 安装模式

​	NPM 的包安装分为本地安装和全局安装两种，从命令行看，两者只相差 `-g` 参数。



