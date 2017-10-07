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



