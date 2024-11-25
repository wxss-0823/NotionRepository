# SQLite 教程

## 1. SQLite 基础教程

### 1.1. SQLite 简介

​	SQLite 是一个进程内的库，实现了自给自足的、无服务器的、零配置的、事务性的 SQL 数据库引擎。SQLite 引擎不是一个独立的进程，可以按应用程序的需求进行静态或者动态连接，也可以直接访问其存储文件。

- 不需要一个单独的服务器进程或操作系统（无服务器的）；
- SQLite 不需要配置，这意味着不需要安装或管理；
- 一个完整的 SQLite 数据库是存储在一个单一的跨平台的磁盘文件；
- SQLite 非常小，是轻量级的，完全配置时小于 400 KB，省略可选功能配置时小于 250 KB；
- SQLite 是自给自足的，这意味着不需要任何外部的依赖；
- SQLite 事务是完全兼容 ACID 的，允许从多个进程或线程安全访问；
- SQLite 可以 UNIX 和 Windows 中运行。

### 1.2. SQLite 点命令

​	这些命令不以 `;` 结束：

<table>
  <tr align='center'>
    <td><b>命令</td>
    <td><b>描述</td>
  </tr>
	<tr>
    <td>.backup ?DB? FILE</td>
    <td>备份 DB 数据库（默认是 main）到 FILE 文件</td>
	</tr>
  <tr>
    <td>.bail ON|OFF</td>
    <td>发生错误后停止（默认是 OFF）</td>
	</tr>
  <tr>
    <td>.databases</td>
    <td>列出数据库的名词及其所依赖的文件</td>
	</tr>
  <tr>
    <td>.dump ?TABLE?</td>
    <td>以 SQL 文本格式转储数据库，如果指定了 TABLE，则只会转储匹配 LIKE 模式的 TABLE</td>
  </tr>
  <tr>
    <td>.echo ON|OFF</td>
    <td>开启或关闭 echo 命令</td>
	</tr>
  <tr>
    <td>.exit</td>
    <td>退出 SQLite 提示符</td>
	</tr>
  <tr>
    <td>.explain ON|OFF</td>
    <td>开启或关闭适合于 EXPLAIN 的输出模式，如果不带参数，则开启 EXPLAIN</td>
	</tr>
  <tr>
    <td>.header(s) ON|OFF</td>
    <td>开启或关闭头部显示</td>
	</tr>
  <tr>
    <td>.help</td>
    <td>显示帮助信息</td>
	</tr>
  <tr>
    <td>.import FILE TABLE</td>
    <td>导入来自 FILE 文件的数据到 TABLE 表中</td>
	</tr>
  <tr>
    <td>.indices ?TABLE?</td>
    <td>显示所有索引的名称，如果指定了 TABLE 表，则只显示匹配 LIKE 模式的 TABLE 索引</td>
	</tr>
  <tr>
    <td>.load FILE ?ENTRY?</td>
    <td>加载一个扩展库</td>
	</tr>
  <tr>
    <td>.log FILE|OFF</td>
    <td>开启或关闭日志，FILE 文件可以是 stderr（标准错误） 或者stdout（标准输出）</td>
	</tr>
  <tr>
    <td>.mode MODE</td>
    <td>
      设置输出模式：
      <ul>
        <li><b>csv ：</b>逗号分隔的值<br/></li>
				<li><b>column ：</b>左对齐的列<br/></li>
        <li><b>html ：</b>HTML 的 &lttable&gt 代码<br/></li>
        <li><b>insert ：</b>TABLE 表的 SQL 插入语句<br/></li>
        <li><b>line ：</b>每行一个值<br/></li>
        <li><b>list ：</b>由 .separator 字符串分隔的值<br/></li>
        <li><b>tabs ：</b>由 Tab 分隔的值<br/></li>
        <li><b>tcl ：</b>TCL 列表元素<br/></li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>.nullvalue STRING</td>
    <td>在 NULL 值的地方输出 STRING 字符串</td>
	</tr>
  <tr>
    <td>.output FILENAME</td>
    <td>发送输出到 FILENAME 文件</td>
	</tr>
  <tr>
    <td>.output stdout</td>
    <td>发送输出到屏幕</td>
	</tr>
  <tr>
    <td>.print STRING</td>
    <td>逐字地输出 STRING 字符串</td>
	</tr>
  <tr>
    <td>.prompt MAIN CONTINUE</td>
    <td>替换标准提示符</td>
	</tr>
  <tr>
    <td>.quit</td>
    <td>退出 SQLite 提示符</td>
	</tr>
  <tr>
    <td>.read FILENAME</td>
    <td>执行 FILENAME 文件中的 SQL</td>
	</tr>
  <tr>
    <td>.schema ?TABLE?</td>
    <td>显示 CREATE 语句，如果指定了 TABLE，则只显示匹配 LIKE 模式的 TABLE</td>
	</tr>
  <tr>
    <td>.separator STRING</td>
    <td>改变输出模式和 .import 所使用的的分隔符</td>
	</tr>
  <tr>
    <td>.show</td>
    <td>显示各种设置的当前值</td>
	</tr>
  <tr>
    <td>.stats ON|OFF</td>
    <td>开启或关闭统计</td>
	</tr>
  <tr>
    <td>.tables ?PATTERN?</td>
    <td>列出匹配 LIKE 模式的表的名称</td>
	</tr>
  <tr>
    <td>.timeout MS</td>
    <td>尝试打开锁定的表的时间（单位：ms）</td>
	</tr>
  <tr>
    <td>.width NUM NUM</td>
    <td>为“column”模式设置列宽度</td>
	</tr>
  <tr>
    <td>.timer ON|OFF</td>
    <td>开启或关闭 CPU 定时器</td>
	</tr>
