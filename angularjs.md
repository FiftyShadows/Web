##定义模块

var App = angular.module('App',[]);






##定义控制器

- 一个页可以有多个模块，但是不能互想嵌套 

- 控制器可以嵌套

```html
<body>
<div class="box" ng-app="App">
    <h1 ng-controller="DemoController">{{name}}在{{school}}学习使用AngularJS</h1>
    <ul ng-repeat="(key, course) in courses">
        <li>第{{key+1}}天：{{course}}</li>
    </ul>
</div>

<script src="./libs/angular.min.js"></script>
<script>
var App = angular.module('App',[]);
App.controller('DemoController',['#scope',function (#scope){
    // $scope 是一个空对象{}，此对象就是Model
    $scope.name = '范冰冰';
    $scope.school = 'itcast';
    $scope.courses=['MVC','模块化','指令'];
}]);
</script>
</body>
```





##指令

HTML在构建应用（App）时存在诸多不足之处，AngularJS通过扩展一系列的HTML属性或标签来弥补这些缺陷，所谓指令就是AngularJS自定义的HTML属性或标签，这些指令都是以ng-做为前缀的，例如ng-app、ng-controller、ng-repeat等。



###内置指令

- ng-app 指定应用根元素，至少有一个元素指定了此属性。

- ng-controller 指定控制器

- ng-show控制元素是否显示，true显示、false不显示

    - display掉

- ng-hide控制元素是否隐藏，true隐藏、false不隐藏

- ng-if控制元素是否“存在”，true存在、false不存在

    - remove掉

- ng-src增强图片路径(去掉html加载时的缩略图)

    - `<li><img src="{{path}}" alt=""></li>`加载两次，会有缩略图，闪烁
    
    - `<li><img ng-src="{{path}}" alt=""></li>`

- ng-href增强地址

    - `<link rel="stylesheet" href="{{link}}">`
    
    - `<link rel="stylesheet" ng-href="{{link}}">`

- ng-class控制类名

    - `<li ng-class="{red: true, blue: true}">ng-class指令</li>`

- ng-include引入模板

    - ajax

- ng-disabled表单禁用

- ng-readonly表单只读

- ng-checked单/复选框表单选中

- ng-selected下拉框表单选中

![](/assets/360截图20171007171945862.jpg)




###自定义指令

AngularJS允许根据实际业务需要自定义指令，通过angular全局对象下的directive方法实现。

- 自定义指令的类型 E、A、C、M

- E(element)可以作为元素 `<tag></tag>`

- A(attribute)可以作为属性

- C(class)作为类名`<div class="tag"></div>`

- M(mark)可作为备注，注释

![](/assets/360截图20171008014902108.jpg)



```javascript
var App = angular.module('App', []);

App.directive('tag', function (){
    return{
        restict:'ECMA',
        //templateUrl:'./index.html',
        //replace:true,//是否删除标签
        template:'<h1>Hello Angular</h1>'
    }
});
```







##数据绑定

AngularJS是以数据做为驱动的MVC框架，所有模型（Model）里的数据经由控制器（Controller）展示到视图（View）中。
所谓数据绑定指的就是将模型（Model）中的数据与相应的视图（View）进行关联，分为单向绑定和双向绑定两种方式。



###单向绑定

单向数据绑定是指将模型（Model）数据，按着写好的视图（View）模板生成HTML标签，然后追加到DOM中显示，如之前所学的artTemplate 模板引擎的工作方式。



###双向绑定

双向绑定则可以实现模型（Model）数据和视图（View）模板的双向传递。



###相关指令

在AngularJS中通过`“{{}}”`和ng-bind指令来实现模型（Model）数据向视图模板（View）的绑定，模型数据通过一个内置服务$scope来提供，这个$scope是一个空对象，通过为这个对象添加属性或者方法便可以在相应的视图（View）模板里被访问

注：“{{}}”是ng-bind的简写形式，其区别在于通过“{{}}”绑定数据时会有“闪烁”现象，添加ng-cloak也可以解决“闪烁”现象，通过ng-bind-template可以绑定多个数据。

