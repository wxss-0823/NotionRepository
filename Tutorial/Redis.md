# Redis 教程

## 1. Redis 配置

​	Redis 配置文件位于安装目录下，Windows 操作系统中名为 `redis.windows.conf`。可以通过命令 `CONFIG GET *` 查看全部的配置项，或者修改配置文件的项。

### 1.1. 读取配置

```shell
CONFIG GET CONFIG_SETTING_NAME
```

### 1.2. 写入配置

```shell
CONFIG SET CONFIG_SETTING_NAME NEW_CONFIG_VALUE
```

### 1.3. 参数说明

| 配置项                                                 | 说明                                                         |
| :----------------------------------------------------- | :----------------------------------------------------------- |
| `daemonize no`                                         | Redis 默认不是以守护进程的方式运行，可以通过该配置项修改，使用 yes 启用守护进程（Windows 不支持守护线程的配置为 no ） |
| `pidfile /var/run/redis.pid`                           | 当 Redis 以守护进程方式运行时，Redis 默认会把 pid 写入 /var/run/redis.pid 文件，可以通过 pidfile 指定 |
| `port 6379`                                            | 指定 Redis 监听端口，默认端口为 6379                         |
| `bind 127.0.0.1`                                       | 绑定的主机地址                                               |
| `timeout 300`                                          | 当客户端闲置多长秒后关闭连接，如果指定为 0 ，表示关闭该功能  |
| `loglevel notice`                                      | 指定日志记录级别，Redis 总共支持四个级别：debug、verbose、notice、warning，默认为 notice |
| `logfile stdout`                                       | 日志记录方式，默认为标准输出，如果配置 Redis 为守护进程方式运行，而这里又配置为日志记录方式为标准输出，则日志将会发送给 /dev/null |
| `databases 16`                                         | 设置数据库的数量，默认数据库为 0，可以使用 SELECT 命令在连接上指定数据库 id |
| `save <seconds> <changes>`                             | 指定在多长时间内，有多少次更新操作，就将数据同步到数据文件，可以多个条件配合 |
| `rdbcompression yes`                                   | 指定存储至本地数据库时是否压缩数据，默认为 yes，Redis 采用 LZF 压缩，如果为了节省 CPU 时间，可以关闭该选项，但会导致数据库文件变的巨大 |
| `dbfilename dump.rdb`                                  | 指定本地数据库文件名，默认值为 dump.rdb                      |
| `dir ./`                                               | 指定本地数据库存放目录                                       |
| `slaveof <masterip> <masterport>`                      | 设置当本机为 slave 服务时，设置 master 服务的 IP 地址及端口，在 Redis 启动时，它会自动从 master 进行数据同步 |
| `masterauth <master-password>`                         | 当 master 服务设置了密码保护时，slave 服务连接 master 的密码 |
| `requirepass foobared`                                 | 设置 Redis 连接密码，如果配置了连接密码，客户端在连接 Redis 时需要通过 `AUTH <password>` 命令提供密码，默认关闭 |
| ` maxclients 128`                                      | 设置同一时间最大客户端连接数，默认无限制，Redis 可以同时打开的客户端连接数为 Redis 进程可以打开的最大文件描述符数，如果设置 `maxclients 0`，表示不作限制，当客户端连接数到达限制时，Redis 会关闭新的连接并向客户端返回 `max number of clients reached` 错误信息 |
| `maxmemory <bytes>`                                    | 指定 Redis 最大内存限制，Redis 在启动时会把数据加载到内存中，达到最大内存后，Redis 会先尝试清除已到期或即将到期的 Key，当此方法处理后，仍然到达最大内存设置，将无法再进行写入操作，但仍然可以进行读取操作，Redis 新的 vm 机制，会把 Key 存放内存，Value 会存放在 swap 区 |
| `appendonly no`                                        | 指定是否在每次更新操作后进行日志记录，Redis 在默认情况下是异步的把数据写入磁盘，如果不开启，可能会在断电时导致一段时间内的数据丢失，因为 redis 本身同步数据文件是按上面 save 条件来同步的，所以有的数据会在一段时间内只存在于内存中，默认为 n |
| `appendfilename appendonly.aof`                        | 指定更新日志文件名，默认为 appendonly.aof                    |
| `appendfsync everysec`                                 | 指定更新日志条件，共有 3 个可选值：**no**：表示等操作系统进行数据缓存同步到磁盘（快）**always**：表示每次更新操作后手动调用 fsync() 将数据写到磁盘（慢，安全）**everysec**：表示每秒同步一次（折中，默认值） |
| `vm-enabled no`                                        | 指定是否启用虚拟内存机制，默认值为 no                        |
| `vm-swap-file /tmp/redis.swap`                         | 虚拟内存文件路径，默认值为 /tmp/redis.swap，不可多个 Redis 实例共享 |
| `vm-max-memory 0`                                      | 将所有大于 vm-max-memory 的数据存入虚拟内存，无论 vm-max-memory 设置多小，所有索引数据都是内存存储的，默认值为 0 |
| `vm-page-size 32`                                      | Redis swap 文件分成了很多的 page，一个对象可以保存在多个 page 上面，但一个 page 上不能被多个对象共享，vm-page-size 根据存储的数据大小来设定 |
| `vm-pages 134217728`                                   | 设置 swap 文件中的 page 数量，由于页表（一种表示页面空闲或使用的 bitmap）是在放在内存中的，在磁盘上每 8 个 pages 将消耗 1byte 的内存。 |
| `vm-max-threads 4`                                     | 设置访问 swap 文件的线程数，最好不要超过机器的核数，如果设置为 0，那么所有对 swap 文件的操作都是串行的，可能会造成比较长时间的延迟，默认值为 4 |
| `glueoutputbuf yes`                                    | 设置在向客户端应答时，是否把较小的包合并为一个包发送，默认为开启 |
| `hash-max-zipmap-entries 64 hash-max-zipmap-value 512` | 指定在超过一定的数量或者最大的元素超过某一临界值时，采用一种特殊的哈希算法 |
| `activerehashing yes`                                  | 指定是否激活重置哈希，默认为开启                             |
| `include /path/to/local.conf`                          | 指定包含其它的配置文件，可以在同一主机上多个 Redis 实例之间使用同一份配置文件，而同时各个实例又拥有自己的特定配置文件 |

