# Apache 部署

## 1. 部署步骤

- 打开 [HTTP SERVER PROJECT 官网](https://httpd.apache.org/download.cgi)，找到 [Files for Microsoft Windows](https://httpd.apache.org/docs/current/platform/windows.html#down)；
- 根据指引，找到二进制包发布网站 [Apache Louge](https://www.apachelounge.com/download/)；
- 下载压缩包，根据系统选择，一般选择 64 位：
  - 2024/11/2：**Apache 2.4.62-240904 Win64** 

- 解压后将文件夹 Apache24 移动到需要的目录下，作为服务器的根目录，尽量保证路径没有中文和空格，以防出现 bug；
  - 2024/11/2：**d:\Users\Apache24**

- 修改配置文件：根据 ReadMe.txt 指引，需要在 **./conf/httpd.conf** 中修改服务器根目录声明；

  ```
  Define SRVROOT "d:/Users/Apache24"
  ```

  此时可以在 cmd 中，更换路径至 **d:/User/Apache24/bin** ，并输入 `httpd.exe` 启动进程。

- 启动成功后，在浏览器中输入 `http://localhost/`，会显示 It Works，表明配置成功，否则会显示 404 not found。

## 2. 其他操作

​	操作尽量在管理员身份下进行。

### 2.1. 域名声明

​	需要在 **httpd.conf** 下声明 DNS 名称，搜索变量 `ServerName 192.168.0.100` 并配置，如果没有域名，其值应该为主机 IP。用以隐藏警告：

```shell
AH00558: httpd.exe: Could not reliably determine the server's fully qualified domain name, using 192.168.0.100. Set the 'ServerName' directive globally to suppress this message
```

### 2.2. 安装为服务

​	在 cmd 中输入 `httpd.exe -k install` ，返回下面文本说明安装成功。

```shell
Installing the 'Apache2.4' service
The 'Apache2.4' service is successfully installed.
Testing httpd.conf....
Errors reported here must be corrected before the service can be started.
```

​	可以通过命令 `services.msc` 打开服务控制面板，手动开关 **httpd.exe**。

​	也可以通过 `httpd -h` 查看命令帮助文档。

### 2.3. 配置 CGI 脚本

​	在配置文件 **httpd.conf** 中搜索路径为 **cgi-bin** 的定义，添加一条可识别的脚本类型 `AddHandler cgi-script .py .cgi` ，用于声明 python 文件可以识别。

​	在浏览器中输入 `http://localhost/cgi-bin/hello.py` 查看是否整整输出。

**注意：**需要在 python 脚本的第一行指定编译器的完整路径，否则服务器无法解析脚本。

- 2024/11/3：`#!D:\Users\Anaconda\anaconda3\python.exe`

### 2.4. 配置 html 文件

​	html 文件可以放在目录 `./htdocs/...`，在 URL 中指向具体需要执行的路径即可，这里的路径不能加入 `htdocs`。

- 2024/11/3：`http://localhost/XSLT/XSLTOnClient.html`。

**注意：**如果不指定路径，URL 仅输入 `localhost` 会默认指向 `./htdocs/index.html`。