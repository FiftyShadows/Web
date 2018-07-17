## vue

- Vue-cli

- 单文件组件 + 声明式渲染

- 生命周期


npm install -g vue-cli

vue init webpack my-project

npm install && npm run dev


npm i -g nodemon

npm i -S wafer2-client-sdk

npm i -D sass-loader node-sass    可能需要




## 如何获取小程序在page onLoad时候传递的options

- this.$root.$mp.query进行获取



## a标签跳转页面

-- 默认是navigateTo方法

```
<a :href="detailUrl"></a>

computed: {
    detailUrl(){
        return '/pages/detail/main?id=' + this.book.id
    }
}

```


## click方法跳转页面

- 同微信



## 数组的元素分成每3个一组

- 如果通用    请用chunk函数    比如lodash的chunk方法



## 设置image mode="aspectFit"可自动居中