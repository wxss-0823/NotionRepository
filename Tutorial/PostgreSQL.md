# PostgreSQL 教程

## 1. PostgreSQL 数据类型

### 1.1. 数值类型

​	由 2 字节、4 字节或 8 字节的整数以及 4 字节或 8 字节的浮点数和可选精度的十进制数组成。

| 名字             | 存储长度 | 描述                 | 范围                                         |
| :--------------- | :------- | :------------------- | :------------------------------------------- |
| smallint         | 2 字节   | 小范围整数           | -32768 到 +32767                             |
| integer          | 4 字节   | 常用的整数           | -2147483648 到 +2147483647                   |
| bigint           | 8 字节   | 大范围整数           | -9223372036854775808 到 +9223372036854775807 |
| decimal          | 可变长   | 用户指定的精度，精确 | 小数点前 131072 位；小数点后 16383 位        |
| numeric          | 可变长   | 用户指定的精度，精确 | 小数点前 131072 位；小数点后 16383 位        |
| real             | 4 字节   | 可变精度，不精确     | 6 位十进制数字精度                           |
| double precision | 8 字节   | 可变精度，不精确     | 15 位十进制数字精度                          |
| smallserial      | 2 字节   | 自增的小范围整数     | 1 到 32767                                   |
| serial           | 4 字节   | 自增整数             | 1 到 2147483647                              |
| bigserial        | 8 字节   | 自增的大范围整数     | 1 到 9223372036854775807                     |

### 1.2. 货币类型

​	存储带有固定小数精度的货币金额。`numeric`、`int` 和 `bigint` 类型的值可以转换为 `money`，不建议使用浮点数来处理处理货币类型，因为存在舍入错误的可能性。

| 名字  | 存储容量 | 描述     | 范围                                           |
| :---- | :------- | :------- | :--------------------------------------------- |
| money | 8 字节   | 货币金额 | -92233720368547758.08 到 +92233720368547758.07 |

### 1.3. 字符类型

| 名称                             | 描述             |
| :------------------------------- | :--------------- |
| character varying(n), varchar(n) | 变长，有长度限制 |
| character(n), char(n)            | 定长，不足补空白 |
| text                             | 变长，无长度限制 |

### 1.4. 日期/时间类型

| 名字                                      | 存储空间 | 描述                     | 最低值        | 最高值        | 分辨率         |
| :---------------------------------------- | :------- | :----------------------- | :------------ | :------------ | :------------- |
| timestamp [ (*p*) ] [ without time zone ] | 8 字节   | 日期和时间(无时区)       | 4713 BC       | 294276 AD     | 1 毫秒 / 14 位 |
| timestamp [ (*p*) ] with time zone        | 8 字节   | 日期和时间，有时区       | 4713 BC       | 294276 AD     | 1 毫秒 / 14 位 |
| date                                      | 4 字节   | 只用于日期               | 4713 BC       | 5874897 AD    | 1 天           |
| time [ (*p*) ] [ without time zone ]      | 8 字节   | 只用于一日内时间         | 00:00:00      | 24:00:00      | 1 毫秒 / 14 位 |
| time [ (*p*) ] with time zone             | 12 字节  | 只用于一日内时间，带时区 | 00:00:00+1459 | 24:00:00-1459 | 1 毫秒 / 14 位 |
| interval [ *fields* ] [ (*p*) ]           | 12 字节  | 时间间隔                 | -178000000 年 | 178000000 年  | 1 毫秒 / 14 位 |

### 1.5. 布尔类型

| 名称    | 存储格式 | 描述       |
| :------ | :------- | :--------- |
| boolean | 1 字节   | true/false |

### 1.6. 枚举类型

​	枚举类型是一个包含静态和值的有序集合的数据类型。

```postgresql
CREATE TYPE mood AS ENUM ('value1', 'value2', 'value3');
```

### 1.7. 几何类型

