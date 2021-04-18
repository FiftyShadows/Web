# 3.CSS布局

## 常用布局方法

* table表格布局
* float浮动+margin
* inline-block布局
* flexbox布局

## 表格布局

```text
    <table style="width:800px;">
        <tr>
            <td class="left" style="width:200px;">左</td>
            <td class="right">右</td>
        </tr>
    </table>
```

特点

* 设置一边的宽度，另一边自动填充
* 文字垂直居中

```text
    <div class="table" style="margin-top：20px;display:table;width:800px;height:200px;">
        <div class="table-row" style="table-row">
            <div class="left table-cell" style="display:table-cell;vertical-align:center;">左</div>
            <div class="right table-cell" style="display:table-cell;vertical-align:center;">右</div>
        </div>
    </div>
```

## 一些布局属性

* 确定元素的显示类型
  * block/inline/inline-block
* 确定元素的位置
  * relative的偏移相对于元素本身，不改变占据的空间
  * absoulute脱离文档流，对其他元素的布局不会造成影响，偏移相对于最近的relative或者absoulute
  * fixed脱离文档流，对其他元素的布局不会造成影响，偏移相对于可视区域
  * 默认按照顺序层叠，定位为relative,absoulute,fixed的三种元素可以通过z-index指定刻度

## flexbox布局，真正用于布局的方式，float本来用于图文混排，inline-block也不是用于布局的

* 弹性盒子
* 盒子本来就是并列的
* 指定宽度即可
* 没有被大规模使用，主要是兼容性问题，低版本IE完全不支持flex,属性和写法有过3次变更，需要兼容语法，大部分移动浏览器可以兼容

```text
<head>
    <style>
        .container{
            width: 800px;
            height: 200px;
            display: flex;
        }
        .flex{
            background:red;
            margin: 5px;
            flex: 1;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="flex">
            flex
        </div>
        <div class="flex" style="flex:3">
            flex
        </div>
        <div class="flex">
            flex
        </div>
        <div class="flex" style="width:50px;flex:none;">
            flex
        </div>
        <div class="flex">
            flex
        </div>
    </div>
</body>
```

```text
<head>
    <style>
        .container{
            width: 800px;
            height: 200px;
            display: flex;
        }
        .left{
            background: red;
            display: flex;
            width: 200px;
        }
        .right{
            background: blue;
            display: flex;
            flex:1;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="left">
            左
        </div>
        <div class="right">
            右
        </div>
    </div>
</body>
```

## float布局

* 元素"浮动"
* 脱离文档流
* 但不脱离文本流
* 图文混排，文字环绕
* 对自身的影响：
  * 形成“块”（BFC）
  * 位置尽量靠上
  * 位置尽量靠左（右）
* 对兄弟元素的影响：
  * 上面贴非float元素
  * 旁边贴float元素
  * 不影响其他块级元素位置
  * 影响其他块级元素内部文本
* 对父级元素的影响
  * 从布局上“消失”
  * 高度塌陷
* 清除浮动的两种方式
  * 父元素设置overflow:auto;
  * clearfix

```text
<head>
    <style>
        .container{
            background: red;
            width: 400px;
            margin: 20px;
        }
        .p1{
            background: green;
            float: left;
            width: 200px;
            height: 50px;
        }
        .clearfix::before,
        .clearfix::after{
            content:' ';
            clear:both;
            display: block;
            visibility: hidden;
            height: 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <span class="p1">
            float
        </span>
        <div class="p2">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Magni esse dolorum quis? Nostrum ullam enim, similique ea quis omnis ducimus mollitia iusto error accusamus vero sequi optio aliquam pariatur sapiente repudiandae tenetur quod quia, at reiciendis molestiae aliquid dolores. Nesciunt magnam possimus nulla aliquam corporis sit hic labore libero asperiores magni optio repudiandae eveniet ducimus, temporibus molestias quia reprehenderit soluta, voluptatem ipsum. Tenetur cum doloribus ullam commodi, excepturi maxime quisquam obcaecati tempora explicabo provident ipsa iure, voluptas consequuntur ex eius vel, possimus deserunt! Aperiam quo at ex voluptatum commodi deserunt amet, porro, aspernatur nisi temporibus non vitae voluptates cum atque!
        </div>
    </div>
    <div class="container clearfix">
        <span>写几个字</span>
        <span class="p1">
            float
        </span>
        <span class="p1">
            float
        </span>
    </div>
    <div class="container" style="height:200px;background:blue;"></div>
</body>
```

### 两栏或三栏布局

```text
<head>
    <style>
        .container{
            width: 800px;
            height: 200px;
        }
        .left{
            background: red;
            float: left;
            height: 100%;
            width: 200px;
        }
        .middle{
            margin-left: 200px;
            margin-right: 200px;
        }
        .right{
            background: blue;
            float:right;
            height: 100%;
            width: 200px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="left">
            左
        </div>
        <div class="right">
            右
        </div>
        <div class="middle">
            中间
        </div>
    </div>
</body>
```

* 既然是用margin，左右空间也可以用absoulute
  * absoulute的高度需要显示指定的，无法跟父文档做高度的绑定，百分比无效
  * 完全脱离了文档流，缺少一些适应性方面的特性

## inline-block布局

* 像文本一样排block元素
* 没有清除浮动等问题
* 需要处理间隙
  * 设置父元素font-size:0
  * 去掉标签间的空白
  * 标签间加注释
