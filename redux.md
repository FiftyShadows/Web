## Redux

- 创建createStore (state, stateChanger)函数，createState函数会返回getState和dispatch

- 让createStore返回subscribe方法，订阅DOM的修改

- 优化性能，renderApp之前比较新旧数据，减少不必要的重新渲染，dispatch时的数据不可变性，共享结构

