# bun

## 环境搭建

protected-mode no #关闭保护模式，开启的话，只有本机才可以访问redis

#bind 127.0.0.1（bind绑定的是自己的机器网卡ip，如果有多块网卡可以配多个ip，代表允许客户端通过机器的那些网卡ip去访问）

daemonize yes #后台启动

## RDB快照
save Redis将内存数据快照保存在名字为dump.rdb的二进制文件中。 #save 60 1000
bgsave 
## AOF
appendfsync always: 

appendfsync everysec: 

appendfsynv no:

auto-aof-rewrite-percentage 100 

auto-aof-rewrite-min-size 64mb bgrewriteaof重写AOF
## rdb aop混合持久化
aof-use-rdb-preamble yes
## redis管道

## 主从复制
主从风暴

port 6380

pidfile /var/run/redis_6380.pid # 把pid进程号写入pidfile配置的文件

logfile "6380.log"

dir /usr/local/redis-5.0.3/data/6380 #指定数据存放目录

配置主从复制

replicaof 192.168.0.60 6379 # 从本机6379的redis实例复制数据，Redis 5.0之前使用slaveof

replica-read-only yes #配置从节点只读

## lua脚本
eval

## 哨兵架构

cp sentinel.conf sentinel-26379.conf

prot 26379

daemonize yes

pidfile "/var/run/redis-sentinel-26379.pid"

logfile "26379.log"

dir "/usr/local/redis-5.0.3/data"

sentinel monitor mymaster 192.168.0.60 6379 2

## 集群搭建部署

  (1)daemonize 
  
 （2）port 8001（分别对每个机器的端口号进行设置）
 
 （3）pidfile /var/run/redis_8001.pid # 把pid进程号写入pidfile配置的文件
 
 （4）dir /usr/local/redis‐cluster/8001/（指定数据文件存放位置，必须要指定不同的目录位置，不然会
丢失数据）

 （5）cluster‐enabled yes（启动集群模式）
 
 （6）cluster‐config‐file nodes‐8001.conf（集群节点信息文件，这里800x最好和port对应上）
 
 （7）cluster‐node‐timeout 10000
 
  (8)# bind 127.0.0.1（bind绑定的是自己机器网卡的ip，如果有多块网卡可以配多个ip，代表允许客户端通
过机器的哪些网卡ip去访问，内网一般可以不配置bind，注释掉即可）

  (9)protected‐mode no （关闭保护模式）
  
  (10)appendonly 
  
  如果要设置密码需要增加如下配置
  
  (11)requirepass bun (设置redis访问密码)
  
  (12)masterauth bun (设置集群节点间访问密码，跟上面一致)

网络抖动:cluster-node-timeout

脑裂问题:min-replicas-to-write

集群是否完整才对外提供服务:cluster-require-full-coverage no 

延迟计算公司:delay=500ms+random(0~500ms)+slave_rank*1000ms

redis-cli -a bun --cluster create --cluster-replicas 1 host:port

redis-cli -a bun -h -p

redis‐cli ‐a bun ‐‐cluster add‐node 192.168.0.61:8007 192.168.0.61:8001

redis‐cli ‐a bun ‐‐cluster reshard 192.168.0.61:8001

添加从节点 cluster replicate 2728a594a0498e98e4b83a537e19f9a0a3790f38

删除从节点 redis‐cli ‐a bun ‐‐cluster del‐node 192.168.0.61:8008 a1cfe35722d151cf70585cee212755653

删除主节点 rehard分片 redis‐cli ‐a bun ‐‐cluster reshard 192.168.0.61:8007