| 名字    | 存储空间    | 说明                   | 表现形式               |
| :------ | :---------- | :--------------------- | :--------------------- |
| point   | 16 字节     | 平面中的点             | (x,y)                  |
| line    | 32 字节     | (无穷)直线(未完全实现) | ((x1,y1),(x2,y2))      |
| lseg    | 32 字节     | (有限)线段             | ((x1,y1),(x2,y2))      |
| box     | 32 字节     | 矩形                   | ((x1,y1),(x2,y2))      |
| path    | 16+16n 字节 | 闭合路径(与多边形类似) | ((x1,y1),...)          |
| path    | 16+16n 字节 | 开放路径               | [(x1,y1),...]          |
| polygon | 40+16n 字节 | 多边形(与闭合路径相似) | ((x1,y1),...)          |
| circle  | 24 字节     | 圆                     | <(x,y),r> (圆心和半径) |

### 1.8. 网络地址类型

​	PostgreSQL 提供用于存储 IPv4 、IPv6 、MAC 地址的数据类型，用这些数据类型存储网络地址比用纯文本类型好， 因为这些类型提供输入错误检查和特殊的操作和功能。

| 名字    | 存储空间     | 描述                    |
| :------ | :----------- | :---------------------- |
| cidr    | 7 或 19 字节 | IPv4 或 IPv6 网络       |
| inet    | 7 或 19 字节 | IPv4 或 IPv6 主机和网络 |
| macaddr | 6 字节       | MAC 地址                |

### 1.9. 位串类型

​	位串就是一串 1 和 0 的字符串。它们可以用于存储和直观化位掩码。 

- `bit(n)`：类型的数据必须准确匹配长度 n， 试图存储短些或者长一些的数据都是错误的；
- `bit varying(n)`：类型数据是最长 n 的变长类型，更长的串会被拒绝。
- 写一个没有长度的 `bit` 等效于 `bit(1)`，而没有长度的 `bit varying` 意思是没有长度限制。

### 1.10. 文本搜索类型

​	全文检索即通过自然语言文档的集合来找到那些匹配一个查询的检索。

| 名字     | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| tsvector | 是一个无重复值的 `lexemes` 排序列表， 即一些同一个词的不同变种的标准化 |
| tsquery  | 存储用于检索的词汇，并且使用布尔操作符 `&`，`|` 和 `!` 来组合它们，括号用来强调操作符的分组 |

### 1.11. UUID 类型

​	`uuid` 数据类型用来存储 RFC 4122，ISO/IEF 9834-8:2005 以及相关标准定义的通用唯一标识符。这个标识符是一个由算法产生的 **128** 位标识符，使它不可能在已知使用相同算法的模块中和其他方式产生的标识符相同。

​	`UUID` 被写成一个小写十六进制数字的序列，由分字符分成几组：一组8位数字 + 3组4位数字 + 一组12位数字，总共 32 个数字代表 128 位。

```text
a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11
```

### 1.12. XML 类型

​	`xml` 数据类型可以用于存储XML数据。 将 XML 数据存到 text 类型中的优势在于它能够为结构良好性来检查输入值， 并且还支持函数对其进行类型安全性检查。 要使用这个数据类型，编译时必须使用 `configure --with-libxml`。

#### 1.12.1. 创建XML值

​	`xml` 可以存储由 XML 标准中的 `XMLDecl? content` 定义的内容片段，这意味着内容片段可以有多个顶级元素或字符节点。 

​	`xmlvalue IS DOCUMENT` 表达式可以用来判断一个特定的 `xml` 值是一个完整的文件还是内容片段。

```postgresql
XMLPARSE (DOCUMENT '<?xml version="1.0"?><book><title>Manual</title><chapter>...</chapter></book>')
XMLPARSE (CONTENT 'abc<foo>bar</foo><bar>foo</bar>')
```

### 1.13. JSON 类型

​	`json` 数据类型可以用来存储 JSON（JavaScript Object Notation）数据， 这样的数据也可以存储为 text，但是 `json` 数据类型更有利于检查每个存储的数值是可用的 JSON 值。

相关的函数处理 `json` 数据

- `array_to_json("json")`：将数组转化为 `json`；
- `row_to_json`：将行转化为 `json`。

### 1.14. 数组类型

​	PostgreSQL 允许将字段定义成变长的多维数组，数组类型可以是任何基本类型或用户定义类型，枚举类型或复合类型。

#### 1.14.1. 声明数组

​	创建表的时候，我们可以声明数组，方式如下：

```postgresql
CREATE TABLE sal_emp (
    name            text,
    pay_by_quarter  integer [ARRAY] [],
    schedule        text[][]
);
```

#### 1.14.2. 插入值

