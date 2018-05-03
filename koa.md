##Koa 所有的功能都是通过中间件实现的，前面例子里面的main也是中间件。每个中间件默认接受两个参数

- Context: 表示一次对话的上下文（包括 HTTP 请求和 HTTP 回复）。通过加工这个对象，就可以控制返回给用户的内容。

- next: 只要调用next函数，就可以把执行权转交给下一个中间件。




##Context的属性

- ctx.response.body： 发送给用户的内容

- ctx.request.accepts： 判断一下，客户端希望接受什么数据（根据 HTTP Request 的Accept字段）。if (ctx.request.accepts('xml'))

- ctx.response.type: 指定返回类型。ctx.response.type = 'xml';

- fs.createReadStream：同步读取文件内容。fs.createReadStream('./demos/template.html')

- ctx.request.path: 可以获取用户请求的路径，由此实现简单的路由。if (ctx.request.path !== '/')

- 





##koa-route 模块

- 原生路由用起来不太方便，我们可以使用封装好的koa-route模块。app.use(route.get('/', main));




##koa-static模块

- 封装了静态资源（图片、字体、样式表、脚本......）的请求。

- const serve = require('koa-static');

- const main = serve(path.join(__dirname));





















