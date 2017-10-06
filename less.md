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
.test_hunhe{
    .border2(30px);
}
//混合-默认带值
```









