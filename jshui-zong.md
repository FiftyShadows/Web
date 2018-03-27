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




##字符串转换成数组：

var str = "红鲤鱼与绿鲤鱼与驴";
var arr =  str.split("");




text-align:center;可以使内联元素居中对齐，让块状里面的元素（比如文字）居中或者上下移。把块状元素设定一个宽度，就会发现块状元素无法居中，你居中的是行内的文本。



map() 方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。



##javascript时间戳和日期字符串相互转换

**new Date(year, month, date);  可越界；month从0到11**

![](/assets/360截图20171211102720134.jpg)

```js
// 获取某个时间格式的时间戳
var stringTime = "2014-07-10 10:21:12";
var timestamp2 = Date.parse(new Date(stringTime));
timestamp2 = timestamp2 / 1000;
//2014-07-10 10:21:12的时间戳为：1404958872 
console.log(stringTime + "的时间戳为：" + timestamp2);

// 将当前时间换成时间格式字符串
var timestamp3 = 1403058804;
var newDate = new Date();
newDate.setTime(timestamp3 * 1000);
// Wed Jun 18 2014 
console.log(newDate.toDateString());
// Wed, 18 Jun 2014 02:33:24 GMT 
console.log(newDate.toGMTString());
// 2014-06-18T02:33:24.000Z
console.log(newDate.toISOString());
// 2014-06-18T02:33:24.000Z 
console.log(newDate.toJSON());
// 2014年6月18日 
console.log(newDate.toLocaleDateString());
// 2014年6月18日 上午10:33:24 
console.log(newDate.toLocaleString());
// 上午10:33:24 
console.log(newDate.toLocaleTimeString());
// Wed Jun 18 2014 10:33:24 GMT+0800 (中国标准时间)
console.log(newDate.toString());
// 10:33:24 GMT+0800 (中国标准时间) 
console.log(newDate.toTimeString());
// Wed, 18 Jun 2014 02:33:24 GMT
console.log(newDate.toUTCString());

```


##类型转换

- Boolean(value) 是把值转换成Boolean类型

- Nnumber(value) 是把值转换成数字

- parseInt和parseFloat则可以只转换开头的数字部分

- String(value) 是把值转换成字符串

- parseInt和parseFloat则可以只转换开头的数字部分


##浅复制和深复制

- 浅复制只会将对象的各个属性进行依次复制，并不会进行递归复制，而 JavaScript 存储对象都是存地址的，所以浅复制会导致 obj.arr 和 shallowObj.arr 指向同一块内存地址

```
//浅复制
var obj = { a:1, arr: [2,3] };
var shallowObj = shallowCopy(obj);

function shallowCopy(src) {
  var dst = {};
  for (var prop in src) {
    if (src.hasOwnProperty(prop)) {
      dst[prop] = src[prop];
    }
  }
  return dst;
}
```

- 深复制则不同，它不仅将原对象的各个属性逐个复制出去，而且将原对象各个属性所包含的对象也依次采用深复制的方法递归复制到新对象上。这就不会存在上面 obj 和 shallowObj 的 arr 属性指向同一个对象的问题。

```
var obj = { a:1, arr: [1,2] };
var obj2 = deepCopy(obj);
```


- 需要注意的是，如果对象比较大，层级也比较多，深复制会带来性能上的问题。在遇到需要采用深复制的场景时，可以考虑有没有其他替代的方案。在实际的应用场景中，也是浅复制更为常用。



##查找值在数组中的位置

- indexOf([ 1, 2, 3, 4 ], 3)

如果数组中存在 item，则返回元素在数组中的位置，否则返回 -1

- array.indexOf(value);



##JSON

- 使用反斜线对字符串中的双引号进行转义


- 除了双引号和反斜线，还需要转义以下字符串：

  - \/（正斜线）
  
  - \b（退格符）
  
  - \f（换页符）
  
  - \t（制表符）
  
  - \n（换行符）
  
  - \r（回车符）
  
  - \u（后跟十六进制字符\u263A）


```
{
  "promo": "Say \"Bob's the best!\" at checkout for free 8oz bag of kibble."
}

{
  "location": "C:\\Program Files"
}

{
  "story": "\\t Once upon a time, in a far away land \\n there lived a princess."
}
```

- 序列化和反序列化

  - 反序列化JSON.parse()，将文本转换成对象。
  
  - 序列化JSON.stringfy(),将对象转换成文本。



##Object.assign()

- 合并多个对象

- 克隆对象（浅）

- 为对象添加多个方法

