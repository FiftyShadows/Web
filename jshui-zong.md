#自定义属性（兼容写法）

1. 直接绑定属性：不会再标签中显示（没有的属性）；
2. 标签中的自定义属性，不能box.aaa获取
（火狐谷歌IE9+）(IE678可以获取)
3. get/setAttribute（）；可以

```javascript
两种方式不能交换使用，赋值和获取值必须使用用一种方法。
var div = document.getElementById("box");
//元素节点.属性（元素节点[属性]）:绑定的属性值不会出现在标签上。
div.aaaa = "1111";
console.log(div.aaaa);
//get/set/removeAttribut: 绑定的属性值会出现在标签上。
div.setAttribute("bbbb","2222");

console.log(div.getAttribute("aaaa"));
console.log(div.bbbb);
```




字符串转换成数组：

var str = "红鲤鱼与绿鲤鱼与驴";
var arr =  str.split("");




text-align:center;可以使内联元素居中对齐，让块状里面的元素（比如文字）居中或者上下移。把块状元素设定一个宽度，就会发现块状元素无法居中，你居中的是行内的文本。



map() 方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。



##javascript时间戳和日期字符串相互转换

Date.parse(new Date("2014-07-10 10:21:12"))