- `<li ng-cloak>{{name}}{{age}}</li>`    ng-cloak通过css3属性选择器设置display解决“闪烁”，所以angular需要放在head里加载。

- `<li ng-bind-template="{{name}}{{age}}"></li>`


通过为表单元素添加ng-model指令实现视图（View）模板向模型（Model）数据的绑定。

通过ng-init可以初始化模型（Model）也就是$scope。

```
<div ng-controller="DemoController" ng-init="name='itcast';age=10">
    <h1>{{name}}</h1>
    <h2>{{age}}</h2>
</div>
```


AngularJS对事件也进行了扩展，无需显式的获取DOM元素便可以添加事件，易用性变的更强。通过在原有事件名称基础上添加ng-做为前缀，然后以属性的形式添加到相应的HTML标签上即可。如ng-click、ng-dblclick、ng-blur等。

```
<div ng-controller="DemoController">
	<ul>
		<li><button ng-click="single()">单击</button></li>
		<li><button ng-dblclick="double()">双击</button></li>
		<li><input type="text" ng-blur="blur()"></li>
		<li ng-mouseout="mouseout()">一些内容</li>
	</ul>
</div>
```



通过ng-repeat可以将数组或对象数据迭代到视图模板中，ng-switch、on、ng-switch-when可以对数据进行筛选。

```
<ul>
	<li ng-repeat="item in items" ng-switch="item">
		<span ng-switch-when="css">{{item}}</span>
	</li>
</ul>
```







##作用域

通常AngularJS中应用（App）是由若干个视图（View）组合成而成的，而视图（View）又都是HTML元素，并且HTML元素是可以互相嵌套的，另一方面视图都隶属于某个控制器（Controller），进而控制器之间也必然会产生嵌套关系。

每个控制器（Controller）又都对应一个模型（Model）也就是$scope对象，不同层级控制器（Controller）下的$scope便产生了作用域。



###根作用域

一个AngularJS的应用（App）在启动时会自动创建一个根作用域$rootScope，这个根作用域在整个应用范围（ng-app所在标签以内）都是可以被访问到的。

`<body ng-app="App" ng-init="name='康熙'">`


###子作用域

通过ng-controller指令可以创建一个子作用域，新建的作用域可以访问其父作用域的数据。






##过滤器

在AngularJS中使用过滤器格式化展示数据，在“{{}}”中使用“|”来调用过滤器，使用“:”传递参数。


###内置过滤器

- currency将数值格式化为货币格式

- date日期格式化，年（y）、月（M）、日（d）、星期（EEEE/EEE）、时（H/h）、分（m）、秒（s）、毫秒（.sss），也可以组合到一起使用。

- filter在给定数组中选择满足条件的一个子集，并返回一个新数组，其条件可以是一个字符串、对象、函数

- json将Javascrip对象转成JSON字符串。

- limitTo取出字符串或数组的前（正数）几位或后（负数）几位

- lowercase将文本转换成小写格式

 - uppercase将文本转换成大写格式

- number数字格式化，可控制小位位数

- orderBy对数组进行排序，第2个参数可控制方向(默认false)

```javascript
<ul ng-controller="DemoController">
	<li>{{price|currency:'￥'}}</li>
	<li>{{now|date:'yyyy/MM/dd hh:mm:ss'}}</li>
	<li>{{items|filter:'s'}}</li>
	<li>{{students|filter:{age: 16} }}</li>
	<li>{{students|json}}</li>
	<li>{{items|limitTo:-1}}</li>
	<li>{{str|uppercase|limitTo:3}}</li>
	<li>{{str|lowercase}}</li>
	<li>{{num|number:0}}</li>
	<li>{{items|orderBy: '':true}}</li>
	<li>{{students|orderBy: 'age': false}}</li>
</ul>
<script>
	var App = angular.module('App', []);

	App.controller('DemoController', ['$scope', function ($scope) {

		$scope.price = 11.11;

		$scope.now = new Date;

		$scope.items = ['html', 'css', 'js'];

		$scope.students = [
			{name: '小红', age: 16},
			{name: '小明', age: 16},
			{name: '小米', age: 10}

		];

		$scope.str = 'hello Angular';

		$scope.num = '10.2345';


	}]);

	// var str = '10.5a';

	// alert(Number(str));
</script>
```


