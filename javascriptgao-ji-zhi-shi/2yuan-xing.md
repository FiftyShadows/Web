## 原型的实际应用

- 描述一下jquery/zepto如何使用原型

- 结合自己的项目经验，说一下自己开发的例子



## 如何体现原型的扩展性



## zepto如何使用原型


#### 为什么要把原型方法放在$.fn？

- 因为要扩展插件

- 在jQuery.fn/$.fn开发插件，扩展属性

    - $.fn.hetNodeName = function () { return this[0].nodeName}
    
    
    
#### 好处

- 只有$会暴露在window全局变量，避免全局变量污染

- 将插件扩展统一到$.fn.xxx这一个接口，方便使用





```js
//zepto源码

var zepto = {}

zepto.init = function (selector){
    //源码中，这的处理情况比较复杂，这里弱化了
    var slice = Array.prototype.slice;
    var dom = slice.call(document.querySelectorAll(selector));
    return zepto.Z(dom, selector);
}

//即使用zepto时候的$
var $ = function (selector){
    return zepto.init(selector);
}

//Z构造函数
function Z(dom, selector){
    var i, len = dom ? dom.length : 0;
    for(i = 0; i < len; i++) this[i] = dom[i];
    this.length = len;
    this.selector = selector || '';
}

zepto.Z = function (dom, selector){
    return new Z(dom, selector);
}

$.fn = {
    constructor: zepto.Z,
    css: function (key, value) {
    
    },
    html: function (value) {
    
    }
};

zepto.Z.prototype = Z.prototype = $.fn;
```



```js
//js模拟
(function (window){

    var zepto = {};
    
    function Z(dom, selector){
        var i, len = dom ? dom.length : 0;
        for(i = 0; i < len; i++) this[i] = dom[i];
        this.length = len;
        this.selector = selector || '';
    }
    
    $.fn = {
        constructor: zepto.Z,
        css: function (key, value) {
    
        },
        html: function (value) {
    
        }
    };
    
    Z.prototype = $.fn;
    
    zepto.Z = function (dom, selector){
        return new Z(dom, selector);
    }
    
    zepto.init = function (seleector){
        var slice = Array.prototype.slice;
        var dom = slice.call(document.querySelectorAll(selector));
        return zepto.Z(dom, selector);
    }

    var $ = function (selector){
        return zepto.init();
    }
    window.$ = $;
})(window)
```


```
//jquery的使用

(function (){
     var jQuery = function (jquery){
        rertun new jQuery.fn.init(selector);
     }
    
     jQuery.fn = jQuert.prototype = {
        consturctor: jQuery,
        css: function (key, value) {
    
        },
        html: function (value) {
    
        }
     };
    
     var init = jQuery.fn.int = function(selector){
         var slice = Array.prototype.slice;
         var dom = slice.call(document.querySelectorAll(selector));
         
         var i, len = dom ? dom.length : 0;
         for(i = 0; i < len; i++) this[i] = dom[i];
         this.length = len;
         this.selector = selector || '';
     }
     
     init.prototype = jQuery.fn;
     
     window.$ = window.jQuery = jQuery ;
}())
```



















