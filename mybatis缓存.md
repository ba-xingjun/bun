# bun
## 1级缓存 
PerpetualCache Map<Object,Object> flushCache 一
级缓存中的key是由sql语句、条件、statement等信息组成一个唯一值。一级缓存中的value，就是查询出的结果对象。
