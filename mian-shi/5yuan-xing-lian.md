##原型链类

- 创建对象有几种方法

- 原型、构造函数、实例、原型链

- instanceof原理

- new运算符




##创建对象有几种方法

![](/assets/360截图20171213202704402.jpg)

Object.create() 方法会使用指定的原型对象及其属性去创建一个新的对象。




##原型、构造函数、实例、原型链

![](/assets/360截图20171213205351951.jpg)

通过构造函数prototype对象实现继承，实例的对象继承的属性和方法都指向同一个地址，减少内存占用。



##instanceof用来判断一个对象在其原型链中是否存在一个构造函数的 prototype 属性

![](/assets/360截图20171213205701928.jpg)




##new运算符

![](/assets/360截图20171214133847151.jpg)




##代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>原型链</title>
</head>
<body>
	<script type="text/javascript">
		// 第一种方式：字面量
		var o1 = {name: 'o1'};
		var o2 = new Object({name: 'o2'});
		// 第二种方式：通过构造函数
		var M = function(name) {this.name = name;}
		var o3 = new M('o3');
		// 第三种方式：Object.create
		var p = {name: 'p'};
		var o4 = Object.create(p);

		M.prototype.say = function() {
			console.info('say hi');
		}

		o5 = new M('o5');

		console.info(o3.__proto__ === M.prototype);
		console.info(o3.__proto__.__proto__ === Object.prototype);
		console.info(o3.__proto__.constructor === M);

		var new2 = function(func){
			var o = Object.create(func.prototype);
			var k = func.call(o);
			if(typeof k === 'object'){
				return k
			}else{
				return o
			}
		}

		o6 = new2(M);
		console.info(o6);
	</script>
</body>
</html>
```
