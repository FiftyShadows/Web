##内容

- 创建Web服务器

- Http通讯

- WebSocket通讯




##创建web服务器

- 使用Nodejs创建服务器

- 使用Express创建restful的http服务

- 监控服务器文件的变化


全局安装nodemon监控服务器文件的变化

nodemon app.js





##Http通讯

![](/assets/360截图20171025174703604.jpg)

![](/assets/360截图20171025175208531.jpg)

![](/assets/360截图20171025175339519.jpg)

get方法只是定义了http请求，只有调用Subscribe方法才发送。


####管道处理http流

![](/assets/360截图20171025175701902.jpg)

![](/assets/360截图20171025175639833.jpg)


####发送http请求的时候带上请求头

![](/assets/360截图20171025180207948.jpg)




##WeBsokect通讯

创建WebSocket服务器，使用WebSocket协议通讯

- 低负载二进制协议，主流浏览器已支持

- WebSocket允许在同一个链接中同时进行双方向的数据传递，长链接协议，不需要在每次发送和接收数据时建立连接，所以延迟比http低，不需要携带链接相关的信息，传递的消息数据比http少

![](/assets/360截图20171025181930567.jpg)




