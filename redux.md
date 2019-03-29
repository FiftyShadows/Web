## Redux

- 创建createStore (state, stateChanger)函数，createState函数会返回getState和dispatch

- 让createStore返回subscribe方法，订阅DOM的修改

- 优化性能，renderApp之前比较新旧数据，减少不必要的重新渲染，dispatch时的数据不可变性，共享结构

- Rdeucer(纯函数)：负责初始化state和修改state

    - reducer 是不允许有副作用的。你不能在里面操作 DOM，也不能发 Ajax 请求，更不能直接修改 state，它要做的仅仅是 —— 初始化和计算新的 state。



## React-redux

- 将context对象设置为store = createStore(themeReducer)