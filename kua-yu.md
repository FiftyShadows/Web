## 为什么浏览器不支持跨域

- cookie LocalStorage

- DOM元素也有同源策略 iframe

- ajax也不支持跨域




## 实现跨域

- jsonp

- cors

- postMessage

- document.domain

- window.name

- location.hash

- http-proxy

- nginx

- websocket



## jsonp

- 只能发送get请求，不支持post，put，delete

- 不安全 xss攻击

```html
<script>
    function jsonp({url, params, cb}) {
        return new Promise((resolve, reject) => {
            let script = document.createElement('script')
            window[cb] = function(data){
                resolve(data)
                document.body.removeChild(script)
            }
            params = {...params, cb}
            let arr = []
            for (const key in params) {
                arr.push(`${key}=${params[key]}`)
            }
            script.src = `${url}?${arr.join('&')}`
            document.body.appendChild(script)
        })
    }
    jsonp({
        url: 'https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su',
        params: {wb: 'b'},
        cb: 'show'
    }).then(data => {
        console.info(data)
    })
</script>
```


## cors

```js
let express = require('express')
let app = express()
app.use(express.static(__dirname))

let whiteList = ['http://localhost:3000']
app.use((req, res, next) => {
    let origin = req.headers.origin
    if(whiteList.includes(origin)){
        //允许哪个源可以访问
        res.header('Access-Control-Allow-Origin', origin)
        // res.header('Access-Control-Allow-Origin', '*')   //星号不允许携带cookie
        //允许哪个头可以访问
        res.header('Access-Control-Allow-Headers', 'name')
        //允许哪个方法可以访问，默认get
        res.header('Access-Control-Allow-Methods', 'PUT')
        //允许携带cookie，不设置会报错
        res.header('Access-Control-Allow-Credentials', true)
        //预检的存活时间(秒)
        res.header('Access-Control-Max-Age', 600)
        //允许前端获取的头
        res.header('Access-Control-Expose-Headers', 'name')
        if (req.method === 'OPTIONS'){
            console.info('OPTIONS不作处理')
            res.end()   //OPTIONS请求不做任何处理
        }
    }
    next()
})
app.put('/getData', (req, res) => {
    res.end('copy that')
})
app.listen(4000)
```


## postMessage

```html
//a.html    http://localhost:3000/a.html
<iframe src="http://localhost:4000/b.html" frameborder="0" id="frame" onload="load()"></iframe>
<script>
    let frame = document.getElementById('frame')        
    frame.onload = function () {
        frame.contentWindow.postMessage('a页面发送数据', 'http://localhost:4000')
    }
    window.onmessage = function (e) {
        console.info('a接收到b页面发来的数据', e)
    }
</script>


//b.html    http://localhost:4000/b.html
<script>
    window.onmessage = function (e){
        console.info('b页面获取到a页面的postMessage', e)
        e.source.postMessage('b页面返回数据', e.origin)
    }    
</script>
```



## window.name

```
//a,b页面同域， c页面不同域window.name = 'xxx'

//a页面iframe指向c页面， c页面onload后修改src, window.name仍保留值
<iframe src="http://localhost:4000/c.html" frameborder="0" id="frame" onload="load()"></iframe>
<script>
    let first = true
    let frame = document.getElementById('frame')     
    frame.onload = function () {
        if(first){
            frame.src = 'http://localhost:3000/b.html'
            first = false
        }
        else{
            console.info(frame.contentWindow.name)
        }
    }
</script>
```



## location.hash

- 路径后面的hash值可以用来通信

```
//a,b页面同域， c页面不同域
//a.html
<iframe src="http://localhost:4000/c.html#pageA"></iframe>
<script>
    window.onhashchange = function (){
        console.info(location.hash)
    }
<script>

//c.html
<script>
    let iframe = document.createElement('iframe')
    iframe.src = 'http://localhost:3000/b.html#pageC'
    document.body.appendChild(iframe)
</script>

//b.html
<script>
    window.parentt.parent.location.hash = location.hash
<script>
```



## document.domain

```
//针对不同的子域名a.zf.cn:3000/a.html和b.zf.cn:4000/b.html
//a.html
<iframe src="http://b.zf.cn:4000/b.html" id="framme" onload="load()"></iframe>
<script>
    document.domain = 'zf.cn'
    function load(){
        frame.contentWindow.a
    }
<script>

//b.html
<script>
    document.domain = 'zf.cn'
    a = 100
</script>
```



## websocket



## nginx

```
location ~.*\.json{
    root json;
    add_header "Access-Control-Allow-Origin" "*"；
}
```




