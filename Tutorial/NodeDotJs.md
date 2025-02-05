# NodeDotJs 教程

## 1. 创建应用

​	在传统的 PHP 开发中，需要一个像 Apache 或 Nginx 的 HTTP 服务器，并且需要配置 `mod_php` 或 `php-cgi` 来处理 PHP 脚本，从而生成动态内容，也就是说 PHP 依赖于外部的 HTTP 服务器来接收请求并提供 Web 页面。

​	Node.js 本身就内置了一个 HTTP 服务器模块，这意味着在使用 Node.js 开发时，开发者可以直接使用 Node.js 的 HTTP 模块来创建服务器，处理 HTTP 请求，并生成 Web 页面，而不需要依赖外部的 HTTP 服务器软件。