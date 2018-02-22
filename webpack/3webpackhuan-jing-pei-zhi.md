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