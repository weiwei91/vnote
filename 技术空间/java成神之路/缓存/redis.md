# redis
# 数据类型
* String
* List
* Set
* Hash
* Zset

# RedisTemplate
它是spring封装的对象，支持所有的redis原生的api

```
redisTemplate.opsForValue();//操作字符串 
redisTemplate.opsForHash();//操作hash 
redisTemplate.opsForList();//操作list 
redisTemplate.opsForSet();//操作set 
redisTemplate.opsForZSet();//操作有序set
redisTemplate.opsForGeo();//操作地图数据
```

# 使用建议
1.合理分配过期时间(根据数据量和数据大小设置合理过期时间，不然内存会被消耗殆尽)[理解]
2.使用命名空间[理解，多个组件使用中间件]
3.选用合适的数据结构
[
1.https://redis.io/commands  理解命令及其原理，选择合适的
2.不建议使用redis缓存单个数据大小较大的对象，尤其是使用Set，Hash此类数据结构的时候。理由是redis是单线程，过多的大对象访问增加了网络IO压力，对Redis性能有一点影响，另方面redis的虚拟内存page较小，如果内存碎片率较高，则分配/申请内存时性能上有些影响，如果较大的对象可以考虑memcache。
]
4.多个操作使用pinepine[不太理解]


# 实验环境的搭建
各种数据结构的使用场景
