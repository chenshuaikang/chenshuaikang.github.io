---
layout: post
title: redis使用总结
category: redis
excerpt: redis命令大全
tags: [redis]
---

## Redis 简介
Redis 是完全开源免费的，遵守BSD协议，是一个高性能的key-value数据库。
Redis 与其他 key - value 缓存产品有以下三个特点：
- Redis支持数据的持久化，可以将内存中的数据保存在磁盘中，重启的时候可以再次加载进行使用。
- Redis不仅仅支持简单的key-value类型的数据，同时还提供list，set，zset，hash等数据结构的存储。
- Redis支持数据的备份，即master-slave模式的数据备份。

## Redis 优势
- 性能极高 – Redis能读的速度是110000次/s,写的速度是81000次/s 。
- 丰富的数据类型 – Redis支持二进制案例的 Strings, Lists, Hashes, Sets 及 Ordered Sets 数据类型操作。
- 原子 – Redis的所有操作都是原子性的，意思就是要么成功执行要么失败完全不执行。单个操作是原子性的。多个操作也支持事务，即原子性，通过MULTI和EXEC指令包起来。
- 丰富的特性 – Redis还支持 publish/subscribe, 通知, key 过期等等特性。

## 基本命令

1、启动redis
> src/redis-server &

2、关闭redis
> src/redis-cli shutdown

3、客户端
> redis-cli

4、远程连接
> redis-cli -h host -p port -a password

## Key 命令
1、获取所有的key
> keys *

2、设置key
> set key1 value1

3、获取key
> get key1

4、删除key
> del key1

5、判断key是否存在
> exists key

6、设置过期时间（单位毫秒）
> pexpire key 10

7、用时间戳的方式给key设置过期时间
> expire key timestamp

8、删除过期时间
> persist key

9、修改key的名称
> rename key newkey

10、清除指定库
> flush db

## String 命令

1、设置值
> set key value

2、获取值
> get key

3、将给定key的值设为value，并返回key的旧值
> getset key value

4、获取一个或者多个给定key的值
> mget key1 key2

5、只有在 key 不存在时设置 key 的值
> setnx key value

6、返回 key 所储存的字符串值的长度
> strlen key

7、同时设置一个或多个 key-value 对
> mset key value [key value...]

8、将 key 中储存的数字值增一。
> incr key

9、将 key 中储存的数字值减一
> decr key

## Hash 命令

1、删除一个或多个哈希表字段
> hdel key filed1 [filed2]

2、查看哈希表 key 中，指定的字段是否存在
> hexists key filed

3、获取存储在哈希表中指定字段的值
> hget key filed

4、获取在哈希表中指定 key 的所有字段和值
> hgetall key

5、获取所有哈希表中的字段
> hkeys key

6、获取哈希表中字段的数量
> hlen key

7、获取所有给定字段的值
> hmget key filed1 [filed2]

8、获取哈希表中所有值
> hvals key

9、将哈希表 key 中的字段 field 的值设为 value
> hset key filed value

10、迭代哈希表中的键值对
> hscan key cursor [MATCH pattern] [COUNT count] 

## 配置命令

1、添加日志
> vim redis.conf
> logfile /data/redis_cache/logs/redis.log #日志路径
