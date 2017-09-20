
dolphin:
f3	拆分切换

f8  隐藏文件


kconsole:
ctrl + shift + k/l  清屏
ctrl + w  关闭标签



方法一：
　　如果只是想临时使用http代理，可以在使用apt-get之前于终端下输入：
	export http_proxy="http://用户名:密码@代理IP:代理端口"
	export http_proxy="http://192.168.1.20:1080"
 
方法二：（方法一的持久化）
　　如果希望apt-get与其它应用程序都可以一直使用http代理，可以这样： 
　　在终端下编辑~/.bashrc文件：　　vim ~/.bashrc
　　在文件末尾添加如下两句：

	http_proxy="http://192.168.1.20:1080"
	export http_proxy



全局
f1 			桌面
alt + s  	google
alt + b		baidu

f4			mac的f3

ctrl+alt+esc	kill 一个窗口	



linux 挂载  ntfs
先安装：
sudo apt-get install ntfs-config
再配置一下：
sudo ntfs-config




格式化为 ntfs
sudo apt-get install ntfsprogs
sudo mkntfs /dev/sdb1

sudo mkfs.vfat -F 32 /dev/sdb1即可将u盘格式化为fat32格式。 
假如你要把指定磁盘格式化为NTFS格式那么你需要sudo apt-get install ntfsprogs来安装ntfs读写工具，然后执行sudo mkfs.ntfs /dev/sda1，此过程会很慢。对于要格式化为linux ext格式的分区就更容易了： 
sudo mkfs.ext4 /dev/sda1 # 格式化为ext4分区 
sudo mkfs.ext3 /dev/sda1 # 格式化为ext3分区 
sudo mkfs.ext2 /dev/sda1 #格式化为ext2分区 
PS：对于要格式化的分区必须要先用umount卸载掉才能格式化哦。 



 

#备份系统：到 /media/bkp：

# 清理旧版本的软件缓存
sudo apt-get autoclean
#
# 清理所有软件缓存
sudo apt-get clean
#
# 删除系统不再使用的孤立软件
sudo apt-get autoremove


sudo tar vzcpf /media/bkp/ubuntu_`date +%Y%m%d_%H`.tar.gz --exclude=/proc --exclude=/dev--exclude=/mnt --exclude=/media --exclude=/lost+found --exclude=/cdrom --exclude=/tmp --exclude=/sys --exclude=/home/xx/.cache --exclude=/run / > /media/bkp/ubuntu_`date +%Y%m%d_%H`.log 2> /media/bkp/ubuntu_`date +%Y%m%d_%H`.error


恢复系统：
推荐备份下：/boot和/etc/fstab，然后再执行恢复命令
将备份文件拷贝到/目录，执行恢复命令：
# 使用gzip格式
su - root
tar vxzpf ubuntu*.tar.gz -C /




KDE - Baloo file-index is not working
Disable it in ~/.kde4/share/config/baloofilerc. Set
Indexing-Enabled=false