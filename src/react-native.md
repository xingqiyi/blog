## 注释 
组件内部注释 : /*  */
组件之间需要 包起来: {/**/}  


 


### Flex
justifyContent是相对于主轴的对齐方式，而alignItems是相对于交叉轴的对齐方式。
主轴和交叉轴是相对于flexDireaction的值而言的，主轴和交叉轴是相对于flexDireaction的值而言的，主轴和交叉轴是相对于flexDireaction的值而言的



### PureComponent
Most of the time, you can use React.PureComponent instead of writing your own shouldComponentUpdate.
It only does a shallow comparison, so you can't use it if the props or state may have been mutated in a way that a shallow comparison would miss.


### android App 图标
D:\xingqiyi\oaapp\android\app\src\main\res\mipmap-hdpi
jpush 通知栏 默认会使用 app图标


### 触摸组件
RN 的组件除了 Text，其他组件默认是不支持点击事件，也不能响应基本触摸事件，
所以 RN 中提供了几个直接处理响应事件的组件，
TouchableHighlight
TouchableOpacity
TouchableNativeFeedback
TouchableWithoutFeedback。
这几个组件的功能和使用方法基本类似，只是 Touch 的反馈效果不一样，
Touchable** 有如下几个回调方法：

onPressIn：点击开始；
onPressOut：点击结束或者离开；
onPress：单击事件回调；
onLongPress：长按事件回调。