
2018-02-08 -by arvin
--------------------
常见问题：
1，
xxl-job-executor-sample-springboot下application.properties文件

### xxl-job admin address list, such as "http://address" or "http://address01,http://address02"
这里实际指的是：admin-web的URL地址：
xxl.job.admin.addresses=http://127.0.0.1:8080/xxl-job-admin //部署在tomcat下的地址
xxl.job.admin.addresses=http://127.0.0.1:7701/ //直接在ideal下开始调试时tomcat下的地址
如果URL地址不正确，可能会报如下错误：
16:48:22.863 logback [Thread-9] INFO  c.x.j.c.t.ExecutorRegistryThread - >>>>>>>>>>> xxl-job registry error, registryParam:RegistryParam{registGroup='EXECUTOR', registryKey='xxl-job-executor-sample', registryValue='192.168.1.203:9999'}
java.lang.RuntimeException: RpcResponse byte[] is null
	at com.xxl.job.core.rpc.netcom.NetComClientProxy$1.invoke(NetComClientProxy.java:65)
	at com.sun.proxy.$Proxy53.registry(Unknown Source)
	at com.xxl.job.core.thread.ExecutorRegistryThread$1.run(ExecutorRegistryThread.java:57)
	at java.lang.Thread.run(Thread.java:745)
解决方案：
xxl.job.admin.addresses=改为正确的URL
====================================
2，
JobHandler(value="shardingJobHandler")
JobHandler的名字是value的值=shardingJobHandler
3，
在线Cron表达式生成器
http://cron.qqe2.com/
4，
运行过程中不时报错: java.lang.ClassCastException: java.lang.String cannot be cast to com.xxl.job.core.rpc.codec.RpcResponse #223
https://github.com/xuxueli/xxl-job/issues/223
最新发现：
如果将adminAddresses 设置成 ip+port地址的情况下，这种错误没有发生
在adminAddresses 设置成 域名地址 的情况下，这种错误才会发生，1个小时内不定时发生好几次。。。

5，
参考文章：
分布式任务调度平台XXL-JOB
http://www.xuxueli.com/xxl-job/#/
==
yaozd/xxl-job: A lightweight distributed task scheduling framework.（分布式任务调度平台XXL-JOB）
https://github.com/yaozd/xxl-job
==
分布式任务调度平台XXL-JOB - 许雪里 - 博客园--(许雪里是xxl-job的作者，特别推荐-byArvin)
https://www.cnblogs.com/xuxueli/p/5021979.html
==
运行过程中不时报错: java.lang.ClassCastException: java.lang.String cannot be cast to com.xxl.job.core.rpc.codec.RpcResponse · Issue #223 · xuxueli/xxl-job
https://github.com/xuxueli/xxl-job/issues/223
==
Releases · xuxueli/xxl-job-(稳定版
https://github.com/xuxueli/xxl-job/releases
==