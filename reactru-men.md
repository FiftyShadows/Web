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




##props和state的区别

- React 中，props 一般只作为父组件给子组件传递数据用，不要试图去修改自己的 props ，除非你想自找麻烦

- props 不能被自身修改

- React 会实时监听每个组件的 props 和 state 的值，一旦有变化，会立刻更新组件，将结果重新渲染到页面上

- 父组件的state常常转变子组件的props

- 从子组件的角度来看，props是不可变的。如何改变子组件的props？我们仅仅需要改变父组件内部的state即可，父组件的state改变之后，引起父组件重新渲染，在渲染的过程中，子组件的data变成父组件this.state.childDdta的值。

- 父组件：处理复杂的业务逻辑、交互以及数据等。子组件：称它为Stateless组件即无状态组件，只用作展示。在我们开发过程中，尽可能多个使用无状态组件，可以缕清业务之间的逻辑关系,提高渲染效率。

- 如果子组件想要改变自身的data，这时候需要，父组件传递给子组件一个方法，改变父组件自身的state。

- 一个子控件自身可以管理自己的state，但是需要注意的是，无法管理其子控件的state。所以可以认为，state是子控件自身私有的




##无状态组件

- 无状态的函数创建的组件是无状态组件，它是一种只负责展示的纯组件，对于这种无状态的组件，使用函数式的方式声明，会使得代码的可读性更好，并能大大减少代码量，箭头函数则是函数式写法的最佳搭档



##页面返回

- window.history.back()



##componentDidMount和componentDidUpdate两个生命周期的不同

- 页面初次渲染，会走compnentDidMount

- 页面再次渲染，就不会走componentDidMount，而只走componentDidUpdate

**一定要判断参数是否发生变化**



##当props和state发生变化时执行，并且在render方法之前执行，当然初始化render时不执行该方法，需要特别注意的是，在这个函数里面，你就不能使用this.setState来修改状态。这个函数调用之后，就会把nextProps和nextState分别设置到this.props和this.state中。紧接着这个函数，就会调用render()来更新界面了




##组件更新结束之后执行，在初始化render时不执行




##componentWillReceiveProps：当props发生变化时执行，初始化render时不执行，在这个回调函数里面，你可以根据属性的变化，通过调用this.setState()来更新你的组件状态，旧的属性还是可以通过this.props来获取,这里调用更新状态是安全的，并不会触发额外的render调用

- 当组件被更新时，使用该方法是操作DOM的一次机会。这也是一个适合发送请求的地方，要是你对比了当前属性和之前属性（例如，如果属性没有改变那么请求也就没必要了）。



##componentWillReceiveProps(nextProps)

- componentWillReceiveProps()在装配了的组件接收到新属性前调用。若你需要更新状态响应属性改变（例如，重置它），你可能需对比this.props和nextProps并在该方法中使用this.setState()处理状态改变。



