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

![](/assets/微信截图_20180701122853.png)

![](/assets/微信截图_20180701123038.png)





































































