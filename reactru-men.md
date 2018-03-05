npm install --save react react-dom babelify babel-preset-react

npm install --save babel-preset-es2015

npm i -S webpack@1.13.2

npm i -S webpack-dev-server@1.16.5

webpack --watch

webpack-dev-server --content-base src

webpack-dev-server localhost:8080/webpack-dev-server

webpack-dev-server --content-base src --inline --hot



##atom安装本packages

- atom-ternjs对es5,es6，nodejs等的语法支持

- atom-beautify对……语言格式化

- open-in-brower

- emmet

- file-icons

- highlight-line

- highlight-selected




##约束性和非约束性组件

- 非约束性：即通过查询DOM，获取DOM属性的方式来做。跟之前jquery的做法一样，都是围绕着DOM来做的。缺点有两个：

    - 依赖DOM操作，不符合组件化的设计，也不易扩展
    
    - 查询DOM消耗更多性能
    
- 约束性：即监控<input>的变化，将值实时保存到state中，直接从state中获取值。React或者Vue都是一种基于数据驱动视图的设计方式，定好数据和视图的规则之后，只更改数据，不直接操作DOM。操作DOM的事情，交给React或者Vue这个框架的代码来搞定。




