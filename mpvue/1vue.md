# 1.基础

## vue

* Vue-cli
* 单文件组件 + 声明式渲染
* 生命周期

npm install -g vue-cli

vue init webpack my-project

npm install && npm run dev

npm i -g nodemon

npm i -S wafer2-client-sdk

npm i -D sass-loader node-sass 可能需要

## 如何获取小程序在page onLoad时候传递的options

* this.$root.$mp.query进行获取

## a标签跳转页面

-- 默认是navigateTo方法

```text
<a :href="detailUrl"></a>

computed: {
    detailUrl(){
        return '/pages/detail/main?id=' + this.book.id
    }
}
```

## click方法跳转页面

* 同微信

## 数组的元素分成每3个一组

* 如果通用    请用chunk函数    比如lodash的chunk方法

## 设置image mode="aspectFit"可自动居中

## 通过百度API\([http://api.map.baidu.com/geocoder/v2/\)和经纬度，获取用户省市区](http://api.map.baidu.com/geocoder/v2/%29和经纬度，获取用户省市区)

## 通过em控制星级评价组件

## eslint --fix --ext .js.vue src server/controllers

* `--ext`后指定js文件的扩展

## 组件内的data不能用对象，必须是函数return，多个组件共享变量，会导致bug

* 一个组件的 data 选项必须是一个函数，因此每个实例可以维护一份被返回对象的独立的拷贝

