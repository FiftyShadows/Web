# 1.基础知识（上）

### JavaScript数据类型

#### 简单数据类型

* string
* number
* boolean
* undefined

  **复杂数据类型**

* Object
* Array
* Date
* RegExp
* Function
* String
* Number
* Boolean
* null
* Math

### 值类型和引用类型

* 值类型： 存储的是数据本身的值就是值类型的数据
* 引用类型：存储的是数据的地址的值就是引用类型的数据，数据自己在内存中单独存储
* 引用类型：对象、数组、函数

### typeof 判断对象的类型  返回值是string类型的

引用类型中，除了function其他的对象都是object类型

```javascript
 typeof undefined     //undefined 
 typeof 'abc'         //string
 typeof 123           //number
 typeof true          //boolean
 typeof {}            //object
 typeof []            //object
 typeof null          //object 
 typeof console.log   //function
```

### 变量计算 - 强制类型转换

* 字符串拼接 `var b = 100 + '100'; //'10000'`
* ==运算 100 == '100' //true 0 == '' //true null == undefined //true
* if语句 var a = true; if\(a\){ //... } var b = 100; if\(b\){ //... } var c =''; if\(c\){ //... }
* 逻辑运算 console.log\(10 && 0\) //0 console.log\('' \|\| 'abc'\) //'abc' console.log\(!window.abc\) //true

### 何时使用 === 和 ==

if\(obj.a == null\){ // 这里相当于 obj.a === null \|\| obj.a === undefined ,简写形式 // 这是jQuery源码中推荐的写法 }

其他时候用 ===

### JS中的内置函数

Object Array Boolean Number String Function Date RegExp Error

### JS按存储方式区分变量类型

* 值类型
* 引用类型

### 如何理解JSON

JSON只不过是一个JS对象而已

JSON.stringify\({a:10,b:20}\);对象转换成字符串

JSON.parse\('{"a":10,"b":20}'\);字符串转换成对象

## 原型和原型链

### 构造函数

* var a = {} 其实是 var a = new Object\(\)的语法糖
* var a = \[\] 其实是 var a = new Array\(\)的语法糖
* function Foo\(\){...} 其实是 var Foo = new Function\(...\)
* 使用instanceof判断一个函数是否是一个变量的构造函数

### 原型规则和示例

#### 五条原型规则

1. 所有的引用类型（数组、对象、函数），都具有对象特性，即可自由扩展属性（除了'null'以外）
2. 所有的引用类型（数组、对象、函数），都有一个**proto**属性，属性值是个普通的对象
3. 所有的函数，都有一个prototype属性，属性值也是一个普通对象
4. 所有的引用类型（数组、对象、函数），**proto**属性值指向它的构造函数的"prototype"属性值
5. 当试图得到一个对象的某个属性时，如果这个对象本身没有这个属性，那么会去它的**proto**\(即它的构造函数的prototype\)中寻找。

循环对象自身的属性

var item for \(item in f\){ //高级浏览器已经在 for in 中屏蔽了来自原型的属性 //但是这里建议大家还是加上这个判断，保证程序的健壮性 if\(f.hasOwnProperty\(item\)\){ console.log\(item\) } }

### 原型链

#### 如何准确判断一个变量是数组类型

var arr = \[\]; arr instanceof Array; //true

#### 写一个原型链继承的例子

```javascript
function Elem(id){
    this.elem = document.getElementById(id);
}

Elem.prototype.html = function (val){
    var elem = this.elem;
    if(val){
        elem.innerHTML = val;
        return this;
    }else{
        return elem.innerHTML;
    }
}

Elem.prototype.on = function (type,fn){
    var elem = this.elem;
    elem.addEventListener(type,fn);
    return this;
}

var div1 = new Elem("div1");

div1.html("<p>hello</p>")on("click",function (){
    alert("clicked");
});
```

#### 描述 new 一个对象的过程

* 创建一个新对象 
* this 指向一个新对象
* 执行代码，即对 this 赋值
* 返回 this

#### zepto\(或其他框架\) 源码中如何使用原型链

* 阅读源码是高效提高技能的方式
* 但不能“埋头苦钻”有技巧在其中（jQuery源码分析）
* 慕课网搜索“zepto设计和源码分析”

