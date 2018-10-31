## react路由的两种方式

- HashRouter:利用 hash 实现路由切换

    - hashchange
    
    - 用于静态文件服务

- BrowerRouter:利用 H5 api 实现路由的切换

    - 没有#
    
    - history.pushState({p:path})    三个参数：状态对象，标题，URL
    
    - url回车后回去找真实的路径，需要后端配合
    
    - 用于动态网站服务
    

```html
//BrowerRouter
<a onclick="push('/a')">a</a>
<a onclick="push('/b')">b</a>

<script>
    function push(path){
        history.pushState({p:path}, null, path)
    }
    //监听不到pushState，但能监听到浏览器前进后退
    window.addEventListener('popstate', e => {
        console.info(history)
        console.info(e)
    })
</script>
```