##题目

- 编写一个通用的事件监听函数

- 描述事件冒泡流程

    - DOM树形结构
    
    - 事件冒泡
    
    - 阻止冒泡
    
    - 冒泡应用
    

        

- 对于一个无限下拉加载图片的页面，如何给每个图片绑定事件




###通用事件绑定

```
function bindEvent(elem,type,fn){
    elem.addEventListener(type,fn);
}

```

完善通用绑定事件的函数
```
function bindEvent(elem,type,selector,fn){
    if(fn == null){
        fn = selector;
        selector = null;
    }
    elem.addEventListener(type,function (e){
        var target;
        if(selector){
            target = e.target;
            if(target.matches(selector)){
                fn.call(selector,e);
            }
        }else{
            fn(e);
        }
    });
}

```






###事件冒泡

![](/assets/360截图20171003152545764.jpg)




###事件代理

“事件代理”即是把原本需要绑定的事件委托给父元素，让父元素担当事件监听的职务。


- 代码简洁

- 减少浏览器内存占用





###关于IE低版本的兼容性

- IE低版本使用attachEvent绑定事件，和W3C标准不一样

- IE低版本使用量以非常少，很多网站都早已不支持

- 建议对IE低版本的兼容性：了解即可，无需深究

- 如果遇到对IE低版本要求苛刻的面试，果断放弃












##题目

- 手动编写一个ajax，不依赖第三方库

- 跨域的几种实现方式




###知识点

- XMLHttpRequest

![](/assets/360截图20171003162014787.jpg)



- 状态码说明

![](/assets/360截图20171003205936235.jpg)

![](/assets/360截图20171003210121533.jpg)




- 跨域




###IE兼容性问题

- IE低版本还用ActiveObject，和W3C标准不一样

- IE低版本使用量以非常少，很多网站都早已不支持

- 建议对IE低版本的兼容性：了解即可，无需深究

- 如果遇到对IE低版本要求苛刻的面试，果断放弃





###跨域

- 什么是跨域

    - 浏览器有同源策略，不允许ajax访问其他域接口
    
    - 跨域条件：协议、域名、端口，有一个不同就算跨域（https默认端口443）


- 可以跨域的三个标签

    - 但是有三个标签允许跨域加载资源
    
    - `<img src=xxx>`
    
    - `<link href=xxx>`
    
    - `<script src=xxx>`


- 三个标签的场景

    - `<img>用于打点统计，统计网站可能是其他域`

    - `<link><script>可以使用CDN，CDN的也是其他域`

    - `<script>可以用于JSONP，马上讲解`


- 跨域注意事项

    - 所有的跨域请求都必须经过信息提供方允许
    
    - 如果未经允许即可获取，那是浏览器同源策略出现漏洞






###JSONP

![](/assets/360截图20171003212654923.jpg)






###服务器端设置http header

![](/assets/360截图20171003213253756.jpg)








##题目

- 请描述一下cookie，sessionStorage和localStorage的区别？


































































































