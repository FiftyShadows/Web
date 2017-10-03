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

- XMLhttpRequest

- 状态码说明



























































































































