##常说的JS（浏览器执行的JS）包含两部分：

JS基础知识：ECMA262标准

JS-Web-API：W3C标准


##W3C标准中关于JS的规定有：

- DOM操作

- BOM操作

- 事件绑定

- ajax请求（包括http协议）

- 存储

***

但是W3C标准没有规定任何JS基础相关的东西

不管什么变量类型、原型、作用域和异步

只管定义用于浏览器中JS操作页面的API和全局变量


***

全面考虑，JS内置的全局对象和函数有哪些？

- 之前讲过的Object Array Boolean String Json等

- 刚刚提到的window document

- 接下来还有继续讲到的所有未定义的全局变量，如navigator.userAgent





##DOM操作

- DOM是哪种基本的数据结构？

- DOM操作的常用API有哪些

- DOM节点的attr和property有何区别



###DOM的本质

树形结构


###DOM节点操作

DOM可以理解为：

浏览器把拿到的HTML代码。结构化一个浏览器能识别并且JS可操作的一个模型而已。


- 获取DOM节点

- prototype

- Attribute




















