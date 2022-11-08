在druid配置中添加连接超时回收机制；

      jdbc-url: jdbc:mysql://172.119.0.12:3306/jzj_dev?useUnicode=true&characterEncodeing=utf-8
      username: root
      password: x5
      driverClassName: com.mysql.jdbc.Driver
  # 下面为连接池的补充设置，应用到上面所有数据源中
  # 初始化大小，最小，最大
      initialSize: 1
      minIdle: 1
      maxActive: 20
      maxWait: 60000
      timeBetweenEvictionRunsMillis: 60000
      minEvictableIdleTimeMillis: 300000
      validationQuery: SELECT 1
      testWhileIdle: true
      testOnReturn: false
      testOnBorrow: false
      poolPreparedStatements: true
      maxPoolPreparedStatementPerConnectionSize: 20
      #配置监控统计拦截的filters，去掉后监控界面sql将无法统计,'wall'用于防火墙
      filters: stat, wall, log4j
      connectionProperties: druid.stat.mergeSql=true;druid.stat.slowSqlMillis=5000
      #超时回收机制
      removeAbandoned: true
      removeAbandonedTimeout: 1800
      logAbandoned: false


logAbandoned="true"设置为true,程序在回收连接的同时会打印日志。会影响速度，正式运行可以关闭。