</table>

### 1.3. SQLite 语法

#### 1.3.1. 大小写敏感性

​	SQLite 不区分大小写，但有些命令大小写敏感，例如：`GLOB` 和 `glob` 是不同的含义。

#### 1.3.2. 注释

​	SQLite 注释由两种表示方式：

- 以两个连续的 `-` 开始，并至第一个换行符结束，或者直到输入结束，以先到者为准；

	```sqlite
	-- 这是一个注释
	```

- 类似 C 语言的风格， 以 `/*` 开始，以 `*/` 结束，或者直到输入结束，以先到者为准。

	```sqlite
	/* 这是一个注释 */
	```

#### 1.3.3. 语句

##### ANALYZE 语句

```sqlite
ANALYZE;
-- or
ANALYZE database_name;
-- or
ANALYZE database_name.table.name;
```

##### AND/OR 子句

```sqlite
SELECT * FROM table_name WHERE CONDITION-1 {AND|OR} CONDITION-2;
```

##### ALTER TABLE 语句

```sqlite
ALTER TABLE table_name ADD COLUMN ...;
ALTER TABLE table_name RENAME TO  ...;
```

##### ATTACH DATABASE 语句

```sqlite
ATTACH DATABASE 'database_name' AS 'alias_name'
```

##### BEGIN TRANSACTION 语句

```sqlite
BEGIN;
-- or
BEGIN EXCLUSIVE TRANSACTION;
```

##### BETWEEN 语句

```sqlite
SELECT * FROM table_name WHERE column_name BETWEEN val-1 AND val-2;
```

##### COMMIT 语句

```sqlite
COMMIT;	
```

##### CREATE 语句

```sqlite
-- 创建索引
CREATE INDEX index_name ON table_name (column_name COLLATE NOCASE);
-- 创建唯一索引
CREATE UNIQUE INDEX index_name ON table_name (column-1, column-2, ... , column-n);
-- 创建表格
CREATE TABLE table_name(
	column-1 datatype,
  column-2 datatype,
  column-3 datatype,
  ... ,
  column-n datatype,
  PRIMARY KEY(one or more columns)
)
-- 创建触发器
CREATE TRIGGER database_name.trigger_name
BEFORE INSERT ON table_name FOR EACH ROW
BEGIN
	stmt-1;
	stmt-2;
	...;
END;
-- 创建视图
CREATE VIEW database_name.view_name AS SELECT stmt...;
-- 创建虚拟表
CREATE VIRTUAL TABLE database_name.table_name USING weblog(access.log);
-- or
CREATE VIRTUAL TABLE database_name.table_name USING fts3();
```

##### COMMIT TRANSACTION 语句

```sqlite
COMMIT;
```

##### COUNT 子句

```sqlite
SELECT COUNT(column_name) FROM table_name WHERE CONDITION;
```

##### DELETE 子句

```sqlite
DELETE FROM table_name WHERE {CONDITION};
```

##### DETACH DATABASE 语句

```sqlite
DETACH DATABASE 'Alias-name'
```

##### DISTINCT 子句

```sqlite
SELECT DISTINCT column-1, column-2, ... , column-n FROM table_name;
```

##### DROP 语句

```sqlite
-- 删除索引
DROP INDEX database_name.index_name;
-- 删除表格
DROP TABLE database_name.table_name;
-- 删除视图
DROP VIEW view_name;
-- 删除触发器
DROP TRIGGER trigger_name;
```

##### EXISTS 语句

```sqlite
SELECT column-1, column-2, ... , column-n FROM table_name WHERE column_name EXISTS (SELECT * FROM table_name);
```

##### EXPLAIN 语句

```sqlite
EXPLAIN INSERT statement...;
-- or
EXPLAIN QUERY PLAN SELECT statement...;
```

##### GLOB 子句

```sqlite
SELECT column-1, column-2, ... , column-n FROM table_name WHERE column_name GLOB {PATTERN};
```

##### GROUP BY 子句

```sqlite
SELECT SUM(column_name) FROM table_name WHERE CONDITION GROUP BY column_name;
```

##### HAVING 子句

```sqlite
SELECT SUM(column_name) FROM table_name WHERE CONDITION GROUP BY column_name Having (arithematic funciton condition);
```

##### IN 子句

```sqlite
SELECT column-1, column-2, ... , column-n FROM table_name WHERE column_name IN (val-1, val-2, ... , val-n);
```

##### LIKE 子句

```sqlite
SELECT column-1, column-2, ... , column-n FROM table_name WHERE column_name LIKE {PATTERN};
```

##### NOT IN 子句

```sqlite
SELECT colunm-1, column-2, ... , column-n 
FROM table_name
WHERE column_name NOT IN (val-1, val-2, ... , val-n);
```

##### PRAGMA 语句

```sqlite
PRAGMA pragma_name;
```

##### RELEASE SAVEPOINT 语句

```sqlite
RELEASE savepoint_name;
```

##### REINDEX 语句

```sqlite
REINDEX collation_name;
REINDEX database_name.index_name;
REINDEX database_name.table_name;
```

