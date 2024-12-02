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

