## 2. Redis 数据类型

### 2.1. String

​	`string` 是 Redis 最基本的类型，是二进制安全的，意思是 `string` 可以包含任何数据，比如： jpg 图片或者序列化的对象；最大能存储 512 MB。

#### 2.1.1. 常用命令

- `SET key value`：设置键的值；
- `GET key`：获取键的值；
- `INCR key`：将键的值加 1；
- `DECR key`：将键的值减 1；
- `APPEND key value`：将值追加到键的值之后。

### 2.2. Hash

​	`hash` 是一个键值对集合，类似于一个小型 NoSQL 数据库。Redis `hash` 是一个 `string` 类型的 `field` 和 `value` 的映射表，适合用于存储对象，每个哈希最多可以存储 $2^{32}-1$ 个键值对。

#### 2.2.1. 常用命令

- `HSET key field value`：设置哈希表中字段的值；
- `HGET key field`：获取哈希表中字段的值；
- `HGETALL key`：获取哈希表中所有字段和值；
- `HDEL key field`：删除哈希表中的一个或多个字段。

### 2.3. List

​	`list`是简单的字符串列表，按照插入顺序排序，可以添加一个元素到列表的头部/左边，或者尾部/右边，列表最多可以存储 $2^{32} - 1$ 个元素。

#### 2.3.1. 常用命令

- `LPUSH key value`：将值插入到列表头部；
- `RPUSH key value`：将值插入到列表尾部；
- `LPOP key`：移出并获取列表的第一个元素；
- `RPOP key`：移出并获取列表的最后一个元素；
- `LRANGE key start stop`：获取列表在指定范围内的元素。

### 2.4. Set

​	`Set` 是 `string` 类型的无序集合，集合是通过哈希表实现的，所以添加，删除，查找的复杂度都是 O(1)，集合中最大的成员数为 $2^{32} - 1$ 。

#### 2.4.1. 常用命令

- `SADD key value`：向集合添加一个或多个成员；
- `SREM key value`：移除集合中的一个或多个成员；
- `SMEMBERS key`：返回集合中的所有成员；
- `SISMEMBER key value`：判断值是否是集合的成员。

### 2.5. zset

​	`zset` 和 `set` 一样也是 `string` 类型元素的集合，且不允许重复的成员。不同的是每个元素都会关联一个`double` 类型的分数，Redis 正是通过这些分数来为集合中的成员进行从小到大的排序。`zset` 的成员是唯一的，但分数（score）却可以重复。

#### 2.5.1. 常用命令

- `ZADD key score value`：向有序集合添加一个或多个成员，或更新已存在成员的分数；
- `ZRANGE key start stop [WITHSCORES]`：返回指定范围内的成员；
- `ZREM key value`：移除有序集合中的一个或多个成员；
- `ZSCORE key value`：返回有序集合中，成员的分数值；

## 3. Redis 命令

​	Redis 命令用于在 redis 服务上执行操作。

### 3.1. 键（key）

```shell
COMMAND KEY_NAME
```

