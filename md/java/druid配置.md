```yml
type: com.alibaba.druid.pool.DruidDataSource
    druid:
      username: api
      password: Password1234
      #连接池的初始大小，最小，最大，超时时间
      initial-size: 5
      min-idle: 5
      max-active: 100
      max-wait: 6000
      #多久一检测
      time-between-eviction-runs-millis: 30000
      #最小生存时间
      min-evictable-idle-time-millis: 50000
      validation-query: select 1
      test-on-borrow: false
      test-on-return: false
      #打开PScache
      pool-prepared-statements: true
      max-pool-prepared-statement-per-connection-size: 20
      #配置监控统计拦截的filters
      filters: stat,wall,slf4j
      #通过connectionProperties属性打开mergeSql功能,慢SQL记录
      connection-properties: druid.stat.mergeSql\=true;druid.stat.slowSqlMillis\=5000
      #配置DruidStatFilter
      web-stat-filter:
        enabled: true
        url-pattern: "/*"
        exclusions: "*.js,*.gif,*.jpg,*.bmp,*.png,*.css,*.ico,/druid/*"
      #配置DruidStatViewServlet
      stat-view-servlet:
        url-pattern: "/druid/*"
        ##        allow: 127.0.0.1,148.70.17.87
        reset-enable: false
        login-username: api
        login-password: Password1234
        enabled: true
```