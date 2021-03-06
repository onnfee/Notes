##　事务

- 定义
  - 与传统关系型数据库事务不同，redis事务不会执行回滚，而是继续执行后续的命令
  - 一组命令的集合，事务与命令都是最小执行单位，原理是先将属于一个事务的命令发送给redis，然后redis一次执行这些命令
  - 可以保证一个事务内的命令一次执行而不被其他命令插入影响
- 使用

```
multi
用于监视一个事务块的开始，之后的所有命令都放在队列里，等遇到exec命令再执行
exec
用于执行事务块内所有的命令，如果命令被中断，返回fasle
watch
用于监视一个或多个key，如果在事务执行之前这个或（这些）key被其他命令所改动，事务将被中断。
unwatch
用于取消watch命令对所有key的监视
discard
取消事务，放弃执行事务块内的所有命令2
```

##　使用场景

- 缓存
- 排行榜
- 计数器
- 分布式会话
- 分布式锁

##　缓存

- 缓存穿透

```
	缓存穿透，是指查询一个数据库一定不存在的数据。
	正常的使用缓存流程大致是，数据查询先进行缓存查询，如果key不存在或者key已经过期，再对数据库进行查询，并把查询到的对象，放进缓存。
	在工作中，为了防止缓存穿透的发生，将数据库查询的空对象也放入缓存。
```



- 缓存雪崩

```
	缓存雪崩，是指在某一个时间段，缓存集中过期失效。
	比如双十一的抢购，有一波商品时间比较集中的放入了缓存，假设缓存一个小时。那么到了凌晨一点钟的时候，这批商品的缓存就都过期了。而对这批商品的访问查询，都落到了数据库上，对于数据库而言，就会产生周期性的压力波峰。
	正确做法是不同类商品，缓存不同周期，并且同一类的商品，还要再加上一个随机因子，这样尽可能的分散缓存时间。
	除此之外，还有自然雪崩，缓存服务器宕机，对数据库造成的压力是不可预估的。

```



- 缓存击穿

```
	当大量请求同时访问一个key时，这个key刚好失效，此时这些请求都落到数据库上。
```

