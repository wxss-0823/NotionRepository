# SQLite 教程

## 1. SQLite 基础教程

### 1.1. SQLite 简介

​		SQLite 是一个进程内的库，实现了自给自足的、无服务器的、零配置的、事务性的 SQL 数据库引擎。SQLite 引擎不是一个独立的进程，可以按应用程序的需求进行静态或者动态连接，也可以直接访问其存储文件。

- 不需要一个单独的服务器进程或操作系统（无服务器的）；
- SQLite 不需要配置，这意味着不需要安装或管理；
- 一个完整的 SQLite 数据库是存储在一个单一的跨平台的磁盘文件；
- SQLite 非常小，是轻量级的，完全配置时小于 400 KB，省略可选功能配置时小于 250 KB；
- SQLite 是自给自足的，这意味着不需要任何外部的依赖；
- SQLite 事务是完全兼容 ACID 的，允许从多个进程或线程安全访问；
- SQLite 可以 UNIX 和 Windows 中运行。

### 1.2. SQLite 点命令

​		这些命令不以 `;` 结束：

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

​		SQLite 不区分大小写，但有些命令大小写敏感，例如：`GLOB` 和 `glob` 是不同的含义。

#### 1.3.2. 注释

​		SQLite 注释由两种表示方式：

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























































































































































## 2. SQLite3 高级教程



































