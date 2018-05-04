##Koa 所有的功能都是通过中间件实现的，前面例子里面的main也是中间件。每个中间件默认接受两个参数

- Context: 表示一次对话的上下文（包括 HTTP 请求和 HTTP 回复）。通过加工这个对象，就可以控制返回给用户的内容。

- next: 只要调用next函数，就可以把执行权转交给下一个中间件。




##Context的属性

- ctx.response.body： 发送给用户的内容

- ctx.request.accepts： 判断一下，客户端希望接受什么数据（根据 HTTP Request 的Accept字段）。if (ctx.request.accepts('xml'))

- ctx.response.type: 指定返回类型。ctx.response.type = 'xml';

- fs.createReadStream：同步读取文件内容。fs.createReadStream('./demos/template.html')

- ctx.request.path: 可以获取用户请求的路径，由此实现简单的路由。if (ctx.request.path !== '/')

- ctx.response.redirect: 可以发出一个302跳转，将用户导向另一个路由。ctx.response.redirect('/');





##koa-route 模块

- 原生路由用起来不太方便，我们可以使用封装好的koa-route模块。app.use(route.get('/', main));




##koa-static模块

- 封装了静态资源（图片、字体、样式表、脚本......）的请求。

- const serve = require('koa-static');

- const main = serve(path.join(__dirname));




##中间件

- 因为它处在 HTTP Request 和 HTTP Response 中间，用来实现某种中间功能。app.use()用来加载中间件。

- Koa 所有的功能都是通过中间件实现的，前面例子里面的main也是中间件。每个中间件默认接受两个参数，第一个参数是 Context 对象，第二个参数是next函数。只要调用next函数，就可以把执行权转交给下一个中间件。




##中间件栈

- 多个中间件会形成一个栈结构（middle stack），以"先进后出"（first-in-last-out）的顺序执行。

- 如果中间件内部没有调用next函数，那么执行权就不会传递下去。




##异步中间件

- 如果有异步操作（比如读取数据库），中间件就必须写成 async 函数。

- const main = async function (ctx, next) {
  ctx.response.type = 'html';
  ctx.response.body = await fs.readFile('./demos/template.html', 'utf8');
};

- fs.readFile是一个异步操作，必须写成await fs.readFile()，然后中间件必须写成 async 函数。






##koa-compose模块(中间件的合成)

- 可以将多个中间件合成为一个。const middlewares = compose([logger, main]);





##错误处理

- 如果代码运行过程中发生错误，我们需要把错误信息返回给用户。HTTP 协定约定这时要返回500状态码。

- ctx.throw: 抛出错误。ctx.throw(500);/ctx.throw(400, '.name required');

- 如果将ctx.response.status设置成404，就相当于ctx.throw(404)，返回404错误。ctx.response.status = 404;





##处理错误的中间件

- 为了方便处理错误，最好使用try...catch将其捕获。但是，为每个中间件都写try...catch太麻烦，我们可以让最外层的中间件，负责所有中间件的错误处理。

- try...catch内使用await next();





##error 事件的监听

- 运行过程中一旦出错，Koa 会触发一个error事件。监听这个事件，也可以处理错误。

- app.on('error', (err, ctx) =>
  console.error('server error', err);
);




##释放 error 事件

- 如果错误被try...catch捕获，就不会触发error事件。这时，必须调用ctx.app.emit()，手动释放error事件，才能让监听函数生效。ctx.app.emit('error', err, ctx);





##Cookies

- ctx.cookies.set('view', n);

- ctx.cookies.get('view') 




##koa-body模块

- koa-body模块可以用来从 POST 请求的 (表单) 数据体里面提取键值对。

- ctx.request.body

- const koaBody = require('koa-body');  先调用app.use(koaBody());

- koa-body模块还可以用来处理文件上传。

- ctx.request.body.files





