​	插入值使用花括号 `{}`，元素在 `{}` 处使用逗号隔开。

```postgresql
INSERT INTO sal_emp
    VALUES ('Bill',
    '{10000, 10000, 10000, 10000}',
    '{{"meeting", "lunch"}, {"training", "presentation"}}');
```

#### 1.14.3. 访问数组

```postgresql
SELECT name FROM sal_emp WHERE pay_by_quarter[1] <> pay_by_quarter[2];
```

#### 1.14.4. 修改数组

```postgresql
UPDATE sal_emp SET pay_by_quarter = '{25000,25000,27000,27000}' WHERE name = 'Carol';
-- 或者使用构造器语法
UPDATE sal_emp SET pay_by_quarter = ARRAY[25000,25000,27000,27000] WHERE name = 'Carol';
```

#### 1.14.5. 数组中检索

​	搜索数组中的某一个值，需要遍历该数组。

```postgresql
SELECT * FROM sal_emp WHERE pay_by_quarter[1] = 10000 OR
                            pay_by_quarter[2] = 10000 OR
                            pay_by_quarter[3] = 10000 OR
                            pay_by_quarter[4] = 10000;
```

​	也可以找出数组中所有元素都等于 10000 的行。

```postgresql
SELECT * FROM sal_emp WHERE 10000 = ALL (pay_by_quarter);
-- 或者使用 generate_subscript 函数
SELECT * FROM
   (SELECT pay_by_quarter,
           generate_subscripts(pay_by_quarter, 1) AS s
      FROM sal_emp) AS foo
 WHERE pay_by_quarter[s] = 10000;
```

### 1.15. 复合类型

#### 1.15.1. 声明复合类型

```postgresql
CREATE TYPE complex AS (
    r       double precision,
    i       double precision
);
```

#### 1.15.2. 复合类型值输入

​	要以文本常量书写复合类型值，在圆括弧里包围字段值并且用逗号分隔他们。

```postgresql
'( val1 , val2 , ... )'
```

#### 1.15.3. 访问复合类型

​	要访问复合类型字段的一个域，需要写出一个点以及域的名字， 必须用圆括弧来避免分析器混淆。

```postgresql
SELECT (item).name FROM on_hand WHERE (item).price > 9.99;
```

### 1.16. 范围类型

​	范围数据类型代表着某一元素类型在一定范围内的值。内置的范围类型有：

- `int4range`：`integer` 的范围；
- `int8range`：`bigint` 的范围；
- `numrange`：`numeric`的范围；
- `tsrange`：`timestamp without time zone` 的范围；
- `tstzrange`：`timestamp with time zone` 的范围；
- `daterange`：`date` 的范围。

### 1.17. 对象标识符类型

​	PostgreSQL 在内部使用对象标识符（OID）作为各种系统表的主键。同时，系统不会给用户创建的表增加一个 OID 系统字段，除非在建表时声明了 `WITH OIDS` 或者配置参数`default_with_oids` 设置为开启。

| 名字          | 引用         | 描述               | 数值例子                              |
| :------------ | :----------- | :----------------- | :------------------------------------ |
| oid           | 任意         | 数字化的对象标识符 | 564182                                |
| regproc       | pg_proc      | 函数名字           | sum                                   |
| regprocedure  | pg_proc      | 带参数类型的函数   | sum(int4)                             |
| regoper       | pg_operator  | 操作符名           | +                                     |
| regoperator   | pg_operator  | 带参数类型的操作符 | *(integer,integer) 或 -(NONE,integer) |
| regclass      | pg_class     | 关系名             | pg_type                               |
| regtype       | pg_type      | 数据类型名         | integer                               |
| regconfig     | pg_ts_config | 文本搜索配置       | english                               |
| regdictionary | pg_ts_dict   | 文本搜索字典       | simple                                |

### 1.18. 伪类型

​	PostgreSQL 类型系统包含一系列特殊用途的条目， 它们按照类别来说叫做伪类型。伪类型不能作为字段的数据类型， 但是它可以用于声明一个函数的参数或者结果类型。 伪类型在一个函数不只是简单地接受并返回某种 SQL 数据类型的情况下很有用。

