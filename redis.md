# bun

## RDB快照
save Redis将内存数据快照保存在名字为dump.rdb的二进制文件中。 #save 60 1000
bgsave 
## AOF
auto-aof-rewrite-percentage 100 auto-aof-rewrite-min-size 64mb bgrewriteaof重写AOF
## rdb aop混合持久化
aof-use-rdb-preamble yes
