## 什么是单线程，和异步有什么关系

- 单线程-只有一个线程，同时只能做一件事，两段代码不能同时执行

- 原因-避免DOM渲染的冲突

    - 浏览器需要渲染DOM
    
    - JS可以修改DOM结构
    
    - JS执行的时候，浏览器DOM渲染会暂停
    
    - 两段JS也不能同时执行(都修改DOM就冲突了)
    
    - webworker支持多线程，但是不能访问DOM

- 解决方案-异步

    - 没按照书写顺序执行，可读性差
    
    - callback中不容易模块化


## 什么是event-loop

- 事件轮询，JS实现异步的具体解决方案

- 同步代码，直接执行

- 异步函数先放在异步队列中

- 带同步函数执行完毕，轮询执行异步队列的函数




## 是否用过jQuery的Deferred

- 无法改变JS异步和单线程的本质

- 只能从写法上杜绝callback这种形式

- 它是一种语法糖形式，但是解耦了代码

- 很好的体现： 开放封闭原则

![](/assets/微信截图_20180630214521.png)

![](/assets/微信截图_20180630214740.png)

![](/assets/微信截图_20180630220804.png)

![](/assets/微信截图_20180630220427.png)


#### 总结dtd的API可分成两类，用意不同

- 第一类： dtd.resolve    dtd.reject

- 第二类： dtd.then   dtd.done    dtd.fail

- 这两类应该分开，否则后果很严重

![](/assets/微信截图_20180630224005.png)

![](/assets/微信截图_20180630224154.png)

![](/assets/微信截图_20180630224345.png)

#### 问题解答

- 可以jQuery1.5对ajax的改变举例

- 说明如何简单的封装、使用Deferred(封装waitHandle函数，开放封闭原则的好处)

- 说明promise和Deferred的区别(只能被动监听，没法主动修改)    图灵机 图灵完备语言



## Promise的基本使用和原理

- 基本语法

- 异常捕获

![](/assets/微信截图_20180630230752.png)

- 多个串联

![](/assets/微信截图_20180630233803.png)

- Promise.all和Promise.race

![](/assets/微信截图_20180630233929.png)

- Promise标准

    - 通过bluebird使低级浏览器支持Promise标准
    
    - 关于"标准"的闲谈
    
         - 任何技术推广使用都需要一套标准来支撑
         
         - 如html、js、css、http等，无规矩不成方圆
         
         - 任何不符合标准的东西，终将会被用户抛弃
         
         - 不要挑战标准，不要自造标准
            
    - 状态变化
    
        - 三种状态：pending fulfilled rejected
        
        - 初始状态是pending
        
        - pending变为fulfilled，或者pending变为rejected
        
        - 状态变化不可逆
    
    - then 返回的必须是一个Promise实例
    
```js
    function loadImg(src) {
        return new Promise(function (resolve, reject) {
            var img = document.createElement('img');
            img.onload = function () {
                // throw new Error('自定义错误');
                resolve(img);
            }
            img.onerror = function () {
                reject('图片加载失败');
            }
            img.src = src;
        });
    }

    var src1 = 'https://www.imooc.com/static/img/index/logo.png1';
    var src2 = 'https://img1.mukewang.com/545863570001cf3702200220-100-100.jpgx';

    // loadImg(src)
    //     .then(function (img) {
    //         console.info(1, img.width);
    //         return img;
    //     })
    //     .then(function (img) {
    //         console.info(2, img.height);
    //     })
    //     .catch(function (ex) {
    //         console.info(ex);
    //     });

    let result1 = loadImg(src1);
    let result2 = loadImg(src2);
    Promise.all([result1, result2]).then(function (datas) {
        console.info('all1', datas[0]);
        console.info('all2', datas[1]);
    })
    .catch(function (ex) {
        console.info('all-err', ex);
    });
    Promise.race([result1, result2]).then(function (data) {
        console.info('race', data);
    })
    .catch(function (ex) {
        console.info('race-err', ex);
    });
```



## 介绍一下async/await(和Promise的区别、联系)

- then只是将callback拆分了

- async/await是最直接的同步写法

    - 使用await,函数必须用async标识
    
    - await后面跟的是一个Promise实例
    
    - 需要babel-polyfill
    
- 用try……catch处理异常
    
![](/assets/微信截图_20180701105038.png)

## 总结一下当前JS解决异步的方案

- jQuery Deferred

- Promise

- Async/Await

- Generator

    - 原理比较复杂
    
    - 不是异步的直接替代方式
    
    - 有更好更简洁的解决方案 async/await
    
    - koa使用async/await























































