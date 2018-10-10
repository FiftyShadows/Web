## 什么是DOCTYPE及作用

- DTD是一系列的语法规则，用来定义XML或HTML的文件类型。浏览器会使用它来判断文档类型，决定使用何种协议来解析，以及切换浏览器模式。

- DOCTYPE使用来声明文档类型和DTD规范，一个主要用途便是文件合法性验证。

    - HTML5    `<DOCTYPE html>`
    
    - HTML4.01 Strict    该DTD包含所有HTML元素和属性，但是不包括展示性和弃用的元素
    
    - HTML4.01 Transitional    该DTD包含所有HTML元素和属性，包括展示性和弃用的元素


![](/assets/微信截图_20181010153707.png)



## 重排Reflow

- DOM结构中的各个元素偶有自己的盒子(模型)，这些都需要浏览器根据各种样式来计算并根据计算结果将元素放到它该出现的位置，这个过程称之为Reflow



## 触发Reflow

- 当你增删改DOM节点时，会导致Reflow和Repaint

- 当你移动DOM的位置，或是搞个动画的时候

- 当你修改CSS样式的时候

- 当你Resize窗口的时候(移动端没有这个问题)，或是滚动的时候

- 当你修改网页的默认字体时



## 重绘Repaint



## 触发Repaint

- DOM改动

- CSS改动

- 如何避免最小长度的Repaint



## JS运行机制

- 任务队列

- 异步任务挂起

- 同步任务执行完之前，任何的异步任务都不会被执行

- EventLoop

```
console.log(1)
while(true){
    
}
console.log(2)
```

```
console.log(1)
setTimeout(function (){
    console.log(2)
}, 0)
while(true){
    
}
```

```
for(var i = 0; i < 4; i++){
    setTimeout(function (){
        console.log(i)    //4，注意最后一次i++
    }, 100)
}
```


![](/assets/bg2014100802.png)

















