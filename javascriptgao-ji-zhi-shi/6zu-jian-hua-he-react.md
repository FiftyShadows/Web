## 组件化

- 是否做过react开发？

- React以及组件化的一些核心概念

- 实现流程



## 题目

- 说一下对组件化的理解

    - 组件的封装
    
        - 封装视图
        
        - 数据
        
        - 变化逻辑(数据驱动视图变化)
    
    - 组件的复用
    
        - props传递
        
        - 复用

- JSX本质是什么

    - JSX语法
    
        - html形式
        
        - 引入JS变量和表达式
        
        - if else
        
        - 循环
        
        - style和className
        
        - 事件
    
    - JSX解析成JS
    
        - JSX其实是语法糖
        
        - 开发环境会将JSX变异成JS代码
        
        - JSX的写法大大降低了学习成本和编码工作量
        
        - 同时，JSX也会增加debug成本
    
    - 独立的标准
    
        - JSX是React引入的，但不是React独有的
        
        - React已经将它作为一个独立标准开放，其他项目也可用
        
        - React.createElement是可以自定义修改的
        
        - 说明：本身功能已经完备；和其他标准兼容和扩展性没问题
        
![](/assets/微信截图_20180709160633.png)

![](/assets/微信截图_20180709161015.png)

![](/assets/微信截图_20180709160953.png)

![](/assets/360截图18141228396723.png)


                


- JSX和vdom的关系

    - vdom是React初次推广开来的，结合JSX
    
    - JSX就是模板，最终要渲染成html
    
    - 初次渲染 + 修改state后的re-render
    
    - 正好符合vdom的应用场景
    


- 说一下setState的过程

- 阐述自己对React和vue的认识

    - mvvm
    
    - 组件化
    

    

## 何时patch

- 初次渲染-ReactDOM.render(<App/>, container)

- 会触发patch(container, vnode)

- re-render - setState

- 会触发patch(vnode, newVnode)




## 自定义组建的解析

- 'div' - 直接渲染`<div>`即可，vdom可以做到

- Input和List，是自定义组件(class)，vdom默认不认识

- 因此Input和List定义的时候必须声明render函数

- 根据props初始化实例，然后执行实例的render函数

- render函数返回的还是vnode对象



## JSX和vdom的关系

- 为何需要vdom:JSX需要渲染成html，数据驱动视图

- React.createElement和h，都生成vnode

- 何时patch: ReactDOM.render(...)和setState

- 自定义组件的解析：初始化实例，然后执行render



## React setState的过程

- setState的异步

    - 可能会一次执行多次setState
    
    - 你无法规定、限制用户如何使用setState
    
    - 没必要每次setState都重新渲染，考虑性能
    
    - 即便是每次重新渲染，用户也看不到中间的效果
    
    - 只看到最后的结果即可

- vue修改属性也是异步

    - 效果、原因和setState一样
    
    - set中执行updateComponent是异步的

- setState的过程

    - 最终走到patch(preVnode, newVnode)    通过在setState的回调函数中renderComponent
    
    
    

## React vs vue

- 两者的本质区别

    - vue - 本质是MVVM框架，有MVC发展而来
    
    - React - 本质是前端组件化框架，由后端组件化发展而来
    
    - 但这并不妨碍他们两者都能实现相同的功能

- 看模板和组件化的区别

    - vue - 使用模板(最初由angular提出)
    
    - React - 使用JSX
    
    - 模板语法上，我更加倾向于JSX   但模板和JS混在一起，未分离 
    
    - 模板分离上，我更加倾向于vue    但指令语法与js不相符合
    
    - React本身就是组件化，没有组件化就不是React
    
    - vue也支持组件化，不过是在MVVM上的扩展
    
    - 对于组件化，我更加倾向于React，做的彻底而清晰

- 两者共同点

    - 都支持组件化
    
    - 都是数据驱动视图
    
    
    
## 问题解答

- 国内使用，首推vue。文档更易读、易学、社区够大

- 如果团队水平较高，推荐使用React。组件化和JSX




















    
    






 






























