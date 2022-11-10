1.  EXPLAIN：这个是比较浅显的分析，并不会真正执行 SQL，分析出来的可能不够准确详细。但是能发现一些关键问题。
2.  PROFILING： 通过 `set profiling = 1` 开启的 SQL 执行采样。可以分析 SQL 执行分为哪些阶段，并且每阶段的耗时如何。需要执行并且执行成功 SQL，并且分析出来的阶段不够详细，一般只能通过某些阶段是否存在如何避免这些阶段的出现进行优化（例如避免内存排序的出现等等）。
3.  OPTIMIZER TRACE：详细展示优化器的每一步，需要执行并且执行成功 SQL。MySQL 的优化器由于考虑的因素太多，迭代太多，配置相当复杂，默认的配置在大部分情况没问题，但是在某些特殊情况会有问题，需要我们进行人为干预。

这里再说一下在不同的 MySQL 版本， **EXPLAIN 和 OPTIMIZER TRACE 结果可能不同，这是 MySQL 本身设计上的不足导致的，EXPLAIN 更贴近最后的执行结果，OPTIMIZER TRACE 相当于在每一步埋点采集，在 MySQL 不断迭代开发的时候，难免会有疏漏**

### **MySQL InnoDB 查询优化器数据配置（MySQL InnoDB Optimizer Statistics）**

> https://dev.mysql.com/doc/refman/8.0/en/innodb-persistent-stats.html

1.  `innodb_stats_persistent` 全局变量控制全局默认的数据是否持久化，默认为 ON 即持久化，我们一般不会能接受在内存中保存，这样万一数据库重启，表就要重新分析，这样减慢启动时间。控制单个表的配置是 `STATS_PERSISTENT`（在 `CREATE TABLE` 以及 `ALTER TABLE` 中使用）。
2.  `innodb_stats_auto_recalc` 全局变量全局默认是否自动更新，默认为 ON 即在表中有 10% 以上的行更新后触发后台异步更新采集数据，。控制单个表的配置是 `STATS_AUTO_RECALC`（在 `CREATE TABLE` 以及 `ALTER TABLE` 中使用）。
3.  `innodb_stats_persistent_sample_pages` 全局变量控制全局默认的采集页的数量，默认为 20. 即每次更新，随机采集表以及表中的每个索引的 20 页数据，用于**估算每个索引的查询消耗是多大以及全表扫描消耗是多大**，控制单个表的配置是 `STATS_SAMPLE_PAGES`（在 `CREATE TABLE` 以及 `ALTER TABLE` 中使用）。

》https://zhuanlan.zhihu.com/p/472931123