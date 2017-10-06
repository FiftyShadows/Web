##变量

```
@test_width:300px;

```


##混合

```less
//混合
.box{
    width:300px;
    height:300px;
    .border;
}
.border{
    border:5px solid pink;
}
//混合-可带参数
.borer2(@border_width){
    border:solid red @border_with;
}
.test_hunhe2{
    .border2(30px);
}
//混合-默认带值
.border3(@border_width:10px){
    border:solid red @border_with;

}
.test_hunhe3{
    .border3();
}
```





###匹配模式


```
.triangle(top,@w:5px,@c:#ccc){
    border:@w;
    border-color:color:transparent transparent @c transparent;
    border-style:dashed dashed solid dashed;
}
.triangle(bottom,@w:5px,@c:#ccc){
    border:@w;
    border-color:color:@c transparent transparent transparent;
    border-style:solid dashed dashed dashed;
}
.triangle(@_,@w:5px,@c:#ccc){
    width:0;
    height:0;
    overflow:hidden;
}

.sanjiao{
    .triangle(top);
}




```






































