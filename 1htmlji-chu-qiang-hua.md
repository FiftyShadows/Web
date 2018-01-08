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





