| 命令                                        | 描述                                                         |
| ------------------------------------------- | :----------------------------------------------------------- |
| `DEL key`                                   | 该命令用于在 key 存在时删除 key                              |
| `DUMP key`                                  | 序列化给定 key ，并返回被序列化的值                          |
| `EXISTS key`                                | 检查给定 key 是否存在                                        |
| `EXPIRE key`                                | seconds 为给定 key 设置过期时间，以秒计                      |
| `EXPIREAT key timestamp`                    | EXPIREAT 的作用和 EXPIRE 类似，都用于为 key 设置过期时间。 不同在于 EXPIREAT 命令接受的时间参数是 UNIX 时间戳（unix timestamp） |
| `PEXPIRE key milliseconds`                  | 设置 key 的过期时间以毫秒计                                  |
| `PEXPIREAT key milliseconds-timestamp`      | 设置 key 过期时间的时间戳（unix timestamp）以毫秒计          |
| `KEYS pattern`                              | 查找所有符合给定 pattern 的 key                              |
| `MOVE key db`                               | 将当前数据库的 key 移动到给定的数据库 db 当中                |
| `PERSIST key`                               | 移除 key 的过期时间，key 将持久保持                          |
| `PTTL key`                                  | 以毫秒为单位返回 key 的剩余的过期时间                        |
| `TTL key`                                   | 以秒为单位，返回给定 key 的剩余生存时间（TTL, time to live） |
| `RANDOMKEY`                                 | 从当前数据库中随机返回一个 key                               |
| `RENAME key newkey`                         | 修改 key 的名称                                              |
| `RENAMENX key newkey`                       | 仅当 newkey 不存在时，将 key 改名为 newkey                   |
| `SCAN cursor [MATCH pattern] [COUNT count]` | 迭代数据库中的数据库键                                       |
| `TYPE key`                                  | 返回 key 所储存的值的类型                                    |

### 3.2. 字符串（String）

​	用于管理 Redis 字符串的值。

| 命令                             | 描述                                                         |
| -------------------------------- | ------------------------------------------------------------ |
| `SET key value`                  | 设置指定 key 的值                                            |
| `GET key`                        | 获取指定 key 的值                                            |
| `GETRANGE key start end`         | 返回 key 中字符串值的子字符串                                |
| `GETSET key value`               | 将给定的 key 值设为 value，并返回 key 的旧值                 |
| `GETBIT key offset`              | 对 key 所储存的字符串值，获取指定偏移量上的位                |
| `MGET key1 [key2 ...]`           | 获取一个或多个给定的 key 的值                                |
| `SETBIT key offset value`        | 对 key 所储存的字符串值，设置或清除指定偏移量上的位          |
| `SETEX key seconds value`        | 将值 value 关联到 key，并将 key 的过期时间设为 seconds       |
| `SETNX key value`                | 只有在 key 不存在时，设置 key 值                             |
| `SETRANGE key offset value`      | 用 value 参数覆写给定 key 所存储的字符串从指定偏移量开始的值 |
| `STRLEN key`                     | 返回 key 所储存的字符串值的长度                              |
| `MSET key value [key value ...]` | 同时设置一个或多个 key-value 对，当且仅当所有给定 key 不存在 |
| `PSETEX key milliseconds value`  | 设置 key-value 对的同时，设置 key 的生存时间，以 ms 为单位   |
| `INCR key`                       | 将 key 中储存的数字值加一                                    |
| `INCRBY key increment`           | 将 key 所储存的值加上给定的增量                              |
| `INCRBYFLOAT key increment`      | 将 key 所储存的值加上给定的浮点增量                          |
| `DECR key`                       | 将 key 中储存的数字值减一                                    |
| `DECRBY key decrement`           | 将 key 中储存的数字减去给定的减量                            |
| `APPEND key value`               | 如果 key 已经存在并且是一个字符串，将只当值追加到原来值的末尾 |

### 3.3. 哈希（Hash）

​	`hash` 是一个 `string` 类型的 `field`（字段）和 `value` 的映射表。每个 `hash` 最多储存 $2^{32}-1$ 个键值对。

| 命令                                             | 描述                                            |
| ------------------------------------------------ | ----------------------------------------------- |
| `HDEL key field1 [field2]`                       | 删除一个或多个哈希表字段                        |
| `HEXISTS key field`                              | 查看哈希表 key 中，指定字段是否存在             |
| `HGET key field`                                 | 获取存储在哈希表指定字段的值                    |
| `HGETALL key`                                    | 获取在哈希表中指定 key 的所有字段的值           |
| `HINCREBY key field increment`                   | 为哈希表 key 中指定字段的整数值增加 increment   |
| `HINCRBYFLOAT key field increment`               | 为哈希表 key 中的指定字段的整数值增加 increment |
| `HKEYS key`                                      | 获取哈希表中所有字段                            |
| `HLEN key`                                       | 获取哈希表中字段的数量                          |
| `HMGET key field1 [field2]`                      | 获取所有给定字段的值                            |
| `HMSET key field1 value1 [field2 value2]`        | 同时将多个 field-value 对设置到哈希表中         |
| `HSET key field value`                           | 将哈希表 key 中的字段 field 的值设为 value      |
| `HSETNX key field value`                         | 只有在字段 field 不存在时，设置哈希表的值       |
| `HVALS key`                                      | 获取哈希表中所有值                              |
| `HSCAN key cursor [MATCH pattern] [COUNT count]` | 迭代哈希表中的键值对                            |

