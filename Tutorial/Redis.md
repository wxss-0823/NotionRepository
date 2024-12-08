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

Update GitPush.exe.

















