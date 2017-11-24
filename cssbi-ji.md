##移除input在type="number"时的上下箭头

1. chrome浏览器移除
```
input::-webkit-outer-spin-button,input::-webkit-inner-spin-button{
        -webkit-appearance:textfield;
}
```

2. firefox浏览器下移除
```
input[type="number"]{
        -moz-appearance:textfield;
}
```

3. 用type="tel"代替

input[type="tel"]的value值亦是number，且其没有type="number"时的上下箭头，故我们可以用[type="tel"]代替[type="number"]，达到一样的效果，并通过设置maxlength = "m"限定value值得长度。如果有其他的要求，可以通过正则来判断






















