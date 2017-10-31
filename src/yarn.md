
```bash
yarn add  eslint-plugin-import --dev

yarn remove eslint-plugin-import

yarn global add eslint


yarn == yarn install


yarn start == npm start


yarn init


npm i -g serve  //静态文件服务 
serve folderName  //发布
```


~,^的区别是：
~的意思是匹配最近的小版本 比如~1.2.3将会匹配所有的1.2.x版本，但不匹配1.3.0， 1.2.0 <= ~1.2.3 <1.3.0
^的意思是最近的一个大版本 比如^1.2.3 将会匹配 所有 1.x.x 包括1.3.0 但不包括2.0 1.0.0 <= ^1.2.3 < 1.x.x