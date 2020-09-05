<!--
 * @Author: your name
 * @Date: 2020-09-02 14:57:22
 * @LastEditTime: 2020-09-02 15:40:30
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: d:\Github\Xmind-and-md\md\Javaweb\redis.md
-->
1. 命令操作
   1. 字符串类型(String)
      1. 存储:set key value
      2. 获取:get key
      3. 删除:del key
   2. 哈希类型(Hash)
      1. 存储:hset key field value
      2. 获取:hget key key field
      3. 删除:hdel key field
      4. 获取所有:hgetall
   3. 列表类型(list)
      1. 添加:
         1. lpush key value:将元素从左边添加
         2. rpush key value:将元素从右边添加
      2. 获取:
         1. lrange key start end:范围获取
      3. 删除:
         1. lpop key:删除列表最左边的元素并将元素返回
         2. rpop key:删除列表最右边的元素并将元素返回
   4. 集合类型(set)*不允许重复*
      1. 存储:sadd key value
      2. 获取:smebers key:获取所有元素
      3. 删除:srem key value:删除set集合中某个元素
   5. 有序集合(sortedset)
      1. 存储:zadd key score value
      2. 获取:zrange key start end
      3. zren key value
   6. 通用命令
      1. keys *:查询所有的键
      2. type key:获取键对应value的数据类型
      3. del key:删除指定的del