* 做自适应比较空困难，适合定宽布局

```text
<head>
    <style>
        .container{
            width: 800px;
            height: 200px;
            font-size: 0;
        }
        .left{
            background: red;
            display: inline-block;
            height: 100%;
            width: 200px;
            font-size: 16px;
        }
        .right{
            background: blue;
            display: inline-block;
            height: 100%;
            width: 600px;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="left">
            左
        </div>
        <div class="right">
            右
        </div>
    </div>
</body>
```

## 响应式设计和布局

* 在不同设备上正常使用
* 一般主要处理屏幕大小问题
* 主要方法：
  * 隐藏 + 折行 + 自适应空间
  * rem/viewport/media query
* viewport可视区大小等于屏幕大小，不加iphone默认页面宽度980

```text
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .container {
            max-width: 800px;
            min-height: 200px;
            display: flex;
            border: 1px solid black;
        }

        .left {
            display:flex;
            width: 200px;
            background: red;
            margin: 5px;
        }

        .right {
            background: blue;
            display: flex;
            flex:1;
            margin: 5px;
        }

        @media (max-width:640px) {
            .left {
                display: none;
            }
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="left">
            这里是一些不重要内容，比如广告、友情链接
        </div>
        <!-- a -->
        <div class="right">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Officiis modi laudantium impedit, illum quia eaque dolores architecto voluptatem in asperiores animi tempore eligendi ipsam quaerat officia quae porro qui quod? Aliquid, fugit cumque placeat recusandae libero dicta laboriosam quas, velit minus, reprehenderit reiciendis facere nihil itaque maxime hic voluptate! Rerum unde architecto nam, debitis a odio impedit quidem quo commodi officiis neque magni tempora sint doloribus consequatur culpa officia quibusdam, molestiae nobis nulla esse, quas delectus! Soluta odio qui ullam!
        </div>
    </div>
</body>
```

### 案例二：折行的方式

```text
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .container{
            margin:0 auto;
            max-width: 800px;
            border:1px solid black;
            font-size: 0;
        }
        .intro{
            display: inline-block;
            width: 180px;
            height: 180px;
            line-height: 180px;
            text-align: center;
            border-radius: 90px;
            border:1px solid red;
            margin: 7px;
            font-size:16px;
        }
        @media (max-width:640px){
            .intro{
                margin: 7px auto;
                display: block;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="intro">
            介绍1
        </div>
        <div class="intro">
            介绍2
        </div>
        <div class="intro">
            介绍3
        </div>
        <div class="intro">
            介绍4
        </div>
    </div>
</body>
```

### 自适应空间

* `<meta name="viewport" content="width=320px">`
* window.innerWidth
* rem，不一定会非常精确

```text
<head>
    <meta name="viewport" content="width=320px">
    <style>
        .container{
            margin:0 auto;
            max-width: 800px;
            border:1px solid black;
            font-size: 0;
        }
        .intro{
            display: inline-block;
            width: 180px;
            height: 180px;
            line-height: 180px;
            text-align: center;
            border-radius: 90px;
            border:1px solid red;
            margin: 7px;
            font-size:16px;
        }
        @media (max-width:640px){
            .intro{
                margin: 7px auto;
                display: block;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="intro">
            介绍1
        </div>
        <div class="intro">
            介绍2
        </div>
        <div class="intro">
            介绍3
        </div>
        <div class="intro">
            介绍4
        </div>
    </div>
</body>
```

```text
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        html{
            font-size: 20px;
        }
        .container{
            margin:0 auto;
            max-width: 800px;
            border:1px solid black;
            font-size: 0;
        }
        .intro{
            display: inline-block;
            width: 9rem;
            height: 9rem;
            line-height: 9rem;
            text-align: center;
            border-radius: 4.5rem;
            border:1px solid red;
            margin: 0.3rem;
            font-size:0.8rem;
        }
        @media (max-width:375px){
            html{
                font-size: 24px;
            }
        }
        @media (max-width:320px){
            html{
                font-size: 20px;
            }
        }
        @media (max-width:640px){
            .intro{
                margin: 0.3rem auto;
                display: block;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="intro">
            介绍1
        </div>
        <div class="intro">
            介绍2
        </div>
        <div class="intro">
            介绍3
        </div>
        <div class="intro">
            介绍4
        </div>
    </div>
</body>
```

## 主流网站使用的布局方式

* 国内主要使用float布局
* 苹果使用flex布局

## 面试真题

1. 实现两栏（三栏）布局的方法
   * 表格布局
   * float+margin布局，兼容性非常好
   * inline-block布局
   * flex布局
2. position:absoulute/fixed有什么区别
   * 前者相对最近的absoulute/relative
   * 后者相对屏幕（viewport）,fixed在移动端兼容问题
3. display:inline-block的间隙
   * 原因：字符间距
   * 解决：消灭字符或者消灭间距
4. 如何清除浮动
   * 浮动元素不会占据父元素的布局空间，浮动元素可能会超出父元素，从而对其他元素产生影响
   * 让盒子负责自己的布局
   * overflow:hiddden\(auto\)
   * ::after{clear:both}
5. 如何适配移动端页面？
   * viewport
   * rem/viewport/media query
   * 设计上：隐藏 折行 自适应

