# 6.CSS预处理器

* less基于node写的，编译非常快，有浏览器可以直接使用的版本。复杂场景下显得繁琐
* sass是用Ruby写的，编译过程会较慢，node下会有node的包解决

## 语法

* 嵌套
* 变量和计算，减少重复代码
* extend和mixin代码片段
* 循环 适用于复杂有规律的样式
* import CSS文件模块化
  * css原生的import不会做代码合并的事情，只是在浏览器端去动态引用其他的样式表。性能差，需要发独立的请求

### less

* @符号
* 变浅`background: lighten(@bgColor, 40%);`
* `@fontSize + 2px`
* mixin
* extend 可以提取公共的样式

```text
//mixin
.block(@fontSize){
    font-size: @fontSize;
    border: 1px solid #ccc;
    border-radius: 4px;
}

.content{
    .block(@fontSize + 2px);
}


//extend
.block{
    font-size: @fontSize;
}
.wrapper{
    .nav:extend(.block){

    }
    .content{
        &:extend(.block){

        }
    }
}
```

## sass

* $符号
* 也有lighten函数
* !default是用来指定变量默认值

```text
@mixin block(){
    font-size: $fontSize;
    border: 1px solid #ccc;
    border-radius: 4px;
}

.content{
    @include block($fontSize + 2px);
}
```

