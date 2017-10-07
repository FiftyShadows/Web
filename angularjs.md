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












