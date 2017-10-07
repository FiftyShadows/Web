##定义模块

var App = angular.module('App',[]);



##定义控制器

- 一个页可以有多个模块，但是不能互想嵌套 

App.controller('DemoController',['#scope',function (#scope){
    // $scope 是一个空对象{}，此对象就是Model
    $scope.name = '范冰冰';
    $scope.school = 'itcast';
}]);




