### 3.4. 列表（List）

​	Redis 列表是简单的字符串列表，按照插入顺序排序，可以添加一个元素到列表的头部，或者尾部。一个列表最多可以包含 $2^{32}-1$ 个元素。

| 命令                                    | 描述                                                         |
| --------------------------------------- | ------------------------------------------------------------ |
| `BLPOP key1 [key2] timeout`             | 移出并获取列表的第一个元素，如果列表没有元素会阻塞列表，直到等待超时或发现可弹出的元素为止 |
| `BRPOP key1 [key2] timeout`             | 移出并获取列表的最后一个元素，如果列表没有元素会阻塞列表，直到等待超时或发现可弹出的元素为止 |
| `BRPOPLPUSH source destination timeout` | 从列表中弹出一个值，将弹出的元素插入到另外一个列表中并返回它，如果列表没有元素会阻塞列表，直到等待超时或发现可弹出的元素为止 |
| `LINDEX key index`                      | 通过索引获取列表中的元素                                     |
| `LINSERT key BEFROE|AFTER pivot value`  | 在列表的元素前或者后插入元素                                 |
| `LLEN key`                              | 获取列表长度                                                 |
| `LPOP key`                              | 移出并获取列表的第一个元素                                   |
| `LPUSH key value1 [value2]`             | 将一个或多个值插入到列表头部                                 |
| `LPUSHX key value`                      | 将一个值插入到已存在的列表头部                               |
| `LRANGE key start stop`                 | 获取列表指定范围内的元素                                     |
| `LREM key count value`                  | 移除列表元素                                                 |
| `LSET key index value`                  | 通过索引设置列表元素的值                                     |
| `LTRIM key start stop`                  | 对一个列表进行修剪（trim），不在指定区间内的元素都将被删除   |
| `RPOP key`                              | 移除列表的最后一个元素，返回值为移除的元素                   |
| `RPOPLPUSH source destination`          | 移除列表的最后一个元素，并将该元素添加到另一个列表并返回     |
| `RPUSH key value1 [value2]`             | 在列表中添加一个或多个值到列表尾部                           |
| `RPUSHX key value`                      | 为已存在的列表添加值                                         |

### 3.5. 集合（Set）

​	Redis 的 Set 是 String 类型的无序集合，集合成员是唯一的，这就意味着集合中不能出现重复的数据。集合对象的编码可以是 `intset` 或者 `hashtable`，最大成员数为 $2^{32}-1$ 。

| 命令                                             | 描述                                                |
| ------------------------------------------------ | --------------------------------------------------- |
| `SADD key member1 [member2]`                     | 向集合添加一个或多个成员                            |
| `SCARD key`                                      | 获取集合成员数                                      |
| `SDIFF key1 [key2]`                              | 返回第一个集合与其他集合之间的差集                  |
| `SDIFFSTORE destination key1 [key2]`             | 返回给定所有集合的差集并储存在 destination 中       |
| `SINTER key1 [key2]`                             | 返回给定所有集合的交集                              |
| `SINTERSOTRE destination key1 [key2]`            | 返回给定所有集合的交集并存储在 destination 中       |
| `SISMENBER key member`                           | 判断 member 元素是否是集合 key 的成员               |
| `SMEMBERS key`                                   | 返回集合中的所有成员                                |
| `SMOVE source destination member`                | 将 member 元素从 source 集合移动到 destination 集合 |
| `SPOP key`                                       | 移除并返回集合中的一个随机元素                      |
| `SRANDMEMBER key [count]`                        | 返回集合中一个或多个随机数                          |
| `SREM key member1 [member2]`                     | 移除集合中一个或多个成员                            |
| `SUNION key1 [key2]`                             | 返回所有给定集合的并集                              |
| `SUNIONSTORE destination key1 [key2]`            | 所有给定集合的并集储存在 destination 集合中         |
| `SSCAN key cursor [MATCH pattern] [COUNT count]` | 迭代集合中的元素                                    |

### 3.6. 有序集合（Sorted set）

