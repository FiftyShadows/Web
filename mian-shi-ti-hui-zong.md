前言

又到了金三银四的季节，小伙伴们你们是否满足现状，是否能够接受公司给你的加薪、年终奖金。是不是需要看看web前端行情再做打算呢？我根据目前掌握的知识，以及了解到的内容，和面试其他同学的时候注意事项，给出以下建议希望你能够找到更适合的岗位。

尊重被尊重

面试是一个很严肃的话题，作为一名求职者应该尊重面试官。

着装干净整齐（有的公司会要求西装）
面试时候坐姿端正自然，切勿翘腿、葛优躺
认真倾听，切勿玩手机、接电话
面试打分

我们公司面试求职者打分流程是

表达、沟通能力（30%）
技术能力（40%）
礼貌礼节（20%）
其他（10%）
面试流程

大致面试流程

笔试（有的没有）
自我介绍
聊技术
问面试者你有什么想问的吗？
前端技术

前端技术面试大致分一下几大方向

HTML

1、HTML5新增了哪些内容或API，使用过哪些
    document.querySelector()和document.querySelectorAll()方法；HTML5之classList属性；HTML5之全屏FullScreen；Page Visibility
2、input和textarea的区别
    <input>是一个单行输入框，有value属性（value属性指定初始值），但是它不能自动换行；用来放置字数较少的单行文字内容；<textarea>是一个多行输入框，没有value属性，但是它能自动换行；一般让用户可以输入多行文字,输入的文字信息量相比较大
3、用一个div模拟textarea的实现
    `<div contenteditable="true"></div>` ；设定一个最大高度(max-height)，让其超出的时候出现滚动条
4、什么是语义化的HTML?
    语义化的HTML就是写出的HTML代码，符合内容的结构化（内容语义化），选择合适的标签（代码语义化），能够便于开发者阅读和写出更优雅的代码的同时让浏览器的爬虫和机器很好地解析。
　　1.语义化有利于SEO，有利于搜索引擎爬虫更好的理解我们的网页，从而获取更多的有效信息，提升网页的权重。
　　2.在没有CSS的时候能够清晰的看出网页的结构，增强可读性。
　　3.便于团队开发和维护，语义化的HTML可以让开发者更容易的看明白，从而提高团队的效率和协调能力。
　　4.支持多终端设备的浏览器渲染。
5、HTML5 为什么只需要写 !DOCTYPE HTML？
    HTML 4.01 中的 doctype 需要对 DTD 进行引用，因为 HTML 4.01 基于 SGML。
    而 HTML 5 不基于 SGML，因此不需要对 DTD 进行引用，但是需要 doctype 来规范浏览器的行为。
    其中，SGML是标准通用标记语言,简单的说，就是比HTML,XML更老的标准，这两者都是由SGML发展而来的。
    BUT，HTML5不是的。
    
6、Doctype作用？标准模式与兼容模式各有什么区别?
    <!DOCTYPE>声明位于位于HTML文档中的第一行，处于 <html> 标签之前。作用：告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。标准模式的排版 和JS运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示,模拟老式浏览器的行为以防止站点无法工作。
简单的说，就是尽可能的显示能显示的东西给用户看。
    
7、html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML和HTML5？
    语义化更好的内容标签（header,nav,footer,aside,article,section）;音频、视频API(audio,video);画布(Canvas) API;地理(Geolocation) API;本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；sessionStorage 的数据在浏览器关闭后自动删除;表单控件，calendar、date、time、email、url、search ;新的技术webworker, websocket, Geolocation;纯表现的元素：
    移除的元素：basefont，big，center，font, s，strike，tt，u；对可用性产生负面影响的元素：frame，frameset，noframes；
    支持HTML5新标签：IE8/IE7/IE6支持通过document.createElement方法产生的标签，可以利用这一特性让这些浏览器支持HTML5新标签，浏览器支持新标签后，还需要添加标签默认的样式;当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架:
    ```
       <!--[if lt IE 9]> 
       <script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script> 
       <![endif]--> 
    ```

8、请描述一下 cookies，sessionStorage 和 localStorage 的区别？
    1.存储大小:
        cookie数据大小不能超过4k。
        sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。
        
    2.有效时间:
        localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
        sessionStorage  数据在当前浏览器窗口关闭后自动删除。
        cookie          设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭
        
    3.数据与服务器之间的交互方式:
        cookie的数据会自动的传递到服务器，服务器端也可以写cookie到客户端
        sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。
        
    获取cookie内容:`var data=document.cookie;//获取对应页面的cookie `
    
9.关于height：100%无效的解决办法与细节
    对于块级元素浏览器总是默认使其宽度等于父容器宽度的100%不需要自己设定，但是对高度的计算就并非这样了，当没有显式得定义容器的高度时，其高度由其包裹的内容决定，当显式得定义高度时，容器的高度就为设定的值，使用overflow可以对超出高度的内容进行处理。
    

CSS

1、简要说一下float的特性
    1. 应用于文字围绕图片
    2. 创建一个块级框
    3. 多列浮动布局
    4. 浮动元素的宽度、高度自适应，但可以设置其值。
    
2、CSS隐藏元素的几种方法（至少说出三种）
     opacity 设为 0、将 visibility 设为 hidden、将 display 设为 none 或者将 position 设为 absolute 然后将位置设到不可见区域。z-index、overflow

