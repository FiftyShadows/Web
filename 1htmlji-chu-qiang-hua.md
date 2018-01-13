##HTML常见元素

- head中的元素，不会在页面上留下直接的内容

    - meta
    
    - title
    
    - style
    
    - link
    
    - script
    
    - base

- body中的元素，内容直接出现在页面上

    - div/section/article/aside/header/footer

    - p
    
    - span/em/strong
    
    - table/thead/tbody/tr/td
    
    - ul/ol/li/dl/dt/dd
    
    - a
    
    - form/input/select/textarea/button

- `<meta charset="utf-8">`

- `<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no">`    ip不指定viewport，默认宽度是980px

- `<base href="/">`    指定基础路径





##HTML重要属性

- a[href,target]

- img[src,alt]    alternative替换资源

- table td[colspan,rowspan]    合并单元格

- form[target,method,enctype]    enctype针对post的编码格式，urlencode（文本）/formdata（数据编码，上传文件）

- input[type,value]

- button[type]

- select>option[value]

- label[for]


```html
/*name相同，只能选一个，不能同时选*/
<input type="radio" name="radio1" id="radio1-1"/>
<label for="radio1-1">选项一</label>
<input type="radio" name="radio1" id="radio1-2"/>
<label for="radio1-2">选项二</label>

/*普通按钮用来绑定事件*/
<button type="button">普通按钮</button>

/*submit按钮出现在form中才有意义*/
<button type="submit">提交按钮一</button>
<input type="submit" value="提交按钮二"/>

/*reset按钮出现在form中才有意义*/
<button type="reset">重置按钮</button>
```


- 面试：如果是ajax请求，并不通过form的submit提交，是否需要form元素

    - 不一定需要，仍然建议使用form，首先由submit，reset的特性可以利用
    
    - 用form可以批量的获取表单，jquery中有serialize()方法可以获取到整个表单所有的数据
    
    - 当有form的时候可以和一些框架，验证组件结合
    
    - 用户特性，密码管理工具可以记住密码，所以涉及到表单的时候，建议放上一个form




##如何理解HTML

- HTML“文档”

- 描述文档的“结构”

- 有区块和大纲

- 工具https://h5o.github.io/





##HTML5

- HTML4/4.01(SGML)

- XHTML(XML)    非常严格，所有的标签必须是小写，所有的属性必须是小写，所有属性必须要有值。XHTML2.0更加严格

- HTML5    基于HTML4

![](/assets/360截图20180108211344031.jpg)

- w3c验证网站： validator.w3.org


####新区块标签

- section

- article

- nav

- aside    不出现在大纲中，表示不太重要的东西，广告等


####表单增强

- 日期、时间、搜索

- 表单验证

- Placeholder自动聚焦


####新增语义

- header/footer头尾    可以放在articale中

- section/article区域    文章、导航、热点新闻等section；更完整的东西，博客，含标题、内容、评论等；section零碎的区块，article完整的区块

- nav导航    栏目，层级

- aside    不重要的内容，语义：侧边栏

- em/strong强调

- i icon    保留




##HTML元素分类

- 按默认样式分

    - 块级block
    
    - 行内inline
    
    - inline-block
    
    
- 按内容分

![](/assets/360截图20180108215642206.jpg)

https://www.w3.org/TR/html5/dom.html#phrasing-content





##HTML元素嵌套关系

- 块级元素可以包含行内元素

- 块级元素不一定能不含块级元素    div可以包含div，section可以包含div，p不可以包含div

- 行内元素一般不能包含块级元素

- 为什么a > div是合法的？    不一定合法，a的content model是transparent；

- `<p><a href="#"><div>P &gt; A &gt; DIV</div></a></p>`不合法






##HTML元素默认样式

- 默认样式的意义

- 默认样式带来的问题

    - list-style-position:inside;
    
- CSS Reset

- YUI CSS Reset

- *{margin: 0; padding: 0;}

- Normalize.css    样式修正





##面试真题

1. doctype的意义是什么

    - 让浏览器以标准模式渲染
    
    - 让浏览器知道元素的合法性
    
2. HTML、XHTML、HTML5的关系

    - HTML属于SGML
    
    - XHTML属于XML，是HTML进行XML严格化的结果
    
    - HTML5不属于SGML或XML，比XHTML宽松
    
3. HTML5有什么变化

    - 新的语义化元素
    
    - 表单增强
    
    - 新的API(离线、音视频、图形、实时通信、本地存储、设备能力)
    
    - 分类和嵌套变更
    
4. em和i有什么区别

    - em是语义化的标签，表强调
    
    - i是纯样式的标签，表斜体
    
    - HTML5中i不推荐使用，一般用作图标
    
5. 语义化的意义是什么

    - 开发者容易理解
    
    - 机器容易理解结构（搜索、读屏软件）
    
    - 有助于SEO
    
    - semantic microdata
    
6. 哪些元素可以自闭和

    - 表单元素input
    
    - 图片img
    
    - br、hr
    
    - meta、link
    
7. HTML和DOM的关系

     - HTML是“死”的
     
     - DOM由HTML解析而来，是活的
     
     - JS可以维护DOM
     
8. property(特性)和attribute(属性)的区别

    - attribue是“死”的
    
    - property是“活”的
    
9. form的作用有哪些

    - 直接提交表单
    
    - 使用submit/reset按钮
    
    - 便于游览器保存表单
    
    - 第三方库可以整体提取值
    
    - 第三方库可以进行表单验证