| 名字             | 描述                                                |
| :--------------- | :-------------------------------------------------- |
| any              | 表示一个函数接受任何输入数据类型                    |
| anyelement       | 表示一个函数接受任何数据类型                        |
| anyarray         | 表示一个函数接受任意数组数据类型                    |
| anynonarray      | 表示一个函数接受任意非数组数据类型                  |
| anyenum          | 表示一个函数接受任意枚举数据类型                    |
| anyrange         | 表示一个函数接受任意范围数据类型                    |
| cstring          | 表示一个函数接受或者返回一个空结尾的 C 字符串       |
| internal         | 表示一个函数接受或者返回一种服务器内部的数据类型    |
| language_handler | 一个过程语言调用处理器声明为返回 `language_handler` |
| fdw_handler      | 一个外部数据封装器声明为返回 `fdw_handler`          |
| record           | 标识一个函数返回一个未声明的行类型                  |
| trigger          | 一个触发器函数声明为返回 `trigger`                  |
| void             | 表示一个函数不返回数值                              |
| opaque           | 一个已经过时的类型，以前用于所有上面这些用途        |

## 2. PostgreSQL 常用指令

### 2.1. 创建数据库

```postgresql
CREATE DATABASE dbname;
```

### 2.2. 选择数据库

```postgresql
\l 								-- 查看已经存在的数据库
\c database_name;	-- 进入数据库
```

### 2.3. 删除数据库

```postgresql
DROP DATABASE [IF EXISTS] database_name;
```

### 2.4. 创建表格

```postgresql
CREATE TABLE table_name(
   column1 datatype,
   column2 datatype,
   column3 datatype,
   .....
   columnN datatype,
   PRIMARY KEY( column1, column2, ... )
);
```

### 2.5. 删除表格

```postgresql
DROP TABLE table_name;
```

### 2.6. 模式（SECHMA）

​	PostgreSQL 模式（SCHEMA）可以看着是一个表的集合，一个模式可以包含视图、索引、数据类型、函数和操作符等。

- 允许多个用户使用一个数据库并且不会互相干扰；
- 将数据库对象组织成逻辑组以便更容易管理；
- 第三方应用的对象可以放在独立的模式中，这样它们就不会与其他对象的名称发生冲突。

```postgresql
CREATE SCHEMA myschema (
	...
);
```

### 2.7. INSERT INTO 语句

​	PostgreSQL `INSERT INTO` 语句用于向表中插入新记录，可以插入一行，也可以同时插入多行。

```postgresql
INSERT INTO TABLE_NAME (column1, column2, column3,...columnN) VALUES (value1, value2, value3,...valueN), (value1, value2, value3,...valueN), ... ;
```

### 2.8. SELECT 语句

​	PostgreSQL `SELECT` 语句用于从数据库中选取数据。

```postgresql
SELECT column1, column2,...columnN FROM table_name;
```

### 2.9. 运算符

#### 2.9.1. 算术运算符

| 运算符 |        描述        |
| :----: | :----------------: |
|   +    |         加         |
|   -    |         减         |
|   *    |         乘         |
|   /    |         除         |
|   %    |     模（取余）     |
|   ^    |        指数        |
|  \|/   |       平方根       |
| \|\|/  |       立方根       |
|   !    |        阶乘        |
|   !!   | 阶乘（前缀操作符） |

#### 2.9.2. 比较运算符

| 运算符 |   描述   |
| :----: | :------: |
|   =    |   等于   |
|   !=   |  不等于  |
|   <>   |  不等于  |
|   >    |   大于   |
|   <    |   小于   |
|   >=   | 大于等于 |
|   <=   | 小于等于 |

#### 2.9.3. 逻辑运算符

| 运算符 |     描述     |
| :----: | :----------: |
|  AND   | 逻辑与运算符 |
|  NOT   | 逻辑非运算符 |
|   OR   | 逻辑或运算符 |

#### 2.9.4. 位运算符

| 运算符 | 描述                                 |
| :----- | :----------------------------------- |
| &      | 按位与操作，按二进制位进行"与"运算   |
| \|     | 按位或运算符，按二进制位进行"或"运算 |
| #      | 异或运算符，按二进制位进行"异或"运算 |
| ~      | 取反运算符，按二进制位进行"取反"运算 |
| <<     | 二进制左移运算符                     |
| >>     | 二进制右移运算符                     |

### 2.10. 表达式

```postgresql
SELECT column1, column2, columnN
FROM table_name
WHERE [CONDITION | EXPRESSION];
```

