#JS模块化

##CommonJS

- Modules/1.1.1

- 一个文件为一个模块

- 通过module.exports暴露模块接口

- 通过require引入模块

- 同步执行

![](/assets/360截图20180207210242388.jpg)



##AMD——Async Module Definition

- 使用define定义模块

- 使用require加载模块

- RequireJS

- 依赖前置，提前执行

![](/assets/360截图20180207210312902.jpg)



##CMD

- Common Module Definition

- 一个文件是一个模块

- 通过define来定义一个模块

- 通过require来加载一个模块

- SeaJS

- 尽可能懒执行

![](/assets/360截图20180207211057576.jpg)



##UMD

- Universal Module Definition

- 通用解决方案

- 三个步骤

    - 判断是否支持AMD
    
    - 判断是否支持CommonJS
    
    - 如果都没有，使用全局变量
    
![](/assets/360截图20180207233458916.jpg)



##ESM

- EcmaScript Module

- 一个文件一个模块

- export/import

- 在一个文件或模块中，export、import可以有多个，export default仅有一个

- 通过export方式导出，在导入时要加{ }，export default则不需要

- 使用export default命令，为模块指定默认输出，这样就不需要知道所要加载模块的变量名。export default输出一个叫做default的变量，然后系统允许你为它取任意名字。所以可以为import的模块起任何变量名，且不需要用大括号包含。

![](/assets/360截图20180207233704733.jpg)

![](/assets/360截图20180207234407709.jpg)

![](/assets/360截图20180207234554396.jpg)



##Webpack支持

- AMD

- ES Modules(推荐的)

- CommonJS







#CSS模块化

##CSS设计模式

- OOCSS    设计和结构分离，内容和容器分离

- SMACSS    可扩展和模块化结构，减少代码量，简化代码的维护

- Atomic CSS    原子CSS，基于视觉功能少的，单用途的CSS

- MCSS    多层级CSS

- AMCSS    针对属性的CSS设计

- BEM    块元素状态，bootstrap

- CSS Modules







#Webpack

##Webpack概述

##功能进化

####Webpack V1

- 编译、打包

- HMR(模块热更新)

- 代码分割

- 文件处理


####Webpack V2

- Tree Shaking    移除没用的代码，体积更小

- ES module

- 动态Import

- 新的文档


####Webpack V3

- Scope Hoisting(作用域提升)

- Magic Comments(配合动态import使用)


##核心概念

- Entry

- Output

- Loaders

- Plugins

####Entry

- 代码的入口

- 打包的入口

- 单个或多个

####Output

- 打包成的文件(bundle)

- 一个或多个

- 自定义规则

- 配合CDN

![](/assets/360截图20180208005653237.jpg)

####Loaders

- 处理文件

- 转化为模块

####常用Loader

- 编译相关

    - babel-loader、ts-loader
    
- 样式相关

    - style-loader、css-loader、less-loader、postcss-loader
    
- 文件相关

    - file-loader、url-loader
    
####Plugins

- 参与打包整个过程

- 打包优化和压缩

- 配置编译时的变量

- 极其灵活

####常用Plugins

- 优化相关

    - CommonsChunkPlugin
    
    - UglifyjsWebpackPlugin
    
- 功能相关

    - ExtractTextWebpackPlugin
    
    - HtmlWebpackPlugin
    
    - HotModuleReplacementPlugin
    
    - CopyWebpackPlugin
    
####名词

- chunk    代码块

- Bundle    打包好的代码

- Module    模块