##### ROLLBACK 语句

```sqlite
ROLLBACK;
-- or
ROLLBACK TO SAVEPOINT savepoint_name;
```

##### SAVEPOINT 语句

```sqlite
SAVEPOINT savepoint_name;
```

##### SELECT 语句

```sqlite
SELECT column-1, column-2, ... , column-n
FROM table_name;
```

##### UPDATE 语句

```sqlite
UPDATE table_name
SET column-1 = v-1, column-2 = v-2, ... , column-n = v-n
[ WHERE CONDITION ];
```

##### VACUUM 语句

```sqlite
VACUUM;
```

##### WHERE 语句

```sqlite
SELECT col-1, col-2, ... ,col-n
FROM table_name
WHERE CONDITION;
```

### 1.4. SQLite 数据类型

​	SQLite 数据类型是一个用来指定任何对象的数据类型的属性。SQLite 中每一列，每个变量或表达式，都有相关的数据类型。

#### 1.4.1. 存储类

| 存储类  | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| NULL    | 是一个 NULL 值                                               |
| INTEGER | 是一个带符号的整数，根据值存储在 1 ~ 8 个字节中              |
| REAL    | 是一个浮点数，存储在 8 字节的 IEEE 浮点数字                  |
| TEXT    | 是一个文本字符串，使用数据库编码（UTF-8、UTF-16BE 或 UTF-16LE）存储 |
| BLOB    | 是一个 blob 数据，完全根据它的输入存储                       |

#### 1.4.2. 亲和（Affinity）类型

​	SQLite 支持列的亲和类型概念，即每一列仍然可以存储多种不同的数据类型，但当数据插入时，该字段的数据将会优先采用亲和亲缘类型作为该值的存储方式。

| 亲和类型 | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| TEXT     | 数值型数据在被插入之前，需要被转化为文本格式，再插入到目标字段 |
| NUMERIC  | 当文本数据插入时，如果转换操作不会导致数据信息丢失以及完全可逆，那么 SQLite 会把数据转化为 INTEGER 或 REAL 类型的数据，如果转换失败，则仍会以 TEXT 的方式存储数据；当 NULL 或 BLOB 类型的数据插入时，SQLite 不做转换 |
| INTEGER  | 规则等同于 NUMERIC，区别在于执行 CAST 表达式                 |
| REAL     | 规则基本等同于 NUMERIC，唯一区别在于不会将浮点格式的常量文本转换为 INTEGER 存储 |
| NONE     | 不做任何转换，直接以该数据所属的数据类型进行存储             |

#### 1.4.3. 数据类型与亲和类型对应关系

<table>
  <tr align='center'>
  	<td><b>亲和类型</b></td>
    <td><b>数据类型</b></td>
  </tr>
  <tr>
    <td>INTEGER</td>
    <td>
    	<ul>
        <li>INT</li>
        <li>INTEGER</li>
        <li>TINYINT</li>
        <li>SMALLINT</li>
        <li>MEDIUMINT</li>
        <li>BIGINT</li>
        <li>UNSIGNED BIG INT</li>
        <li>INT2</li>
        <li>INT8</li>
      </ul>
    </td>
  </tr>
  <tr>
  	<td>TEXT</td>
    <td>
      <ul>
        <li>CHARACTER(20)</li>
        <li>VARCHAR(255)</li>
        <li>VARYING CHAR ACTER(255)</li>
        <li>NCHAR(55)</li>
        <li>NATIVE CHARACTER(70)</li>
        <li>NVARCHAR(100)</li>
        <li>TEXT</li>
        <li>CLOB</li>
      </ul>
    </td>
  </tr>
  <tr>
  	<td>BLOB</td>
    <td>
    	<ul>
        <li>BOLB</li>
        <li>未指定类型</li>
      </ul>
    </td>
  </tr>
  <tr>
  	<td>REAL</td>
    <td>
    	<ul>
        <li>REAL</li>
        <li>DOUBLE</li>
        <li>DOUBLE PRECISION</li>
        <li>FLOAT</li>
      </ul>
    </td>
  </tr>
  <tr>
  	<td>NUMERIC</td>
    <td>
    	<ul>
        <li>NUMERIC</li>
        <li>DECIMAL</li>
        <li>BOOLEAN</li>
        <li>DATE</li>
        <li>DATETIME</li>
      </ul>
    </td>
  </tr>
</table>

#### 1.4.4. Boolean 数据类型

​	SQLite 没有单独的 BOOLEAN 存储类。布尔值被存储为整数：0（false），1（true）。

#### 1.4.5. Date 与 Time 数据类型

​	SQLite 没有一个单独的用于存储日期或时间的存储类，但是能够存储为 TEXT，REAL 或 INTEGER 值。

| 存储类  | 日期格式                                                     |
| ------- | ------------------------------------------------------------ |
| TEXT    | 格式为 "YYYY-MM-DD HH:MM:SS.SSS" 的日期                      |
| REAL    | 从公元前 4714 年 11 月 24 日格林尼治时间的正午开始算起的天数 |
| INTEGER | 从 1970-01-01 00:00:00 UTC 算起的秒数                        |

​	可以使用任何上述格式来存储日期和时间，并且可以使用内置的日期和时间函数来自由转换不同格式。

### 1.5. SQLite 基础操作

#### 1.5.1. 创建数据库

​	如果存在，则打开对应数据库；如果不存在，则创建同名数据库。

