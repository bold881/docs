### Redis的应用场景

#### 1. Redis的常用场景

* 缓存，读写分离
* 短信验证码、配置信息（string、自动过期）
* 商品详情、个人信息详情、新闻详情(hash)
* 省市区表、字典表、消息队列、时间轴lpush，lrange(list)
* 好友列表、倒排索引(set)
* 评分排序、有优先级的消息队列（zset)
* 分布式锁（单线程）
* 秒杀系统（主从热备、数据分片、持久化）
* 计数器（string，hash，sorted set)
* 分布式会话

### 参考列表

* https://zhuanlan.zhihu.com/p/29665317
* https://www.scienjus.com/redis-use-case/
* https://segmentfault.com/a/1190000016188385

