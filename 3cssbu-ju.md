##常用布局方法

- table表格布局

- float浮动+margin

- inline-block布局

- flexbox布局





##表格布局

```
    <table style="width:800px;">
        <tr>
            <td class="left" style="width:200px;">左</td>
            <td class="right">右</td>
        </tr>
    </table>
```

特点

    - 设置一边的宽度，另一边自动填充

    - 文字垂直居中


```
    <div class="table" style="margin-top：20px;display:table;width:800px;height:200px;">
        <div class="table-row" style="table-row">
            <div class="left table-cell" style="display:table-cell;vertical-align:center;">左</div>
            <div class="right table-cell" style="display:table-cell;vertical-align:center;">右</div>
        </div>
    </div>
```





##一些布局属性

- 确定元素的显示类型
    
    - block/inline/inline-block
    
- 确定元素的位置

    - relative的偏移相对于元素本身，不改变占据的空间
    
    - absoulute脱离文档流，对其他元素的布局不会造成影响，偏移相对于最近的relative或者absoulute
    
    - fixed脱离文档流，对其他元素的布局不会造成影响，偏移相对于可视区域
    
    - 默认按照顺序层叠，定位为relative,absoulute,fixed的三种元素可以通过z-index指定刻度





##flexbox布局，真正用于布局的方式，float本来用于图文混排，inline-block也不是用于布局的

- 弹性盒子

- 盒子本来就是并列的

- 指定宽度即可

- 没有被大规模使用，主要是兼容性问题，低版本IE完全不支持flex,属性和写法有过3次变更，需要兼容语法，大部分移动浏览器可以兼容

```
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

```
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




##float布局

- 元素"浮动"

- 脱离文档流

- 但不脱离文本流

- 图文混排，文字环绕

- 对自身的影响：

    - 形成“块”（BFC）
    
    - 位置尽量靠上
    
    - 位置尽量靠左（右）
    
- 对兄弟元素的影响：

    - 上面贴非float元素
    
    - 旁边贴float元素
    
    - 不影响其他块级元素位置
    
    - 影响其他块级元素内部文本
    
- 对父级元素的影响

    - 从布局上“消失”
    
    - 高度塌陷
    
- 清除浮动的两种方式

    - 父元素设置overflow:auto;
    
    - clearfix
    
```
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


####两栏或三栏布局

```
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

- 既然是用margin，左右空间也可以用absoulute

    - absoulute的高度需要显示指定的，无法跟父文档做高度的绑定，百分比无效
    
    - 完全脱离了文档流，缺少一些适应性方面的特性






##inline-block布局