```sqlite
sqlite3 database_name.db
-- 或者
.open database_name.db
```

#### 1.5.2. 附加数据库

​	允许用户将一个数据库文件连接到当前正在使用的数据库中，从而可以通过一个连接同时操作多个数据库文件。

```sqlite
ATTACH DATABASE 'path/file_name' as database_name;
```

​	使用语句 `dabase_name.table` 指定要查询的表所属的数据库。

#### 1.5.3. 分离数据库

​	用于将一个逻辑数据库从当前连接中分离，如果同一个数据文件有多个引用，可以只断开指定别名的连接，其余仍然有效。

```sqlite
DETACH DATABASE 'Alias-Name'
```

#### 1.5.4. 创建表

​	告诉数据库系统创建一个新表的关键字，并指定标的唯一名称或标识（`table_name`）。

```sqlite
CREATE TABLE database_name.table_name(
	column1 datatype PRIMARY KEY(one or more columns),
	column2 datatype,
	column3 datatype,
	... ,
	columnN datatype
);
```

#### 1.5.5. 删除表

​	用于删除表定义及其相关的全部数据、索引、触发器、约束和该表的权限规范。

```sqlite
DROP TABLE database_name.table_name;
```

#### 1.5.6. Insert 语句

​	用于向数据库的某个表中添加新的数据行。如果为表中的所有列添加值，不需要指定列名词，但是要确保值的顺序与定义一致。

```sqlite
INSERT INTO table_name [(column1, column2, column3, ... , columnN)]
VALUE (value1, value2, value3, ... , valueN);
```

##### 使用一个表填充另一个表

```sqlite
INSERT INTO first_table_name [(column1, column2, ... , columnN)]
SELECT column1, column2, ... , columnN
FROM second_table_name
WHERE condition;
```

#### 1.5.7. SELECT 语句

​	用于从 SQLite 数据库表中获取数据，以结果表的形式返回数据。

```sqlite
SELECT column1, column2, column3, ... , columnN FROM table_name;
```

​	如果想获取所有可用的字段。

```sqlite
SELECT * FROM table_name;
```

##### 设置输出列的宽度

​	有时由于默认显示列宽 `.mode column` 不足，导致输出被截断，此时自定义输出列宽。

```sqlite
-- 依次定义输出列宽
.width col1, col2, col3, ... colN
```

##### Schema 信息

​	由于**点命令**仅在 SQLite 提示符中可用，当外部连接时，需要使用下述语句罗列数据库中的表。

```sqlite
SELECT tbl_name FROM sqlite_master WHERE type = 'table';
```

​	如果想要读取表的完整定义信息。

```sqlite
SELECT sql FROM sqlite_master WHERE type = 'table' AND tbl_name = 'table_name';
```

### 1.6. SQLite 基础表达式

#### 1.6.1. 运算符

##### 算术运算符

| 运算符 | 描述                             |
| ------ | -------------------------------- |
| +      | 加法，把两个操作数相加           |
| -      | 减法，左操作数减去右操作数       |
| *      | 乘法，把两个操作数相乘           |
| /      | 除法，左操作数除以右操作数       |
| %      | 取模，左操作数除以右操作数的余数 |

##### 比较运算符

| 运算符 | 描述                                                         |
| ------ | ------------------------------------------------------------ |
| ==     | 检查两个操作数的值是否相等，如果相等，则条件为真             |
| =      | 检查两个操作数的值是否相等，如果相等，则条件为真             |
| !=     | 检查两个操作数的值是否相等，如果不相等，则条件为真           |
| <>     | 检查两个操作数的值是否相等，如果不相等，则条件为真           |
| >      | 检查左操作数的值是否大于右操作数的值，如果是，则条件为真     |
| <      | 检查左操作数的值是否大于右操作数的值，如果是，则条件为真     |
| >=     | 检查左操作数的值是否大于等于右操作数的值，如果是，则条件为真 |
| <=     | 检查左操作数的值是否小于等于右操作数的值，如果是，则条件为真 |
| !<     | 检查左操作数的值是否不小于右操作数的值，如果是，则条件为真   |
| !>     | 检查左操作数的值是否不大于右操作数的值，如果是，则条件为真   |

##### 逻辑运算符

| 运算符  | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| AND     | 用于在一个 SQL 语句的 WHERE 子句中使用多个条件               |
| BETWEEN | 用于在给定的最小值与最大值范围内进行查找                     |
| EXISTS  | 用于在满足一定条件的指定表中搜索行的存在                     |
| IN      | 用于把某个值与一系列指定列表的值进行比较                     |
| NOT IN  | 用于把某个值与不再一系列指定列表的值进行比较                 |
| LIKE    | 用于把某个值与使用通配符运算符的相似值进行比较               |
| GLOB    | 用于把某个值与使用通配符运算符的相似值进行比较（大小写敏感） |
| NOT     | 所有逻辑运算符的对立面                                       |
| OR      | 用于结合一个 SQL 语句的 WHERE子句的多个条件                  |
| IS NULL | 用于把某个值与 NULL 值进行比较                               |
| IS      | 与 = 相似                                                    |
| IS NOT  | 与 != 相似                                                   |
| \|\|    | 连接两个不同字符串，得到一个新的字符串                       |
| UNIQUE  | 搜索指定表中的每一行，确保唯一性                             |

##### 位运算符

