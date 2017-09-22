

## 
初始化  版本指定
react-native init AwesomeProject  --version 0.44.3





## no bundle url present make sure

```
Edit <your_project_folder>/ios/<project_name>/AppDelegate.m and change the jsCodeLocation variable as follows:

jsCodeLocation =
    [NSURL URLWithString:@"http://127.0.0.1:8081/index.ios.bundle?platform=ios&dev=true"];
```



## 
 在开发者菜单中选择"Debug JS Remotely"选项，
 即可以开始在Chrome中调试JavaScript代码。点击这个选项的同时会自动打开调试页面 http://localhost:8081/debugger-ui.




## ios 真机 调试

RCTWebSocketExecutor.m
localhost 改 ip

AppDelegate.m   改为 ip
jsCodeLocation =   [NSURL URLWithString:@"http://192.168.1.255:8081/index.ios.bundle?platform=ios&dev=true"];



## 真机调试 设置 team 报错
Failed to create provisioning profile. The app ID

选择 ssr



##  真机调试时  打包时

Please unlock your device and reattach. (0xE80000E2).

解决方法是：打开手机设置->通用->还原->还原位置与隐私；
然后会有弹窗提示你是否信任此电脑，点击信任，重启Xcode之后，运行项目到手机上
解决办法来自于：iOS中项目运行到真机上提示设备被锁定解决方法Development cannot be enabled while your device is locked. ，谢谢





##  No devices are booted.

重启模拟器

Boot the respective simulator manually
Go to spotlight search and start to type simulator
When spotlight presents the search result, choose the simulator app and hit Enter
Go to simulator app's menu: Hardwire -> Device -> iOS 10.0 -> iPhone 6 and select it
Reset
Go to simulator app's menu: Simulator -> Reset Content and Settings...
Retry
Command react-native run-ios again



## Print: Entry, ":CFBundleIdentifier", Does Not Exist
```
rm -rf ~/.rncache

```


## 模拟器 与真机直接的切换   打包时需改成真机

``` 
AppDelegate.m
#模拟器
 jsCodeLocation = [[RCTBundleURLProvider sharedSettings] jsBundleURLForBundleRoot:@"index.ios" fallbackResource:nil];
#真机：
jsCodeLocation = [[NSBundle mainBundle] URLForResource:@"index.ios" withExtension:@"jsbundle"];
```

##  

##  no dimension set for key window

```
删掉 ios/build 重运行
```


##  根目录文件不能叫 index.js   猜测应该是与 index.ios.js 冲突

##  打包
```
打包 需要在 ios   文件夹; android 需要新建assets 文件夹
 
 http://blog.csdn.net/sinat_34380438/article/details/76614309


```

## 报错：Invariant Violation:Application XXXX has not been registered.

A：请确保index.*.js中的

AppRegistry.registerComponent('项目名',() => ...);
与appDelegate.m中的

RCTRootView*rootView = [[RCTRootViewalloc]initWithBundleURL:jsCodeLocation
moduleName:@"项目名" launchOptions:launchOptions];
或是MainActivity.java中的

@Override
protected String getMainComponentName() {
  return "项目名";
}
都保持一致。


## 
Q：有一些示例代码中有奇怪的问号，比如function foo(x:?string)，代表什么意思？

A：这是通过一个名为flow的外部工具为javascript加上强类型检查的功能，不影响编译和运行。直接无视就好。


##  Failed to create provisioning profile



I have had this error multiple times and what solves it for me is the following:

In the list with the view of all certificates, right click on each row and move each certificate to trash (go to Xcode > Preferences > Choose account > Click View Details)
Go to member center download the right certificates again and click on them so
Restart Xcode
Go to build settings and set the right Code signing for debug/release - you should be able to see an option on the row that says "Identities from profile..."
If this doesn't work then you should consider revoking your certificate and then create a new one and the do the steps above again.