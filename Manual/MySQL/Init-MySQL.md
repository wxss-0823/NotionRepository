### MySQL初始化配置步骤

1. 官网下载免安装压缩包（不要下载 installer ，会直接安装在 C 盘不能选路径）

2. 解压，放在合适路径下，将 mysql 版本文件添加入系统环境变量；

   `mysql = “.../mysql-x.x.x-win64”，Path = “%mysql%\bin`

3. 在 `mysql-x.x.x-win64` 下新建 `my.ini` 文件，文件内容如下：

   **其中跳过密码部分未测试成功**

   > [client]
   > #设置mysql客户端默认字符集
   > default-character-set=UTF8MB4
   > [mysqld]
   > #设置跳过密码
   > #skip-grant-tables
   > #设置3306端口
   > port = 3306
   > #设置mysql的安装目录 这块换成自己解压的路径
   > basedir=D:\\Users\\MySQL\\mysql-9.0.1-winx64
   > #允许最大连接数
   > max_connections=200
   > #服务端使用的字符集默认为8比特编码的latin1字符集
   > character-set-server=UTF8MB4
   > #创建新表时将使用的默认存储引擎
   > default-storage-engine=INNODB

4. 管理员身份运行 `cmd` ，切换路径至 `”.../mysql-x.x.x-win64“` 按顺序输入如下命令

   > 初始化服务端，并显示在控制台
   >
   > 记录初始随机密码，用于后续登录

   `mysqld --initialize --console`

   > 安装 mysqld

   `mysqld -install`

   > 启动 mysql /关闭 mysql
   
   `net start mysql / net stop mysql`
   
   如果上述某一步出问题，可以使用 `sc delete mysql` 删除服务，重新安装一次，建议将文件删除重新开始，也可以执行 `mysqld --remove mysql` 移除服务。

5. 输入 `net start mysql` 确保服务运行；输入 `mysql -u root -p` 以 root 身份登录 mysql ；输入之前记录的密码，显示成功登录 `mysql>`

6. 此时任何命令都不能执行，需要更改临时密码，输入如下命令：

   > 修改密码

   `ALTER USER USER() IDENTIFIED BY ”password“;`

   > 刷新系统权限命令

   `FLUSH PRIVILEGES; `

7. 输入 `exit;` 重新进入就可以正常执行命令了。

8. 密码：`020823`

### MySQL 升级

1. 从 https://mysql.net.cn/downloads/ 下载最新的 MySQL Windows ZIP Archive 发行版；
2. 如果服务器正在运行，请将其停止。如果服务器作为服务安装，请在命令提示符中输入以下命令停止服务

```shell
SC STOP mysqld_service_name
# 或者
net stop mysqld_service_name
```

​	如果没有将 MySQL 作为服务器运行，请使用 `mysqladmin` 将其停止。

```shell
"%mysql%\bin\mysqladmin" -u root -p [password] shutdown
```

3. 提取 ZIP 存档，并覆盖现有的 Mysql 安装。
4. 重新启动服务器，可以使用 `SC START mysqld_service_name` 或者 `net stop mysqld_service_name` ，否则直接调用 `mysqld_sevice_name mysqld` 。

