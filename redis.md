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
master 选举
脑裂问题
