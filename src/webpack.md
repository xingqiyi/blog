

## devtool: 'eval-source-map'  便于调试

## webpack-dev-server  监听代码


## babel
Babel其实是几个模块化的包，其核心功能位于称为babel-core的npm包中，
webpack可以把其不同的包整合在一起使用，对于每一个你需要的功能或拓展，你都需要安装单独的包
用得最多的是解析Es6的babel-env-preset包和解析JSX的babel-preset-react包
 

Babel其实可以完全在 webpack.config.js 中进行配置，
但是考虑到babel具有非常多的配置选项，为避免webpack.config.js太复杂，因此把babel的配置选项放在一个单独的名为 ".babelrc" 的配置文件中。
webpack会自动调用.babelrc里的babel配置选项），如下：
 

## loaders

通过使用不同的loader，webpack有能力调用外部的脚本或工具，实现对不同格式的文件的处理，比如说分析转换scss为css，或者把下一代的JS文件（ES6，ES7)转换为现代浏览器兼容的JS文件，对React的开发而言，合适的Loaders可以把React的中用到的JSX文件转换为JS文件。

Loaders需要单独安装并且需要在webpack.config.js中的modules关键字下进行配置，Loaders的配置包括以下几方面：

- test：一个用以匹配loaders所处理文件的拓展名的正则表达式（必须）
- loader：loader的名称（必须）
- include/exclude:手动添加必须处理的文件（文件夹）或屏蔽不需要处理的文件（文件夹）（可选）；
- query：为loaders提供额外的设置选项（可选）
 
## css-loader 和 style-loader，
 
 css-loader 使你能够使用类似@import 和 url(...)的方法实现 require()的功能
 style-loader 将所有的计算后的样式加入页面中
 二者组合在一起使你能够把样式表嵌入webpack打包后的JS文件中


## CSS module

 被称为CSS modules的技术意在把JS的模块化思想带入CSS中来，通过CSS模块，所有的类名，动画名默认都只作用于当前模块。Webpack对CSS模块化提供了非常好的支持，只需要在CSS loader中进行简单配置即可，然后就可以直接把CSS的类名传递到组件的代码中，这样做有效避免了全局污染。
 

## CSS 预处理 loader

- Less Loader
- Sass Loader
- postcss-loader 和 autoprefixer


## 插件
Loaders和Plugins常常被弄混，但是他们其实是完全不同的东西，
可以这么来说，loaders是在打包构建过程中用来处理源文件的（JSX，Scss，Less..），一次处理一个，
插件并不直接操作单个文件，它直接对整个构建过程其作用。

常用插件:
- HtmlWebpackPlugin
- Hot Module Replacement