### 2.11. WHERE 子句

```postgresql
SELECT column1, column2, columnN
FROM table_name
WHERE [condition1];
```

### 2.12. AND & OR 运算符

#### 2.12.1. AND

​	`AND` 运算符表示一个或者多个条件必须同时成立。

```postgresql
SELECT column1, column2, columnN
FROM table_name
WHERE [condition1] AND [condition2]...AND [conditionN];
```

#### 2.12.2. OR

​	`OR` 运算符表示多个条件中只需满足其中任意一个即可。

```postgresql
SELECT column1, column2, columnN
FROM table_name
WHERE [condition1] OR [condition2]...OR [conditionN];
```

### 2.13. UPDATE 语句

​	用于更新在 PostgreSQL 数据库中的数据。

```postgresql
UPDATE table_name
SET column1 = value1, column2 = value2...., columnN = valueN
WHERE [condition];
```

### 2.14. DELETE 语句

```postgresql
DELETE FROM table_name WHERE [condition];
```

### 2.15. LIKE 子句

​	用于获取包含某些字符的数据，如果没有使用通配符，`LIKE` 子句和等号 `=` 得到的结果是一样的。

- `%`：百分号，匹配任意字符； 
- `_`：下划线，匹配一个字符。

```postgresql
SELECT FROM table_name WHERE column LIKE 'XXXX%';
-- 或者
SELECT FROM table_name WHERE column LIKE '%XXXX%';
-- 或者
SELECT FROM table_name WHERE column LIKE 'XXXX_';
-- 或者
SELECT FROM table_name WHERE column LIKE '_XXXX';
-- 或者
SELECT FROM table_name WHERE column LIKE '_XXXX_';
```

### 2.16. LIMIT 子句

​	用于限制 SELECT 语句中查询的数据的数量。

```postgresql
SELECT column1, column2, columnN
FROM table_name
LIMIT [no of rows] OFFSET [row num];
```

### 2.17. ORDER BY 语句

```postgresql
SELECT column-list
FROM table_name
[WHERE condition]
[ORDER BY column1, column2, .. columnN] [ASC | DESC];
```

### 2.18. GROUP BY 语句

​	在 PostgreSQL 中，`GROUP BY` 语句和 `SELECT` 语句一起使用，用来对相同的数据进行分组。`GROUP BY` 在一个 `SELECT` 语句中，放在 `WHERE` 子句的后面，`ORDER BY` 子句的前面。

```postgresql
SELECT column-list
FROM table_name
WHERE [ conditions ]
GROUP BY column1, column2....columnN
ORDER BY column1, column2....columnN
```

### 2.19. WITH 子句

​	在 PostgreSQL 中， `WITH` 子句提供了一种编写辅助语句的方法，以便在更大的查询中使用，这些语句通常称为通用表达式（Common Table Express，CTE），也可以当做一个为查询而存在的临时表。`WITH` 子句在多次执行子查询时特别有用，允许在查询中通过它的名称多次引用他，在使用前必须先定义。

```postgresql
WITH
	name_for_summary_data AS (
  	SELECT Statement)
  SELECT columns
  FROM name_for_summary_data
  WHERE conditons <=> (
  	SELECT column
 		FROM name_for_summary_data)
 	[ORDER BY columns]
```

### 2.20. HAVING 子句

​	用于筛选分组后的各组数据，在由 `GROUP BY` 子句创建的分组上设置条件。`HAVING` 子句必须放置在 `GROUP BY` 子句后面，`ORDER BY` 子句前面。

```postgresql
SELECT column-list
FROM table_name
WHERE [conditions]
GROUP BY column-list
HAVING [conditions]
ORDER BY column-list
```

### 2.21. DISTINCT 关键字

​	用于去除重复记录，只获得唯一的记录。

```postgresql
SELECT DISTINCT column1, column2, ... , columnN
FROM table_name
WHERE [condition]
```

## 3. PostgreSQL 高级指令

### 3.1. 约束

​	用于规定表中的数据规则，如果存在违反约束的数据行为，行为会被约束终止。

#### 3.1.1. NOT NULL 约束

​	默认情况下，列可以保存为 NULL 值，如果不想某列有 NULL 值，需要在该列定义此约束，指定在该列上不允许 NULL 值。NULL 与没有数据不一样，它表示未知的数据类型。