```
var nObj = Object.assign({},obj,obj1);//花括号叫目标对象，后面的obj、obj1是源对象。对象合并是指：将源对象里面的属性添加到目标对象中去，若两者的属性名有冲突，后面的将会覆盖前面的

   
//【注意】：当Object.assign()方法用于数组时：
 var arr11 = Object.assign([1,2,3],[4,5]);
 console.log(arr11);//[4,5,3]
 //[说明]:对象是根据属性名来对应，数组是根据索引号来对应   
```


##Ajax

- post application/json 

![](/assets/360截图20171205155857590.jpg)




##JS异常

- 运行异常

- 资源加载错误




##外联script的异步加载方式

async




##body和html

document.body和document.documentElement







##charset && script.setAttribute('charset', charset);


```
util.createScript = function (url, charset) {
     var script = document.createElement('script');
     script.setAttribute('type', 'text/javascript');
     charset && script.setAttribute('charset', charset);
     script.setAttribute('src', url);
     script.async = true;
     return script;
 };
 ```
 
 
 ##事件
 
 onload,onerror,onhashchange,message
 
 
 ##var hobby = document.getElementsByTagName("input");使用forEach
 
 hobby 并不是一个真正的数组，但他有length属性，所以可以用for循环，forEach是真正数组的方法，所以hobby不能直接用forEach
 
 - Array.prototype.forEach.call(hobby,function(element,index){ ... });
 
 - [].forEach.call(hobby,function(element,index){ ... });





##数组去重

- 题目：有数组 var arr = ['a', 'b', 'c', '1', 0, 'c', 1, '', 1, 0]，请用JavaScript实现去重函数unqiue，使得unique(arr)返回 ['a', 'b', 'c', '1', 0, 1, '']

```
//es6最简单的办法
function unique(arr){
  return arr.filter((item, index) => index === this.indexOf(item));
}

//es6遍历数组，不支持ie6-8
function unique(arr) {
  var ret = []
   for (var i = 0; i < arr.length; i++) {
    var item = arr[i]
    if (ret.indexOf(item) === -1) {
      ret.push(item)
    }
  }
   return ret
}

//es5,两重循环，内存消耗大
var indexOf = [].indexOf ?
    function(arr, item) {
      return arr.indexOf(item)
    } :
    function indexOf(arr, item) {
      for (var i = 0; i < arr.length; i++) {
        if (arr[i] === item) {
          return i
        }
      }
      return -1
    }
 function unique(arr) {
  var ret = []
   for (var i = 0; i < arr.length; i++) {
    var item = arr[i]
    if (indexOf(ret, item) === -1) {
      ret.push(item)
    }
  }
   return ret
}


//优化方案，核心是构建了一个 hash 对象来替代 indexOf. 注意在 JavaScript 里，对象的键值只能是字符串，因此需要var key = typeof(item) + item 来区分数值 1 和字符串 '1' 等情况。
function unique(arr) {
  var ret = []
  var hash = {}
   for (var i = 0; i < arr.length; i++) {
    var item = arr[i]
    var key = typeof(item) + item
    if (hash[key] !== 1) {
      ret.push(item)
      hash[key] = 1
    }
  }
   return ret
}
```
 
 
 
 
 
 ##数组对象去重
 
 ```js
 function arrayUnique2(arr, name) {
  var hash = {};
  return arr.reduce(function (item, next) {
    hash[next[name]] ? '' : hash[next[name]] = true && item.push(next);
    return item;
  }, []);
}

 ```
 
 
 
 
##表达式(expressions)和语句(statements)之间的区别
 
- 表达式会产生一个值,它可以放在任何需要一个值的地方
 
```
myvar
3 + x
myfunc("a", "b")
```

- 语句可以理解成一个行为.循环语句和if语句就是典型的语句.你可以使用一个表达式来代替.这样的语句称之为表达式语句.但反过来不可以:你不能在一个需要表达式的地方放一个语句.比如,一个if语句不能作为一个函数的参数.

- 类似if语句功能的表达式叫做条件运算符(三元运算符)

- 分号可以连接两个语句

- 逗号运算符会计算前后两个表达式,然后返回右边表达式的计算结果

```
Statement -> Block
           | VariableStatement
           | EmptyStatement
           | ExpressionStatement
           | IfStatement
           | IterationStatement
           | ContinueStatement
           | BreakStatement
           | ReturnStatement
           ...

ExpressionStatement -> Expression;

Expression -> this
            | 基本表达式
            | 属性访问表达式
            | new表达式
            | 函数调用表达式
            | 函数表达式
            | 自增/自减表达式
            | 算术表达式
            | 逻辑表达式
            ...
```








