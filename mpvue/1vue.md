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



## 跳转页面

```
<a :href="detailUrl"></a>

computed: {
    detailUrl(){
        return '/pages/detail/main?id=' + this.book.id
    }
}

```