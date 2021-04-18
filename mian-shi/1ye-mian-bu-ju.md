# 1.页面布局

```text
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="
    UTF-8">
    <title>layout</title>
    <style type="text/css">
        html *{
            margin: 0;
            padding: 0;
        }
        section{
            margin-bottom: 20px;
        }
        div{
            min-height: 100px;
        }
    </style>
</head>
<body>
    <!-- 浮动布局 -->
    <section class="layout float">
        <style type="text/css">
            .layout.float .left{
                width: 300px;
                float: left;
                background-color: red;
            }
            .layout.float .center{
                background-color: yellow;
            }
            .layout.float .right{
                width: 300px;
                float: right;
                background: blue;
            }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="right"></div>
            <div class="center">
                <h1>浮动解决方案</h1>
                1.这是三栏布局中间部分
                2.这是三栏布局中间部分
            </div>
        </article>
    </section>

    <!-- 绝对定位 -->
    <section class="layout absolute">
        <style type="text/css">
            .layout.absolute .left{
                position: absolute;
                left: 0;
                width: 300px;
                background: red;
            }
            .layout.absolute .center{
                position: absolute;
                left: 300px;
                right: 300px;
                background: yellow;
            }
            .layout.absolute .right{
                position: absolute;
                right: 0;
                width: 300px;
                background: blue;
            }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="center">
                <h1>绝对定位解决方案</h1>
                1.这是三栏布局中间部分
                2.这是三栏布局中间部分
            </div>
            <div class="right"></div>
        </article>
    </section>

    <!-- flex布局 -->
    <section class="layout flexbox">
        <style type="text/css">
            .layout.flexbox{
                margin-top: 140px;
            }
            .layout.flexbox .left-center-right{
                display: flex;
            }
            .layout.flexbox .left{
                width: 300px;
                background: red;
            }
            .layout.flexbox .center{
                flex: 1;
                background: yellow;
            }
            .layout.flexbox .right{
                width: 300px;
                background: blue;
            }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="center">
                <h1>flex布局解决方案</h1>
                1.这是三栏布局中间部分
                2.这是三栏布局中间部分
            </div>
            <div class="right"></div>
        </article>
    </section>

    <!-- 表格布局 -->
    <section class="layout table">
        <style type="text/css">
            .layout.table .left-center-right{
                width: 100%;
                display: table;
                height: 100px;
            }
            .layout.table .left{
                display: table-cell;
                width: 300px;
                background: red;
            }
            .layout.table .center{
                display: table-cell;
                background: yellow;
            }
            .layout.table .right{
                display: table-cell;
                width: 300px;
                background: blue;
            }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="center">
                <h1>表格布局解决方案</h1>
                1.这是三栏布局中间部分
                2.这是三栏布局中间部分
            </div>
            <div class="right"></div>
        </article>
    </section>

    <!-- grid布局 -->
    <section class="layout grid">
        <style type="text/css">
            .layout.grid .left-center-right{
                display: grid;
                width: 100%;
                grid-template-rows: 100px;
                grid-template-columns: 300px auto 300px;
            }
            .layout.grid .left{
                background: red;
            }
            .layout.grid .center{
                background: yellow;
            }
            .layout.grid .right{
                background: blue;
            }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="center">
                <h1>网格解决方案</h1>
                1.这是三栏布局中间部分
                2.这是三栏布局中间部分
            </div>
            <div class="right"></div>
        </article>
    </section>

    <!-- 使用inline-block -->
    <section class="layout basic">
        <style type="text/css">
            .layout.basic .left-center-right{
                width: 100%;
            }
            .layout.basic .left-center-right>div{
                display: inline-block;
                vertical-align:top;
            }
            .layout.basic .left{
                width: 300px;
                background: red;
            }
            .layout.basic .center{
                width: calc(100% - 600px);
                background: yellow;
            }
            .layout.basic .right{
                width: 300px;
                background: blue;
            }
        </style>
        <article class="left-center-right">
            <div class="left"></div><div class="center">
                <h1>解决方案</h1>
                1.这是三栏布局中间部分
                2.这是三栏布局中间部分
            </div><div class="right"></div>
        </article>
    </section>

</body>
</html>
```

