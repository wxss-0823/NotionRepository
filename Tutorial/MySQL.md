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

```mysql
-- 删除旧用户
DROP USER 'jogn'@'localhost';
-- 重新创建用户并指定新的主机
CREATE USER 'john'@'%' IDENTIFIED BY 'password';
```

#### 1.2.9. 创建用户时指定权限

```mysql
CREATE USER 'john'@'localhost' IDENTIFIED BY 'password123' WITH GRANT OPTION;
GRANT ALL PRIVILEGES ON test_db.* TO 'john'@'localhost';
```

## 2. MySQL 常用指令

### 2.1. 创建数据库

```mysql
CREATE DATABASE database_name;
```

### 2.2. 删除数据库

```mysql
DROP DATABASE [IF EXISTS] database_name;
```

- `IF EXISTS`：判断当数据库存在时才删除，避免由于不存在引发的错误。

### 2.3. 选择数据库

```mysql
USE database_name;
```

### 2.4. 数据类型

#### 2.4.1. 数值类型

| 类型         | 大小                                     | 范围（有符号）                                               | 范围（无符号）                                               | 用途            |
| :----------- | :--------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :-------------- |
| TINYINT      | 1 Bytes                                  | (-128，127)                                                  | (0，255)                                                     | 小整数值        |
| SMALLINT     | 2 Bytes                                  | (-32 768，32 767)                                            | (0，65 535)                                                  | 大整数值        |
| MEDIUMINT    | 3 Bytes                                  | (-8 388 608，8 388 607)                                      | (0，16 777 215)                                              | 大整数值        |
| INT或INTEGER | 4 Bytes                                  | (-2 147 483 648，2 147 483 647)                              | (0，4 294 967 295)                                           | 大整数值        |
| BIGINT       | 8 Bytes                                  | (-9,223,372,036,854,775,808，9 223 372 036 854 775 807)      | (0，18 446 744 073 709 551 615)                              | 极大整数值      |
| FLOAT        | 4 Bytes                                  | (-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38) | 0，(1.175 494 351 E-38，3.402 823 466 E+38)                  | 单精度 浮点数值 |
| DOUBLE       | 8 Bytes                                  | (-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 双精度 浮点数值 |
| DECIMAL      | 对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2 | 依赖于M和D的值                                               | 依赖于M和D的值                                               | 小数值          |

#### 2.4.2. 日期和时间类型

| 类型      | 大小 ( bytes) | 范围                                                         | 格式                | 用途                     |
| :-------- | :------------ | :----------------------------------------------------------- | :------------------ | :----------------------- |
| DATE      | 3             | 1000-01-01/9999-12-31                                        | YYYY-MM-DD          | 日期值                   |
| TIME      | 3             | '-838:59:59'/'838:59:59'                                     | HH:MM:SS            | 时间值或持续时间         |
| YEAR      | 1             | 1901/2155                                                    | YYYY                | 年份值                   |
| DATETIME  | 8             | '1000-01-01 00:00:00' 到 '9999-12-31 23:59:59'               | YYYY-MM-DD hh:mm:ss | 混合日期和时间值         |
| TIMESTAMP | 4             | '1970-01-01 00:00:01' UTC 到 '2038-01-19 03:14:07' UTC结束时间是第 **2147483647** 秒，北京时间 **2038-1-19 11:14:07**，格林尼治时间 2038年1月19日 凌晨 03:14:07 | YYYY-MM-DD hh:mm:ss | 混合日期和时间值，时间戳 |

#### 2.4.3. 字符串类型

| 类型       | 大小                  | 用途                            |
| :--------- | :-------------------- | :------------------------------ |
| CHAR       | 0-255 bytes           | 定长字符串                      |
| VARCHAR    | 0-65535 bytes         | 变长字符串                      |
| TINYBLOB   | 0-255 bytes           | 不超过 255 个字符的二进制字符串 |
| TINYTEXT   | 0-255 bytes           | 短文本字符串                    |
| BLOB       | 0-65 535 bytes        | 二进制形式的长文本数据          |
| TEXT       | 0-65 535 bytes        | 长文本数据                      |
| MEDIUMBLOB | 0-16 777 215 bytes    | 二进制形式的中等长度文本数据    |
| MEDIUMTEXT | 0-16 777 215 bytes    | 中等长度文本数据                |
| LONGBLOB   | 0-4 294 967 295 bytes | 二进制形式的极大文本数据        |
| LONGTEXT   | 0-4 294 967 295 bytes | 极大文本数据                    |

#### 2.4.4. 枚举与集合类型

- **ENUM**：枚举类型，用于存储单一值，可以选择一个预定义的集合。
- **SET**：集合类型，用于存储多个值，可以选择多个预定义的集合。

#### 2.4.5. 空间数据类型（Spatial Data Types）

​	`GEOMETRY`, `POINT`, `LINESTRING`, `POLYGON`, `MULTIPOINT`, `MULTILINESTRING`, `MULTIPOLYGON`, `GEOMETRYCOLLECTION`：用于存储空间数据（地理信息、几何图形等）。

### 2.5. 创建数据表

```mysql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
);
```

### 2.6. 删除数据表

```mysql
DROP TABLE [IF EXISTS] table_name;  -- 会检查是否存在，如果存在则删除
```

### 2.7. 插入数据

```mysql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

### 2.8. 查询数据

```mysql
SELECT column1, column2, ...
FROM table_name
[WHERE condition]
[ORDER BY column_name [ASC | DESC]]
[LIMIT number];
```

- `WHERE condition`：一个可选的子句，用于指定过滤条件，只返回符合条件的行；
- `ORDER BY column_name [ASC | DESC]`：一个可选的子句，用于指定结果集的排序顺序，默认是升序（ASC）；
- `LIMIT number`：一个可选的子句，用于限制返回的行数。

### 2.9. WHERE 子句

```mysql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

### 2.10. UPDATE 更新

```mysql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

### 2.11. DELETE 语句

```mysql
DELETE FROM table_name
WHERE condition;
```

### 2.12. LIKE 子句

​	用于匹配模糊的关键字。

```mysql
SELECT column1, column2, ...
FROM table_name
WHERE column_name LIKE pattern;
```

- `pattern`：用于匹配的模式，可以包含通配符。
  - `%`：表示 0 个或多个字符；
  - `_`：表示一个字符。

### 2.13. UNION 操作符

​	用于连接两个以上的 `SELECT` 语句的结果到一个结果集，并去除重复的行。

```mysql
SELECT column1, column2, ...
FROM table1
WHERE condition1
UNION
SELECT column1, column2, ...
FROM table2
WHERE condition2
[ORDER BY column1, column2, ...];
```

### 2.14. ORDER BY 子句

​	用于对读取的数据进行排序。

```mysql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1 [ASC | DESC], column2 [ASC | DESC], ...;
```

### 2.15.  GROUP BY 语句

​	用于根据一个或多个列对结果集进行分组，在分组的列上需要指定聚合函数。

```mysql
SELECT column1, aggregate_function(column2)
FROM table_name
WHERE condition
GROUP BY column1;
```

- `aggregate_function(column2)`：对分组后的每个组执行的聚合函数，可以是：`COUNT`，`SUM`，`AVG`等。

### 2.16. JOIN 子句

​	用于在两个或多个表中查询数据。

- **INNER JOIN（内连接,或等值连接）**：获取两个表中字段匹配关系的记录。
- **LEFT JOIN（左连接）：**获取左表所有记录，即使右表没有对应匹配的记录。
- **RIGHT JOIN（右连接）：** 与 LEFT JOIN 相反，用于获取右表所有记录，即使左表没有对应匹配的记录。

```mysql
SELECT column1, column2, ...
FROM table1
INNER JOIN table2 ON table1.column_name = table2.column_name;
```

### 2.17. NULL 值处理

- `IS NULL`：当列的值是 NULL，此运算符返回 true；
- `IS NOT NULL`：当列的值不为 NULL，运算符返回 true；
- `<=>`：比较操作符（不同于 = 运算符），当比较的的两个值相等或者都为 NULL 时返回 true。

### 2.18. 正则表达式

​	使用 `REGEXP` 和 `RLIKE` 操作符来进行正则表达式匹配。

| 模式       | 描述                                              |
| :--------- | :------------------------------------------------ |
| ^          | 匹配输入字符串的开始位置                          |
| $          | 匹配输入字符串的结束位置                          |
| .          | 匹配除 "\n" 之外的任何单个字符                    |
| [...]      | 字符集合。匹配所包含的任意一个字符                |
| [^...]     | 负值字符集合。匹配未包含的任意字符                |
| p1\|p2\|p3 | 匹配 p1 或 p2 或 p3                               |
| *          | 匹配前面的子表达式零次或多次                      |
| +          | 匹配前面的子表达式一次或多次                      |
| {n}        | n 是一个非负整数，匹配确定的 n 次                 |
| {n,m}      | m 和 n 均为非负整数，最少匹配 n 次且最多匹配 m 次 |

### 2.19. 事务

​	事务是一组 SQL 语句的执行，用于处理操作量大，复杂度高的数据。它们被视为一个单独的工作单元。

#### 2.19.1. 事务的条件

- **原子性：**一个事务（transaction）中的所有操作，要么全部完成，要么全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。
- **一致性：**在事务开始之前和事务结束以后，数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设规则，这包含资料的精确度、串联性以及后续数据库可以自发性地完成预定的工作。
- **隔离性：**数据库允许多个并发事务同时对其数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。
- **持久性：**事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。

#### 2.19.2. 事务的控制语句

- `BEGIN` 或 `START TRANSACTION`：显式地开启一个事务；
- `COMMIT` 或 `COMMIT WORK`：提交事务，并使已对数据库进行的所有修改成为永久性的；
- `ROLLBACK` 或 `ROLLBACK WORK`：回滚会结束用户的事务，并撤销正在进行的所有未提交的修改；
- `SAVEPOINT identifier`：允许在事务中创建一个保存点，一个事务中可以有多个 SAVEPOINT；
- `RELEASE SAVEPOINT identifier`：删除一个事务的保存点，当没有指定的保存点时，执行该语句会抛出一个异常；
- `ROLLBACK TO identifier`：把事务回滚到标记点；
- `SET TRANSACTION` 用来设置事务的隔离级别：
  - InnoDB 存储引擎提供事务的隔离级别有 `READ UNCOMMITTED`、`READ COMMITTED`、`REPEATABLE READ` 和 `SERIALIZABLE`。

### 2.20. ALTER 命令

​	**ALTER** 命令允许你添加、修改或删除数据库对象，并且可以用于更改表的列定义、添加约束、创建和删除索引等操作。

```mysql
ALTER TABLE table_name
ADD COLUMN new_column_name datatype;
```

### 2.21. 索引

​	MySQL 索引是一种数据结构，用于加快数据库查询的速度和性能。

#### 2.21.1. 创建索引

```mysql
CREATE INDEX index_name
ON table_name (column1 [ASC|DESC], column2 [ASC|DESC], ...);
```

#### 2.21.2. 修改表结构（添加索引)

```mysql
ALTER TABLE table_name
ADD INDEX index_name (column1 [ASC|DESC], column2 [ASC|DESC], ...);
```

#### 2.21.3. 创建表的时候直接指定

```mysql
CREATE TABLE table_name (
  column1 data_type,
  column2 data_type,
  ...,
  INDEX index_name (column1 [ASC|DESC], column2 [ASC|DESC], ...)
);
```

#### 2.21.4. 删除索引的语法

```mysql
DROP INDEX index_name ON table_name;
```

#### 2.22.5. 临时表

​	MySQL 临时表在需要保存一些临时数据时是非常有用的。临时表只在当前连接可见，当关闭连接时，MySQL 会自动删除表并释放所有空间。

```mysql
CREATE TEMPORARY TABLE temp_table_name (
  column1 datatype,
  column2 datatype,
  ...
);
```

### 2.23. 复制表

​	如果需要完全的复制 MySQL 的数据表，包括表的结构，索引，默认值等。

- 使用 `SHOW CREATE TABLE` 命令获取创建数据表 `CREATE TABLE` 语句，该语句包含了原数据表的结构，索引等；
- 复制以下命令显示的 SQL 语句，修改数据表名，并执行SQL语句，通过以上命令将完全的复制数据表结构；
- 如果需要复制表的内容，可以使用 `INSERT INTO ... SELECT` 语句来实现。

### 2.24. 元数据

​	MySQL 元数据是关于数据库和其对象（如表、列、索引等）的信息。元数据存储在 MySQL 数据库的 `information_schema` 数据库中。

#### 2.24.1. SCHEMATA 表

​	存储有关数据库的信息，如数据库名、字符集、排序规则等。

```mysql
SELECT * FROM information_schema.SCHEMATA;
```

#### 2.24.2. TABLES 表

​	包含有关数据库中所有表的信息，如表名、数据库名、引擎、行数等。

```mysql
SELECT * FROM information_schema.TABLES WHERE TABLE_SCHEMA = 'your_database_name';
```

#### 2.24.3. COLUMNS 表

​	包含有关表中列的信息，如列名、数据类型、是否允许 NULL 等。

```mysql
SELECT * FROM information_schema.COLUMNS WHERE TABLE_SCHEMA = 'your_database_name' AND TABLE_NAME = 'your_table_name';
```

#### 2.24.4. STATISTICS 表

​	提供有关表索引的统计信息，如索引名、列名、唯一性等。

```mysql
SELECT * FROM information_schema.STATISTICS WHERE TABLE_SCHEMA = 'your_database_name' AND TABLE_NAME = 'your_table_name';
```

#### 2.24.5. KEY_COLUMN_USAGE 表

​	包含有关表中外键的信息，如外键名、列名、关联表等。

```mysql
SELECT * FROM information_schema.KEY_COLUMN_USAGE WHERE TABLE_SCHEMA = 'your_database_name' AND TABLE_NAME = 'your_table_name';
```

#### 2.24.6. REFERENTIAL_CONSTRAINTS 表

​	存储有关外键约束的信息，如约束名、关联表等。

```mysql
SELECT * FROM information_schema.REFERENTIAL_CONSTRAINTS WHERE CONSTRAINT_SCHEMA = 'your_database_name' AND TABLE_NAME = 'your_table_name';
```

### 2.25. 序列

​	序列是一种**自增生成数字**序列的对象，一张数据表只能有一个字段自增主键。MySQL 本身没有内建的序列类型，但可以使用 `AUTO_INCREMENT` 属性来指定表中某一列的自增性。

```mysql
CREATE TABLE example_table (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50)
);
```

### 2.26. 处理重复数据

​	可以在 MySQL 数据表中设置指定的字段为 `PRIMARY KEY` 或者 `UNIQUE` 索引来保证数据的唯一性。

### 2.27. 导出数据

#### 2.27.1. SELECT ... INTO OUTFILE 语句

```mysql
SELECT column1, column2, ...
INTO OUTFILE 'file_path'
FROM your_table
WHERE your_conditions;
```

#### 2.27.2. mysqldump 工具

​	`mysqldump` 是 MySQL 提供的用于备份和导出数据库的命令行工具。使用 `mysqldump` 导出数据需要使用 `--tab` 选项来指定导出文件指定的目录，该目标必须是可写的。

```mysql
mysqldump -u username -p password -h hostname database_name > output_file.sql
```

### 2.28. 导入数据

#### 2.28.1. mysql 命令导入

```shell
mysql -u your_username -p -h your_host -P your_port -D your_database
```

#### 2.28.2. source 命令导入

```mysql
create database abc;      # 创建数据库
use abc;                  # 使用已创建的数据库 
set names utf8;           # 设置编码
source /home/abc/abc.sql  # 导入备份数据库
```

#### 2.28.3. LOAD DATA 导入

```mysql
LOAD DATA LOCAL INFILE 'dump.txt' 
INTO TABLE mytbl [(b, c, a)];			-- 指定列的顺序
```

#### 2.28.4. mysqlimport 导入

​	`mysqlimport` 客户端提供了 `LOAD DATA INFILEQL` 语句的一个命令行接口。`mysqlimport` 的大多数选项直接对应 `LOAD DATA INFILE` 子句。

```shell
mysqlimport -u root -p --local mytbl dump.txt
```