​	Redis 有序集合和集合一样，也是 `string` 类型元素的集合，且不允许重复的成员；不同的是每个元素都会关联一个 `double` 类型的分数，通过这些分数来为集合中的成员进行从小到大的排序。有序集合的成员是唯一的，但是分数可以重复，最大成员数为 $2^{32}-1$ 。

| 命令                                             | 描述                                                         |
| ------------------------------------------------ | ------------------------------------------------------------ |
| `ZADD key score1 member1 [score2 member2]`       | 向有序集合添加一个或多个成员，或者更新已存在成员的分数       |
| `ZCARD key`                                      | 获取有序集合的成员数                                         |
| `ZCOUNT key min max`                             | 计算在有序集合中指定区间分数的成员数                         |
| `ZINCREBY key increment member`                  | 有序集合中对指定成员的分数加上增量 increment                 |
| `ZINTERSTORE destination numkeys key [key ...]`  | 计算给定的一个或多个有序集的交集并将结果存储在新的有序集合 destination 中 |
| `ZLEXCOUNT key min max`                          | 在有序集合中计算指定字典区间内成员数量                       |
| `ZRANGE key start stop [WITHSCORES]`             | 通过索引区间返回有序集合指定区间内的成员                     |
| `ZRANGEBYLEX key min max [LIMIT offset count]`   | 通过字典区间返回有序集合的成员                               |
| `ZRANGEBYSCORE key min max`                      | 通过分数返回有序集合指定区间内的成员                         |
| `ZRANK key member`                               | 返回有序集合中指定成员的索引                                 |
| `ZREM key member [member ...]`                   | 移除有序集合中的一个或多个成员                               |
| `ZREMRANGEBYLEX key min max`                     | 移除有序集合中给定字典区间的所有成员                         |
| `ZREMRANGEBYRANK key start stop`                 | 移除有序集合中给定的索引区间的所有成员                       |
| `ZREMRANGEBYSCORE key min max`                   | 移除有序集合中给定的分数区间的所有成员                       |
| `ZREVRANGE key start stop [WITHSCORES]`          | 返回有序集合中指定区间内的成员，通过索引，分数由高到低       |
| `ZREVRANGEBYSCORES key max min [WITHSCORES]`     | 返回有序集合中指定分数区间的成员，分数由高到低排序           |
| `ZREVRANK key memeber`                           | 返回有序集合中指定成员的排名，有序集成员按分数值递减排序     |
| `ZSCORE key member`                              | 返回有序集中，成员的分数值                                   |
| `ZUNIONSTORE destination numkeys key [key ...]`  | 计算给定的一个或多个有序集的并集，并存储在新的 key 中        |
| `ZSCAN key cursor [MATCH pattern] [COUNT count]` | 迭代有序集合中的元素，包括元素成员和元素分值                 |

### 3.7. HyperLogLog

​	Redis HyperLogLog 是用来做基数统计的算法，优点是在输入元素数量或体积非常大时，计算基数所需的空间是固定的，并且很小的。这与元素越多，内存耗费越多的集合形成鲜明对比。HyperLogLog 只会根据输入元素来计算基数，而不会储存输入元素本身，所以不能像集合那样，返回输入的各个元素。

#### 3.7.1. 基数

​	基数是指数据集中不重复元素的数量，基数估计就是在误差允许范围内，快速计算基数。

#### 3.7.2. 命令

| 命令                                        | 描述                              |
| ------------------------------------------- | --------------------------------- |
| `PFADD key element [element ...]`           | 添加指定元素到 HyperLogLog 中     |
| `PFCOUNT key [key ...]`                     | 返回给定 HyperLogLog 的基数估算值 |
| `PFMERGE destkey sourcekey [sourcekey ...]` | 将多个 HyperLogLog 合并为一个     |

### 3.8. 发布订阅

​	Redis 发布订阅（pub/sub）是一种消息通信模式：发信者（pub）发送消息，订阅者（sub）接收消息。Redis 客户端可以订阅任意数量的频道。

| 命令                                          | 描述                             |
| --------------------------------------------- | -------------------------------- |
| `PSUBSCRIBE pattern [pattern ...]`            | 订阅一个或多个符合给定模式的频道 |
| `PUBSUB subcommand [argument [argument ...]]` | 查看订阅与发布系统的状态         |
| `PUBLISH channel message`                     | 将信息发送到指定频道             |
| `PUNSUBSRIBE [pattern [pattern ...]]`         | 退订所有给定模式的频道           |
| `SUBSCRIBE channel [channel ...]`             | 订阅给定的一个或多个频道的信息   |
| `UNSUBSCRIBE [channel [channel ...]]`         | 退订给定的频道                   |

### 3.9. 事务

​	Redis 事务可以一次执行多个命令，并且带有以下三个保证：