3、CSS清除浮动的几种方法（至少两种）
    父级div定义 height;结尾处加空div标签 clear:both;添加一个空div，利用css提高的clear:both清除浮动，让父级div能自动获取到高度;父级div定义 伪类:after 和zoom;父级div定义 overflow:hidden;父级div定义 overflow:auto;父级div 也一起浮动;父级div定义 display:table;结尾处加 br标签 clear:both 

4、CSS居中（包括水平居中和垂直居中）
    水平居中：
    ```
        //不知道自己高度和父容器高度的情况下, 利用绝对定位只需要以下三行：
        parentElement{
            position:relative;
        }
    
         childElement{
                position: absolute;
                top: 50%;
                transform: translateY(-50%);
        
         }
         //若父容器下只有一个元素，且父元素设置了高度，则只需要使用相对定位即可
         parentElement{
        height:xxx;
        }
    
        .childElement {
          position: relative;
          top: 50%;
          transform: translateY(-50%);
        }
    ```
    Flex 布局
    1、父元素高度确定的单行文本            设置  height = line-height      
    2、父元素高度确定的多行文本
        a:插入  table （插入方法和水平居中一样），然后设置  vertical-align:middle            
        b:先设置  display:table-cell  再设置  vertical-align:middle

5、介绍一下CSS的盒子模型？
    1）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)
    2）有两种， IE 盒子模型、标准 W3C 盒子模型；IE的content部分包含了 border 和 padding;

6、CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？ CSS3新增伪类有那些？
    CSS 选择符：
        1)id选择器(# myid)
        2)类选择器(.myclassname)
        3)标签选择器(div, h1, p)
        4)相邻选择器(h1 + p)
        5)子选择器(ul > li)
        6)后代选择器(li a)
        7)通配符选择器( * )
        8)属性选择器(a[rel = "external"])
        9)伪类选择器(a: hover, li:nth-child)
    可继承的样式：
        1)font-size
        2)font-family
        3)color
        4)text-indent
    不可继承的样式：
        1)border
        2)padding
        3)margin
        4)width
        5)height
    优先级算法：
        1)优先级就近原则，同权重情况下样式定义最近者为准;
        2)载入样式以最后载入的定位为准;
        3)!important >  id > class > tag  
        4)important 比 内联优先级高，但内联比 id 要高
    CSS3新增伪类举例：
        1)p:first-of-type  选择属于其父元素的首个 <p> 元素的每个 <p> 元素。
        2)p:last-of-type   选择属于其父元素的最后 <p> 元素的每个 <p> 元素。
        3)p:only-of-type  选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。
        4)p:only-child     选择属于其父元素的唯一子元素的每个 <p> 元素。
        5)p:nth-child(2)  选择属于其父元素的第二个子元素的每个 <p> 元素。
        6):enabled :disabled 控制表单控件的禁用状态。
        7):checked         单选框或复选框被选中。

7、CSS3有哪些新特性？
    CSS3有哪些新特性？
        1)CSS3实现圆角（border-radius），阴影（box-shadow），
        2)对文字加特效（text-shadow、），线性渐变（gradient），旋转（transform）
        3)transform:rotate(9deg) scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);// 旋转,缩放,定位,倾斜
        4)增加了更多的CSS选择器  多背景 rgba 
        5)在CSS3中唯一引入的伪元素是 ::selection.
        6)媒体查询，多栏布局
        7)border-image

8、什么是BFC？

9、如何实现等高布局？

10、li与li之间有看不见的空白间隔是什么原因引起的？有什么解决办法？
    浏览器的默认行为是把inline元素间的空白字符（空格换行tab）渲染成一个空格，也就是我们上面的代码<li>换行后会产生换行字符，而它会变成一个空格，当然空格就占用一个字符的宽度。

11、伪元素与伪类的区别？
12、响应式布局你是如何实现？如果兼容低版本浏览器你会如何实现？
13、z-index层叠顺序是？
14、过渡与动画的区别是什么？
15、什么是CSS reset？
16、CSS Sprite是什么，谈谈这个技术的优缺点？
17、px与em、rem区别？
18、你能描述一下渐进增强和优雅降级之间的不同吗?
    优雅降级一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。渐进增强针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。

JavaScript

1、作用域
2、变量提升
3、闭包是什么？你在工作中是否使用过？
4、call与apply区别？
5、手写bind函数？
6、原型与原型链
7、继承，几种继承方式？他们的优缺点？
8、数组基本操作都有什么？
9、设计模式你都知道那些？
10、JavaScript中this是如何工作的
11、箭头函数
12、事件模型及事件代理/委托
13、如何添加、删除、修改节点
14、什么是jsonp？
15、高阶函数
16、js线程你是如何理解的？
17、setTimeout与setInterval有何区别？使用时需要注意什么？
18、什么是隐式转换？需要注意什么？
19、如何将120542.00转换为120,542.00
20、AMD与CMD区别？

框架

vue (vuex、vue-router、ssr)
1、组件传值prop
2、路由
3、vue如何实现双向数据绑定
4、过滤器
5、computed
6、vue生命周期钩子函数
7、插槽

react (react-native)
1、render
2、生命周期
3、更改状态State
4、jsx
5、组件传值Props

angularjs
打包工具

1、gulp
2、webpack

代码管理工具

1、SVN
2、Git

最后总结

上面是我大致总结的一些面试题与需要注意的事项，至于打包工具与三大框架更为细致的问题没有太多的时间进行详细描述。希望上面的总结对你有用。

```
if (!(a in window)){
    var a = 10;    //变量提升
}
console.log(a);    //undefined
```



