 
```shell
pm2 start app.js --name="api"

pm2 start (0,2,3)

pm2 flush    #清空日志
```

```shell
pm2 install pm2-logrotate
pm2 get pm2-logrotate  查询设置

pm2 set pm2-logrotate:max_size 1K 
pm2 set pm2-logrotate:compress true 
pm2 set pm2-logrotate:rotateInterval '*/5 * * * *'
pm2 set pm2-logrotate:retain 100
```
 

- Start the maximum processes depending on available CPUs
 ```
 pm2 start app.js -i 0
 ```
- Start the maximum processes -1 depending on available CPUs
```
pm2 start app.js -i -1
```

- Start 3 processes
```
 pm2 start app.js -i 3
 ```


pm2 reload
正确情况下，PM2采用fork模式新建worker进程，即主进程fork自身，产生一个worker进程。
pm2 reload命令则会用spawn方式启动，即一个接一个启动worker进程，一个新的worker启动成功，再杀死一个旧的worker进程。
采用这种方式，重新部署新版本时，服务器就不会中断服务。




```
$pm2 monit 
```