| 运算符 | 描述       |
| ------ | ---------- |
| &      | 按位与     |
| \|     | 按位或     |
| ~      | 按位非     |
| <<     | 左移运算符 |
| >>     | 右移运算符 |

#### 1.6.2. WHERE 子句

​	用于指定从一个表或多个表中获取数据的条件，如果满足条件，则从表中返回特定的值，可以用于过滤记录，只获取需要的记录。

```sqlite
SELECT column1, column2, column3, ... , columnN
FROM table_name
WHERE [condition]
```

#### 1.6.3. AND/OR 运算符

​	用于编译多个条件来缩小在 SQLite 语句中所选的数据，被称为连接运算符。

##### AND

​	当所有条件都为真时，整个条件为真。

```sqlite
SELECT column1, column2, column3, ... , columnN
FROM table_name
WHERE [condition1] AND [condition2] ... AND [conditionN]
```

##### OR

​	当任何一个条件为真时，整个条件为真。

```sqlite
SELECT column1, column2, column3, ... , columnN
FROM table_name
WHERE [condition1] OR [condition2] ... OR [conditonN]
```

#### 1.6.4. UPDATE 语句

​	用于修改表中已有的记录，可以使用带有 `WHERE` 子句的查询来更新选定行。

```sqlite
UPDATE table_name
SET column1 = value1, column2 = value2, ... , columnN = valueN
WHERE [condition];
```

#### 1.6.5. DELETE 语句

​	用于删除表中的已有记录，可以使用带有 `WHERE` 子句的查询来删除选定行。

```sqlite
DELETE FROM table_name
WHERE [condition];
```

#### 1.6.6. LIKE 子句

​	用于匹配通配符指定模式的文本值。如果搜索表达式与模式表达式匹配，`LIKE` 运算符将返回真（true，1）。常用的通配符：

- 百分号：`%`，代表零个、一个或多个数字，字符；
- 下划线：`_`，代表一个单一的数字或字符。

​	这些符号的可以被组合使用。

```sqlite
SELECT column_list
FROM table_name
WHERE column LIKE 'xxxx%';
```

#### 1.6.7. GLOB 子句

​	用于匹配通配符指定模式的文本值。如果搜索表达式与模式表达式匹配，`GLOB` 运算符将返回真（true，1）。与 `LIKE` 运算符不同的是，`GLOB` 是大小写敏感的。常用的通配符语法：

- `*`：匹配零个、一个或多个数字或字符；

- `?`：代表一个单一的数字或字符；

- `[...]`：匹配方括号内指定的字符之一；

- `[^...]`：匹配不在方括号内指定的字符之一。

#### 1.6.8. LIMIT 子句

​	用于限制由 `SELECT` 语句返回的数据数量。

```sqlite
SELECT column1, column2, ... , columnN
FROM table_name
LIMIT [num of rows];
-- 或者
SELECT column1, column2, ... , columnN
FROM table_name
LIMIT [num of rows] OFFSET [row num];
```

#### 1.6.9. ORDER BY 子句

​	用来基于一个或多个列按升序或降序顺序排列数据。

```sqlite
SELECT column-list
FROM table_name
[WHERE condition]
[ORDER BY column1, column2, column3, ... , columnN][ASC | DESC];
```

- `ASC`：默认值，从小到大，升序排列；
- `DESC`：从大到小，降序排列。

​	可以使用多个列，基于多个列多次排序，每列可以指定不同的排序方式。

```sqlite
SELECT column-list
FROM table_name
ORDER BY column1 ASC, column2 DESC;
```

​	如果不指定排序规则，则默认按照 `ASC` 排序，上面的代码可以等效简化为：

```sqlite
SELECT column-list
FROM table_name
ORDER BY column1, column2 DESC;
```

#### 1.6.10. Group By 子句

​	用于与 `SELECT` 语句一起使用，来对相同的数据进行分组。`GROUP BY` 语句必须放在 `WHERE` 子句之前，`ORDER BY` 子句之后。

```sqlite
SELECT column-list
FROM table_name
WHERE [ condition ]
GROUP BY column1, column2, ... , columnN
ORDER BY column1, column2, ... , columnN;
```

​	这种分组是指将所选中的列中相同的项合并。

#### 1.6.11. Having 子句

​	用于使用指定条件过滤将出现在最终结果中的分组结果。

```sqlite
SELECT column-list
FROM table_name
WHERE [ condition ]
GROUP BY column-list
HAVING [ condition ]
ORDER BY column-list;
```

#### 1.6.12. Distinct 关键字

​	 与 `SELECT` 语句一起使用，用于消除所有重复的记录，并只获取唯一一次记录。

```sqlite
SELECT DISTINCT column-list
FROM table_name 
WHERE [ condition ]
```

## 2. SQLite 高级教程

### 2.1. SQLite PRAGMA

```sqlite
// 查询值
PRAGMA pragma_name;
// 设置值
PRAGMA pragma_name = value;
```

#### 2.1.1. auto_vacuum

​	获取或设置 `auto_vacuum` 模式。

```sqlite
 PRAGMA [database.]auto_vacuum;
 PRAGMA [database.]auto_vacuum = mode;
```

| PRAGMA 值        | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| 0 或 NONE        | 禁用 Auto-vacuum，默认模式，数据库文件尺寸不会缩小           |
| 1 或 FULL        | 启用 Auto-vacuum，全自动模式，数据库文件会随数据移除而缩小   |
| 2 或 INCREMENTAL | 启用 Auto-vacuum，必须手动激活，引用数据被维持，自由页面只放在自由列表中，可在任何时候被 `incremental_vacuum` 覆盖 |