#### 3.1.2. UNIQUE 约束

​	用于设置列是唯一的，避免同一列出现重复值。

#### 3.1.3. PRIMARY KEY 约束

​	称为主键，是数据表中每一条记录的唯一标识，一张表只能由一个 `PRIMARY KEY`。

#### 3.1.4. FOREIGN KEY 约束

​	外键约束，指定列中的值必须匹配另一个表中的某一行中出现的值。通常一个表中 `FOREIGN KEY` 指向另一个表中 `UNIQUE KEY`，即维护相关表之间的引用完整性。

#### 3.1.5. CHECK 约束

​	保证列中的所有值满足某一条件，即对输入一条记录进行检查。

#### 3.1.6. EXCLUSION 约束

​	确保当满足所有指定的运算时，不插入数据。

```postgresql
CREATE TABLE table_name (
	... ,
	EXCLUDE USING gist
	( condition1 ,
	conditon2 )
);
```

**注意：**Gist（Generalized Search Tree），即通用搜索树。

#### 3.1.7. 删除约束

​	删除约束必须指导约束名称，使用 `\d table_name` 查找系统生成的名称。

```postgresql
ALTER TABLE table_name DROP CONSTRAINT some_name;
```

### 3.2. JOIN

​	用于把来自两个或多个表的行结合起来，基于这些表之间的共同字段。

#### 3.2.1. CROSS JOIN

​	交叉连接把第一个表的每一行与第二个表的每一行进行匹配，产生 n*m 的表。

```postgresql
SELECT ... FROM table1 CROSS JOIN table2 ...
```

#### 3.2.2. INNER JOIN

​	根据连接谓词结合两个表的列值来创建一个新的结果表，查询会找出所有满足连接谓词的匹配对。

```postgresql
SELECT table1.column1, talbe2.column2 ...
FROM table1
INNER JOIN table2
ON table1.common_filed = table2.common_filed;
```

#### 3.2.3. OUTER JOIN

​	外部连接是内部连接的扩展，用于输出内部连接无法输出的行。

##### LEFT OUTER JOIN

​	左表被选择的行，即使没有匹配也会出现在结果表中。

```postgresql
SELECT ... FROM table1 LEFT OUTER JOIN table2 ON conditional_expression ...
```

##### RIGHT OUTER JOIN

​	右表被选择的行，即使没有匹配也会出现在结果表中。

```postgresql
SELECT ... FROM table1 RIGHT OUTER JOIN table2 ON conditional_expression ...
```

##### FULL OUTER JOIN

​	全外连接会将所有表被选择的行，即使没有匹配都显示的结果表中。

```postgresql
SELECT ... FROM talbe1 FULL OUTER JOIN table2 ON conditional_expression ...
```

### 3.3. UNION 操作符

​	用于合并两个或多个 `SELECT` 语句的结果。每个结果表必须拥有相同数量的列，相似的数据类型，和相同的列顺序。

#### 3.3.1. UNION

```postgresql
SELECT column1 [, column2]
FROM table1 [, table2]
[WHERE conditon]

UNION

SELECT column1 [, column2]
FROM table1 [, table2]
[WHERE conditon];
```

**注意：**`UNION` 操作符会将重复的行删除。

#### 3.3.2. UNION ALL

```postgresql
SELECT column1 [, column2]
FROM table1 [, table2]
[WHERE conditon]

UNION ALL

SELECT column1 [, column2]
FROM table1 [, table2]
[WHERE conditon];
```

**注意：**`UNION ALL` 操作符不会删除重复的行。

### 3.4. NULL 值

​	NULL 值代表遗漏的未知数据，默认地，表的列可以存放 NULL 值。

#### 3.4.1. IS NOT NULL

​	筛选表中不为空的值。

#### 3.4.2. IS NULL

​	筛选表中为空的值。

### 3.5. 别名

​	可以用 SQL 重命名一张表或者一个字段的名称，这个名称就叫做该表或该字段的别名，创建别名是为了让表名和列名可读性更强。

```postgresql
SELECT column1, column2, ...
FROM table_name AS alias_name
WHERE [condition];
```

### 3.6. 触发器

​	触发器是数据库的回调函数，它会在数据库事件发生时自动执行/调用，

