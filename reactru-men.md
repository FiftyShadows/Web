## React特点

- 声明式编码 Declaractive

- Component-Based 组件化编码

- 高效的DOM Diff算法，最小化页面重绘

- 单向数据流



## MV* 框架

- 只关注视图view层和数据层model



## es6 组件 this 的处理方式有两种

- bind(this)

- 箭头函数




componentWillMount  将要装载，在render之前调用；

      componentDidMount，（装载完成），在render之后调用

componentWillMount  每一个组件render之前立即调用；

      componentDidMount  render之后并不会立即调用，而是所有的子组件都render完之后才可以调用

componentWillMount  可以在服务端被调用，也可以在浏览器端被调用；

      componentDidMount  只能在浏览器端被调用，在服务器端使用react的时候不会被调用
      

一般来说，有些组件的启动工作是依赖 DOM 的，例如动画的启动，而 componentWillMount 的时候组件还没挂载完成，所以没法进行这些启动工作，这时候就可以把这些操作放在 componentDidMount 当中。



shouldComponentUpdate(nextProps, nextState)：你可以通过这个方法控制组件是否重新渲染。如果返回 false 组件就不会重新渲染。这个生命周期在 React.js 性能优化上非常有用。
componentWillReceiveProps(nextProps)：组件从父组件接收到新的 props 之前调用。
componentWillUpdate()：组件开始重新渲染之前调用。
componentDidUpdate()：组件重新渲染并且把更改变更到真实的 DOM 以后调用。



根据是否需要高度的复用性，把组件划分为 Dumb 和 Smart 组件，约定俗成地把它们分别放到 components 和 containers 目录下。

Dumb 基本只做一件事情 —— 根据 props 进行渲染。而 Smart 则是负责应用的逻辑、数据，把所有相关的 Dumb（Smart）组件组合起来，通过 props 控制它们。

Smart 组件可以使用 Smart、Dumb 组件；而 Dumb 组件最好只使用 Dumb 组件，否则它的复用性就会丧失。

要根据应用场景不同划分组件，如果一个组件并不需要太强的复用性，直接让它成为 Smart 即可；否则就让它成为 Dumb 组件。

还有一点要注意，Smart 组件并不意味着完全不能复用，Smart 组件的复用性是依赖场景的，在特定的应用场景下是当然是可以复用 Smart 的。而 Dumb 则是可以跨应用场景复用，Smart 和 Dumb 都可以复用，只是程度、场景不一样。



Dumb 组件最好不要依赖除了 React.js 和 Dumb 组件以外的内容。它们不要依赖 Redux 不要依赖 React-redux。这样的组件的可复用性是最好的，其他人可以安心地使用而不用怕会引入什么奇奇怪怪的东西。
当我们拿到一个需求开始划分组件的时候，要认真考虑每个被划分成组件的单元到底会不会被复用。如果这个组件可能会在多处被使用到，那么我们就把它做成 Dumb 组件。



Smart 组件不用考虑太多复用性问题，它们就是用来执行特定应用逻辑的。Smart 组件可能组合了 Smart 组件和 Dumb 组件；但是 Dumb 组件尽量不要依赖 Smart 组件。因为 Dumb 组件目的之一是为了复用，一旦它引用了 Smart 组件就相当于带入了一堆应用逻辑，导致它无法无用，所以尽量不要干这种事情。一旦一个可复用的 Dumb 组件之下引用了一个 Smart 组件，就相当于污染了这个 Dumb 组件树。如果一个组件是 Dumb 的，那么它的子组件们都应该是 Dumb 的才对。



React.js 除了状态提升以外并没有更好的办法帮我们解决组件之间共享状态的问题，而使用 context 全局变量让程序不可预测。通过 Redux 的章节，我们知道 store 里面的内容是不可以随意修改的，而是通过 dispatch 才能变更里面的 state。所以我们尝试把 store 和 context 结合起来使用，可以兼顾组件之间共享状态问题和共享状态可能被任意修改的问题。



一个状态可能被多个组件依赖或者影响，而 React.js 并没有提供好的解决方案，我们只能把状态提升到依赖或者影响这个状态的所有组件的公共父组件上，我们把这种行为叫做状态提升。



高阶组件就是一个函数，传给它一个组件，它返回一个新的组件。新的组件使用传入的组件作为子组件。

高阶组件的作用是用于代码复用，可以把组件之间可复用的代码、逻辑抽离到高阶组件当中。新的组件和传入的组件通过 props 传递信息。



## react脚手架

npm i -g create-react-app

create-react-app my-app 





npm install --save react react-dom babelify babel-preset-react

npm install --save babel-preset-es2015

npm i -S webpack@1.13.2

npm i -S webpack-dev-server@1.16.5

webpack --watch

webpack-dev-server --content-base src

webpack-dev-server localhost:8080/webpack-dev-server

webpack-dev-server --content-base src --inline --hot



##exact的值为bool型，为true是表示严格匹配，为false时为正常匹配。



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





##虽然 this.props 由React本身设置以及this.state 具有特殊的含义，但如果需要存储不用于视觉输出的东西，则可以手动向类中添加其他字段。

- 如果你不在 render() 中使用某些东西，它就不应该在状态中。




##因为 this.props 和 this.state 可能是异步更新的，你不应该依靠它们的值来计算下一个状态。




