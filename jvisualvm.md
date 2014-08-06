#visialvm监控远程主机，需要首先在远程主机上开启jstatd监控服务。

注意：jdk1.5以上的jvm启动时都已默开启JMX，1.4及以下版本的，需要使用启动参数-D显式开启JMX。被监控主机的主机名称需要与主机的ip地址对应。可以hostname查看当前主机名称，如果hostname映射的ip127.0.0.1，或者是其它ip地址，需要修改需要修改为指向本机IP地址。

###被监控机器需要显式指定jstatd监控权限。示例如下，创建一个policy文件，名称为“jstatd.all.policy”(随便起)，内容为
"grant codebase "file:${java_home}/../lib/tools.jar" {  
   permission java.security.AllPermission;  
}; "
。注意${java_home}变量，如果本地没有定义，可以直接替换成JDK的全路径。


###启动jstatd服务，该服务是本地监控程序获取远程服务器jvm状态的桥梁。启动命令为"jstatd -J-Djava.security.policy=jstatd.all.policy"。特别注意一下启动改命令的权限即可。
如果系统中有使用root用户启动的服务，改jstatd服务也需要使用root启动。


###在本地jvisualvm中“远程”选项卡添加一个远程服务器的链接，就可以看到所有的jvm实例的监控数据了。
