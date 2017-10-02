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

    - 获取DOM节点，以及节点的property和Atrribute
    
    - 获取父节点，获取子节点
    
    - 新增节点，删除节点
    


- DOM节点的attr和property有何区别

    - property只是一个JS对象的属性的修改
    
    - Attribute是对html标签属性的修改




###DOM的本质

树形结构


###DOM节点操作

DOM可以理解为：

浏览器把拿到的HTML代码。结构化一个浏览器能识别并且JS可操作的一个模型而已。


- 获取DOM节点

- property
JS对象标准属性

- Attribute
文档属性




###DOM结构操作

- 新增节点

- 获取父节点

parentElement

- 获取子节点

childNodes

- 删除节点

removeChild()






##BOM操作

- 如何检测浏览器的类型

- 拆解url的各部分



###navigator

var ua = navigator.userAgent;

var isChrome = us.indexOf('Chrome');

console.log(isChrome);




###screen

console.log(scren.width);

console.log(screen.height);





###location

console.log(location.href);

console.log(location.protocol);    //协议

console.log(location.host);     //域名

console.log(location.pathname);    //路径

console.log(location.search);    //参数

console.log(location.hash);    //#后边





###history











































