# bun

## RDB快照
save Redis将内存数据快照保存在名字为dump.rdb的二进制文件中。 #save 60 1000
bgsave 
## AOF
appendfsync always: appendfsync everysec: appendfsynv no:
auto-aof-rewrite-percentage 100 auto-aof-rewrite-min-size 64mb bgrewriteaof重写AOF
## rdb aop混合持久化
aof-use-rdb-preamble yes

## 主从复制

port 6380
pidfile /var/run/redis_6380.pid # 把pid进程号写入pidfile配置的文件
logfile "6380.log"
dir /usr/local/redis-5.0.3/data/6380 #指定数据存放目录

配置主从复制
replicaof 192.168.0.60 6379 # 从本机6379的redis实例复制数据，Redis 5.0之前使用slaveof
replica-read-only yes #配置从节点只读
