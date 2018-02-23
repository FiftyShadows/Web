##webpack watch mode

- webpack -w --progress --display-reasons --color




##webpack-dev-server

- live reloading    刷新浏览器

- 打包文件？NO    打包文件运行在内存中，不在本地

- 路径重定向

- https

- 在浏览器中显示编译错误

- 接口代理

- 模块热更新    不刷新浏览器更新代码

####devServer配置

- inline    是否使用iframe

- contentBase    提供内容的路径，静态需要指定

- port    监听端口

- historyApiFallback    服务端渲染

- https

- proxy    远程接口代理

- hot    模块热更新，某个时间内替换掉代码

- openpage    指定最先打开的页面

- lazy    访问的资源才会去打包，适合多页面应用

- overlay    遮罩，编译错误提示，eslint





##Source Map调试

- Devtool

- webpack.SourceMapDevToolPlugin

- webpack.EvalSourceMapDevToolPlugin

- 通过插件可以更灵活控制SourceMap的生成

####SourceMap七种模式

- Development

    - eval

    - eval-source-map

    - cheap-eval-source-map

    - cheap-module-eval-source-map
    
- Production

    - source-map
    
    - hidden-source-map
    
    - nosource-source-map
    
![](/assets/360截图20180223222019824.jpg)
    
####css,less,sass,uglyfy需要开启SourceMap

- css-loader.option.sourcemap

- less-loader.option.sourcemap

- sass-loader.option.sourcemap

####常用的

- eval

- source-map

- cheap-module-source-map