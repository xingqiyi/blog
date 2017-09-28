## 注释 
组件内部注释 : /*  */
组件之间需要 包起来: {/**/}  



onEndReached 会执行多次




justifyContent是相对于主轴的对齐方式，而alignItems是相对于交叉轴的对齐方式。
主轴和交叉轴是相对于flexDireaction的值而言的，主轴和交叉轴是相对于flexDireaction的值而言的，主轴和交叉轴是相对于flexDireaction的值而言的




Most of the time, you can use React.PureComponent instead of writing your own shouldComponentUpdate.
It only does a shallow comparison, so you can't use it if the props or state may have been mutated in a way that a shallow comparison would miss.