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