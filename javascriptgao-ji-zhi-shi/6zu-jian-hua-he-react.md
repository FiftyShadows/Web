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






 






























