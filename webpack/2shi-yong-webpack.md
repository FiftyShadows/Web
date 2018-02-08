##打包JS

- webpack entry <entry> output

- webpack --config webpack.conf.js


##编译ES6/7

- Babel

- Babel-presets

- Babel-plugin



##Babel

- Babel-loader

- babeljs.io

- npm i babel-loader@8.0.0-beta.0 @babel/core

- npm i babel-loader babel-core -D



##Babel Presets    针对语法

- es2015

- es2016

- es2017

- env

- babel-preset-react

- babel-preset-stage 0 - 3

- npm i @babel/preset-env -D

- npm i babel-preset-env -D

```
module: {
        rules: [
            {
                test: /\.js$/,
                use: {
                    loader: 'babel-loader',
                    options: {
                        presets: [
                            ['babel-preset-env', {
                                targets: {
                                    browsers: ['> 10%', 'last 2 versions']    //chrome: '52'
                                }
                            }]
                        ]
                    }
                },
                exclude: '/node-modules/'
            }
        ]
    }
```


##针对函数和方法

- Generator

- Set

- Map

- Array.from

- Array.prototype.includes


##Babel Polyfill

- 全局垫片

- 为应用准备

- npm i babel-polyfill -S

- import "babel-polyfill"



##Babel Runtime Transform

- 局部垫片

- 为开发框架准备

- npm i babel-plugin-transform-runtime -D

- npm i babel-runtime -S

- .babelrc

![](/assets/360截图20180208213230459.jpg)








##typescript-loader

- 安装

    - npm i typescript ts-loader -D
    
    - npm i typescript awesome-typescript-loader -D
    
- 配置

    - tsconfig.json
    
    - webpack.config.js
    

##tsconfig

- 配置选项

    - 官网/docs/handbook/compiler-options.html
    
- 常用选项

    - compilerOptions
    
    - include
    
    - exclude
    

##声明文件

- npm i @types/lodash -D

- npm i @types/vue -D


##Typings

- npm i typings -g

- typings i lodash -D

![](/assets/360截图20180208212552725.jpg)












##提取公用代码

- 减少代码冗余

- 提高用户加载速度


##CommonsChunkPlugin

- webpack.optimize.CommonsChunkPlugin


##配置

```
{
    plugins: [
        new webpack.optimize.CommonsChunkPlugin(option)
    ]
}
```

- options.name or options.names

- options.filename

- options.minChunks

- options.chunks

- options.children

- options.deepChildren

- options.async

- 场景

    - 单页应用
    
    - 单页应用 + 第三方依赖
    
    - 多页应用 + 第三方依赖 + webpack生成代码