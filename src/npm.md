ubuntu 安装 npm:
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:gias-kay-lee/npm
sudo apt-get update
sudo apt-get install npm


升级npm到最新
sudo npm install npm@latest -g



Npm的配置管理及设置代理:
http://www.cnblogs.com/huang0925/archive/2013/05/17/3083207.html


npm init
npm install

npm config list
npm config ls -l

npm config set <><>

npm config help


npm cache clean


npm root：查看当前包的安装路径
npm root -g：查看全局的包的安装路径


npm ls -g --depth=0

npm config set proxy http://192.168.1.101:1080
npm config delete proxy


修改 npm全局安装路径

npm config set prefix /home/xx/xx-server/npm/npm-global/
npm config set cache /home/xx/xx-server/npm/npm-cache/

全局安装了无法找到命令:
全局安装路径 添加到 系统环境变量
echo -e "export PATH=$(npm prefix -g)/bin:$PATH" >> ~/.bashrc && source ~/.bashrc


全局安装了无法 require 这个包:
export NODE_PATH=$(npm prefix -g)/lib/node_modules



安装过程中说没权限，sudo 也不行:
获取缓存目录 npm config get cache (~/.npm)
删除缓存目录
sudo rm -rf ~/.npm
再次安装坚决不要用 sudo，如果还是出现权限问题请修改安装路径权限



cnpm   /usr/bin/env: "node": 没有那个文件或目录:

ln -s /usr/bin/nodejs /usr/bin/node

sudo ln -s /usr/bin/nodejs ~/.nvm/versions/node/v7.3.0/bin/node 

sudo ln -s  ~/.nvm/versions/node/v7.3.0/bin/node /usr/bin/node
sudo ln -s  ~/.nvm/versions/node/v7.3.0/bin/node /usr/bin/nodejs
 



3.2、使用npm安装插件：命令提示符执行npm install <name> [-g] [--save-dev]；

npm install gulp-less --save-dev
    -g：全局安装。将会安装在C:\Users\Administrator\AppData\Roaming\npm，并且写入系统环境变量；  非全局安装：将会安装在当前定位目录；  全局安装可以通过命令行在任何地方调用它，本地安装将安装在定位目录的node_modules文件夹下，通过require()调用；
    --save：将保存配置信息至package.json（package.json是nodejs项目配置文件）；
    -dev：保存至package.json的devDependencies节点，不指定-dev将保存至dependencies节点；一般保存在dependencies的像这些express/ejs/body-parser等等。


npm install，则会根据package.json下载所有需要的包，
npm install --production只下载dependencies节点的包）。


3.3、使用npm卸载插件：npm uninstall <name> [-g] [--save-dev]  PS：不要直接删除本地插件包
删除全部插件：借助rimraf：
npm install rimraf -g
用法：rimraf node_modules

3.4、使用npm更新插件：npm update <name> [-g] [--save-dev]
3.4.1、更新全部插件：npm update [--save-dev]
3.5、查看npm帮助：npm help
3.6、当前目录已安装插件：npm list


 npm install cnpm -g --registry=https://registry.npm.taobao.org
cnpm跟npm用法完全一致，只是在执行命令时将npm改为cnpm（以下操作将以cnpm代替npm）


jshint 使用:
npm install jshint -g
jshint ./app/model.js