#### 2.1.2. cache_size

​	获取或暂时设置在内存中页面缓存的最大尺寸。

```sqlite
PRAGMA [database.]cache_size;
PRAGMA [database.]cache_size = pages;
```

- `pages`：表示在缓存中的页面数，默认为 2000 页，最小为 10 页。

#### 2.1.3. case_sensitive_like

​	控制内置的 `LIKE` 表达式的大小写敏感度。默认为忽略大小写（false），目前无法查询该 PRAGMA 的当前状态。

```sqlite
PRAGMA case_sensitive_like = [true|false];
```

#### 2.1.4. count_changes

​	获取或设置数据操作语句的返回值。默认为无返回值（false），如果设置为 true，语句会返回一个单行单列的表，由一个单一的整数构成， 该整数表示操作影响的行。

```sqlite
PRAGMA count_changes;
PRAGMA count_changes = [true|false];
```

#### 2.1.5. database_list

​	用于列出所有数据库的连接。

```sqlite
PRAGMA database_list;
```

#### 2.1.6. encoding

​	控制字符串编码及存储在数据库文件中的模式。

```sqlite
PRAGMA encoding;
PRAGMA encoding = format;
```

#### 2.1.7. freelist_count

​	用于返回当前被标记为免费和可用的数据库页数。

```sqlite
PRAGMA [database.]freelist_count;
```

#### 2.1.8. index_info

​	用于返回关于数据库索引的信息。

```sqlite
PRAGMA [database.]index_info( index_name );
```

#### 2.1.9. index_list

​	用于列出所有与表相关联的索引。

```sqlite
PRAGMA [database.]index_list( table_name );
```

#### 2.1.10. journal_mode

​	获取或设置日志文件的存储和处理模式。

```sqlite
PRAGMA [database.]journal_mode;
PRAGMA [database.]journal_mode = mode;
```

| PRAGMA 值 | 描述                                               |
| --------- | -------------------------------------------------- |
| DELETE    | 默认模式，事务结束时，日志文件将被删除             |
| TRUNCATE  | 日志文件被截断为零字节长度                         |
| PERSIST   | 日志文件被留在原地，但头部被重写，表面日志不再有效 |
| MEMORY    | 日志记录保留在内存中，而不是在磁盘上               |
| OFF       | 不保留任何日志记录                                 |

#### 2.1.11. max_page_count

​	获取或设置数据库允许的最大页数。默认值是 1,073,741,823，

```sqlite
PRAGMA [database.]max_page_count;
PRAGMA [database.]max_page_count = max_page;
```

#### 2.1.12. page_size

​	获取或设置数据库页面的大小。默认情况下，可以为：512，1024，2048，4096，8196，16384，32768 字节。改变数据库页面大小的唯一方法就是设置页面大小，然后立即 `VACCUM` 该数据库。

```sqlite
PRAGMA [database.]page_size;
PRAGMA [database.]page_size = bytes;
```

#### 2.1.13. parser_trace

​	用于控制解析器的打印。默认情况下，被设置为 false，但设置为 true 时，则启用。此时 SQL 解析器会随着解析 SQL 命令，打印状态。

```sqlite
PRAGMA parser_trace = [true|false];
```

#### 2.1.14. recursive_triggers

​	获取或设置递归触发器功能。如果未启用递归触发器，一个触发器不会触发另一个触发器。

```sqlite
PRAGMA recursive_triggers;
PRAGMA recursive_triggers = [true|false];
```

#### 2.1.15. schema_version

​	获取或设置存储在数据库头中的架构版本值。值为一个 32 位有符号整数值，用来追踪架构的变化。

```sqlite
PRAGMA [database.]schema_version;
PRAGMA [database.]schema_version = number;
```

#### 2.1.16. secure_delete

​	用来控制内容从数据库中删除的方式。安全删除标志默认是关闭。

```sqlite
PRAMGA [database.]secure_delete;
PRAMGA [database.]secure_delete = [true|false];
```

#### 2.1.17. sql_trace

 	用于把 SQL 追踪结果转储到屏幕上。

```sqlite
PRAGMA sql_trace;
PRAGMA sql_trace = [true|false];
```

#### 2.1.18. synchronous 

​	获取或设置当前磁盘的同步模式。用于控制 SQLite 将数据写入物理存储的方式。

```sqlite
PRAGMA [database.]synchronous;
PRAGMA [database.]synchronous = mode;
```

| PRAGMA 值   | 描述                             |
| ----------- | -------------------------------- |
| 0 或 OFF    | 不进行同步                       |
| 1 或 NORMAL | 在关键的磁盘操作的每个序列后同步 |
| 2 或 FULL   | 在每个关键的磁盘操作后同步       |

#### 2.1.19. temp_store

​	获取或设置临时数据库文件的存储模式。

```sqlite
PRAGMA temp_store;
PRAGMA temp_store = mode;
```

| PRAGMA 值    | 描述                              |
| ------------ | --------------------------------- |
| 0 或 DEFAULT | 默认使用编译时的模式，通常是 FILE |
| 1 或 FILE    | 使用基于文件的存储                |
| 2 或 MEMORY  | 使用基于内存的存储                |

#### 2.1.20. temp_store_directory