- 批量操作在发送 `EXEC` 命令之前被放入队列缓存；
- 收到 `EXEC` 命令后进入事务执行，事务中任意命令执行失败，其余命令依然被执行；
- 在事务执行过程中，其他客户端提交的命令请求不会插入到事务执行命令序列中。

​	一个事务从开始到执行会经历：开始事务，命令入队，执行事务，三个阶段。

| 命令                  | 描述                                                         |
| --------------------- | ------------------------------------------------------------ |
| `MULTI`               | 标记一个事务块的开始                                         |
| `EXEC`                | 执行所有事务块的命令                                         |
| `DISCARD`             | 取消事务，放弃执行事务块内的所有命令                         |
| `WATCH key [key ...]` | 监视一个或多个 key，如果在事务执行之前，key 被其他命令改动，那么事务将被打断 |
| `UNWATCH`             | 取消 `WATCH` 命令对所有 key 的监视                           |

### 3.10. 脚本

​	Redis 脚本使用 Lua 解释器来执行，通过内嵌支持 Lua 环境。

| 命令                                               | 描述                                                   |
| -------------------------------------------------- | ------------------------------------------------------ |
| `EVAL script numkeys key [key ...] arg [arg ...]`  | 执行 Lua 脚本                                          |
| `EVALSHA sha1 numkeys key [key ...] arg [arg ...]` | 执行 Lua 脚本                                          |
| `SCRIPT EXISTS script [script ...]`                | 查看指定脚本是否已经被保存在缓存当中                   |
| `SCRIPT FLUSH`                                     | 从脚本缓存中移除所有脚本                               |
| `SCRIPT KILL`                                      | 杀死当前正在运行的 Lua 脚本                            |
| `SCRIPT LOAD script`                               | 将脚本 script 添加到脚本缓存中，但并不立即执行这个脚本 |

### 3.11. 连接

​	Redis 连接命令主要用于连接 Redis 服务

| 命令            | 描述               |
| --------------- | ------------------ |
| `AUTH password` | 验证密码是否正确   |
| `ECHO message`  | 打印字符串         |
| `PING`          | 查看服务是否运行   |
| `QUIT`          | 关闭当前连接       |
| `SELECT index`  | 切换到指定的数据库 |

### 3.12. 服务器

​	Redis 服务器命令主要用于管理 Redis 服务。

| 命令                                           | 描述                                                         |
| ---------------------------------------------- | ------------------------------------------------------------ |
| `BGREWRITEAOF`                                 | 异步执行一个 AOF（AppendOnly File）文件重写操作              |
| `BGSAVE`                                       | 在后台异步保存当前数据库的数据到磁盘                         |
| `CLIENT KILL [ip:port] [ID client-id]`         | 关闭客户端连接                                               |
| `CLIENT LIST`                                  | 获取连接到服务器的客户端连接列表                             |
| `CLIENT GETNAME`                               | 获取连接的名称                                               |
| `CLIENT PAUSE timeout`                         | 在指定时间内终止运行来自客户端的命令                         |
| `CLIENT SETNAME connection-name`               | 设置当前连接的名称                                           |
| `CLUSTER SLOTS`                                | 获取集群节点的映射数组                                       |
| `COMMAND`                                      | 获取 Redis 命令详情数组                                      |
| `COMMAND COUNT`                                | 获取 Redis 命令总数                                          |
| `COMMAND GETKEYS`                              | 获取给定命令的所有键（已删除）                               |
| `TIME`                                         | 返回当前服务器时间                                           |
| `COMMAND INFO command-name [command-name ...]` | 获取指定 Redis 命令描述的数组                                |
| `COFIG GET parameter`                          | 获取指定配置参数的值                                         |
| `CONFIG REWRITE`                               | 对启动 Redis 服务器时所指定的 redis.conf 配置文件进行改写    |
| `CONFIG SET paremeter value`                   | 修改 Redis 配置参数，无需重启                                |
| `CONFIG RESETSTAT`                             | 重置 `INFO` 命令中的某些统计数据                             |
| `DBSIZE`                                       | 返回当前数据库的 key 的数量                                  |
| `DEBUG OBJECT key`                             | 获取 key 的调试信息                                          |
| `DEBUG SEGFAULT`                               | 让 Redis 服务器崩溃                                          |
| `FLUSHALL`                                     | 删除所有数据库的所有 key                                     |
| `FLUSHDB`                                      | 删除当前数据库的所有 key                                     |
| `INFO [section]`                               | 获取 Redis 服务器的各种信息和统计数值                        |
| `LASTSAVE`                                     | 返回最近一次 Redis 成功将数据保存到磁盘上的时间，以 UNIX 时间戳格式表示 |
| `MONITOR`                                      | 实时打印出 Redis 服务器接收到的命令，调试用                  |
| `ROLE`                                         | 返回主从实例所属的角色                                       |
| `SAVE`                                         | 同步保存数据到磁盘                                           |
| `SHUTDOWN [NOSAVE] [SAVE]`                     | 异步保存数据到磁盘，并关闭服务器                             |
| `SLAVEOF host port`                            | 将当前服务器转变为指定服务器的从属服务器                     |
| `SLOWLOG subcommand [argument]`                | 管理 Redis 的慢日志                                          |
| `SYNC`                                         | 用于**复制功能**（replication）的内部命令                    |

