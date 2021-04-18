# 8.CSS工程化

## 工程化

* 组织、优化、构建、维护

## PostCSS和插件

* PostCSS本身只有解析CSS的能力
* import 模块合并
* autoprofixier
* cssnano压缩代码，还能去掉无用、重复的代码
* cssnext使用css新特性
* precss变量、变量、循环等

## 使用

* npm i postcss-cli

```text
postcss xx.css -o xx.css

//postcss.config.js
const cssnano = require('cssnano');
const atImport = require('postcss-import');
const cssnext = require('postcss-cssnext');
const precss = require('precss');

module.exports = {
    plugins: [
        atImport,
        cssnext,
        precss,
        autoprefixer({
            browers: ['Firefox > 1']
        }),
        cssnano
    ],
};
```

## gulp

## webpack

* style-loader\(将js样式插入head\), css-loader\(将css变成js\)
  * js负责在head中插入style标签和样式，性能不好
* 在css-loader中打开modules，类名变成hashcode，解决类名冲突
* extract-text-webpack-plugin把js中引入的css提取出来打包成css文件

## 如何解决css模块化问题\(import加载耗性能，多一些连接数\)

* less,sass等css预处理器，将css合并
* postcss插件\(precss-import/precss等\)
* webpack处理css（css-loader + style-loader）

