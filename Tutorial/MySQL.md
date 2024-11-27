# MySQL 教程

## 1. MySQL 管理

### 1.1. 启动及关闭服务器

#### 1.1.1. 服务管理工具

- `win+R` 打开"运行"对话框；
- 输入 `services.msc`，找到 MySQL 服务，右击选择启动。

#### 1.1.2. 通过命令提示符

​	以管理员身份打开命令提示符。

```shell
# 启动 MySQL 服务器
net start mysql
# 关闭 MySQL 服务器
net stop mysql
```

### 1.2. 用户设置

#### 1.2.1. 创建用户

```mysql
CREATE USER 'username'@'host' IDENTIFIED BY 'password';
```

- `username`：用户名;
- `host`：指定用户可以从哪些主机连接，例如：`localhost` 仅允许本地连接，`%` 允许从任何主机连接；
- `password`：用户的密码。

#### 1.2.2. 授权权限

​	创建用户后，需要授予他们访问权限，使用 `GRANT` 命令来授予权限。

```mysql
GRANT privileges ON database_name.* TO 'username'@'host';
```

- `privileges`：所需的权限，如 `ALL PRIVILEGES`、`SELECT`、`INSERT`、`UPDATE`、`DELETE` 等；
- `database_name.*`：表示对某个数据库或表授予权限，`database_name.*` 表示对整个数据库的所有表授予权限，`database_name.table_name` 表示对指定的表授予权限；
- `TO 'username'@'host'`：指定授予权限的用户和主机。

#### 1.2.3. 刷新权限

​	授予或撤销权限后，需要刷新权限使更改生效。

```mysql
FLUSH PRIVILEGES;
```

#### 1.2.4. 查看用户权限

```mysql
SHOW GRANTS FOR 'username'@'host';
```

#### 1.2.5. 撤销权限

```mysql
REVOKE privileges ON database_name.* FROM 'username'@'host';
```

#### 1.2.6. 删除用户

```mysql
DROP USER 'username'@'host';
```

#### 1.2.7. 修改用户密码

```mysql
ALTER USER 'username'@'host' IDENTIFIED BY 'new_password';
```

#### 1.2.8. 修改用户主机

​	要更改用户的主机（即允许从哪些主机连接），可以先删除用户，再重新创建一个新的用户。









