### 3.13. GEO

​	Redis GEO 主要用于存储地理位置信息，并对存储的信息进行操作。

#### 3.13.1. geoadd

​	用于存储指定的地理空间位置，可以将一个或多个经度（longitude）、纬度（latitude）、位置名称（member），添加到指定的 key 中。

```shell
GEOADD key longitude latitude member [longitude latitude member ...]
```

#### 3.13.2. geopos

​	用于从给定的 key 中返回所有指定名称的位置，不存在的返回 `nil`。

```shell
GEOPOS key member [member ...]
```

#### 3.13.3. geodist

​	用于返回两个给定位置之间的距离。

```shell
GEODIST key member1 member2 [m|km|ft|mi]
```

#### 3.13.4. georadius、georadiusbymember

​	`georadius` 以给定的经纬度为中心，返回键包含的位置元素中，与中心距离不超过给定最大距离的所有位置元素，`georadiusbymember` 以给定的位置元素为中心。

```shell
GEORADIUS key longitude latitude radius m|km|ft|mi [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count] [ASC|DESC] [STORE key] [STOREDIST key]
GEORADIUSBYMEMBER key member radius m|km|ft|mi [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count] [ASC|DESC] [STORE key] [STOREDIST key]
```

#### 3.13.5. geohash

​	Redis GEO 使用 `geohash` 保存地理位置的坐标，`geohash` 用于获取一个或多个位置元素的坐标。

```shell
GEOHASH key member [member ...]
```

### 3.14. Stream

​	Redis Stream 主要用于消息队列（MQ，Message Queue），Redis 本身有一个发布订阅（pub/sub）来实现消息队列功能，但它有个缺点就是消息无法持久化，无法记录历史消息，而 Stream 提供了消息持久化和主备复制功能，可以让任何客户端访问任何时刻的数据，并且能记住每一个客户端的访问位置，还能保证信息不丢失。

​	Stream 有一个消息链表，将所有加入的消息都串起来， 每个消息都有一个唯一对应的 ID 和对应的内容。每个 Stream 都有唯一的名称，它是 Redis 的 key，在首次使用 `XADD` 指令追加消息时自动创建。

#### 3.14.1. XADD

​	向队列添加消息，如果指定队列不存在，则创建一个队列。

```shell
XADD key ID field value [field value ...]
```

- `key`：队列名称，如果不存在就创建；
- `ID`：消息 ID，使用 `*` 表示由 Redis 生成，可以自定义，但是要保证递增性；
- `field value`：记录。

#### 3.14.2. XTRIM

​	对流进行修剪，限制长度。

```shell
XTRIM key MAXLEN [~] count
```

- `key`：队列名称；
- `count`：数量。

#### 3.14.3. XDEL

​	删除消息。

```shell
XDEL key ID [ID ...]
```

- `key`：队列名称；
- `ID`：消息 ID。

#### 3.14.4. XLEN

​	获取流包含的元素数量，即消息长度。

```shell
XLEN key
```

- `key`：队列名称。

#### 3.14.5. XRANGE

​	获取消息列表，会自动过滤已经删除的信息。

```shell
XRANGE key start end [COUNT count]
```

- `key`：队列名；
- `start`：开始值，`-` 表示最小值；
- `end`：结束值，`+` 表示最大值；
- `count`：数量。

#### 3.14.6. XREVRANGE

​	反向获取消息列表，会自动过滤已经删除的消息。

```shell
XREVRANGE key end start [COUNT count]
```

- `key`：队列名；
- `end`：结束值，`+` 表示最大值；
- `start`：开始值，`-` 表示最小值；
- `count`：数量。

#### 3.14.7. XREAD

​	以阻塞或者非阻塞的方式获取消息列表。

```shell
XREAD [COUNT count] [BLOCK milliseconds] STREAMS key [key ...] id [id ...]
```

- `count`：数量；
- `milliseconds`：可选，阻塞毫秒数，没有就是设置为非阻塞模式；
- `key`：队列名；
- `id`：消息 ID。

#### 3.14.8. XGROUP CREATE

​	创建消费者组。

```shell
XGROUP [CREATE key groupname id|$] [SETID key groupname id|$] [DESTORY key groupname] [DELCONSUMER key groupname consumername]
```

