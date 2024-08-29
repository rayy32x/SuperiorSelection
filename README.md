# SuperiorSelection
# 尚品优享
项目描述：SpringBoot单体项目，主要内容包括：用户验证码登录，添加QPS高的商户进缓存，并解决经典的缓存问题，保证了数据库和缓存的双写一致。实现了优惠券秒杀功能，解决超卖和一人一单问题并完成异步优化。实现关注推送和点赞排行榜功能，以及页面的UV和PV统计。<br>
技术栈：SpringBoot+SpringMVC+Redis+Lua+MySQL+MyBatis-Plus+Nginx<br>
● 使用Redis存入Token代替Session，实现验证码登录和自动注册。自定义双重拦截器，实现Token有效期的刷新；<br>
● 使用AOP+自定义注解+SpringTask定时任务，基于ConcurrentHashMap实现了对query接口的QPS实时计算，并将QPS高于标准的热点数据加入Redis缓存。<br>
● 基于Redis实现商户信息缓存，使用AOP+自定义注解+布隆过滤器/空值法解决缓存穿透问题，使用逻辑过期/互斥锁解决缓存击穿问题，并利用泛型和函数式接口对上述所有方法进行整合封装。部署Redis集群+哨兵解决缓存雪崩问题；<br>
● 使用RabbitMQ可靠性消息队列异步更新缓存，对比AOP+延迟双删策略，实现Redis与MySQL的双写最终一致性；<br>
● 使用CAS乐观锁解决优惠券库存超卖问题，使用Redission分布式锁，Lua脚本实现分布式环境下的一人一单功能；<br>
● 使用RabbitMQ消息队列对秒杀业务的性能进行优化，实现异步下单，同时完成流量削峰，功能解耦；<br>
● 使用SortedSet实现对博客的点赞排序；使用Feed流实现关注博主的博客推送；<br>
● 基于HyperLogLog实现页面的UV统计，并结合AOP实现对页面的PV统计。<br>
