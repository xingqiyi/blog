
查看 redis相关信息
redis-cli -h localhost info

redis-cli -h localhost info | grep 'redis_version'



redis-server -v


config set stop-writes-on-bgsave-error no




redis-cli -h 192.168.1.10 -p 6379
auth Geonoon
keys *
smembers setname
flushdb




其实Redis是可以安装成windows服务的，开机自启动，命令如下：
redis-server --service-install redis.windows.conf
安装完之后，就可看到Redis已经作为windows服务了
启动停止服务:
redis-server --service-start
redis-server --service-stop


lua:

# redis-cli --eval detect.lua


SET detect "ssss"
SCRIPT LOAD "local f=loadstring(redis.call('get',KEYS[1]));return f()"
EVALSHA "1d757ea0d253288071ab7e2358562b8721098142" 1 detect okALqsGyR/yjMzjU/G8AKg== 

 


查看redis 内存情况:
info memory



watch:
http://www.guoweiwei.com/2012/09/redis-status-and-performance-monitor.html

redis-benchmark -h localhost -p 6379 -c 100 -n 100000


redis-cli -h localhost -p 6379 monitor


redis-cli -h localhost -p 6379 info


redis-stat :
java -jar redis-stat-0.4.13.jar --server







