jvisialvm监控远程主机


jdk1.5以上的jvm启动时都已默开启jmx，1.4及以下版本的，需要在启动参数-D显式JMX
被监控主机的主机名称需要与主机的ip地址对应。可以hostname查看当前主机名称，hostname映射的ip127.0.0.1，或者是其它ip地址xuigaiwei，
需要修改
