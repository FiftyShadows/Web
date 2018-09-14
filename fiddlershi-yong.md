![](/assets/360截图18720118100141133.png)



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

可以选择隐藏Rules > Hide Connects
```



点击 Fiddler 左下角的“Capturing”。其实是File > Capture Traffic的快捷键，可以控制是否把 Fiddler 注册为PC系统代理，当左下角显示Capturing时，Capture Traffic是打开的，此时的IE的Internet选项>连接>局域网设置中的代理服务器是勾选的；否则是没有勾选的。 也就是显示了就抓pc的包，不显示就不抓pc的包。



## Composer    修改请求返回值

- Rules设置after response

- Transform设置无压缩

- TextView修改值

