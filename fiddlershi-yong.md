## AutoResponsder

- 替换线上服务器返回的文件，修复线上Bug

- 替换成状态码，延迟返回




## Composer模拟客户端向服务器发送请求




## tools Host

- 替换请求的地址，将线上地址替换到本地




## FiddlerScript模拟网络延迟

- OnBeforeRequest方法里加入`oSession["request-trickle-delay"] = "3000";`    `oSession["response-trickle-delay"] = "3000";`



## 第三方插件 Willow




## 官方插件

- JS Formatter

- Traffic Differ    网站优化对比





```
HttpTuunnel(也叫Http隧道，Http穿梭），是这样一种技术: 它用HTTP协议在要通信的Client和Server建立起一条”Tunnel”，然后Client和Server之间的通信，都是在这条Tunnel的基础之上。
```