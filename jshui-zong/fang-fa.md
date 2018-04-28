##随机获取5位字符串

`Math.random().toString(36).replace(/[^a-z]+/g, '').substr(0, 5)`



##in关键字的用法

1. 最常用的是在for in 循环中遍历对象的键



##window.innerWidth




##this本身表示函数运行时自动生成的内部对象，只能在函数内部使用，随着函数使用场合的不同，this的值会发生变化。总的原则：this指得是调用函数的对象。

1. 当其出现在setTimeout的函数参数中时，函数参数是一个纯粹的函数调用，并不隶属于哪个对象，属于全局调用，这种情况下this指的是全局对象global。

2. 当this出现在对象的函数中时，this指的是对象。

3. 在构造函数中，指的是new生成的空对象。

4. apply,call,bind方法中的第一个参数。




##try catch finally

- catch子句包含try块中抛出异常时要执行的语句。也就是，你想让try语句中的内容成功， 如果没成功，你想控制接下来发生的事情，这时你可以在catch语句中实现。 如果有在try块中有任何一个语句（或者从try块中调用的函数）抛出异常，控制立即转向catch子句。如果在try块中没有异常抛出，会跳过catch子句。

- finally子句在try块和catch块之后执行但是在下一个try声明之前执行。无论是否有异常抛出或着是否被捕获它总是执行。




##encodeURIComponent

- encodeURIComponent 转义除了字母、数字、(、)、.、!、~、*、'、-和_之外的所有字符。

- 为了避免服务器收到不可预知的请求，对任何用户输入的作为URI部分的内容你都需要用encodeURIComponent进行转义。比如，一个用户可能会输入"Thyme &time=again"作为comment变量的一部分。如果不使用encodeURIComponent对此内容进行转义，服务器得到的将是comment=Thyme%20&time=again。请注意，"&"符号和"="符号产生了一个新的键值对，所以服务器得到两个键值对（一个键值对是comment=Thyme，另一个则是time=again），而不是一个键值对。




##ele.getBoundingClientRect()

- 返回值是一个DOMRect对象，DOMRect 对象包含了一组用于描述边框的只读属性——left、top、right和bottom，单位为像素。除了 width 和 height 外的属性都是相对于视口的左上角位置而言的。

- 跟window.scroll.height组成加载更多组件，`window.scroll.height> ele.getBoundingClientRect().top`

![](/assets/rect.png)




##Object.create(proto[, propertiesObject])

- Object.create() 方法会使用指定的原型对象及其属性去创建一个新的对象。

```js
var p = {x: 1, y: 2};
var tmp = Object.create(p);
console.log('tmp.__proto__ === p ?', tmp.__proto__ === p);  //true
```

```js
// Shape - 父类(superclass)
function Shape() {
  this.x = 0;
  this.y = 0;
}

// 父类的方法
Shape.prototype.move = function(x, y) {
  this.x += x;
  this.y += y;
  console.info('Shape moved.');
};

// Rectangle - 子类(subclass)
function Rectangle() {
  Shape.call(this); // call super constructor.
}

// 子类续承父类
Rectangle.prototype = Object.create(Shape.prototype);
Rectangle.prototype.constructor = Rectangle;

// 因为使用“.prototype =...”后,constructor会改变为“=...”的那个
// constructor，所以要重新指定.constructor 为自身。


var rect = new Rectangle();

console.log('Is rect an instance of Rectangle?',
  rect instanceof Rectangle); // true
console.log('Is rect an instance of Shape?',
  rect instanceof Shape); // true
rect.move(1, 1); // Outputs, 'Shape moved.'
```



##instanceof

- instanceof 运算符用来测试一个对象在其原型链中是否存在一个构造函数的 prototype 属性。换言之也就是判断一个实体是不是某个构造函数的实体

```
function People(){
  this.name = 'sun';
  this.id = 1;
}

function Shape() {
  this.x = 0;
  this.y = 0;
}

var tmp = new Peole;
console.log(tmp instanceof Peolpe);  //true
console.log(tmp instanceof Object);  //true
console.log(tmp instanceof Object);  //false
```



##Object.assign()

- Object.assign() 方法用于将所有可枚举属性的值从一个或多个源对象复制到目标对象。它将返回目标对象。

- 深浅拷贝问题：针对深拷贝，需要使用其他方法，因为 Object.assign()拷贝的是属性值。假如源对象的属性值是一个指向对象的引用，它也只拷贝那个引用值。

- 继承属性和不可枚举属性是不能拷贝的

- 原始类型会被包装为对象

```js
//Deep Clone
obj1 = { a: 0 , b: { c: 0}};
let obj3 = JSON.parse(JSON.stringify(obj1));
obj1.a = 4;
obj1.b.c = 4;
console.log(JSON.stringify(obj3));  // { a: 0, b: { c: 0}};
```



##Location.replace

Location.replace()方法以给定的URL来替换当前的资源。 与assign() 方法 不同的是调用replace()方法后，当前页面不会保存到会话历史中（session History），这样用户点击回退按钮将不会再跳转到该页面。




##window.onresize

onresize属性可以用来获取或设置当前窗口的resize事件的事件处理函数。



##回到顶部

```js
  var topBtn = document.querySelector('.float-nav .top');
  topBtn.addEventListener(
    'click',
    function() {
      window.scrollTo(0, 0);
    },
    false
  );
```




##判断页面大小并重定向

```
(function() {
  // mobile redirect
  function detectmob() {
    if (window.innerWidth < 800 || window.innerHeight < 512) {
      return true;
    } else {
      return false;
    }
  }

  if(detectmob()) {
    location.replace('mindex.html');
  }

  window.onresize = function() {
    detectmob() && location.replace('mindex.html');
  };
)()
```




##Array.prototype.push()方法将一个或多个元素添加到数组的末尾，并返回新数组的长度



##for in遍历的是数组的索引（即键名），而for of遍历的是数组元素值。



##数字保留小数位数

- num.toFixed(2)保留两位小数

- Math.floor(15.7784514000 * 100) / 100 

- Number(15.7784514000.toString().match(/^\d+(?:\.\d{0,2})?/)) 





