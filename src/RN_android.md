# React-native  android


## 调试

>你可以通过摇晃设备或是选择iOS模拟器的"Hardware"菜单中的"Shake Gesture"选项来打开开发菜单。另外，如果是在iOS模拟器中运行，还可以按下Command⌘ + D 快捷键，Android模拟器对应的则是Command⌘ + M（windows上可能是F1或者F2）。

## windows android 每次  下载 gradle的问题

Exception in thread “main” java.net.ConnectException: Connection timed out: conn
ect

> 手动下载:
http://services.gradle.org/distributions/gradle-2.4-all.zip

> 修改改 {MyProject-path}\android\gradle\wrapper\gradle-wrapper 里的 distributionUrl 为本地路径：
distributionUrl=file:///D:/xingqiyi/RN/gradle-2.4-all.zip



## failed to find Build Tools revision 25.0.2    android sdk 版本 问题

```css
见rn 初始化 步骤
Android Studio
Tools -> Android -> SDK Manager
```

## react-native-starter   中  API_KEY not definded

```css
issue:
Let copy .env.sample to .env file and change the configuration variables
.env.sample 文件  改名为  .env
```


## 命令行翻墙

```css
set HTTP_proxy=http://127.0.0.1:62497
set HTTPS_proxy=http://127.0.0.1:62497
```

## Error: EPERM: operation not permitted,

```
网络问题
```

## 很慢: Resolving dependencies ':app:_releaseApk'

```
./android/build.gradle
change your jcenter() to mavenCentral() :


buildscript {
    repositories {
        // jcenter()
         mavenCentral()
    }

```

## expected a component class, got [object Object]

```js
    组件大小写的问题
    JSX中 不能使用 div 等 html
```


## could not get batchedbridge make sure

https://stackoverflow.com/questions/34175416/how-to-use-offline-bundle-on-android-for-react-native-project

```
react-native bundle --platform android --dev false --entry-file index.android.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/

```

- 1 when server start, open next terminal with same path as project path

- 2 copy and paste this command: Before you copy and paste command in command propmt, make assets folder in project respective path as: android/app/src/main/assets

  > paste this command in command prompt and run:

  > react-native bundle --platform android --dev false --entry-file index.android.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/

- 3 Then in assets folder there will appear file as index.android.bundle

- 4 Finally, run command: react-native run-android(while building new offline apk you need not to start server, your offline js file will help you to build apk file.)

- 5 Final, apk now build is ready for running in different devices(run apk from app/src/build/debug.apk).

- 6 Sometimes newly made apk will run without showing images, If application runs without image , then copy and paste the specific image resource folder into android/app/src/main/assets/(image source folder)

- 7 Again rerun application and thus build apk is ready for running.


## android 打包步骤 debug

- 1 添加文件夹: \android\app\src\main\assets
- 2 运行 react-native run-android
- 3 运行 react-native bundle --platform android --dev false --entry-file index.android.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/
- 4 运行 react-native run-android
- 5 \android\app\build\outputs\apk\app-debug.apk
- 6 如果图片异常,复制图片到 assets文件夹,rerun

## 真机调试 
 (https://facebook.github.io/react-native/docs/running-on-device.html)

-  通过 usb

> adb reverse tcp:8081 tcp:8081
> 执行 npm start 开启服务器即可,不需要每次 run-android 

- 通过 wifi

> app菜单 - Dev Setting 设置ip:port


## Generating Signed APK , 打包apk

http://reactnative.cn/docs/next/signed-apk-android.html#content

1. keytool -genkey -v -keystore my-release-key.keystore -alias rn-key-alias -keyalg RSA -keysize 2048 -validity 10000

 密码: 123456

2. 把生成的 my-release-key.keystore 文件放到你工程中的android/app文件夹下。

3. 编辑~/.gradle/gradle.properties

MYAPP_RELEASE_STORE_FILE=my-release-key.keystore
MYAPP_RELEASE_KEY_ALIAS=rn-key-alias
MYAPP_RELEASE_STORE_PASSWORD=123456
MYAPP_RELEASE_KEY_PASSWORD=123456

3.
添加签名到项目的gradle配置文件
编辑你项目目录下的android/app/build.gradle
```
android {
    ...
    defaultConfig { ... }
    signingConfigs {
        release {
            storeFile file(MYAPP_RELEASE_STORE_FILE)
            storePassword MYAPP_RELEASE_STORE_PASSWORD
            keyAlias MYAPP_RELEASE_KEY_ALIAS
            keyPassword MYAPP_RELEASE_KEY_PASSWORD
        }
    }
    buildTypes {
        release {
            ...
            signingConfig signingConfigs.release
        }
    }
}
```
4.生成 apk 
cd android && ./gradlew assembleRelease

android/app/build/outputs/apk/app-release.apk

5. 测试应用的发行版本
 cd android && ./gradlew installRelease



## 打包步骤 4 报错:
 Unable to process incoming event 'ProgressComplete ' (ProgressCompleteEvent)
添加参数:
 .\gradlew assembleRelease --console plain



 ## drawable vs mipmap
图片应该放在drawable文件夹下，而mipmap文件夹只适合放app icons ，之前Android Studio 1.1版本的时候app icons上上传几个不同分辨率的图片，
而现在Android Studio 2.1.2 已经把mipmap文件夹默认分为了不同分辨率的文件夹，方便适配。


## The SDK Build Tools revision (23.0.2) is too low for project ':jcore-react-native'. Minimum required is 25.0.0
android/build.grandle
```
  classpath 'com.android.tools.build:gradle:2.2.3'
```

