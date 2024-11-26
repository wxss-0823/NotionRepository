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

- `username`：用户名。
- `host`：指定用户可以从哪些主机连接。例如，`localhost` 仅允许本地连接，`%` 允许从任何主机连接。
- `password`：用户的密码。



























