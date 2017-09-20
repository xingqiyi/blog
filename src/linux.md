

限制cpu占用 工具 cpulimit
cpulimit -e firefox -l 30


//copy 文件夹  -r  递归
cp -r folder1 folder2


查看权限
ls -l
ls -a  查看all  包括隐藏文件

查看在线用户
who




编辑文件
sudo gedit filename

 Linux下删除非空文件夹：
 rm -rf dirname    -r 循环 -f 强制


 Linux下删除空文件夹：
 rmdir -p dirname


linux下重命名文件或文件夹的命令mv既可以重命名，又可以移动文件或文件夹.
例子：将目录A重命名为B
mv A B

例子：将/a目录移动到/b下，并重命名为c
mv /a /b/c

ssh copy 文件
scp filename1 远程用户名@IP：目录/filename2
-v




pwd 查看当前路径

vi NewFilename  新建 文件  编辑文件
mkdir /home/u1 新建文件夹


 

### 各种压缩命令：
http://www.cnblogs.com/eoiioe/archive/2008/09/20/1294681.html

.tar.gz 和 .tgz:
解压：tar zxvf FileName.tar.gz
压缩：tar zcvf FileName.tar.gz DirName

.rar
解压：rar x FileName.rar
压缩：rar a FileName.rar DirName



查看,修改文件
权限:
http://www.cppblog.com/deercoder/articles/110129.html

行动：
+ 表示添加权限
- 表示删除权限
= 表示使之成为唯一的权限
ugoa+-=rwx

chmod ug+w,o-w file  用户和组可写,其他不可写
chmod 777 filename 	 所有

chmod [-R] xyz 文件或目录  
-R：进行递归的持续更改，即连同子目录下的所有文件都会更改  





以下命令可以查看磁盘各分区大小、已用空间等信息：
df -h
以下命令可以查看foo目录的大小：
du -sh foo


#查看当前目录下的所有目录以及子目录的大小
$ du -h
$ du -ah

#-h:用K、M、G的人性化形式显示 human-readable
#-a:显示目录和文件 all
#-s:sum

du -h tmp
du -ah tmp
#只查看当前目录下的tmp目录(包含子目录)的大小


#查看当前目录及其指定深度目录的大小
sudo du -ah --max-depth=1
#--max-depth＝n:只深入到第n层目录，此处设置为0，即表示不深入到子目录



free -k/-m/-g  查看内存使用情况
uptime
	用来显示任务队列信息。
	| 现在的时间 | 系统开机运转到现在经过的时间 | 连线的使用者数量 | 最近一分钟，五分钟和十五分钟的系统负载 |
	11:00:16 up 1 day,  2:24,  4 users,  load average: 0.21, 0.25, 0.36

top  查看 系统资源占用


npm:

sudo apt-get install python-software-properties
sudo add-apt-repository ppa:gias-kay-lee/npm
sudo apt-get update
sudo apt-get install npm


node:

$ sudo add-apt-repository ppa:chris-lea/node.js
$ sudo apt-get update
$ sudo apt-get install nodejs


gedit:

sudo apt-get install gedit


  

端口:

一、查看哪些端口被打开  netstat -anp
二、关闭端口号:iptables -A INPUT -p tcp --drop 端口号-j DROP
　　iptables -A OUTPUT -p tcp --dport 端口号-j DROP
三、打开端口号：iptables -A INPUT -ptcp --dport  端口号-j ACCEPT
四、以下是linux打开端口命令的使用方法。
　　nc -lp 23 &(打开23端口，即telnet)
　　netstat -an | grep 23 (查看是否打开23端口)
五、linux打开端口命令每一个打开的端口，都需要有相应的监听程序才可以

查看 是否开通端口
telnet www.geonoon.net 3001

run  name.sh:
./name.sh
or   sh name.sh




修改配置文件后
source file 可不重启 及时生效



echo 输出信息到屏幕 或文件
echo "This is a test." > ./test.txt