- PostgreSQL 触发器可以在几种情况下触发：
	- 执行操作之前；
	- 执行操作之后；
	- 更新操作。
- 触发器的 `FOR EACH ROW` 属性是可选的，如果选中，当操作修改时每行调用一次；相反，选中 `FOR EACH STATEMENT` 不选修改了多少航，每个语句标记的触发器执行一次；
- `WHEN` 子句和触发器操作在引用 `NEW.column-name` 和 `OLD.column-name` 表单插入、删除或更新时可以访问每一行元素；
- 如果存在 `WHEN` 子句，只会执行 `WHEN` 子句成立的那一行，如果有没有 `WHEN` 子句，会在每一行执行；
- `BEFORE` 或 `AFTER` 关键字决定何时执行触发器动作；
- 要修改的表必须存在于同一数据库中，作为触发器被附件的表或视图，且必须只使用 `table_name` ，而不是 `database.table_name`；
- 当创建约束触发器会指定约束选项，当约束触发器实现的约束被违反时，将抛出异常。

#### 3.6.1. 创建触发器

```postgresql
CREATE TRIGGER trigger_name [BEFORE|AFTER|INSTEAD OF] event_name
ON table_name
[
  -- 触发器逻辑......
];
```

####  3.6.2. 列出触发器

```postgresql
SELECT * FROM pg_trigger;
```

#### 3.6.3. 删除触发器

```postgresql
DROP trigger ${trigger_name} ON ${table_of_trigger_dependent};
```

### 3.7. 索引

​	索引是加速搜素引擎检索数据的一种特殊表查询。通过创建索引，下一次检索时将会加快速度。

#### 3.7.1. 创建索引

```postgresql
CREATE [UNIQUE] INDEX index_name 
ON table_name(column-list);
```

#### 3.7.2. 局部索引

```postgresql
CREATE [UNIQUE] INDEX index_name 
ON table_name(column-list)
WHERE condition;
```

#### 3.7.3. 隐式索引

​	在 PostgreSQL 中，隐式索引是在创建对象时，由数据库服务器自动创建的索引，这类索引通常为主键索引和唯一约束索引。其创建和管理是由 PostgreSQL 自动完成，用户不需要手动干预，这使得数据库管理变得更加简单和高效。

#### 3.7.4. 删除索引

```postgresql
DROP INDEX index_name;
```

### 3.8. ALTER TABLE

​	用于添加、修改，删除一张已经存在的表列，也可以用于添加和删除约束。

#### 3.8.1. 添加/删除列

```postgresql
ALTER TABLE table_name [ADD|DROP] COLUMN column_name;
```

#### 3.8.2. 修改列数据类型

```postgresql
ALTER TABLE table_name ALTER COLUMN column_name TYPE DATATYPE datatype_name;
```

#### 3.8.3. 添加列约束

```postgresql
-- 添加唯一约束
ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE (column-list);
-- 添加 CHECK 约束
ALTER TABLE table_name ADD CONSTRAINT constraint_name CHECK (condition);
```

#### 3.8.4. 添加主键约束

```postgresql
ALTER TABLE table_name ADD CONSTRAINT constraint_name PRIMARY KEY (column-list);
```

#### 3.8.5. 删除约束

```postgresql
ALTER TABLE table_name DROP CONSTRAINT constraint_name;
```

### 3.9. TRUNCATE TABLE

​	用于删除表中的数据，但不删除表的结构。

```postgresql
TRUNCATE TALBE table_name;
```

### 3.10. VIEW

​	视图是一个以预定义的 PostgreSQL 查询形式存在的表的组合，是一种虚拟表，可以从一个或多个表中创建。视图是只读的，但是可以在视图上创建触发器，当尝试修改视图时，在对应表中实现操作。

#### 3.10.1. 创建视图

```postgresql
CREATE [TEMP | TEMPORARY] VIEW view_name AS
SELECT column1, column2 ...
FROM table_name
WHERE [condition];
```

#### 3.10.2. 删除视图

```postgresql
DROP VIEW view_name;
```

### 3.11. TRANSACTION

​	事务是数据库管理系统执行过程中的一个逻辑单位，由一个有限的数据库操作序列构成。

- 为数据库操作序列提供了一个从失败中恢复到正常状态的办法，同时提供了数据库即使在正常状态下仍然能保持一致性的方法；
- 当多个应用程序在并发访问数据库时，可以提供一个隔离方法，防止互相之间的操作互相干扰。

