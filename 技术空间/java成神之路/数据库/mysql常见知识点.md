# mysql常见知识点
## 数据库的三大范式
- 第一范式：属性不可再分
- 第二范式：非主属性完全依赖于主属性
- 第三范式：非主属性之间不存在传递依赖
注意一点：反模式
通过数据库范式化设计，将导致数据库业务涉及的表变多，并且可能需要将涉及的业务表进行多表连接查询，这样将导致性能变差，且不利于分库分表。因此，出于性能优先的考量，可能在数据库的结构中需要使用反模式的设计，即空间换取时间，采取数据冗余的方式避免表之间的关联查询。

## 什么是索引
类比词典的目录检索
### 优点
- 1 减少磁盘IO,加快检索速度.  
- 2 降低排序成本
### 缺点
- 1 降低更新操作效率
- 2 需要多余的存储磁盘空间
### 使用场景
- 1 表的数据量比较大[中大型]（如果太小，全表搜索的效率更高）
- 2 特大型的表，建立和使用索引的代价也会随着增长，可以使用分库分表[分区表](https://blog.csdn.net/admin1973/article/details/55504018))

## 索引类型
索引，都是实现在存储引擎层，主要有六中类型
- 1.普通索引：最基本的索引没有任何约束
- 2.唯一索引：与普通索引类型，但是具有唯一性约束
- 3.主键索引：特殊的唯一索引，不允许有空值
- 4.复合索引：将多个索引组合在一起创建，可以覆盖多个列
- 5.外键索引：只有InnoDB类型的表才可以使用外键索引，保证数据的一致性、完整性和实现级联操作。
- 6.全文索引：MySQL 自带的全文索引只能用于 InnoDB、MyISAM ，并且只能对英文进行全文检索，一般使用全文索引引擎。

常见的全文索引方案是Elasticsearch[没有使用经验，后面增加实践]

## 索引创建的原则
- 1. 最适合索引的列是出现在WHERE子句的列，或者子句的列而不是出现在select关键字后的列.
- 2. 索引的技术越大，索引效果越好.
 [索引技术介绍](https://blog.csdn.net/mingyundezuoan/article/details/79038989)
- 3. 根据情况创建复合索引，因为复合索引的基数大
- 4. 索引个数尽量少，值尽量短(减少存储空间，和磁盘IO) 
## 索引使用的注意事项
- 1.  [索引使用注意事项](http://blog.720ui.com/2017/mysql_core_04_index_item)
- 2. 索引查看,explain语句(TODO,细化)

## 索引原理
- [索引背后的数据结构和算法原理](http://blog.codinglabs.org/articles/theory-of-mysql-index.html)
- [MySQL索引原理](https://blog.csdn.net/u013235478/article/details/50625677)
- [深入理解MySQL索引原理和实现——为什么索引可以加速查询？](https://blog.csdn.net/tongdanping/article/details/79878302)

mysql中，有两种索引方式
- B-Tree索引
- Hash索引
- [MySQL BTree索引和hash索引的区别](https://blog.csdn.net/oChangWen/article/details/54024063)

## mysql的事务隔离级别
- 读未提交
- 读已提交
- 可重复读
- 可串行化

## mysql的锁机制
从锁的机制划分:悲观锁，乐观锁    
从锁的粒度划分:行锁，段锁，表锁   
从锁的性质划分:排他锁和共享锁

## mysql的执行顺序
- (1)     SELECT
- (2)     DISTINCT <select_list>
- (3)     FROM <left_table>
- (4)     <join_type> JOIN <right_table>
- (5)     ON <join_condition>
- (6)     WHERE <where_condition>
- (7)     GROUP BY <group_by_list>
- (8)     HAVING <having_condition>
- (9)     ORDER BY <order_by_condition>
- (10)    LIMIT <limit_number>
- [SQL查询之执行顺序解析](http://zouzls.github.io/2017/03/23/SQL%E6%9F%A5%E8%AF%A2%E4%B9%8B%E6%89%A7%E8%A1%8C%E9%A1%BA%E5%BA%8F%E8%A7%A3%E6%9E%90/)

## 聊聊mysql优化
[MySQL索引原理及慢查询优化](https://tech.meituan.com/2014/06/30/mysql-index.html)


## 什么是MVCC
[什么是MVCC](mvcc原理.md)



## 面试题目
[10道myql查询面试题目](https://www.yanxurui.cc/posts/mysql/2016-11-10-10-sql-interview-questions/)

[10道myql查询面试题目](10道myql查询面试题目.md)

## 事务是如何通过日志实现的

















## 参考资料
http://svip.iocoder.cn/MySQL/Interview/









