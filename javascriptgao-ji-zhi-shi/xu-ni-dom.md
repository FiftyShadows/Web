## 问题

* vdom是什么？为何会存在vdom？

* vdom的如何应用，核心API是什么？

* 介绍一下diff算法



## 什么是vdom

* virtual dom，虚拟DOM(document object model)

* 用JS模拟DOM结构

* DOM变化的对比，放在JS层来做\(只有JS是图灵完备语言--能实现各种逻辑的语言\)

* 提高重绘性能，浏览器中DOM渲染是最昂贵的

- 每次render，整个table都会重新渲染一遍

![](/assets/360截图20180318184643532.jpg)

![](/assets/微信截图_20180701120835.png)

![](/assets/微信截图_20180701120811.png)

![](/assets/微信截图_20180701120725.png)

![](/assets/微信截图_20180701121341.png)



## 遇到的问题

* DOM操作是"昂贵"的，js运行效率高

* 尽量减少DOM操作，而不是"推到重来"

* 项目越复杂，影响就越严重

* vdom即可解决

![](/assets/360截图20180318203127426.jpg)



## 问题解答--为何会存在vdom？

* virtual dom，虚拟DOM

* 用JS模拟DOM结构

* DOM操作非常'昂贵'，尽量减少DOM操作

* 将DOM对比操作放在JS层，提高效率



## snabbdom

![](/assets/微信截图_20180701123038.png)

![](/assets/微信截图_20180701122853.png)

![](/assets/微信截图_20180701161315.png)

![](/assets/微信截图_20180701175743.png)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>

<body>
    <div id="container"></div>
    <button id="btn-change">change</button>
</body>

</html>
<script src="https://cdn.bootcss.com/snabbdom/0.7.1/snabbdom.js"></script>
<script src="https://cdn.bootcss.com/snabbdom/0.7.1/snabbdom-class.js"></script>
<script src="https://cdn.bootcss.com/snabbdom/0.7.1/snabbdom-props.js"></script>
<script src="https://cdn.bootcss.com/snabbdom/0.7.1/snabbdom-style.js"></script>
<script src="https://cdn.bootcss.com/snabbdom/0.7.1/snabbdom-eventlisteners.js"></script>
<script src="https://cdn.bootcss.com/snabbdom/0.7.1/h.js"></script>
<script>
    var snabbdom = window.snabbdom;

    var patch = snabbdom.init([
        snabbdom_class,
        snabbdom_props,
        snabbdom_style,
        snabbdom_eventlisteners
    ]);

    var h = snabbdom.h;

    var data = [
        {
            name: '张三',
            age: '20',
            address: '北京'
        },
        {
            name: '李四',
            age: '21',
            address: '上海'
        },
        {
            name: '王五',
            age: '25',
            address: '广州'
        },
    ];

    data.unshift({
        name: '姓名',
        age: '年龄',
        address: '地址'
    });

    var container = document.getElementById('container');

    // 渲染函数
    var vnode;
    function render(data) {
        var newVnode = h('table', {}, data.map(function (item) {
            var tds = [], i;
            for (i in item) {
                if (item.hasOwnProperty(i)) {
                    tds.push(h('td', {}, item[i] + ''));
                }
            }
            return h('tr', {}, tds);
        }));

        if (vnode) {
            patch(vnode, newVnode);
        }
        else {
            patch(container, newVnode);
        }

        vnode = newVnode;
    }

    // 初次渲染
    render(data);



    var btnChange = document.getElementById('btn-change');
    btnChange.addEventListener('click', function () {
        data[1].age = 30;
        data[2].address = '深圳';
        render(data);
    });
</script>
```




## diff算法

- 什么是diff算法    linux的基础命令

- 去繁就简

    - diff算法非常复杂，实现难度很大，源码量很大
    
    - 去繁就简，讲明白核心流程，不关心细节    二八原则：20%的功能满足80%需求

    - 面试官也大部分都不清楚细节，但是很关心核心流程
    
    - 去繁就简之后，依然具有很大挑战性，并不简单
    
- vdom为何用diff算法

    - DOM操作是"昂贵"的，因此尽量减少DOM操作
    
    - 找出本次DOM必须更新的节点来更新，其它的不更新
    
    - 这个"找出"的过程，就需要diff算法

- diff算法的实现流程




#### diff实现过程

- patch(container, vnode)

- patch(vnode, newVnode)

- 核心逻辑，createElement和updateChildren

![](/assets/微信截图_20180701182725.png)

![](/assets/微信截图_20180701182920.png)

![](/assets/微信截图_20180701190556.png)

![](/assets/微信截图_20180701191041.png)

- 不仅仅是以上内容

    - 节点新增和删除
    
    - 节点重新排序
    
    - 节点属性、样式、事件绑定
    
    - 如何极致压榨性能
































































