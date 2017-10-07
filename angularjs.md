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
App.controller('DemoController',['#scope',function (#scope){
    // $scope 是一个空对象{}，此对象就是Model
    $scope.name = '范冰冰';
    $scope.school = 'itcast';
    $scope.courses=['MVC','模块化','指令'];
}]);
</script>
</body>
```



























