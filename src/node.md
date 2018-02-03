
node 版本管理工具  n

npm install -g n

n 回车 可以切换版本

n stable  安装稳定版本

n latest  安装最新版本




sudo 安装的 node npm  做以下设置  不用一直输 sudo
改变目录的所有者
sudo chown -R $USER /usr/local  
sudo chown -R $USER:$(id -gn $USER) /home/ubuntu/.config