​	获取或设置用于临时数据库文件的位置。

```sqlite
PRAGMA temp_store_directory;
PRAGMA temp_store_directory = "directory_path";
```

#### 2.1.21. user_version

​	获取或设置存储在数据库头的用户自定义的版本值。值为一个 32 位有符号整数，可以有开发人员设置，用于版本跟踪。

```sqlite
PRAGMA [database.]user_version;
PRAGMA [database.]user_version = number;
```

#### 2.1.21. writable_schema

​	获取或设置是否能够修改系统表。如果设置了该 PRAGMA，则表以 `sqlite_` 开始，可以创建和修改，包括 `sqlite_maste` 表。

```sqlite
PRAGMA writable_schema;
PRAGMA writable_schema = [true|false];
```

​	使用该 PRAGMA 时要注意，因为它可能导致整个数据库损坏。

### 2.2. SQLite 约束

​	约束是在表的数据列上强制执行的规则，用来限制可以插入到表中的数据类型，用来确保数据库中数据的准确性和可靠性。

#### 2.2.1. NOT NULL

​	默认情况下，列可以保存 NULL 值。如果不想在某列有 NULL 值，那么需要在该列上定义约束，指定在该列上不允许 NULL 值。

```sqlite
CREATE TABLE table_name(
	... ,
	NAME TEXT NOT NULL,
	...
);
```

#### 2.2.2. DEFAULT

​	在 `INSERT INTO` 语句没有提供一个特定的值时，为列提供一个默认值。

```sqlite
CREATE TABLE table_name(
	... ,
	SALARY REAL DEFAULT 100.00 ,
	...
);
```

#### 2.2.3. UNIQUE

​	防止在一个特定的列上存在两个记录具有相同的值。

```sqlite
CREATE TABLE table_name(
	... ,
	AGE INT NOT NULL UNIQUE ,
	...
);
```

#### 2.2.4. PRIMARY KEY

​	唯一标识数据库中的每个记录，与 UNIQUE 类似。一个表中可以有多个 UNIQUE 列，但是只能有一个 PRIMARY KEY，这个主键可以由多个列（字段）构成，称为复合键。主键可以被设置为其他表的外键，用于创建表之间的关系，

```sqlite
CREATE TABLE table_name(
	ID INT NOT NULL,
	CATALOG_ID INT NOT NULL,
	PRIMARY KEY(ID, CATALOG_ID),
	...
);
```

#### 2.2.5. CHECK

​	用于启用一个插入检查。如果条件值为 false，则该条插入记录违反了约束，不能插入到表。

```sqlite
CREATE TABLE table_name(
	... ,
	SALARY REAL CHECK(SALARY > 0), 
	...
);
```

#### 2.2.6. 删除约束

​	使用 `ALTER TABLE` 语句，并指定要删除的约束类型。

##### 删除主键约束

```sqlite
ALTER TABLE table_name
DROP CONSTRAINT primary_key_name;
```

##### 删除唯一约束

```sqlite
ALTER TABLE table_name
DROP CONSTRAINT unique_constraint_name;
```

##### 删除外键约束

```sqlite
ALTER TABLE table_name
DROP CONSTRAINT foreign_key_constraint_name;
```

### 2.3. SQLite Join

​	用于结合两个或多个数据库中表的记录。

#### 2.3.1. CROSS JOIN - 交叉连接

​	把第一个表的每一行与第二个表的每一行进行匹配。如果两个表分别有 x 和 y 行，则结果表有 x*y 行。

```sqlite
SELECT ... FROM table1 CROSS JOIN table2 ...;
```

#### 2.3.2. INNER JOIN - 内连接

​	根据连接谓词结合两个表的列值来创建一个新的结果表。

```sqlite
SELECT ... FROM table1 [INNER] JOIN table2 ON conditional_expression ...;
```

​	为了避免冗余，并保持较短的措辞，可以使用 `USING` 表达式声明内连接的条件。

```sqlite
SELECT ... FROM table1 JOIN table2 USING ( condition ... );
```

​	自然连接（NATURAL JOIN）类似于 `JOIN...USING` ，只是它会自动测试两个表中的每一列的相同值。

```sqlite
SELECT ... FROM table1 NATURAL JOIN table2 ...
```

#### 2.3.3. OUTER JOIN - 外连接

​	是内连接的扩展，SQLite 只支持左外连接。声明方法与内连接相同，但是外连接的结果表会合并任何未连接的行，并使用 NULL 填充外连接的列。

```sqlite
SELECT ... FROM table1 LEFT OUTER JOIN table2 ON conditional_expression ...;
```

​	为了避免冗余，并保持较短的措辞，可以使用 `USING` 表达式声明内连接的条件。

```sqlite
SELECT ... FROM table1 LEFT OUTER JOIN table2 USING ( condition ... );
```

### 2.4. SQLite Unions 子句

​	用于合并两个或多个 `SELECT` 语句的结果。每个 `SELECT` 所选择的列必须数目相同、数据类型相同、顺序相同，长度不需要相同。

#### 2.4.1. UNION

```sqlite
SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]

UNION

SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]
```

#### 2.4.2. UNION ALL

​	用于结合两个 `SELECT` 语句的结果，包括重复行。

```sqlite
SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]

UNION ALL

SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]
```

### 2.5. SQLite NULL

​	用来表示一个缺失值的项，但是这个项的类型是已知的。

### 2.6. SQLite Alias

