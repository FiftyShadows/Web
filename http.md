## Https

- 公钥

- 私钥



## RESTful(Representational State Transfer)

- 如果一个架构符合REST原则，就称它为RESTful架构。

- URL定位资源，用HTTP动词（GET,POST,DELETE,DETC）描述操作。



## Http的三次握手

- TCP connection



## TCP协议三次握手

- 第一步：client 发送 syn 到server 发起握手；

- 第二步：server 收到 syn后回复syn+ack给client；

- 第三步：client 收到syn+ack后，回复server一个ack表示收到了server的syn+ack（此时client的56911端口的连接已经是established）。

```
- URG: 此标志表示TCP包的紧急指针域（后面马上就要说到）有效，用来保证TCP连接不被中断，并且督促中间层设备要尽快处理这些数据。

- ACK: 此标志表示应答域有效，就是说前面所说的TCP应答号将会包含在TCP数据包中。有两个取值: 0和1，为1的时候表示应答域有效，反之为0。

- PSH: 这个标志位表示Push操作。所谓Push操作就是指在数据包到达接收端以后，立即传送给应用程序，而不是在缓冲区中排队。

- RST: 这个标志表示连接复位请求。用来复位那些产生错误的连接，也被用来拒绝错误和非法的数据包。

- SYN: 表示同步序号，用来建立连接。SYN标志位和ACK标志位搭配使用，当连接请求的时候，SYN=1，ACK=0。连接被响应的时候，SYN=1，ACK=1。这个标志的数据包经常被用来进行端口扫描。扫描者发送一个只有SYN的数据包，如果对方主机响应了一个数据包回来 ，就表明这台主机存在这个端口。但是由于这种扫描方式只是进行TCP三次握手的第一次握手，因此这种扫描的成功表示被扫描的机器不很安全，一台安全的主机将会强制要求一个连接严格的进行TCP的三次握手。

- FIN: 表示发送端已经达到数据末尾，也就是说双方的数据传送完成，没有数据可以传送了，发送FIN标志位的TCP数据包后，连接将被断开。这个标志的数据包也经常被用于进行端口扫描。
```



## URI

- URI 统一资源标识，用来唯一标识互联网上的信息资源。包括URL和URN

- URL 统一资源定位器

- URN 永久统一资源定位符



## Cache-Control:max-age=100

- public, private

- must-revalidate

- no-cache, no-store



## 缓存验证

- last-modified配合if-modified-since

- etag配合if-none-match


![](/assets/360截图182903307410994.png)


![](/assets/360截图167204029912987.png)


物理层主要作用是定义物理设备如何传输数据

数据链路层在通信的实体间建立数据链路连接

网络层为数据在节点之间传输创建逻辑链路

传输层向用户提供可靠的端到端服务(传输层向高层屏蔽了下层数据通信的细节)

应用层为应用软件提供了很多服务

    - 构建与TCP协议之上
    
    - 屏蔽网络传输相关细节
    
