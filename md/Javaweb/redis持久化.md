<!--
 * @Author: your name
 * @Date: 2020-09-02 15:43:54
 * @LastEditTime: 2020-09-02 16:11:48
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \undefinedd:\Github\Xmind-and-md\md\Javaweb\redis持久化.md
-->
1. 持久化
   1. RDB:
      1. 默认方式,不需要进行配置
      2. 在一定的间隔时间中,检测key的变化情况
         1. 修改方式:
            1. 编辑redis.windows.conf文件
                ```
                # after 900 sec (15 min) if at least 1 key changed
                save 900 1
                # after 300 sec (5 min) if at least 10 keys changed
                save 300 1
                # after 60 sec if at keast 10000 keys changed
                save 60 1000
                ```
   2. AOF:
      1. 日志记录方式,记录每一条命令的操作。
      2. 修改方式:
         1. 编辑redis.conf(启用)
            ```
            appendonly yes;
            ```
        2. 配置选项
            ```
            #appendfsync always#每一次操作都持久化
            appendfsync everysec#每隔一秒持久化一次
            #appendfsync no 不持久化
            ```