​	用于暂时把表或列重命名为另一个名字，这被称为别名。

#### 2.6.1. 表别名

```sqlite
SELECT column1, column2, ...
FROM table_name AS alias_name
WHERE [condition];
```

#### 2.6.2. 列别名

```
SELECT column1 AS alias_name
FROM table_name
WHERE [condition];
```

### 2.7. SQLite Trigger

​	触发器是数据库的回调函数，会在指定的数据库事件发生时自动执行。

- 可以在特定的数据库表发生 `DELETE` 、`INSERT` 或 `UPDATE` 时触发，或在一个或多个指定表的列发生更新时触发；
- 只支持 `FOR EACH ROW` 触发器，没有 `FOR EACH STATEMENT` 触发器；
- `WHEN` 子句和触发器动作可能访问使用表单 `NEW.column-name` 和 `OLD.column-name` 的引用插入、删除或更新的行元素；
- 如果提供 `WHEN` 子句，则只针对 `WHEN` 子句为真的指定行执行 SQL 语句；如果没有，则针对所有行执行 SQL 语句；
- `BEFORE` 或 `AFTER` 关键字决定何时执行触发器动作；
- 当触发器相关联的表删除时，自动删除触发器；
- 要修改的表必须存在于同一数据库中，作为数据库被附加的表或视图，且必须只使用 `tablename`，而不是 `database.tablename`；
- SQL 函数 `RAISE()` 用于在触发器程序中抛出异常。

#### 2.7.1. 语法

```sqlite
CREATE TRIGGER trigger_name [BEFORE|AFTER] event_name
ON table_name
BEGIN
	-- 触发器逻辑
END；
```

#### 2.7.2. 列出触发器

​	可以从 `sqlite_master` 表中列出所有触发器。

```sqlite
SELECT name FROM sqlite_master
WHERE type = 'trigger';
```

​	如果需要列出特定表上的触发器，可以使用 `AND` 子句连接表名。

```sqlite
SELECT name FROM sqlite_master
WHERE type = 'trigger' AND tbl_name = 'table_name';
```

#### 2.7.3. 删除触发器

```sqlite
DROP TRIGGER trigger_name;
```

### 2.8. SQLite Index

​	索引是一种特殊的查找表，用来加快数据检索，但会减慢数据插入。

#### 2.8.1. CREATE INDEX

```sqlite
CREATE INDEX index_name ON table_name;
```

##### 单列索引

```sqlite
CREATE INDEX index_name
ON table_name (column_name);
```

##### 唯一索引

```sqlite
CREATE UNIQUE INDEX index_name
ON table_name (column_name);
```

##### 组合索引

```sqlite
CREATE INDEX index_name
ON table_name (column1, column2);
```

##### 隐式索引

​	在创建对象时，由数据库服务器自动创建的索引。索引自动创建为主键约束与唯一约束。

**注意：**可以使用 `.indices` 列出表上所有可用的索引。

#### 2.8.2. DROP INDEX

​	用于删除索引。

```
DROP INDEX index_name;
```

#### 2.9. SQLite Indexed By

​	规定必须需要命名的索引来查找表。如果索引名不存在或不能用于查询，SQLite 语句准备失败。

```sqlite
SELECT|DELETE|UPDATE column1, column2, ...
FROM table_name
INDEXED BY (index_name)
WHERE ( conditon );
```

​	也可以使用 `NOT INDEXED` 子句规定不使用索引访问前面的表，包括不适用由 `UNIQUE` 和 `PRIMARY KEY` 约束隐式创建的索引。但是即使指定了 `NOT INDEXED`，`INTEGER PRIMARY KEY` 仍然可以被用于查找条目。

### 2.10. SQLite Alter

​	不通过执行一个完整的转储和数据的重载来修改已有的表。仅支持重命名表和在已有的表中添加列。

#### 2.10.1. 重命名表

```sqlite
ALTER TABLE database_name.table_name RENAME TO new_table_name;
```

#### 2.10.2. 添加列

​	新添加的列以 NULL 填充。

```sqlite
ALTER TABLE database_name.table_name ADD COLUMN column_def...;
```

### 2.11. SQLite Truncate Table

​	SQLite 没有截断表的命令，但是可以使用 `DELETE` 删除表中全部数据。

#### 2.11.1. 删除数据

​	这种方法无法将递增数归零。

```sqlite
DELETE FROM table_name;
```

#### 2.11.2. 删除递增数

​	当数据表中包含自增列是，会自动建立一个名为 `sqlite_sequence` 的表，这个表包含两个列：`name` 和 `seq`。`name` 记录自增列所在的表，`seq` 记录当前序号。如果想把某个自增列的序号归零，只需要修改 `sqlite_sequence` 表即可。

```sqlite
DELETE FROM sqlite_sequence WHERE name = 'table_name';
```

### 2.12. SQLite View

​	视图是一个通过相关的名称存储在数据库中的 SQL 语句，实际上是一个以预定义的 SQLite 查村形式存在的表的组合。

​	SQLite 视图是只读的，因此无法在视图执行修改语句，但是可以在视图上创建一个触发器，当尝试修改时触发，修改的行为在触发器内定义。

#### 2.12.1. 创建视图

```sqlite
CREATE [TEMP | TEMPORARY] VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE [ condition ];
```

#### 2.12.2. 删除视图

```sqlite
DROP VIEW view_name;
```

### 2.13. SQLite Transaction



