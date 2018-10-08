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

```
//a.html    http://localhost:3000/a.html
//b.html    http://localhost:3000/b.html
```