###自定义过滤器


```
<h4>{{info|capitalize:123}}</h4>

App.filter('capitalize', function () {
	return function (input, arg2) {
		console.log(arg2);
		return input[0].toUpperCase() + input.slice(1);
	}

});

$scope.info = 'my name is ';
```






##依赖注入

AngularJS采用模块化的方式组织代码，将一些通用逻辑封装成一个对象或函数，实现最大程度的复用，这导致了使用者和被使用者之间存在依赖关系。

所谓依赖注入是指在运行时自动查找依赖关系，然后将查找到依赖传递给使用者的一种机制。

常见的AngularJS内置服务有$http、$location、$timeout、$rootScope等


###推断式注入

没有明确声明依赖，AngularJS会将函数参数名称当成是依赖的名称。

这种方式会带来一个问题，当代码经过压缩后函数的参数被压缩，这样便会造成依赖无法找到。



###行内注入

以数组形式明确声明依赖，数组元素都是包含依赖名称的字符串，数组最后一个元素是依赖注入的目标函数。






##服务

服务是一个对象或函数，对外提供特定的功能。




###内建服务

- $location是对原生Javascript中location对象属性和方法的封装。![](/assets/image016.png)

- $timeout&$interval对原生Javascript中的setTimeout和setInterval进行了封装。![](/assets/image017.png)

- $filter在控制器中格式化数据。![](/assets/image018.png)

- $log打印调试信息。![](/assets/image019.png)

- $http用于向服务端发起异步请求。同时还支持多种快捷方式如$http.get()、$http.post()、$http.jsonp。![](/assets/image020.png)


####$http

传递的数据可以是'key=val&key=val'形式，这种形式叫formData
Content-Type 设成 application/x-www-form-urlencoded
当请求数据类型不一样，后端在接收的时采取方法也不一样
假如上述方式以PHP为例可以使用$_POST接收

application/json;charset=UTF-8 就是json对象形式传
Request Payload
假如采用上述方式，以PHP为例$_POST就不能接收了

```js
$http({
	url: 'example.php',
	// method: 'get',
	method: 'post',
	headers: {
		'Content-Type': 'application/x-www-form-urlencoded'
	},
	params: { // get 参数
		name: 'itcast',
		sex: '男'
	},
	// data: 'age=10'
	data: { // post 传参
		age: 10
	}
}).success(function (info) {
	// info 就是返回的数据
	$log.info(info);
});
```

![](/assets/360截图20171009033113278.jpg)

####跨域

```js
App.controller('DemoController', ['$http', '$scope', function ($http, $scope) {

	$http({
		url: 'jsonp.php?callback=JSON_CALLBACK',
		//JSON_CALLBACK是占位符，jQuery能自动生成
		method: 'jsonp' // 采用JSONP方式
	}).success(function (info) {
		console.log(info);
	});

}]);
```

![](/assets/360截图20171009034737917.jpg)


###自定义服务


- factory方法

![](/assets/360截图20171009042151554.jpg)

- service方法

![](/assets/360截图20171009130210167.jpg)

- value方法定义常量

	- 本质上一个服务,从表现形式上是一个常量

![](/assets/360截图20171009131425514.jpg)







##模块加载



###配置块

![](/assets/360截图20171009142728965.jpg)

###运行块

![](/assets/360截图20171009143902757.jpg)







##路由

一个应用是由若个视图组合而成的，根据不同的业务逻辑展示给用户不同的视图，路由则是实现这一功能的关键。


###SPA

- 不产生跳转

- 把若干功能集成到一个页面


###路由


