- `key`：队列名称，如果不存在就创建；
- `groupname`：组名；
- `$`：表示从尾部开始消费，只接受新消息，当前 Stream 消息会全部忽略。

#### 3.14.9. XREADGROUP GROUP

​	用于读取消费者组中的消息。

```shell
XREADGROUP GROUP groupname consumer [COUNT count] [BLOCK milliseconds] [NOACK] [STREAMS] key [key ...] ID [ID ...]
```

- `groupname`：消费组名；
- `consumer`：消费者名；
- `count`：读取数量；
- `milliseconds`：阻塞毫秒数；
- `key`：队列名；
- `ID`：消息 ID。

## 4. Redis 高级教程

### 4.1. 数据备份与恢复

#### 4.1.1. 保存数据

​	Redis `SAVE` 命令用于创建当前数据库的备份，将在 `dir` 对应路径下，创建名为 `dbfilename` 的备份文件。

#### 4.1.2. 恢复数据

​	将备份文件移动到 `dir` 约束的路径下，并指定 `dbfilename` 为对应文件名，并启动服务即可。

#### 4.1.3. 后台保存数据

​	Redis 备份文件也可以使用命令 `BGSAVE` ，该命令将在后台执行。

### 4.2. 安全

​	可以通过配置文件设置密码参数，这样客户端连接到 Redis 服务需要密码验证，可以使服务更安全。在配置文件中设置属性 `repuirepass` 的值为密码值。在下一次连接 Redis 服务时，使用 `AUTH password` 验证密码。

### 4.3. 性能测试

​	Redis 的性能测试是通过同时执行多个命令实现的。

```shell
redis-benchmark [option] [option value]
```

**注意：**该命令是在 Redis 的目录下执行的，而不是 Redis 的客户端的内部指令。

| 选项    | 描述                                           | 默认值    |
| ------- | ---------------------------------------------- | --------- |
| `-h`    | 指定服务器主机名                               | 127.0.0.1 |
| `-p`    | 指定服务器端口                                 | 6379      |
| `-s`    | 指定服务器 socket                              | --        |
| `-c`    | 指定并发连接数                                 | 50        |
| `-n`    | 指定请求数                                     | 10000     |
| `-d`    | 以字节形式指定 `SET/GET` 值的数据大小          | 2         |
| `-k`    | 1=keep alive；0=reconnect                      | 1         |
| `-r`    | `SET/GET/INCR` 使用随机 key，`SADD` 使用随机值 | --        |
| `-P`    | 通过管道传输 `<numreq>` 请求                   | 1         |
| `-q`    | 强制退出 Redis，仅显示 query/sec 值            |           |
| `--csv` | 以 csv 格式传输                                |           |
| `-l`    | 生成循环，永久执行测试                         |           |
| `-t`    | 仅运行以逗号分隔的测试命令列表                 |           |
| `-L`    | Idle 模式，仅打开 N 个 idle 连接并等待         |           |

### 4.4. 客户端连接

​	Redis 通过监听一个 TCP 端口或者 Unix socket 的方式来接收来自客户端的连接，当一个连接建立后，Redis 内部会进行以下操作：

- 首先，客户端的 socket 被设置为非阻塞模式，因为 Redis 在网络事件处理上采用的是非阻塞多路复用模型；
- 然后，为这个 socket 设置 TCP_NODELAY 属性，禁用 Nagle 算法；
- 最后，创建一个可读的文件事件用于监听这个客户端 socket 的数据发送。

#### 4.4.1. 最大连接数

​	通过修改 redis.conf 文件对这个值进行修改。

```shell
CONFIG SET/GET maxclients [value]
```

#### 4.4.2. 客户端命令

| 命令             | 描述                                           |
| ---------------- | ---------------------------------------------- |
| `CLIENT LIST`    | 返回连接到 Redis 服务器的客户端列表            |
| `CLIENT SETNAME` | 设置当前连接的名称                             |
| `CLIENT GETNAME` | 获取通过 `CLIENT SETNAME` 命令设置的服务器名称 |
| `CLIENT PAUSE`   | 挂起客户端连接，指定挂起时间以毫秒计           |
| `CLIENT KILL`    | 关闭客户端连接                                 |

### 4.5. 管道技术

​	Redis 是一种基于客户端-服务端模型以及请求/响应协议的 TCP 服务，一个请求会遵循：

1. 客户端向服务端发送一个查询请求，并监听 socket 返回，通常是以阻塞模式，等待服务端响应；
2. 服务端处理命令，并将结果返回给客户端。

​	Redis 管道技术可以在服务端未响应时，客户端可以继续向服务端发送请求，并最终一次性读取所有服务端的响应。管道技术最显著的优势是提高了 Redis 服务的性能。



























