#### 3.11.1. 开始事务

​	用于启动一个事务，一直执行下去，直到遇到下一个 `COMMIT` 或 `ROLLBACK` 命令。

```postgresql
BEGIN;
-- 或
BEGIN TRANSACTION;
```

#### 3.11.2. COMMIT 命令

​	用于把事务调用的更改保存到数据库中的事务命令，即确认事务。

```postgresql
COMMIT;
```

#### 3.11.3. ROLLBACK 命令

​	用于撤销尚未保存到数据库的事务命令，即回滚事务。

```postgresql
ROLLBACK;
```

### 3.12. LOCK

​	锁主要是为了保护数据库数据的一致性，可以组织用户修改一行或整个表，一般用在并发较高的数据库中。多个用户访问数据库的时候，若对并发操作不加控制，就可能读取和存储不正确的数据，破坏数据库的一致性。

- 排它锁：Exclusion Locks，如果数据对象加上排它锁，则其他事务不能对它读取和修改；
- 共享锁：Share Locks，如果加上共享锁，则其他事务可以读取，但不能修改。

```postgresql
LOCK [ TABLE ] table_name IN lock_mode;
```

- `talbe_name`：要锁定的现有表的名称；
- `lock_mode`：锁定模式指定表被并发访问的行为，包含：`ACCESS SHARE`，`ROW SHARE`，`SHARE`，`ROW EXCLUSION`，`SHARE UPDATE EXCLUSION`，`SHARE ROW EXCLUSION`，`EXCLUSION`，`ACCESS EXCLUSION`。

#### 3.12.1. 死锁

​	当两个事务彼此等待对方完成其操作时，可能会发生死锁，PostgreSQL 可以检测它们，并以回滚结束它们。为了防止程序遇到这个问题，需要保证设计为以相同的顺序锁定对象。

#### 3.12.2. 咨询锁

​	PostgreSQL 提供了创建具有应用程序定义含义的锁的方法，这些被称为咨询锁。由于系统并不强制使用它们，所以正确使用它们取决于应用程序。

### 3.13. 子查询

​	指在 PostgreSQL 查询中的 `WHERE` 子句中嵌入查询语句，一个 `SELECT` 语句的查询结果能够作为另一个语句的输入值。

```postgresql
SELECT column_name [, column_name ]
FROM table1 [, table2 ]
WHERE column_name OPERATOR
	(SELECT column_name [, column_name]
	FROM table1 [, table2 ]
	[WHERE]);
```

### 3.14. AUTO INCREMENT

​	自动增长会在新记录插入表中时生成一个唯一的数字。PostgreSQL 使用序列来标识字段的自增长，数据类型由 `smallserial`，`serial`，`bigserial`，类似于 MySQL 数据库支持的 `AUTO_INCREMENT` 属性。

```postgresql
CREATE TABLE table_name (
	column SERIAL
);
```

### 3.15. PRIVILEGES

​	无论何时创建数据库对象，都会为其分配一个所有者，通常是执行 `CREATE` 语句的人，对于大多数类型的对象，初始状态是只有所有者（或超级用户）才能修改或删除对象，要允许其他角色或用户使用它，必须为该用户设置权限。

#### 3.15.1. GRANT

​	用于为用户分配权限。

```postgresql
GRANT privilege [, ...]
ON object [, ...]
TO { PUBLIC | GROUP group | username }
```

- `privilege`：可以是 `SELECT`，`INSERT`，`UPDATE`，`DELETE`，`RULE`，`ALL`；
- `object`：要授予访问权限的对象名称；
- `PUBLIC`：所有用户；
- `GROUP group`：为用户组授予权限；
- `username`：要授予权限的用户名。

#### 3.15.2. REVOKE

​	用于取消对用户的授权。

```postgresql
REVOKE privilege [, ...]
ON object [, ...]
TO { PUBLIC | GROUP group | username }
```

#### 3.15.3. 添加/删除用户

```postgresql
-- 添加用户
CREATE USER username WITH PASSWORD 'password';
-- 删除用户
DROP USER username;
```

## 4. 其他文档

​	详细的常用函数，进阶应用可以查看 [官方文档](https://www.postgresql.org/docs/) 。
